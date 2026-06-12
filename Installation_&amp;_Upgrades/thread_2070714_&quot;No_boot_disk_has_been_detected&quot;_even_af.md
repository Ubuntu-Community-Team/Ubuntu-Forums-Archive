---
title: "&quot;No boot disk has been detected&quot; even after reinstalling grub"
date: 2012-10-13
forum: Installation &amp; Upgrades
---

### Post by joehill on 2012-10-13
I just moved and decided to keep my old hard drive with Precise installed on the first partition (now sda1) and my /home on sda3 (swap in the middle) but to leave my old computer and put my hard drive into a new one. I have not  I swapped my hard drive for the one that came with the computer (it had Windows installed) and tried to boot up but got the message "ERROR: No boot disk has been detected or the disk has failed." I've tried a number of things to solve this problem, including reinstalling grub several times (which was more complicated than it sounds, because apparently with my current computer grub expects to have a separate partition flagged as "bios_grub", something that took me a while to figure out). But no matter what I've tried, I always turn on the computer and get the same message about no boot disk.

I've tried several steps. I first tried just running "grub-install" but that failed with an error message saying it couldn't find a /boot/grub to write to and asking if I had mounted the partition. I got this whether or not I mounted the partition. Then I tried reinstalling Ubuntu from the live CD and it kept telling me to go back and create a partition marked for use as a "Reserved BIOS Boot partition", although it offered no way of doing this from within the installer.

Most recently I've tried installing Boot Repair, which also told me I needed a Bios partition but at least told me how to do it (from gparted, create a parition, leave it unformatted, and flag it as "bios_grub"). I tried Boot Repair with the default options and rebooted to get the same error (the output from that attempt is here: [http://paste.ubuntu.com/1276233/](http://paste.ubuntu.com/1276233/)). Then I tried the advanced options, including removing the previous grub and upgrading to the newest version and installing it on both sda and sda1. Again I rebooted and got the same error message that there is no boot disk (output from that attempt here: [http://paste.ubuntu.com/1277022/](http://paste.ubuntu.com/1277022/)).

I may just try again to reinstall Ubuntu, although I'm not sure the problem will go away because I think the Ubuntu installer just writes grub in the same way I just did.

Any ideas? I've installed Ubuntu many many times over the past 8 or so years on many computers and have never had a problem of a computer not recognizing a hard drive with Ubuntu and grub installed on it as bootable.

Thanks!

---

### Post by darkod on 2012-10-13
I don't know how exactly you tied to reinstall grub2, and how boot-repair tried to do it, but as you can see at the top of the results the core.img file can't be found correctly.

Try this. Get the 12.04 cd and boot it in live mode. Open terminal,  and reinstall grub2:
```
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

Reboot without the cd and see how it goes.

---

### Post by oldfred on 2012-10-13
Darko's procedure should work to install grub. But Boot-Repair should have fixed it. 

Your most current pastebin still shows the grub in the MBR saying it cannot find core.img (which should be in the bios_grub partition). Do not install grub to a partition like sda1, that will not work.

You have a very large 3TB drive that has to use the new gpt partitioning  scheme. With gpt you have to have the bios_grub partition for grub to  install correctly. 

Also we are finding with large / (root) partitions grub has issues.  So be sure to keep a smaller root partition. Yours at 15GB is smallish with a 3TB drive. I use 25GB and you obviously have room for more.

---

### Post by joehill on 2012-10-13
Thanks for your suggestions. I went ahead and reinstalled Ubuntu without errors but I got the same error of no boot disk when I rebooted. Then I tried darkod's suggestion of reinstalling from the command line without errors--even though I'm sure that's what Boot Repair did twice and Ubiquity did once--and got the same error. This is confusing because Windows boots (on a different hard drive) on the same computer, and the same hard drive booted Precise on a different computer with almost the same partitioning, even without the 50mb bios_grub partition that I installed yesterday.

Oldfred, are you suggesting growing the / partition? I'm confused because you say Ubuntu has problems with larger / partitions but that I have room for more. I could shrink the larger /home partition and create a larger one for / afterwards but I can't imagine needing all that much space in /.

I'm confused about the inability to find core,img because I'm sure boot-repair and ubiquity both had grub-install write core.img to sda4, but then grub still apparently looks in the wrong sector and can't find it.

Maybe more importantly, the error I'm getting when I actually boot is not a grub error but the bios saying it can't find a boot disk to begin with, so we're not even in grub yet. I wonder if that means the bios is simply not finding grub in the first place or thinks the disk itself is not bootable.

Could there be a problem with the disk itself not being compatible with this bios? I'm thinking of installing Ubuntu on the hdd that came preinstalled with Windows and seeing if the bios likes that disk better, then hooking my old one one up for the home directory. I don't know why it would like one hdd better than the other though.

Thanks for the suggestions, and I'd really appreciate any further clarifications.

---

### Post by darkod on 2012-10-13
I thought it's a bios message too, and it might be related to the fact you have no boot flag on any partition. However, with gpt and the bios_grub flag, I didn't think you need the boot flag too.

In any case, it doesn't hurt to try. If your /dev/sda1 is still root after the reinstall, try this from live mode:
```
sudo parted /dev/sda
set 1 boot on
quit
```

That will set the boot flag on partition #1. Reboot and see if it helped.

In your latest install, did you also use the auto method, or you installed manually?

---

### Post by oldfred on 2012-10-13
+1 on Darko's suggestion of boot flag.

There have been some BIOS primarily Intel motherboard that require a boot flag to even boot at all. And even with gpt drives that seems to be required. 

Grub does not need a boot flag and with gpt you are not supposed to use a boot flag except on efi partiton. In parted the boot flag is really to set the efi partition as ef00. But Intel's BIOS does not follow the convention and wants a boot flag.

Depending on how much software you plan to add to your / (root) partition 15GB is fine. My normal suggestion is 10 to 25GB  where smaller size is only for smaller hard drives.

---

