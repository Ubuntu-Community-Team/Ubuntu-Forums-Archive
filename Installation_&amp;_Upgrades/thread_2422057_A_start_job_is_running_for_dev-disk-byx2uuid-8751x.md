---
title: "A start job is running for dev-disk-by\x2uuid-8751\x2dF0FF.device"
date: 2019-07-01
forum: Installation &amp; Upgrades
---

### Post by jonathan232 on 2019-07-01
Note: This is my first time using Ubuntu Forms so please feel free to advise me to change formatting and such. Any advice is appreciated. 

I just decided to use Ubuntu over Windows 10 on my laptop. I proceeded to install Ubuntu 18.04 onto a flashdrive with Rufus and then try to boot it up. After some fiddling with boot options and nomodeset, I was able to erase Windows and install Ubuntu. During the boot, this message appears.

"(1 of 2) A start job is running for udev Coldplug all devices (seconds / no limit)"
"(2 of 2) A start job is running for dev-disk-by\x2uuid-8751\x2dF0FF.device (seconds / 1min 30s)"

After 1 minute and 30 seconds, it gives me emergency mode and these errors.

[ TIME ] Timed out waiting for device dev-disk-by\x2uuid-8751\x2dF0FF.device.
[DEPEND] Dependency failed for File System Check on /dev/disk/by-uuid/8751-F0FF.
[DEPEND] Dependency failed for /boot/efi.
[DEPEND] Dependency failed for Local File Systems.
[DEPEND] Dependency failed for Clean up any mess left by 0dns-up

I have already checked by /etc/fstab for wrong uuids. The only thing out of the ordinary is that there is a /swapfile line.
/swapfile    none    swap    sw    0    0

Thanks in advance

EDIT: After Installing Boot-Repair on instruction from @TheFu
I was having trouble loading the live usb, black screen on boot with nomodeset not helping. Eventually I figured out it was an acpi problem so I used acpi=off. Here is the link:

Boot-Repair Summary Link: [http://paste.ubuntu.com/p/8WmzfmmdMc/](http://paste.ubuntu.com/p/8WmzfmmdMc/)

EDIT: After running commands and gathering information with instructions from @ubfan1
Hey ubfan1,

My machine is a HP ENVY m6 Notebook.

Mind I am running these commands from the recovery terminal after the start job times out. 
"sudo blkid | grep swap" outputs nothing as my fstab is using /swapfile? Is this an error?
```

sudo blkid
/dev/sda1: UUID="8751-FOFF" TYPE="vfat" PARTLABEL="EFI System Partition" PARTUUID="32790d3c-9507-4d84-b07e-301fcfcf5398"
/dev/sda2: UUID="af639486-f01f-4ed2-84eb-96ab9ce96fc8" TYPE="ext4" PARTUUID="769092c0-a6c4-46c1-95c5-cad175211d8e"

```

How do you want me to run dosfsck? With -a?
I ran fsck with no arguments and this printed.
```

fsck
fsck from util-linux 2.31.1
e2fsck 1.44.1 (24-Mar-2018)
/dev/sda2 is mounted
e2fsck: Cannot continue, aborting.

```

Also, how would I add a boot flag to the ESP?

Sorry, I'm new to linux.

---

### Post by TheFu on 2019-07-02
```
[DEPEND] Dependency failed for File System Check on /dev/disk/by-uuid/8751-F0FF.
```
is probably the EFI partition.  Look at how it is setup.
Did you choose to use LVM or not?
Is the system legacy BIOS boot or EFI boot?

If it is a specific make/model of computer, often searching for "ubuntu install {make/model}" will provide tips to get it installed. Some vendors are known NOT to follow EFI standards in their BIOS implementations, so manual intervention is needed just to boot.

To get the most/best help, Boot into the "Try Ubuntu" using that flash drive, install boot-repair package and run it. **DO NOT **ask it to run a repair.  Ask it to gather information, I think that button is in the bottom-center of the screen.  It will post the important data and provide a URL.  Post that URL back here so some experts can review it and make suggestions.

---

### Post by jonathan232 on 2019-07-05
I was able to get the link.
I also added it to the main post.

Thanks again

---

### Post by jonathan232 on 2019-07-08
bump

---

### Post by Frogs Hair on 2019-07-09
Thread moved per request.

---

### Post by jonathan232 on 2019-07-12
bump

---

### Post by jonathan232 on 2019-07-13
Bump

---

### Post by ubfan1 on 2019-07-14
Nothing obvious, usually the problem is a wrong UUID.  lets check again with sudo blkid |grep swap  to see what uuids are current.  then check the filessytem on the ESP with dosfsck. Might as well add boot flag to the ESP, that's what the spec says. Now what brand machine are you using?  Some brands have vendor specific issues (HP names, Acer trust, etc.).

---

### Post by jonathan232 on 2019-07-14
Hey ubfan1,

BRAND MACHINE
My machine is a HP ENVY m6 Notebook.

COMMANDS
Mind I am running these commands from the recovery terminal after the start job times out. 
"sudo blkid | grep swap" outputs nothing as my fstab is using /swapfile? Is this an error?
```

sudo blkid
/dev/sda1: UUID="8751-FOFF" TYPE="vfat" PARTLABEL="EFI System Partition" PARTUUID="32790d3c-9507-4d84-b07e-301fcfcf5398"
/dev/sda2: UUID="af639486-f01f-4ed2-84eb-96ab9ce96fc8" TYPE="ext4" PARTUUID="769092c0-a6c4-46c1-95c5-cad175211d8e"

```

How do you want me to run dosfsck? With -a?
I ran fsck with no arguments and this printed.
```

fsck
fsck from util-linux 2.31.1
e2fsck 1.44.1 (24-Mar-2018)
/dev/sda2 is mounted
e2fsck: Cannot continue, aborting.

```

Also, how would I add a boot flag to the ESP?

Sorry, I'm new to linux

---

### Post by ubfan1 on 2019-07-14
Oops, sorry, had swap on my mind since I just this problem with a swap file that had been reformatted by another installer (changing the UUID).
For the boot flag, you could use parted /dev/sda   (or whatever disk)  and the command  
set 1 boot on
Linux really doesn't need the boot flag, but your machine's firmware may use it in some way (Since you do boot, you probably don't need it).

HP, usually takes some name tweaking to make grub run, but again, not your problem if it runs grub.

The mount of the ESP at /boot/efi may be unmounted -- it's really only needed for updating the bootloaders.
then dosfsck -a /dev/sda1  or whatever
Repeat until no errors.

Checking the UUIDs used in the bootprocess:
Look at /boot/efi/EFI/ubuntu/grub.cfg
That should be a 3 line stub file which brings in the maintained grub.cfg file from the root filesystem -- check that the UUID in use if really for the root filessytem.
The maintained grub.cfg file looked OK, and the UUID had not changed, so that should be ok.
The start job may take 90 seconds to finish, there is a countdown at the end of the line. Did you wait long enough for it to finish?  Bad if it restarts repeatedly.

---

### Post by jonathan232 on 2019-07-14
I checked with parted /dev/sda. sda1 already has the boot flag on it

I DID wait long enough for the start job to finish. It times out and brings me to maintenance mode. Thats how I get to a command line.

The only error I get from the dosfsck -a /dev/sda1 is for a dirty bit which it cleans up.
dosfsck -a /dev/sda2 returns "Logical sector size is zero."

I also tried changing the entries in /etc/fstab to /dev/sda1 and sda2 but that just changed it to:
```

[COLOR=#000000](1 of 2) A start job is running for udev Coldplug all devices (seconds / no limit)[/COLOR]
[COLOR=#000000](2 of 2) A start job is running for dev-sda1.device (seconds / 1min 30s)[/COLOR]

```

I reverted my fstab and the original error is still occurring.

---

### Post by jonathan232 on 2019-07-14
Something to note, when I add noapic to the boot options, it displays this:
```

Gave up waiting for root file system device.
-Boot args (cat /proc/cmdline)
  -Check rootdelay= (did the system wait long enough?)
-Missing modules (cat /proc/modules; ls dev)
ALERT! UUID=[COLOR=#000000][FONT=&amp]af639486-f01f-4ed2-84eb-96ab9ce96fc8 does not exist. Dropping to a shell!


[/FONT][/COLOR]BusyBox v1.27.2 (Ubuntu 1:1.27.2-2ubuntu3) built-in shell (ash)
Enter 'help' for a list of built-in commands

(initramfs) <-- Here is where I can type

```

The UUID given above is sda2 according to fstab and blkid.

---

### Post by ubfan1 on 2019-07-15
From your posting, I do not see the UUID=[COLOR=#000000][FONT=&amp]af639486-f01f-4ed2-84eb-96ab9ce96fc8 on anything. Your blkid, line 527:
527 [/FONT][/COLOR]/dev/sda1: UUID="8751-F0FF" TYPE="vfat" PARTLABEL="EFI System Partition" PARTUUID="83b16673-0fbe-443a-a5f4-accbd2e3967c"
528 /dev/sda2: UUID="ff752250-eea1-461a-b14c-4329e304319a" TYPE="ext4" PARTUUID="065a897d-d8da-496d-91fb-cc8ef5289b54"

---

### Post by jonathan232 on 2019-07-15
Where are you seeing this, I'm only able to see to line 347 on my boot repair summary. Also when I run blkid I see that the sda2 uuid matches what it supposedly should be. Not the one you are showing?

---

### Post by ubfan1 on 2019-07-15
From the link in your message number three.

---

### Post by jonathan232 on 2019-07-15
I'm sorry, that was user error on my part. I installed Ubuntu using a different USB and updated the repair link. I just checked the post in advanced mode and it said the URL didn't change although the display text for it did? I've removed the outdated link.

---

### Post by jonathan232 on 2019-07-16
I think I may have found the problem?
In maintenance mode when I run mount, I only see that sda2 is mounted. Not sda1. When I run mount /dev/sda1, it successful ly mounts onto /boot/efi automatically due to the fstab file. So why isn't it mounting on startup? Is there a fstab or grub option I can add so it does this?

---

### Post by Dennis N on 2019-07-16
What does your /etc/fstab file look like?

---

### Post by ubfan1 on 2019-07-16
The remaining boot-repair in the original post shows only an 8G install media for sda, and no other disk.  Please try the running boot-repair report again, and ensure your hard disk, whether sda or sdb, is in the output.

---

### Post by jonathan232 on 2019-07-16
Here is a picture of my fstab. I'm on vacation right now with no keyboard to type with so I'd rather do this. 
[ATTACH=CONFIG]283632[/ATTACH]

There is an error with my HP laptop where I need a wired connection for internet with the liveUSB. Is there any way I can get boot-repair on the laptop while it's in emergency mode and run it in terminal only?

---

### Post by Dennis N on 2019-07-17
There's something wrong with your attachment in post #20: It gives an error message: "Invalid Attachment specified..."

---

### Post by jonathan232 on 2019-07-21
After about four weeks of the same problem, I burned my usb with Linux Mint and installed that. With "acpi=off" and in legacy mode, it works. Unfortunately I was never able to fix the problem.

---

