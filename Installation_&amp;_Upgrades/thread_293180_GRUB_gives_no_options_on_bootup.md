---
title: "GRUB gives no options on bootup"
date: 2006-11-04
forum: Installation &amp; Upgrades
---

### Post by micahphd on 2006-11-04
Hey Everyone,

I've spent some time poking about in these forums trying to find a solution for this but I'm not coming up with anything.  Also, I'm definitely a Linux newb.  I've been using Windows forever but decided it's about time to get out there and learn Linux (and I'm lovin it so far).  So here's the lowdown:

I installed Edgy from scratch on my laptop.  I love it and it runs just fine.  I realized though that I need to get Windows dual-booting on here too for the sake of some beloved computer games =)  I found a number of how-to's that I read up on but all of them showed how to add Ubuntu to a system that already has Windows (I'm doing it the other way around since I already have Ubuntu installed).  So I decided to try anyway.

I have a 100GB HD on my laptop that I partitioned for Ubuntu.  So I wanted to take that and shrink what was being used and put Windows on the rest.  I booted into the Ubuntu 6.10 Live CD and used GParted to shrink the Linux partition to 30GB.  I thought I read somewhere that Windows had to be at the front of a drive but being as I couldn't find the same article and couldn't find anything else saying the same thing, I decided to proceed.

I then installed Windows on the remaining 60+GB.  As expected it booted into Windows without any issue (having overwritten GRUB as the Windows master boot record).  So far so good.  Then I booted back into the Ubuntu 6.10 Live CD to reload GRUB (this all following a couple how-to's I read and a friend's advice).

Once I rebooted it went straight into my pre-existing Ubuntu build (that which is still running fine and I'm on right now).  So my problem is that I was fully expecting options from GRUB once I reinstalled it but there was no choice, it just went straight into Ubuntu off the hard-drive.  Here's my current partition layout:

/dev/sd1 (ext; 29.43GB)
(Unallocated; 6.46MB)
/dev/sd2 (ntfs; 60.83GB)
(Unallocated; 3.69MB)
/dev/sd3 (Extended; 2.89GB)
  /dev/sd5 (linux-swap; 2.89GB)

Anyone have any advice as to what I can do to get GRUB to recognize both my Ubuntu and Windows partitions?  I don't have much experience with GRUB so I'm not sure what I could do to get it to give me some options.  Any help would be appreciated.

Thanks in advance for your time and help!

---

### Post by bulldog on 2006-11-04
Try to hit ESC before Ubuntu boots,I think you have GRUB hidden. 

Go into your menu.lst and see if windows is listed.

```
gksudo gedit /boot/grub/menu.lst
```

Place a # before the hidden option to see GRUB at boot time```
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

```

---

### Post by micahphd on 2006-11-04
Thanks for the suggestion.  I actually just got back from a reboot after doing that and saw your message.  I hashed out "hidden" only to see that my only options through GRUB were Ubuntu.  So it looks like GRUB doesn't even see Windows installed on the other partition.

I'm going to keep poking around in these GRUB settings to see if there is something missing that I have to point it to all partitions or something to boot from,  My guess is that GRUB wasn't giving me options because it never saw Windows but if it had it might have automatically disabled the hidden option.

---

### Post by bulldog on 2006-11-04
Can you give the output of```
sudo fdisk -l
``` l as in like
So we can see which partition is listed for your windows install.

If we now that we can easely put windows into your menu.lst.

```
### END DEBIAN AUTOMAGIC KERNELS LIST


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sd2
title		Microsoft Windows XP Professional
rootnoverify (hd0,0)
savedefault
makeactive
chainloader	+1
```

This is an example how it should be,you have to verify if the entry points to the correct partition.
If I read your first post it should be sd2.

---

### Post by micahphd on 2006-11-04
Here's what that returns:
```
Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        3842    30860833+  83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2   *        3843       11784    63783720    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3           11785       12161     3028252+   5  Extended
Partition 3 does not end on cylinder boundary.
/dev/sda5           11785       12161     3028221   82  Linux swap / Solaris

```

---

### Post by micahphd on 2006-11-04
Ah, I see in menu.lst where I might add the Windows info...

Is it as simple as just adding

```
title		Windows XP Professional SP2
root		(hd0,0)
makeactive
chainloader	+1
```

at the end of the other entries towards the bottom of the menu.lst file?  And if so, what is the "chainloader" line for?  I am getting this from the "examples" section of menu.lst.  I'm looking into the chainloader option now but am not sure it is necessary at first glance.  I think I'm gonna add the above to the menu.lst and I'll see what happens.  If it doesn't load windows ok I'll try taking the chainloader part out.

---

### Post by micahphd on 2006-11-04
Well, it wasn't that easy =)  I saw Windows as the option in the menu but nothing happened when I selected it.  It's all good though, I'm still pluggin away at it.  I'm gonna match up my entry in the menu.lst file with what you have listed here and see how that goes.

EDIT: Well some progress is better then none.  After copying what you pasted I get the following error:

Error 13: Invalid or unsupported executable format

I'm seeing some other examples around the web that suggest my formatting is good here.  I wonder if there is something in the Windows boot.ini that needs to be fixed.  I'm getting out of my league here...

---

### Post by micahphd on 2006-11-05
I've decided to start from scratch and am going to do this by all the toutorials.  so I'll install Windows, then install Ubuntu and set GRUB up that way.  Hopefully this will work.

Well, I'm guessing my previous issues had something to do the location of the Windows partition not being at the front of the disk.  I installed Windows fresh with no issues (on 60GB of the 100GB drive) and Ubuntu on the rest (let it manually partition the remaining space) and all is well.  Right after Ubuntu finished installing and rebooted it gave me the boot options of itself or Windows and Windows loaded fine.

I'm assuming there is a way around this and it would have somehow been possible to move the Windows partition around and get it all to work, but it never hurts to start from scratch =)

Now to get everything back to how it was...

---

