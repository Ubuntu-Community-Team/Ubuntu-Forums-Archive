---
title: "Bootmgr is missing - USB install"
date: 2013-04-08
forum: Installation &amp; Upgrades
---

### Post by scordes on 2013-04-08
Hi everyone - really need some help with something that I should be able to sort myself but no amount of forum browsing is helping.

I have just finished building the first of a number of computers made from second hand and randomly collected parts which will form a render farm for autodesk maya. Working on an extremely tight budget I will be using ubuntu and installing maya onto that and just using the backburner to run on the other machines. Now I am having real problems installing ubuntu via USB onto the PC (there is no optical drive). I have a newly formatted 40gig hard drive and have set the boot order in the BIOS to USB first and all I am getting is the bootmgr is missing error.

I have built PCs in the past and successfully installed windows so I am 99% sure that I have my system set-up correctly however there may be some 'trick' I need to do for ubuntu. Would really appreciate your help. I can't afford to buy many copies of windows!

Steve

---

### Post by C.S.Cameron on 2013-04-08
Welcome to the Forums.

What program did you use to install Ubuntu to the USB?
I prefer Startup Disk Creator or UNetbootin.
Did you check the MD5SUM of the iso.
Some bios see Flash drives as just another drive, so in BIOS the flash drive is set as first HDD and the BIOS is then not set to boot USB first.
Some older computers will not boot flash and then you need something like Plop boot manager.
Some newer computers with Secure Boot find it hard to dual boot flash.

---

### Post by scordes on 2013-04-08
Thanks for the reply. I used universal usb installer from the ubuntu website. 

I'm afraid I don't know what MD5SUM is so I can't answer that.
I think the boot order is right as I set it to cd-rom and harddrive with no media in and got the 'disk boot failure - insert system disk' message.

---

### Post by mpenney on 2013-04-08
Did you format the Flashdrive?

---

### Post by scordes on 2013-04-08
Yes I did. Everything the USB and the Hard-drive has been freshly formatted.

---

### Post by C.S.Cameron on 2013-04-08
MD5SUM will tell you if the downloaded iso is corrupt, ie a bad download.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Lots of people have had problems with Universal.

Have you tried the flash drive on another computer

---

### Post by oldfred on 2013-04-08
If it is a bootable flash drive your BIOS should see it as a bootable device. Some may show it as another hard drive, not in the list of USB devices to boot.
If you do not have USB as a choice your system may not boot from USB devices. If less than 6 years old it should boot from USB.

Bootmgr missing is from hard drive as that is a Windows error.

---

### Post by scordes on 2013-04-09
thanks everyone for the replies. I will check with MD5SUM tonight on Friday as I am away with work until then. I downloaded the ISO from the ubuntu page but I guess things can always go wrong.  I will also try another USB installer you recommended above.

The bios lets me choose USB-FDD and various other USB options but none work. At the moment I only have my big-rig workstation and my laptop to test and I don't really want to mess around with my rig as if anything goes wrong I could miss a clients deadline. How do I test it on my laptop without screwing up what's already on there?

Thanks and sorry to sound such a noob! I am so used to just putting a windows CD in and letting it work!

---

### Post by oldfred on 2013-04-09
My system had many USB settings like the USB-FDD and originally I tried all of them, nothing worked. I tried flash drive on my laptop and it worked, so I know it was good. I just about gave up. But I had it plugged in and since I have multiple hard drives went into the list to change which drive I boot from and there it was. It is often listed as a hard drive choice not a USB choice. And it boots like another hard drive. I put a full install into my 16GB flash drive and it boots as another hard drive only a bit slower.

You should be able to boot and have two choices. One is install and the other is live mode. You should always use live mode to test that everything works and you start to understand some of the differences of Ubuntu. It will not be fast since running from flash drive, but most once loaded is cached in RAM so it runs well once started up.

Depending on video you may also need boot parameters. I have nVidia and have to add nomodeset on every live mode boot and first boot after install or until I install the nVidia drivers.

---

### Post by C.S.Cameron on 2013-04-09
So where can I find Maya 2013 for Linux?
I don't see it on the Autodesk demo site.

---

### Post by scordes on 2013-04-12
Thanks everyone I have used a different installer as recommended above and switched around the boot options and I am now at the front end of the USB installer and it is installing nicely. Many thanks for all your help. I will report back once I have a fully operational machine!

---

### Post by scordes on 2013-04-12
Wooohooooo it's worked. Thank you all for your help.

Steve

---

