### TSL/SSL sáttmálaferlið (handshake)
#### Skref fyrir skref með dæmum frá Uglu

![Ugla-handaband](https://imgur.com/HOm8DeH.jpg)

---

### Skref 1.
##### Biðlari sækist eftir SSL/TSL samskiptum.

* Biðlari (*client*) sendir HTTPS beiðni á þjón (*server*) Uglu.

* Samskiptaaðferð (*SSL/TLS*).

* Dulkóðunarpakki (*Cipher Suite*)

----

#### Innihald dulkóðunarpakkans

* Algoriðmi til að búa til og skiptast á lyklum (*key exchange algorithm*).

* Algoriðmi fyrir umfangsdulkóðun (*bulk encryption algorithm*).

* Algoriðmi fyrir skilaboðastaðfestingu (*message authentication code algorithm*).

* Fókusum mest á lyklaskiptin.

---

### Skref 2.
##### Vefþjónninn svarar

----

Það sem vefþjónninn sendir til baka:

* Dulkóðunarpakka sem báðir aðilar styðja.

* Lotuauðkenni (*session ID*)

* Auðkennisskírteini sem er gefið út af þriðja aðila (*certificate authority*)

----

![chrome-security-tab](https://imgur.com/Eeg8GiQ.png)

----

![session-id](https://imgur.com/zjSADwG.png)

----

![certificate-ugla](https://imgur.com/0qxygan.png)

---

### Skref 3.
##### Biðlarinn sannprófar auðkennisskírteinið.

----

Fjögur skref:

* Er dagsetningin í dag innan gildistíma skírteinisins?

* Er þriðji aðilinn sem gefur út skírteinið á lista yfir trausta aðila hjá biðlaranum?

* Biðlarinn ber saman almenna lykilinn sem hann er með fyrir þennan aðila og þann á skírteininu.

* Stemmir lénið á skírteininu við lén þjónsins?

----

Ef komist er í gegnum öll þessi skref veit biðlarinn að þjónninn er sá sem hann segist vera.

----

![client-trusted-certificates](https://imgur.com/QNeGgpw.png)

---

### Skref 4.
##### Biðlarinn og þjónninn þurfa lykil til að dulkóða / afkóða skilaboð.

----

#### Samhverfir lyklaalgoriðmar

Samhverfir lyklaalgoriðmar nota einn lykil til að dulkóða og afkóða, algengast er hins vegar að nota ósamhverfa lyklaalgoriðma til þess að búa til samhverfan lykil.

----

#### Ósamhverfir lyklaalgorðmar

Án þess að vita neina stærðfræði á bakvið lyklaalgoriðma þurfum við að treysta þessu tvennu um ósamhverfa lyklaalgoriðma:

----

1. Öll skilaboð sem eru dulkóðuð með lyklinum hjá Uglu geta einungis verið afkóðuð með einkalykli Uglu.

2. Aðili með aðgang að almenna lyklinum hjá Uglu getur staðfest ef skilaboð voru send af einhverjum með aðgang að einkalykli Uglu.

----

#### ECDGE_RSA

* EC**_DG_**E: Diffie-Helmann mjög algengur ósamhverfur (asymmetric) algoriðmi.

* Biðlarinn dulkóðar skilaboð með almenna lykli Uglu til að búa til sameiginlegt leyndarmál (samhverfan lykil). Ugluþjónninn afkóðar skilaboðin með einkalykilinum sínum.

----

![asymmetric-dæmi](https://imgur.com/u3AZ8ull.jpg)

---

### Skref 5.
##### Staðfesting

----

* Ugluþjónninn sendir til baka staðfestingarskilaboð, dulkóðuð með leyndarmálinu / samhverfa lyklinum.

* Þetta sameiginlega leyndarmál / þessi samhverfi lykill er svo notaður til að afkóða og dulkóða öll skilaboð á milli biðlarans og þjónsins.

---

### Niðurstaðan
##### Örugg SSL/TLS samskipti á milli biðlarans og þjónsins

![Ugla-handaband](https://imgur.com/HOm8DeH.jpg)

---

### Heimildir

* https://www.youtube.com/watch?v=33VYnE7Bzpk

* https://www.ibm.com/support/knowledgecenter/en/SSFKSJ_7.1.0/com.ibm.mq.doc/sy10660_.htm

* https://en.wikipedia.org/wiki/Cipher_suite

* https://docs.oracle.com/cd/E19693-01/819-0997/aakhc/index.html

* https://www.ssl2buy.com/wiki/symmetric-vs-asymmetric-encryption-what-are-differences#targetText=Symmetric%20encryption%20uses%20a%20single,and%20decrypt%20messages%20when%20communicating.&targetText=Asymmetric%20encryption%20takes%20relatively%20more%20time%20than%20the%20symmetric%20encryption