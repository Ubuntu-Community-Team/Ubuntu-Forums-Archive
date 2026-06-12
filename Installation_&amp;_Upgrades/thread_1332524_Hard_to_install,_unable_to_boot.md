---
title: "Hard to install, unable to boot"
date: 2009-11-20
forum: Installation &amp; Upgrades
---

### Post by chinchulin on 2009-11-20
Hi to all. This is my first post in this forum.
I have been fooling around with Ubuntu live cds for a while. Different versions of Ubuntu didn't get on too well with my configuration and even booting "live" I had desync'ed image or errors. I checked RAM, HD... Everything was ok and worked fine with XP. 

Some days ago I decided to erase XP and install the new Karmic Koala from scratch in a 60 GB partition. This time I tried to do a fresh install but my computer kept rebooting all the time soon after the small white round logo appeared on screen. I was able to boot live and install from there. Afterwards, I tried again, formatted and installed from scratch. I used 50 GB for system (Ext 4, mounted on \) and 10 GB for Swap. It booted ok, I updated some files, downloaded some codecs and surfed the internet for a while. Last night I turned the pc on and... it wouldn't boot. I tried modifying some BIOS parameters and I got the different messages you can see in these pictures:

[IMG]http://img263.imageshack.us/img263/3425/mensaje01.jpg[/IMG]

[IMG]http://img263.imageshack.us/img263/5800/mensaje02.jpg[/IMG]

Any idea about why this is happening? How can I fix it? Is there any incompatibility with my gear? 

Please, excuse my possible errors and imprecissions, I'm more or less a beginner. ;)

AMD XP 2800, 1 GB RAM, MOBO Asus AN7, HD Seagate 400 GB, ATI Radeon 9650

---

### Post by louieb on 2009-11-20
What happened when you pressed <ctrl>+d?

Do you remember what part of the BIOS setup you modified.? Maybe you should try the BIOS default options again?

1st thing I would do is boot with the live CD - open System>Administration>Gparted
right click on the Ubuntu partition and select **check **then **apply**. Then reboot.


Do you have Internet with the live CD?

---

### Post by chinchulin on 2009-11-21
Hi [louieb]("http://ubuntuforums.org/member.php?u=120176"). Thanks for your answer:

> **louieb said:**
> What happened when you pressed <ctrl>+d?
It tried to boot again but immediately came back to the same screen.

> **louieb said:**
> Do you remember what part of the BIOS setup you modified.? Maybe you should try the BIOS default options again?
I tried everything that came to my mind. First I used the "defaults" option, then I used "optimal"... Then I started modifying the RAM times. This motherboard has the dual channel feature and I set the times to "Controlled by SPD" to enable it. It didn't work, so I tried all the other settings like "turbo", "optimal". I think the pc started beeping and didn't post at all with "turbo". I even opened the case and moved the modules around. 
After the RAM changes didn't solve the issue I tried any option that sounded reasonable to me and some that didn't, like enabling/disabling the onboard audio soundcard or firewire, raid and so on. I looked for something with the name ACPI on it, since it's mentioned in the pictures, but I didn't find anything. I reseted the bios several times with the hardware jumper as well.
BIOS is updated to the last version published. And as I said before, everything has been working ok for years with XP.

> **louieb said:**
> 1st thing I would do is boot with the live CD - open System>Administration>Gparted
right click on the Ubuntu partition and select **check **then **apply**. Then reboot.
What does it do? 

> **louieb said:**
> Do you have Internet with the live CD?I'm going to try it and I'll let you know.

Thanks again!

---

### Post by louieb on 2009-11-21
> **chinchulin said:**
> 
What does it do? 
  tries to fix file system errors. runs
```
e2fsck -f -y -v /dev/sda#
```

---

### Post by ahmet1916 on 2009-11-22
Hey there

You may be experiencing a kind of sata disk problem which I had several times on many linux distributions. Here is the solution works fine for me. On the boot up screen where you can select the language, type of installation etc. press F6 for advanced boot up options then type      pci=nomsi   

Then continue booting up. In my case, I have some problems with the south bridge of my motherboard and this causes the linux systems to fail loading sata disk modules.

You may want to give it a try. Hopfuly it works for you as well.

---

### Post by chinchulin on 2009-11-22
Hello!
I took a picture of the message appearing when I pressed ctrl+D. This is it:
[IMG]http://img513.imageshack.us/img513/1654/ctrld.jpg[/IMG]

It says something about the date being wrong, but I adjusted the date several times and it wasn't the problem.

I booted live and used gparted and it worked! I adjusted to dual channel in BIOS and everything seems to work ok (I have just booted once, anyway).
This is the way gparted looks:
[IMG]http://img513.imageshack.us/img513/4217/gpartedl.jpg[/IMG]

Swapping partition is not in the same logical drive Ubuntu is. Is this ok?

Thanks for your answer ahmet1916, but my HD is IDE.

---

