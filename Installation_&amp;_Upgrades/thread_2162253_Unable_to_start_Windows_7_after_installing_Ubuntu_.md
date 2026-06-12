---
title: "Unable to start Windows 7 after installing Ubuntu 12.04 LTS"
date: 2013-07-13
forum: Installation &amp; Upgrades
---

### Post by ali8 on 2013-07-13
I hate starting new thread about a problem already encountered by others. But I tried the solutions and did not work:

1) sudo grub-update  ==> Did NOT work
2) Boot Repair (Recommended settings) ==> Did NOT work
3) Boot Repair (Advanced Settings - "repair windows boot files") ==> option disabled ==> Did NOT work
4) Windows 7 repair ==> Did NOT work

I have a windows 7 Ultimate x64 plus Ubuntu 12.04 LTS, both on partition C. Partition D is for my files, Partition E is also for my files but encrypted with
 BitLocker (I have the recovery key and know the password). All partitions are NTFS.

_**THE PROBLEM**_: after booting, 4 options appear: Ubuntu, Ubuntu Recovery Mode, Memory Test, Windows 7. Selecting windows 7 brings a black screen
 for 2 seconds then I get back to grub menu.

What options do I have other than formatting C again and installing Windows...?

here's my boot-repair log: [http://paste.ubuntu.com/5872398/](http://paste.ubuntu.com/5872398/)

-------------------------------------------------------------------------------------------------------------------------------------------------------------

I want to try "restore MBR" in boot-repair, it is a good idea?

---

### Post by ali8 on 2013-07-13
I tried following one thread which said that drive C must be active befor windows can repair, so i made it active but now grub2 does not appear and i get ""no such partition". i  am now using my mobile to respond.

---

### Post by ali8 on 2013-07-13
I finally formatted C and re-installed Windows 7.

Any ideas what was wrong?

---

### Post by oldfred on 2013-07-14
Your BootInfo report showed you installed grub2's boot loader to the PBR or partition boot sector of Windows. All NTFS partitions have to have a NTFS boot signature which also has the same partition info as partition table and which boot loader ntldr(XP) or bootmgr(Vista/7/8) to use. When it has grub in PBR it is not valid.

NTFS does keep a backup and testdisk can usually restore from backup. Windows fixBoot which repairs PBR and chkdsk which reset size info in PBR also works from Windows repairCD. 

You should have a Windows repairCD or flash drive and Ubuntu liveCD or flash for the current version of every install you have, so you can make repairs.

---

### Post by ali8 on 2013-07-15
I already had the Windows DVD and tried repair from there, but as I mentioned earlier it did not work.

So how do people install windows 7 plus Ubuntu without having such problems?

---

### Post by oldfred on 2013-07-15
If you install grub2's boot loader to the MBR of the hard drive, you usually do not have issues. 

A few with encryption or special DRM software used to have issues but most of those have been resolved. Some of those then used EasyBCD and installed grub to the PBR of the Ubuntu partition (not NTFS partition) and EasyBCD uses grub4dos to chainload to Ubuntu. But that compromises grub2 as it does not really fit into a PBR and converts to blocklists or hard coded links. If any of the other parts of grub in Ubuntu are updated and address on drive changes, you have to do major repairs to grub.

---

### Post by fantab on 2013-07-16
> **ali8 said:**
> I finally formatted C and re-installed Windows 7.

Any ideas what was wrong?

Although I don't really know what went wrong, Oldfred makes sense.

> What options do I have other than formatting C again and installing Windows...?

You had installed Ubuntu 'inside' Windows using WUBI. You must seriously consider installing Ubuntu to its own partition if you want to continue using it. WUBI installs are not meant to be a permanent way to run Ubuntu.

---

### Post by ali8 on 2013-07-16
@fantab, no I did NOT. I installed a stand-alone Ubuntu from DVD.

---

