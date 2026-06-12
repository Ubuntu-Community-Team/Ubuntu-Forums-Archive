---
title: "Help me choose an OS besides 12.04 due to my machine"
date: 2012-06-08
forum: Installation &amp; Upgrades
---

### Post by whowinsdares on 2012-06-08
Hi all,
 
A kind man gifted me a Toshiba Tecra A1 a week ago, which is running windows XP professional SP3 **very slowly**, and no MS Office.
 
I desperately need to be running Open Office on a fresh install for work I need to do ASAP. So I downloaded:
 
ubuntu-12.04-desktop-i386.iso
 
...and got the message...
 
This kernel requires the following features not present on the CPU
 
Pae 
 
Unable to boot - please use a kernal appropriate for your CPU
 
Could someone please recommend an OS - an earlier version of Ubuntu assumably that I can install off a USB drive I bought for the purpose today?
 
I am in hospital and dont have acess to anything besides a USB wireless internet modem, the Lap top, and the flash drive. I also have the - 
ubuntu-12.04-desktop-i386.iso on a CD I bought, which is also on ISO on the desktop of this machine.
 
I am in hospital for a bad leg infection, I been here for 2 weeks and going to be here for another 2 weeks. I've had 2 surgeries under general anesthetic and will be having at lease 1 more (skin grafts).
 
I need to be emailing perfect documents by next Tuesday. Could someone please help me I don't want to do this on my own. I got a bit of money and can get to a computer store if I need but I cant really afford much.
 
Many thanks in advance!!
 
Ben from Perth Western Australia

---

### Post by wojox on 2012-06-08
Did you try the [non-pae iso]("http://people.canonical.com/~diwic/12.04-nonpae/")?

---

### Post by snowpine on 2012-06-08
Is this your computer?

[http://reviews.cnet.com/laptops/toshiba-tecra-a1-15/1707-3121_7-30566387.html](http://reviews.cnet.com/laptops/toshiba-tecra-a1-15/1707-3121_7-30566387.html)

Pentium 4 is a decent processor, but if you have the bare minimum 256mb RAM, your options are limited. If you have 512mb or 1gb RAM then *maybe* you can run Ubuntu. At this very moment I am running Ubuntu 12.04 with a few browser windows and a blank document in LibreOffice Writer, and I am using approximately 500mb RAM (out of 2gb total).

Lubuntu is a "lightweight" Ubuntu that will probably give you much better performance on this very old computer: [http://lubuntu.net/](http://lubuntu.net/)
Be sure to read [the Help pages]("https://help.ubuntu.com/community/Lubuntu/GetLubuntu"), because even lightweight Lubuntu considers anything under 600mb "low RAM" requiring a special installation procedure.

---

### Post by Dragonbite on 2012-06-08
I get that message with my IBM Thinkpad T42 as well.

Ubuntu includes the PAE in the kernel and if the system does not inlcude it, as older computers don't, it won't boot. I haven't heard of any boot commands to set which will bypass this.

So to install Ubuntu 12.04 you need to use an "alternative" kernel, which unfortunately does not come in a LiveCD version (instal only).

The good news is that Xubuntu and Lubuntu are shipped without this piece so they run perfectly fine in a Live environment and installed.  I have Xubuntu installed on my previously-mentioned Thinkpad without any issues.

So you can install either the non-PAE alternate full Ubuntu 12.04, install the alternate and then install unity (or whatever), or install Xubuntu or Lubuntu.

---

### Post by OpenSourceRules on 2012-06-08
I'm not trying to be mean, but even 512MB of RAM is not likely to get you anywhere; even a browser and things that run in the background take about 300MB of RAM.

It may be time to recycle your computer for a new one.

---

### Post by Penguinnerd on 2012-06-08
Nonsense. No need to recycle the PC yet.

Download Lubuntu. It will work.

---

### Post by Dragonbite on 2012-06-08
Yes, 512 Ram is low compared to modern standards, but it is still sufficient.  I would definitely look at Lubuntu and Xubuntu and ways to "trim the fat".

That being said, any upgrade in RAM will provide a noticeable improvement.

---

