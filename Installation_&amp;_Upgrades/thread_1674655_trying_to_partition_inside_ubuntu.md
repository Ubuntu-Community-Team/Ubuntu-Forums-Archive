---
title: "trying to partition inside ubuntu"
date: 2011-01-24
forum: Installation &amp; Upgrades
---

### Post by gordie69 on 2011-01-24
Trying to partition inside ubuntu so I can install W7 dual booted aside ubuntu can someone help having a blonde moment

---

### Post by Quackers on 2011-01-24
Any partitioning needs to be done without the system running. I would suggest using gparted from the live cd desktop. You'll also need to right-click on the swap partition and select "swapoff" before any changes are made.

---

### Post by WthIteh on 2011-01-24
> **gordie69 said:**
> Trying to partition inside ubuntu so I can install W7 dual booted aside ubuntu can someone help having a blonde moment
Windows 7 usually needs about 20 GB. You may give it more if you want to install more software on it. The final decision will be related to your total hard disk size too.
You could do the repartitioning using gparted.
If you haven't it installed you could install it by
```
sudo apt-get install gparted
```
and run it by
```
sudo gparted
```
then select the drive with extra space and resize it, creating free space.
DO NOT forget to backup your important data before any change.

---

### Post by presence1960 on 2011-01-24
> **WthIteh said:**
> Windows 7 usually needs about 20 GB. You may give it more if you want to install more software on it. The final decision will be related to your total hard disk size too.
You could do the repartitioning using gparted.
If you haven't it installed you could install it by
```
sudo apt-get install gparted
```
and run it by
```
sudo gparted
```
then select the drive with extra space and resize it, creating free space.
DO NOT forget to backup your important data before any change.

You can not resize the ubuntu partition from within ubuntu because it will be mounted. There is no way to unmount it while ubuntu is running. It must be done from a bootable CD/DVD/USB such as the ubuntu Live CD, gparted Live CD, or a third party software such as parted-magic, hiren's boot CD, etc.

---

### Post by Megaptera on 2011-01-24
Have you looked in to the Grub / boot issues with installing Windows after Ubuntu? I belive Grub works best with Ubuntu installed after Windows?

---

### Post by WthIteh on 2011-01-24
> **Megaptera said:**
> Have you looked in to the Grub / boot issues with installing Windows after Ubuntu? I belive Grub works best with Ubuntu installed after Windows?
It is easy to reinstall grub after installing Windows from a LiveCD.
Also it is not required to use gparted from a LiveCD in all cases. Maybe there was one separate big partition as the home partition which could be unmounted and resized.
We should wait for next post and details about partitions.

---

### Post by gordie69 on 2011-01-24
Thanks guys

---

### Post by gordie69 on 2011-01-24
That sudo command is something

---

### Post by presence1960 on 2011-01-24
> **WthIteh said:**
> It is easy to reinstall grub after installing Windows from a LiveCD.
Also it is not required to use gparted from a LiveCD in all cases. Maybe there was one separate big partition as the home partition which could be unmounted and resized.
We should wait for next post and details about partitions.

+1 On GRUB. Quite a few people do not fathom that when you install windows after linux that windows overwrites GRUB on the MBR. Therefore from ignorance comes the belief that it is "better" to install windows first. All you need to do is spend 1 minute from the live CD and run 2 commands to put GRUB back on the MBR.

As far as resizing a partition other than /, you are absolutely correct. The vagueness of the original post led me to believe the OP was trying to resize /. We'll have to wait for the OP to explain further.

---

### Post by Megaptera on 2011-01-24
> **presence1960 said:**
> +All you need to do is spend 1 minute from the live CD and run 2 commands to put GRUB back on the MBR..

Thanks for that, what are the 2 commands please?

---

### Post by presence1960 on 2011-01-24
> **Megaptera said:**
> Thanks for that, what are the 2 commands please?

if your ubuntu partition is sda7 and you want GRUB on MBR of sda do this from the Live CD in terminal:

```
sudo mount /dev/sda7 /mnt
```This will mount your ubuntu / partition, Then in terminal run:

```
sudo grub-install --root-directory=/mnt/ /dev/sda
```This will install GRUB in the MBR of sda and look to the partition in /mnt (sda7 you mounted with the previous command) for the boot files. 

[here]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD") is a link with more detailed instructions for your reference.

---

### Post by Megaptera on 2011-01-24
Thanks very much presence1960.

---

### Post by gordie69 on 2011-01-30
sorry the commands just on sudo which completely directly does what every you want still learning but anyway thanks for the partition program gpart I installed and it works

---

