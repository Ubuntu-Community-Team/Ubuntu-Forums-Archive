---
title: "Accessing the NTFS Partition"
date: 2006-08-12
forum: Installation &amp; Upgrades
---

### Post by mrmcctt on 2006-08-12
Just a quick question.  I installed Ubuntu 6.06 on a dual boot system with WinXP.  I am trying to get the NTFS partition to automatically mount at boot using the instructions in the link below

[http://tinyurl.com/m6q2b](http://tinyurl.com/m6q2b)

After following the instructions and attempting to do a ```
sudo mount -a
``` I get an error stating that /dev/hda1 is already mounted in mtab in /tmp/disks-conf-hda1.

I found the file and it has root only permission.  My question is how do I get the ntfs partition listed in /etc/mtab as ```
/dev/hda1 /media/windows ntfs rw,nls=utf8,umask=0222 0 0
``` out of the mtab file and into fstab so I can see the partition from Ubuntu.  I'm really not sure if I can just remove this line from the /etc/mtab without borking the system so I'll ask first.

Thanks

---

### Post by RedBoot on 2006-08-12
Maybe this is too simplistic, but on the dual boot systems I have with Ubuntu, the NTFS volume appears on my desktop (in fact it's the only icon.) I just double click it and I'm there.

Do you see such an icon on your desktop?

---

### Post by mrmcctt on 2006-08-12
No I don't and it isn't listed in MAIN MENU>PLACES>COMPUTER either.

As an update....I can go to ```
/media/windows
``` and view all of the files and folders in the directory.

I just need to know how to get it (the Windows Partition) to mount on boot so I can see it.

---

### Post by RedBoot on 2006-08-13
I read that site and then looked at my fstab file. Perhaps the inclusion of the "/windows" in those instructions was not quite correct.

A line from my fstab shows:
```
/dev/sda1  /media/sda1  ntfs  defaults,nls=utf8,umask=007,gid=46 0  1
```

Can't tell you what all the stuff nls... on is about, but the key point is that /media/sda1 (hda1 in your case?) is definitely different than /media/windows

Hope this helps.

---

### Post by randell6564 on 2006-08-13
> **mrmcctt said:**
> No I don't and it isn't listed in MAIN MENU>PLACES>COMPUTER either.

As an update....I can go to ```
/media/windows
``` and view all of the files and folders in the directory.

I just need to know how to get it (the Windows Partition) to mount on boot so I can see it.

You dont want "/dev/hda1 **/media/windows** ntfs rw,nls=utf8,umask=0222 0 0"

You want /dev/hda1 **/windows** ntfs rw,nls=utf8,umask=0222 0 0 in your /etc/fstab.

If this does not work then post the output of 'sudo fdisk -l'

---

### Post by mrmcctt on 2006-08-13
Thanks for all your help.  The instructions in the guide worked fine.  For some reason I was thinking that I wouldn't have to reboot after doing the ```
sudo mount -a
``` command.  

After turning off the computer last night and starting it up this morning I was greeted with the windows hard drive icon on my desktop and everything seems to be working fine.

I don't remember having to do a reboot for something like this before but then my memory isn't what it used to be.

Again...Thanks for your help.

---

### Post by RedBoot on 2006-08-13
Good deal.

Is it mapped only to the \Windows folder? Can you get to your Documents and Settings folders, too?

---

### Post by mrmcctt on 2006-08-13
It's listed as 
```
/dev/hda1  /media/windows  ntfs    nls=utf8,umask=0222 0  0
```
in my /etc/fstab and
```
/dev/hda1 /media/windows ntfs rw,nls=utf8,umask=0222 0 0
```
in my /etc/mtab.

Everything seems to work OK.  I can see the ntfs partition and all the folders inside it.  I guess that the /etc/mtab threw me because I've never seen it before so I wasn't sure if this was new or not.

Oh well....Live and learn.

---

