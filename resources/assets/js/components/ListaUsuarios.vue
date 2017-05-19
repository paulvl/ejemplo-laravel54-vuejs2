<template>
    <div>
        <p>usuarios</p>

        <h1>{{ mensaje }}</h1>

        <table class="table">
            <thead>
                <tr>
                    <th>id</th>
                    <th>nombre</th>
                    <th>correo</th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="usuario in usuarios" v-if="usuarios.length">
                    <td>{{ usuario.id }}</td>
                    <td>{{ usuario.name }}</td>
                    <td>{{ usuario.email }}</td>
                </tr>
                <tr v-if="!usuarios.length">
                    <td class="text-center" colspan="3">No hay usuarios</td>
                </tr>
            </tbody>
        </table>
    </div>
</template>

<script>
    export default {
        data: function() {
            return {                
                usuarios: [],
                mensaje: '',
            }
        },
        mounted() {
            console.log('Componente Lista de usuario.')
            this.mensaje = window.Laravel.mensaje
            axios.get('/user')
                .then(response => {
                    this.usuarios = response.data
                })
                .catch(function (response) {
                })
        }
    }
</script>
