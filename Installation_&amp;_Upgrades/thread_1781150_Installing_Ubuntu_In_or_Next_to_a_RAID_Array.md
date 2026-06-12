---
title: "Installing Ubuntu In or Next to a RAID Array"
date: 2011-06-13
forum: Installation &amp; Upgrades
---

### Post by Sparkssss on 2011-06-13
I am very eager to try and maybe even stay permanently on ubuntu, so i went ahead and burned my disk but it seems i have come up against a problem. After having spent hours searching these forums without results i decided to start my own thread.

I have the common issue, that i have a RAID 0 array.

Currently I have 2x500GB HDD's in RAID 0, and out of that 1TB i formed 2x500GB partitions, so that i basically had two fast partitions with no space gain. I also have a 1TB HDD that is not in an array with any other disk but has been divided into 2 partitions.
Originally i wanted to install ubuntu onto the empty RAID 0 partition (Windows 7 is on the other) but it seems that is not at all an option. So then i thought why not install ubuntu on the second partition of the 1TB HDD, so i went ahead and did that but now it seems after i have installed it i could not access it and also after a few tries my windows 7 boot manager stopped working so i had to repair that too.

Now I am wondering if there is anyway i can solve this? My original idea was to install ubuntu and get it to "ignore" windows 7, so that neither interfered with the other's boot manager, but i cant see how to do that as my own knowledge of that is rather limited. If anyone has any good ideas dont hesitate to suggest them please ;)

---

### Post by jake.anq on 2011-06-13
Hi

The first thing to try is to access your BIOS and change the boot priority to the 1Tb disk.  This process varies greatly between makes and models of computers but it should be under something like 'boot order'.
Try to set it to:
CD/DVD
1Tb HDD
Raid disks.

After doing this, you should get the Grub boot loader appearing.
If this fails, try running the[**B**oot-info]("http://bootinfoscript.sourceforge.net/") script from a livecd/usb and post the output here.

---

### Post by YesWeCan on 2011-06-13
Hi there. When you say you have a RAID0 array what do you mean? Did you create this array using Ubuntu?
AFAIK Grub2 version 1.99 can directly boot a RAID0 array.
You can find your Grub version with [COLOR=Navy]grub-install -v[/COLOR]

The way grub works is that it overwrites the standard MBR at the start of a disk and it needs files that are inside the Ubuntu root partition in order to present you with a boot menu.

The Ubuntu installer is tragic in its stupidity IMO because it defaults to installing the Grub MBR on sda regardless of which disk you choose to put Ubuntu on and there is no explicity warning and many folks miss this. Normally, if you put Ubuntu on its own disk (not the Windows disk) it is sensible to install Grub MBR to the Ubuntu disk. Then you can set your bios to boot the Ubuntu disk directly. This avoids any future issues when Windows overwrites the MBR on its own disk.

---

### Post by psusi on 2011-06-13
What do you mean installing it on the raid array is not an option?  It sounds like you have a bios fakeraid and installing Ubuntu to the unused partition on it will work just fine.

---

### Post by Sparkssss on 2011-06-14
I created the array in the bios, my motherboard (EVGA P55 FTW 200) allows me to do this. I have no idea if it is a fakeraid or not, but when i tried to install ubuntu to the empty partition it never actually listed the disks that are in the raid array, and when i tried using wubi to install it on the raid array it just never got through a full install. Setting the 1TB HDD to a higher boot priority then the raid array makes sense to me though, so i will go ahead and try that next weekend.

---

