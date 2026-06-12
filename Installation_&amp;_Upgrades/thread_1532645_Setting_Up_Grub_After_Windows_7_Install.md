---
title: "Setting Up Grub After Windows 7 Install"
date: 2010-07-16
forum: Installation &amp; Upgrades
---

### Post by Trilby on 2010-07-16
I have a laptop which this morning had Ubuntu installed on it with no partitioning. Since then I have partitioned the hard-drive into three sections: A partition called "William", the original Ubuntu partition and a general data storage partition called "DATA" (in that order). I then installed Windows 7 Professional 64-Bit on the William partition with no problems to speak of. I have been following the instructions on how to re-enable grub & grub2 after a Windows install at [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

At the final stage, I am required to input into terminal:

```
ubuntu@ubuntu:~$ sudo grub-install  --root-directory=/media/5bb17d6a-493b-4561-855d-7a9033a30b8b /dev/sda2
```Where the 5bb1... and sda2 were identified in previous stages of the instructions.
However, instead of getting:

```
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)   /dev/sda
```I get:

```
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/media/5bb17d6a-493b-4561-855d-7a9033a30b8b /dev/sda2
/usr/sbin/grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea..
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and its use is discouraged..
/usr/sbin/grub-setup: error: if you really want blocklists, use --force.
```What should I do?

Many thanks,
Trilby.

---

### Post by NFblaze on 2010-07-16
I think you want ubuntu@ubuntu:~$ sudo grub-install --root-directory=/media/5bb17d6a-493b-4561-855d-7a9033a30b8b **/dev/sda**

Not /dev/sda2

Grub has to go in the MBR. Which is the first 512 of the hard-disk. Which isnt really a partition.

Give it a whirl.

---

### Post by drs305 on 2010-07-16
NFblaze is correct, and I took a look at the document you linked to make sure the instructions are correct. They are - don't add the partition at the end of the command (use **sda** and *not* sda2).

If it doesn't see your Windows partition when you reboot, run "sudo update-grub" and it will usually find it the second time.

---

### Post by lindsay7 on 2010-07-16
Here is the was to do this.

[http://www.webupd8.org/2009/12/how-to-recover-grub2-linux.html](http://www.webupd8.org/2009/12/how-to-recover-grub2-linux.html)

---

### Post by Trilby on 2010-07-16
I have grub back
Thanks guys, you've all be very helpful :-)

---

