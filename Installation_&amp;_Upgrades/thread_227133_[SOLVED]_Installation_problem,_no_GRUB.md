---
title: "[SOLVED] Installation problem, no GRUB"
date: 2006-08-01
forum: Installation &amp; Upgrades
---

### Post by WolfLust on 2006-08-01
Hello all,

I tried to install Ubuntu 6.06 i386, at first I tried to create on 20Gbs Unlocated (on a drive which already has Winxp on one of its partition but I left these 20Gbs unlocated to install Linux later on) I wanted to have a 19Gb "/" and a 1Gb SWAP, clicked proceed, formatted the partition, but got 20Gbs to the / and 0Kbs to swap, and reported that it cannot create SWAP, then I gave 19Gbs to "/" and nothing to SWAP attempting to give space to SWAP later on. the installation finished and I reached the restart part where I have to remove the cd. I did, restarted, and Windows started with no grub or any way to enter UBUNTU. how can I fix that please? and I tried entering using rescue mode, it loaded a screen and gave:

GRUB

Error 17.

In addition to that, when I tried entering through the LiveCd Install/Start option I got back to the Tour mode as if I want to install it, but I cannot mount, delete, format, or even access all of my partitions so I couldn't reinstall Ubuntu.

Can anyone help me solve this please? 

I am also worried if I try to install Grub it might damage my MBR and I wont be able to access Winxp.

---

### Post by drosophyllum on 2006-08-01
Sorry that no one has replied, I hope you didn't lose this post.
Well,  If I were you, I would find the windoZ installation cd as those usually have GREAT partitioners that sadly are notmuch eye candy...
Delete the entire disk,
then make a new fts windoZ partition consuming half your drive, from now on refure to it as the ghettos.
now leave the rest alocated/freespace
install install the diseased operating system you know as windoZ on the ghettos of your drive then install ubuntu using the option to install on the largest amount of freespace.
this worked for me.
But I have no Idea what went wrong on your comp...
try reburning the iso image with other software.

bye bye now....

---

### Post by WolfLust on 2006-08-01
Thanks for your reply,

I managed to access the LiveCd and start it normally, then use Ubuntu's partition tool to partition my drives, I created the SWAP partition and reinstall Ubuntu again.

Restarted once prompted to, and directly entered winxp with no trace of GRUB.

The windows/Ubuntu harddisk is SATA drave identified as "sda"

Also, is there a windows installer for GRUB? and which version is the safest? 

Thanks again.

---

### Post by zxee on 2006-08-01
There are other bootloaders that will allow you to access linux installs from windows. [http://btmgr.webframe.org/](http://btmgr.webframe.org/) I don't use it myself but it seems that it works for some people. You should also be able to install grub from chroot. Do man chroot at a shell. Hope that helps.

---

### Post by WolfLust on 2006-08-01
is there a way to install GRUB using the livecd? 

when I tried:

sudo grub
root (hd0,1)
setup(hd0)
quit


it wouldn't read hd0 or 1, since mine are hdb (the music hdd with no OS on it), and sda which has ubuntu and windows.

---

### Post by zxee on 2006-08-01
> **WolfLust said:**
> is there a way to install GRUB using the livecd? 

when I tried:

sudo grub
root (hd0,1)
setup(hd0)
quit


it wouldn't read hd0 or 1, since mine are hdb (the music hdd with no OS on it), and sda which has ubuntu and windows.

Try > sudo grub-install hd? from the livecd. replace the question mark with the drive you want to install to. You can also install to a root partition. If you want to do that then you would include the partition number as grub reads it e.g hd?,? 
Remember grub counts from 0.

---

### Post by WolfLust on 2006-08-01
Alright, but it will install if windows and Ubuntu are both on a SATA drive?

---

### Post by zxee on 2006-08-01
> **WolfLust said:**
> Alright, but it will install if windows and Ubuntu are both on a SATA drive?

It should and it should also see your windows install and create an entry for it in menu.lst. I don't use windows though. Sata drives seem to be pretty well support now-my is.
As I posted you could try the smart boot manager from windows if you're concerned about your MBR. You can always revive your mbr, if it doesn't work the way you expect, with fdisk /mbr in dos.

---

### Post by WolfLust on 2006-08-01
I tried "grub-install sda" and I got:

subuntu@ubuntu:~$ sudo grub-install sda
Probing devices to guess BIOS drives. This may take a long time.
Format of install_device not recognized.
Usage: grub-install [OPTION] install_device
Install GRUB on your drive.

  -h, --help              print this message and exit
  -v, --version           print the version information and exit
  --root-directory=DIR    install GRUB images under the directory DIR
                          instead of the root directory
  --grub-shell=FILE       use FILE as the grub shell
  --no-floppy             do not probe any floppy drive
  --force-lba             force GRUB to use LBA mode even for a buggy
                          BIOS
  --recheck               probe a device map even if it already exists

INSTALL_DEVICE can be a GRUB device name or a system device filename.

---

### Post by WolfLust on 2006-08-01
zxee or if someone else can help:

Everywhere I read they say that the GRUB Legacy (version 0.9x) is dropped because it contained alot of bugs, thus GRUB 2 is developped now.

Wouldn't it be better to install GRUB 2? how can I do that please and whats the best version to use? Thanks alot for all your support today.

---

### Post by zxee on 2006-08-01
> **WolfLust said:**
> zxee or if someone else can help:

Everywhere I read they say that the GRUB Legacy (version 0.9x) is dropped because it contained alot of bugs, thus GRUB 2 is developped now.

Wouldn't it be better to install GRUB 2? how can I do that please and whats the best version to use? Thanks alot for all your support today.

The last time I looked at the grub website grub2 was still in development. That means we're all stuck with grub legacy until grub2 becomes stable. Yup-I just checked their page: [http://www.gnu.org/software/grub](http://www.gnu.org/software/grub) and that's the current situation.
I haven't heard there are "a lot of bugs" in grub legacy. It just seems that the developers want a newer version that's more flexible and has different features, and they can't do that with the old code. So you can't install grub2-it's not ready for installation/regular use.
You can try to learn what grub does or look for a different boot loader that runs from windows.
There is an online grub manual here: [http://www.gnu.org/software/grub/manual/grub.html](http://www.gnu.org/software/grub/manual/grub.html)

---

### Post by zxee on 2006-08-01
Hi Again, Sorry I've been helping a couple of people with grub problems today and sometimes I forget who had what issue. In a previous post you included this: > I tried "grub-install sda" and I got:


Grub doesn't understand drives begining with "s" a grub drive always begins with "h". If you only have that one drive on your computer then the command you want to issue is > sudo grub-install hd0 the last symbol in the command is a zero. There are other ways to go about this but if you want to install to the mbr that should work. Hope I've helped.

---

### Post by WolfLust on 2006-08-02
Hello again guys,

I tried to install GRUB manually yesterday and seems it worked, I inserted the LiveCD and when I reached the menu I booted rescue. This took me to the GRUB menu and I choose to enter UBUNTU.

THe problem I'm still facing is that GRUB doesn't show when I start the pc, it only does when I use rescue mode from the cd.

I think this is because GRUB is not successfully installed on the MBR, or maybe my BIOS is bugged. how can I figure how to solve this? thanks in advance.

---

### Post by zxee on 2006-08-02
The forums are a little screwy today it seems so I hope this posts correctly.
If you can use the live cd than maybe you can chroot to your install. You would mount the install i.e > sudo mount /dev/sda mnt/sda and then > sudo chroot /mnt/sda In the chroot environment type > grubat the grub prompt type > find /boot/grub/stage1 if you get a response to that ,hopefully you will you can then type > setup (hd0) or whatever drive designation grub returns from that find command. Hope that helps.

---

### Post by zxee on 2006-08-02
The forums are screwy today.

---

### Post by VirtuAlex on 2006-08-02
Have you tried to go to BIOS and change the boot sequence for hard drives? In my case grub installed itself to the first IDE drive for some misterious reasons.

---

### Post by WolfLust on 2006-08-02
@ zxee : here's what I got:

walidch@walidch:~$ sudo mount /dev/sda mnt/sda
Password:
mount: you must specify the filesystem type
walidch@walidch:~$ sudo chroot /mnt/sda
chroot: cannot change root directory to /mnt/sda: No such file or directory
walidch@walidch:~$ sudo mount /dev/sda /mnt/sda
mount: you must specify the filesystem type


@ VirtuAlex : both windows and Ubuntu are installed on my sata, and the BIOS is set to boot from the SATA drive only, I'll try to change that now and see if it works :)

---

### Post by zxee on 2006-08-02
> **WolfLust said:**
> @ zxee : here's what I got:

walidch@walidch:~$ sudo mount /dev/sda mnt/sda
Password:
mount: you must specify the filesystem type
walidch@walidch:~$ sudo chroot /mnt/sda
chroot: cannot change root directory to /mnt/sda: No such file or directory
walidch@walidch:~$ sudo mount /dev/sda /mnt/sda
mount: you must specify the filesystem type


@ VirtuAlex : both windows and Ubuntu are installed on my sata, and the BIOS is set to boot from the SATA drive only, I'll try to change that now and see if it works :)

I left out a step-sorry. If you're going to try the chroot you first need to make a directory to mount sda to. So> sudo mkdir /mnt/sda another pronlem might occur. Is the install taking up the whole drive? If it's on a partition say sda1 then you need to use that instead of sda.

---

### Post by WolfLust on 2006-08-02
I tried what VirtuAlex said and it worked, turned out that GRUB installs itself on the IDE drive.

zxee and VirtualAlex thanks alot, specially zxee for your patience.

---

### Post by VirtuAlex on 2006-08-02
> **WolfLust said:**
> walidch@walidch:~$ sudo mount /dev/sda mnt/sda
Password:
mount: you must specify the filesystem type
You can't just mount whole hard drive. You have to use partition number like /dev/sda1 or /dev/sda2 whatever your linux partition is. You can figure out that using sudo fdisk -l
> **WolfLust said:**
> @ VirtuAlex : both windows and Ubuntu are installed on my sata, and the BIOS is set to boot from the SATA drive only
And nevertheless grub got into completely wrong drive in my case. I have moved it later to SATA but... It was weird...

---

### Post by VirtuAlex on 2006-08-02
> **WolfLust said:**
> turned out that GRUB installs itself on the IDE drive.
In case you'll decide to move the grub to sata there should be howto in this forum somewhere. I saw it couple of times, but it seems I can never find anything when I need it. If it would be any help, here is my thread about it: [http://ubuntuforums.org/showthread.php?t=218525]("http://ubuntuforums.org/showthread.php?t=218525")

---

