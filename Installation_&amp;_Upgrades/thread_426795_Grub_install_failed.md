---
title: "Grub install failed"
date: 2007-04-28
forum: Installation &amp; Upgrades
---

### Post by expatCM on 2007-04-28
The CD media is known good  (just used to install on other machines).  Dual boot with Windows.

The install process runs correctly until the very end when it comes to write grub to the start of the ext3 partition.

It terminates with the error "Executing grub-install hda3 failed.  This is a fatal error."

I do not know why this happens and what to do to fix it.  Any suggestions?

---

### Post by louieb on 2007-04-28
reinstall grub or duel boot links in signature should get you going.

---

### Post by expatCM on 2007-04-28
reinstall Grub?  But how ?   it is not yet installed ...?

"dual boot links in signature" ... what signature?  what links?

---

### Post by bulldog on 2007-04-29
> **expatCM said:**
> reinstall Grub?  But how ?   it is not yet installed ...?

"dual boot links in signature" ... what signature?  what links?

Can you boot the live cd and perform in a terminal the command```
sudo fdisk -l
``` it's a lowercase L.
Copy the output to the forum and we take it from there.

Reinstalling GRUB isn't hard to do,but is there a reason why you want to install it to a partition instead of in the MBR of the hdd,which is the 'normal' way for installing GRUB.

---

### Post by jwalker46 on 2007-04-29
Bulldog,  I have the same problem, and will try your suggestion as soon as I logoff here.  Incidentally, the reason for /not/ wanting to write to the MBR is simple: there are many utlitilies such as GAG and EasyBCD that are easier to configure (edit) than GRUB.  As you know, many of us trying Ubuntu are coming from Windows, and we have been using GUIs for a decade, so any command-line editing is prone to error.  So, I would certainly prefer leaving my MBR (I have EasyBCD installed) alone, so there is absolutely no risk I can screw it up and be unable to boot back into Windoze.

---

### Post by bulldog on 2007-04-29
> **jwalker46 said:**
> Bulldog,  I have the same problem, and will try your suggestion as soon as I logoff here.  Incidentally, the reason for /not/ wanting to write to the MBR is simple: there are many utlitilies such as GAG and EasyBCD that are easier to configure (edit) than GRUB.  As you know, many of us trying Ubuntu are coming from Windows, and we have been using GUIs for a decade, so any command-line editing is prone to error.  So, I would certainly prefer leaving my MBR (I have EasyBCD installed) alone, so there is absolutely no risk I can screw it up and be unable to boot back into Windoze.

LOL,okay,I can live with that:) 
But if you set GRUB in the MBR and it fails,just a windows install disk,or the [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/) can bail you out.

In fact GRUB isn't difficult at all,it just put the OS's in a list [menu.lst] and points to the partition where the desired OS is located,from there on the boot loader from the OS takes over to boot the OS.
No hanky panky is going on,for that matter.

---

### Post by expatCM on 2007-04-29
erm .... how do I navigate to the hard drive from the command prompt?   I can find the fstab file if I use Places / Search for Files and then drill down but from the command prompt ... hmmm...

The fstab file shows the following if that helps ....

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=446eb33b-f998-405f-863b-c0ab78be57a8 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=42CD-663B  /media/hda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hdb1
UUID=4631-F8C1  /media/hdb1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda2
UUID=f2436a06-4ef7-4524-b55a-b3ab7afa5536 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by louieb on 2007-04-29
> **expatCM said:**
> reinstall Grub?  But how ?   it is not yet installed ...?
"dual boot links in signature" ... what signature?  what links?
Signature is the two lines at the bottom of my post.

> **expatCM said:**
> erm .... how do I navigate to the hard drive from the command prompt?   ...
Applications>Accessories>Terminal.

From you fstab and your description of the install you do have GRUB installed it just isn't working. Since I'm lazy and could just cut and paste catlett's or Herman's work. The links are easier.

---

### Post by jwalker46 on 2007-04-29
louieb, I have the same problem as expatCM, but the find command returns "not found".  The grub error message was quite clear (not installed).  So...?  :confused: :confused:

---

### Post by louieb on 2007-04-29
> **jwalker46 said:**
> louieb, I have the same problem as expatCM, but the find command returns "not found".  The grub error message was quite clear (not installed).  So...?  :confused: :confused:
So I'm guessing your install died before grub was put in place. 
The easiest fix is [Super Grub Disk Webpage]("http://supergrub.forjamari.linex.org/")
And a really good how to on it.   [Herman on SuperGrub]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html") (Part of the Duel Boot site).

---

### Post by jwalker46 on 2007-04-29
expatCM, here is a fix that worked for me: 

(1) when you get to partition, highlight the root partition (or wherever you want to put GRUB), and select "ON" for "bootable flag".  I also resized the swap to 1 GB (that was mentioned on another thread).  Between the two changes, I was able to install GRUB.  I assume the problem was the bootable flag.

(2) use superGRUB or Knoppix to change the active partition to your Windows install.

(3) reboot; you should get to the Windows boot manager

(4) use GAG or EasyBCD (my choice) to setup a simple GUI for multi-booting.  EasyBCD will find Windows, and it is simple to add the location of GRUB for the Ubuntu install.

RSVP if this does not work.

---

### Post by expatCM on 2007-04-30
I have run through this again now, watching what happens.   Grub fails to install at about 96% of the whole install process.  It then terminates, gives an error message and on clicking the error message the install program then ends.

So what you end up with is no grub and also no operating system since the last 4% is not completed and so therefore the install is incomplete.

To solve this problem I have put the boot loader on the first sector of the drive and yes it works.  The trouble is that this is not what I wanted and looking forward to the time when it is appropriate to loose XP for good then the boot loader will probably be history as well when the volume is formatted.

Too much trouble to think about now ...  leaving it for something to look forward to ....  :)

---

