---
title: "Can't install bootloader to Linux partition"
date: 2010-04-29
forum: Installation &amp; Upgrades
---

### Post by ColmCille on 2010-04-29
I'm doing a dual boot, Windows 7 and Ubuntu 10.04, using EasyBCD as my boot manager.

During the installation, I created my ext4 partitions for root, /home and swap. Got to the "advanced" tab, and when I select any Linux partition, the "ok"  button is grayed out. It will only allow me to install to Windows partitions. I need to install to the Linux partition to use EasyBCD. 

Anyone know anything about this? 

Thanks.

---

### Post by Vined Adobo on 2010-04-30
> **ColmCille said:**
> I'm doing a dual boot, Windows 7 and Ubuntu 10.04, using EasyBCD as my boot manager.

During the installation, I created my ext4 partitions for root, /home and swap. Got to the "advanced" tab, and when I select any Linux partition, the "ok"  button is grayed out. It will only allow me to install to Windows partitions. I need to install to the Linux partition to use EasyBCD. 

Anyone know anything about this? 

Thanks.


Hmm... I'm sure you can't boot from swap or /home. I think you boot from /dev/sda or something like that.  Did you make a mount point of "/" (no quotes) for your root partition?  You have to mount the root partition from / That's my guess.

Dave

---

### Post by ColmCille on 2010-04-30
> **Vined Adobo said:**
> Hmm... I'm sure you can't boot from swap or /home. I think you boot from /dev/sda or something like that.  Did you make a mount point of "/" (no quotes) for your root partition?  You have to mount the root partition from / That's my guess.

Dave

Right, I created the root partition, a.k.a. dev/sda5 on my machine, assigned it mount point /, and it is exactly where I tried to install the bootloader. But when I highlight that partition, the "ok" button is grayed out. In other words, it won't let me do it. 

If I highlight *any* of the Linux partitions (just for kicks), it is similarly grayed out. 

However, if I highlight any of the three (four including the thumb drive) Windows partitions, or the hard drive itself (dev/sda), or even the Ubuntu Live Disk (dev/sdb1) the "ok" button is no longer grayed out. Basically, it will let me install it anywhere but onto a Linux partition. 

I have no idea why. It doesn't seem much to ask. Maybe I'm doing some stupid thing wrong, but my addled brain can't comprehend it. I don't know what. It's not a hard process. I've done it before with Hardy. Exact same thing, different interface.

No, I think I'll blame Lucid. :P

Anyway, thanks for taking a guess.

---

### Post by Vined Adobo on 2010-04-30
> **ColmCille said:**
> Right, I created the root partition, a.k.a. dev/sda5 on my machine, assigned it mount point /, and it is exactly where I tried to install the bootloader. But when I highlight that partition, the "ok" button is grayed out. In other words, it won't let me do it. 

If I highlight *any* of the Linux partitions (just for kicks), it is similarly grayed out. 

However, if I highlight any of the three (four including the thumb drive) Windows partitions, or the hard drive itself (dev/sda), or even the Ubuntu Live Disk (dev/sdb1) the "ok" button is no longer grayed out. Basically, it will let me install it anywhere but onto a Linux partition. 

I have no idea why. It doesn't seem much to ask. Maybe I'm doing some stupid thing wrong, but my addled brain can't comprehend it. I don't know what. It's not a hard process. I've done it before with Hardy. Exact same thing, different interface.

No, I think I'll blame Lucid. :P

Anyway, thanks for taking a guess.

Yeah, you've got me stumped.
Bump it every day or two.  Maybe a partition expert will see it.

---

### Post by kansasnoob on 2010-04-30
> **ColmCille said:**
> Right, I created the root partition, a.k.a. dev/sda5 on my machine, assigned it mount point /, and it is exactly where I tried to install the bootloader. But when I highlight that partition, the "ok" button is grayed out. In other words, it won't let me do it. 

If I highlight *any* of the Linux partitions (just for kicks), it is similarly grayed out. 

However, if I highlight any of the three (four including the thumb drive) Windows partitions, or the hard drive itself (dev/sda), or even the Ubuntu Live Disk (dev/sdb1) the "ok" button is no longer grayed out. Basically, it will let me install it anywhere but onto a Linux partition. 

I have no idea why. It doesn't seem much to ask. Maybe I'm doing some stupid thing wrong, but my addled brain can't comprehend it. I don't know what. It's not a hard process. I've done it before with Hardy. Exact same thing, different interface.

No, I think I'll blame Lucid. :P

Anyway, thanks for taking a guess.

I've only done this once but from what I remember combined with my notes I had to choose not to install grub2 anywhere. That is when I got to the last step of the installation where you can review all of the installation info I clicked on the Advanced button in the lower right hand corner and simply "unchecked" the Install Bootloader option.

Then when the installation was complete instead of rebooting I stayed in the Live Desktop and installed grub2 to the partition using a chroot like this:

(Note: I'm using /dev/sda5 because that's what you said).

```
sudo mount /dev/sda5 /mnt && sudo mount --bind /dev /mnt/dev &&sudo mount --bind /proc /mnt/proc && sudo chroot /mnt
```

I then check to be sure I've mounted what I want with:

```
lsb_release -a
```

Then install grub2 to the partition:

```
grub-setup --force /dev/sda5
```

Then just exit and unmount:

```
exit
```

```
sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt
```

Good luck :)

---

### Post by psusi on 2010-04-30
I have a feeling it doesn't like extended partitions.  Try using a primary partition.

---

### Post by ottosykora on 2010-04-30
grub2 does not like to be installed in the actual root partition apparently, no difference if primary or logical partition. I don't know why this is so, but I was told, that people  had big problems after installed it into the root partition.

So I tried last time to install some fedora this way, I also had to simply not install any grub at all and then later used legacy grub 'super grub disk' to install grub into the root partition 'by hand'. 

See also if you have not a choice of selecting which grub to install, the legacy one will do it right.

---

### Post by psusi on 2010-04-30
Grub2 should work fine being installed to the partition, it just isn't the recommended way since it has to use block lists, so if the core file ever moves it will totally break booting.

---

### Post by ColmCille on 2010-04-30
I did already try a primary partition, and all that did was make the rest of my available space unavailable. 

I guess I'll have to try and install manually, though I don't know why I should have to do that. Surely Canonical didn't pull a Microsoft on us, deciding that since it is not recommended, we'll have to do it manually? Nah, probably it's just a bug or oversight.

Maybe I'll try 9.10 instead.

Thanks for the replies, everyone.

---

### Post by wilee-nilee on 2010-04-30
> **ColmCille said:**
> I did already try a primary partition, and all that did was make the rest of my available space unavailable. 

I guess I'll have to try and install manually, though I don't know why I should have to do that. Surely Canonical didn't pull a Microsoft on us, deciding that since it is not recommended, we'll have to do it manually? Nah, probably it's just a bug or oversight.

Maybe I'll try 9.10 instead.

Thanks for the replies, everyone.

Your asking for problems now and in the future not just letting grub be the boot manager. Good luck though this will be a learning experience for you.

---

### Post by ColmCille on 2010-04-30
> **wilee-nilee said:**
> Your asking for problems now and in the future not just letting grub be the boot manager. Good luck though this will be a learning experience for you.

For the last couple years I've used EasyBCD for multi-booting between Windows and Linux. Never had a single problem with it. 

Excuse me while I go find some wood to knock on. :)

---

### Post by wilee-nilee on 2010-05-01
> **ColmCille said:**
> For the last couple years I've used EasyBCD for multi-booting between Windows and Linux. Never had a single problem with it. 

Excuse me while I go find some wood to knock on. :)

I hope you get it working, but I think the ext4 partition can't be used, I am not sure on this but that is the general scuttlebutt. ;)

---

### Post by linuxbeb on 2010-05-01
ColmCille

Similar to you, I was cracking my head to resolve this issue. I saw your posts in a number of forums. 

The workaround is to install GRUB2 manually. 

1. Using your LiveCD - follow the installation Ubuntu BUT when you reach the screen where you have access to the Advanced button, deselect install bootloader. 
<The reason is that we will install it manually, since our setting is to maintain Window NTLDR as the bootloader>

2. Then you have the option to reboot, but before that, install the GRUB2 using the Wiki guide [https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

3. Remember to use the "sudo" command

4. Follow the instructions in Step 2. You need to use sudo grub-install --force /dev/sda6   --> change this according to your setup
Make sure you check the last line saying there is no major error after the command.

5. When step 2 completed, you can reboot to make sure everything is fine - your Windows before proceeding further. At this stage you won't be able
to see your Linux in your Window bootloader

6. Depending on your config, I didn't use EasyBCD so this step might be different. I need to create binary file of Linux using the command below
sudo dd if=/dev/sda3 of=/mnt/share/ubuntu1004.bin bs=512 count=1

7. Modify the NTLDR bootloader e.g. my configuration is as 
C:\ubuntu1004.ini = "Ubuntu 10.04 (Desktop)"

8. Login and enjoy the sleek Ubuntu 10.04 :D

Hope it works for you. 


P/S: As pointed out, it may be better to use GRUB in the future but at the moment, until I am completely convinced with Linux, I will redo refresh my laptop configuration to Linux. The benefit of sticking with Window NTLDR is that if we remove Linux in the future, it won't touch or has issue like missing NTLDR error.

---

### Post by ottosykora on 2010-05-01
common, so perfect is the grub not.

I am using for long time other boot managers and grub just in the root partition. This work definitely more stable an dreliable then all other grub constructs.
Recently I just had to clone a hard drive with grub, half of the things did not work later on the copy.
With other boot managers I have never experienced such problems. Gub is simply too fragile and absolutely not fault tolerant.

---

