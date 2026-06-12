---
title: "java installation failed"
date: 2014-08-03
forum: Installation &amp; Upgrades
---

### Post by daniel175 on 2014-08-03
```
danielvos@ubuntu-gebruiker-pc:/$ sudo apt-get install default-jdk
Pakketlijsten worden ingelezen... Klaar
Boom van vereisten wordt opgebouwd
De status informatie wordt gelezen... Klaar
U wilt waarschijnlijk 'apt-get -f install' uitvoeren om volgende op te lossen:
De volgende pakketten hebben niet-voldane vereisten:
 default-jdk : Vereisten: default-jre (= 1:1.6-43ubuntu2) maar het zal niet geïnstalleerd worden
               Vereisten: openjdk-6-jdk (>= 6b23~pre11-1ubuntu1~) maar het zal niet geïnstalleerd worden
 linux-image-server : Vereisten: linux-image-3.2.0-64-generic maar het zal niet geïnstalleerd worden
 linux-server : Vereisten: linux-headers-server (= 3.2.0.64.76) maar 3.2.0.67.79 zal geïnstalleerd worden
E: Er zijn niet-voldane vereisten. U kunt best 'apt-get -f install' uitvoeren zonder pakketten op te geven, (of u kunt zelf een oplossing specificeren).
danielvos@ubuntu-gebruiker-pc:/$

```

Does anybody know how to fix this?

---

### Post by kkkkdddd on 2014-08-03
try
sudo apt-get -f install default-jdk 

-f is the same as --fix-broken

---

