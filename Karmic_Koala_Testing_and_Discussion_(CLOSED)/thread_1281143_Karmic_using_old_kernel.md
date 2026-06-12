---
title: "Karmic using old kernel"
date: 2009-10-02
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by thecow on 2009-10-02
Hello I recently updated to the Karmic beta.  When I type uname -r I get the following:

$ uname -r
2.6.30-020630-generic


When using 9.04 I had updated to this kernel version because of some fixes I was looking for.  However Karmic uses 2.6.31 so it's odd to me that this isn't the kernel version being used.  During bootup if I hit 'esc' during Grub startup I see no entry for 2.6.31.  

Ive already tried the sudo update-grub command and restarted, however it doesn't allow me to use 2.6.31

Any help would be appreciated

---

### Post by thecow on 2009-10-03
Alright well I tried to change /boot/grub/menu.lst by adding in the appropriate fields i.e:

## ## End Default Options ##

title		Ubuntu 9.10, kernel 2.6.31-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.31-11-generic root=UUID=46cb7bd8-65c6-4d3b-8bc9-3536fa175995 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-11-generic
quiet


title		Ubuntu 9.04, kernel 2.6.30-020630-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.30-020630-generic root=UUID=46cb7bd8-65c6-4d3b-8bc9-3536fa175995 ro quiet splash 
initrd		/boot/initrd.img-2.6.30-020630-generic
quiet

title		Ubuntu 9.04, kernel 2.6.30-020630-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.30-020630-generic root=UUID=46cb7bd8-65c6-4d3b-8bc9-3536fa175995 ro  single
initrd		/boot/initrd.img-2.6.30-020630-generic




I added in the top one in what I thought was the same format as whats listed below it.  However during boot it gives me an error and will not continue

---

### Post by thecow on 2009-10-03
This is in the wrong place presumably so could a mod delete this?

---

### Post by diebels on 2009-10-03
Check if you got the 31 kernel installed
```
dpkg --get-selections | grep linux-image
```

---

### Post by thecow on 2009-10-03
$ dpkg --get-selections | grep linux-image
linux-image-2.6.22-14-generic			install
linux-image-2.6.24-16-generic			deinstall
linux-image-2.6.24-17-generic			deinstall
linux-image-2.6.24-18-generic			deinstall
linux-image-2.6.24-19-generic			deinstall
linux-image-2.6.24-21-generic			install
linux-image-2.6.27-11-generic			deinstall
linux-image-2.6.27-7-generic			deinstall
linux-image-2.6.27-9-generic			deinstall
linux-image-2.6.28-11-generic			deinstall
linux-image-2.6.28-15-generic			deinstall
linux-image-2.6.30-020630-generic		install
linux-image-2.6.31-11-generic			install
linux-image-generic				install

---

### Post by VMC on 2009-10-03
I'm curious about what grub your using. output
```
ls /boot/grub/grub*
```

---

### Post by thecow on 2009-10-03
$ ls /boot/grub/grub*
/boot/grub/grubenv

---

### Post by VMC on 2009-10-03
> **thecow said:**
> $ ls /boot/grub/grub*
/boot/grub/grubenv

It appears your missing grub.cfg

Maybe it got deleted. type ```
sudo update-grub
```

---

### Post by thecow on 2009-10-03
```
sudo update-grub
[sudo] password for : 
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz
Found kernel: /boot/vmlinuz-2.6.31-11-generic
Found kernel: /boot/vmlinuz-2.6.30-020630-generic
Found kernel: /boot/vmlinuz-2.6.24-21-generic
Found kernel: /boot/vmlinuz-2.6.22-14-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done
```


Then:

```
ls /boot/grub/grub*
/boot/grub/grubenv
```

Didn't seem to fix it

---

### Post by VMC on 2009-10-03
Are you logged on to the machine your trying to fix?
Let's see what's all there.

```
ls /boot/grub
```

---

### Post by thecow on 2009-10-03
```
$ ls /boot/grub
default        fat_stage1_5       jfs_stage1_5  menu.lst.bak1      stage1
device.map     grubenv            menu.lst      minix_stage1_5     stage2
e2fs_stage1_5  installed-version  menu.lst~     reiserfs_stage1_5  xfs_stage1_5
```

And yes I am presently sitting at the machine

---

### Post by thecow on 2009-10-03
Maybe you could give me an example of what should be in grub.cfg and see if that solves this issue?  It seems that 2.6.31 is indeed installed based off what I posted above, it's just having trouble booting from it

---

### Post by VMC on 2009-10-03
You are running karmic, correct?

If so, then type this

```
sudo blkid
```

---

### Post by thecow on 2009-10-03
```
$ sudo blkid
[sudo] password for brian: 
/dev/sda1: UUID="46cb7bd8-65c6-4d3b-8bc9-3536fa175995" TYPE="ext3" 
/dev/sda5: UUID="19186006-90dc-403e-b9b9-bee22828867c" TYPE="swap" 
```

Heres the sequence of events I went through.  I was on 9.04 then I typed 'update-manger -d'.  I then proceeded to download all the updates for 9.10.  At some point it asked me if I wanted to keep my version of menu.lst, however it said it had made changes to it.  So I said yes thinking I could keep my old linux-images and use the new one as it changed it.  It then finished and restarted my computer, it first looked like it was booting into 9.04 but then the screen changed colors and styles to that of 9.10.  So I really have no idea what is going on

---

### Post by VMC on 2009-10-03
> **thecow said:**
> ```
$ sudo blkid
[sudo] password for brian: 
/dev/sda1: UUID="46cb7bd8-65c6-4d3b-8bc9-3536fa175995" TYPE="ext3" 
/dev/sda5: UUID="19186006-90dc-403e-b9b9-bee22828867c" TYPE="swap" 
```

Heres the sequence of events I went through.  I was on 9.04 then I typed 'update-manger -d'.  I then proceeded to download all the updates for 9.10.  At some point it asked me if I wanted to keep my version of menu.lst, however it said it had made changes to it.  So I said yes thinking I could keep my old linux-images and use the new one as it changed it.  It then finished and restarted my computer, it first looked like it was booting into 9.04 but then the screen changed colors and styles to that of 9.10.  So I really have no idea what is going on

I see now. I couldn't figure out how you were still on grub-legacy.

I just read up on this
"GRUB 2 will be installed by default on NEW installations of Karmic. If you have upgraded from Jaunty 9.04 to Karmic 9.10 you can follow the install instructions for Jaunty 9.04 below."

From [**_this_**]("https://wiki.ubuntu.com/Grub2") site. Please read that info and follow the instructions listed **below**. Then come back here.

Edit: correction. Follow [THIS]("https://wiki.ubuntu.com/KernelTeam/Grub2Testing") site instructions.

---

### Post by thecow on 2009-10-03
Haha, well I followed the first set.  And now it won't boot.  And with that I think its time I go and take my mind off Linux before I hurt this laptop

---

### Post by itsjareds on 2009-10-03
Woah, didn't see a second page here, my comment doesn't make sense now :)

-- post removed --

---

