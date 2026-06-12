---
title: "Computer Gets Stuck Installing Ubuntu 10.04"
date: 2010-09-20
forum: Installation &amp; Upgrades
---

### Post by SignatureSeriesOwner on 2010-09-20
Hi all,


I'm having an issue installing Ubuntu 10.04 onto my Dell laptop (Inspiron 2600).

I'll put the disc in, start the computer, and it comes up with the DOS-like screen, where it will say (after the copyright)  boot:

I'll hit Enter, and the Try/Install/Memory Check, etc window will pop up, and I'll click install.

In a few short seconds the screen pops up with "ubuntu" with 5 dots below it that will change from grey to red (loading, I assume)


Then (after several minutes)   I'll get this screen:


 [IMG]http://i283.photobucket.com/albums/kk282/1994LTCSS/100_0191.jpg[/IMG]

And after a couple minutes, the disc will slow down (and stop) and the HD activity light will go out. After that, nothing changes.


Any ideas?  I'm very new to Linux, and I don't want this one disc to give me a bad image of it.  I don't know if I'm doing something wrong, or what.


Thanks!

---

### Post by mörgæs on 2010-09-21
The Inspiron 2600 is and old-timer. How much memory does it have?

---

### Post by Rubi1200 on 2010-09-21
And what graphics card is installed?

---

### Post by SignatureSeriesOwner on 2010-09-21
It's not THAT old.  Geez.   :D  


It has 320MB of RAM installed currently,  it was supposed to be 512, but the guy I bought the other 256MB stick from never put it in an antistatic bag, so that was DOA.

Graphics card....

Intel Extreme Graphics 855 GM, if that is of any help.


Thanks!  :)

---

### Post by OperatorA on 2010-09-21
Good morning folks...Forums using "Ubuntu-Linux 10.4.x" and the Google "Chrome" browser for Linux...The Ubuntu install did not go too bad, but as it was removing the *temp files it logged an error and locked up the system. I tried to turn off the system and it went to a blank screen, and kept trying to boot. Computer would NOT turn off. I used the off switch on my surge protector, waited 15 seconds...(actually I went outside and smoked a cigarette...LOL) turned it back on and the PC booted into a menu that loaded Linux by default, but gave you the choice of booting to Windows-XP. Used a Linux utility to set the "default" OS to Windows (my family is OS "challenged"...LOL). Linux by choice. All works fine. Linux has already downloaded 60+ "security updates" just like Windows. Files were copied from my documents folder in Windows. All appears working. All my hardware was recognized. :-\"

---

### Post by Rubi1200 on 2010-09-21
> **SignatureSeriesOwner said:**
> It's not THAT old.  Geez.   :D  


It has 320MB of RAM installed currently,  it was supposed to be 512, but the guy I bought the other 256MB stick from never put it in an antistatic bag, so that was DOA.

Graphics card....

Intel Extreme Graphics 855 GM, if that is of any help.


Thanks!  :)
You have an Intel chipset, see here for workarounds:
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

---

### Post by mörgæs on 2010-09-21
Given the 855 problem and the ... eh, limited, memory I would go for a 9.10 Lubuntu:

[http://ubuntuforums.org/showpost.php?p=9811956&postcount=4](http://ubuntuforums.org/showpost.php?p=9811956&postcount=4)

---

### Post by Rubi1200 on 2010-09-21
> **mörgæs said:**
> Given the 855 problem and the ... eh, limited, memory I would go for a 9.10 Lubuntu:

[http://ubuntuforums.org/showpost.php?p=9811956&postcount=4](http://ubuntuforums.org/showpost.php?p=9811956&postcount=4)
I second the motion!

There are workarounds for the 8xxx series chipset but if you have limited RAM as well it would be better to go for a lighter alternative as suggested by mörgæs.

---

### Post by SignatureSeriesOwner on 2010-09-21
Ah, I see.  Once again, held back by Intel.


Would Lubuntu 10.04 work on my machine?


320MB of RAM (512 installed soon)
14.8GB spare space on HD
1.06GHz Celeron
Intel 855 GM graphics
Currently Windows XP Home installed, slimmed down to occupying 3.7GB. :)

---

### Post by Rubi1200 on 2010-09-21
> **SignatureSeriesOwner said:**
> Ah, I see.  Once again, held back by Intel.


Would Lubuntu 10.04 work on my machine?


320MB of RAM (512 installed soon)
14.8GB spare space on HD
1.06GHz Celeron
Intel 855 GM graphics
Currently Windows XP Home installed, slimmed down to occupying 3.7GB. :)
You could give it a go, but you will have to use the workarounds I linked to in a previous post. 

I have the same chipset and on my test laptop I applied the Glasen PPA workaround which worked perfectly for me (and a few others I have helped with this issue), but there is no guarantee.

In any event, I see no harm in trying it.

---

### Post by SignatureSeriesOwner on 2010-09-21
What is the difference in 9.10 and 10.04 that makes my laptop not a "direct install" out of curiosity?


9.10 would most likely be a direct install, due to the fact it works with the 855 GM ,correct?

---

### Post by mörgæs on 2010-09-22
I don't understand the question. By 'direct install', do you mean an installation straight from the CD rather than an upgrade from an earlier release? Always go for the first. 

Here is the background for why 10.04 does not work with 855 and similar chipsets:
[https://bugs.launchpad.net/ubuntu/lucid/+source/linux/+bug/563277](https://bugs.launchpad.net/ubuntu/lucid/+source/linux/+bug/563277)

---

### Post by SignatureSeriesOwner on 2010-09-23
Yes, a direct install from a LiveCD, versus an upgrade.  I never had another version of Linux on that machine.

---

### Post by Rubi1200 on 2010-09-23
As mörgæs already posted, there is an issue with your chipset in 10.04 that was not there in earlier versions.

There is a workaround (also as posted).

---

