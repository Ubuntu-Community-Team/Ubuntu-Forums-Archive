---
title: "Grub issues..."
date: 2013-01-30
forum: Installation &amp; Upgrades
---

### Post by Patriot3G on 2013-01-30
I've recently built a new PC...using the Asus Crosshair V Motherboard, and 3 hdds (2 SSD's). 

Right now Windows resides on the C:\ drive (first SSD), Ubuntu is on the F:\ drive (2nd SSD), and the other harddrive is empty. After installation I reboot, and Grub does not appear, its boots right into windows 8. 

Any ideas how I can fix this?

Thanks :D

---

### Post by papibe on 2013-01-30
Hi Patriot3G. Welcome to the forums ):P

If it is booting directly to Windows, you are going to need to use a Live media to repair/reinstall grub.

You can use the same Ubuntu installation media as a Live CD/USB, and repair grub. Take a look at this [tutorial]("https://help.ubuntu.com/community/Boot-Repair") for details.

Install grub on the disk that the BIOS is set to boot from.

Let us know how it goes.
Regards.

---

### Post by darkod on 2013-01-30
> **Patriot3G said:**
> I've recently built a new PC...using the Asus Crosshair V Motherboard, and 3 hdds (2 SSD's). 

Right now Windows resides on the C:\ drive (first SSD), Ubuntu is on the F:\ drive (2nd SSD), and the other harddrive is empty. After installation I reboot, and Grub does not appear, its boots right into windows 8. 

Any ideas how I can fix this?

Thanks :D

First of all, do you have ubuntu or wubi? If windows says that disk is F: that sounds like only wubi inside windows. Windows will only assign letters to ntfs partitions and linux doesn't install on ntfs. It uses its own filesystem.

So, any repairs you try to do must be for wubi, not ubuntu. And most tutorials are for proper ubuntu.

I suggest you install proper dual boot with linux type partitions, don't use the windows installer.

Go into Control Panel -> Programs, remove wubi (ubuntu), and install it properly booting with its cd/usb, not from inside windows.

---

### Post by Patriot3G on 2013-01-30
I was using a Wubi install, because I couldn't figure out what to do. lol

It's uninstalled now, and I'm sitting at the install screen. Here is where I think I'm going wrong: Device for bootloader installation.


Sda is the harddrive I was going to use to install Ubuntu on.
Sdb is my back up harddrive.
Sdc has Windows 8 on it.

Under "Device for bootloader installation" I have options to install to anyone of those 
drives and a partition on Sdc (Windows 8 Loader). Where should I install the bootloader too?

---

### Post by darkod on 2013-01-30
Any MBR, which means no partition, no number in it.

In this case, you can put it on the ubuntu disk, that would mean on /dev/sda. That's the device for bootloader installation.

Don't forget to set bios to boot from sda after that.

---

### Post by Patriot3G on 2013-01-30
Roger. I'll let you know how it goes. Thanks!

---

### Post by Patriot3G on 2013-01-30
OK, I installed it, and set the BIOS to boot off Sda. Now I get "No Boot Mgr".  So I used my USB stick to boot into Ubuntu and ran boot repair and got this:

"GPT detected. Please create a BIOS-Boot partition (>1MB, unformatted filesystem, bios_grub flag). This can be performed via tools such as Gparted. Then try again."



[http://paste.ubuntu.com/1590852/](http://paste.ubuntu.com/1590852/) < Boot info



Grr :(

---

### Post by darkod on 2013-01-30
You have gpt table on sda. For gpt table you need a 1MiB partition with NO filesystem, with the bios_grub flag set. This is so that grub2 can install correctly.

Boot into live mode first, create new blank gpt table and the small partition, then start the install and create the other partitions as you like. DO NOT touch the small one during the install.
```
sudo parted /dev/sda
unit MiB
print #(make sure it's the correct disk not to delete data on another one)
mklabel gpt
mkpart GRUB 1 2
set 1 bios_grub on
quit
```

That will make the small partition. Start the install and install again.

---

### Post by oldfred on 2013-01-30
In addition to bios_grub partition to get grub to install correctly in sda, you have some partition errors?

But it looks more like partition table is totally corrupt or is just random data? Or did you just have one large NTFS that is now too large, and the other partitions do not exist?

> /dev/sdb1 ends after the last sector of /dev/sdb
/dev/sdb1 overlaps with /dev/sdb2
/dev/sdb1 overlaps with /dev/sdb3
/dev/sdb1 overlaps with /dev/sdb4
/dev/sdb2 ends after the last sector of /dev/sdb
/dev/sdb2 overlaps with /dev/sdb3
/dev/sdb3 ends after the last sector of /dev/sdb
/dev/sdb4 ends after the last sector of /dev/sdb


---

### Post by Patriot3G on 2013-01-30
Alrighty. Trying that right now.

Sdb is a 1TB external, I just unplugged that.

---

### Post by Patriot3G on 2013-01-30
Still receive the boot mgr not installed error on boot. I tried to run boot-repair, but it keeps giving me this error: 

"Filesystem repair requires to unmount partitions. Please close all your programs. Then close this window."

Right now I am on the LiveOS...So nothing should be mounted.


[http://paste.ubuntu.com/1590976/](http://paste.ubuntu.com/1590976/) << New file.

---

### Post by oldfred on 2013-01-30
The bios_grub must be unformatted. It shows sda1 as ext4. Unformatted  is a choice in gparted (I think at bottom of list of formats). Then rerun Boot-Repair.

---

### Post by darkod on 2013-01-30
Not sure if that boot mgr message might be from UEFI. If the board is UEFI capable, make sure you have it disabled in bios. The boot type should be Legacy Only, without UEFI.

Since windows uses msdos table, you are using legacy boot and keep it that way. Don't involve uefi boot and best to be disabled.

---

### Post by Patriot3G on 2013-01-30
Alrighty, I tried that -- still have the same issue, I can get into windows if I chose the windows drive in my BIOS, but no grub and no ubuntu. The Boot-Repair is still doing the same "unmount" loop. This is frustrating :mad:


My board supports UEFI, but from what I read it cannot be disabled, there is nothing in the BIOS options to switch to legacy. Could this be the issue? It's the Asus Crosshair V Formula. I just updated the BIOS to the latest version, but still no option. 


Meh.

---

### Post by Patriot3G on 2013-01-30
[http://paste.ubuntu.com/1592085/](http://paste.ubuntu.com/1592085/) 

I finally figured out the boot repair part, but when I reboot with sda as my boot drive...it goes right into windows.  Meh.

---

### Post by darkod on 2013-01-31
You have no bootloader on /dev/sda. I think it got messed up during the install when it saw sda1 has a filesystem. I said not to create any filesystem on it and leave it alone during the install like three times at least. :)

I'm not sure if grub2 is fully installed or not. There is a short and long way to try a restore. Lets go with the short first.

Boot the ubuntu cd in live mode, open terminal and execute:
```
sudo mount /dev/sda2 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

Reboot without the cd and see if you get the grub menu and whether it works.

If you get a grub rescue prompt, don't worry, we can do the longer procedure after that.

---

### Post by Patriot3G on 2013-01-31
Boom! That did it. Thanks a lot man :D

---

