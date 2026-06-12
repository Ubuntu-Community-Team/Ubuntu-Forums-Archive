---
title: "Install Ubuntu 12.04"
date: 2012-06-18
forum: Installation &amp; Upgrades
---

### Post by mr.suchy on 2012-06-18
Hi everyone!

Yesterday I want install new Ubuntu 12.04 from USB because I don't have any DVD-rom in PC/Home. I 

always write new Ubuntu on usb and install. Unfortunately I have problem with it. When I enter personal infromation like login, password I clikc "NEXT" then I see only cursor nothing else. What can I do with this problem ? Sorry for my langauge.


--edit
I burn a cd with ubuntu and run install. I have the same error, check this screen. Of course everything in this screen is OK.

[http://imageshack.us/photo/my-images/834/sam3926h.jpg/](http://imageshack.us/photo/my-images/834/sam3926h.jpg/)

---

### Post by sudodus on 2012-06-19
I'm not sure from your screendump. Are there already four primary partitions when you start installing Ubuntu? In that case yes.

There might also be a problem due to problems to detect your hardware. In that case, you might need to enter some boot option, for example ***nomodeset***. See this link
[[COLOR="Red"]_https://help.ubuntu.com/community/BootOptions_[/COLOR]]("https://help.ubuntu.com/community/BootOptions")

Did you try to run Ubuntu live 'test Ubuntu' from the CD drive before installing it? If you did not, please do it now, because it will give us valuable information without tampering with your hard drive.

If you get it running live, please run the following command and post the output text in a reply.
```
sudo fdisk -lu
```
Put the output text between CODE tags: Mark it and click on the # icon at the top of the editing window.

---

### Post by mr.suchy on 2012-06-19
Yeah U right I have four primary partition. Of course I run Ubuntu Live and everyting looks good. When I back home I try run install with nomodeset like U say. Tell me much more about nomodeset what this mean ? I try create one primary partition and few logical partition maybe this is source od my problem with Ubuntu 12.04. One again sorry for my english and thanks for help dude.

Best regards!

---

### Post by sudodus on 2012-06-19
nomodeset:

This option is running the graphics in a basic mode during the boot process. There are other boot options for other typical problems with some hardware (when automatic recognition fails). But you run Ubuntu live and it looks good, so I doubt that is the problem.

list partitions:

When booted into a live session, please run the following command and post the output text in a reply.
```
sudo fdisk -lu
```

if 4 primary partitions for Windows:

Unfortunately, that makes it impossible for Ubuntu to add its partitions (a root partition and a swap partition).

But you can do something, if you are prepared to edit your partition table. You must delete one partition and shrink one partition, so that you can create an extended partition, and in that extended partition you (or the Ubuntu installer) can make the partitions necessary.

Editing partitions is risky, so if you decide to do it, you should ***backup*** your whole hard drive for example with Clonezilla, or at least backup your private files (documents, pictures, ...) and make a recovery disk for Windows.

---

### Post by mr.suchy on 2012-06-19
OK. SO when I back home I format my hard drive and then I create one partition for windows (primary) and few logical for Ubuntu like You said. I have my hard drive in image so I can restore all partition in few minutes with clonzilla :D I replay later when I check this with logical partition. Thanks again.

---

### Post by sudodus on 2012-06-19
I guess from your signature, that you are an IT pro, so editing the partition table should not be too difficult. And you probably know already, if there is one particular partition that you can simply wipe (and maybe move its content somewhere else before wiping it).

I guess from the picture of a monitor screen, that you have a desktop or tower computer. Another possibility is to get a second internal drive and install Ubuntu and grub to that second drive, while Windows can remain with its four partitions on the first drive.

*Edit: I use gparted run from a live session booted from the Ubuntu CD/USB drive to edit partitions.*

---

### Post by mr.suchy on 2012-06-20
Yesterday I did a few tests. First I create a main partition (primary) with few logical and run install Ubuntu. Secondly I run install Ubuntu a check that install create partition automatic and he took all disk. 

Wahtever I set, check the command "Sudo fdisk -lu" return smimilary results.

```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000584b9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048   151060479    75529216   83  Linux
/dev/sda2       151062526   156301311     2619393    5  Extended
/dev/sda5       151062528   156301311     2619392   82  Linux swap / Solaris

Disk /dev/sdb: 4011 MB, 4011491328 bytes
124 heads, 62 sectors/track, 1019 cylinders, total 7834944 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x20ac7dda

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   ?  3224498923  3657370039   216435558+   7  HPFS/NTFS/exFAT
/dev/sdb2   ?  3272020941   930513678   976730017   16  Hidden FAT16
/dev/sdb3   ?           0           0           0   6f  Unknown
/dev/sdb4        50200576   974536369   462167897    0  Empty

Partition table entries are not in disk order


```I don't understand this

```
This doesn't look like a partition table
Probably you selected the wrong device.
```I run install with atribut ```
no modeset
``` but without success.

--edit

```
Disk /dev/sdb: 4011 MB
```

this is a probably a usb with linux install so this error not applicable my problem with install I guess.

---

### Post by YannBuntu on 2012-06-20
> **mr.suchy said:**
> Hi everyone!

Yesterday I want install new Ubuntu 12.04 from USB because I don't have any DVD-rom in PC/Home. I 

always write new Ubuntu on usb and install. Unfortunately I have problem with it. When I enter personal infromation like login, password I clikc "NEXT" then I see only cursor nothing else. What can I do with this problem ? Sorry for my langauge.


--edit
I burn a cd with ubuntu and run install. I have the same error, check this screen. Of course everything in this screen is OK.

[http://imageshack.us/photo/my-images/834/sam3926h.jpg/](http://imageshack.us/photo/my-images/834/sam3926h.jpg/)

- The option suggested by sudodus is "nomodeset", not "no modeset".
- Anywyay: as you can boot your USB session without kernel option, I think you don't need it neither on the installed system.
- you don't have 2 primary partitions on sda, but 2 (1 primary + 1 extended), so you can still add 2 primary.

Please try to install [11.10]("http://releases.ubuntu.com/11.10/") and tell us if you have the same problem or not.

---

### Post by WasMeHere on 2012-06-21
> **mr.suchy said:**
> 
```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000584b9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048   151060479    75529216   83  Linux
/dev/sda2       151062526   156301311     2619393    5  Extended
/dev/sda5       151062528   156301311     2619392   82  Linux swap / Solaris

```

+1 to *Yannbuntu*'s suggestions

Furthermore, since you have no Windows or other file system to preserve it ***should*** be easy to install

- Ubuntu with Unity or Gnome 3
or some other flavour,
- Kubuntu with KDE fancy but as demanding as 'vanilla' Ubuntu
- Lubuntu with LXDE ultra-light desktop environment
- Xubuntu with XFCE light desktop environment.

Maybe you will be happy with Ubuntu 11.10. Otherwise we need to find out why it didn't work for you, and it would help if you post your specifications, at least CPU, RAM and graphics card.

---

### Post by mr.suchy on 2012-06-21
Hi,

Thanks one again for help and patience. I start from end my story. I finally install Ubuntu 12.04. I Firstly I install ubuntu 11.10 and then I upgrade to 12.04 and that is it. Right now I must optimize a gnome shell for my PC. Only information about my PC is in my signature. 

```

Disk /dev/sda: 80.0 GB, 80026361856 bytes
g&#322;owic: 255, sektorów/&#347;cie&#380;k&#281;: 63, cylindrów: 9729, w sumie sektorów: 156301488
Jednostka = sektorów, czyli 1 * 512 = 512 bajtów
Rozmiar sektora (logiczny/fizyczny) w bajtach: 512 / 512
Rozmiar we/wy (minimalny/optymalny) w bajtach: 512 / 512
Identyfikator dysku: 0x00072c1a

Urz&#261;dzenie Rozruch   Pocz&#261;tek      Koniec   Bloków   ID  System
/dev/sda1   *    43806720    85207039    20700160   83  Linux
/dev/sda2       151062526   156301311     2619393    5  Rozszerzona
/dev/sda3            2048    43806719    21902336    7  HPFS/NTFS/exFAT
/dev/sda4        85207040   151060479    32926720   83  Linux
/dev/sda5       151062528   156301311     2619392   82  Linux swap / Solaris

```

Please say what can I check, write to help another people with similar problem like me.

---

### Post by WasMeHere on 2012-06-21
> **mr.suchy said:**
> Hi,

Thanks one again for help and patience. I start from end my story. I finally install Ubuntu 12.04. I Firstly I install ubuntu 11.10 and then I upgrade to 12.04 and that is it. Right now I must optimize a gnome shell for my PC. Only information about my PC is in my signature. 

```

Disk /dev/sda: 80.0 GB, 80026361856 bytes
g&#322;owic: 255, sektorów/&#347;cie&#380;k&#281;: 63, cylindrów: 9729, w sumie sektorów: 156301488
Jednostka = sektorów, czyli 1 * 512 = 512 bajtów
Rozmiar sektora (logiczny/fizyczny) w bajtach: 512 / 512
Rozmiar we/wy (minimalny/optymalny) w bajtach: 512 / 512
Identyfikator dysku: 0x00072c1a

Urz&#261;dzenie Rozruch   Pocz&#261;tek      Koniec   Bloków   ID  System
/dev/sda1   *    43806720    85207039    20700160   83  Linux
/dev/sda2       151062526   156301311     2619393    5  Rozszerzona
/dev/sda3            2048    43806719    21902336    7  HPFS/NTFS/exFAT
/dev/sda4        85207040   151060479    32926720   83  Linux
/dev/sda5       151062528   156301311     2619392   82  Linux swap / Solaris

```

Please say what can I check, write to help another people with similar problem like me.
Sorry, I did not notice the specs in your signature! Anyway I'm happy it works for you now. I see you have two linux partitions. Are both working installations? Or should you actually wipe one of them?

Is your system fast and responsive enough, then I think everything is OK. Otherwise try Lubuntu or Xubuntu live (booted from CD/USB) to taste that flavour.

*Edit: And when you feel like it, please click on ***Thread Tools*** and mark this thread as SOLVED*

---

### Post by mr.suchy on 2012-06-21
> **Olle Wiklund said:**
> I see you have two linux partitions. Are both working installations? Or should you actually wipe one of them?


I don't understand. Could you use another words ? :-)

---

### Post by WasMeHere on 2012-06-21
> > **mr.suchy said:**
> Hi,

Thanks one again for help and patience. I start from end my story. I finally install Ubuntu 12.04. I Firstly I install ubuntu 11.10 and then I upgrade to 12.04 and that is it. Right now I must optimize a gnome shell for my PC. Only information about my PC is in my signature. 

```

Disk /dev/sda: 80.0 GB, 80026361856 bytes
g&#322;owic: 255, sektorów/&#347;cie&#380;k&#281;: 63, cylindrów: 9729, w sumie sektorów: 156301488
Jednostka = sektorów, czyli 1 * 512 = 512 bajtów
Rozmiar sektora (logiczny/fizyczny) w bajtach: 512 / 512
Rozmiar we/wy (minimalny/optymalny) w bajtach: 512 / 512
Identyfikator dysku: 0x00072c1a

Urz&#261;dzenie Rozruch   Pocz&#261;tek      Koniec   Bloków   ID  System
/dev/sda1   *    43806720    85207039    20700160   83  Linux
/dev/sda2       151062526   156301311     2619393    5  Rozszerzona
/dev/sda3            2048    43806719    21902336    7  HPFS/NTFS/exFAT
/dev/sda4        85207040   151060479    32926720   83  Linux
/dev/sda5       151062528   156301311     2619392   82  Linux swap / Solaris

```

Please say what can I check, write to help another people with similar problem like me.
Sorry, I did not notice the specs in your signature! Anyway I'm happy it works for you now. [COLOR="Red"]I see you have two linux partitions. Are both working installations? Or should you actually wipe one of them?
[/COLOR]
Is your system fast and responsive enough, then I think everything is OK. Otherwise try Lubuntu or Xubuntu live (booted from CD/USB) to taste that flavour.

*Edit: And when you feel like it, please click on ***Thread Tools*** and mark this thread as SOLVED*

> **mr.suchy said:**
> I don't understand. Could you use another words ? :-)
I see that you have two linux partitions: [FONT="Courier New"]/dev/sda1[/FONT] and [FONT="Courier New"]/dev/sda4[/FONT]. What are these partitions? Two separate linux installations, or two partitions that are part of the same installation, typically a root partition (/) and a home partition (/home)? Probably you know, otherwise please post the output of the command ```
df
``` when running an (or the) installed system.

I was thinking that maybe you had installed 11.10 *and* 12.04, or that you left your first system (the incomplete 12.04) and then installed 11.10. In that case either [FONT="Courier New"]/dev/sda1[/FONT] or [FONT="Courier New"]/dev/sda4[/FONT] should be wiped (deleted) and the free space could be used as a data partition or to test some other Ubuntu flavour or linux distro.

---

### Post by haresear on 2012-06-21
If your install still hangs after you enter your personal information, you might be experiencing the "slide show crash" that many people with AMD cpu's have run into. If so, I would suggest you boot to the live CD desktop and remove (uninstall) the 'ubiquity-slide-show' package before starting the install. There is a long thread in this forum on this problem. See post #91 in this thread:
[http://ubuntuforums.org/showthread.php?t=1965802&highlight=ubiquity+slide+show+crash&page=10]("http://ubuntuforums.org/showthread.php?t=1965802&highlight=ubiquity+slide+show+crash&page=10")

---

### Post by mr.suchy on 2012-06-22
```

root@ubuntu-desktop:/home/mrsuchy/Pobrane# df
System plików              1K-bl     u&#380;yte  dost&#281;pne %u&#380;. zamont. na
/dev/sda1               20635692   4723964  14876724  25% /
udev                     1282748         4   1282744   1% /dev
tmpfs                     516000       840    515160   1% /run
none                        5120         0      5120   0% /run/lock
none                     1290000       992   1289008   1% /run/shm
/dev/sda4               32846676  16679628  14520712  54% /home
/dev/sdb1              245166940 205578752  39588188  84% /media/Toshiba USB-HDD 1
/dev/sdb3               16048932    981484  15067448   7% /media/Toshiba USB-HDD 3
/dev/sdb2              227167128 126339548 100827580  56% /media/Toshiba USB-HDD 2
/dev/mapper/truecrypt1   2092792   1228756    864036  59% /media/truecrypt1
/dev/mapper/truecrypt2  10465048   4175388   6289660  40% /media/truecrypt2
root@ubuntu-desktop:/home/mrsuchy/Pobrane# 

```
I have two partition ( / an/home). 

@haresear your hear sound good but I don't test it right now. Maybe tomorrow I clone my disk and check this tip.

---

### Post by sudodus on 2012-06-23
Hi again mr.suchy,

How is your computer running now? Is the installed system working? Is there still something that you want to improve, that we might help you do?

---

### Post by mr.suchy on 2012-06-23
Hi,

Some time I have crash when I use a calc or something like this. Don't know how to start ndiswrapper automatic. I set everything like in official doc but it doesn't work.

---

### Post by sudodus on 2012-06-23
> **mr.suchy said:**
> Hi,

Some time I have crash when I use a calc or something like this. Don't know how to start ndiswrapper automatic. I set everything like in official doc but it doesn't work.

You are not supposed to get crashes running calc. But if it was a single event ...

Sometimes ndiswrapper works well, sometimes not so well, sometimes not at all. Check how your wifi chip/card/stick is reported to work with linux in

[[COLOR="Red"]_https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported_[/COLOR]]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported")

or some other link in the internet.

---

### Post by mr.suchy on 2012-06-23
Thanks. I just wonder about joining to group that report bugs in Ubuntu :-)

I can't find it:
```
01:09.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)
    Subsystem: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 19
    Memory at eb000000 (32-bit, non-prefetchable) [size=64K]
    Memory at eb010000 (32-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: ndiswrapper

```

---

### Post by sudodus on 2012-06-23
> **mr.suchy said:**
> Thanks. I just wonder about joining to group that report bugs in Ubuntu :-)

That's a good idea. I was beta testing Lubuntu 12.04 and I learned a lot.

The more people that report bugs, the better :KS

---

### Post by KegHead on 2012-06-23
Hi!

Olle Wiklund?

I'm Jim Wicklund

---

### Post by WasMeHere on 2012-06-23
> **KegHead said:**
> Hi!

Olle Wiklund?

I'm Jim Wicklund

Hi Jim,

Maybe we are distant relatives :-)

Olle

---

### Post by KegHead on 2012-06-24
Hi!

Maybe!

My Grandfather was born in Stockholm in 1896?

Migrated to Norway, Michigan and became a US citizen.

Happy Ubunting!

KegHead

---

### Post by WasMeHere on 2012-06-24
Let us talk more via [Ubuntu Forum] Private Messages :-)

I sent one to you. Can you find it?

---

