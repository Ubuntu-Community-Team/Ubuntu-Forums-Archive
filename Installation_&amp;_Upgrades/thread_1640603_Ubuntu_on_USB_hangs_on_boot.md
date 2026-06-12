---
title: "Ubuntu on USB hangs on boot"
date: 2010-12-08
forum: Installation &amp; Upgrades
---

### Post by Inquirer002 on 2010-12-08
I loaded Ubuntu onto my USB using the USB installer, and then attempted to create a persistent drive (>4GB) according to the link :[http://www.pendrivelinux.com/create-a-larger-than-4gb-casper-partition/](http://www.pendrivelinux.com/create-a-larger-than-4gb-casper-partition/)

But when I boot from the USB it hangs. I am new to Ubuntu, so I cannot give a lot of details.

When booting from the USB, it goes to the setup screen where I select boot from the USB. A list of commands appear on the screen (it's too quick,to read) and then it arrives at the intro screen with the Ubuntu symbol. On this screen it hangs. 

Any suggestions on how to fix this.

---

### Post by sikander3786 on 2010-12-08
Try adding some boot parameters.

There are 6 of them and you might need to try all of them, one-by-one. I suspect nomodeset or acpi=off might work.

Press F6 to access them.

[https://help.ubuntu.com/community/LiveCDBootOptions#Main%20Page%20Options](https://help.ubuntu.com/community/LiveCDBootOptions#Main%20Page%20Options)

---

### Post by Inquirer002 on 2010-12-08
Thanks for the help! I shall take a look at the link and attempt that. 

A couple of points that might be of help. I reinstalled ubuntu using the USB installer and selected 'persistent 4GB' as one of its options (instead of creating a separate casper-rw partition). It now boots fine, but the problem is that I would like to use more than 4GB and the USB installer doesn't have that option. 
I also also took a look at the my flash drive using GParted and I noticed something I thought was strange. The Mount Point for this usb is listed as /cdrom. Should that be the parameter?

---

### Post by C.S.Cameron on 2010-12-08
Since the txt.cfg file has already been modified by the USB installer just delete the casper-rw file and create the casper-rw partition as ext2. 3 or 4.

You can also create an ext2, 3 or 4 partition and name it home-rw, it will only save your home folder.

---

### Post by Inquirer002 on 2010-12-08
The partition I had made when it hanged was a casper-rw ext2 partition. Now I created a casper-rw ext4 and it works...so far :)

Thanks for the help!

---

