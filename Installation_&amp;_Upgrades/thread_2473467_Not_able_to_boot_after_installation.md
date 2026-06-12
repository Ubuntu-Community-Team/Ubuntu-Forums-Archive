---
title: "Not able to boot after installation"
date: 2022-04-05
forum: Installation &amp; Upgrades
---

### Post by smhardesty2 on 2022-04-05
I downloaded Lubuntu 20.04.4 because I'm looking for an LXDE or LXQT distro. I seem to be having problems with the install. 

I was able to run the DVD Live and after looking around just a little I decided I'd like to install it to the hard drive and try it out for a while. The install seems to go well, but when I reboot after successful install, all I get is a strange looking boot screen. It looks a lot like the boot screen I get when selecting F12 during boot up, but is larger and includes a new entry named, "ubuntu". I have tried selecting every option on the boot priority screen and all it does is return me to the same boot screen. I checked the BIOS and there is, in fact, a new entry named ubuntu. I'm not sure how that happened and I can not remove it from the BIOS.

So, what am I doing wrong? I have my BIOS set to legacy with the optical drive first then the hard drive. Do I need to change to UEFI settings in the BIOS or is there some other problem I have? Any help will be appreciated.

---

### Post by oldfred on 2022-04-05
If UEFI system, often better to use UEFI. Only some old early UEFI from 2012 & 2013 often needed BIOS boot. And some systems just want to boot Windows.

What brand/model system?
What video card/chip?

Please copy & paste the pastebin link to the Bootinfo summary report ( do not post report), do not run the auto fix till reviewed.Lets see details, use ppa version with your USB installer (2nd option) or any working install,  not Boot-Repair ISO
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)            
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by ActionParsnip on 2022-04-05
Is this a single boot system or are you dual booting with Windows?

---

### Post by smhardesty2 on 2022-04-05
Sorry. I had to run to the dentist this afternoon. I just now popped back in here. It's a single boot install. I don''t dual boot anything anymore. I haven't been on a Windows computer in 20 years and my wife hasn't used Windows in 15 years. We're strictly a Linux family. I always partition the hard drive the same way. I set an 8 GB swap area, a 20 GB root partition, then the rest of the hard drive is set to /home. In this case it's a 1 TB HDD.

Here are the specs of the laptop I'm trying to get Lubuntu installed on.

Lenovo G51-35
AMD A8-7410 quad core
8 GB RAM
1 TB HDD
Radeon R5 graphics
Kabini HDMI/DP audio
Realtek RTL8723 wireless adpater
Realtek RTL8111 gigabit Ethernet
PLDS DVD-RW optical drive
Blackweb wireless Bluetrace mouse

---

### Post by ActionParsnip on 2022-04-05
If its a single boot then disable secure boot and you'll have an easier time

---

### Post by smhardesty2 on 2022-04-05
I have my BIOS set to Legacy support with the optical drive first on the list and the hard drive second. I still get what appears to be a boot selection menu. It's not the boot menu from the Lenovo laptop. It's a lot like that menu, but it's definitely different and it now has that ubuntu choice which was actually added to the BIOS menu. I can not remove that option. I can not get past the boot menu. Regardless of which option I choose, it simply blinks then t=I'm right back at that menu. I simply can not boot.

If it helps anybody, I did try to install EndeavorOS on the same laptop and I received that same boot menu.

---

### Post by yancek on 2022-04-06
Get the boot repair script suggested in post 2 above.   You can use the Ubuntu live system to do it and use the 2nd option explained on that page.  That should give enough informatiom on the system for someone to make suggestions to help you boot.

---

### Post by tea for one on 2022-04-06
> **smhardesty2 said:**
> If it helps anybody, I did try to install EndeavorOS on the same laptop and I received that same boot menu.

It would be very helpful if you could supply the information from the boot-repair report suggested by oldfred in post 2.

Edit: A bit slow off the starting blocks.

---

### Post by smhardesty2 on 2022-04-06
Thanks for the replies, guys. I think I'm just going to pass on jumping through all the hoops to get an install working. I have since found two different LXQT distros that will suit my needs. Both of the other distros install without any snags. I'll be trying each of those two out over the next few days before I decide on which of them to implement as my daily driver.

---

