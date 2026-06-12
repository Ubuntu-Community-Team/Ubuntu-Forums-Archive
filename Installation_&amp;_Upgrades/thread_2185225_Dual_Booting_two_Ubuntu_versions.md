---
title: "Dual Booting two Ubuntu versions"
date: 2013-11-01
forum: Installation &amp; Upgrades
---

### Post by SuperFreak on 2013-11-01
I have Ubuntu 12.04 on my computer now. I would like to put Ubuntu 14.04 as a dual boot on the same computer.
Here are the steps I have taken
1)created USB key with 14.04 64 bit on it
2)created 2 partitions one for root and one for home
3) Run 14.04 installation up to point of creating mount points for / and home
The next step I am stuck at is select "device for bootloader installation". 

Should this be the preexisting efi partition or somewhere else. Will this overwrite the 12.04 bootloader or work hand in hand with it?

---

### Post by ubfan1 on 2013-11-01
Since 14.04 will not be officially released for several months, it might be a good idea to try to separate any new bootloader code it wants to put into the EFI partition, so you can keep your existing, released code until you are ready to update.  In theory, a second EFI partition should work to allow this, but will be inconvenient, as you should only have one boot flag set at any time.  Another alternative is to skip the bootloader, and let update-grub on the 12.04 system pick up the new 14.04 system.   If you just installed the 14.04 to the existing EFI partition, it should work, but then the grub boot menu would be from the 14.04 system -- so you would have to run grub-update there when you changed 12.04 kernels.  Depends upon how important it is to keep the 12.04 system running while you are experimenting with the 14.04.

---

### Post by SuperFreak on 2013-11-01
Thanks for your reply ubfan1. from what I understand of your post it is possible to install 14.04 without a bootloader(and later update the 12.04 bootloader). If that is the case what do I do with the drop down menu for "device for bootloader installation". As far as I can tell there is no option for leaving this blank.
I definitely want to keep 12.04 functional as that is my "production machine" I don't have another computer to test 14.04. Perhaps this is too risky to do if 12.04 may get wrecked

---

### Post by fantab on 2013-11-01
I don't think so. Ubuntu installer does not give you an option to NOT install GRUB.
Just let the installer install GRUB and there shouldn't be a problem. Or you can install Grub to 14.04's / partition (This what I'd do if it were a BIOS/Legacy Boot).

A suggestion regarding Partitions:
Having only 5.34GB of /home is pointless. Either don't have /home at all or add more GB to it.
I have installed 14.04 to a 20GB Partition and have about 60% free space.

---

### Post by leeper69 on 2013-11-01
Hi I have 13.10 and 12.4 dule booting on my system when I installed 13.10 I installed grub on the root for it's partision Looks like / in gparted this kept my old grub for 12.4 working.
I noticed that you dont have a linux swap partision from your attached thumbnail of your gparted, this partision should be at least twice the size of your installed memory and one swap file will work for both system files.

---

### Post by SuperFreak on 2013-11-02
@leeper69  Thanks that sounds like a good plan.
My Swap partition is on another hard drive not shown in the gparted screenshot
@Fantab You of course are right about the partition sizes. However the plan is to eventually copy the root and home partitions to a new space(using ReDo) and expand the home directory. In my 12.04 install root is presently using over 14 GB so I want to keep root fairly large

---

### Post by ubfan1 on 2013-11-02
Savest to experiment with 14.04 in a virtual machine.  Install qemu-kvm (or your favorite):
sudo apt-get install qemu-kvm
qemu-img create  myvm.img -f qcow2 10G
kvm -m 750 -cdrom  14.04.iso -boot d myvm.img
kvm -m 750 myvm.img
Creates a (max) 10G vm, which starts small and expands to fill space.  Uses 750M of memory, usr more if you like.

I guess the "none" option was wishful thinking on my part, I've found even explicit locations are sometimes ignored and the hard disk's EFI partition used (seems to vary by release).

---

