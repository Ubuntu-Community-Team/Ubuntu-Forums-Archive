---
title: "cant boot to Ubuntu but windows runs perfectly"
date: 2012-07-31
forum: Installation &amp; Upgrades
---

### Post by johnnycatt on 2012-07-31
I installed Ubuntu 10.04 beside Windows 7 (not wubi). It seemed to work well except for a monitor problem which I think I had worked out.

I then upgraded to Ubuntu 11... it seemed to go ok.

I upgraded to Ubuntu 12.

After that, I could not boot either Ubuntu 12 or Windows7 

I installed boot-restore (I think that is the name of it) using LiveCD.

the computer will now boot straight to Windows7 ONLY!

I used liveCD and ran "fdisk-l" and it shows if have 3 "fat", 2 ubuntu and one other partition. 

I looked at the harddrive using the Windows 7 program and it ONLY shows the 148MB for Windows (not the rest of the 320MB of the harddrive).

on my other desktop computer, when I turn on the computer, it gives me a menu to choose either windows or Linux.  The Computer in Question here never gives me an option .

how do I get my Ubuntu??

---

### Post by drs305 on 2012-07-31
Was the app Boot Repair?  If not, install it while on the LiveCD Desktop and run the "Recommended Repair". If it fails to fix things, you can run the boot info script from the same app. Post the contents or link of the file it generates and we can take a look.

A link to Boot Repair is in my signature line.

---

### Post by johnnycatt on 2012-07-31
drs, 
yes, boot repair was what I ran.. after teh upgrade to Ubuntu 12 when I restarted, all it gave me was a black screen that said somehting like "boot restore>" or something like that.  I cam to the forum and searched for that term and the thread said to try "boot-repair."  after I ran it I got Window7 back and it game me this address:

[http://paste.ubuntu.com/1119247/](http://paste.ubuntu.com/1119247/)

that was the first one...  I ran it again, hoping it might "add" Ubuntu on the 2nd try since it seemed to "find" Windows7 on the first try.

the 2nd address it gave was:


[http://paste.ubuntu.com/1120503/](http://paste.ubuntu.com/1120503/)

---

### Post by johnnycatt on 2012-07-31
btw... I'm a huge Jeffersonian, too, bro!

---

### Post by joco1500 on 2012-07-31
Just delete the ubuntu patron and use wubi
it installs the newest version of ubuntu

wubi works on old computers all the way down to windows me (2000)

---

### Post by drs305 on 2012-07-31
Grub isn't installed and for some reason Boot Repair didn't install it either. There is a message "Error: Can't have a partition outside the disk!" but I am not sure if that is the problem.  Grub won't install if it cannot locate the proper boot files.

I would try to mount the Ubuntu partition (sda6) from the LiveCD and see if you have the necessary files. 

```
sudo mount /dev/sda6 /mnt
sudo ls /mnt/boot # Do you see the kernel (vmlinuz-X-XX-..... and initrd.img-X.XX...)
sudo ls /mnt/boot/grub # Are there any *.mod files.

```

If the kernel and initrd images are on the partition and the partition mounts and is readable, Boot Repair has an advanced option to install Grub2 via chroot. You might try installing GRUB via this procedure.

If it fails and you lose your Windows boot, you can restore Windows by running the following 2 commands (don't run the others the terminal suggests):

```

sudo apt-get install lilo
sudo lilo -M /dev/sda1 mbr

```

There is a link in my signature line about Chroot but I'd use Boot Repair and only reference the Chroot link for more information on what is happening.

---

### Post by johnnycatt on 2012-07-31
OK, MY DUMBA$$ qustion of the day:

what's a Kernel?

---

### Post by johnnycatt on 2012-07-31
sudo mount /dev/sda6 /mnt  -- went ok

sudo ls /mnt/boot  -- gave teh following message:

ls: cannot access /mnt/boot: no such file or directory

---

### Post by drs305 on 2012-08-01
It appears that you don't have either the /boot files and/or the /boot folder. This contains the initrd image used to initially boot. The 'kernel' is the 'engine' of the OS. The major version (3.0.0,-... 3.0.2-..., etc) varies from release to release is updated within the release (3.0.2-23, 3.0.2-24, etc). Your system must find that file to boot.

Did you try to make a separate /boot partition? I don't see an additional partition on your computer. A separate /boot partition is normally not necessary. If you did try to make a separate /boot partition it's possible the partition error message may be a factor.

If this is a new installation and you don't have a lot of configuration modifications or data on the Ubuntu partition, it might be faster to reinstall rather than try to troubleshoot - but that is up to you.

If you want to try to find the boot folder, mount the Ubuntu partition again and open nautilus as 'root' (gksu nautilus /mnt). Explore the contents of the partition. If you can't find the boot folder (in this case under /mnt/boot) your installation probably was not successful.

---

### Post by johnnycatt on 2012-08-01
To be honest, I would love to "re-install."  I just don;t want to loose the 1/2 of my harddrive that has the Ubuntu that isn't accessible right now!

If we can do that, I will re-install... I'd prefer to re-install with a liveCD.  The biggest thing I worry about is losing that 1/2 of my harddrive.  I DON'T want to install ubuntu on the same partition as Windows7 and then divide that 1/2 of the partition.

does that make sence?

---

### Post by oldfred on 2012-08-02
If you use any of the auto install options, you may lose something as it automatically shrinks some partition to make room for the new install.

But if you use Something Else or manual install you will just overwrite the current install of Ubuntu. Just be sure to choose the same partition for / (root) as your current one & its format ext4. It should find swap. If you have the separate partition for /home choose it also. If you have any data you want saved DO NOT reformat it.

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

---

