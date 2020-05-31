Документация за приложение HOME MANAGER
             
Цел

Основното предназначение е предоставяне на възможност, фирма потребител, да осъществи поддръжка на жилищни сгради. Необходимо е определяне на: домоуправител (служител на компанията), отделна такса за всяка сграда, списък с обслужваните сгради, списък с платежните статуси на всяка една и др. </br>
Тези функционалности са осъществени чрез следните класове: <b> Company, Person, Owner, Employee, Fee, Apartment, Building, HomeManager. </b> Всеки един съдържа два конструктора (дифолтен и с параметри), както и предефиниран метод toString(с изключение на клас HomeManager). </br> </br>


<b> Клас Company </b>

Клас, съдържащ три полета (име на собственика, име на компанията и списък със служителите). Освен аксесорите и мутаторите, са налични още три метода: </br>
<i><b> AddEmployee и AddEmployees </b></i> - добавяне на служител; в AddEmployee се добавя обект на клас AddEmployee, а в AddEmployees се добавя предварително запълнен списък със служителите. </br>
Третият метод отпечатва списъка със служители. </br> </br>


<b> Клас Person </b>

Абстрактен клас, явяващ се базов за други два - Owner и Employee. Съдържа основни описателни характеристики за един човек (име, години, националност, пол). Всички предоставени методи служат за аксесори и мутатори. </br> </br>


<b>Клас Owner</b>

Производен на клас Person, включващ допълнително поле (професия). Всички предоставени методи служат за аксесори и мутатори. </br> </br>


<b> Клас Employee </b>

Производен на клас Person, включва три допълнителни полета (идентификационен номер, максимално допустим брой обслужвани сгради и списък с управляваните сгради). Освен наличните аксесори и мутатори, съществуват методи за добавяне на сграда към списъка и за отпечатване на прилежащите към него сгради. </br> </br>


<b> Клас Fee </b>

Клас, съдържащ две полета -  задължителната такса за апартамент и таксата за всеки обитател в него. Всички предоставени методи служат за аксесори и мутатори. </br> </br>


<b> Клас Apartment </b>

Клас, съдържащ основните описателни характеристики за един апартамент (собственик, номер на апартамент, етаж, брой живущи, съгласие за плащане на таксата по поддръжка). Освен тях, има и още две - зададената от фирмата такса и обща сума от таксите на обитателите.
Освен аксесори и мутатори, още два метода допълват класа:

<i><b> SetPaymentFeе </b></i> - задаване изискваната от фирмата такса (обект на клас Fee); методът се извиква в метода SetRequiredFee на клас Building </br>
<i><b> PayFee </b></i> - проверяване, дали собственикът е съгласен да плати изискваната от фирмата такса; при положителен отговор се изчислява общата за апартамента сума (задължителна за апартамент + такса за обитател * броя на обитателите в дадения апартамента). </br> </br>


<b> Клас Building </b>

Клас, съдържащ основните описателни характеристики за един апартамент (адрес, година на строителство, застроена площ, обитаема площ, общи части, брой етажи, брой апартаменти, брой обитатели, строителен материал). Към тях са добавени едно поле (за мениджър от клас Employee) и две колекции - списък с апартаментите в сградата и платежният статус (относно таксата) на всеки апартамент. Освен аксесорите и мутаторите, съществуват още няколко метода:

<i><b> SetBuildingManager </b></i> - задаване на домоуправителя (клас Employee) </br>
<i><b> SetRequiredFee </b></i> – апартамент от списъка извиква аксесора си SetPaymentFee и подава като параметър изискваната от фирмата такса </br>
<i><b> GetBuildingResidentsAmount </b></i> - определяне броя на обитателите, като сума от обитателите във всеки апартамент </b></i></br>
<i><b> AddApartment и AddApartments </b></i> - добавяне на апартамент; в AddApartment се добавя обект от AddApartment, а в AddApartments предварително запълнен списък с апартаменти </br>
<i><b>ShowOwnersList - </b></i> отпечатване списъка с апартаменти </br> </br>


<b> Клас HomeManager </b>

Клас, съдържащ  основните описателни характеристики (фирма, задължителна такса за апартамент, такса за обитател). Допълнителните полета са (изчислената такса за апартамент, сбора на таксите на всички апартаменти, сума на събраните такси, брой на обитатели във всяка сграда) и четири колекции (списък с управлявани сгради, списък с домоуправителите, списък на апартаментите в дадената сграда, списък на платежния статус за всеки апартамент). Освен аксесори и мутатори, налични са и следните методa:

<i><b> SetHomeManager </b></i> - overload-нат метод; в едната си версия избира домоуправител, чието име е зададено от фирмата потребител, а в другата - се избира, в зависимост дали той е достигнал броят на максимално обслужвани сгради (ако не е, името на служителя се отпечатва - в противен случай изхвърля изключение от тип MaxBuildingsAmountException) </br>
<i><b> SetFloorFeeIncrement и SetResidentFeeIncrement </b></i> - задаване допълнително повишение на таксите, в зависимост от броя на етажите и обитателите </br>
<i><b> SetCalculatedApartmentFee </b></i> - задаване на сградата изчислената, изисквана такса</br>
<i><b> SetPaymentStatus и SetStatus </b></i> - отбелязване променения платежен статус на дадения апартамент, в списъка с апартаменти </br>
<i><b> GetCollectedFees </b></i> - сумиране на всички платени такси </br>
<i><b> AddHomeManagers </b></i> - добавяне предварително създаден списък със служители </br>
<i><b> AddHomeManagerToList </b></i> - добавяне на служител (клас Employee) </br>
<i><b> AddBuildingToList </b></i> - добавяне на сграда към списъка с обслужвани сгради </br>
<i><b> ShowRequiredFee </b></i> - отпечатване общата сума, която сградата трябва да предостави </br>
<i><b> ShowManagedBuildings </b></i> - отпечатване списъка със сградите </br>
<i><b> ShowPaymentStatus </b></i> - отпечатване всеки апартамент, неговата такса и платежният му статус </br>
<i><b> ShowResidentsAmount </b></i> - отпечатване броя на обитателите в дадената сграда </br> </br>


Начин на работа

Фирмата потребител въвежда необходимите данни за таксата, максималния брой управлявани от служител сгради и (евентуално) конкретен служител за домоуправител.
