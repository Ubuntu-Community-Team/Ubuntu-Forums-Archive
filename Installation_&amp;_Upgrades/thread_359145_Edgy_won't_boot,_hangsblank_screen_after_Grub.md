---
title: "Edgy won't boot, hangs/blank screen after Grub"
date: 2007-02-11
forum: Installation &amp; Upgrades
---

### Post by PillowFightin on 2007-02-11
I just installed Edgy on a small-form factor Dell, an Optiplex GX60. It was running mostly fine until I installed Tux Paint last night (am a newbie and not very good at installing .deb files yet, so I hope I did it right). Now it won't boot into Ubuntu at all. It will load the GRUB words, then I get a blinking cursor, and after that just a black screen and absolutely nothing. 

Dell specs (so far as I know it) are: 

1.7 Celeron
256MB RAM (I was planning on upgrading this)
CDRW

I have no clue how to troubleshoot this. Help? Thanks kindly for any ideas...

---

### Post by geek_Man on 2007-02-11
Okey dokey, can you post your menu.lst file please? The path is /boot/grub/menu.lst. Just post the file's contents and I'll have a look. Also, can you post the output of "fdisk -l"?

---

### Post by PillowFightin on 2007-02-13
Forgive me, but I am truly a newbie...can you post the exact command lines, or direct me to a place that has specifics? I have tried a few things and haven't gotten anywhere.  :(

---

### Post by geek_Man on 2007-02-14
Okay, boot with the live CD, go into a terminal and type "gedit /media/name_of_drive/boot/grub/menu.lst". The name_of_drive is just whatever drive you have Ubuntu installed on (that drive should show up on your desktop, mine was usbdisk, although yours should be different). So then you just copy and paste the contents of that file into your post. Then type "sudo fdisk -l" into the terminal and post whatever that says. Hope this helps.

---

### Post by PillowFightin on 2007-02-15
Strangely, I get a completely blank screen for menu.lst. I tried both hda0 and hda1, and I don't know what else to try. Either way what gedit shows me is just blank. I installed clean and have no dual-boot or anything, so I don't know where else things would be.

Here's is what I get for "fdisk -l":


```
Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       14501   116479251   83  Linux
/dev/hda2           14502       14593      738990    5  Extended
/dev/hda5           14502       14593      738958+  82  Linux swap / Solaris

```

---

### Post by geek_Man on 2007-02-15
Ah, hda doesn't work. If you open Nautilus, look to the left side of the window and there are couple shortcuts. Double-click the one that says "filesystem". Hopefully you'll see a bunch of folders like "bin", "var", "dev", and "media". Look for the one called "media", double-click that folder and you'll see some hard drive names (mind you, not hda or sda, but names like "DELL_HARDDRIVE" or "firewiredisk"). Figure out which drive is the one that has Ubuntu installed on it and replace "name_of_drive" with that drive name.

And do you have two drives or one? If you have two drives you have to type "sudo fdisk -l" not just "fdisk -l". If you have only one drive then disregard that last part.

---

### Post by PillowFightin on 2007-02-15
I am sorry...but even browsing through Nautilus yields nothing. It shows absolutely nothing inside the media folder. Am I supposed to be logged in as root or something first?

Just one hard drive. (This thing will never be able to have more than that due to its tiny size).

If it helps,this install is only a few days old so I don't mind reinstalling if that's going to be the end result anyway...

---

### Post by PillowFightin on 2007-02-16
Ok, before you go to any more trouble on my behalf...I got impatient and did a Boot and Nuke. I think I will just try a reinstall and go back to Dapper. Dapper seemed a little less touchy! Then I'll upgrade to FF when it's out.

Thanks kindly for all your help...I hope to get better at this soon!

---

### Post by geek_Man on 2007-02-16
Okay, sorry I couldn't help.

---

### Post by rosieg on 2007-02-16
Are you sure your computer is hanging i.e. does the hard drive light stop flashing?

On my computer the initial splash image thing doesn't work so when I turn it on, it boots up with a blank screen with  cursor, then the cursor goes away and I wait....and wait... thenit goes to the login screen.

---

### Post by PillowFightin on 2007-02-18
Hi,

No, it was definitely MIA...I reformatted and installed Dapper and thankfully have none of these problems now!

---

