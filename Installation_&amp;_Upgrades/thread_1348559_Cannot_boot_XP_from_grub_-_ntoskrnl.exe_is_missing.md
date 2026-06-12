---
title: "Cannot boot XP from grub - ntoskrnl.exe is missing"
date: 2009-12-07
forum: Installation &amp; Upgrades
---

### Post by brexsis on 2009-12-07
i upgraded from kubuntu 9.04 to 9.10, but things were weird and i installed fresh kubuntu 9.10.
but now i have problem that i cant boot WinXP, it says: "<Windows root>\ system32\ntoskrnl.exe is missing or corrupt."
i tried copy that file from CD, but no changes. only if i restore windows MBR, then i can get to boot windows, so Windows is all right, but grub or something is crashing my WinXP.
i have 2HDD`s
HDD1 = WinXP
HDD2 = kubuntu root/boot/home partitions, and 1 ntfs partition

if i set HDD1 as primary boot HDD, then i can boot into WinXP,
if i set HDD2 as primary boot HDD, then i can boot into Kubuntu, but i **cant **boot into Windows (it shows OS list of WinXp and Kubuntu (Wubi)) and shows me this error:
**"<Windows root>\ system32\ntoskrnl.exe is missing or corrupt."**
(i have 2 kubuntus, 1 is Wubi, other is genuine fresh install on second HDD.)

anyone can help me with this?

---

### Post by dstew on 2009-12-07
That message is generated from the Windows boot system. If Windows boots fine when HDD1 is set as the primary boot disk, perhaps the Windows boot loader is unable to function properly with the Windows disk as the second hard drive. Maybe you should re-install grub into the MBR of the Windows disk. Then Windows should be happy. Another thought is to use the grub map statement (if you are using grub 0.97). That can fool the Windows boot loader into thinking it is disk no. 1, and improve performance. See [this thread]("http://www.linuxforums.org/forum/installation/36888-grub-wont-boot-windows-xp.html") for an example. I don't know how to do the same thing with grub 1.97 though.

---

### Post by brexsis on 2009-12-07
> **dstew said:**
> That message is generated from the Windows boot system. If Windows boots fine when HDD1 is set as the primary boot disk, perhaps the Windows boot loader is unable to function properly with the Windows disk as the second hard drive. Maybe you should re-install grub into the MBR of the Windows disk. Then Windows should be happy. Another thought is to use the grub map statement (if you are using grub 0.97). That can fool the Windows boot loader into thinking it is disk no. 1, and improve performance. See [this thread]("http://www.linuxforums.org/forum/installation/36888-grub-wont-boot-windows-xp.html") for an example. I don't know how to do the same thing with grub 1.97 though.
when i still had kubuntu 9.04 and HDD2 as primary HDD, then all worked well. it "broke" when i upgraded to 9.10 and even when i 2 times reinstalled kubuntu 9.10 (including boot partitions formatting) it wont work. grub2 doesnt like here something  :(

---

### Post by darkod on 2009-12-07
First I would get rid of wubi unless you really need it. Wubi is just to try ubuntu and since you already have it installed as dual boot too, no really point in wubi. On the other hand, wubi + windows can make some problems with the windows bootloader which is where your problem is.
You said yourself, grub2 has no problem booting your kubuntu.
If you decide to get rid of wubi, don't forget you need to do it with add/remove programs. After that, repair the XP boot process (just in case), boot your Kubuntu and do the update-grub command. It should locate the repaired XP and boot it fine from the menu.
In this setup kubuntu+wubi+XP there are simply too many unknows. Windows and linux put together.

---

### Post by brexsis on 2009-12-07
> **darkod said:**
> First I would get rid of wubi unless you really need it. Wubi is just to try ubuntu and since you already have it installed as dual boot too, no really point in wubi. On the other hand, wubi + windows can make some problems with the windows bootloader which is where your problem is.
You said yourself, grub2 has no problem booting your kubuntu.
If you decide to get rid of wubi, don't forget you need to do it with add/remove programs. After that, repair the XP boot process (just in case), boot your Kubuntu and do the update-grub command. It should locate the repaired XP and boot it fine from the menu.
In this setup kubuntu+wubi+XP there are simply too many unknows. Windows and linux put together.
this is how i did:
* i had WinXp and Kubuntu.
* then i upgraded Kubuntu.
* then i reinstalled Kubuntu, tried WinXp but it didnt boot.
* i installed Wubi, to check out how really it works.
* i did fixmbr from windows CD.
* a new kubuntu reinstall with formated /boot partition.
still cant get to boot XP through grub2.
but i will try to uninstall wubi and do a fixboot and then fixmbr. :)

---

### Post by brexsis on 2009-12-09
still i cant get to boot windows through grub2...

---

### Post by darkod on 2009-12-09
> **brexsis said:**
> this is how i did:
* i had WinXp and Kubuntu.
* then i upgraded Kubuntu.
* then i reinstalled Kubuntu, tried WinXp but it didnt boot.
* i installed Wubi, to check out how really it works.
* i did fixmbr from windows CD.
* a new kubuntu reinstall with formated /boot partition.
still cant get to boot XP through grub2.
but i will try to uninstall wubi and do a fixboot and then fixmbr. :)

You're doing too much. Settle for one choice and try to solve a problem if it happens. Don't reinstall immediately. At this point I can't even follow you what your hdd looks like.
Post the results of
sudo fdisk -l

or a screenshot of Gparted.

---

