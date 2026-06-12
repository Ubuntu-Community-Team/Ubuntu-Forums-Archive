---
title: "Can't install dapper or edgy: &quot;can't access tty&quot;"
date: 2006-11-17
forum: Installation &amp; Upgrades
---

### Post by kebes on 2006-11-17
I am trying to install Kubuntu on a Core 2 Duo (Conroe) 1.8 GHz system that has an Intel DG965SS motherboard. When trying to Kubuntu 6.06 LTS (Dapper Drake) the installation would freeze at the "Mounting root file system..." line. After some looking around, I assumed I was running into the problem described here:

[https://wiki.ubuntu.com/Core_2_Duo_Support](https://wiki.ubuntu.com/Core_2_Duo_Support)

Essentially that support for the 965 chipset (specifically for IDE devices) is missing in Dapper. I thought that Edgy fixed this, so I tried an install of Kubuntu 6.10 (Edgy Eft). I verified the CD MD5sum.

During install of Edgy, the install blocks with this error:
```

BusyBox v1.1.3 (Debian 1:1.1.3-2ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands.
/bin/sh: can't access tty; job control turned off
(initramfs)

```

If I do "Ctrl+Alt+F1" I see these errors:
```

cp: unable to open '/root/var/log/': No such file or directory
mount: Mount /root/dev on /dev/.static/dev failed: No such file or directory
mount: Mount /sys on /root/sys failed: No such file or directory
mount: Mount /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init
```

I have tried adding in various boot options (such as pci=nommconf  all-generic-ide noacpi) but they don't help.

Does anyone know what's going on? Is the problem I'm seeing with Edgy also related to the 965 chipset (the install can't read from the IDE CD/DVD drive?) or is it something else entirely?

As always, any help would be greatly appreciated.

---

### Post by kebes on 2006-11-20
Here's an update on my progress.

The above problems were with the Live CD. I tried the "alternate" installer and have managed to at least get a little bit further along. The IDE CD-ROM is (as before) recognized during the initial load of the installer, but then goes missing. Basically the installer cannot read the CD-ROM and fails to mount it to "/cdrom/".

So I decided to try to install from a USB key, and am following the instructions here:
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

At first it seemed to be working. The installation complains about a missing CD-ROM, I go "Ctrl+Alt+F2" and do mount the USB key onto "/cdrom/". Then the installer keeps going, asking for questions and so forth.

However it eventually dies with this error:
```

Debootstrap Error
Failed to determine the codename for the release.

```

If I go to "Ctrl+Alt+F4" I see a similar logged error:
```

base-installer: error: exiting on error base-installer/no_codename
```

The problem might be missing symlinks, since the USB-key is FAT and so doesn't preseve symlinks. I can copy the USB-key contents to an ext3 partition on the hard-disk, but I will have to rebuild the symlinks myself. In particular, I've noticed that the file:
/cdrom/dists/stable
is zero-sized. I assumed it was meant to be a symlink to "/cdrom/dists/edgy/". However there is a file in the root of the CD called "ubuntu" (mounts to "/cdrom/ubuntu") and which is also supposed to be a symlink? Does anyone know where it is supposed to point?

Basically I am stuck... but I'm SO CLOSE to getting this to work! The installer just needs to be tricked into thinking it's a normal CD-environment install and it will proceed.

Does anyone have any suggestions or insights? I've been working on this for days now and I really need to get it finished!

Thanks in advance.

---

### Post by kebes on 2006-11-21
To anyone who runs into similar problems, this is what I finally did:

I installed Fedora Core 6 with the options:
linux text all-generic-ide pci=nommconf irqpoll

(after install I edited "/etc/inittab" and changed "id:3:initdefault" to "id:5:initdefault" so that it boots into GUI instead of text mode)

The problem is that kernel versions 2.6.17 (and older) cannot use the intel 965 chipset. So Ubuntu Edgy (which uses 2.6.17) cannot boot. Fedora Core 6 happens to use 2.6.18 and so it boots and installs fine.

I guess I will just have to wait until the next Ubuntu release, which will no doubt include the required kernel.

---

### Post by drtvasudevan on 2006-11-27
> **kebes said:**
> To anyone who runs into similar problems, this is what I finally did:

I installed Fedora Core 6 with the options:
linux text all-generic-ide pci=nommconf irqpoll

.....

much obliged.
i am in similar predicament.
will try fc6
tv

---

### Post by drtvasudevan on 2006-12-02
> **kebes said:**
> To anyone who runs into similar problems, this is what I finally did:

I installed Fedora Core 6 with the options:
linux text all-generic-ide pci=nommconf irqpoll

.....

thanks for the suggestion.
now i have some hopes.
i had two failed downlaods.
there is this SHA1SUM now not md5.
i dont know how to check this in windows.

anyway i tried a install and seems that it will work.
it reported bad cd missing files and had to be aborted but it did start the installation proper..

now to get at the good copies of the cds..

btw it says partition hdgx
hdg?
is that what you too got?
any problems there?

thanks in advance

tv

---

### Post by kebes on 2006-12-03
> **drtvasudevan said:**
> anyway i tried a install and seems that it will work.
it reported bad cd missing files and had to be aborted but it did start the installation proper..

I didn't get that error exactly, but the BIOS is buggy and I would sometimes get strange errors before the installer started. However when I finally got into the installer, it worked fine, and moreover the final install of FC6 has no troubles at all.


> btw it says partition hdgx
hdg?
is that what you too got?
any problems there?


Not sure what you're asking. Did you get an error related to "hdg"? The partitioning system should auto-detect your disks and assign names like hda, hdb (or sda, sdb if they are SATA-based). "hdg" is perhaps just the name of assigned to your hard drive?

---

### Post by drtvasudevan on 2006-12-04
> **kebes said:**
> 
Not sure what you're asking. Did you get an error related to "hdg"? The partitioning system should auto-detect your disks and assign names like hda, hdb (or sda, sdb if they are SATA-based). "hdg" is perhaps just the name of assigned to your hard drive?

it reports the hard disk as hdg
it is not a name i assigned to it.
it is 250 seagate sata drive
perhaps the para meters all-generic-ide pci=nommconf irqpoll has something to do with it?
anyway i am downloading the second cd now.
will report in two days

---

### Post by drtvasudevan on 2006-12-05
ok.done it.
my system specs: core2 duo DG965RY intel mobo 250 SATA hd one gig RAM.
downloaded with some difficult the first two cd images of fedora core 6. the SHA1 sum check was a pain -did not do it.
the hash values were different.
checked the cdrom during installation.needed another download from different site for the first cd.
gave the parameters as mentioned in this thread.
it analysed the disk and said it could not find the partition table in device sda do i want to format destroying all data? i panicked and said no.
later chose manual partition configuration.
it proceeded to show a list of the partitions (made previously with bootitng) in dev hdg.
chose a root and home partition.
install went with no problems.
needed just the first two cds for a default gnome desktop install.
installed grub in its own partition .
used OSL to boot to it.
changed the init level
now running FC6.
need to figure out updates (networking)
firefox has the good old ipv6 problem. that inspite of turning off ipv6 during install.(you get an option)
need to mount other partitions.
need to figure out how to make the dvd rom work (if it will)
can i use the PATA patch?
a million thanks for letting me know a workable linux for this mobo.
regards

---

### Post by kebes on 2006-12-05
> **drtvasudevan said:**
> ok.done it.
now running FC6.

Good work!

> need to figure out updates (networking)

Fedora uses "yum" instead of "aptitude" (or "apt-get") which is used in ubuntu. You can go:
$ su
# yum update

To install updates.

> need to figure out how to make the dvd rom work (if it will)

On my system the DVD-ROM worked after a fresh install (at least it can read ... have not tried burning data yet...). No patch was required.

---

### Post by drtvasudevan on 2006-12-05
> **kebes said:**
> Good work!
Fedora uses "yum" instead of "aptitude" (or "apt-get") which is used in ubuntu. You can go:
$ su
# yum update

To install updates.
yes.
but somehow in my place it has been a problem right from the beginning.
some configuration that i am not getting right.
the usual dhcp connects to net but updates dont take place till a specific dns number is configured.:confused: 

[QUOTE On my system the DVD-ROM worked after a fresh install (at least it can read ... have not tried burning data yet...). No patch was required.[/QUOTE]
ok will look around.
till ubuntu comes up to deliver this will have to do.
thanks

---

### Post by styfer on 2006-12-06
hi
i have the exact same problem

can't access tty; job control turned off

follow by a command prompt
strange but true when i type 'exit' (without qoutes) i can boot to ubuntu

can you guys with the problem try that?

---

### Post by kebes on 2006-12-06
> can't access tty; job control turned off
follow by a command prompt
strange but true when i type 'exit' (without qoutes) i can boot to ubuntu

That doesn't work in my case. When the error occurs I see this:
```

/bin/sh: can't access tty; job control turned off
(initramfs)
```

I only get the "(initramfs)" prompt, not a full command-prompt. When I type "exit" here nothing happens. Thanks for the info, though!

---

### Post by goathens on 2006-12-19
i'm currently trying a hybrid solution between using the livecd and the usbflash drive in those directions.

My situation is that the livecd does boot - but then the cdrom doesn't mount due to core 2 duo / intep chipset issues.  I tried the usbkey, but it never loaded the linux kernel. so i mix and match.

Using the alternate install cd, i boot up to the installation, and before reaching the cdrom detection phase, i load a new console and mount the usbkey as the cdrom (the usbkey has the same image as the cdrom I am booting from). I then hit the CODENAME NOT FOUND error.

I'm thinking of modifying this slightly.
instead of copying the files from the livecd onto the usb stick, what if i copy the iso file instead? Then i can mount the usbstick, and mount the iso inside to cdrom

mount -o loop -t iso9660 /usbstick/ubuntu-XXx-blah.iso /cdrom

This way, there is no way that the symlinks or ubunut shortcut or whatever even matter, since you mount the iso itself.

I'm not sure if your system loads up the linux kernel at boot like mine does though, so your milage may vary.

*note* i haven't actually attempted this solution with the .iso image. I'll try it tomorrow and report any results.

---

