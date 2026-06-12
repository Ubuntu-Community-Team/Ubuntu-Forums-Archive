---
title: "reinstall Edgy without reformatting"
date: 2007-10-12
forum: Installation &amp; Upgrades
---

### Post by robmiracle on 2007-10-12
Stupid me, I have my drive all on /.   Once upoine a time, I had it formatted properly with home being a seperate partition, but through upgrades and problems with the installer I ended up with just /

That said, I've been running Edgy for some time and I wanted to upgrade to Gutsy.   I wanted to do it in one pass, but it appears I have to upgrade to Feisty first, then to Gutsy.  I update my apt/sources.list file and do an apt-get update; apt-get dist-upgrade.

It failed because somehow ligmjpegtools was installed.  I went into synaptic and removed libjpegtools and it finished the upgrade to feisty.   Along the way I got prompted to set values for /etc/mdadm/mdadm.conf and it said to erase the field if I'm not using raid.  I have a single SATA drive (/dev/sda) and I wasn't using any RAID that I'm aware of.

Upon reboot, I get a message about a configuration error with the mdadm.conf file.   I've not found any information on correcting it.  There is a lot of stuff on goggle, but its all assuming I have a RAID setup.

So I said, we let me just install Gutsy from the live CD.   It won't boot on my system (I suspect its hitting hardware problem wiht my Pentium D 830 which causes Windows to not work.  (I can't run the 686 kernel on this system as well or any form of windows).

I downloaded Edgy to reinstall from a CD, but its insisting on reformating the / file system which is a bad thing (at least until I'm able to get a big enough external drive to back the files off, which may be a couple of months).

So, how can I reinstall Edgy (or possibly Fiesty) hoping this mdadm problem with go away or how can I just fix that file?

Thanks
Rob

---

### Post by oxenfrogga on 2007-10-13
Hi Rob,

try deleting mdadm:
sudo apt-get remove mdadm

I think I can remember that it helped in my case long ago.

Cheers,
Harald

---

### Post by robmiracle on 2007-10-13
how can I do that without booting up?   I do get dropped to a very limited shell, but I'm not sure I can apt-get from there.

---

### Post by Ptero-4 on 2007-10-13
You can use the chroot command to get into your installed system and use aptitude (use it in the aptitude remove form, the barebones tty doesn't have the capalities needed to run the aptitude ncurses gui) to remove mdadm, then exit the chroot (with the exit command) and reboot.

---

