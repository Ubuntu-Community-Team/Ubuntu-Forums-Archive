---
title: "install Grub using Live-CD"
date: 2011-06-20
forum: Installation &amp; Upgrades
---

### Post by cccc on 2011-06-20
hi

Howto install Grub into a ubuntu partition using ubuntu Live-CD 10.04?
I've tried the following, but it doesn't work:```

$ sudo passwd root
Enter new UNIX password: 
Retype new UNIX password: 
passwd: password updated successfully
ubuntu@ubuntu:~$ su
Password: 
root@ubuntu:/home/ubuntu# grub-install /dev/sda2
/usr/sbin/grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?).
No path or device is specified.
Try `/usr/sbin/grub-probe --help' for more information.
Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.
```

Howto specify module option `--modules'?

---

### Post by cccc on 2011-06-20
I've tried the following:```

# sudo mount /dev/sda2 /mnt
root@ubuntu:/home/ubuntu# sudo grub-install --root-directory=/mnt /dev/sda2
/usr/sbin/grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea..
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and its use is discouraged..
/usr/sbin/grub-setup: error: if you really want blocklists, use --force.

# **sudo grub-install --root-directory=/mnt /dev/sda2 --force**
/usr/sbin/grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea..
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and its use is discouraged..
Installation finished. No error reported.

```but after restart I get just grub command line -> **grub>**

---

### Post by drs305 on 2011-06-20
The normal commands to install Grub2 would be:
```
sudo mount /dev/sdXY # Example: sudo mount /dev/sda1
sudo grub-install --root-directory=/mnt /dev/sdX # Example: sudo grub-install --root-directory=/mnt /dev/sda
```

The way you installed it, G2 was installed onto the partition, which is not recommended unless you have a particular need for it. That's why you had to use the '--force' command.

Using the commands in this post, the drive's MBR contains information which then points to the Grub files in the Ubuntu's installation. The method is much more forgiving if the boot files are moved around; just make sure the BIOS first attempts to boot the drive listed in the command.

---

### Post by nzjethro on 2011-06-20
Is the problem because you are attempting to install it to a partition rather than to a drive? Try again
```
# sudo mount /dev/**sda** /mnt
root@ubuntu:/home/ubuntu# sudo grub-install --root-directory=/mnt /dev/sda2
```

instead of ***sda5***

---

### Post by YesWeCan on 2011-06-20
grub-install --force /dev/sda2

It will still whine a lot but it will do it. :)
The reason it whines is that it is possible for it to stop working suddenly if the location on disk of one of the Grub files changes for any reason. This is not an issue when Grub is installed to the MBR sectors.

[edit]drs305 has it covered for installing it using CD.

---

### Post by cccc on 2011-06-20
> **YesWeCan said:**
> grub-install --force /dev/sda2

It will still whine a lot but it will do it. :)
The reason it whines is that it is possible for it to stop working suddenly if the location on disk of one of the Grub files changes for any reason. This is not an issue when Grub is installed to the MBR sectors.

[edit]drs305 has it covered for installing it using CD.

still doesn't work:```

# grub-install --force /dev/sda2
/usr/sbin/grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?).
No path or device is specified.
Try `/usr/sbin/grub-probe --help' for more information.
Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.

# mount /dev/sda2 /mnt
root@ubuntu:/home/ubuntu# install-grub --force --root-directory=/mnt /dev/sda2
install-grub: command not found

# grub-install --force --root-directory=/mnt /dev/sda2
/usr/sbin/grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea..
/usr/sbin/grub-setup: **[COLOR="Red"]warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and its use is discouraged..[/COLOR]**
Installation finished. No error reported.

```

---

### Post by cccc on 2011-06-20
> **nzjethro said:**
> Is the problem because you are attempting to install it to a partition rather than to a drive? Try again
```
# sudo mount /dev/**sda** /mnt
root@ubuntu:/home/ubuntu# sudo grub-install --root-directory=/mnt /dev/sda2
```

instead of ***sda5***

Thx, but pls go to the top and see my second posting.

---

### Post by drs305 on 2011-06-20
> 
# grub-install --force --root-directory=/mnt /dev/sda2
/usr/sbin/grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea..
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and its use is discouraged..
Installation finished. No error reported.

Although it complained, if you look at the last line G2 was most likely successfully installed on the partition.

You can check by running the boot info script - click on the "BIS" link in my signature line. Download and extract the script, then run it and check the contents of RESULTS.txt

---

### Post by YesWeCan on 2011-06-20
That warning message is pants. :P
"This is impossible. This is really not a good idea. Ok I have done it."

What it is trying to say is that it does not do embedding but what it can do may be unreliable. Why it bothers to mention something it cannot do that most users won't have heard of anyway is another matter.


Anyhow, is this really what you want to do? If you want to boot the partition you need to set the boot flag for it in the MBR.

---

### Post by cccc on 2011-06-21
Thx a lot, but howto install Grub into MBR of the hard disk using Ubuntu Live-CD?

---

### Post by drs305 on 2011-06-21
> **cccc said:**
> Thx a lot, but howto install Grub into MBR of the hard disk using Ubuntu Live-CD?

When you run "grub-install" with the correct "--root-directory" switch (see previous posts) the information will be porperly written to the MBR.

See Post #3, but be sure to use the correct partition number for your Ubuntu partition.

---

