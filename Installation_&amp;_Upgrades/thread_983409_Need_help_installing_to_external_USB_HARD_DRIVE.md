---
title: "Need help installing to external USB HARD DRIVE"
date: 2008-11-15
forum: Installation &amp; Upgrades
---

### Post by ipodk88 on 2008-11-15
hello everyone
im new to the forums, i was hoping you could help me out a little

what im trying to do is install ubuntu 8.10 to a 2.5" external usb HD. once i do this, i want to be able to boot it from my computer (and hopefully on others too?, and use remastersys to create a live CD after i do a bit of modifying.

in the tutorials i have read, they have said that i need to unplug my internal hard drive first.
this isnt an option for me...
anyway around this? and could you provide me with a site with good instructions?


thanks for any help.

---

### Post by Pumalite on 2008-11-15
At step 7 of the installation; go to 'Advanced Tab' and replace (hd0) for '/dev/???' where '???' is your USB. When you finish installing and before reboot; edit your /boot/grub/menu.lst and make 'groot' and 'root' (hd0,0). Then at boot, go into BIOS and make USB first in the boot order.

---

### Post by ipodk88 on 2008-11-15
is there a good website for these instructions?

---

### Post by caljohnsmith on 2008-11-15
Try Herman's website:

[http://www.herman.linuxmaniac.net/p23.html](http://www.herman.linuxmaniac.net/p23.html)

Note on step 7 where it shows a picture of the "Advanced" settings that Pumalite refers to. Just specify /dev/sdb or whichever is your external drive there. If you have any problems getting through that tutorial, be sure to let us know and we'll try to help. :)

---

### Post by Pumalite on 2008-11-15
And this:
[http://www.ubuntuswitch.com/2006/08/01/installing-ubuntu-on-an-external-usb-hard-drive/](http://www.ubuntuswitch.com/2006/08/01/installing-ubuntu-on-an-external-usb-hard-drive/)
[http://ubuntuforums.org/showthread.php?t=614913](http://ubuntuforums.org/showthread.php?t=614913)
[http://ubuntuforums.org/showthread.php?t=614863](http://ubuntuforums.org/showthread.php?t=614863)

---

### Post by ipodk88 on 2008-11-15
you guys are great 
thanks :)
if anything goes wrong ill be sure to some here

---

### Post by Roger Allott on 2008-11-16
I'm trying to do the same thing as ipodk88 except that I'm happy if needed to remove my internal HDD.

My install though is falling over at step 4.

When my internal HDD is there, the only options I'm given are to install to the internal HDD.

When I've removed my internal HDD, I get no options whatsoever.

I know that Ubuntu can 'see' my external HDD as when I plug in the USB connector I get the file browser for the three partitions on it. I can read any file on the external HDD and can write a file to it.

So why can't step 4 of the install see my external USB HDD???

I'm currently on day 3 of trying to work out how to install Ubuntu. Why doesn't anyone make life simple?

---

### Post by caljohnsmith on 2008-11-16
Roger, how about when you have both drives connected, open a terminal from the Ubuntu Live CD (Applications > Accessories > Terminal), and please post the output of:
```
sudo fdisk -lu
```
So I can see if your second drive is even being detected by Ubuntu.

---

### Post by Roger Allott on 2008-11-16
> **caljohnsmith said:**
> Roger, how about when you have both drives connected, open a terminal from the Ubuntu Live CD (Applications > Accessories > Terminal), and please post the output of:
```
sudo fdisk -lu
```
So I can see if your second drive is even being detected by Ubuntu.

Yes, it's definitely finding it. This is the result of that command but with the -l suffix instead of -lu

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x509ee0a7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1530    12288000   27  Unknown
/dev/sda2   *        1530       13567    96685056    7  HPFS/NTFS
/dev/sda4           13567       19458    47314944    7  HPFS/NTFS
Partition 4 does not end on cylinder boundary.

Disk /dev/sdb: 80.0 GB, 80026361344 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x94e494e4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        2010    16145293+   7  HPFS/NTFS
/dev/sdb2            2011        8538    52436160    5  Extended
/dev/sdb3            8539        8610      578340   82  Linux swap / Solaris
/dev/sdb4   *        8611        9729     8988367+  83  Linux
/dev/sdb5            2011        8538    52436128+   7  HPFS/NTFS
```

The 160Gb disk (sda) is my internal HDD and the 80Gb disk (sdb) is the external HDD connected through USB.

---

### Post by caljohnsmith on 2008-11-16
Yes, your sdb1 drive is at least recognized by fdisk, so that's a good sign. When you go through the installer and get to the step where it asks how you want to prepare your disk space, try using the "Manual" option (not either of the Guided optons) and see if you can select the sdb drive. Let me know if that helps, or let me know exactly what problems you encounter; it might also help if you can post a screen shot showing the point where you have problems to clarify things.

---

### Post by Roger Allott on 2008-11-16
> **caljohnsmith said:**
> Yes, your sdb1 drive is at least recognized by fdisk, so that's a good sign. When you go through the installer and get to the step where it asks how you want to prepare your disk space, try using the "Manual" option (not either of the Guided optons) and see if you can select the sdb drive. Let me know if that helps, or let me know exactly what problems you encounter; it might also help if you can post a screen shot showing the point where you have problems to clarify things.

Yes, I've tried the Manual option but when it offers the list of available drives my external HDD isn't there.

I'll have to reboot to retry the install and see if I can paste some screenshots using the image program.

---

### Post by ipodk88 on 2008-11-16
im glad this thread is helpful :)
i forgot to mention im on a laptop, if it matters,
i might attempt an install today.

---

### Post by Roger Allott on 2008-11-16
I'm also on a laptop, but I don't see why that would be important.

This is the screen I get first of all for Step 4 of the install:
[IMG]http://i476.photobucket.com/albums/rr122/Latrax/Step4-1.png[/IMG]

And if I select the "Manual" option, this is what I get:
[IMG]http://i476.photobucket.com/albums/rr122/Latrax/Step4-2.png[/IMG]

---

### Post by caljohnsmith on 2008-11-16
That is really strange, Roger, that the installer doesn't seem to recognize your sdb drive at all. Sounds like it could be a bug with the installer. The only other thing I can think of is maybe if you change the way your sdb drive is setup in BIOS, that might fix the issue. Otherwise, I think I would file a bug at bugs.launchpad.net, because that's definitely a bug that should be fixed (if it really is a bug).

---

### Post by Roger Allott on 2008-11-16
> **caljohnsmith said:**
> That is really strange, Roger, that the installer doesn't seem to recognize your sdb drive at all. Sounds like it could be a bug with the installer. The only other thing I can think of is maybe if you change the way your sdb drive is setup in BIOS, that might fix the issue. Otherwise, I think I would file a bug at bugs.launchpad.net, because that's definitely a bug that should be fixed (if it really is a bug).

Well it's useful to know that it's probably a bug and not me or my system going bonkers!

I've tried creating a bug report in launchpad and I put in that the Distribution is Ubuntu and the Package is 8.10, but I'm getting the error message:
```
There is no package name '8.10' published in Ubuntu
```

WTF????

---

### Post by ipodk88 on 2008-11-16
is it possible to only have 2 partitions on my external drive (one for ubuntu, one for storage space for use with windows?)

---

### Post by Pumalite on 2008-11-16
You might get away with it. Also; if you already have a /swap partition in your internal drive; your USB can use it.

---

### Post by ipodk88 on 2008-11-16
sorry, i didnt really understand what you were saying..
its brand new, so i dont think theres any partions on it,
if i wanted to create 2 (1 for ubuntu, one for windows) would there be an option for this during the install?

---

### Post by Pumalite on 2008-11-16
Sure.

---

### Post by ipodk88 on 2008-11-16
i have another question for you guys, 
cant i just run a wubi install, and select the external drive as the HD to install to?
and would this work if i wanted to use remastersys eventually?
thanks

---

### Post by Roger Allott on 2008-11-17
What the heck is a 'wubi install'?

---

### Post by ipodk88 on 2008-11-17
an install where no partitioning is needed.
im guessing it would work..

---

