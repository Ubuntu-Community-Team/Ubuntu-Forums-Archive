---
title: "USB flash Drive multi-boot"
date: 2010-02-21
forum: Installation &amp; Upgrades
---

### Post by blzrdphoto on 2010-02-21
I'm fairly new to the Linux community but I do have some experience doing minor things but what I'm trying to do is a little beyond my level.

I am trying to dual boot or possibly tri-boot on a Thumb drive.  My goal is to create a rescue/removeable OS disk.  I want to have ubuntu on one partition, a swap disk on another, then have Bart PE on another, then if possible a real installation of windows XP that is fully functional.  I have tried searching online for something like this and I couldn't find anything.

I understand how to install...
 - Ubuntu 9.10 with casper-rw ([http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-in-windows/](http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-in-windows/))
 - Bart PE ([http://www.tomshardware.com/reviews/windows-pocket,1113.html](http://www.tomshardware.com/reviews/windows-pocket,1113.html))
 - Windows XP ([http://www.michaelstevenstech.com/cleanxpinstall.html](http://www.michaelstevenstech.com/cleanxpinstall.html))

I just don't know how to get all this onto one flash drive with a swap disk.  I'm using a Super Talent 4.0 GB flash drive ([http://www.supermediastore.com/product/u/supertalent-4gb-pico-c-usb-flash-drive](http://www.supermediastore.com/product/u/supertalent-4gb-pico-c-usb-flash-drive)) and what I want is...

1.0 GB   - Ubuntu 9.10
0.5 GB   - Bart PE
1.5 GB   - Windows XP SP2
1.0 GB   - Swap

I may also want to add in Ubuntu Rescue Remix 9.10 Live just for good measure but there's not really a huge need at this point.

_____________________________________________________

Does anyone know if this has been attempted or been successful?  If not does anyone have any ideas how this might be implemented?

Thank you in advance for any help!

---

### Post by ottosykora on 2010-02-21
it might be possible somehow, with the use of reasonably configurable boot manager, but few things could be problematic. Bart: whyt type of partition you want have for it? XP again what partiton? If those are similar partitons, it might not work at all, BartPE is also kind of windows, it will try to discover other win partitions and only one is windows readable partition is allowed on a flash drive unless it is one you are able to flip the removable bit permanently in the controller.

Then forget the swap. Leave some 10 % empty on the flash, otherwise it will tend very slow. Now swap files are more in use anyway.

You could use one partiton only for grub (just small one)and then start all others from there. This would give you more controll over what is going on.

But already the installation of XP on the stick is challenge in itself, possible but complex.

Curious how it will work when it is done, report then here.

---

### Post by ottosykora on 2010-02-21
note also, what is described here: [http://www.michaelstevenstech.com/cleanxpinstall.html](http://www.michaelstevenstech.com/cleanxpinstall.html)

will definitely not work on flash. XP is on the installation disk configured so it will not install on any removable media. There are tricks to overcome this, but not just plug and play.
Also XP will have to be activated and is in configuration then for one computer only, that means only one set of hardware. Will not work on next computer this way. 
You might look then for things like winbuilder to make it.

for the grub, respectve the grub partition, see

[http://members.iinet.net.au/~herman546/p15.html#How_to_make_a_separate_Grub_Partition_](http://members.iinet.net.au/~herman546/p15.html#How_to_make_a_separate_Grub_Partition_)

---

### Post by C.S.Cameron on 2010-02-21
I have used information on this page to install XP to flash drive:
[http://www.ngine.de/article/id/8](http://www.ngine.de/article/id/8)
But there was not enough space on the drive afterward to do a full install of Ubuntu.
Also XP runs very, very slow from flash drive, but is good enough to play movies.

---

### Post by blzrdphoto on 2010-02-21
After what I have read so far it's going to be a lot more trouble than it's worth to have bart pe and windows XP on the same drive so I am going to scrap that.  

So what I would like to do now is have

- 1 GB    Ubuntu 9.10
- 0.25 GB URR 9.10 ([http://www.pendrivelinux.com/install-ubuntu-rescue-remix-to-a-flash-drive/](http://www.pendrivelinux.com/install-ubuntu-rescue-remix-to-a-flash-drive/))
- 1 GB    Bart PE using FAT16
All remaining space to swap disk and grub partition.

The only problem is I'm not all that familiar with repartitioning drives and setting up grub controllers.  What would be the proper order to install these on? and how would I get the drive to have all the neccessary partitions?  Can I do that from windows or would I need to use fdisk in linux?  (Fdisk is a little overwhelming for me) Would I be able to install bart pe and then when I install linux it finds the windows partition and sets up the grub for me?  

Sorry if I sound like I'm stupid, haha but thank you guys for all the replies so far.  I'm having a bit of a reality check...

---

