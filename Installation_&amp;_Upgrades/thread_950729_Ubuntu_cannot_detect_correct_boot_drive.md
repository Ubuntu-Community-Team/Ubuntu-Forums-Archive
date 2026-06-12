---
title: "Ubuntu cannot detect correct boot drive"
date: 2008-10-17
forum: Installation &amp; Upgrades
---

### Post by aajax on 2008-10-17
I've installed Ubuntu, along with other OSs, on systems that have multiple drives.  It is sometimes necessary to boot from a drive other than the one that the BIOS uses by default.  In my experience most , if not all, BIOS configuration options allow the choice of boot drive to be changed from the default setting.  It appears to me as though this has the affect of making the chosen drive appear to be the first drive during the boot process but the drives revert to their natural order once the system is running normally.  Therefore, a running system can (always does in my case on several different machines) see a drive configuration that is different than what the boot loader finds.  As a result, Ubuntu erroneously concludes that it should boot from a secondary drive (partition) when in fact the boot loader always sees the boot drive as the first drive (hd0 in GRUB terms). 

Prior to trying Ubuntu (first 7.10 and now 8.04.1) my experience is with Debian up through Sarge, which uses LILO (successfully in my scenario), rather than GRUB.  While GRUB may have lots of capability not present in LILO I'm finding it to be anything but grand when it comes to getting my system booted.  It might be possible to dismiss this as a minor nuisance if it were only the Ubuntu installation process that builds a system that cannot boot.  However, even though it was fairly easy to find a fix (i.e., update drive settings in /boot/grub/menu.lst), I didn't have to go very far before discovering that Ubuntu unfixes it (possibly by running update-grub) as a routine matter of applying system updates.

My current hope is that there is a solution for this serious defect that I have yet to discover.  If so, I'd be very grateful if someone more familiar with GRUB, than I am, could enlighten me.  If not, Ubuntu developers need to come up with an improvement.

---

### Post by caljohnsmith on 2008-10-17
> **aajax said:**
> I've installed Ubuntu, along with other OSs, on systems that have multiple drives.  It is sometimes necessary to boot from a drive other than the one that the BIOS uses by default.  In my experience most , if not all, BIOS configuration options allow the choice of boot drive to be changed from the default setting.  It appears to me as though this has the affect of making the chosen drive appear to be the first drive during the boot process but the drives revert to their natural order once the system is running normally.  Therefore, a running system can (always does in my case on several different machines) see a drive configuration that is different than what the boot loader finds.  As a result, Ubuntu erroneously concludes that it should boot from a secondary drive (partition) when in fact the boot loader always sees the boot drive as the first drive (hd0 in GRUB terms). 

I think you might be a little confused about how Grub sees drives on start up versus how Grub or Linux sees drives once you've booted into Linux, so I'm hoping this might help: on start up, Grub sees the order of drives as the same as the BIOS boot order, because on start up Grub must use BIOS to access the drives. Note that the BIOS boot order has nothing to do with the device order in Linux's /dev directory, because Linux works through the kernel (not through BIOS) to access the drives; Linux's /dev directory is ordered by the type of device, so for HDDs they would be ordered by whether they are IDE, SATA, USB, and so on. So when you run Grub commands inside Ubuntu, then unless you tell Grub otherwise, the following would be true:
```
(hd0) = sda
(hd1) = sdb
(hd2) = sdc
...etc
```
But on start up, as I explained above, it is different: if you have say sdb as your drive to boot first on start up, then on start up Grub will see sdb as (hd0) since sdb is the first in the boot order. Then whichever drive is second in the boot order will be (hd1), and so on. Does that maybe help clarify better what is happening?
> **aajax said:**
> 
However, even though it was fairly easy to find a fix (i.e., update drive settings in /boot/grub/menu.lst), I didn't have to go very far before discovering that Ubuntu unfixes it (possibly by running update-grub) as a routine matter of applying system updates.
The solution to that should be as simple as changing the "#groot=(hdX,Y)" line in your menu.lst to use the correct (hdX,Y) value for Ubuntu. The groot line is how the update-grub command determines which partition Ubuntu is on. :)

---

### Post by aajax on 2008-10-17
My experience is exactly as you explain.  My apologies for not being clear.  I even fumbled my way along and figured out that I could update menu.lst and expected that this would be the end of it.  That is what I meant when saying this might be dismissed as mere nuisance.

However, the nasty part is that Ubuntu keeps changing menu.lst such that the defective values are perpetually restored. In that, the mere act of updating the system can cause it to go from booting fine to being unbootable.  This is especially egregious when unattended booting is desired.

From my little bit of research I'm thinking this is a consequence of running update-grub which may be used by some package maintainers.  I understand that there are things, like updating the kernel, that may require menu.lst to be changed.  However, there needs to be a way turn off (prevent) the drive specifiers from being arbitrarily changed.  Another possibility would be to allow the admin to explicitly designate/override what values are to be used.

---

### Post by Herman on 2008-10-17
:) Hello aajax,
Ubuntu is based on Debian, and in the middle of our /boot/grub/menu.lst files, we have an area called the  '[DEBIAN AUTOMAGIC KERNELS LIST]("http://users.bigpond.net.au/hermanzone/p15.htm#DEBIAN_AUTOMAGIC_KERNELS_LIST")'. 
Thanks to the Debian Automagic Kernels List, we don't need to manually edit our menu.lst files whenever we are issued with an upgraded kernel.
Instead, the script called 'update-grub' is run automatically, and that creates a new (updated) menu.lst file for us based on information stored in the Debian Automagic Kernels List.

The purpose of the Debian Automagic kernels list is to store the information we want to make persistent over kernel upgrades.
If the information in the 'debian automagic kernels list' is incorrect, we will get a new GRUB menu that will be incorrect.
Therefore, if we needed to make any important changes to the [operating system booting stanzas]("http://users.bigpond.net.au/hermanzone/p15.htm#Operating_system_Entries") to get Ubuntu to boot properly when we first installed, we also need to make the same changes in our 'debian automagic kernels lists. 

The 'in [groot=]("http://users.bigpond.net.au/hermanzone/p15.htm#groot")' value would be the one you would need to edit in this case.

---

### Post by Herman on 2008-10-17
Unfortunately it has been a problem for as long as I can remember that some BIOSes like to report the disk order to GRUB one way, and others do it another way when there are different types of disks present. (IDE, SCSI/SATA, and USB).
As far as I know, if they fix GRUB for some BIOSes, there will be even more BIOSes of the other type that will cause the same, (or equal but opposite) problem.

The introduction of the use of file system UUID numbers in our /etc/fstab files was one great improvement we have seen in booting.
Before that, the linux kernel depended on having the correct linux drive designation in the booting stanza, (like '/dev/sda2. or '/dev/hda1', and such). 
If the drives were changed, (by inserting a flash memory stick for example), the Linux kernel could be confused about where to find it's initrd.img and booting scripts.

The same thing could be done with hard disks. 
There's a 'disk identifier', which is unique in every MBR. I wonder if that could be used to help GRUB to find the right hard disk? 
The 'disk identifier' can be seen each time we run 'sudo fdisk -lu'.
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: [COLOR=Sienna]**0x000ba675**[/COLOR]

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    42331274    21165606   83  Linux
/dev/sda2        42331275   312576704   135122715    5  Extended
/dev/sda5        42331401   306937889   132303244+  83  Linux
/dev/sda6       306937953   312576704     2819376   82  Linux swap / Solaris
```That's just an idea, I don't know if it would really help or not, greater minds than mine have probably already thought of that.

Unfortunately, GNU GRUB 'Legacy', which we use now, is no longer under development.
It will be replaced with [GRUB 2]("http://www.gnu.org/software/grub/grub-2.en.htm") someday, but we have been waiting for it for a very log time already.
Perhaps that idea has already been incorporated and we might see it in GRUB2.

Vista's new boot loader is tied to the MBR's 'Disk Signature', but the reasons for M'soft choosing to do that was more to make things harder for people, not easier. Being a proprietary operating system, they need to employ a lot of antipiracy measures, and those can be double - edged swords. [Multibooters - Dual/Multi Booting With Vista]("http://www.multibooters.co.uk/").

You can install LiLo if you prefer. LiLo can be installed with Synaptic Package Manager, and it will even live happily in the same /boot directory with GRUB.
(There is no need to uninstall GRUB to install LiLo).
LiLo doesn't like our file system UUID numbers in /etc/fstab, we need to revert to the old '/dev/sda1' type of info in our /etc/fstab files before configuring LiLo. [LiLo Page]("http://users.bigpond.net.au/hermanzone/p4.html").

LiLo can also be installed when Ubuntu is installed if we use the 'Alternate' CD, see my sig links for details.

Regards, Herman :)

---

### Post by aajax on 2008-10-18
WaLa!  I cannot be too confident at this point but it looks like the "groot" setting in the Debian Automagical whatever section of menu.lst is the work around that addresses this issue.

Many thanks for the tip!

I noticed a file named "device.map", which is contained in the /boot/grub directory.  The contents are pretty simple and appear to designate the correspondence between the GRUB and Linux method of designating devices (partitions).  To the extent that this file is only used during boot (GRUB) processing it is wrong as created by the Linux installer.  I'm thinking it shouldn't hurt to make it correct but that's not possible if it is used both by Linux and GRUB.  

If anyone knows how this files is used I'd be grateful for the benefit of their insight.

---

### Post by Herman on 2008-10-19
I think that the device.map file is just for the user's information.
It might be handy to take a look at when we have a mixture of IDE, SCSI (SATA) and USB disks in one computer and we get GRUB Error 17 and we ant to see how (why) that happened.

I don't believe that editing device.map actually does anything. 
I was hoping it would and I tried very hard in the following thread to leran how to get device.map to do something, but it didn't work for me, [Grub error 17]("http://ubuntuforums.org/showthread.php?t=442945").

It won't hurt anything if you make it correct, but in the above linked thread,  meierfra and I agreed that the best way to fix GRUB Error 17 when it's caused by mixed hard disks is to change the hard disk order in the BIOS to suit what GRUB thinks the disk order should be. (As in device.map). (Rather than the other way around).

Regards, Herman :)

---

### Post by caljohnsmith on 2008-10-19
Hi Herman, I found out from experimenting once that Grub actually does use the device.map file on start up, but only if you have references to /dev/hdX or /dev/sdX type devices in the menu.lst. In other words, if you don't use UUIDs like in the following case:
```
title        Ubuntu 8.04, kernel 2.6.24-19-generic
root         (hd0,1)
kernel        /boot/vmlinuz-2.6.24-19-generic root=[COLOR="Red"]/dev/sda2[/COLOR] ro quiet splash
initrd        /boot/initrd.img-2.6.24-19-generic
quiet
```
Grub will look up "/dev/sda" in the device.map to see which Grub drive (hdX) it corresponds to. Therefore I found from experimenting that if you want to use "hda" instead of "sda" in the above example, it is as simple as changing the device.map to use "hda" instead of "sda". And although I didn't try it, I'll bet you could include both if you wanted to in the device.map:
```

(hd0)	/dev/sda
(hd0)  /dev/hda
```
That way both sda and hda would be mapped to Grub's (hd0), and you wouldn't have to remember which one to use. :)

---

### Post by Herman on 2008-10-21
> I found out from experimenting once that Grub actually does use the device.map file on start up, but only if you have references to /dev/hdX or /dev/sdX type devices in the menu.lst. In other words, if you don't use UUIDs
:) Thank you caljohnsmith, that's something I didn't think of, I'll try that out later, good to know, thanks for sharing.
Regards, Herman :)

---

