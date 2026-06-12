---
title: "Serious Grub Problem - landing on promt instead of menu"
date: 2014-04-25
forum: Installation &amp; Upgrades
---

### Post by schwarzie2 on 2014-04-25
Hello eveyone.

i just installed Mint 16 on my Thinkpad T61 as a paralell installation to Windows 7.

I have a SSD as my primary harddisk and then sometimes a 320gb Disk in my Ultrabay as a secondary drive. Like right now.

After installing and rebooting i found out that my thinkpad still was booting straight to windows. After much experimenting i just tried booting from my seondary drive. and Tada, i go the Grub Bootmenu.
Linux has my drives in the wrong order. The Ultrabay is the secondary drive (both Windows and the Bios confirm this) and the SSD my primary. But the primary drive is named sbb and the secondary, temporary is sda. that this is not an acceptable solution should be clear, i want to use both system whenever i want, not only when i have the right drive in my ultrabay.

So after some google fu i installed Grub to try out some commands i found. since ghe "sudo grub" command told me that it is not installed i corrected that with synaptics. Afterwards starting it send me to a grub promt with out any meaningful help. Back to square one. After a little more google fu i found the Grub Customizer. installed it and it gave me the option to install Grub on the primary mbr.

After doing that and rebooting windows wasnt loaded, but instead i lande on that grub promt...

So right now i have the option to choose between the grub promt which does nothing for me, or using my temporary drive to boot from and then choose either operating system.

My Questions now:

How can i fix my grub issues on the primary disk?
How can i purge the rub menu and everything the linux install did to the secondary drive?
can i change linux wrong perception what is the primary and what is the secondary drive? without having to manipulate a million configfiles by hand? :D I fear this issue will bite me in the future so i would like to see it solved.

And totally unrelated to this issue:
How can i automount drives? so far i have to open my windows partitions at least once so they are properly mounted which is an issue since i use the same firefox profile under windows and under linux. Same for Miranda IM. Is simply inconvinient.

best regards
Schwarzie

---

### Post by Double.J on 2014-04-25
Hi there!

A warm welcome to the forums. 

The short answer is to boot into ubuntu, open a terminal with ctrl+alt+t and paste in 
```
sudo grub-install /dev/sdb
sudo update-grub
```This will make sure that ubuntu's grub is in the windows mbr and that it is pointing to ubuntu's /boot directory.

As for the disk order; I think there may be a slight confusion. Because you are using two different hard drives, there isn't actually any 'order'. There are just two drives. Any operating system will think it is the center of the universe and list all other drives after it's own because it boots it's drive first. The boot order is something else. Obviously two hard drives can't boot at the same time, so the bios has to know where to boot.

In the first instance, grub installed correctly to it's own mbr (dev/sda - your platter drive) but your bios was still trying to boot the ssd, so looked there first and found windows bootloader and started windows. 

Windows tells you you it's the primary drive (C:) because just like ubuntu it looks on it's own disk first. Personally I would have changed the boot order in the bios to boot the platter drive first and then let ubuntu boot the windows disk rather than write over the mbr on the windows disk - than way when if you remove ubuntu, you would have just needed to set bios back to the ssd and windows would have booted as was.

as your system currently is, the options are to either install ubuntu to the windows disk as I mentioned above, or use the windows disk to repair the ssd mbr and set the boot order in bios to the platter drive.

Jj

---

### Post by Double.J on 2014-04-25
Additionally With regards to auto mounting, there is a file in /etc/fstab that handles which drives are auto mounted at boot and where they mount to.

I will add that it is generally not recommended to auto mount the windows C: drive, but non system partitions are fine.

For example to add an ntfs partition to auto mount, first find it's UUID with
```
blkid
```Copy the uuid for the right partition  (it'll look something like 395d83-28j64-2sl7b94)

Create a folder for the partition to mount at, usually in /media:
```
sudo mkdir /media/data
```

The backup and open the fstab with
```
sudo cp /etc/fstab /etc/fstab.orig &&a sudo nano /etc/fstab
```

The line for an ntfs partition would look like:
```
UUID=395d83-28j64-2sl7b94    /media/data    ntfs    defaults    0    0
```This tells ubuntu to mount the partition at /media/data every time it boots and to give all users access to read/write.

Please note that this is an example. The fstab file is very powerful with a lot of commands. Please read [this]("https://help.ubuntu.com/community/Fstab") guide. For first time use I'd also recommend sharing the changes you make with us before you reboot just to make sure everything will go okay.

Jj

---

### Post by schwarzie2 on 2014-04-25
Hi there and thanks for your answer. I currently run the ubtuntu Boot-repair that completely purged grup and is now reinstalling it. Hopefully this helps.

Regarding the fstab and automount: The C: Drive was one of the drives i intended to automount since i share my firefox profile from there. why exactly is that a bad idea?

As the mountpoint i woul like to use the default ones that get used when i just double click the drive so it gets mounted. currently i have to do that to a) use firefox due to the shared profile and b) for another drive to connect into the wlan since the zertificates needed for this wlan are on that drive.

---

### Post by schwarzie2 on 2014-04-25
> **Double.J said:**
> Hi there!

As for the disk order; I think there may be a slight confusion. Because you are using two different hard drives, there isn't actually any 'order'. There are just two drives. Any operating system will think it is the center of the universe and list all other drives after it's own because it boots it's drive first. The boot order is something else. Obviously two hard drives can't boot at the same time, so the bios has to know where to boot.
exactly. and my SSD is the permanently installed drive and also the drive which has windows and Linux installed on it. The other drive is just a datagrave.

> 
In the first instance, grub installed correctly to it's own mbr (dev/sda - your platter drive) but your bios was still trying to boot the ssd, so looked there first and found windows bootloader and started windows. 
Well i never installed anything on the platter drive. both linux and windows are on the SSD. I have no idea why linux saw it as the primary drive. the platter drive gets changed sometimes, i have two more for the ultrabay slot and a dvd drive. so using the plater drive for anything os related is a bad idea ;)I

It looks like the ubuntu boot repair oiption was successful, i will reboot now and hope the best ;)

---

### Post by Double.J on 2014-04-25
HI there,

two reasons mainly - the first is that when a partition is mounted, it becomes part of the OS that mounted it - allowing all changes and modifications. Because windows and ubuntu hide their files in different ways, ubuntu will see all hidden and system files for windows as if they are normal files. This vastly increases the chances of accidentally modifying them.

The second reason is hibernation. If windows is hibernated and then you mount it in ubuntu, you can A) risk damaging the hibernated state, and B) any changes you make to the C: drive will be forgotten by windows when you awake.

it is generally recommended to shrink C, create D: in ntfs and use this as a shared data partition between the two

Jj

---

### Post by schwarzie2 on 2014-04-25
Well i dont use hibernate, so that wont be an issue. For the rest, i didnt intend to create another partition just for my firefox profile, the reason that i accidentially delete file is a risk im willing to take ;) As a overall shared data partition i have the external drives in the ultrabay slot. so its just for the profile.

Interestingly with "Laufwerke" (Diskmanager in english?) i see that both drives are marked for "atomatisches einhängen" (automount) but still i have to click them to initialize them.

Is there an alternative to manipulating the fstab file? It doesnt look that noobiefriendly ;)

---

### Post by Double.J on 2014-04-26
Hi there, I looked I to it for you and it looks like pysdm, (storage device manager) might be the way to go (after 12 years of linux I must confess I just didn't think to look for a gui tool) I would advise however that you still back up your fstab file before making any changes! ;)

---

