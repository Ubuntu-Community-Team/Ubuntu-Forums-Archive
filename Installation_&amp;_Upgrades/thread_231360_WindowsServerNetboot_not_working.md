---
title: "WindowsServerNetboot not working"
date: 2006-08-07
forum: Installation &amp; Upgrades
---

### Post by Hermiod on 2006-08-07
I have a damaged CD/DVD drive and am trying to install Ubuntu using netboot, I followed the procedures in the windows netboot guide
[https://help.ubuntu.com/community/Installation/WindowsServerNetboot](https://help.ubuntu.com/community/Installation/WindowsServerNetboot)
and had a look at the linux netboot guide 
[https://help.ubuntu.com/community/Installation/Netboot](https://help.ubuntu.com/community/Installation/Netboot)

I manage to start the PXE boot on the other PC, but it fails giving me a "Kernel Panic - not syncing: VFS: unable to mount root fs on unknown-block(8,1)".

After some thinking I noticed that in none of the above guides it specifies what I am supposed to do with the ubuntu iso. I checked out a few files in the netboot folder and some of them have a line containing "root=/dev/rd/0 rw", I suppose that points to the install files. 

The howto is not clear, how do I make the installer see the install files on my windows machine? Is the error relative to something else ?

---

### Post by Hermiod on 2006-08-07
It seems I copied the wrong file, apparently there is a prelinux.cfg file and a prelinux.cfg directory. Once I copied the directory it booted. Its now downloading stuff from the internet.

I still dont know how to tell it to get install files from my other pc and not from the internet.

---

