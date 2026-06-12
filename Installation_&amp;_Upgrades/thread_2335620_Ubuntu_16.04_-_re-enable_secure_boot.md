---
title: "Ubuntu 16.04 - re-enable secure boot?"
date: 2016-08-30
forum: Installation &amp; Upgrades
---

### Post by sonicking on 2016-08-30
Hi,

I had to disable secure boot to install a driver for my wireless card.  I used this commend to disable:

```

[COLOR=#545454][FONT=arial]sudo [/FONT][/COLOR][COLOR=#6A6A6A][FONT=arial]**mokutil**[/FONT][/COLOR][COLOR=#545454][FONT=arial] --disable-validation
[/FONT][/COLOR]
```[COLOR=#545454][FONT=arial]

Now that I am done installing, do I need to re-enable the secure boot?  It feels weird to see that it says "booting to insecure mode" everytime I start the computer.  If so, how do I re-enable it?

Also just for my knowledge, is it my computer at risk if I leave it in the insecure mode???[/FONT][/COLOR]

---

### Post by mörgæs on 2016-09-01
Security is a huge topic. I'll only post a few notes. 

An attack coming from booting a hostile / tampered-with kernel (being Windows or Linux) is a very rare event. Other kinds of attack, say through a browser and the associated plug-ins, are much more important. 

When the Linux developers were forced to accept the 'secure' boot demands it caused wide criticism. The effect is that Microsoft now can ban a kernel from being signed if they find a security related reason, and as all kernels (being Windows or Linux) have security flaws Microsoft has the main switch in their hands. Not that they have tried using it yet. 

Enjoy the freedom that you have the option to disable the 'secure' boot option. I keep my old BIOS-running hardware without 'secure' features for as long as possible. Your operative system itself is one of the most secure ones available. 

Meanwhile keep focus on real security threats. To begin with, apply all software updates and install as few browser plug-ins as possible.

---

### Post by sonicking on 2016-09-02
> **mörgæs said:**
> 
Meanwhile keep focus on real security threats. To begin with, apply all software updates and install as few browser plug-ins as possible.

Hi, I am completely new to Ubuntu and Linux in general.  Please forgive my ignorance.

When I was using Windows, I used Symantec Anti Virus with a licence from my school.  It had a real-time anti-virus protection feature and it sometimes would stop virus from websites I visited on Chrome.

I checked and my school does not have the same licence for Symantec on Ubuntu.  I don't even know whether Symantec supports Ubuntu.

Do you recommend any other anti-virus extension for Chrome on Ubuntu????  Thanks!

---

### Post by wildmanne39 on 2016-09-02
Anti-virus really is not needed because there are not any known viruses for ubuntu at this time and if there where it could not harm ubuntu as long as you are not logged in as root and that account is disabled by default.

The exception would be if you are sharing a lot of emails with windows computers that could be harmed by a windows virus.

There is a ubuntu virus detector it is called clamV but it does not work very good and gives a lot of false positives.

---

### Post by sonicking on 2016-09-03
> **Wild Man said:**
> Anti-virus really is not needed because there are not any known viruses for ubuntu at this time and if there where it could not harm ubuntu as long as you are not logged in as root and that account is disabled by default.

Hi.  Booting in insecure mode is not the same thing as logging in as root, correct?  Thanks.

---

### Post by wildmanne39 on 2016-09-03
No it is not.

---

### Post by mörgæs on 2016-09-04
Here's something about logging in as root: 
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by dbsnare072 on 2016-11-13
I had the same issues. I reinstalled ubuntu completely and even when booting from a live usb of 16.04, I still get the booting in insecure mode. How do I re-enable secure boot?

---

### Post by wildmanne39 on 2016-11-13
Did you sign the key for the driver that you were having issues with? if so then do:
```
sudo mokutil --enable-validation
```
if you did not sign the key then the driver you disabled secure boot for will stop working.

---

