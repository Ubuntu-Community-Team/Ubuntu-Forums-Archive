---
title: "Advice requested re grub and MBR on upgrade"
date: 2010-05-12
forum: Installation &amp; Upgrades
---

### Post by yxlbaz on 2010-05-12
I have two instances of Kubuntu 9.10 (Karmic)

I have installed grub2 and all seems OK except for a small bug with update-grub which I have a workaround for.  Reported elsewhere

The working system is on /dev/sda7
My copy for testing is on /dev/sda5

gparted flags /dev/sda1 as "boot" and that partition has temp files only.

update-grub found my test system on sda5 OK.

I would like to upgrade 9.10 on /dev/sda5 to 10.04 (Lucid) as a trial as I had problems with this upgrade on my working system (sda7) and had to recover from a backup image - hence the test system on sda5

I would like advice on what happens to grub2 and MBR which I assume is on sda1 when I do this upgrade.

I expect that the upgrade will change grub (in MBR?) to use sda5 instead of sda7 as the main grub filesystem.  If not, then all is fine and I carry on as usual.

If not then how to I re-instate my working grub (/boot/grub/*) to sda7 (my working system) as far as the bootloader in MBR is concerned.  Is it simply a case of backup and then re-install MBR after the upgrade?  Or is there a better way or have I misunderstood something?

Thanks

---

### Post by dino99 on 2010-05-12
note that grub2 does not like grub1 and its menu.lst, you need to only have grub-pc and grub-common installed.

when you upgrade, grub installer will ask you where you want to install it with a popup box:
 choose sda if you have only linux distro (no windoz bootloader to overwrite)
or sda5 or sda7 or both if you have windoz

sudo grub-mkconfig
sudo update-grub

---

### Post by yxlbaz on 2010-05-13
Thanks dino99

I do have only grub-pc and grub-common installed in both instances of Kubuntu 9.10

I did not know about the choice on installation - thanks for that.

I think I'm being a bit picky.  I wanted to end up with sda7 as the first place that update-grub looks for kernels and sda5 discovered by /etc/grub.d/os-prober.  I don't fully understand how this process works.  If the install does what I expect then it's not a big issue I guess I'll just change the default menu item for grub.cfg.

edit - Perhaps if I simply run update-grub from the sda7 instance after the upgrade on sda5 everything will go back in place as it is pre-upgrade apart from the kernel versions on sda5.

---

### Post by frantid on 2010-05-13
You're right, whatever system you are booted into when you run the grub scripts will become the default list on the top of the menu via the linux part of /etc/grub.d/

Without knowing your exact setup, it sounds like you have a separate boot partition for your grub files.  If this is true, you would have to do the advanced setup when the updater asks where you want to put the install.  If you don't want the test lucid to interfere with your current grub setup, I would recommend putting grub in the partition of your test partition.  Then your stable version will find it after you run update-grub.

If you run [meierfra's bootinfoscript]("http://sourceforge.net/projects/bootinfoscript/") post the results here, it will give a detailed look at your setup.  Then you can get accurate advice.

---

### Post by yxlbaz on 2010-05-13
Thanks Frantid.  This confirms what I thought -

"... whatever system you are booted into when you run the grub scripts will become the default list on the top of the menu via the linux part of /etc/grub.d/"

Here is part of the output from meierfra's bootinfoscript -

                Boot Info Script 0.55    dated February 15th, 2010

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in
    partition #7 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdf

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:
    Operating System:
    Boot files/dirs:

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab
                       /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab
                       /boot/grub/core.img

sda8: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:
    Operating System:
    Boot files/dirs:

sdf1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:
    Operating System:
    Boot files/dirs:


_______________________________
_______________________________
It's a big file and I'll attempt to attach the whole thing for interest.

sdf1 is an external disk and not implicated with this.


I'll give it a go at the weekend when my system can be offline.

Thanks again

---

### Post by frantid on 2010-05-14
it looks okay, you do have the old menu.lst files in your /boot/grub/   I would rename them if you want to keep them as backups.

otherwise, I would -- actually I did on mine -- install your test lucid grub into your test partition or you could just check not to install grub at all in that test install.

---

