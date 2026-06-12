---
title: "GRUB2 bootloader crashes with Win7 and Ubuntu 10.04 dual boot"
date: 2010-05-07
forum: Installation &amp; Upgrades
---

### Post by matrix13 on 2010-05-07
I have a Dell Studio 14 laptop with Windows 7 64bit preinstalled. The processor is core i5 and the machine has 4GB RAM. I freed 25GB of memory from my Hard disk and tried to install Ubuntu 10.04 (AMD). Everything went fine. I restarted and Logged into Ubuntu. It worked like a charm. Then I restarted to Windows7. This also worked well as expected.

But, when I rebooted again, I got a black screen saying that
“No modules found. Press any key to restart”
When I press a key, it says “No operating system found”, probably after checking through a network (it printed lines starting with PXE).

I tried exactly in the same way with Ubuntu 8.04 in my machine, and this worked without any problem. The Bootloader was not corrupted after restarting from Windows. I noticed the problem with Ubuntu 9.10 and 10.04. I feel like a problem regarding the bootloader version. AFAIK, 9.10 and 10.04 is using GRUB2 when 8.04 use the old version of GRUB. Will I have to switch to the legacy GRUB? (I would love to keep using GRUB2). If yes, I would like to know How.

Is there any way to resolve this issue?
Thanks and Regards

---

### Post by lechien73 on 2010-05-07
If you boot from a LiveCD, does:
```
sudo fdisk -l
```
show your Linux and Windows partitions?

Maybe you need to reinstall Grub using the instructions found at point 13, [here.]("http://ubuntuforums.org/showthread.php?t=1195275")

---

### Post by matrix13 on 2010-05-12
fdisk shows the windows and linux partitions.
I reinstalled GRUB2 from 10.04 live cd. But, whenever I boot into windows7, then restart the machine, GRUB 2 is again lost.

---

### Post by darkod on 2010-05-12
I hate this branded machines. You are right, it's related to grub2 vs grub1 but it's not ubuntu's fault.

Months ago we were very puzzled here on the forum with such behavior and the conclusion was (can't remember right now how strong was the evidence, but there was some):

Some HP and Dell machines have pieces of HP/Dell software working behind your back without you even knowing about it. After you boot windows they think your MBR is corrupted and do something. That something slices a piece of grub2 and makes it unusable. Grub1 is smaller in size and is not affected.

If you boot only ubuntu grub2 will work perfectly for as long as you want. The first boot into windows destroys it.

I can't remember if there was a definite solution, but now when you know the problem maybe google and searching this forum/archive can help. I'm pretty sure this is your problem.

Not sure if Dell support will have something smart to say. After all, adding ubuntu is not forbidden.

---

### Post by oldfred on 2010-05-12
We had so many the meierfra posted a page:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR)
[http://www.supergrubdisk.org/wiki/WindowsErasesGrub](http://www.supergrubdisk.org/wiki/WindowsErasesGrub)
In Windows 7, I had to remove Windows 7 DataSafe.
HP ProtectTools, Dell Recovery, and a few others write into MBR meierfra.
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941)
[https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/441941?comments=all](https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/441941?comments=all)
Dell Media direct issues with MBR
[http://ubuntuforums.org/showthread.php?t=923576](http://ubuntuforums.org/showthread.php?t=923576)
[http://ubuntuforums.org/showthread.php?t=1344828](http://ubuntuforums.org/showthread.php?t=1344828)

---

### Post by a546 on 2010-05-18
I have the same problem with Windows XP and Ubuntu 10.04.

---

### Post by oldfred on 2010-05-18
a546 welcome to the Ubuntu Forum.

the problem you have does not sound like what this thread is discussing which is primarily with win7 software overwriting the MBR. Please start a new thread and add some more information on exactly what is happening. Is your grub boot loader only not work after using certain software in windows? If it does not start at all check any of many threads on that issue first.

---

### Post by a546 on 2010-05-19
> **oldfred said:**
> a546 welcome to the Ubuntu Forum.

the problem you have does not sound like what this thread is discussing which is primarily with win7 software overwriting the MBR. Please start a new thread and add some more information on exactly what is happening. Is your grub boot loader only not work after using certain software in windows? If it does not start at all check any of many threads on that issue first.

Okay, thanks.

---

### Post by mikef01 on 2010-05-20
I have been struggling with this problem, when dual-booting 10.04 and Windows 7, on a Dell Inspiron 1545, 64 bit.  The result has been a wipe-out of GRUB after re-booting to Windows, reulting in an unbootable machine and "Module not found..." appearing. The problem is undoutedly the ill-disciplined Dell software that Dell have added in - I don't think it's a problem with either Windows 7 or 10.04, (GRUB 2), or their interaction. Getting rid of the Dell software works.
 
I have found the following solution to work for me (tested several times now and couldn't break it):
 
[LIST]
[*]Boot into Windows 7 using the supplied re-installation DVD
[*]Don't install but pick "Repair my PC"
[*]Follow the Windows instructions as given in the excellent site:
[/LIST][http://mattrudge.wordpress.com/2010/05/06/dual-boot-in-ubuntu-10-04/](http://mattrudge.wordpress.com/2010/05/06/dual-boot-in-ubuntu-10-04/)
 
[LIST]
[*]Then boot into Windows 7, from the hard disk, "as normal"
[*]Uninstall Dell DataSafe in Control Panel>Programs and Features
[*]Reboot using an Ubuntu install cd or similar device using the "try-out" option rather than the install
[*]Follow the "Windows boots, but Ubuntu won’t..." instructions on Matt Rudge's site as above
[*]Reboot and GRUB 2 should work...
[/LIST]Voila - seems to work:)

---

### Post by drgb on 2010-05-29
Thanks, mikef01. These steps worked for me. 
The only difference was that I had no usable Windows 7 recovery disk, so I had to reinstall grub in Ubuntu from the Ubuntu live cd, then boot Windows 7, remove the Dell Data Safe programs (I uninstalled all 3--basic, supporting software and online backup), then do the grub2 reinstall from the Ubuntu live cd a second time.
Now all is good.

---

### Post by rbisawa on 2010-06-06
[FONT=Arial][SIZE=2]Thanks, mikef01 !!
These steps worked for me too.

I also had no usable Windows 7 recovery disk, so  I had to reinstall grub in Ubuntu from the Ubuntu live cd, then boot  Windows 7, remove the Dell Data Safe programs ( I also uninstalled all  3--basic, supporting software and online backup ), then did the grub2  reinstall from the Ubuntu live cd a second time.

Now all is well.

[/SIZE][/FONT]

---

### Post by \/\/ill on 2010-07-21
I had this or a similar problem on my Dell Vostro laptop. After booting into Windows (most of the time) my system's MBR would be corrupted so GUB wouldn't load, I'd have to play arround with a live CD to restore it.

I also found that sometimes when booting into Windows, my touchpad was unresponsive and I had to plug in a seperate mouse.

This was not a Dell install of Windows 7, but a fresh install.

Eventually, I installed the latest BIOS update provided on the Dell website and all seems well now - hope this helps.

My next laptop will not be a Dell.

Will

---

### Post by mdog on 2010-08-08
I managed to fix this without removing dell datasafe (alienrespawn on my pc, same software apparently) by doing the following:

1. Fix grub 2 so I could boot into windows

2. Use the MbrFix.exe program (you need to download it and run it as administrator) to rewrite a windows MBR to the disk

3. Install EasyBCD in windows 7 and make a boot menu that points to my windows 7 partition and my linux /boot partition (it has a grub 2 option)

So what you get is basically a windows compatible boot loader, when you pick your linux installation from it, it goes right to the grub-2 boot menu you are used to.

I DON'T know if a kernel update in ubuntu will overwrite the MBR again, which could be a problem.

---

### Post by tames on 2010-08-26
This happened to me, exactly as described, on a new Dell 1558 Studio laptop, after installing ubuntu 10.04 to dual boot with Windows 7. I panicked, and did a reinstallation of the "factory configuration", which worked, but of course blew away the linux installation (instead of repairing the MBR with the ubuntu Live CD). Before reinstalling linux, I updated my bios to the latest version A08. Upon reinstalling linux, and booting into Windows 7 several times, I am not having the problem (and did not need to uninstall the Dell DataSafe programs). Time will tell whether this will be a permanent fix, but recommend you try updating your Dell bios to the latest version, before installing linux, as another user described. It looks like the issue of DataSafe MBR corruption may have been addressed by a bios change.

---

### Post by candtalan on 2010-12-01
I am having this same mbr corruption in a friend's HP Laptop after just installing Ubuntu 10.04.1 as dual boot on his XP machine.
I am SO glad to have found this thread! Thanks for being here!

After an initial worry panic (!) I convinced myself I had somehow caused it, but later decided it was only after Windows shutdown.

This laptop is HP Compaq nx6325, CPU mobile AMD sempron  3400+,1800MHz, 512MB RAM. ROM date: 07/06/2006, ROM bios version F.02

I have been reinstalling grub2 from live cd so much now that I can almost do it in my sleep....

The HD contains a 6 GB recovery partition which is one of the grub2 boot options, along with XP, and the Windows side does contain some HP recovery programs. S far as I know  they are not running, but it may be there is something in the background. It also has anti virus avg free and I had started to consider if avg was doing some background mbr work. previous posts her say that when the Dell data safe stuff was removed, the problem went, so maybe it is not the avg.

I do not yet know what I might need to exactly do to get round this.

For reference, my thread, which after some confusion finally ends with me realising I had this problem and not some other, is
"HP laptop auto recovers Windows mbr after Ubuntu install! Help?" 
[http://ubuntuforums.org/showthread.php?t=1634386](http://ubuntuforums.org/showthread.php?t=1634386)
In hindsight, it is a misleading title, but it was the best I could do at the time!

I will look for data recovery software or similar, on the HP, and then consider actions and post back here.

---

### Post by candtalan on 2010-12-06
> **candtalan said:**
> I am having this same mbr corruption in a friend's HP Laptop after just installing Ubuntu 10.04.1 as dual boot on his XP machine.(snip)
Now sorted by removing some HP software.
Removed: (in this sequence, without rebooting unless stated)

AVGfree antivirus (reinstalled finally though)
HP Backup and Recovery manager (includes auto remove of recovery partition)
HP Protect Tools (Bios) 
HP Credential Protect Tools
HP Embedded Security Protect Tools (security chip previously set to 'Disabled')
HP Smart card Security for Protect Tools (forces reboot at this stage)(this reboot did not corrupt the mbr :-)  )
HP Protect Tools Security Manager 

Voluntary reboot
Normal restart into XP, confirming that mbr is not now being corrupted.
However, the mbr is a clean XP Windows mbr, without Grub, for dual boot,  so I reinstalled Grub from an Ubuntu Live CD 

Note: 
1) At the beginning of the above sequence of software removal I removed AVG in case it was participating in the mbr corruption. After the normal reboots became available, I then re installed (the latest version ) of AVGfree and there were no subsequent mbr problems.
2) Before doing the software removal actions above, I used partimage (which is on parted magic live CD) to create and save image of the Restore partition, for reference. Also, because the proprietary restore software was also to be removed, I created and saved the Windows partition image. If Windows ever needed to be reinstalled it would be much easier for me to re image the Windows partition than it would be to reinstall from scratch.


PS
Have just seen I now have 1000 beans! Celebration!

---

