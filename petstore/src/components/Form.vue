<template>
    <div>
        <my-header :cartItemCount="cartItemCount"></my-header>
        <div class="row">
            <div class="col-md-10 col-md-offset-1">
                <div class="row">
                    <div class="col-md-4">
                        <strong>Имя:</strong>
                        <input v-model.trim="order.firstName" class="form-control" />
                    </div>
                    <div class="col-md-4">
                        <strong>Фамилия:</strong>
                        <input v-model.trim="order.lastName" class="form-control" />
                    </div>
                    <div class="form-group">
                        <div class="col-md-12"><strong>Адрес(улица, дом, квартира):</strong></div>
                        <div class="col-md-12"><input v-model.trim="order.address" class="form-control" /></div>
                    </div>
                    <div class="form-group">
                        <div class="col-md-12"><strong>Город:</strong></div>
                        <div class="col-md-12"><input v-model.trim="order.city" class="form-control" /></div>
                    </div>
                    <div class="form-group">
                        <div class="col-md-12"><strong>Область:</strong></div>
                        <div class="col-md-12">
                            <select v-model="order.region"
                                    class="form-control">
                                <option disabled value="">Область</option>
                                <option v-for="(region, key) in regions"
                                        v-bind:value="region">
                                    {{key}}
                                </option>
                            </select>
                        </div>
                    </div>
                    <div class="form-group">
                        <div class="col-md-12"><strong>Почтовый индекс:</strong></div>
                        <div class="col-md-12"><input v-model.number="order.zip"
                                                      class="form-control"
                                                      type="number" /></div>
                    </div>
                    <div class="form-group">
                        <div class="col-md-6 boxes">
                            <input type="checkbox" id="gift" value="true"
                                   v-bind:true-value="order.sendGift"
                                   v-bind:false-value="order.dontSendGift"
                                   v-model="order.gift">
                            <label for="gift">Отправить подарком?</label>
                        </div>
                    </div>
                    <div class="form-group">
                        <div class="col-md-6 boxes">
                            <input type="radio" id="home"
                                   v-bind:value="order.home"
                                   v-model="order.method">
                            <label for="home">Домашний адрес</label>
                            <input type="radio" id="business"
                                   v-bind:value="order.business"
                                   v-model="order.method">
                            <label for="business">Рабочий адрес</label>
                        </div>
                    </div>
                    <div class="col-md-12 verify">
                    <pre>
                        Имя: {{order.firstName}}
                        Фамилия: {{order.lastName}}
                        Адрес: {{order.address}}
                        Город: {{order.city}}
                        Область: {{order.region}}
                        Почтовый индекс: {{order.zip}}
                        Подарок: {{order.gift}}
                        Домашний/рабочий: {{order.method}}
                    </pre>
                    </div>
                    <div class="form-group">
                        <div class="col-md-6">
                            <button type="submit"
                                    class="btn btn-primary submit"
                                    v-on:click="submitForm">Заказать</button>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import MyHeader from './Header.vue';
export default {
    name: 'Form',
    components: {MyHeader},
    props: ['cartItemCount'],
    data () {
        return {
            regions: {
                MO: 'Московская область',
                VL: 'Владимирская область',
                AR: 'Архангельская область'
            },
            order: {
                firstName: '',
                lastName: '',
                address: '',
                city: '',
                zip: '',
                method: 'Домашний адрес',
                business: 'Рабочий адрес',
                home: 'Домашний адрес',
                gift: 'Отправить подарком',
                sendGift: 'Отправить подарком',
                dontSendGift: 'Покупаю для себя',
                region: ''
            }
        }
    },
    methods: {
        submitForm() {
            alert('Submitted');
        }
    }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
