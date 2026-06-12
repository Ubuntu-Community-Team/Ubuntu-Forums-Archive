---
title: "black screen after 10.10 install"
date: 2011-02-10
forum: Installation &amp; Upgrades
---

### Post by JanvL on 2011-02-10
Hi,

I have rebuild my system, with an 
Asus motherboard M4A88TD-V EVO/USB3 with radeon 4250 integrated
8 Gb memory
Athlon II 4x 640
2 x 1 TB sata3 WD Harddisks

I installed 10.10 64bit, and ran through the whole install with the alternate CD without problems, Installed grub in the MBR on the 120 Gb partition for 10.10, it even recognised my 2 3ware pci raidcontroler on which 8.04 is installed.

When I start I get grub, when I choose for 10.10 I get a black screen with a cursor blinking in the left uppercorner. Luckily I can start into 8.04.

I have no idea how to continu.
for now I will burn a knoppix cd so I can read the ext4 partition with 10.10 and hope to find something to solve this.

Glad for any help,
Jan

---

### Post by P4man on 2011-02-10
Try booting with nomodeset. See the link in my signature if you need help with that ->

---

### Post by JanvL on 2011-02-10
Hi and thanks

at least I see something now, but it will not start.
I tried with nomodeset and with noacpi but after recognising the drives, HD's and DVD-drives the system hangs

I also gave noquiet and nosplash so i see what is happening.

Any other ideas, please .  .

Kind regards,
Jan

---

### Post by P4man on 2011-02-10
Go in to your bios, see if you have settings for the sata controller. Try changing them (ECHI/compatibility mode). if the kernel hangs at the dvd drive, can you disconnect it and see what happens?

---

### Post by JanvL on 2011-02-10
Thank you for your advise.

After I unplugged both optical drives (EDI-flatcable and power) the system started,
Even without changing the boot-options in grub.

I do not understand how I was able to install 10.10 through such an optical drive that now blocks the system, curious. Both drives are pretty old so maybe I should get a sata DVD rw instead.

First I got loads of updates and then I started to download all the software that I use, that takes some time loading and installing a couple of Gb over the internet, my connection is not the fastest.

I want to use KDE, on top of Gnome, that seemed to give the most stable system on 8 and 9 versions, now I am just struggeling a bit to get KDM when the system starts.

So I can put solved in the thread thanks to you.

Kind regards,
Jan

---

### Post by P4man on 2011-02-10
> **JanvL said:**
> Thank you for your advise.

After I unplugged both optical drives (EDI-flatcable and power) the system started,
Even without changing the boot-options in grub.

I do not understand how I was able to install 10.10 through such an optical drive that now blocks the system, curious. Both drives are pretty old so maybe I should get a sata DVD rw instead.

Thats odd. Ive seen SATA optical drives cause problems, often cured by changing sata mode in the bios, but Ive never seen an IDE device block boot. Oh well, glad you figured it out. Perhaps try reconnecting the drives one by one, see which one is the offending one, and perhaps look for a firmware upgrade for that drive.
> 
I want to use KDE, on top of Gnome, that seemed to give the most stable system on 8 and 9 versions, now I am just struggeling a bit to get KDM when the system starts.

Eck. Mixing gnome and kde is not something that increases reliability.. it just causes a bit of a mess and doubles the amount of updates you'll get. If you want to run KDE, you should have installed Kubuntu.

Anyway, to choose gdm or kdm, just run

```
sudo dpkg-reconfigure gdm
```

Then you can select the KDE or gnome greeter as default one.

---

### Post by JanvL on 2011-02-10
Hi,

I also changed sata mode, forgot to mention, but only after I unplugged the drives the machine booted.

I have run 8.04 with a mix of KDE and Gnome software without trouble.
I like Quanta which is KDE but I also like synaptic that is Gnome.
Most software I use is not specific for either one, like Gimp, Inkscape, Xara LX and OpenOffice.

For webdesign/programming I need Apache/PHP/MySQL to test on localhost.
The jump from a Pentium 4 2.6 Ghz with 1 Gb memory to this Athlon 4 core with 8 Gb memory is a leap forward in time.
I am just waiting for an afforable sata3 hardware raidcontroller, I do not like software raid.

kind regards,
Jan

---

