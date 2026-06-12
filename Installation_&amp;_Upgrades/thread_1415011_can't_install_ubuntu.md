---
title: "can't install ubuntu"
date: 2010-02-24
forum: Installation &amp; Upgrades
---

### Post by someone235 on 2010-02-24
I have an xp on my pc, and I want to install ubuntu.
I have a disk of v9.04, and a usb-stick with 9.10.
Nor the usb-stick nor the cd are booting.
If I use at the CD the windows' installer, When I restart I arrive to ubuntu command line.
How can I install it?

---

### Post by darkod on 2010-02-24
You need to go into the BIOS and make sure CDROM, or USB, or both, are before HDD in boot devices. It sounds like the pc is booting straight from your hdd. You need to tell it to boot from cd or usb first.
Then when you insert bootable cd or usb stick it will boot from it.

---

### Post by someone235 on 2010-02-25
I have some USBs in the BIOS:
USB-ZIP
USB-HDD
USB-CDROM
Which of the I need to choose?

---

### Post by MelDJ on 2010-02-25
if you want to install through usb try USB HDD. 
if that doesnt work, install from cd by changing the BIOS to boot from cdrom

---

### Post by darkod on 2010-02-25
> **someone235 said:**
> I have some USBs in the BIOS:
USB-ZIP
USB-HDD
USB-CDROM
Which of the I need to choose?

Yes, USB-HDD. Even if you are using usb stick, not usb hdd, it goes under the category USB-HDD.

---

### Post by Arkasai on 2010-02-25
I'm having a similar issue getting ubuntu 9.10 installed from my USB storage as well.  I can get to the boot menu but none of the options work.  I get an error ```
Cannot find kernel image: /casper/vmlinuz
```

I used pendrivelinux.com's tool to set up the usb, they rolled in casper rw recently and I think it may be the cause of the error.  I did not specify persistence when I set it up, since I simply want to use the usb to install the OS.

---

### Post by someone235 on 2010-02-27
OK, I've tried any version I could of Ubuntu (7.10-32bit-CDROM, 9.10-32bit-USB,9.10-64bit-USB,9.04-32bit-CD)&#1509;
In all the versions my installation is getting stuck in the beginning.
what can I do????

---

### Post by darkod on 2010-02-27
> **someone235 said:**
> OK, I've tried any version I could of Ubuntu (7.10-32bit-CDROM, 9.10-32bit-USB,9.10-64bit-USB,9.04-32bit-CD)&#1509;
In all the versions my installation is getting stuck in the beginning.
what can I do????

Can you be more specific about what is happening? When you boot from cd or usb, do you get the main ubuntu menu successfully?
If yes, did you try selecting Try Ubuntu and what happens after that?

---

### Post by macorro on 2010-02-27
Also unable to install Ubuntu 9.10 from downloaded and burned CD. 

Replacing my HDD, Laptop would not recognise Desktop CD as valid. Had altered Boot options to 
1. Changed USB CD-ROM to first place and optical disk drive to second
2.Leave multiboot and CD-ROM boot both enabled. HDD is fifth on the list, with optical disk drive and USB CD-ROM being now being first and second
3. Disabled multiboot and leave only CD-ROM boot enabled

Have reinstalled Window XP in the hope that imagined missing drivers would be installed and to prove the CD drive was working. XP installed fine.

Power up with install CD in place which is now ignored irrespective of boot order.

Out of ideas. Please help!

---

### Post by darkod on 2010-02-27
> **macorro said:**
> Also unable to install Ubuntu 9.10 from downloaded and burned CD. 

Replacing my HDD, Laptop would not recognise Desktop CD as valid. Had altered Boot options to 
1. Changed USB CD-ROM to first place and optical disk drive to second
2.Leave multiboot and CD-ROM boot both enabled. HDD is fifth on the list, with optical disk drive and USB CD-ROM being now being first and second
3. Disabled multiboot and leave only CD-ROM boot enabled

Have reinstalled Window XP in the hope that imagined missing drivers would be installed and to prove the CD drive was working. XP installed fine.

Power up with install CD in place which is now ignored irrespective of boot order.

Out of ideas. Please help!

It might be the image got corrupt during download.
Did you make sure you created the CD correctly, you didn't just burn the image file on it as a file right?
And it should be burned at 8x or 4x, not more.
You can also try if you can boot the cd in another computer if you have one.

---

### Post by someone235 on 2010-02-28
> **darkod said:**
> Can you be more specific about what is happening? When you boot from cd or usb, do you get the main ubuntu menu successfully?
If yes, did you try selecting Try Ubuntu and what happens after that?
I have the menu, and I choose "Install Ubuntu" or "Try Ubuntu", and then I have a progress bar, and when it is something about 80%, it is getting stuck (I've waited more than one hour).
The same thing occurs in any version of ubuntu, even those I requested by mail (the original ones).
any suggestions?

---

### Post by macorro on 2010-02-28
Darko,

Thanks for your support! Great to know someone is out there when helpis needed!

Downloaded the Ubuntu recommended CD burn software and Ubuntu loaded fine. Perhaps my existing burn software did not properly recognise the nature of the ISO file.

Regards

[IMG]http://ubuntuforums.org/images/icons/icon7.gif[/IMG]

---

