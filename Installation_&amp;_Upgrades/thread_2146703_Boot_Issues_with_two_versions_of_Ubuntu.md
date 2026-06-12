---
title: "Boot Issues with two versions of Ubuntu"
date: 2013-05-19
forum: Installation &amp; Upgrades
---

### Post by chazdg24 on 2013-05-19
[http://paste.ubuntu.com/5680862/](http://paste.ubuntu.com/5680862/)

I have two hard drives with Windows 7 on sda and Ubuntu 13.04 and Ubuntu 12.10 on sdb.  When selecting 13.04, I get a cursor that flashes, then a message with my computer info and tty, then a login request.  I ignore that and 13.04 will boot after about 20 seconds.  How do I get rid of that.  My plan is to wipe out 12.10 when Mint 15 comes out.  I suspect I need to do something different during installation as I keep getting the same error message every time a new version comes out.  Thanks for any help.

---

### Post by jamesisin on 2013-05-19
Is this a new install of 13.04?  Did you run sudo update-grub yet?

---

### Post by chazdg24 on 2013-05-19
Relatively new.  I ran the boot repair in 12.10 as I am running the new version of Cinnamon.  Before that, I was getting that message when booting into 12.10.

If I could get Cinnamon to work correctly in 13.04, I would forget about 12.10.  However, it keeps freezing and screwing up Unity in the process (another issue for another post).

Edit:  I took a good look at that report and noticed a reference to Windows 8.  I did triple boot W7, W8 and Ubuntu 12.10 for a short time but quickly removed it and thought I restored my W7 MBR.  I then did a boot repair to restore Grub.  When 13.04 came out, I installed it alongside 12.10.  Grub picked up all three OS's but I had the problem I mentioned above.

---

### Post by chazdg24 on 2013-05-19
I am going to reply to my own thread in hopes of getting some feedback.  During the installation process, should Grub be installed on the first hard drive (sda) or the second hard (sdb)?  I have both 13.04 and 12.10 installed on sdb with grub installed on sda.  I have read that Grub should have been installed on the second hard drive containing Ubuntu 13.04 and 12.10.

When installing a second distro sharing the swap space, is there anything I can do now regarding my current configuration?  Finally, when I decide to install Mint 15 and remove 12.10, is there anything I should do differently to avoid the boot issues I described above?

Any guidance is really appreciated.  Thanks!

---

### Post by oldfred on 2013-05-19
You can install grub to either MBR. To me the advantage of grub in the MBR of the same drive is that then only drive has to work to boot Ubuntu and then you can have the Windows boot loader in sda and if the Ubuntu drive fails you can at least boot Windows. I generally believe in a operating system and it boot loader in every drive. Data then can be on various drives.

You either install grub from the Linux system you are keeping or when reinstalling be sure to use manual install and choose where to install grub. Then set BIOS to boot that drive.

You can also use Boot-Repair.
       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)

---

### Post by jamesisin on 2013-05-19
If you are running a multiboot system you can use a single swap partition for multiple swapping operating systems.  This is due to the fact that they will not be accessing the swap partition at the same time.  You just have to specify partitions at install and point swap to the already existing swap partition.  I believe it is possible to change a current swap pointer but perhaps someone else here could point you to a tutorial as I don't know of one.

---

### Post by chazdg24 on 2013-05-20
> **oldfred said:**
> You can also use Boot-Repair.
       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

That is what I did.  It is in post #1.  Any advice to deal with this issue is appreciated.  Thanks guys!

[http://paste.ubuntu.com/5680862/](http://paste.ubuntu.com/5680862/)

---

### Post by oldfred on 2013-05-20
So grub from sdb works ok?
I would just install Windows boot loader to sda, so you can boot with that. You can use a Windows repairCD or flash but need to set BIOS to boot sda before repair.
Not sure if Boot-Repair offers to just install a Windows boot loader to sda. It uses the syslinux boot loader.
But you can install lilo which also works like the Windows boot loader.

 Restore basic windows boot loader - universe enabled if error on lilo not found
Simply open Synaptic and Settings > Repositories and tick the box against the Universe repo in the Ubuntu Software tab. Close that window and click on reload before installing lilo with Synaptic or command line.
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR with bootloader.

You also have a lot of kernels. It may be time to house clean. I prefer to just use synaptic, some have posted scripts or just use command line.
      
 Check current kernel I also keep one older just in case:
#Current kernel:
uname -a
# kernels 
dpkg --list | grep linux-image


 In synaptic search for linux-image to choose to delete old ones
Also command line in post #8
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)

---

### Post by chazdg24 on 2013-05-20
> **oldfred said:**
> So grub from sdb works ok?
I would just install Windows boot loader to sda, so you can boot with that. You can use a Windows repairCD or flash but need to set BIOS to boot sda before repair.
Not sure if Boot-Repair offers to just install a Windows boot loader to sda. It uses the syslinux boot loader.
But you can install lilo which also works like the Windows boot loader.

 Restore basic windows boot loader - universe enabled if error on lilo not found
Simply open Synaptic and Settings > Repositories and tick the box against the Universe repo in the Ubuntu Software tab. Close that window and click on reload before installing lilo with Synaptic or command line.
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR with bootloader.

You also have a lot of kernels. It may be time to house clean. I prefer to just use synaptic, some have posted scripts or just use command line.
      
 Check current kernel I also keep one older just in case:
#Current kernel:
uname -a
# kernels 
dpkg --list | grep linux-image


 In synaptic search for linux-image to choose to delete old ones
Also command line in post #8
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)
I knew I would hear about the kernel issue!  :)  You are right about the house cleaning.

You would know much more than I do, but from that report, it appears that Grub is installed in both sda and sdb.  Am I wrong?  What I don't understand is why I need to install lilo.  I don't get how that would repair the Windows universal boot loader (is that the cause of my error message when booting into 13.04?).  Wouldn't the Windows 7 installation do the same (obviously wiping out Grub which is easy enough to fix).  Further, I thought Grub was superior or is that not the case.  

I hate to be a pest, but I am trying to gain as much knowledge as possible so I don't repeat the same errors in the future.  Thanks!

Edit:  I take that back, the Windows bootloader is installed on both drives.  How did that happen?  I never had Windows installed on sdb.  Is Grub installed on both drives or just sda?  I'm quite confused.

---

### Post by oldfred on 2013-05-20
Last BootInfo showed grub2's boot loader in every MBR. Are you just looking at boot flags?

Syslinux and lilo are boot loaders that work just like Windows in MBR. But to boot Windows you only install the MBR part and not any of the rest of the boot loader for Lilo or syslinux.
The Windows code in the MBR just looks at partition table  and finds primary partition with boot flag and jumps to the PBR or partition boot sector to find more boot code. And what is in PBR is then booted.
Actually lilo works a bit better than Windows as you can boot XP in a logical partition. Lilo boots from logical partitions but part of the Windows boot loader only checks primary partitions and will not let you boot from logicals.

 Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

### Post by chazdg24 on 2013-05-20
> **oldfred said:**
> Last BootInfo showed grub2's boot loader in every MBR. Are you just looking at boot flags?

Syslinux and lilo are boot loaders that work just like Windows in MBR. But to boot Windows you only install the MBR part and not any of the rest of the boot loader for Lilo or syslinux.
The Windows code in the MBR just looks at partition table  and finds primary partition with boot flag and jumps to the PBR or partition boot sector to find more boot code. And what is in PBR is then booted.
Actually lilo works a bit better than Windows as you can boot XP in a logical partition. Lilo boots from logical partitions but part of the Windows boot loader only checks primary partitions and will not let you boot from logicals.

 Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

I'm more confused than ever. I have never understood the 'boot flags' concept and where a boot flag should be installed (W7, Ubuntu 13.04 or 12.10).  In fact, I never tried to figure it out after screwing up many an installation of Ubuntu.
 
What I am trying to figure out is how to remove the message I receive when logging into 13.04 (that message does not appear with only one distro on sdb - 12.10 was installed on the second hard drive at first, booted quickly without issues).  I think Grub is installed in sda - I think (is that correct, that's what Boot Manager tells me....).  I would prefer not to blow up W7, Ubuntu 12.10 & Ubuntu 13.04 if I don't understand what is going on. :confused:

---

### Post by oldfred on 2013-05-20
Only Windows uses boot flags. Grub does not use a boot flag.
But a few BIOS (mostly Intel motherboards) check for a boot flag on a primary partition or will not even let you start to boot. So even with Ubuntu we suggest a boot flag, but grub does not need it.

Did you look at MultiBooters site. It pictorially explains BIOS booting.

---

### Post by chazdg24 on 2013-05-20
> **oldfred said:**
> Only Windows uses boot flags. Grub does not use a boot flag.
But a few BIOS (mostly Intel motherboards) check for a boot flag on a primary partition or will not even let you start to boot. So even with Ubuntu we suggest a boot flag, but grub does not need it.

Did you look at MultiBooters site. It pictorially explains BIOS booting.
Good information and yes I read that site once, got dizzy and closed it.  I will read it again another day.  I am sure I will be able to absorb it.  I hope...

---

### Post by chazdg24 on 2013-05-20
> **oldfred said:**
> Restore basic windows boot loader - universe enabled if error on lilo not found
Simply open Synaptic and Settings > Repositories and tick the box against the Universe repo in the Ubuntu Software tab. Close that window and click on reload before installing lilo with Synaptic or command line.
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
Well I did this and I booted directly into Windows.  I then booted into my Ubuntu 13.04 disk and did the recommended repairs.  The Grub menu is back but I still have the same issue outlined in my initial post.  Here is the output:

[http://paste.ubuntu.com/5685460/](http://paste.ubuntu.com/5685460/)

I have no idea what is going on.  Any ideas are appreciated!  :)

---

### Post by chazdg24 on 2013-05-21
Anybody have a clue what is going?  Help...:)

---

### Post by arpanaut on 2013-05-21
Did you change the boot order to boot sdb first like the pastebin report suggested?
With that set up you should be able to choose what you want to boot directly.

I don't know but there might be a conflict with the NeoSmart boot loader you installed into windows.
I haven't used that in years so don't know how it works these days.

You defeated your purpose when you did the boot repair default repair, what oldfred was suggesting,
was to have windows bootloader on sda, then use the bios to change which disk was the primary in the bootorder.
When you did the repair you overwrote the win bootloader in sda with grub. So the lilo work was nullified.

Try changing in the bios to have sdb as the first hard disk in the booting order and see if things boot correctly.

That's all I got for now.

---

### Post by chazdg24 on 2013-05-21
> **arpanaut said:**
> Did you change the boot order to boot sdb first like the pastebin report suggested?
With that set up you should be able to choose what you want to boot directly.

I don't know but there might be a conflict with the NeoSmart boot loader you installed into windows.
I haven't used that in years so don't know how it works these days.

You defeated your purpose when you did the boot repair default repair, what oldfred was suggesting,
was to have windows bootloader on sda, then use the bios to change which disk was the primary in the bootorder.
When you did the repair you overwrote the win bootloader in sda with grub. So the lilo work was nullified.

Try changing in the bios to have sdb as the first hard disk in the booting order and see if things boot correctly.

That's all I got for now.
I think my answers were not very clear to oldfred, but I did indeed change the boot sequence directly after installing lilo and booting directly into windows 7.  It did not help.  After booting into into W7 after changing the boot order to the second hard drive, I still booted to W7 (I don't understand that). I had no choice at that point but to install Grub to gain access to 13.04 and 12.10.  Just to be sure, I did it all over again with the same results.  By the way W7 is a clean install without NeoSmart boot loader.   Yet is appears to show up.  I don't get it.

---

### Post by oldfred on 2013-05-21
If you set sdb as boot drive in BIOS Windows may have installed its boot loader to sdb, even though the main install is on sda. It installs boot files to the drive set as boot in BIOS.

---

### Post by chazdg24 on 2013-05-24
> **oldfred said:**
> If you set sdb as boot drive in BIOS Windows may have installed its boot loader to sdb, even though the main install is on sda. It installs boot files to the drive set as boot in BIOS.
I figured this issue out and it has nothing to do with where Grub is located or the BIOS.  The latest round of updates screwed up my 13.04 installation.  After trying every trick in the book, I decided to wipe out 13.04 and reinstall.  Instead of installing the boot loader in sda, I installed it in the mount point partition and let 12.10 control Grub.  The down side is that I must boot into 12.10 to update Grub to include 13.04, which is exactly what I did.  I rebooted in 13.04 with no errors!

I updated my system and rebooted.  Still a nice clean boot.  Next I installed the ATI 13.4 driver for 13.04 using these instructions:  [http://askubuntu.com/questions/124292/what-is-the-correct-way-to-install-ati-catalyst-video-drivers-fglrx/286775#286775](http://askubuntu.com/questions/124292/what-is-the-correct-way-to-install-ati-catalyst-video-drivers-fglrx/286775#286775)

I rebooted and get the same error message I outline in my first post.  This is a video card driver issue!  I just wanted to inform everyone about this and thank you oldfred for your help.

---

