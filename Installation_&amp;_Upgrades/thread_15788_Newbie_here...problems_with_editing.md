---
title: "Newbie here...problems with editing"
date: 2005-02-16
forum: Installation &amp; Upgrades
---

### Post by JGKC9AYC on 2005-02-16
I installed Warty last nite.  Today, when I rebooted & it went into Grub, my XP OS wasn't there.  I was told to check /boot/grub/menu.lst, which I did, and I found nothing there about my XP partition.  I can't edit it because I don't know how to get into "root" or whatever this distro calls it.
Cany anyone hold my hand & help?  :)
Thanks in advance.

---

### Post by tkiesel on 2005-02-16
Hi JGKC9AYC,

Click on Applications -> System Tools -> Terminal

In the window that comes up, type:

 gedit /boot/grub/menu.lst

A read-only text editor pops up with that file.  If you could copy and paste the output here, I or someone else can possibly help you out.

Don't worry. You'll be able to fix this.  :)

-T

---

### Post by Tiede on 2005-02-16
JGKC9AYC, at the installation phase, Grub is suposed to tell you it found your other operating system (or systems) for you to accept them. Did you remember seeing something in the install about Windows XP?

In the terminal, type "sudo fdisk -l" (without the quotes) and give the output here.
It will most likely ask you for a password, which will be the password you use to login.

---

### Post by Xian on 2005-02-16
[QUOTE=JGKC9AYC]I can't edit it because I don't know how to get into "root" or whatever this distro calls it.[/QUOTE]
From the taskbar: Applications > System Tools > Terminal

Then follow this sequence at the command prompt:
```
$ sudo gedit /boot/grub/menu.lst
Password:
```

The password is the same as the one you use to login.

A new window will open that has the contents of the menu.lst file. 
You are looking for something that looks like this:
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Windows NT/2000/XP
root		(hd0,0)
savedefault
chainloader	+1
```

---

### Post by JGKC9AYC on 2005-02-16
tkiesel, here's your info:

title		Ubuntu, kernel  
root		(hd0,2)
kernel		/boot/vmlinuz root=/dev/hda3 ro console=tty0 quiet splash
initrd		/boot/initrd.img
savedefault
boot

title		Ubuntu, kernel  (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz root=/dev/hda3 ro console=tty0 single
initrd		/boot/initrd.img
savedefault
boot

title		Ubuntu, kernel 2.6.8.1-3-amd64-generic 
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.8.1-3-amd64-generic root=/dev/hda3 ro console=tty0 quiet splash
initrd		/boot/initrd.img-2.6.8.1-3-amd64-generic
savedefault
boot

title		Ubuntu, kernel 2.6.8.1-3-amd64-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.8.1-3-amd64-generic root=/dev/hda3 ro console=tty0 single
initrd		/boot/initrd.img-2.6.
8.1-3-amd64-generic
savedefault
boot

I think the "2.6.8.1-3 is leftovers from an Ubuntu install gone bad...i'd like to delete those.

Tiede, here's your info:

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        7337    58934421    7  HPFS/NTFS
/dev/hda2            7338        7466     1036192+  82  Linux swap
/dev/hda3   *        7467       14531    56749612+  83  Linux
/dev/hda4           14532       14593      498015    f  W95 Ext'd (LBA)
/dev/hda5           14532       14593      497983+  82  Linux swap

Disk /dev/hdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       19457   156288321   42  SFS

I appreciate y'alls help...hope we can get it working!  :)

---

### Post by Xian on 2005-02-16
[QUOTE=JGKC9AYC]I can't edit it because I don't know how to get into "root" or whatever this distro calls it.[/QUOTE]
From the taskbar: Applications > System Tools > Terminal

Then follow this sequence at the command prompt:
```
$ sudo gedit /boot/grub/menu.lst
Password:
```
The password is the same as the one you use to login.

A new window will open that has the contents of the menu.lst file. 
You are looking for something that looks like this:
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Windows NT/2000/XP
root		(hd0,0)
savedefault
chainloader	+1
```

---

### Post by Xian on 2005-02-16
[QUOTE=JGKC9AYC] Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        7337    58934421    7  HPFS/NTFS[/QUOTE]
Yeah, that's great. See where your Windows OS is on hda1?
So, we just need to add that to your grub's menu.lst file.

Append the following to /boot/grub/menu.lst
```
title		Windows NT/2000/XP
root		(hd0,0)
savedefault
chainloader	+1
```

---

### Post by JGKC9AYC on 2005-02-16
I've seen stuff like this:

title=Windows
rootnoverify (hd0,0)
makeactive
chainloader +1 

what's the difference, if any?
Thanks.

Also, will it be ok to delete the other Ubuntu entries from the previous install?  I assume I just highlight & delete?

---

### Post by Xian on 2005-02-16
[QUOTE=JGKC9AYC]what's the difference, if any?

Also, will it be ok to delete the other Ubuntu entries from the previous install?  I assume I just highlight & delete?[/QUOTE]
Makeactive is a command that sets the active partition on the root disk to GRUB's root device. This command is limited to primary PC partitions on a hard disk

Yes, you can just highlight and delete, but the entries noted below may actually refer to linked files that point to a legitimate kernel. Best to check that and then make a decision.

```
kernel /boot/vmlinuz root=/dev/hda3 ro console=tty0 quiet splash
initrd /boot/initrd.img
```
Synaptic generally will create linked files for you in either the / or /boot directory to the most recent kernel. This is just a tool to assist you in keeping track of what is on your system.

---

### Post by JGKC9AYC on 2005-02-16
I originally installed "Hedgehog"(?), but it said it was missing files & could only boot into a command prompt or whatever linux calls that.  I then downloaded & installed "Warty"(?).  The original install at least gave me the opportunity to boot into Windows...no pressing of the "ESC" key was needed.  I do remember seeing those before I installed Warty, that's why I asked if they could be deleted or not...I didn't know if perhaps it was leftover or what.

---

### Post by Xian on 2005-02-16
[QUOTE=JGKC9AYC]I didn't know if perhaps it was leftover or what.[/QUOTE]
To be leftover the partitioner during the Warty install would have failed or been told to not format your root or boot directory, and even then I doubt that it would have worked in such a fashion. I would think that all those entries refer to the same kernel. 

Open Nautilus (Computer > Home) and goto /boot/vmlinuz. 
Right click on the file and select "Properties".
A new window will open. Look for the line "Link Target". 

Is there a notation for that line and does it refer to /boot/vmlinuz-2.6.8.1-3-amd64-generic?

---

### Post by JGKC9AYC on 2005-02-16
I don't have "Nautilus" under "Computer, Home".    ](*,)

---

### Post by Xian on 2005-02-16
[QUOTE=JGKC9AYC]I don't have "Nautilus" under "Computer, Home". [/QUOTE]
No, I meant that's HOW you open Nautilus. 
From the taskbar click on Computer and then click "Home".

Or you can select Applications > Run Applicaton
Then type in "Nautilus" [no quotes] and click Run

Navigate the file browser to /boot and look for those files.

---

### Post by tkiesel on 2005-02-16
Nautilus is what opens when you click Computer -> Home   It's like Windows Explorer in Windows. It's a file browser. :)

Did you follow Xian's instructions in [this post?](http://www.ubuntuforums.org/showpost.php?p=72338&postcount=4)  I think that'll set you up to boot Windows from Grub.  :)

---

### Post by JGKC9AYC on 2005-02-16
yes, there's a notation for that line & it does state the directory you specified.

---

### Post by Xian on 2005-02-16
[QUOTE=JGKC9AYC]yes, there's a notation for that line & it does state the directory you specified.[/QUOTE]
Fine, then all those entries in grub are referring to the same kernel. You have some verbose entries that specifically point to the kernel and initrd files, and you have some other entries that use the links we just mentioned. If you don't want to see them all each time you boot then just delete them or comment out one set or the other. 

If you want to save some of the notations for a rainy day but make them transparent, you can change this:```
title Ubuntu, kernel 2.6.8.1-3-amd64-generic 
root (hd0,2)
kernel /boot/vmlinuz-2.6.8.1-3-amd64-generic root=/dev/hda3 ro console=tty0 quiet splash
initrd /boot/initrd.img-2.6.8.1-3-amd64-generic
savedefault
boot

title Ubuntu, kernel 2.6.8.1-3-amd64-generic (recovery mode)
root (hd0,2)
kernel /boot/vmlinuz-2.6.8.1-3-amd64-generic root=/dev/hda3 ro console=tty0 single
initrd /boot/initrd.img-2.6.
8.1-3-amd64-generic
savedefault
boot
```
To this and then save the file:
```
#title Ubuntu, kernel 2.6.8.1-3-amd64-generic 
#root (hd0,2)
#kernel /boot/vmlinuz-2.6.8.1-3-amd64-generic root=/dev/hda3 ro console=tty0 quiet splash
#initrd /boot/initrd.img-2.6.8.1-3-amd64-generic
#savedefault
#boot

#title Ubuntu, kernel 2.6.8.1-3-amd64-generic (recovery mode)
#root (hd0,2)
#kernel /boot/vmlinuz-2.6.8.1-3-amd64-generic root=/dev/hda3 ro console=tty0 single
#initrd /boot/initrd.img-2.6.8.1-3-amd64-generic
#savedefault
#boot
```

---

### Post by JGKC9AYC on 2005-02-16
OK, cool, i'll try that.  I guess that was my main concern after getting my XP to show up.  Guess I kinda wanted to tidy it up some.  Silly me.   :roll: 
I appreciate your help & patience.  :)

---

### Post by Xian on 2005-02-16
[QUOTE=JGKC9AYC]OK, cool, i'll try that.  I guess that was my main concern after getting my XP to show up.  Guess I kinda wanted to tidy it up some.[/QUOTE]
That makes sense. I usually like to keep the verbose entries because I don't prefer to depend upon Synaptic to make correct new links during every kernel upgrade, but even if it didn't you'd still be able to boot as normal since the last working kernel is always saved. But you can certainly always check the link status and just continue to comment out those notations that you feel are redundant.

Did you get Windows to boot okay?

---

### Post by JGKC9AYC on 2005-02-18
Yes...it worked & I went back into Ubuntu later & edited the menu.lst again.  It works great now.  Again, I appreciate your help & patience.
One more question, tho...if I don't hit the <ESC> key in the alloted amount of time, which OS will boot up?

---

### Post by Tiede on 2005-02-19
The one that is highlighted in the GRUB menu.

My guess is it will be Ubuntu (it is the default one).
Of course, you can always edit menu.lst to change the default boot device later. ;)

---

