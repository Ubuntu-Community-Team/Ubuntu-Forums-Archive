---
title: "How to fix a failed dual-boot?"
date: 2010-12-22
forum: Installation &amp; Upgrades
---

### Post by blenderfox on 2010-12-22
I have Maverick installed, and I wanted to dual boot with Windows 7 (because some apps I want to use only work in Windows, and don't work under Wine)

So I resized my partitions to free up 25GB and installed Windows 7. No problem,but now, I cannot boot into my Ubuntu install, even if I mess around with my boot table via tools such as Bootmanager, PartEd, gPart, etc.

I've reverted to a previous CloneZilla image, so I'm back to where I was, minus about 5 hours.

Before I try this again, how do I make sure I can still boot into my Ubuntu install next time, and how do I make sure that I can also boot into Windows by putting it into the Grub menu?

---

### Post by Quackers on 2010-12-22
If you install Windows it will over-write the mbr of the hard drive.
You should then boot from the Ubuntu live cd/usb and re-install grub to the mbr of the hard drive.
The guide below explains how this can be done. If you have any problems just post back here.

[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by blenderfox on 2010-12-22
> **Quackers said:**
> If you install Windows it will over-write the mbr of the hard drive.
You should then boot from the Ubuntu live cd/usb and re-install grub to the mbr of the hard drive.
The guide below explains how this can be done. If you have any problems just post back here.

[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

Thanks. :) Will do

---

### Post by Quackers on 2010-12-22
The short method may be worth trying first, rather than the full chroot method. You will need to know which is the Ubuntu /root partition. If it's sda1 for instance, the terminal commands would be
```
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

* change sda1 to the number of your own Ubuntu /root partition

---

### Post by wilee-nilee on 2010-12-22
> **momokoyukino said:**
> I have Maverick installed, and I wanted to dual boot with Windows 7 (because some apps I want to use only work in Windows, and don't work under Wine)

So I resized my partitions to free up 25GB and installed Windows 7. No problem,but now, I cannot boot into my Ubuntu install, even if I mess around with my boot table via tools such as Bootmanager, PartEd, gPart, etc.

I've reverted to a previous CloneZilla image, so I'm back to where I was, minus about 5 hours.

Before I try this again, how do I make sure I can still boot into my Ubuntu install next time, and how do I make sure that I can also boot into Windows by putting it into the Grub menu?

You should have grub2 post the output from these 2 commands.
```
sudo fdisk -lu
```
Then this one.
```
sudo grub-install -v
```

---

### Post by blenderfox on 2010-12-22
> **wilee-nilee said:**
> You should have grub2 post the output from these 2 commands.
```
sudo fdisk -lu
```
Then this one.
```
sudo grub-install -v
```

I'm guessing I need to do this from the LiveCD? Bear in mind, I've rolled back to my pre-Windows image, so I'll need to reinstall Windows to try this. I'll try the short method (earlier post) first, then I'll do yours and see what happens.

---

### Post by wilee-nilee on 2010-12-22
> **momokoyukino said:**
> I'm guessing I need to do this from the LiveCD? Bear in mind, I've rolled back to my pre-Windows image, so I'll need to reinstall Windows to try this. I'll try the short method (earlier post) first, then I'll do yours and see what happens.

Well it is really hard to tell where your at to be honest.

You might just stop and get some advice before proceeding, by explaining exactly what is on the computer now.

---

### Post by blenderfox on 2010-12-22
Just so I'm clear. The Live CD we're referring to, are we referring a SEPARATE disc to the installation disc I used to install Ubuntu, or the same one (just running in the Trial Ubuntu mode)?

---

### Post by blenderfox on 2010-12-22
> **wilee-nilee said:**
> Well it is really hard to tell where your at to be honest.

You might just stop and get some advice before proceeding, by explaining exactly what is on the computer now.

Now is just Ubuntu. I installed Windows 7, which messed up my MBR, so I reverted back via an image I took before I install Windows 7. I want to make sure I don't have the same problem this time. That's what I mentioned in the first post.

Summary:

1. Ubuntu (Ubuntu primary boot)
2. Snapshot via CloneZilla
3. Install Win 7
4. Ubuntu + Win 7 (Win 7 primary boot) 
5. Revert back via CloneZilla
6. Ubuntu (Ubuntu primary boot)

So, in order to try your advise, I need to reinstall Windows again. If it fails, I can revert back again.

---

### Post by wilee-nilee on 2010-12-22
So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the # in the reply panel this makes code tags paste all the text in between.

Lets get to the heart of the matter run this script and paste all the text from the generated file in codetags. There are instructions in the 1st paragraph for codetags and in my signature as well.

---

### Post by blenderfox on 2010-12-23
I've booted up using my install disc, and started the live mode. I then did the commands quack suggested:

```
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

And rebooted. It only gave me options to boot into Ubuntu and memtest, so I booted into Ubuntu, then ran update-grub. It found my Windows installation and updated my menu. Now it looks like it's solved. I'm going to snapshot my current laptop state now so I don't have to go through this again.

Thanks for the help.

---

### Post by Quackers on 2010-12-23
You're welcome. Glad things look better now :-)
Please mark the thread as solved using the Thread Tools near the top of the page.

---

### Post by blenderfox on 2010-12-25
> **Quackers said:**
> You're welcome. Glad things look better now :-)
Please mark the thread as solved using the Thread Tools near the top of the page.

Done. Thanks for the help :)

---

