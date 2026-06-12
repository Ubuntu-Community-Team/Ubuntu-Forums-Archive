---
title: "/boot/grub/menu.lst for 6.06 and 6.10 xubun"
date: 2007-02-26
forum: Installation &amp; Upgrades
---

### Post by entropyfoe on 2007-02-26
I have Win XP and Mepis loaded on 2 partitions and I want to add xubuntu (already on a third partition) 6.06 LTS 386 desktop , to /boot/grub/menu.lst.

1. Can anyone send a copy of the correct entry to put into /boot/grub/menu.lst?
I can fix and differences in hd0,2 if necessary.

2. Also I am looking for a correct copy of the same thing for xubuntu 6.10 386 desktop.

I have searched the forums for this information, but have not found a convincing list of kernel and initrd names, and any other options that need to be in there. 

If I just install 6.10, it will install a new grub, and I will have to start over.  This happened before, so can I install 6.10 without grub, and then manually edit the existing /boot/grub/menu.lst?
Thanks
Jay

---

### Post by confused57 on 2007-02-27
> **entropyfoe said:**
> I have Win XP and Mepis loaded on 2 partitions and I want to add xubuntu (already on a third partition) 6.06 LTS 386 desktop , to /boot/grub/menu.lst.

1. Can anyone send a copy of the correct entry to put into /boot/grub/menu.lst?
I can fix and differences in hd0,2 if necessary.

2. Also I am looking for a correct copy of the same thing for xubuntu 6.10 386 desktop.

I have searched the forums for this information, but have not found a convincing list of kernel and initrd names, and any other options that need to be in there. 

If I just install 6.10, it will install a new grub, and I will have to start over.  This happened before, so can I install 6.10 without grub, and then manually edit the existing /boot/grub/menu.lst?
Thanks
Jay

You might want to read over this for booting multiple Linux distros:
[http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems](http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems)

What I do is install grub to the root partition of the distro I'm installing, then add an entry to the grub on mbr to boot the new distro using chainloading:

title   New Distro
rootnoverify  (hdx,y)
chainloader +1

You can always reinstall grub to the mbr or to the root partition, using the live cd:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

---

### Post by entropyfoe on 2007-02-27
Hey Confused57,

Hmm, this will work?

title New Distro
rootnoverify (hdx,y)
chainloader +1

Dont I have to put the kernel exact  name and initrd stuff in?  rootnoverify?

This was my question , the exact kernel and initrd string to put in.
Where do I find this for xubuntu 6.06 and 6.10?

Thanks

-Jay

---

### Post by confused57 on 2007-02-27
> **entropyfoe said:**
> Hey Confused57,

Hmm, this will work?

title New Distro
rootnoverify (hdx,y)
chainloader +1

Dont I have to put the kernel exact  name and initrd stuff in?  rootnoverify?

This was my question , the exact kernel and initrd string to put in.
Where do I find this for xubuntu 6.06 and 6.10?

Thanks

-Jay
The entry will only work if grub is installed to the root partition of the distro you want to boot...see the link for reinstalling grub with the live cd I gave you earlier or specify at installation to install grub to the root partition.  Using the live cd, you can install whichever distro's grub you want on the mbr & the other distros to their root partition...for example:
```
sudo grub
```
will give you a grub prompt
```
find /boot/grub/stage1
```
will return the root partitions for all your distros:
root  (hd0,1)  <------Mepis?
root  (hd0,3)  <------Dapper?
root  (hd0,5)  <------Edgy?

if you wanted Dapper as your grub installed to the mbr, then you would:
```
root (hd0,3)
setup (hd0)
```

then install grub to Edgy's root partition:
```
root (hd0,5)
setup (hd0,5)
```
then to exit:
```
quit
```

then add an entry to boot Edgy to your Dapper menu.lst, using chainloading:

title    Dapper
rootnoverify  (hd0,5)
chainloader +1

you'd do the same with any other distros that you want to boot from Dapper's grub.
Using chainloading is personal choice, but it works well for me.

If you would rather use a kernel & initrd to boot your other distros, you could mount the partition they are on and include their entry to boot into your Dapper grub or whichever grub is on the mbr.   See this link for mounting:
[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD)

You can use the live cd or from an installed distro.

A fresh Xubuntu Dapper 6.06.1 should have an entry similar to this:

title		Ubuntu, kernel 2.6.15-26-386
root		(hd1,5)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sda6 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

You need to adjust the root partition & kernel entry root=/dev/hdax for your system.
Edgy kernel should be 2.6.17-10 on a fresh install.

---

### Post by merlinof2 on 2007-02-27
Doggone some of you folks are superb resources.. Thanks up Front!!!

I have a similar issue.

After allowing Ubuntu 6.10 to upgrade from the .10 to the .11 kernel, I started getting an Xwindows Server error on boot indicating the nVidia driver could not be loaded.  And I was getting an ASCII graphics screen as a display.

I used the "ESC" during Grub countdown to try RECOVER the .11 kernel, FAIL

then ESC during Grub countdown and boot to .10 kernel, SUCCESS.  I'm now running that with no issues, all seems to work perfectly.

HOWEVER, how do I remove the .11 entries from the GRUB menu so the default boot is into the .10 kernel.  now I have to be right there to ESC and choose the .10..

Thanks in Advance.

---

### Post by confused57 on 2007-02-27
> **merlinof2 said:**
> Doggone some of you folks are superb resources.. Thanks up Front!!!

I have a similar issue.

After allowing Ubuntu 6.10 to upgrade from the .10 to the .11 kernel, I started getting an Xwindows Server error on boot indicating the nVidia driver could not be loaded.  And I was getting an ASCII graphics screen as a display.

I used the "ESC" during Grub countdown to try RECOVER the .11 kernel, FAIL

then ESC during Grub countdown and boot to .10 kernel, SUCCESS.  I'm now running that with no issues, all seems to work perfectly.

HOWEVER, how do I remove the .11 entries from the GRUB menu so the default boot is into the .10 kernel.  now I have to be right there to ESC and choose the .10..

Thanks in Advance.

Put a # in front of your .11 entries in your /boot/grub/menu.lst, e.g.
#title Ubuntu, kernel 2.6.17-11-generic
#root (hd0,1)
#kernel /boot/vmlinuz-2.6.17-11-generic root=/dev/hda2 ro quiet splash
#initrd /boot/initrd.img-2.6.17-11-generic
#quiet
#savedefault
#boot

#title Ubuntu, kernel 2.6.17-11-generic (recovery mode)
#root (hd0,1)
#kernel /boot/vmlinuz-2.6.17-11-generic root=/dev/hda2 ro single
#initrd /boot/initrd.img-2.6.17-11-generic
#boot

See this thread for how to edit your menu.lst:
[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

---

### Post by merlinof2 on 2007-02-27
Excellent, many thanks "confused57".  I'll give that a try when I get home this evening.

---

