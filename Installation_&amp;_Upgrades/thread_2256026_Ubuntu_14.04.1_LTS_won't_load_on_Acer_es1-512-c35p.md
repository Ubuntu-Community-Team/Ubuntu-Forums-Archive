---
title: "Ubuntu 14.04.1 LTS won't load on Acer es1-512-c35p"
date: 2014-12-09
forum: Installation &amp; Upgrades
---

### Post by dwayne2 on 2014-12-09
Good day folks,
I'm not the most technical individual, so forgive my ignorance. 
I recently purchased this laptop, it came loaded with Windows 8.1. I tried installing Ubuntu alongside Windows, I ended up accidentally replacing the OS entirely. 
Using the Windows recovery USB I made, I was able to restore my computer to factory new condition.
After researching the last few days, I figured out that I left fast boot enabled in Windows. I disabled that function, and tried the process all over again. 
Trying to install Ubuntu again and have not been successful at doing so. 
When I leave the BIOS settings in UEFI, secure boot disabled, it freezes at the Ubuntu loading screen and won't load either install or try function.
In legacy mode it will boot into the live session no problem, but won't recognize I have Windows installed.

I'm at a total loss as to how I can make this a dual boot machine, any help is greatly appreciated.

---

### Post by phil51 on 2014-12-09
Hi

I followed this guide and set up my Acer laptop to dual boot. 

[http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html)

Hope it works out for you.

---

### Post by oldfred on 2014-12-09
Some more links on similar systems.

Video on getting into UEFI - 1 Min Acer but all Windows 8
[http://www.youtube.com/watch?v=QGiG1oljjZI](http://www.youtube.com/watch?v=QGiG1oljjZI)

 How to install Ubuntu for dual-boot with Windows 8 on Acer Aspire V5-551G. Post #3
[http://ubuntuforums.org/showthread.php?t=2176273](http://ubuntuforums.org/showthread.php?t=2176273)

 Acer E3 requires UEFI password to allow added settings Post #8
[http://ubuntuforums.org/showthread.php?t=2253311](http://ubuntuforums.org/showthread.php?t=2253311)
Aspire E1-522 InsydeH20 Bios unlock -  7 min video
[https://www.youtube.com/watch?v=7SkBFkzOW0A](https://www.youtube.com/watch?v=7SkBFkzOW0A)
Acer E1-531 UEFI menus.
[http://www.tomshardware.com/forum/65627-63-body](http://www.tomshardware.com/forum/65627-63-body)
Herman's 2014_02_09 - My Adventure with Secure Boot in an Acer Aspire E1-531 Laptop
[http://members.iinet.net/~herman546/2014_02_09%20-%20My%20Adventure%20with%20Secure%20Boot%20in%20an%20Acer%20Aspire%20E1-531%20Laptop.html](http://members.iinet.net/~herman546/2014_02_09%20-%20My%20Adventure%20with%20Secure%20Boot%20in%20an%20Acer%20Aspire%20E1-531%20Laptop.html)

---

### Post by dwayne2 on 2014-12-09
Thanks for the replies guys.

Phil, that guide is really well written for the tech inept.

I'll give this another shot when I get home tonight, and report back.

Thanks again.

---

### Post by phil51 on 2014-12-09
Good luck and let us know how it goes :)

Phil

---

### Post by dwayne2 on 2014-12-10
I have a question regarding labeling the partitions in gparted. 
Do you just label them root, swap, and home using the label function? 
I know when running the installer you can just use that partition tool to create and label partitions as you go, but I stumbled on that when trying to set the three up in gparted.
Sorry if this is a dumb question lol

---

### Post by oldfred on 2014-12-10
I try to label partitions, but the labels are not used for much except the partitions that are not automounted like /, /home & swap. If not automounted then the auto mount will use the labels. 
Since I do multiple installs I label each root with what version it is, so whatever system I am in, I can tell where the other installs are in case I want to find something in them.

When I forget to assign a label in gparted when creating a partition, or change one, I may use Disks or Disk Utility to add label.

This is my new system, so do not have many other installs yet, but have several other partitions.

```
fred@trusy-ar:~$ sudo blkid -c /dev/null -o list
[sudo] password for fred: 
device     fs_type label    mount point    UUID
-------------------------------------------------------------------------------
/dev/sda1  vfat    EFI      /boot/efi      FD76-E33D
/dev/sda3  ext4    trusty   /              45de38c8-6748-4634-b207-628d9aa8b42b
/dev/sda4  swap             <swap>         7f429d54-b2e9-417a-ab13-b93af50f5159
/dev/sda5  ext4    iso_ssd  (not mounted)  695d18b5-16f8-4e9c-bf66-675a12da5a26
/dev/sdb1  vfat    efi      (not mounted)  68CD-3368
/dev/sdb3  ext4    myth     (not mounted)  8e9b2ec7-56d7-4691-8fcd-bec142445d90
/dev/sdb4  ext4    data     /mnt/data      a0c1c99f-0f09-4787-a7cc-9e15bb3b4aa5
/dev/sdb5  ext4    backup   /mnt/backup    084de40f-8ffd-4af1-97b1-8a60cdd9aab4
/dev/sdb6  ext4    iso_hdd  (not mounted)  7f360ddc-d9fb-4a40-b17a-f2d5af6b61ed
/dev/sdb7  ext4    homerun  (not mounted)  4daeb8c4-01b1-41bd-8773-8ba16566793b
/dev/sdc1  vfat             /media/fred/F9C6-C317 F9C6-C317

```

---

### Post by dwayne2 on 2014-12-11
Thanks for clearing that up Fred.

Well I'm gonna give this one more shot and then I think I'll probably just give up if it doesn't work. This has been a very, very frustrating experience.

So after resetting my computer yet again, I've prepared it to install Ubuntu after removing my recovery partition and all that. And it won't boot using the USB, it just hangs at the Ubuntu loading screen. 
I've tried turning off secure boot but it made no difference, it still hangs at the same screen.
I'm currently downloading a fresh copy of Ubuntu, and will make a new bootable USB.

I really wanted this to be a dual boot system but I'm soo close to just giving up.

---

