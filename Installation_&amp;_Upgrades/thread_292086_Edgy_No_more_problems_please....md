---
title: "Edgy? No more problems please..."
date: 2006-11-03
forum: Installation &amp; Upgrades
---

### Post by Blind010 on 2006-11-03
Hi guys,    
  
First, excuse my bad english. I'm spanish ^^  
  
It's already the second time that I have the same problem upgrading from Dapper to Edgy with two different computers. I'm very angry because the error looks too bad, and a previous time,  I had the same problem and I had to format all the computer. Now, I would like to know which is the problem that causes this.  
    
Ok..   
    
I had installed the Dapper version from the CD. Today I had decided to upgrade to the version 6.10 (Edgy). I went to my sources.list, and I changed 'dapper' for 'edgy' in all the official repositories. And I made an 'apt-get update' and subsequently an 'apt-get dist-upgrade'.    
    
After being waiting exactly 2:59:59s downloading all the packages, it begins to decompress them and to install them. While I spend my time making other things. Suddenly, when I realized, an error had happened in the installation and the upgrading process was canceled. (In that moment I began suspicious because  the same problem arose with the other PC).    
    
So I executed again 'dist-upgrade' (while, I was praying xD)  
  
When 'apt' concluded of making everything, it asks me to restart. So I restart the computer.  
  
And... surprise!! :S  
  
The Ubuntu splash screen, where appear the modules loading, have been disappeared.  
During two minutes the screen is black, and suddenly, a failure of the server of the X returns.  
    
I try to start with the previous kernels and the same thing...    
  
I went to the recovery mode and I tried to make an 'apt-get update' but the wifi connection has been disabled because the ndiswrapper module has been changed. So I have not internet at the moment. (And, to be honest, I think that I am not able to configure it.)  
  
  
    
The problem is... when I make an apt-get dist-upgrade, in the exit of the command i can read:   
    
The following packages have been kept back:    
azureus hpijs python-adns python-clientcookie python-crypto    
python-egenix-mxproxy python-egenix-mxstack python-egenix-mxtexttools    
python-egenix-mxtools python-gadfly python-htmlgrn python-htmltmpl    
python-imagin python-imaging-heals python-jabber python-kjbuckets    
python-ldap python-mysqldb python-pam python-pexpect python-pgsql    
python-pylibacl python-pyopenssl python-pyxattr python-qt3 python-xmp    
python-simpletal python-soappy python-sqlite python-syck python-xmpp    
xserver-xorg-core xserver-xorg-input-elographics xserver-xorg-input-evdev    
xserver-xorg-input-kdb xserver-sorg-input-mouse sxerver-sorg-iunput-synaptics    
    
These are my questions..           
  
Did these packages have to have been installed?    
    
Why are they kept back?  
    
If they have been kept back... is there some way to not keep back them?    
        
I am desperate...      
  
Now, the system is KO. I can only enter in console mode for the recovery mode  (and without internet :( )  
    
    
Is there somebody who can help me?  
    
    
    
Greetings.

---

### Post by divague on 2006-11-03
¿Ubuntu es tu unico sistema operativo?

---

### Post by wieman01 on 2006-11-03
Cannot help you since I am using Dapper, however, a polite piece of advice: Stick with Dapper, the current stable release with long term support (LTS). Why upgrade to Edgy at all?

---

### Post by taurus on 2006-11-03
Again, modifying /etc/apt/sources.list to upgrade from Dapper to Edgy is NOT the right way to do this time...  It will break everything beyond repair.  The right way to upgrade from Dapper to Edgy is here!!!

[http://www.ubuntuforums.org/showthread.php?t=286599](http://www.ubuntuforums.org/showthread.php?t=286599)

---

### Post by wieman01 on 2006-11-03
> **taurus said:**
> Again, modifying /etc/apt/sources.list to upgrade from Dapper to Edgy is NOT the right way to do this time...  It will break everything beyond repair.  The right way to upgrade from Dapper to Edgy is here!!!

[http://www.ubuntuforums.org/showthread.php?t=286599](http://www.ubuntuforums.org/showthread.php?t=286599)
Perhaps you can answer the question... Why should someone upgrade to Edgy at all? I really appreciate Dapper since it offers LTS & is fairly stable. What would be the advantages for an average user in your opinion? I don't see any.

---

### Post by taurus on 2006-11-03
> **wieman01 said:**
> Perhaps you can answer the question... Why should someone upgrade to Edgy at all? I really appreciate Dapper since it offers LTS & is fairly stable. What would be the advantages for an average user in your opinion? I don't see any.

Because they want to run the latest of everything or they just want to be cool because they use the latest version of Ubuntu!!!  Breezy is solid as a rock so why did you upgrade or install Dapper?

---

### Post by wieman01 on 2006-11-03
> **taurus said:**
> Because they want to run the latest of everything or they just want to be cool because they use the latest version of Ubuntu!!!  Breezy is solid as a rock so why did you upgrade or install Dapper?
I didn't. Dapper was my first Ubuntu release. So anything else apart from "cool"? I see the value, no doubt. But as for stability, I prefer Dapper as I am one of those average users I was referring to. Edgy is way too experimental in my opinion.

_**EDIT:**_
Don't want to hijack this thread... my apologies.

---

### Post by Blind010 on 2006-11-03
To divague:

En el PC tengo instalado Windows y Linux en diferentes discos duros.

I have installed Windows and Linux en two differents hard discs.

------

I am surprised that apt-get can give problems...

I am not sure, but I think that in the Ubuntu official web they recommend this way (apt-get) to upgrade.

So, is not there any solution?



Thanks

---

### Post by Blind010 on 2006-11-03
Wieman01...

I upgrade Edgy because with dapper the computer was not turned off. It was hung.      
    
Also, the battery manager of the laptops was not 100% correct and I had problems with the keyboard.  (The pressed keys were repeated when the manager battery jumped)    
    
All these problems were solved when upgrading. And the 'up start' of Ubuntu is also better, throwing the processes in parallel.    
    
Greetings.

---

### Post by divague on 2006-11-03
Si es que realmente quieres instalar edgy, tal vez deberias instalarlo desde cero. Por lo que lei muchas veces hacer un dist-upgrade trae problemas, asi que lo que yo hice fue crear 3 particiones en mi disco /, /home y swap, y siempre que sale una nueva version lo instalo desde cero, y como tengo una particion para /home no tengo que hacer backups de mis archivos y no pierdo la configuracion de los programas que tenia instalados.

---

### Post by taurus on 2006-11-03
> **divague said:**
> Si es que realmente quieres instalar edgy, tal vez deberias instalarlo desde cero. Por lo que lei muchas veces hacer un dist-upgrade trae problemas, asi que lo que yo hice fue crear 3 particiones en mi disco /, /home y swap, y siempre que sale una nueva version lo instalo desde cero, y como tengo una particion para /home no tengo que hacer backups de mis archivos y no pierdo la configuracion de los programas que tenia instalados.
Hey, can you please at least type it in English since it's an English forums!!!

---

### Post by divague on 2006-11-03
> **taurus said:**
> Hey, can you please at least type it in English since it's an English forums!!!

I'm sorry, i was just telling Blind010 that if he really wanted to install edgy, he should do a clean install, because i read in the forums that lots of peolple are having problem making a dist-upgrade.

---

