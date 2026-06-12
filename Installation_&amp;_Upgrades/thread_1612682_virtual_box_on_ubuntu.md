---
title: "virtual box on ubuntu"
date: 2010-11-03
forum: Installation &amp; Upgrades
---

### Post by David52 on 2010-11-03
I have been trying to make my magicJack work on Ubuntu for a while and cannot get it to do so. I have searched on Google and did find some information. I did load virtual box from the software center but it does not work. I run a duel boot system with windows xp and the latest ubuntu system. I read thru the forum that I need to install the binary version on VBox to get the system to reconize the usb port. The one from the software center has nothing for the usb port. It does show on the desktop the mj phone, I do get  a dial tone but that is all because the mj will not mount. I have only been with a linux system for a few months so I do not understand how to do a manual install of VBox from their homepage. Can anyone give me instructions on how to do so. I am pretty much a layman when it comes to this part on llinux. The software download center is really simple to use, but doing this manually I am really stupid on this part. If anyone can help me please do so for I sure would like to say screw windows full time and run ubuntu but we use our mj as our basic telephone and we have to run windows all the time to keep the phone going. Any information would be really helpful please.
David52

---

### Post by sikander3786 on 2010-11-03
Hi.

If the downloaded packages are in .deb format, they can be installed as easily on Ubuntu as you install .exe on Windows. Mean just double click.

Download the correct .deb of Virtualbox for your Ubuntu Version from here and double click it and it would be easy to install.

[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

You can also add the PPA for non-free Virtualbox in Software Center under Edit > Software Sources > Other Software Tab. Instructions on the link posted above. That way you just need to update the repository information and then you'll be able to find the closed source Virtualbox in Software Center.

If you install it by downloading the .deb package, you'll also need to install dkms. Instructions on the the same Virtualbox link posted above.

```
sudo apt-get install dkms
```

---

### Post by David52 on 2010-11-03
on the link u sent me are you talking about downloading this link?  Ubuntu 10.04 LTS ("Lucid Lynx") [i386]("http://download.virtualbox.org/virtualbox/3.2.10/virtualbox-3.2_3.2.10-66523%7EUbuntu%7Elucid_i386.deb") | [AMD64]("http://download.virtualbox.org/virtualbox/3.2.10/virtualbox-3.2_3.2.10-66523%7EUbuntu%7Elucid_amd64.deb") for this is the version of ubuntu I am running. I love the system and I know there is a way to make this magicJack work.
Tks friend
david52

---

### Post by sikander3786 on 2010-11-03
Yes. You can download i386 version if you are running 32-bit Ubuntu and AMD64 version if you are running 64-bit.

I have no idea about magicJack.

---

### Post by David52 on 2010-11-03
I got the package installed thanks. Now I will figure out the rest later this evining. Thanks for the help on install.
david52

---

### Post by David52 on 2010-11-06
I uploaded the Virtual box file the way you told me. I got version 3.2.10 loaded and working in vbox I do have windows xp up and running. I fully do not understand the update process > sudo apt-get install dkms



I did do a system update thru synaptic manager and did install dkms as u spoke of but I cannot get virtual box to acknolwdege the usb port, and I did go into the ubuntu terminal and go into root, but I can not get it to accept the install as quoted. Can anyone tell me what I am doing wrong please?

---

