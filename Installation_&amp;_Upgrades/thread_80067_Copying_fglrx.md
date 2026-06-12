---
title: "Copying fglrx"
date: 2005-10-21
forum: Installation &amp; Upgrades
---

### Post by cherryos on 2005-10-21
hi, i need to copy the fglrx graphics driver from a disk. there's 2 files,
fglrx-driver_8.16.20-1_i386.deb and fglrx-kernel-src_8.16.20-1_i386.deb
but i'm not sure where to copy them. I think it's /etc/video/drivers/. is that right? or is it some other directory? also, what's the right command to copy the files?

---

### Post by Kyral on 2005-10-21
You don't NEED to copy them from the disk to use them.

First read my Terminal for Beginners (In the little block below) to learn how to navigate the command line (and how to copy files BTW). Then just navigate to where the deb files reside and 

```
sudo dpkg -i <filename>
```

For each file

---

### Post by cherryos on 2005-10-21
the driver isn't on the hdd. that's the problem. The system always freezes after I login, and I searched and found that the problem was my radeon graphics card, I needed to install the fglrx driver. So i downloaded it, put it on a disk, but now I don't know what to do with it. Someone told me to copy it to the /etc/video/drivers directory, but I don't have one.

---

### Post by Kyral on 2005-10-21
Ah.

Okay drop to a VT (Virtual Terminal) with CTRL+ALT+F1 (You can get back to X with CTRL+ALT+F7) and login there. Put the disc (Floppy or CD?) in the drive and mount it with

```
sudo mount /media/floppy
```

if its a Floppy or

```
sudo mount /media/cdrom
```

if its a CD.

CD into that directory and use the dpkg commands from there

---

### Post by cherryos on 2005-10-21
I did sudo dpkg --install and then the 2 files. but after i did and tried to log in, a grey box came up and it froze. I tried reconfiguring xserver but that didn't help. did i use the wrong instruction?

---

### Post by Kyral on 2005-10-21
Was it this

sudo dpkg -i  fglrx-driver_8.16.20-1_i386.deb fglrx-kernel-src_8.16.20-1_i386.deb

---

### Post by cherryos on 2005-10-22
no, it was

sudo dpkg --install fglrx-driver_8.16.20-1_i386.deb

sudo dpkg --install fglrx-kernel-src_8.16.20-1_i386.deb

---

### Post by Kyral on 2005-10-23
Try it the way I did

Though -i and --install should be interchangable....

---

### Post by cherryos on 2005-10-23
sweet, I got it.

The installation gave me an error, so I had to run sudo apt-get and install all the missing packages. then i installed the deb file, modified xorg.conf and it worked fine. Thanks for the help. Now I'm finally dual booting.

---

