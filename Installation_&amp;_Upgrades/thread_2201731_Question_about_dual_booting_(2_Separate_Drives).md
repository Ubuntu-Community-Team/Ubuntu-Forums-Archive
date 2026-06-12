---
title: "Question about dual booting (2 Separate Drives)"
date: 2014-01-25
forum: Installation &amp; Upgrades
---

### Post by shadowfox1991 on 2014-01-25
Hello,

I currently have a setup running Windows 8, and wanted to install Ubuntu on another drive that I added to my computer, although I have some questions.

First, if I unplug the Windows drives before launching the installation, does this ensure that grub will never over-write the windows bootloader? (even after they are plugged back in?)
Second, I do have secure boot turned off in the motherboard settings, but is it necessary to turn fast boot as well (Not in Windows but in the UEFI)?

Thank you!

---

### Post by sudodus on 2014-01-26
Welcome to the Ubuntu Forums :-)

> **shadowfox1991 said:**
> Hello,

I currently have a setup running Windows 8, and wanted to install Ubuntu on another drive that I added to my computer, although I have some questions.

First, if I unplug the Windows drives before launching the installation, does this ensure that grub will never over-write the windows bootloader? (even after they are plugged back in?)
Yes, it is a good safety precaution to disconnect a drive you don't want to touch. Ubuntu will not overwrite any bootloader automatically. You can do it *manually* afterwards, if you want to, but then you should know what you are doing.
> 
Second, I do have secure boot turned off in the motherboard settings, but is it necessary to turn fast boot as well (Not in Windows but in the UEFI)?

Thank you!

Yes. And you should also turn off hibernation of Windows. See this link (from when I learned how to do it from *oldfred*)

[http://ubuntuforums.org/showthread.php?t=1769482&page=52&p=12608648#post12608648](http://ubuntuforums.org/showthread.php?t=1769482&page=52&p=12608648#post12608648)

---

### Post by sudodus on 2014-01-26
I should add that if you

1. re-connect the drive with Windows

2. go into the BIOS/UEFI menu system and set the boot order to boot Ubuntu first

3. boot into Ubuntu and run

```
sudo update-grub
```

you should find Windows in the grub menu and be able to select which system to boot. (This writes nothing to the Windows drive.)

If these things do not work, I suggest that you try ***Boot Repair*** and ask at the megathread[URL="http://ubuntuforums.org/showthread.php?t=1769482"]

[Boot-Repair] Graphical tool to repair the PC boot in one click[/URL]

---

### Post by oldfred on 2014-01-26
With UEFI, Ubuntu/grub does not overwrite the Windows boot files. (really old version of grub did have a bug that did that). All boot loaders install in separate folders in efi partition.

But be sure to boot Ubuntu installer in UEFI mode as that is how it installs. Or if you manually installed Windows 8 and it is in BIOS/MBR mode, you will want to install Ubuntu in BIOS boot mode.

But with two drives better to have Ubuntu boot from its drive without other drive. Or have another efi partition on Ubuntu drive. Then each drive can boot without other drive from UEFI menu. That way when one drive fails, you can still boot the other drive.

Its easier to disconnect Windows drive, but if careful and create partitions correctly you can do it with Windows drive installed, but have to use Something Else or manual install. Often best to partition in advance so you have control over partition sizes as auto install just defaults to / (root) and swap and on new drives you may get a way too large root where smaller root is more efficient and you may want shared data partition(s) or separate /home.

If you want suggestions on manual install and partitioning we can give those. Partitioning depends a lot on what you may want to do, and requirements can vary a lot.

 Shows install with screen shots for both BIOS & UEFI, so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot. required for UEFI & grub bug fixes
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by shadowfox1991 on 2014-01-27
Thanks for the info.

I never really partitioned myself, so any help would be greatly appreciated. I will be using a 250GB HDD, and will be using Ubuntu mostly for development purposes (mostly web dev, although it could be pretty much anything). I have 8GB of RAM, not sure if this info is needed for the swap partition, but might as well say it.

Thank you!

---

### Post by oldfred on 2014-01-27
I think gparted is pretty easy to use, but worthwhile to review how it works. I do not queue changes but run each. Sometimes when things are queued up on task may not complete and confuse the next.

 GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
Partitioning basics with some info on /data, older but still good bodhi.zazen
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)

        I used gparted and selected gpt under device, advanced & select gpt over msdos(MBR) default partitioning....


 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 300 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

Even if partitions are created in advance,  you have to use Something else and choose mount like / or /home and format like ext4. You do not have to format with gparted but it really does not matter nor take any real time.

I only boot with BIOS, so I have to have bios_grub, but new drives I put an efi for future use. You do not need bios_grub if UEFI booting. Example shows bios_grub, but you just need the boot flag.

---

