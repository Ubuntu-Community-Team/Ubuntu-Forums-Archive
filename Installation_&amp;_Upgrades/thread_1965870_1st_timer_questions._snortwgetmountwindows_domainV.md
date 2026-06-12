---
title: "1st timer questions. snort/wget/mount/windows domain/VMware"
date: 2012-04-26
forum: Installation &amp; Upgrades
---

### Post by notShai on 2012-04-26
[hello, i have ubuntu 10.04 server on VMware, CLI only no GUI, installed snort 2.9.2.2]

when i try to download the snort rules it fails.
when i tested the same download from a windows pc, it asks me to login, after login it downloads.
i am not a paying member, but im subscribed.

my questions:
[LIST=1]
[*]what is the correct way of downloading from a site with authentication via CLI?
[*]where do i 'cd' into to find the contents of a USB drive i plugged so i dont have to download stuff? when i type 'mount' it lists a bunch of 'not there's
[*]how do i easily copy from a windows share drive over the network under windows domain?
[*]why cant i copy paste from windows into a VMware ubuntu window?
[*]how do i change the VMware screen size? scroll up?
[*]how do i apply group permissions onto a folder? i have a white colored folder name, i want to "blue" it...
[/LIST]


i realize all questions will be a challenge to reply to, i will take anything you got. thanks.

---

### Post by col48 on 2012-04-26
I don't know about the rest but.....

> 4. why cant i copy paste from windows into a VMware ubuntu window?


Think about how copy/paste happens.  'Copy' puts the stuff being copied into a memory buffer under the control of the OS.  'Paste' copies from the buffer into the current document, which may be a different application from the one the stuff came from.

Your main Windows OS and whatever is running under VM do not communicate except to allow VM's client OS to pretend it owns the hardware it knows about (video card, printer, whatever).  The organisation of the memory when Windows has control is not known to the client OS and vice versa, so there is no way copy/paste could cross the boundary.  I think that even if the client OS was another copy of Windows the same would be true.

Workaround?  If you have an area on disk which is known to both systems you could write a document (eg a .txt file) in Windows and then read it in Ubuntu.  WARNING: Don't have the same file open in both OS at the same time as it may get corrupted.

---

### Post by Jive Turkey on 2012-04-26
> **col48 said:**
> I don't know about the rest but.....



Think about how copy/paste happens.  'Copy' puts the stuff being copied into a memory buffer under the control of the OS.  'Paste' copies from the buffer into the current document, which may be a different application from the one the stuff came from.

Your main Windows OS and whatever is running under VM do not communicate except to allow VM's client OS to pretend it owns the hardware it knows about (video card, printer, whatever).  The organisation of the memory when Windows has control is not known to the client OS and vice versa, so there is no way copy/paste could cross the boundary.  I think that even if the client OS was another copy of Windows the same would be true.

Workaround?  If you have an area on disk which is known to both systems you could write a document (eg a .txt file) in Windows and then read it in Ubuntu.  WARNING: Don't have the same file open in both OS at the same time as it may get corrupted.

Another workaround for the copy paste problem is to access the vm via putty in windows instead of the vm interface.

---

### Post by col48 on 2012-04-26
Well, maybe I can contribute a little to:

> 
2. where do i 'cd' into to find the contents of a USB drive i plugged so i dont have to download stuff? when i type 'mount' it lists a bunch of 'not there's

although you'll have to get a final answer from someone else if this doesn't help.

In Ubuntu, if you plug in a USB stick it should pop up in Nautilus (the equivalent of 'File Manager') without the need to do cd in Terminal or to separately mount it.

But if you want to use a Terminal

```
cd /media
dir -al
```
should show it to you alongside other media drives with whatever name the stick was given - the al parameters will show the ownership and the permissions.

You would have to have told Ubuntu when you installed it in VM that the USB drive exists or it won't even see it.  Maybe that's the problem.  I guess you can add it later if that's the problem.

---

### Post by Jive Turkey on 2012-04-26
These aren't specific answers to your questions but they should lead you to the answers you need.

1. man wget
2. read this: [https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB)  VMWare probably complicates this further because your VM needs to have access to the USB drive.
3. you'll need to have the share mounted see "man smbfs"
4. see previous comments
5. I recommend starting the VM and accessing it via putty from windows.  You can also pipe command outputs to the programs "less" or "more" which will allow scrolling.  ie "ls ~/ | less"
6. read "man chmod" & "man chown"

Good luck and have fun!

---

