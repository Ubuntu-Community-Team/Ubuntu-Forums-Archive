---
title: "Move MBR and GRUB to new SSD"
date: 2015-01-04
forum: Installation &amp; Upgrades
---

### Post by Kubischbuntu on 2015-01-04
Hi,

I got myself a SSD and installed Kubuntu 64 onto that  using the custom option to define the root partition. I realize now that  I should have disconnected the old disk for this because the install  detected the old MBR and GRUB on the old disk and re-used it. However I  want to remove that old disk once it is all working and transferred - so  I need the MBR and GRUB to be on the SSD. How can I affect that change  and does it matter that the root partition on the SSD is at the front  i.e. with no space left in front of it? If the answer is to just install  grub to the SSD (it is dev/sda by the way) would that not confuse the  PC to have 2 active MBRs??

Thanx for any advice you may have.

---

### Post by TheFu on 2015-01-04
Concerns:
* SSDs may not have the same blocksize as the old HDD. Best to let the default installer choose the best alignment.
* SSDs are so fast that location of data doesn't matter at all.
* GPT partitioning is newer, has some very nice features and more redundant than the old (1980?) MBR method. STRONGLY recommend GPT over MBR unless your BIOS cannot handle it.  In Linux, GPT can work with BIOS, EFI is not required.

So, with all that, I'd perform a fresh install to the new SSD (just disconnect the SATA cable from the old HDD) and manually size the paritions under the "do something else" option to be close enough to what I already have.

Then I would migrate the apps, settings and data over - in reverse order (except very large data would be last). Here's how: [http://blog.jdpfu.com/2013/12/11/how-to-migrate-debian-ubuntu-systems-and-data-overview](http://blog.jdpfu.com/2013/12/11/how-to-migrate-debian-ubuntu-systems-and-data-overview).  This way I get a fresh install and don't have to recreate settings for the system or my userid.  The first time, it took me about an hour to do a restore/migration. With practice (about once a year), it is 30 minutes now ... ignoring any LARGE data.  I keep large data (audio/video stuff) outside my HOME for this reason.  Having good backups is just part of this solution.

You cannot just mirror an old install unless you can fix the fstab and a few other tiny things from a liveBoot. The moved settings just won't boot on a new SSD. UUIDs have changed.

Hope this helps.

---

### Post by grahammechanical on 2015-01-04
> [COLOR=#000000]If the answer is to just install grub to the SSD (it is dev/sda by the way) would that not confuse the PC to have 2 active MBRs??[/COLOR]

Not at all. Instruct the BIOS/UEFI to boot the SSD and it will look to the SSD and see Grub on it and run it. Instruct the BIOS/UEFI to boot the HDD and it will look to the HDD and see the bootloader there and run it.

When we install Ubuntu/Kubuntu or the other flavours the Installer defaults to installing Grub into the MBR of sda. Did you change the default settings? Was the HDD listed as sda? I doubt very much if the install is using the Grub configuration files on the old hard disk. A new configuration file would have been written but it may have been written to the hard disk and not the SSD.

I speak from experience. I have two hard disks with several installs of Ubuntu and its flavours. I use sdb for my main install of Ubuntu and the BIOS is set to boot sdb and the Grub on it. I install for testing on sda and every time I put in an install Grub is installed into sda and I switch boot priority in the BIOS to run the Grub on sda and then switch back to run the Grub on sdb. There is no confusion at all, except in my head, but not on the machine.

If the SSD is connected to the first SATA port on the motherboard then it will become sda. It will not cause any problems with loading Kubuntu because Grub does not use sda or sdb labels but a Univerally Unique Identifier (UUID) to tell the difference between hard disks.

Work out which drive is sda and which drive is sdb and then load into Kubuntu and run

```
sudo update-grub
```

and then depending on whether the SSD is sda or sdb run

```
sudo grub-install /dev/sda
```

or

```
sudo grub-install /dev/sdb
```

Then the Grub from Kubuntu will be in the MBR of the drive that Kubuntu is on and then set the boot priority to that drive.

Regards.

---

### Post by Kubischbuntu on 2015-01-04
Perfect [**[COLOR=#000000]grahammechanical[/COLOR]**]("http://ubuntuforums.org/member.php?u=1087323") - that told me exactly what I needed to know. I disconnected the old drive - fired it up and sure enough there was my grub menu coming from the new SSD. Happy!
Just out of curiosity what is it doing just before the grub menu while it is showing "Loading operating system..." seems to hang there for a good 10 - 20 sec before moving on??

Cheers

---

### Post by oldfred on 2015-01-05
If you only have Ubuntu, you have BIOS loading, grub loading, but with one install you will not see menu, and then system loading.
If you want to see grub menu, hold shift key from BIOS until menu appears.
BIOS takes a while to check what hardware you have. If for example you have BIOS set to load a floppy drive, but do not have a floppy drive it has to look for it and time out.
Grub also looks for partitions with it search command, which can add a bit.

If booting is slow then there may be issues with some driver and you can remove quiet splash in grub linux line when booting to monitor boot process or check with log file view the log file dmesg which is all the lines posted when booting.

---

