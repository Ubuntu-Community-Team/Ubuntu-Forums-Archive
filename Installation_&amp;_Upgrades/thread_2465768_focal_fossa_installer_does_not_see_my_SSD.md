---
title: "focal fossa installer does not see my SSD"
date: 2021-08-11
forum: Installation &amp; Upgrades
---

### Post by Skaperen on 2021-08-11
i am wanting to install focal on my SSD first.  when i went into do something different that drive did not show up at all.  i quit the install and went into the "try Ubuntu" system and went to a terminal.  i did "cat /proc/partitions" and there was my SSD and all the partitions i already put on it.

my hardware:
/dev/sda a 1T hard drive with MBR partitioning
/dev/sdb a 120G SSD drive with hybrid partitioning (MBR and GPT)
/dev/sdc a 1T hard drive with MBR partitioning

could it be the GPT that is silently confusing the installer?  the kernel has it right.

---

### Post by ActionParsnip on 2021-08-11
Ubuntu can use GPT. No problems. Does the disk show in BIOS?

---

### Post by oldfred on 2021-08-11
Since everything else is MBR, I assume drives are set for AHCI?

Many with SSD have had to have UEFI update & SSD firmware update.

Hybrid is not recommended. And the only time you now need MBR partitioning is if using Windows in BIOS boot mode. And Windows in BIOS/MBR will read data from a gpt partitioned drive.

[http://www.rodsbooks.com/gdisk/hybrid.html](http://www.rodsbooks.com/gdisk/hybrid.html)

---

### Post by Skaperen on 2021-08-11
> **ActionParsnip said:**
> Ubuntu can use GPT. No problems. Does the disk show in BIOS?

yes, and i can boot from it.  i previously had 16.04 on it.

---

### Post by Skaperen on 2021-08-11
> **oldfred said:**
> Since everything else is MBR, I assume drives are set for AHCI?

Many with SSD have had to have UEFI update & SSD firmware update.

Hybrid is not recommended. And the only time you now need MBR partitioning is if using Windows in BIOS boot mode. And Windows in BIOS/MBR will read data from a gpt partitioned drive.

[http://www.rodsbooks.com/gdisk/hybrid.html](http://www.rodsbooks.com/gdisk/hybrid.html)

what is AHCI?

when i installed 16.04 on it (also hybrid partitioned before install) i did nothing special.  the other 2 disks (non-SSD) were partitioned the same way.  and 18.04 was installed on them.  the plan is, when i am ready in a couple days, 20.04 goes on the first drive.  everything was hybrid before.

i increased the partition size for the system partition.  that's why things are a bit more complex this time.  the / partition was 16G and i am expanding it to 28G as part of this re-install, so i am installing on /dev/sdb first.  that and /dev/sdc will become /home in the near future (is a partition on /dev/sda now).

MS Windows is nowhere near this computer.

---

### Post by oldfred on 2021-08-11
The only reason for hybrid was with older Mac that used gpt and older Windows that had to be in BIOS mode on MBR drive.
The rodbooks site has instructions for cleaning up a hybrid drive.

Now the only reason to have MBR is if Booting Windows in BIOS mode.

I even redid my old 2006 laptop with gpt and boot it in BIOS mode.
With gpt and BIOS you have to have a bios_grub partition, or with UEFI you have to have an ESP - efi system partition.

---

### Post by Skaperen on 2021-08-11
this machine is not UEFI.  i don't know if it can be set that way.  it is a System76 Kudu Pro from 2014.  i posted here instead of the System76 forum because previous Ubuntu worked fine.  also, this is actually Xubuntu 20.04 LTS that i am trying to install.  my running 18.04 LTS is Xubuntu, as well.  the install screen did show /dev/sda and /dev/sdc which are both partitioned hybrid.  that's why i thought it was a driver issue until i went into the live Ubuntu and did cat /proc/partitions after which i thought it was an SSD issue.  i don't know if the installer has a way to be told what device to install to beyond what it shows.

the reason i partitioned hybrid is because years ago i wrote a script that allocates partitions the way i wanted it done.  it positions partitions for maximum performance.  it uses the sgdisk command to create the partitions.  below is the script output:
```

part    first sector  last sector   size bytes             start byte  type  comments
------- ------------ ------------ ------------ ----------------------  ----  --------
pri mbr            0            0          512                      0  -MBR  MBR legacy
pri gpt            1           33       16k512                    512  -GPT  GPT primary
par   3           34         2047        1007k                    17k  8301  unused
par   1         2048     58720255     27g1023m                     1m  8304  /
par   2     58720256    125829119          32g                    28g  8200  swap
par   4    125829120    234441613  51g809m455k                    60g  8302  /home
par 128    234441614    234441614          512           111g809m455k  8301  MBR copy
sec gpt    234441615    234441647       16k512        111g809m455k512  -GPT  GPT secondary
------- ------------ ------------ ------------ ----------------------  ----  --------
part    first sector  last sector   size bytes             start byte  type  comments

COMMAND:
sgdisk -o -a 1 -n 1:2048:58720255 -t 1:8304 -n 2:58720256:125829119 -t 2:8200 -n 3:34:2047 -t 3:8301 -n 4:125829120:234441613 -t 4:8302 -n 128:234441614:234441614 -t 128:8301 /dev/sdb

```

---

### Post by Skaperen on 2021-08-11
_i don't actually need hybrid._  Linux is the _only OS_ i boot on this machine and it knows how to deal with GPT.  it even had partition 128 which i had in the GPT table that was not in the MBR table.  any other OSes i might ever boot up will be in VMs.  the reason for hybrid is that was the way **[FONT=courier new]sgdisk[/FONT]** created the partition table.  it was the only partition tool that worked from exact sector numbers that were calculated ahead of time.  i did not and cannot find an option to have **[FONT=courier new]sgdisk[/FONT]** make a purely GPT partition.  i do not know of a tool to convert an existing hybrid into GPT-only (i'll add it to my script if i learn of one).

---

### Post by oldfred on 2021-08-11
The man page for sgdisk shows a specific code for a hybrid partition.
And gdisk or sgdisk can convert a drive from MBR to gpt or vice-versa. Not sure what happens with hybrid.
But it says conversion will probably break booting & you have to reinstall boot loader and fstab as UUIDs/GUIDs will change.
And good backups required.


AHCI is one of the ways drives are connected. Used to be IDE, but newest is now NVMe
[https://en.wikipedia.org/wiki/NVM_Express#Comparison_with_AHCI](https://en.wikipedia.org/wiki/NVM_Express#Comparison_with_AHCI)
[https://en.wikipedia.org/wiki/Parallel_ATA#IDE_and_ATA-1](https://en.wikipedia.org/wiki/Parallel_ATA#IDE_and_ATA-1)

---

### Post by Skaperen on 2021-08-12
> **oldfred said:**
> The man page for sgdisk shows a specific code for a hybrid partition.
And gdisk or sgdisk can convert a drive from MBR to gpt or vice-versa. Not sure what happens with hybrid.
But it says conversion will probably break booting & you have to reinstall boot loader and fstab as UUIDs/GUIDs will change.
And good backups required.

it appears to make it be hybrid by default.  i do a command like:

```

sgdisk -o -a 1 -n 1:2048:58720255 -t 1:8304 -n 2:58720256:125829119 -t 2:8200 -n 3:34:2047 -t 3:8301 -n 4:125829120:234441613 -t 4:8302 -n 128:234441614:234441614 -t 128:8301 /dev/sdb

```

i am doing this to get ready for a full fresh install (i do it this way, instead of an in-place upgrade, to have a clean system for a few years without any 12 year old leftovers in the system).  it is the failure of the first shot that i started this thread about.  there will be more tries, including on a 2nd laptop (identical).  i do want to have a bootable system on /dev/sdb.  plans for the 3rd drive is to make the full drive be encrypted.

> **oldfred said:**
> AHCI is one of the ways drives are connected. Used to be IDE, but newest is now NVMe
[https://en.wikipedia.org/wiki/NVM_Express#Comparison_with_AHCI](https://en.wikipedia.org/wiki/NVM_Express#Comparison_with_AHCI)
[https://en.wikipedia.org/wiki/Parallel_ATA#IDE_and_ATA-1](https://en.wikipedia.org/wiki/Parallel_ATA#IDE_and_ATA-1)

not IDE and not NVMe so it must be AHCI.  at first, i thought you meant a mode i could enable in software.  i just did a quick read and obviously not.  and my next laptop will be NVMe SSD (i see they make 4TB MVMe SSD, now.  yummy!

a mainboard for a big box might have a mix of all attachment.  the board for a laptop generally will not and will have what targets a particular market.

---

### Post by Skaperen on 2021-08-12
i looked at the sizes in the installer and it appeared to be presenting /dev/sdb as /dev/sdc.  there was a /dev/sdd that appeared to be /dev/sdc.  so i went ahead and did the install of Xubuntu 20.04 and it came up on /dev/sdb.  i forgot to set the boot drive so now i have to select my old system in the grub menu.  no big deal.  it's weird that it is remapping the device paths like that.  but, it successfully installed and runs.  i'll be looking around to see what i got.

---

### Post by Skaperen on 2021-08-13
it turns out that the image i had download around a year ago, that i named as being Xubuntu, was not really Xubuntu.  it was something from somewhere and i cannot remember where it came from.  i did not log all that as i should have.  so i downloaded a new image linked from xubuntu.org.  i copied the image to 3 of my minne-pinnes and installed it.  this image did recognize the target drive as **[FONT=courier new]/dev/sdb[/FONT]** correctly.  now i have an initial test copy of Xubuntu 20.04 that i can boot up or supposedly run in a VM (not yet tested).

that previous image was first installed and gave me a Gnome setup and lacked package installs for lightdm and all of Xfce.

---

