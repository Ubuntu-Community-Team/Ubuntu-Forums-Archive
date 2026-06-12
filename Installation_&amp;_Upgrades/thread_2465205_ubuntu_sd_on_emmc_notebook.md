---
title: "ubuntu sd on emmc notebook"
date: 2021-07-25
forum: Installation &amp; Upgrades
---

### Post by syberyandog on 2021-07-25
hi! im quite a newbie in the linux world , the reality is that i was trying to bring back to life a notebook with a busted emmc using linux from the sd card itself

My main thought was to make a full install in the sd then use an usb to boot into it because sd cards are not read like booteable devices mostly.

The thing is , is it possible ? can i get some help in doing it somehow ? thanks in advance !

---

### Post by grahammechanical on 2021-07-25
You could be the first person to try something like this. What you learn would make you an expert. You tells us absolutely nothing about the notebook. What are the hardware specifications? What ports does it have? Is this machine capable of running Ubuntu or some other distribution of Linux?

The difficulty as I see it is the impossibility of running two operating systems at once on the same hardware. I do not think it is possible to run an OS from a USB stick that will then load the OS on the SD card without first shutting down the OS on the USB stick.

It might be possible to run the OS from the USB stick and use the SD card as storage.

Regards

---

### Post by Impavidus on 2021-07-25
It seems I understand the question differently.

Some computers can boot from sd card, others can't. You could put the installed system on the sd card, but the bootloader and /boot partition on the usb drive. But unless you've only got a very small usb drive, you could just as wel install the entire system on the usb drive.

---

### Post by tea for one on 2021-07-25
You can boot an OS directly from a SD card on some devices - have you experimented with your notebook?

If your notebook is one of those devices with a 32GB emmc, then you should think about a lighter version of the Ubuntu family e.g. Xubuntu or Lubuntu?

I assume that you want the OS installed on the SD card because it would be hidden in the chassis and therefore safely portable - is that correct?

Why not consider using a nano usb device - fairly easy to install an OS and bootable?

[https://www.amazon.co.uk/SanDisk-SDCZ430-032G-G46-Ultra-Flash-Drive/dp/B077VXV323?ref_=ast_sto_dp&th=1&psc=1](https://www.amazon.co.uk/SanDisk-SDCZ430-032G-G46-Ultra-Flash-Drive/dp/B077VXV323?ref_=ast_sto_dp&th=1&psc=1)

---

### Post by syberyandog on 2021-07-25
> **grahammechanical said:**
> You could be the first person to try something like this. What you learn would make you an expert. You tells us absolutely nothing about the notebook. What are the hardware specifications? What ports does it have? Is this machine capable of running Ubuntu or some other distribution of Linux?

The difficulty as I see it is the impossibility of running two operating systems at once on the same hardware. I do not think it is possible to run an OS from a USB stick that will then load the OS on the SD card without first shutting down the OS on the USB stick.

It might be possible to run the OS from the USB stick and use the SD card as storage.

Regards


Sorry i didnt say much about the notebook , its an Asus vivobook , it has a celeron n4000 and 4g of ram.
I already try and succefully run diferents builds of linux from usb sticks and windows to go, they work fine depending on how much demanding they get.


> **Impavidus said:**
> It seems I understand the question differently.

Some computers can boot from sd card, others can't. You could put the installed system on the sd card, but the bootloader and /boot partition on the usb drive. But unless you've only got a very small usb drive, you could just as wel install the entire system on the usb drive.

That was the idea in general yes, to use only the usb like a "opener" lets say and redirect the boot process to the Sd card itself , i have some 32 sticks with some live ubuntu builds.
The general idea was to use a live build to install all of the data in the Sd , and then maybe use Grub on a stick to try to boot it ? 
I was also thinking about plop boot manager as an idea to redirect the boot sequence to the Sd but i kinda can't get it to work in the notebook , i burn the image and all but tue stick doesn't boot for some reason.

> **tea for one said:**
> You can boot an OS directly from a SD card on some devices - have you experimented with your notebook?

If your notebook is one of those devices with a 32GB emmc, then you should think about a lighter version of the Ubuntu family e.g. Xubuntu or Lubuntu?

I assume that you want the OS installed on the SD card because it would be hidden in the chassis and therefore safely portable - is that correct?

Why not consider using a nano usb device - fairly easy to install an OS and bootable?

[https://www.amazon.co.uk/SanDisk-SDCZ430-032G-G46-Ultra-Flash-Drive/dp/B077VXV323?ref_=ast_sto_dp&th=1&psc=1](https://www.amazon.co.uk/SanDisk-SDCZ430-032G-G46-Ultra-Flash-Drive/dp/B077VXV323?ref_=ast_sto_dp&th=1&psc=1)

Yes i have and 32gb stick that i use with some live builds but the speed its kinda slow, so knowing that the notebook itself has the sd reader i thought it woud be a shame to not use it basically.

---

### Post by grahammechanical on 2021-07-25
Let us assume that you are familiar with the Ubuntu installation procedure and in particular the Something Else option. If I was to experiment doing this I would have two USB sticks each in a USB port. 

One USB stick would have the Ubuntu live session. Selecting Try Ubuntu I would open GParted and I give the SD card a GPT partition table and an Ext4 format. I may even create partitions on the SD card such as a partition for root and a partition for home and may be a partition for swap. A Data partition may be?

Then I would give the other USB stick a GPT partition table and an Ext4 format. I would create a boot partition and a BIOS boot partition or EFI boot partition depending on whether the motherboard was BIOS or UEFI.

Then I would install Ubuntu using the something else option to set the mount point of the boot partition on the USB stick as /boot and Grub to be installed on the USB stick and I would set the mount point of / to a partition on the SD card and set the mount point of /home also to a partition on the SD card. The same for the swap partition. And let the install proceed and see what happens.

Set the machine to boot from the USB card. I hope it works. If it does a Data partition could be made to automatically mount by editing the /etc/fstab file but that is another question.

Regards

---

