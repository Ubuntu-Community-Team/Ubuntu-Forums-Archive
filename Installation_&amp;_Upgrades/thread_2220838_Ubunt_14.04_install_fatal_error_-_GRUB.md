---
title: "Ubunt 14.04 install fatal error - GRUB"
date: 2014-04-29
forum: Installation &amp; Upgrades
---

### Post by Andre_Figueiredo on 2014-04-29
Hi there,
I`m new to the Linux world. I installed last weekend Ubuntu 14.04 at home and everything went well. I was so impressed I started to migrate the PCs in my firm to Ubuntu. I am trying to install it in the first machine for the second day. Non stop! It is driving me crazy!
Please, any help is appreciated.
It seems to me that every time the installation program tries to write GRUB to sda an error occurs and after that the MBR becomes useless. Then, on next boot a black screen and Read Error.
I`ve done a lot of reading in the forums and already tried:
Boot Repair - only managed to recreate Boot record, no success in reinstalling GRUB. Several attempts.
Tried to install 64 and 32 bits.
Downloaded another 32 bits from home and brought a new Flash Drive.
Changed some settings in BIOS like Quick Boot, ACPI, and a few others.
Tried to install with ext2, ext3 and ext4.
Boot Repair log is here (did not paste it here because seemed very long to me):
[http://paste.ubuntu.com/7361181/](http://paste.ubuntu.com/7361181/)

Using the MBR option in Boot Repair led me back to being able to run Windows 7. I need it to be installed alongside Linux as a way to ease the adoption from my employee.

Any ideas?
Thanks in advance,

Andre

---

### Post by Bashing-om on 2014-04-30
Andre_Figueiredo; Hi ! Welcome to the forum.

I do appreciate your zeal to promote ubuntu.

Let's see what can be done to get your work station restored with dual booting.
This:  - from the boot-repair text output:
> 
grub-install: error: cannot write to `/dev/sda': Input/output error.
grub-install /dev/sda: exit code of grub-install /[color=red]dev/sda:1[/color]

Indicates to me that there is a problem in Windows (sda1).
Maybe use Windows' repair utilities (fixmbr and check disks) to repair.

As then the MBR will be over written by Windows, will require (re-)installing grub to that MBR.

Once the Windows checks are complete, one might then (re-)install ubuntu's boot manager from the liveUSB:
per:
> 
/dev/sda6        97429504   200867839    51719168   83  Linux

Terminal commands:
```

sudo mount /dev/sda6 /mnt ##because ubuntu is installed to 'sda6'
sudo grub-install --boot-directory=/mnt /dev/sda ##'sda' because we want grub installed to the MBR
sudo umount /mnt ##because you are done, simple as that.

```

Now reboot, set bios to boot the 1st hard drive . Once you are to the desk top open a terminal, as we now need to pick up the Windows install and chain load Windows booting to ubuntu's boot manager. Run terminal code:
```

sudo apt-get update
sudo apt-get upgrade
##and the biggy in this regard##
sudo update-grub

```

Now, let's see what happens.
Reboot once more, and now you should boot to ubuntu's boot manager with the option to boot Windows also.


[INDENT][INDENT]should workie great 
[INDENT][INDENT]last long time
[/INDENT][/INDENT][/INDENT][/INDENT]

---

