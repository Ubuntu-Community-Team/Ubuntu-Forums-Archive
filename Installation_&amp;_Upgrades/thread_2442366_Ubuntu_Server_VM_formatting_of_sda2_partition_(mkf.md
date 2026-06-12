---
title: "Ubuntu Server VM: formatting of sda2 partition (mkfs.ext4 -G 4096) before install"
date: 2020-05-02
forum: Installation &amp; Upgrades
---

### Post by antoon-g on 2020-05-02
Hi,

I'm venturing into the fascinating world of Ubuntu and would like to install Ubuntu Server 20.04 LTS as a virtual machine in Hyper-V.

Microsoft recommends that, when creating the file system on which Ubuntu will be installed, the number of block groups that will be packed together to create a larger virtual block group (or "flex_bg group") in an ext4 filesystem should be set to 4096 (mkfs.ext4 -G 4096 /dev/sdX1)

When installing the Ubuntu Server VM, I didn't see an option to set this parameter.

After having installed Ubuntu Server with the default options, I have the following partitions:

```
Model: Msft Virtual Disk (scsi)
Disk /dev/sda: 42.9GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags:

Number  Start   End     Size    File system  Name  Flags
 1      1049kB  538MB   537MB   fat32              boot, esp
 2      538MB   42.9GB  42.4GB  ext4

```
When running ```
dumpe2fs -h /dev/sda2
``` I see that the number of block groups for sda2 is 16:

```
Flex block group size:    16 

```

Is there a way to set this to 4096 during install?

If not, could I repartition sda2 with the correct number of block groups (with which tool (e.g. mounted in a (virtual) DVD drive?)) and then reinstall selecting manually the sda1 and sda2 partitions?

---

### Post by antoon-g on 2020-05-03
Would the following work:


[LIST=1]
[*]mount an Ubuntu LiveCD in a virtual DVD drive and choose 'Try Ubuntu without any change to your computer'
[*]format the sda2 partition with the following command ```
mkfs.ext4 -G 4096 /dev/sda2
``` Will the Ubuntu instance launched from the LiveCD see this partition?; Should I also wipe the sda1 partition with ```
mkfs.vfat -F 32 /dev/sda1
```
[*]reinstall Ubuntu Server and manually select the (reformatted?) sda1 partition and the (reformatted) sda2 partition
[/LIST]

Is there a way to make the Ubuntu Server installer use these partitions as-is without reformatting ?

---

### Post by antoon-g on 2020-05-04
I figured it out and wrote a How-to [here]("https://askubuntu.com/questions/1234686/ubuntu-server-vm-hyper-v-formatting-of-sda2-partition-mkfs-ext4-g-4096-dev").

@Canonical: could you please consider adding an option in the Filesystem Setup menu to set the 'Flex block group size' (perhaps with a dropdown menu offering choices of the power of 2 ?) of the filesystem partition?

---

