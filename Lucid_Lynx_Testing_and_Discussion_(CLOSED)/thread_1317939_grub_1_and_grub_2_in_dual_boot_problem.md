---
title: "grub 1 and grub 2 in dual boot problem"
date: 2009-11-07
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by joepotter on 2009-11-07
I have a karmic install on /dev/sda1 that was upgraded over the course of the testing cycle and has ext3 with legacy grub on it. 

I installed karmic after release over the other karmic install on /dev/sda5 to test the installer and to use as the testing install for lucid.

However, it will not boot. I got an error saying that the files on that partition were incompatible. Error 13 if I remember correctly.

Is there any reason that the legacy grub in the mbr will not allow a grub 2 install on /dev/sda5 to boot?

---

### Post by dino99 on 2009-11-07
some guys already talk about installer problem which don't really install where user ask to be.

Seem that a is show stopper right now.

---

### Post by joepotter on 2009-11-07
> **dino99 said:**
> Seem that a is show stopper right now.

Hey, thanks for that information. No wonder it failed, so back to the drawing board for me.

---

### Post by Trog on 2009-11-07
oops, wrong place to paste, just ignore me.

---

### Post by slakkie on 2009-11-07
What you could do is creating a seperate grub parition so your system boots that grub and chainloads it to the other OS.

I advise you to have a Live CD ready, so you can perform all actions from the Live CD, or have it ready in case your machine doesn't want to boot (which could happen since we are messing with the bootloaders :)).

Create a small partition (/dev/sda1 in my case), make it 20MB or so, then do the following:

```

mkdir /mnt/bootdisk
sudo mount -t ext3 /dev/sda1 /mnt/bootdisk
grub-install --root-directory=/mnt/bootdisk sda1

```

(Details can be found here: [http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-using-grub_002dinstall.html](http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-using-grub_002dinstall.html) )

Change the menu.lst file in /mnt/bootdisk/boot/grub

```

sudo vi /mnt/bootdisk/boot/grub/menu.lst

```

```

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

#
# Default chainloading for grub-legacy to other slices
#
# Debian is the default OS
default         1
timeout         10

#hiddenmenu

color cyan/blue black/blue

title Ubuntu /dev/sda2
root (hd0,1)
chainloader +1

title Debian /dev/sda3
root (hd0,2)
chainloader +1

title Misc /dev/sda5
root (hd0,4)
chainloader +1

```

My Debian box has grub2 and my Ubuntu has grub-legacy. This way I have one bootloader which always allows an OS to have whatever bootloader they need/want/require.

You would need to run some grub commands to install it propperly.. as described here:
[http://orgs.man.ac.uk/documentation/grub/grub_3.html#SEC9](http://orgs.man.ac.uk/documentation/grub/grub_3.html#SEC9)

```

sudo grub
# You are now in a grub shell
grub> root (hd0,0)

grub> find /boot/grub/stage1
 (hd0,0) # /dev/sda1 - Grub boot partition
 (hd0,1) # /dev/sda2 - Ubuntu

grub> setup (hd0)

grub> setup (hd0,0)

```

Now you should be booting with grub-legacy, and chainload to whatever OS is on the other disks..

Hope this helps!

---

### Post by joepotter on 2009-11-07
That is a great trick, and I might want to do that someday. I thank you much for typing in that tutorial.

But first, I would like to figure out dual booting under this new grub.

So, I  put Debian testing on /dev/sda5 and it comes with grub 2. I let it write to mbr and then did an update-grub and it found Ubuntu on /dev/sda1 and I can boot into that. That is  the state of the are as I type this.

What I would like to do is install Ubuntu from disk in /dev/sda1 and use ext4 and grub 2. I would like to have the new grub2 allow me to chainload /dev/sda5 like in the old days and fire up the bootloader (also grub2) to boot Debian.

Any thoughts on this before I give it a shoot?

---

### Post by Gina on 2009-11-22
> **slakkie said:**
> What you could do is creating a seperate grub parition so your system boots that grub and chainloads it to the other OS.

I advise you to have a Live CD ready, so you can perform all actions from the Live CD, or have it ready in case your machine doesn't want to boot (which could happen since we are messing with the bootloaders :)).

Create a small partition (/dev/sda1 in my case), make it 20MB or so, then do the following:

```

mkdir /mnt/bootdisk
sudo mount -t ext3 /dev/sda1 /mnt/bootdisk
grub-install --root-directory=/mnt/bootdisk sda1

```

(Details can be found here: [http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-using-grub_002dinstall.html](http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-using-grub_002dinstall.html) )

Change the menu.lst file in /mnt/bootdisk/boot/grub

```

sudo vi /mnt/bootdisk/boot/grub/menu.lst

```

```

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

#
# Default chainloading for grub-legacy to other slices
#
# Debian is the default OS
default         1
timeout         10

#hiddenmenu

color cyan/blue black/blue

title Ubuntu /dev/sda2
root (hd0,1)
chainloader +1

title Debian /dev/sda3
root (hd0,2)
chainloader +1

title Misc /dev/sda5
root (hd0,4)
chainloader +1

```

My Debian box has grub2 and my Ubuntu has grub-legacy. This way I have one bootloader which always allows an OS to have whatever bootloader they need/want/require.

You would need to run some grub commands to install it propperly.. as described here:
[http://orgs.man.ac.uk/documentation/grub/grub_3.html#SEC9](http://orgs.man.ac.uk/documentation/grub/grub_3.html#SEC9)

```

sudo grub
# You are now in a grub shell
grub> root (hd0,0)

grub> find /boot/grub/stage1
 (hd0,0) # /dev/sda1 - Grub boot partition
 (hd0,1) # /dev/sda2 - Ubuntu

grub> setup (hd0)

grub> setup (hd0,0)

```

Now you should be booting with grub-legacy, and chainload to whatever OS is on the other disks..

Hope this helps!
Been looking for this :lolflag:

I'm having a similar problem with Lucid and Karmic on my laptop.  Prior to installing a grub2 version, I had 3 OSs on the one hard drive.  Ubuntu 9.04 and 8.10 and Windows XP all booting and running happily.  I then installed Karmic = 9.10 letting it install grub2 into the MBR.  On re-start all the OSs were there but nothing would boot.  Moving the selection bar caused a system total freeze as did allowing the timeout to boot 9.10.  It showed a flashing text cursor in the top left corner for a couple of seconds then blank screen and total freeze.

I used the Alternate CD version for installing as I had found the Desktop CD refused to install the grub2 boot loader on either of my two main desktops although it would run as a Live CD.  Now on the laptop the Live CD (Desktop) version won't boot - it produces the same system lockup as attempting to boot an installed version.  So I'm not really sure if my problem actually belongs in this thread.

I reinstalled 9.04 to a spare partition replacing the MBR with a grub legacy loader.  Now all OSs are found including 9.10 and all boot and run except 9.10 which gives the same system lockup as above.  Replacing the menu entry for 9.10 with chainloader didn't help - I get the Error 13 message.

Now to my question (having detailled the problem) :- Does having a separate grub partition rather than using the MBR make the difference?

---

