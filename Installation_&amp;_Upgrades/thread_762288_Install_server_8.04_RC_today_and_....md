---
title: "Install server 8.04 RC today and ..."
date: 2008-04-22
forum: Installation &amp; Upgrades
---

### Post by lord_farfig on 2008-04-22
Hi guys,

I've just built a new server for my home/office and I'm curious to test 8.04 since it's going to be an LTS distro.  Anyway, I wish to know if I install the RC (DLing now) today, can I (in 3, err 2 days) upgrade via APT to the FINAL?  

Not that I can't wait 3 days, but I would rather have this machine online and serving files ASAP.  I get antsy with new equipment!  Hehe. :)

-Eric

(p.s. I posted in Server HW too)

---

### Post by overdrank on 2008-04-22
> **lord_farfig said:**
> Hi guys,

I've just built a new server for my home/office and I'm curious to test 8.04 since it's going to be an LTS distro.  Anyway, I wish to know if I install the RC (DLing now) today, can I (in 3, err 2 days) upgrade via APT to the FINAL?  

Not that I can't wait 3 days, but I would rather have this machine online and serving files ASAP.  I get antsy with new equipment!  Hehe. :)

-Eric

(p.s. I posted in Server HW too)

Hi and welcome, yes when you update when Hardy is released you will have the final product. :KS

---

### Post by jicarre on 2008-04-22
Hi everybody,

I am just arrived on the forum and a very newbie in UBUNTU. I like so much the OS. I am using it since last mounth ! And I manage already a little bite.

While the forum is so big and I tried to find an answer to my question... I did not till now.

After updating UBUNTU to 7.10, I got in trouble with this

"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I had found a solution on the post of UTUTU saying the file "getopt".
I was supposed to copy that file in /usr/bin but I am so ignorant that no possible to do it ! Where can I learn the prompt command and to use the terminal properly... 

Does exist a glossary or lexique with all commands like it was with the DOS ?

I would be so happy to fix that problem first (because of that, no way to install or to uptade UBUNTU not either to report the problem to the community)

Thank you to help me and I will appreciate :(

---

### Post by overdrank on 2008-04-22
> **jicarre said:**
> Hi everybody,

I am just arrived on the forum and a very newbie in UBUNTU. I like so much the OS. I am using it since last mounth ! And I manage already a little bite.

While the forum is so big and I tried to find an answer to my question... I did not till now.

After updating UBUNTU to 7.10, I got in trouble with this

"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I had found a solution on the post of UTUTU saying the file "getopt".
I was supposed to copy that file in /usr/bin but I am so ignorant that no possible to do it ! Where can I learn the prompt command and to use the terminal properly... 

Does exist a glossary or lexique with all commands like it was with the DOS ?

I would be so happy to fix that problem first (because of that, no way to install or to uptade UBUNTU not either to report the problem to the community)

Thank you to help me and I will appreciate :(

Hi and welcome, you will need to run that command in the terminal located under, application, accessories. ```
sudo dpkg --configure -a
```
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)
[http://www.oreillynet.com/linux/cmd/](http://www.oreillynet.com/linux/cmd/)

---

### Post by jicarre on 2008-04-22
Thank you Overdrank,

For answering so fast !

I did that in the terminal and it made that !?!


jicarre@jicarre-desktop:~$ sudo dpkg --configure -a
[sudo] password for jicarre:
Paramétrage de java-common (0.26ubuntu1) ...

Paramétrage de odbcinst1debian1 (2.2.11-16) ...

Paramétrage de unixodbc (2.2.11-16) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
jicarre@jicarre-desktop:~$ 

Is that enough ? I send you this answer and verify if I am able to update or to install program ?:confused:

---

### Post by jicarre on 2008-04-22
Hi , Me one's more


I made an update to see if working. It answered to me :

est impossible d'installer ou de supprimer des logiciels. Veuillez tout d'abord utiliser le gestionnaire de paquets « Synaptic » ou lancer « sudo apt-get install -f » dans un terminal pour réparer ce problème.

So I did that in the terminal and it gave me this :

Outil de configuration des paquets                                              
                                                                                
 &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuration de sun-java6-jre &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;  
 &#9474;                                                                           &#9474;  
 &#9474; Operating System Distributor License for Java v1.1 (DLJ)                  &#8593;  
 &#9474;                                                                           &#9646;  
 &#9474; Operating System Distributor License for Java version 1.1 (DLJ)           &#9618;  
 &#9474;                                                                           &#9618;  
 &#9474; SUN MICROSYSTEMS, INC. ("SUN") IS WILLING TO LICENSE THE JAVA PLATFORM    &#9618;  
 &#9474; STANDARD EDITION DEVELOPER KIT ("JDK" - THE "SOFTWARE") TO YOU ONLY UPON  &#9618;  
 &#9474; THE CONDITION THAT YOU ACCEPT ALL OF THE TERMS CONTAINED IN THIS LICENSE  &#9618;  
 &#9474; AGREEMENT (THE "AGREEMENT").  PLEASE READ THE AGREEMENT CAREFULLY.  BY    &#9618;  
 &#9474; INSTALLING, USING, OR DISTRIBUTING THIS SOFTWARE, YOU ACCEPT ALL OF THE   &#9618;  
 &#9474; TERMS OF THE AGREEMENT.                                                   &#9618;  
 &#9474;                                                                           &#9618;  
 &#9474; 1.  DEFINITIONS. "Software" means the code identified above in binary     &#9618;  
 &#9474;     form, any other machine readable materials including, but not         &#9618;  
 &#9474;     limited to, libraries, source files, header files, and data files),   &#8595;  
 &#9474;                                                                              
 &#9474;                                  <Ok>                                        
 &#9474;                                                                           &#9474;  
 
and more ... But I could not copy and paste here 



What is the trouble, I am trying to type OK but no way to get out of this?&#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;

---

### Post by overdrank on 2008-04-22
> **jicarre said:**
> Hi , Me one's more


I made an update to see if working. It answered to me :

est impossible d'installer ou de supprimer des logiciels. Veuillez tout d'abord utiliser le gestionnaire de paquets « Synaptic » ou lancer « sudo apt-get install -f » dans un terminal pour réparer ce problème.

So I did that in the terminal and it gave me this :

Outil de configuration des paquets                                              
                                                                                
 &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuration de sun-java6-jre &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;  
 &#9474;                                                                           &#9474;  
 &#9474; Operating System Distributor License for Java v1.1 (DLJ)                  &#8593;  
 &#9474;                                                                           &#9646;  
 &#9474; Operating System Distributor License for Java version 1.1 (DLJ)           &#9618;  
 &#9474;                                                                           &#9618;  
 &#9474; SUN MICROSYSTEMS, INC. ("SUN") IS WILLING TO LICENSE THE JAVA PLATFORM    &#9618;  
 &#9474; STANDARD EDITION DEVELOPER KIT ("JDK" - THE "SOFTWARE") TO YOU ONLY UPON  &#9618;  
 &#9474; THE CONDITION THAT YOU ACCEPT ALL OF THE TERMS CONTAINED IN THIS LICENSE  &#9618;  
 &#9474; AGREEMENT (THE "AGREEMENT").  PLEASE READ THE AGREEMENT CAREFULLY.  BY    &#9618;  
 &#9474; INSTALLING, USING, OR DISTRIBUTING THIS SOFTWARE, YOU ACCEPT ALL OF THE   &#9618;  
 &#9474; TERMS OF THE AGREEMENT.                                                   &#9618;  
 &#9474;                                                                           &#9618;  
 &#9474; 1.  DEFINITIONS. "Software" means the code identified above in binary     &#9618;  
 &#9474;     form, any other machine readable materials including, but not         &#9618;  
 &#9474;     limited to, libraries, source files, header files, and data files),   &#8595;  
 &#9474;                                                                              
 &#9474;                                  <Ok>                                        
 &#9474;                                                                           &#9474;  
 
and more ... But I could not copy and paste here 



What is the trouble, I am trying to type OK but no way to get out of this?&#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;
HI and use the tab key to highlight OK and then hit enter. :KS

---

### Post by jicarre on 2008-04-22
Thanks,

I got it !

But it is still saying 


[B]E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.[/B]
[COLOR="Red"]
So I am refering to the following post


[COLOR="Red"]http://ubuntuforums.org/showthread.php?t=724273&highlight=ututu&page=5[/COLOR]

and in particular this :

 Re: sudo dpkg --configure -a
Quote:
Originally Posted by eebamxela View Post
every time i initiate the installation of ANY file, the installer tells me this:



I checked the system monitor for any programs that might be the culprit for this error, but nothing else is open.

Forgive my noobyness, is there a way to install something through the terminal?


the results from those other lines of code are here:
Somehow you lots getopt. Not sure why. [COLOR="SeaGreen"]But anyway, copy the attached file to /usr/bin as root.[/COLOR]

Then, do dpkg --configure -a
[/COLOR]
I hope it will fix the problem, assuming there is nothing else you lost.

Good luck!!!
__________________



So I want to do it like they did... But I am so ignorant that I can not type it properly in the terminal . How to do it ? I tried it but without success 





[http://ubuntuforums.org/showthread.php?t=724273&highlight=ututu&page=5](http://ubuntuforums.org/showthread.php?t=724273&highlight=ututu&page=5)

---

### Post by jicarre on 2008-04-22
After using package manager, it is saying :


[COLOR="SeaGreen"]La liste des logiciels est corrompue

Il est impossible d'installer ou de supprimer des logiciels. Veuillez tout d'abord utiliser le gestionnaire de paquets « Synaptic » ou lancer « sudo apt-get install -f » dans un terminal pour réparer ce problème.[/COLOR]

So I tried to type " sudo apt-get install -f" 
result is :

[COLOR="Blue"]jicarre@jicarre-desktop:~$ sudo apt-get install -f 

[sudo] password for jicarre:

E: L'option « &#65533; » de la ligne de commande [d'origine -f ] est inconnue.

jicarre@jicarre-desktop:~$ sudo apt-get install -f

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

jicarre@jicarre-desktop:~$ dpkg --configure -a

dpkg: l'opération demandée requiert les privilèges du superutilisateur

jicarre@jicarre-desktop:~$ 


[/COLOR]


So it ask for full privileges and while I am the boss (the only one using the computer)

What can I do for giving my full acces to the computer ?

---

### Post by overdrank on 2008-04-22
> **jicarre said:**
> After using package manager, it is saying :


[COLOR="SeaGreen"]La liste des logiciels est corrompue

Il est impossible d'installer ou de supprimer des logiciels. Veuillez tout d'abord utiliser le gestionnaire de paquets « Synaptic » ou lancer « sudo apt-get install -f » dans un terminal pour réparer ce problème.[/COLOR]

So I tried to type " sudo apt-get install -f" 
result is :

[COLOR="Blue"]jicarre@jicarre-desktop:~$ sudo apt-get install -f 

[sudo] password for jicarre:

E: L'option « &#65533; » de la ligne de commande [d'origine -f ] est inconnue.

jicarre@jicarre-desktop:~$ sudo apt-get install -f

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

jicarre@jicarre-desktop:~$ dpkg --configure -a

dpkg: l'opération demandée requiert les privilèges du superutilisateur

jicarre@jicarre-desktop:~$ 


[/COLOR]


So it ask for full privileges and while I am the boss (the only one using the computer)

What can I do for giving my full acces to the computer ?

HI and using the dpkg command you need to add sudo. I gave the link earlier to the root sudo.

---

### Post by jicarre on 2008-04-22
A BIG, BIG THANK You Overdrank,



I am so happy, and I am so confused to not read your links in the bottom of your first message 8

As I was in hurry, I was stupid and I modeled your links with an usual signature... Sorry

But after you told me I had a serious check and NOW ....

Unbelievable I am able to get the root and configure -a... RESULT I am able to install, update and so on !


Many thanks to you Overdrank !:guitar::):KS

---

### Post by overdrank on 2008-04-22
> **jicarre said:**
> A BIG, BIG THANK You Overdrank,



I am so happy, and I am so confused to not read your links in the bottom of your first message 8

As I was in hurry, I was stupid and I modeled your links with an usual signature... Sorry

But after you told me I had a serious check and NOW ....

Unbelievable I am able to get the root and configure -a... RESULT I am able to install, update and so on !


Many thanks to you Overdrank !:guitar::):KS

No problem, with the new forum it is hard to see the links :)

---

### Post by lord_farfig on 2008-04-22
> **overdrank said:**
> Hi and welcome, yes when you update when Hardy is released you will have the final product. :KS

Excellent, that is what I thought.  Thank you for answering *MY* question!

-Eric

---

### Post by overdrank on 2008-04-22
> **lord_farfig said:**
> Excellent, that is what I thought.  Thank you for answering *MY* question!

-Eric

Your welcome, and YOUR thread was slightly highjacked. ;)

---

