---
title: "installed eeeubuntu on eee pc 900a and wont boot without usb drive~"
date: 2008-11-09
forum: Installation &amp; Upgrades
---

### Post by mustangsvo on 2008-11-09
i installed eeeubuntu to my new eee pc 900a i got yesterday. after i installed it, rebooted, took the usb drive out. and it wont boot without the drive? What did i do? im new to linux so try to explain it so ill understand lol. thanks! instant message me at [email]patckc88@aol.com[/email]

---

### Post by Topsiho on 2008-11-09
Try putting the usb stick back in, then boot, and if the boot now succeeds, only remove the stick after right clicking on it's icon, and then choose to safely remove it in the menu list.
My guess is that you just took it out, and that when rebooting, the system expects to find it and it doesn't.

Success,

Topsiho

---

### Post by mustangsvo on 2008-11-09
I just booted into eeeubuntu. Will not let me do anything with this damn usb drive. I tried to reinstall differnet OS's on the eee but it wont let me.

---

### Post by mustangsvo on 2008-11-09
i just installed eeeubuntu to my eee pc and when i took the usb drive out and rebooted my laptop, it wont boot to anyhitng, but when i put my usb drive in it booted fine. what did i do? Im new to linux so try to make things simple for me please?

---

### Post by mustangsvo on 2008-11-09
Ok. no matter what i do, the eee will not boot to anything. it will not do anything besides boot from the usb drive with eeeubuntu on it. i dont know what i did. Is there anyway to just wipe the 4gb ssd clean and start over from nothing?

---

### Post by mustangsvo on 2008-11-09
Earlier I booted eeeubuntu from a usb drive and i loved it alot. So i went along with the install. after it rebooted, The eee will now only boot from the usb drive. I tried getting it to do it without it in, but when i choose the SSD drive it just says disk not exsistant or something along those lines. I do not have a usb dvd drive so i can not formant xandros back on it. I have no idea how to just get eeeubuntu or eeexububtu to the SSD drive. I have no idea what to do someone please help! Its pretty much unusable now!

---

### Post by Topsiho on 2008-11-10
I am sorry to see you are still stuck. But I still think that you took out the usb stick without having it removed safely from the file system. You can not do this in Windows, and you can't do it in Linux either.

When booting the system thinks it is still there, but can't find it, and gets confused, probably keeps on searching until .... 

So put your usb stick back in, boot the computer, and then safely remove the usb stick.

If this doesn't help, I can not help you further.

I have an Acer Aspire One, which is largely similar to your eeepc (which I would have bought but for the fact that in my country it is only available with Windows XP installed). Installing Ubuntu (8.04.1 and 8.10) from a usb stick just went very smoothly, so you should be able to do this too :)

Topsiho

---

### Post by C.S.Cameron on 2008-11-10
On earlier issues of 8.10 the installer was having problems telling which flash drive was which when installing from flash to flash, this was cured using uuic in menu.lst.
Suggest you confirm if the installer is seeing your EEE drive as sda or sdb, and point to this for your boot loader in the last screen of the install process.

---

### Post by colindente on 2008-11-11
You should find that if you hold F9 while rebooting your eee PC you'll get an option to restore Xandros from the "Hidden" partition on the SSD.

---

### Post by help me plz on 2009-11-20
can u help me, i just brought a new eee PC 900a and my friend did something and now i don't understand why it wont log in for and hour or so and still it wont work when ur in, it just freezes. i think it might have a virus, **PLEASE HELP ME!** EMAIL:corey2704@hotmail.com](*,)

---

