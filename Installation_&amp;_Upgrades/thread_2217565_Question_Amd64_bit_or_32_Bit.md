---
title: "Question Amd64 bit or 32 Bit ?"
date: 2014-04-17
forum: Installation &amp; Upgrades
---

### Post by Blue-Fox on 2014-04-17
Planning on doing a clean install of Ubuntu 14.04. I have an AMD Athalon 64bit processor. The pc only has 512 ram. 

My question is should I use the Amd64 bit or 32 Bit version of Ubuntu 14.04? 
Plan on upgrading  the memory but not sure how much I can add. 

Thank you for your help.

---

### Post by jbaerboc on 2014-04-17
I would say go with 64 bit right of the bat. If you are planning on adding anything above 3gb-4gb then you'll need 64 bit to actually use that amount of ram anyway. I have 64-bit running with 8gb of ram.

---

### Post by Blue-Fox on 2014-04-17
Thanks for the input. I had been using lubuntu 14.04 beta2 for a few days while I was waiting for the ubuntu 14.04 Lts to be released and it seamed to work ok.

---

### Post by su:bhatta on 2014-04-17
> **jbaerboc said:**
>  If you are planning on adding anything above 3gb-4gb then you'll need 64 bit to actually use that amount of ram anyway. I have 64-bit running with 8gb of ram.

This is not required actually. Even if you install 32Bit, it will be able to use 4GB or 8Gb RAM.
Actually, 32Bit system supports upto 64Gb RAM.

But since the CPU architecture is 64Bit, it's best you use 64 Bit ISO and install.
Also, since you are already running the Beta2, running the following commands in a terminal will upgrade your present installation to 14.04 LTS:

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo apt-get -f install
```

---

### Post by Muhammad_Ahmad_Mujtaba on 2014-04-17
> **su:bhatta said:**
> This is not required actually. Even if you install 32Bit, it will be able to use 4GB or 8Gb RAM.Actually, 32Bit system supports upto 64Gb RAM.Yeah supports only, but cannot utilize more than 4GB [in many cases, not completely 4GB RAM itself is utilized.]I have PC's in my university which are 32bit architecture PC's and when i see their RAM's [manually , in the motherboard, it says 8GB]but it only shows round around 4GB [not completely 4GB] because of 32 bit long addresses which can max access 4GB at a time

---

### Post by su:bhatta on 2014-04-17
> **Muhammad_Ahmad_Mujtaba said:**
> Yeah supports only, but cannot utilize more than 4GB [in many cases, not completely 4GB RAM itself is utilized.]I have PC's in my university which are 32bit architecture PC's and when i see their RAM's [manually , in the motherboard, it says 8GB]but it only shows round around 4GB [not completely 4GB] because of 32 bit long addresses which can max access 4GB at a time

Is this with Linux or Windows?

Have a look here: [https://help.ubuntu.com/community/32bit_and_64bit](https://help.ubuntu.com/community/32bit_and_64bit)
with pae, Ubuntu utilizes 64Gb RAm on 32bit architecture.

---

### Post by jbaerboc on 2014-04-18
> **su:bhatta said:**
> Is this with Linux or Windows?

Have a look here: [https://help.ubuntu.com/community/32bit_and_64bit](https://help.ubuntu.com/community/32bit_and_64bit)
with pae, Ubuntu utilizes 64Gb RAm on 32bit architecture.

I definitely did not know PAE could do that. That being said unless your CPU is not 64-bit why on earth would you go with 32-bit with that much RAM? This part grabbed my attention:

"[COLOR=#333333][FONT=Ubuntu]If you are doing heavy work where you have started to hit the 4GB memory barrier, then 64-bit is for you. Certain intensive tasks such as encoding video or audio also run significantly faster on 64-bit operating systems (NOTE: this is implementation specific).[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu][FONT=inherit][/FONT][/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]Phoronix has done some [testing]("http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1") (2009), comparing 32bit/PAE/64bit, and this seems to indicate that 64bit performs better than 32bit in almost all cases."[/FONT][/COLOR]

---

### Post by Muhammad_Ahmad_Mujtaba on 2014-04-18
PAE, how can i forget this , doh! i learned about it in intel 8088 processor assembly language course, therefore, yes you can do 32 bits extended stuff in Ubuntu OS but my university works with WINDOWS and windows is we all know what xD

---

### Post by sudodus on 2014-04-18
> **jbaerboc said:**
> I definitely did not know PAE could do that. That being said unless your CPU is not 64-bit why on earth would you go with 32-bit with that much RAM? This part grabbed my attention:

"[COLOR=#333333][FONT=Ubuntu]If you are doing heavy work where you have started to hit the 4GB memory barrier, then 64-bit is for you. Certain intensive tasks such as encoding video or audio also run significantly faster on 64-bit operating systems (NOTE: this is implementation specific).[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]Phoronix has done some [testing]("http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1") (2009), comparing 32bit/PAE/64bit, and this seems to indicate that 64bit performs better than 32bit in almost all cases."[/FONT][/COLOR]

In the beginning (and for several years) many tasks were running better in 32-bit systems compared to 64-bit systems, but gradually the software (application programs) take full advantage of the 64-bit architechture. One drawback of 64-bit systems is that they require more RAM for a certain task, so with low RAM, say below 4 GB, it might be better to use a 32-bit system. But with 4 GB or more, I think most people would recommend 64 bits.

---

### Post by jbaerboc on 2014-04-18
> **sudodus said:**
> In the beginning (and for several years) many tasks were running better in 32-bit systems compared to 64-bit systems, but gradually the software (application programs) take full advantage of the 64-bit architechture. One drawback of 64-bit systems is that they require more RAM for a certain task, so with low RAM, say below 4 GB, it might be better to use a 32-bit system. But with 4 GB or more, I think most people would recommend 64 bits.

I love how one can learn so much from these forums :D

---

