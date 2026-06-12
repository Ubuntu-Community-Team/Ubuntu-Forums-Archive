---
title: "Bootlogo graphics init fail on Via EPIA Trident blade 3 graphics core"
date: 2018-04-25
forum: Installation &amp; Upgrades
---

### Post by fourtytwo on 2018-04-25
When booting DVD containing lubuntu-16.04.3-desktop-i386.iso
I have tried typing "help" after the boot prompt but it does nothing.
I was hoping Lubuntu would run on this VIA EPIA Mini-ITX system to make a low power solution but it seems Lubuntu wont get past the boot stage :( Windows-XP installs perfectly and I have installed this Lubuntu DVD on other systems without problems).
Can anybody help me please ?

---

### Post by ajgreeny on 2018-04-25
Tell us more about the hardware in or on this VIA EPIA Mini-ITX system you have, and also what you mean when you say that you type Help at the boot prompt; which boot prompt? 

The more detail we have the easier we may be able to help you.

---

### Post by fourtytwo on 2018-04-25
Many thanks for your reply, my Via motherboard is elderly, the manual is dated 2003! This is the guy [https://www.viatech.com/en/support/eol/epia-eol/](https://www.viatech.com/en/support/eol/epia-eol/) It states in the manual the north bridge containing the graphics is VIA 8601A, this must emulate something win-XP understands as it installs and runs ok.

As for the boot prompt, its the one that follows when booting the ISO from DVD and the message sequence is sometging like
loading logo
graphics failed to initialise
boot:

This sequence continues at around once every 10 seconds for maybe 10 times before it changes to complaining about memory

I read somewhere that typing help to the boot prompt got you somewhere but that must be some other boot prompt elsewhere.

I must confess I am unsure this board would support the application (STM32 debug) as it only has USB1.1 ports BUT I am concerned I might face the same problem later with say a laptop, it seems a bit unfortunate that the bootloader should be dependant upon advanced graphics features, forget the logo and stick to text I say till your in a more advanced state of play! "defensive programming please" :)

---

### Post by mörgæs on 2018-04-25
Are you able to install using the [minimal ISO]("https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall")?

---

### Post by fourtytwo on 2018-04-28
Thank you for your reply, I had not heard of minimal ISO and will certainly try it when possible. I only have a very small workshop so packed away the Via system in favour of a power hungry P4 just to make progress! Next oppertunity I shall certainly try your suggestion :)

---

### Post by mörgæs on 2018-04-28
Good luck. The full list is here:

[http://cdimages.ubuntu.com/netboot/](http://cdimages.ubuntu.com/netboot/)

---

### Post by fourtytwo on 2018-04-30
Hello again well I had good luck eventually with an old copy of Ubuntu 8.10 that the enclosed picture shows booted.
I tried both Bionic and Trusty minimal ISO's and got the same result of Kernal requiring instructions not on this cpu as the enclosed picture shows.

---

### Post by mörgæs on 2018-04-30
This is old skool. I don't remember when I last saw a computer without CMOV.

I guess you can run Ubuntu up to 9.10 but not much further (not that it really makes a difference). This means of course that there is no security so don't use it for anything which requires a password.

Please mark the thread solved as this is as solved as it gets.

---

