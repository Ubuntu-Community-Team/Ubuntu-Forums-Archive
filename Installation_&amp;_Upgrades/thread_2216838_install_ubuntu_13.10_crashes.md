---
title: "install ubuntu 13.10 crashes"
date: 2014-04-14
forum: Installation &amp; Upgrades
---

### Post by savvas2 on 2014-04-14
Hello,

I have read some forums about the error
" load fallback graphic devices failed"
but after some update.
In my case I want to install the 13.10 and I insert the DVD, it starts from DVD, and after some messages that passes, I have this failure
and then a black screen.
Any suggestions?

Thanks in advance

---

### Post by su:bhatta on 2014-04-14
Hi and welcome to the forum.

Please give us details of the system you are using(CPU, Graphics card, RAM etc).

It can be due to the GPU your system uses.
Which graphics card are you using.by any chance is it AMD or Nvidia?

Also, are you using a UEFI boot system?

As a  start you can look here : [http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it?lq=1](http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it?lq=1)

---

### Post by savvas2 on 2014-04-14
Thanks for the quick response,
I tried the link that you sent me but I have black screen with nomodeset or acpi off.
the machine that I try to install Ubuntu is a dual boot with win xp and Ubuntu 12.04
i want to clear the previous installations and install the 13.10
graphics- sis VGA adapter
cpu- Intel pentium 4 3ghz 
Ram- 1 mb
bios , no uefi

---

### Post by su:bhatta on 2014-04-14
Now, I am not sure about the sis VGA adaptor there!
But i dug up this really old thread here : [http://ubuntuforums.org/archive/index.php/t-927219.html](http://ubuntuforums.org/archive/index.php/t-927219.html)
Seems like difficult proposition.
Maybe somebody with better experience can help you out.

But with that Pentium4 that you mention I think you should try Lubuntu : [http://lubuntu.net](http://lubuntu.net)
And I am sure you meant to write Ram : 1GB.

Download the ISO of Lubuntu and see if you get a live session. Also, if required try with 'nomodeset' kernel arguments.
Other options which you have are, Bodhi Linux, which is based on Ubuntu and has a low system resources requirement.

---

### Post by mörgæs on 2014-04-14
The thread mentioned above is obsolete.
SIS graphics work without modifications in 14.04.

---

### Post by su:bhatta on 2014-04-15
> **mörgæs said:**
> The thread mentioned above is obsolete.
SIS graphics work without modifications in 14.04.

Hey morgaes, thanks a ton. I really had no idea about that. 
Will keep that in mind.

---

### Post by mörgæs on 2014-04-15
You're welcome. Please spread the word.
Savvas, how does it work in a live boot of X/Lubuntu 14.04?

---

