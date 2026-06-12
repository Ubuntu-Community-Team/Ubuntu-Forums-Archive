---
title: "Ubuntu live CD and LVM fixing system ..."
date: 2008-03-01
forum: Installation &amp; Upgrades
---

### Post by senare on 2008-03-01
Oki i have tried to fix up my system after its gone broke but I just dont seam to be able to get it working so now i need som help, so please,

First what happend

I had some hardware problems in the form of a malfunctioning power button casing the system to reboot now and then so that might be one source of error and also i tried to do sudo apt get update and upgrade. which seams to have failed i am afriad i dont know the computer rebooted casued by previous mentioned power button and gave kernel panic msg. 

I was on 6.04 and was running a samba share ...

In order to fix it up i first changed the box to remove the hardware problems but the system still wouldnt boot. So i booted using a live CD then to get into the system i did ..

sudo apt-get install lvm2
sudo modprobe dm-mod
sudo vgchange -a y

now i could mount my partitions ...

sudo mkdir /mnt/linux/
sudo mount /dev/Ubuntu/root /mnt/linux/

i did manage to chroot , bit unclear on the detail as i never done it before ill double check what i did

then i updated my sources.list to a clean 7.10 

and did

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

in the hopes that it would fix what was broken if the last update and upgrade ect didnt go a that well ...

had some isuess with cups but i simply removed it since i am not using it since my printer is broke or at least i hope it isnt used for anything else than printing 

however when i tried to reboot it just wont it just prints 99 99 99 99 99 99 all over the screen  so help PLEASE 

And i am noob at linux so i might been doing the wrong things i just read up on what man and google gave me to get this far but it might been all wrong to ... 

Sincerly Maffe

---

### Post by senare on 2008-03-01
I know were little about the booting process but i seam to be using initrd and not initramfs if that helps any tips on how can i se my boot config with out messing it up

---

