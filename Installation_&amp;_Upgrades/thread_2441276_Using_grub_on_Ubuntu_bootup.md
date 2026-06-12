---
title: "Using grub on Ubuntu bootup"
date: 2020-04-21
forum: Installation &amp; Upgrades
---

### Post by andrew_s4 on 2020-04-21
I’ve just installed Ubuntu 19.10 on an external usb ssd. My main computer runs Ubuntu 18.04. Basically I just wanted to see if I could do it without screwing everything up. It all works fine. For most of you this is no great stretch, but I’m a novice at this and am learning through doing!  Now I have the problem that grub on boot up needs to have the usb external drive plugged in or it doesn’t know what to do, and this is the problem.... neither do I. How do I boot up into 18.04 when the usb drive isn’t plugged in. When both os are available on bootup grub gives me the option to boot up the os I wish. But if the usb isn’t there then I get the grub screen prompting me and I don’t know how to begin with it. Could use some help!
thanks
Andrew

---

### Post by CelticWarrior on 2020-04-21
BIOS or UEFI?

---

### Post by andrew_s4 on 2020-04-21
Uefi

---

### Post by CelticWarrior on 2020-04-21
> **andrew_s4 said:**
> Uefi

So just change the OS boot order to the other "Ubuntu".

---

### Post by ajgreeny on 2020-04-21
You currently have grub files on the external disk suppyling the configuration for running the grub when you boot the computer so if the external disk is missing at boot, so are the configuration files, presumably with the ***grub rescue*** prompt.

I think it is possible to sort this out quite easily, though I am no expert when dealing with external disks on a UEFI system.

See **Boot-Repair** in my signature below and follow the instructions there to run the Boot-Info-Script.	 **Do not run the default repair** but simply copy back here the pastebin link you get which will show us a lot more about your system and may help one of our experts tell you what to do next.

---

### Post by oldfred on 2020-04-21
Issue is that new install overwrite the ESP in the internal drive.
It is relatively easy to edit /EFI/ubuntu/grub.cfg which only has 3 lines and refers to the UUID & partition of your install. You just need to edit back to be internal drive.

You can also just boot to internal drive's install and run a total reinstall of grub in UEFI boot mode. Or use Boot-Repair advanced mode to do that for you, but not the default fix.

If in your install, you probably have to change permissions set by the mount of /EFI/ubuntu in your fstab. I change mine, but it may be a security issue. Early UEFI versions of Ubuntu used defaults, but now they use 0077, which gives no permission.
I found after I change it the normal partition remount of `sudo mount -a` does not fully work. I have to reboot system.
sudoedit /etc/fstab
```
#UUID=D966-440A  /boot/efi       vfat    umask=0077      0       1
UUID=D966-440A  /boot/efi       vfat    defaults      0       1

```

To see UUID of internal & external drive. The UUID shown should match external drive's install partition. You just need to change to internal drive's partition.
lsblk -o name,mountpoint,label,size,fstype,uuid,partuuid | egrep -v "^loop"

sudoedit /boot/efi/EFI/ubuntu/grub.cfg
```
search.fs_uuid [COLOR=#ff0000]b913e1bc-6f08-4984-b653-9a604d95470a[/COLOR] root 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg
```

If you put an ESP on your external drive, which you really needed to do. You then can copy /EFI/Boot & /EFI/ubuntu from internal drive's ESP to external drive's ESP. UEFI always boots external drives from /EFI/Boot/bootx64.efi. Full install version of grub also needs the files in /EFI/ubuntu.
You are starting UEFI boot from internal drive's ESP, but using the grub in the external drive's new install to boot.

---

### Post by andrew_s4 on 2020-04-22
> **ajgreeny said:**
> You currently have grub files on the external disk suppyling the configuration for running the grub when you boot the computer so if the external disk is missing at boot, so are the configuration files, presumably with the ***grub rescue*** prompt.

I think it is possible to sort this out quite easily, though I am no expert when dealing with external disks on a UEFI system.

See **Boot-Repair** in my signature below and follow the instructions there to run the Boot-Info-Script.     **Do not run the default repair** but simply copy back here the pastebin link you get which will show us a lot more about your system and may help one of our experts tell you what to do next.

Thank you for your reply. After running the Boot info script I got the following paste in link:
[http://paste.ubuntu.com/p/4Hw85zmvnd/](http://paste.ubuntu.com/p/4Hw85zmvnd/)
I should say at this point I have no idea what is going on! But trust....!

---

### Post by andrew_s4 on 2020-04-22
@OldFred
your explanation and remedies are way over my understanding. I&#8217;m in awe of all who can work in this way, but I&#8217;m struggling to understand your language. If it&#8217;s at all possible to re-write your help in simple layman&#8217;s speak, I&#8217;d give it a shot!! And I&#8217;d also be very grateful.

---

### Post by yancek on 2020-04-22
With the external drive attached, select to boot 18.04 from the boot menu then "You can also just boot to internal drive's install and run a total reinstall of grub in UEFI boot mode" as suggested above. 

Or as also suggested, mount the efi partition on the internal drive and go to the  /boot/efi/EFI/ubuntu/grub.cfg file there using root (sudo) and a text editor to change the first line in that file, example below:

> search.fs_uuid [COLOR=#ff0000]b913e1bc-6f08-4984-b653-9a604d95470a[/COLOR] root 

You need to replace the UUID above with the actual UUID of the partition on which you have installed Ubuntu 18.04.  Get this from a terminal by running:  sudo blkid

---

### Post by oldfred on 2020-04-22
Which is external drive?
You are only showing one ESP - efi system partition. /dev/nvme0n1p1   (note report shows it incorrectly in some places)

If install in sda is also UEFI, it can only boot from the one ESP.
But sda is using the old MBR partitioning & UEFI highly recommends gpt partitioning.
Windows only installs with UEFI using gpt, but Ubuntu does let you use MBR with UEFI, but really should not.

---

### Post by andrew_s4 on 2020-04-24
> **yancek said:**
> With the external drive attached, select to boot 18.04 from the boot menu then "You can also just boot to internal drive's install and run a total reinstall of grub in UEFI boot mode" as suggested above. 

Or as also suggested, mount the efi partition on the internal drive and go to the  /boot/efi/EFI/ubuntu/grub.cfg file there using root (sudo) and a text editor to change the first line in that file, example below:



You need to replace the UUID above with the actual UUID of the partition on which you have installed Ubuntu 18.04.  Get this from a terminal by running:  sudo blkid
So back to it... only have a bit of time per day to get anything done with this problem....
Thank you for your response. 
I have no idea how to go about “booting to internal drive’s install and running a total reinstall of grub in UEFI boot mode” . If you’ve got the patience to take me through the steps I’d gladly do it! But I’m not confident in doing this or changing things in a sort of experimental mode, and then end up with nothing working!!
Hope you’re up for the challenge 8-)

---

### Post by oldfred on 2020-04-24
If you have external drive attached, it should just boot into that install.
But you should get grub menu and chance to boot your internal drive's install.

If you do not get grub menu, and UEFI boot, you have to press escape between UEFI/BIOS screen and when grub menu would appear. Sometimes you have to try several times.
If you left UEFI fast boot on, you many not even have time to press any key. Then you need to turn off fast boot in UEFI.
And often then you need a full cold boot, or full power down and drain all power, so system does full start up & UEFI does its search of configuration to write to drive. Then you have just a few seconds to press correct key to get into UEFI/BIOS.

---

### Post by andrew_s4 on 2020-04-24
> **oldfred said:**
> If you have external drive attached, it should just boot into that install. 
Yes it does. But I don’t want it to. I would like the first choice of boot to remain the internal drive, and then the external. And to boot up regardless of wether the external is attached or not. And if I don’t have it attached, then nothing boots up. 

> But you should get grub menu and chance to boot your internal drive's install.
Yes. But the grub menu only starts up when the external drive is attached. I can see a problem in the future if should something happen to the external drive, I won’t be able to boot into my internal os, without a lot of hassle. 

>  If you do not get grub menu, and UEFI boot, you have to press escape between UEFI/BIOS screen and when grub menu would appear. Sometimes you have to try several times.
If you left UEFI fast boot on, you many not even have time to press any key. Then you need to turn off fast boot in UEFI.
And often then you need a full cold boot, or full power down and drain all power, so system does full start up & UEFI does its search of configuration to write to drive. Then you have just a few seconds to press correct key to get into UEFI/BIOS.
This is all ok and works as you’ve described. No problems there. 
BUT, “running a total reinstall of grub in UEFI boot mode” or
[COLOR=#000000]*“mount the efi partition on the internal drive and go to the /boot/efi/EFI/ubuntu/grub.cfg file there using root (sudo) and a text editor to change the first line in that file”*[/COLOR]
leaves me useless...I haven’t a clue how to start something like that. Unless you can give me step by step instructions. Which I’m hoping for :)

---

### Post by oldfred on 2020-04-24
Not all that difficult to edit a three line file.

But you can just reinstall grub.
Boot into your internal install using grub from external.
Then run this:
sudo grub-install --target=x86_64-efi --efi-directory=/boot/efi

Note your external will only boot from grub on internal drive, as not configured as a stand alone boot.
You may need this if internal grub not updated to find external.
sudo update-grub

But if grub does update when external not connected, it will forget that entry & you have to plug in external &  from internal run the update again.

---

### Post by andrew_s4 on 2020-04-25
Thank you Fred. Problem is solved! Thank you thank you

---

