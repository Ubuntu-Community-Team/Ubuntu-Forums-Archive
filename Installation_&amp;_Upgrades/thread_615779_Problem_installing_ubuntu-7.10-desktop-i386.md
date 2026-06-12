---
title: "Problem installing ubuntu-7.10-desktop-i386"
date: 2007-11-17
forum: Installation &amp; Upgrades
---

### Post by gordoarcane on 2007-11-17
Ok, i have decided to go with this system after becoming *upset* with Microsoft.
My computers specs are : 

Processor type : Intel(R) Celeron(R)
Processor speed : 3.06 ghz
512 mb mem

Totally formatted H/D 80gb

So heres my dilemma, downloaded the LiveCD today, checked the md5sum and that was all good, downloaded the suggested burner for the cd Infracorder, and burned at the slowest speed possible, all was good, bought the best quality cd-r i could. Upon running on the machine that i desire the new OS on, the title page comes up, when i click on install this is the message i get.

[ 31.159505] crc error
[31.160217] Kernel Panic - not syncing : VFS : unable to mount root fs on unknown block (104,1)

So i would be extremely grateful if any of you know what i should do next, im a noob to linux, and wish to become yet another happy and grateful user. If you have suggestions please keep them simple...or as simple as is possible, remember i only have access to my bios etc by pressing del at startup, are there settings in there i should perhaps adjust ? I look forward to hopefully reciveing some replys and ultimately the solution to my problem.

Thanks.

---

### Post by taurus on 2007-11-17
Can you try the alternate CD?

---

### Post by Pumalite on 2007-11-17
[http://ubuntuforums.org/showthread.php?t=477921](http://ubuntuforums.org/showthread.php?t=477921)

---

### Post by gordoarcane on 2007-11-17
> **taurus said:**
> Can you try the alternate CD?

Sorry how do you mean the alternate CD, the other choice available to me from the main download page on the main site ?

Thank you for replying.

---

### Post by taurus on 2007-11-17
[http://www.gtlib.gatech.edu/pub/ubuntu-releases/7.10/](http://www.gtlib.gatech.edu/pub/ubuntu-releases/7.10/)

---

### Post by gordoarcane on 2007-11-17
> **Pumalite said:**
> [http://ubuntuforums.org/showthread.php?t=477921](http://ubuntuforums.org/showthread.php?t=477921)

I see, thread lead me to thread, and to information surrounding the kernal, heartning to see im not the only one, frustrating that it does happen to me and others, thank you for providing the link.

---

### Post by gordoarcane on 2007-11-17
> **taurus said:**
> [http://www.gtlib.gatech.edu/pub/ubuntu-releases/7.10/](http://www.gtlib.gatech.edu/pub/ubuntu-releases/7.10/)

Thank you for the link, however im spoilt for choice, and when i look at all the options for download...tis confusing...

---

### Post by xeth_delta on 2007-11-17
Have you tried what is suggested in the last post of [http://ubuntuforums.org/showthread.php?t=421479&highlight=kernel+panic]("http://ubuntuforums.org/showthread.php?t=421479&highlight=kernel+panic")?

Regardig the alernate cd, if you scroll down page you will find a section called "Alternate install CD", choose "PC (Intel x86) alternate install CD" for 32 bit and "64-bit PC (AMD64) alternate install CD" for 64 bit.

Xeth

---

### Post by Pumalite on 2007-11-17
You can download from here:
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
Mark the box below the sign 'Start Downloading'

---

### Post by gordoarcane on 2007-11-17
> **gordoarcane said:**
> Thank you for the link, however im spoilt for choice, and when i look at all the options for download...tis confusing...

Hmmmm this one i suppose : Desktop CD for 64-bit PC (AMD64) computers, however i have seen that another person with same said problem used an earlier version of ubuntu, after suffering the same problem as me and managed to get that one up and running, would you think it would be wise to install an earlier version, then perhaps upgrade once i actually get my linux os up and running ??

---

### Post by Pumalite on 2007-11-17
You can also try a 32 bit.

---

### Post by gordoarcane on 2007-11-17
ubuntu 5.04, what would you guys think of that version, ?

---

### Post by gordoarcane on 2007-11-17
> **xeth_delta said:**
> Have you tried what is suggested in the last post of [http://ubuntuforums.org/showthread.php?t=421479&highlight=kernel+panic]("http://ubuntuforums.org/showthread.php?t=421479&highlight=kernel+panic")?

Regardig the alernate cd, if you scroll down page you will find a section called "Alternate install CD", choose "PC (Intel x86) alternate install CD" for 32 bit and "64-bit PC (AMD64) alternate install CD" for 64 bit.

Xeth

Yes i tryed the safemode option mentioned there just now, but the same error came up, thank you for the post and thoughts

---

### Post by Pumalite on 2007-11-17
I would go for 6.06 LTS instead.

---

### Post by xeth_delta on 2007-11-17
> **gordoarcane said:**
> Yes i tryed the safemode option mentioned there just now, but the same error came up, thank you for the post and thoughts

I think you also had to pass the "noapic" argument to the kernel at boot time. Did you do that, too?

Xeth

---

### Post by gordoarcane on 2007-11-17
> **gordoarcane said:**
> ubuntu 5.04, what would you guys think of that version, ?

Ok will download and try the 5.04, will come back when i have done it and let you know. Thanks to all that have replyed, makes me feel not alone, and i really appricate the help you have offered. G

---

### Post by gordoarcane on 2007-11-17
> **xeth_delta said:**
> I think you also had to pass the "noapic" argument to the kernel at boot time. Did you do that, too?

Xeth

I dont know what "noapic" is, would it be something i would have to type in as i see that theres an option to do some typing in a small diagonal box that appears by pressing f5 or f6 i think.

---

### Post by gordoarcane on 2007-11-17
> **Pumalite said:**
> I would go for 6.06 LTS instead.

Have taken your advice and am downloading it now. Thanks.

---

### Post by xeth_delta on 2007-11-17
> **gordoarcane said:**
> I dont know what "noapic" is, would it be something i would have to type in as i see that theres an option to do some typing in a small diagonal box that appears by pressing f5 or f6 i think.

I don't have an installation cd with me to check, but I am sure there is an option to pass arguments to the kernel, probably f5 or f6, as you said.

I'll try looking into it.
Xeth

---

### Post by Pumalite on 2007-11-17
[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)
[https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html](https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html)

---

### Post by gordoarcane on 2007-11-17
> **xeth_delta said:**
> I don't have an installation cd with me to check, but I am sure there is an option to pass arguments to the kernel, probably f5 or f6, as you said.

I'll try looking into it.
Xeth

I had a try while waiting for download of 6.06 on this machine, found this : [http://ubuntuforums.org/archive/index.php/t-148761.html](http://ubuntuforums.org/archive/index.php/t-148761.html)
And did as was said but no joy, both noapic and noapic-- . Oh well, will keep plugging away, thank you for the reply.

---

### Post by Pumalite on 2007-11-17
[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)
[https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html](https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html)

---

### Post by xeth_delta on 2007-11-17
> **Pumalite said:**
> [http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)
[https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html](https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html)

Ineed you are right, you can change boot parameters for an installed system from the grub config file and the grub menu typing "e". What I meant was changing the boot parameters while booting the installation CD. I know it is a simple menu option, just don't remember which one, it's been a while since I last used an instalation CD. :)

Maybe the ubuntu documentation link in your post can shed some light.

Xeth

---

### Post by gordoarcane on 2007-11-17
> **Pumalite said:**
> [http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)
[https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html](https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html)

Goshly, tis rather technical, im slowly absorbing the information, obviously this was meant to happen to me...and for me to be here typing, and spending the past 24hrs on a somewhat simple install of an os onto a system...*grins*, thank you for the links, am about to burn the V6.06, wish me luck !

---

### Post by gordoarcane on 2007-11-17
Ok downloaded v6.06. burned etc, ran on the said machine and the same problem as i started this thread off with... does anyone have any ideas on what to do next ?

---

### Post by Pumalite on 2007-11-17
Did you download and try the Alternate CD?

---

### Post by gordoarcane on 2007-11-17
> **Pumalite said:**
> Did you download and try the Alternate CD?

The alternate cd, no i have not done that, just the versions i have listed so far... I have been on this for past 12 hrs, so need some sleep, when i wake up i will download the alternate, and see if that structure helps to perhaps overcome this problem i have so far. Thank you for the suggestion, and i will keep updated and checking.

---

### Post by gordoarcane on 2007-11-18
Ok am downloading the alternate version of 7-10, will try that and see.

---

### Post by gordoarcane on 2007-11-18
I Solved the problem !!!! Hurrah !!! Ok, heres how i did it, i looked round the net and discovered someone had a problem the same, they said they removed a stick of ram, and voila...everything was ok, it was the ram that was faulty...

Upon startup of my system i noticed that it said 256 instead of 512, so i pulled one card, same error, pulled the other card and the install began, as time went on yesterday i felt that it had to be a hardware problem at my end, i kept getting the same error off all the downloaded versions...

Anyway, just gettiing the needed updates on my computer, will be paying the shop where i got the system a visit tommorow with said stick of faulty ram...they said the comp was 100% ok...hmmmm,  Many Many thanks to all of you who gave me suggestions and took the time to write, im now the proud owner of a pure linux Ubuntu system and im very happy.

---

### Post by Pumalite on 2007-11-18
You are welcome. Good luck.

---

### Post by xeth_delta on 2007-11-18
You are most welcome! Enjoy the Ubuntu adventure! :D

By the wat, should you need to check your ram in the future, the installation CDs include a memory integrity check boot option.

Good luck!

Xeth

---

