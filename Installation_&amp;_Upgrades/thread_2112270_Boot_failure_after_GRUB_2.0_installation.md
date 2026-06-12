---
title: "Boot failure after GRUB 2.0 installation"
date: 2013-02-04
forum: Installation &amp; Upgrades
---

### Post by dorruk on 2013-02-04
I have been dual booting Win 7 and Linux for a while. Recently I updated to Win 8 Pro keeping Win 7. As a result, GRUB bootloader was replaced with Windows bootloader. So I couldn't get into Ubuntu.

I found this app it's called BOOTICE. I used it to change my MBR which replaced _Windows NT 6.x_ to _GRUB 2.0_ hoping to get Ubuntu back working.

Now the PC won't boot. I get the following:
```
error: file not found
grub rescue>
```
And I get a command line in which I can move around.

So the only USB drive I have is this 256MB drive. GParted Live is installed on it. I looked up my drive by booting on the GParted Live USB and my files/partitions are still there. Since the drive is 256MB, installing Boot-Repair or Ubuntu Live is no option.

So is there a way to fix the boot sector/MBR and write GRUB on it? GParted Live also has TestDisk but I don't know which type of MBR to choose, when both Windows and Linux are installed.

---

### Post by darkod on 2013-02-04
You don't have your ubuntu cd at hand? It should always be at hand. :)

Grub is not just the small part of code on the MBR, it has to "know" where to look for the rest of the files, to connect to them. Installing grub2 only on the MBR can rarely help (it can help only if the other files are present correctly and you tell it where they are during the install to the MBR).

If there is REALLY no way to make an ubuntu cd/usb, you can try Sustem Rescue CD. It's smaller than ubuntu but not sure if there is a version that fits on 256MB. I think it's 300+MB.

If you can boot the system rescue you can chroot into your installation and install grub2 properly from within.

Other options that should fit on 256MB and have live mode option could be Damn Small Linux or Puppy Linux if I remember correctly.

Once you get any linux that can boot you to command prompt or terminal in live mode, if you are not sure about the chroot procedure ask.

---

### Post by dorruk on 2013-02-04
Is there any way of doing the same from GParted Live's terminal? It's a Linux terminal after all, right?

Thing is, is another distro than GParted Live required? Because I'm not comfortable with installing new live usb operating systems while the one on my USB is already working, I always screw it up :P . Just that I don't want to lose the one that I have at hand, while trying to install another OS.

---

### Post by schragge on 2013-02-04
You can try to boot from the grub prompt:
```

grub rescue> search.file /boot/grub/grub.cfg root
grub rescue> set prefix=($root)/boot/grub
grub rescue> configfile /boot/grub/grub.cfg
grub rescue> boot

```

---

### Post by srekcahrai on 2013-02-04
[http://www.ehow.com/how_10030196_use-grub-rescue.html](http://www.ehow.com/how_10030196_use-grub-rescue.html)

---

### Post by dorruk on 2013-02-04
> **srekcahrai said:**
> [http://www.ehow.com/how_10030196_use-grub-rescue.html](http://www.ehow.com/how_10030196_use-grub-rescue.html)

How do I identify the boot partition?
This is what I get when I type "ls":
```
(hd0) (hd0, msdos7) (hd0, msdos6) (hd0, msdos5) (hd0, msdos3) (hd0, msdos2) (hd0, msdos1)
```

---

### Post by darkod on 2013-02-04
> **dorruk said:**
> Is there any way of doing the same from GParted Live's terminal? It's a Linux terminal after all, right?

Thing is, is another distro than GParted Live required? Because I'm not comfortable with installing new live usb operating systems while the one on my USB is already working, I always screw it up :P . Just that I don't want to lose the one that I have at hand, while trying to install another OS.

You might be able to use it, I have never tried using Gparted live. I assume you know which one is your root partition, if you don't you can check with Gparted.
Also, I guess Gparted live will load as root so you don't need to run sudo in front of commands (sudo is for ubuntu anyway).

As stated above, you might be able to boot from the rescue prompt too. There are many options. If the procedure above to boot from the prompt doesn't work, tell me which is your root partition and I can help with the chroot.

---

### Post by darkod on 2013-02-04
> **dorruk said:**
> How do I identify the boot partition?
This is what I get when I type "ls":
```
(hd0) (hd0, msdos7) (hd0, msdos6) (hd0, msdos5) (hd0, msdos3) (hd0, msdos2) (hd0, msdos1)
```

Well, which one is your root partition? You don't know?

---

### Post by schragge on 2013-02-04
Search for some file that you know is on it
```
grub rescue> help search.file
```

---

### Post by dorruk on 2013-02-04
> **darkod said:**
> Well, which one is your root partition? You don't know?

Well I know it is dev/sda2 but what I get from "ls" is not likely close to it?

---

### Post by schragge on 2013-02-04
Then it is (hd0, msdos2)

---

### Post by darkod on 2013-02-04
> **schragge said:**
> Then it is (hd0, msdos2)

Correct. If you need to do the chroot, say so.

---

### Post by dorruk on 2013-02-04
> **darkod said:**
> Correct. If you need to do the chroot, say so.

What is chroot? It seems to have lots of uses but how does that apply to boot problems particularly?

---

### Post by dorruk on 2013-02-04
By the way, when I got to the command "insmod normal", it says error:unknown filesystem.
It is ntfs. What now?

---

### Post by schragge on 2013-02-04
Then it is the wrong (Windows) partition. What
```
grub rescue> set
``` says?

---

### Post by dorruk on 2013-02-04
> **schragge said:**
> Then it is the wrong (Windows) partition. What
```
grub rescue> set
``` says?

```
prefix=(hd0,msdos2)/boot/grub,
root=(hd0,msdos2),
```

I can post a GParted screenshot if necessary.

---

### Post by darkod on 2013-02-04
Hold on, when we are talking about the ubuntu root partition, that's the root partition of your ubuntu install. It can't be ntfs since it doesn't install on ntfs.

Is /dev/sda2 where you put win8/win7, or ubuntu?

The chroot is a procedure to enter inside a linux installation, so any command you run will be like run from within. It can help in a way that it will install its grub2 on the MBR of the disk.

---

### Post by dorruk on 2013-02-04
dev/sda2 is Windows 7, which the computer came pre-installed in.
I have not changed the bootflag location ever since, and installed Win 8 and Ubuntu besides Win 7.

Now, should I move the bootflag to Ubuntu partition or sth? Or is it enough to set Ubuntu partition as root on grub rescue?

---

### Post by schragge on 2013-02-04
Ok, what do you get after this:
```

grub> search.file /boot/grub/grub.cfg root
grub> set prefix=($root)/boot/grub
grub> set

```

---

### Post by dorruk on 2013-02-04
search.file is an unknown command :/
But ubuntu is installed on dev/sda7 if that's what you're looking for

---

### Post by schragge on 2013-02-04
Then try this instead:
```

grub> search --file /boot/grub/grub.cfg --set root

```

The rest is the same

---

### Post by dorruk on 2013-02-04
Unknown command "search".

As I have mentioned, Ubuntu is on dev/sda7.

---

### Post by schragge on 2013-02-04
> **dorruk said:**
> But ubuntu is installed on dev/sda7 if that's what you're looking for Ah, good.Then
```

set root=(hd0, msdos7)
set prefix=($root)/boot/grub
insmod normal
normal

```

---

### Post by dorruk on 2013-02-04
Ok this is how it went:
```
grub rescue> set root=(hd0,msdos7),
grub rescue> set prefix=(hd0, msdos7)/boot/grub,
grub rescue> insmod normal
error: missing ')'
grub rescue> insmod normal)
error: no such partition
grub rescue> ls
(partitions are still there)
grub rescue> set
prefix=(hd0,
root=(hd0,msdos7),
```

There are no spelling errors, just wrote it down as is.

EDIT: Sorry about that. Just figured out my mistake. In set prefix, I added an unnecessary space.

---

### Post by dorruk on 2013-02-04
Fixing the wrong prefix string, now insmod normal replies:
error: unknown filesystem.
It is ext4. Any ideas?

---

### Post by schragge on 2013-02-04
You somehow missed the closing ')' on 'set root'. Do you entered the comma as the last character? Don't do it. After setting both 'root' and 'prefix'
```
grub> set
``` should show
```

root=(hd0,msdos7),
prefix=(hd0,msdos7)/boot/grub,

```

---

### Post by dorruk on 2013-02-04
That's what I exactly see at the moment. Still insmod normal won't work.

---

### Post by schragge on 2013-02-04
Hmm,

[LIST=1]
[*]You're booting from your harddisk, right? Not from GParted? If the latter, it seems that grub in your GParted doesn't support ext4. What GParted version it is?
[*]Are you sure /dev/sda7 is the Ubuntu partition?
[/LIST]

---

### Post by schragge on 2013-02-04
Ah, sorry, I see. You installed GRUB into MBR with BOOTICE. The version of Grub on BOOTICE probably differs from the version of GRUB in Ubuntu. Can you find some LiveCD with the same Ubuntu version like in your Ubuntu partition and boot from it?

---

### Post by darkod on 2013-02-04
I am not sure how chroot works from Gparted Live, since you have no other linux to boot. Try this in terminal:
(I assume you will be root, or first google how to execute root commands in Gparted Live terminal)
```
mount /dev/sda7 /mnt
mount --bind /proc /mnt/proc
mount --bind /dev /mnt/dev
mount --bind /sys /mnt/sys
chroot /mnt
grub-install /dev/sda
exit
umount /mnt/sys
umount /mnt/dev
umount /mnt/proc
umount /mnt
```

That is a chroot procedure. Hope fully it will work.

And get a new usb stick, it least 1GB and make it ubuntu live usb, and keep it. :)

---

### Post by schragge on 2013-02-04
Another option is to try kexec if it comes installed with GParted.
Something like this:
```

mount -t ext4 /dev/sda7 /mnt
kexec -l /mnt/vmlinuz --append=root=/dev/sda7 --initrd=/mnt/initrd.img
kexec -e

```

---

### Post by srekcahrai on 2013-02-04
> **dorruk said:**
> Well I know it is dev/sda2 but what I get from "ls" is not likely close to it?
(hd0, msdos2)

---

### Post by dorruk on 2013-02-05
> **darkod said:**
> I am not sure how chroot works from Gparted Live, since you have no other linux to boot. Try this in terminal:
(I assume you will be root, or first google how to execute root commands in Gparted Live terminal)
```
mount /dev/sda7 /mnt
mount --bind /proc /mnt/proc
mount --bind /dev /mnt/dev
mount --bind /sys /mnt/sys
chroot /mnt
grub-install /dev/sda
exit
umount /mnt/sys
umount /mnt/dev
umount /mnt/proc
umount /mnt
```

That is a chroot procedure. Hope fully it will work.

And get a new usb stick, it least 1GB and make it ubuntu live usb, and keep it. :)

When I get to "chroot /mnt" it says ```
chroot: failed to run command '/bin/bash': Exec command error.
```

---

### Post by dorruk on 2013-02-05
> **schragge said:**
> Another option is to try kexec if it comes installed with GParted.
Something like this:
```

mount -t ext4 /dev/sda7 /mnt
kexec -l /mnt/vmlinuz --append=root=/dev/sda7 --initrd=/mnt/initrd.img
kexec -e

```

kexec: command not found.

---

### Post by dorruk on 2013-02-05
Ok just borrowed the neighbors usb (should have thought of that earlier :D), installed ubuntu live, then boot-repair and now it's working. Boot-repair summary: [http://paste.ubuntu.com/1613807/](http://paste.ubuntu.com/1613807/)

This better teach me a lesson that I should keep an Ubuntu disc with me at all times.

---

### Post by darkod on 2013-02-05
It looks like you can't do it from Gparted Live, as I assumed. It is not a "full" linux distro.

I can't understand what is the problem using the same stick for Damn Small Linux or Puppy Linux. You said it would overwrite Gparted Live. So what, it's not even a full distro, as you can see yourself. It serves only for partitioning, and you have partitioning tools in one form or another (GUI or command line) in the mentioned distros too.

So, you don't lose anything by overwriting Gparted Live, but you can gain much. It's up to you.

Investigate first and confirm that the distro you want to use can fit on the stick.

---

### Post by dorruk on 2013-02-05
> **darkod said:**
> It looks like you can't do it from Gparted Live, as I assumed. It is not a "full" linux distro.

I can't understand what is the problem using the same stick for Damn Small Linux or Puppy Linux. You said it would overwrite Gparted Live. So what, it's not even a full distro, as you can see yourself. It serves only for partitioning, and you have partitioning tools in one form or another (GUI or command line) in the mentioned distros too.

So, you don't lose anything by overwriting Gparted Live, but you can gain much. It's up to you.

Investigate first and confirm that the distro you want to use can fit on the stick.

Then that would be #1 on my to-do-list, while my computer's now working. Thanks a lot!

---

