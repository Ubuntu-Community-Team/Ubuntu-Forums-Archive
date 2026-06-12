---
title: "Why won't Windows XP load?"
date: 2007-05-17
forum: Installation &amp; Upgrades
---

### Post by Dural on 2007-05-17
I have installed Ubuntu 7.04 on a HP Pavilion Media Center PC with 2 GB of ram, a 300 GB SATA HD, and a NVIDIA 6100 video card. Currently, the computer is set up to dual boot with Windows XP SP2, but Windows refuses to load. It appears on the GRUB menu and everything seems to work until the "Starting up" message appears. Then, the computer seems to spend time loading indefinitely; I'm not sure whether it's freezing or what. I have considered simply reinstalling GRUB, but I want to keep that as a last resort. Any help would be much appreciated. :)

---

### Post by louieb on 2007-05-18
Just wondering did you have to shrink the XP partition in order to install Ubuntu.  If so I've found it normal for windows to run scandisk the first time I boot to it after shrinking its partition. 

Can you browse your windows partition from Ubuntu? If not then you may have a serious problem. But maybe not.

Open Applications>Accessories>Terminal  and copy / paste the output of these two commands. one list your partition table and the other list the size and free space of your mounted partitions.
```
sudo fdisk -lu
df -h 
```

---

### Post by ©TriMoon® on 2007-05-18
Are you seeing the windows "loading screen" or nothing at all?
If you see the loading screen from windows then that means windows XP is infact correctly booted, the reason for the long delay/hang might be due to what the previous poster told...

---

### Post by Dural on 2007-05-18
> **louieb said:**
> Just wondering did you have to shrink the XP partition in order to install Ubuntu.  If so I've found it normal for windows to run scandisk the first time I boot to it after shrinking its partition. 

Can you browse your windows partition from Ubuntu? If not then you may have a serious problem. But maybe not.

Open Applications>Accessories>Terminal  and copy / paste the output of these two commands. one list your partition table and the other list the size and free space of your mounted partitions.
```
sudo fdisk -lu
df -h 
```


[B]
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   533647169   266823553+   7  HPFS/NTFS
/dev/sda2       533647170   621297809    43825320   83  Linux
/dev/sda3       621297810   625137344     1919767+   5  Extended
/dev/sda5       621297873   625137344     1919736   82  Linux swap / Solaris
[/B]



[B]
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2              42G  8.3G   31G  22% /
varrun                975M  108K  975M   1% /var/run
varlock               975M     0  975M   0% /var/lock
procbususb            975M  144K  975M   1% /proc/bus/usb
udev                  975M  144K  975M   1% /dev
devshm                975M     0  975M   0% /dev/shm
lrm                   975M   39M  937M   4% /lib/modules/2.6.20-15-generic/volatile
/dev/sda1             255G   93G  162G  37% /media/disk
[/B]

I know I can mount my Windows partition in Ubuntu, so it seems to be fine, but somehow when I try to boot it from GRUB, it never makes it to the Windows XP logo. It's like it loads indefinitely.

---

### Post by louieb on 2007-05-18
From the windows CD recovery console  there is a command **fixboot** that fixes the boot sector on the Windows partition.(not to be confused with fixmbr)  Might do a search of the MS knowledge base. But I can't imagine why installing Ubuntu would  do anything to it.
Fdisk looks normal. Your XP partition is only 37% used.  You say you can see the data in the windows partition. I'm out of gas. Can't think of a reason for it not to work. The Dual Boot link in my signature has some recovery / rescue tips to try.   I've got some links to recovery CDs [Nuts Linux Links]("http://louboldt.com/ilinuxlinks.htm").

---

### Post by Dural on 2007-05-18
> **louieb said:**
> From the windows CD recovery console  there is a command **fixboot** that fixes the boot sector on the Windows partition.(not to be confused with fixmbr)  Might do a search of the MS knowledge base. But I can't imagine why installing Ubuntu would  do anything to it.
Fdisk looks normal. Your XP partition is only 37% used.  You say you can see the data in the windows partition. I'm out of gas. Can't think of a reason for it not to work. The Dual Boot link in my signature has some recovery / rescue tips to try.   I've got some links to recovery CDs [Nuts Linux Links]("http://louboldt.com/ilinuxlinks.htm").

I downloaded Super Grub Disk on my Windows XP SP2 laptop and extracted the boot folder to the USB drive. I planned to take my USB drive and put it in the Ubuntu computer, but I'm not sure how to do the step where you have to open a GRUB shell with root privileges, because I"m not sure whether I should do this from the terminal in Ubuntu or if I have to reboot the computer and see if there's a command prompt to allow me to do so. The instructions on this site ([http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#boot_windows](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#boot_windows)) were helpful, but they did theirs in Linux (not sure which distro).

Also, if I decide to fix the boot record, will I have to reinstall GRUB?

Update: I've decided to just go with fixboot. The last question still stands.

Update #2: Tried fixboot, and it didn't work. The computer is not frozen, but it's not responding either. It's still there with "Starting up..." and a blinking cursor.  I am currently using the 64 bit version of Ubuntu 7.04 while dual booting with Windows XP SP2 (32-bit version) with GRUB. I hope that's not what's causing the problem.

---

### Post by louieb on 2007-05-18
The only time I've had trouble like your having is the the time I installed Ubuntu and did not run the Defrag tool in XP before shrinking its partition. ( got in a hurry ). Never did get XP to boot. Wound up using Ubuntu to copy my windows data off and reinstalling XP and all the programs. Then put the data back.  It was a pain in the as. Hope you have better luck that I did that time. You have a lot of data on that partition  df shows 93 gig and windows is  about 5 - 10 gig  of that.

---

### Post by logos34 on 2007-05-18
> Update #2: Tried fixboot, and it didn't work. The computer is not frozen, but it's not responding either. It's still there with "Starting up..." and a blinking cursor. I am currently using the 64 bit version of Ubuntu 7.04 while dual booting with Windows XP SP2 (32-bit version) with GRUB. I hope that's not what's causing the problem.

I dual boot xp x64 and 32-bit Ubuntu 6.10 without any trouble, so that's not likely the issue.

What about using winxp cd recovery console to run CHKDSK with repair options?  (this is the first thing that is supposed to happen when you boot into windows immediately after an Ubuntu install/parition resizing).

---

### Post by Dural on 2007-05-19
> **louieb said:**
> The only time I've had trouble like your having is the the time I installed Ubuntu and did not run the Defrag tool in XP before shrinking its partition. ( got in a hurry ). Never did get XP to boot. Wound up using Ubuntu to copy my windows data off and reinstalling XP and all the programs. Then put the data back.  It was a pain in the as. Hope you have better luck that I did that time. You have a lot of data on that partition  df shows 93 gig and windows is  about 5 - 10 gig  of that.

That's funny, because that's what I'm doing right now. :D
Fortunately, I don't need most of the data since I'm on summer break.

> 
I dual boot xp x64 and 32-bit Ubuntu 6.10 without any trouble, so that's not likely the issue.

What about using winxp cd recovery console to run CHKDSK with repair options? (this is the first thing that is supposed to happen when you boot into windows immediately after an Ubuntu install/parition resizing)

Crap. When I booted into Windows XP after installing Ubuntu, it didn't run CHKDSK. Is that why this happened?

---

### Post by Dural on 2007-05-19
I'm really angry now. I just ran CHKDSK from the Windows XP Recovery Console. It said that it did not need to check at all because the volume is in good condition. However, I told it to start anyways. When it finished, it said that there was nothing wrong.

---

### Post by transparent9 on 2007-05-23
I don't know if you've already wiped and started over, but I was having similar problems, had the same exact symptoms as you.  

What I had to do to get things working again was to run testdisk, and use testdisk to fix the boot sector and rebuild the MFT.  Then Windows booted.

---

