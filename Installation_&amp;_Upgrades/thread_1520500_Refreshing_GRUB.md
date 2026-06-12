---
title: "Refreshing GRUB?"
date: 2010-06-29
forum: Installation &amp; Upgrades
---

### Post by Nibinaear on 2010-06-29
I have a dual boot windows / ubuntu hdd 320gb. I had windows problems so wanted to format everything and start again. Unfortunately I had 80gb of stuff which I needed and placed this onto a third drive before format. Just to complicate matters my original windows installation had Ubuntu on wubi inside of it which is now gone. So just to recap:

- Windows with wubi, now gone (free space). 177gb.
- Ubuntu on separate partition now in use. 22gb.
- Third partition for backups. 98gb.

What I want to do now, is:

a) Resize the partition for windows and give the Ubuntu partition more space. I've tried the gparted live cd but it fails to load properly. It either presents nothing, i.e. a blank screen, or presents swirling colourful patterns. I can't resize the ubuntu partition otherwise as it's mounted.

b) Refresh GRUB boot loader so that it is accurate. How do I do this or is it automatic?

---

### Post by darkod on 2010-06-29
Which windows version do you have?

What is not accurate now in the grub menu?

---

### Post by Nibinaear on 2010-06-29
> **darkod said:**
> Which windows version do you have?

What is not accurate now in the grub menu?

I'm on windows 7. When I boot up I am still able to select windows 7 from the Grub menu. But then it just says no boot function. Obviously what I'd like to do is to install windows 7 and then get the grub option for it back. Will it come back automatically when I install windows?

---

### Post by darkod on 2010-06-29
> **Nibinaear said:**
> I'm on windows 7. When I boot up I am still able to select windows 7 from the Grub menu. But then it just says no boot function. Obviously what I'd like to do is to install windows 7 and then get the grub option for it back. Will it come back automatically when I install windows?

If you plan to reinstall win7 now, you will have to reinstall grub2 to the MBR after that. Then boot ubuntu once and run:

sudo update-grub

to update it with the new win7.

You should resize the win7 partition with the windows Disk Management tool, but if you can't boot it right now and want to reinstall it anyway, you can also use Gparted from the ubuntu cd in live mode.

When you boot the cd in live mode the root partition is not mounted and you can resize the win7 partition first, then the root partition. Note that if your root partition is logical (inside extended), you will have to enlarge the extended partition (container) first, and then the root partition.

Reinstalling ubuntu after you reinstall win7 might be a better option. All that resizing can leave things corrupted and not working well. It's up to you.

---

### Post by Nibinaear on 2010-06-30
An update. I'm feeling quite pleased with myself because I typed in all the code to get the grub loader back after windows install and it worked! 

I'm still struggling with resizing the partitions even in live mode. The resize option is not available for the Ubuntu partition.

**Reloading GRUB after a Windows Install**

In case anyone else is struggling with this, here is my version of the instructions:

1) Boot into the Ubuntu live cd by loading it at startup. When you reach the setup screen, exit the installation and you will find yourself in Ubuntu.

2) Enter a terminal and type: 

sudo fdisk -l

This will give you your list of partitions, going to System > Administration > Gparted is also very helpful for this. Now locate the sda number for your Ubuntu install, for example sda5. You can look in Gparted and it will be the nested partition alongside the linux-swap space and unallocated space.

3) Type: 

sudo mount /dev/sdaX /mnt   (where X is the number of your Ubuntu partition.) 

If you get an error telling you to specify the filesystem, then locate the filesystem of your partition from gparted and type the following instead:

sudo mount -t FS /dev/sdaX /mnt

Where FS is your filesystem type, for example ext4 or ntfs, and X is the number of your partition. So typically it might be:

sudo mount -t ext4 /dev/sda5 /mnt

4) Now type: 

sudo grub-install --root-directory=/mnt/ /dev/sda   (no partition number this time).

Now reboot the system and take out the live cd.

5) Re-enter the terminal once in Ubuntu again and type:

sudo update-grub

Hopefully you have grub back now and that this was helpful. I had to wade through loads of docs to get this so I hope this will save someone some time.

---

### Post by darkod on 2010-06-30
> **Nibinaear said:**
> 
I'm still struggling with resizing the partitions even in live mode. The resize option is not available for the Ubuntu partition.


If ubuntu is installed into an extended partition with root and swap being sda5 and sda6 for example, loading the live mode mounts the swap partition sda6. When you open Gparted you will notice the key symbol next to it and because of that next to the extended partition name.
Right click the swap partition and select Swapoff. That should remove the key from both the swap partition and the extended partition.
Then you can resize.
Don't forget that the extended partition is like a container holding the logical partitions. If root is logical and you want to extend it, you will first need to extend the extended partition itself, the container, and only then you can extend the root partition but make sure it doesn't go outside of the extended partition.

---

