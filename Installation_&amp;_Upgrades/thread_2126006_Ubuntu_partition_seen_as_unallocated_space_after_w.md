---
title: "Ubuntu partition seen as unallocated space after windows 8 upgrade"
date: 2013-03-15
forum: Installation &amp; Upgrades
---

### Post by Shaileshpatel on 2013-03-15
[COLOR=#333333][FONT=Ubuntu]Hello,
[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]I have installed Ubuntu 12.04 with Windows 7 as dual-boot. Today I decided to upgrade windows 7 to windows 8 on the other partition. I read on some forums that I would most likely need a liveUSB to repair grub after upgrading windows, so I could boot into Ubuntu again. After installing windows, I used the live-cd to repair Boot-manager using the program "boot-repair".
[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]URL: [http://paste.ubuntu.com/5609860/](http://paste.ubuntu.com/5609860/)[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]
However I still cannot get access to ubuntu and furthermore, according to gparted, the partition with ubuntu 12.04 is seen as unallocated space (!). Did I do something wrong, did I somehow remove Ubuntu? Since I have not done any data back up before Windows upgrade, I want to access to ubuntu, without having to re-install it. Could someone look at my url of boot-repair, and give me suggestions what I could do?[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]
PS: I have used testdisk program, but it fails to recognize actual size of Ubunut partition and thus I didn't proceed.[/FONT][/COLOR]

---

### Post by Bashing-om on 2013-03-15
Shaileshpatel; Hi !

From what little I could determine you must have had what is termed a "wubi" install. Ubuntu running inside of windows. Not a true dual boot // As such I bet ubuntu is long gone with the upgrade from Window's 7 to 8.

Others with "wubi" and Windows experience can advise better. -> but presently there "ain't no" partitions for ubuntu.
[INDENT=2]
There is a bit of work to be done

[/INDENT]

---

### Post by oldfred on 2013-03-15
I do not think it is wubi as you do have an extended partition with some unallocated space from start of extended to the swap. Or that space was probably the / (root) partition.

Did you try testdisk deeper search. I would think it should see the missing partition.

There also are ways to just force in a new partition with parted but I think that is not a lot different than what testdisk does. If you had any backups that showed partition table before, sfdisk output, Boot-Repair output or backup then it would be relatively easy to create a new partition.

Do this first:
       Backup partition table to text file & save to external device.
sudo sfdisk -d /dev/sda > PTsda.txt


 Use parted rescue to restore missing partition details in post #22
[http://ubuntuforums.org/showthread.php?t=1775331](http://ubuntuforums.org/showthread.php?t=1775331)

---

### Post by Bashing-om on 2013-03-15
oldfred, again I stand in need of education:
Is not the first line "/dev loop0    squashfs" from OP's boot info script in reference to how wibi loads (or is this just from a liveCD ??)
> :

"blkid" output: ________________________________________________________________  Device           UUID                                   TYPE       LABEL  /dev/loop0                                              squashfs    /dev/sda1        4488EF0188EEEFFA                       ntfs        /dev/sda2        06F22AEFF22AE2A3                       ntfs        /dev/sda4        B6F0FCF3F0FCBAA7                       ntfs       LENOVO_PART /dev/sda5        8e564dae-7920-43fd-9cf8-6763de978605   swap        /dev/sdb1        E8E3-B2A4                              vfat       PENDRIVE


---

### Post by bcbc on 2013-03-16
> **Bashing-om said:**
> oldfred, again I stand in need of education:
Is not the first line "/dev loop0    squashfs" from OP's boot info script in reference to how wibi loads (or is this just from a liveCD ??)

Refer to [http://en.wikipedia.org/wiki/SquashFS](http://en.wikipedia.org/wiki/SquashFS)
> [COLOR=#000000][FONT=sans-serif]SquashFS is used by the [/FONT][/COLOR][Live CD]("http://en.wikipedia.org/wiki/Live_CD")[COLOR=#000000][FONT=sans-serif] versions of [/FONT][/COLOR][Arch Linux]("http://en.wikipedia.org/wiki/Arch_Linux")[COLOR=#000000][FONT=sans-serif], [/FONT][/COLOR][Debian]("http://en.wikipedia.org/wiki/Debian")[COLOR=#000000][FONT=sans-serif], [/FONT][/COLOR][Fedora]("http://en.wikipedia.org/wiki/Fedora_(operating_system)")[COLOR=#000000][FONT=sans-serif], [/FONT][/COLOR][Gentoo Linux]("http://en.wikipedia.org/wiki/Gentoo_Linux")[COLOR=#000000][FONT=sans-serif], [/FONT][/COLOR][Salix]("http://en.wikipedia.org/wiki/Salix_OS")[COLOR=#000000][FONT=sans-serif], [/FONT][/COLOR][Ubuntu]("http://en.wikipedia.org/wiki/Ubuntu_(operating_system)")

In this case it's the live USB running off the PENDRIVE

---

### Post by oldfred on 2013-03-16
I look for a wubi file or root.disk and only NTFS partitions. Then I am pretty sure bcbc will know more about it.

But when there is a separate swap partition it had to have a full install and then the extended partition looks like it has a gap or space that was probably a / (root) partition.

I am surprised testdisk does not see the old partition. With one or two cases users have just recreated a partition with parted rescue (not new formatted partition) and recovered the system. But really best to know partition sizes by sector. (I run bootinfoscript as part of my rsync backup just to have that documentation).

---

### Post by Bashing-om on 2013-03-16
Thanks guys, able to exercise greater care next time !

---

