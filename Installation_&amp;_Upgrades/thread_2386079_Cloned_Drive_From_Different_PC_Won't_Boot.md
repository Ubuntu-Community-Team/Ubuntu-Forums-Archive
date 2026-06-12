---
title: "Cloned Drive From Different PC Won't Boot"
date: 2018-02-28
forum: Installation &amp; Upgrades
---

### Post by gobbledigook2 on 2018-02-28
I realize this problem has been addressed before ([https://ubuntuforums.org/showthread.php?t=2182661&page=2&highlight=cloned+drive+pc+won%27t+boot](https://ubuntuforums.org/showthread.php?t=2182661&page=2&highlight=cloned+drive+pc+won%27t+boot)), however I seem to be unable to fix this on my own. I am trying simply to get a cloned hard drive with ubuntu to boot on my computer. The computer recognizes in BIOS that the drive exists. I have followed the steps outlined in the other forum link on the second page, but after giving the "boot" command, the computer complains about not finding initrd images. I'm hoping someone can help walk me through the process of correctly setting the parameters for my system. The new computer is running Ubuntu 16.04. Thank you for any assistance you can provide.

---

### Post by oldfred on 2018-02-28
How different are the specs of the computers.
Are both UEFI or both BIOS?
Same video driver?

I generally find it easier just to install. And then if you want you can restore /home and list of installed apps. Essentially just like restoring from your backups to a new drive. And it helps you to know your backup procedure works.

 May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by gobbledigook2 on 2018-02-28
I wish that were an option. Unfortunately I'm doing a research project which requires a clone of a working installation which has certain file systems in place. I apologise, I should have made that clearer before. I'm doing this because some configuration files associated with the research (non Ubuntu related) became corrupted, and I needed a fresh working copy, which I received from a colleague. Both were running BIOS and both had Ubuntu 16.04. I have already tried running boot repair with no success. But I will try the newer version and make the post as you suggested.

---

### Post by sudodus on 2018-03-01
> **oldfred said:**
> How different are the specs of the computers.
...
Same video driver?


If there is a proprietary graphics driver in the system (typically for an nvidia graphics chip/card), and you have another graphics chip/card, you may have problems.

If ***you*** have an nvidia graphics chip/card, and the system does not, you may need the boot option nomodeset and after that maybe install a proprietary driver to take full advantage of the graphics hardware.

---

### Post by oldfred on 2018-03-01
I do not understand that a new install is not feasible.
You always must have good enough backups, especially if anything is unique, so you can restore system.

And trying to restore to different hardware then is always more difficult, but with Ubuntu does usually work.

       May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by gobbledigook2 on 2018-03-05
A new install is not feasible because what I need to restore is an older version of my file system. The method by which we backup our computer (weekly) erases the older versions of the files, and keeps only the newest. That is why my collaborator sent me the working version of his file system on this new hard drive. 
I have run Boot Repair. Here is the output. [http://paste.ubuntu.com/p/PGFjjFvkSG/](http://paste.ubuntu.com/p/PGFjjFvkSG/)

Hopefully you have some idea what is wrong. I am trying to boot the SDA disk with the "WDC" id.

---

### Post by oldfred on 2018-03-05
You are showing both an older BIOS boot loader in MBR, but have UEFI boot configured & in fstab.
So system is UEFI.

But system boots from an ESP - efi system partition which must be FAT32.
But to make it an ESP, with gparted you have to put the boot flag on the FAT32 partition.
Or if using gdisk use code ef00.
Actual gpt(GUID) code is some very long GUID, and different tools use different codes to assign the GUID.

So move boot flag from sda1 to sda2 using gparted from live installer.
Then run Boot-Repair which will uninstall/reinstall grub to add UEFI entry into UEFI menu.
But note that running updates on system will update everything unless you lock out the update of certain packages.
You may be able to manually add an UEFI boot entry with efibootmgr.

 sudo efibootmgr -c -l "\EFI\UBUNTU\SHIMX64.EFI" -L ubuntu -d /dev/sdX -p Y
where /dev/sdX is the disk and Y is the partition number. 
Your ESP is sda2, so:
sudo efibootmgr -c -l "\EFI\UBUNTU\SHIMX64.EFI" -L ubuntu -d /dev/sda -p 2

What brand/model hardware?

You also show a lot of kernels. Generally we suggest only keeping the two newest. But if in your case you need an older one you need to save that.

---

