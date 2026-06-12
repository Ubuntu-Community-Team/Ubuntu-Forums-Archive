---
title: "Dual-boot Mistake?"
date: 2006-08-06
forum: Installation &amp; Upgrades
---

### Post by ddshih on 2006-08-06
I'm new to the world of Linux, but very excited to be using open-source software! Since I wasn't quite sure whether I was going to make a full switch to Ubuntu, I tried to make my Windows machine a dual-boot system.  To begin, everything seems to work right now. I'm able to pick which operating system I want to use at start-up, Ubuntu and XP load up without a hitch, and each can write and read to the shared partition on my hard drive.  

The reason I'm writing is that I'm afraid that I might have made a mistake during the installation which will haunt me later.  I followed this guide: [http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html](http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html).  Everything went according to the guide until I got to the section where I had to set my mount point.  I was able to set the mount point for the Ubuntu installation to /, but no matter what I did, I could not turn the bootable flag on. I decided to proceed with the installation anyway.  After this point, the guide and I went on separate paths.  Instead of getting to choose whether to install the GRUB bootloader to the Master Boot Record, the installation just completed on its own.  I'm afraid that I might have done something goofy with the MBR by not turning the bootable flag on.

Now I'm having a couple of disconcerting things happen with Ubuntu, and I thought I should run them by this knowledgeable linux community to see if there's anything I need to fix.

1) My Windows Partition (hda1), which is formatted to NFTS, shows up like it's a USB flash drive.  I can access it and it also seems like I can write to it.  I try not to do anything with it, because I read somewhere that NFTS and Ubuntu don't always mesh.  

2) My Shared partition (/shared) shows up as a folder and not as a drive under my file system.  Also, when I write files to the shared partition from XP, I'm not automatically granted permission to write to the folders when I look at them in Ubuntu.  It's not a big deal, because I can just right-click on the files and change the properties to allow me to write to them (the X and the Pencil then disappear).

Are these issues indicative of a deeper problem with my installation?  Also, is there a way of remedying these issues?  Thanks for any help that you can provide. Other than that, the set-up was pretty straightforward, and I really like the way Ubuntu has been running.

---

### Post by coffeecat on 2006-08-07
As far as I know you have nothing to worry about, although those more knowledgeable than I may wish to comment. Your points one by one.

**Bootable flag**. If you are referring to the bootbale flag option in Gparted (the partition editor that comes with the Ubuntu live CD), then this is a Windows thing. Windows must be installed to a primary partition and needs a bootable flag although, to be honest, I don't understand the details. A Linux root partition (or any other partition for that matter) can be put on a primary or a logical partition, and Linux can boot from either. I don't think it needs a boot flag and I certainly don't remember such a thing from the many installations I have done of several distros on several machines.

**MBR**. If you used the live CD to install you don't get a choice of where to put stage 1 of the Grub bootloader. It goes on the mbr of the HD. If you need to install it elsewhere you have to use the alternate CD. For a dual-boot such as you have set up you have done just fine.

**Windows partition as flash drive**. Not quite sure what you mean here, but I assume you're referring to the desktop icon. Don't worry about it. This is a feature of Linux/Unix. All mounted partitions and devices are treated as files. A folder/directory is just a type of file. For convenience in a GUI environment an automatically mounted drive/partition is presented as an icon on the desktop.

**NTFS**. My advice is don't attempt to write to a ntfs partition from  Linux. I didn't even know that this was possible in Ubuntu - I've not tried it. It's still considered experimental because the devs have had to reverse-engineer ntfs read/write. Reading ntfs is quite safe.

**Shared Partition**. A partition is meant to be presented as a folder - see above. When you say 'not as a drive' you are still thinking in Windows terms with its ghastly C:, D: etc convention. You'll get used to it. :)  

**Shared file properties**. This should be easily fixable. Post back with the filesystem you chose for you shared partition. Also open a terminal and type:

sudo cat /etc/fstab

and post the output. It's only about half a dozen lines or so. (You'll be prompted for your password first.)

Welcome to the world of Linux. You've made a good choice with Ubuntu. I'll see if I can dig out a couple of web links for you which will expand on some of these points. I'll post back perhaps in a couple of hours when I get a moment and when I've found them

---

### Post by ddshih on 2006-08-07
Hi Coffeecat, 

Thanks for your thorough response! To address your points in an orderly fashion:

**Bootable flag**: the issue with the bootable flag occurred during the installation of Ubuntu.  After I chose to "Manually edit partition tables" (these were partitions that I had already made with GParted), I couldn't turn on the bootable flag. But if the bootable flag isn't all that important--and seeing as my system seems to boot up just fine in either mode--I guess I can stop worrying about that!

**MBR:** I did use MBR. A couple of articles that I read seemed to strongly recommend not installing Ubuntu on the MBR, but instead to install Ubuntu on the hard drive. But if you think that's okay, good!

**Windows partition as a hard drive**: You're right--I really just meant that it showed up on my desktop and in my "Computer."  I was concerned because this partition showed up in the same section with my desktop and file system, but I couldn't get my shared partition to show up there.  I guess I just felt like I had the wrong partition there.

**Shared Partition**: Sorry I'm still stuck in Windows lingo! By "drive" I meant that the Windows partition has a symbol like a hard drive (or my USB flash drive), while the Shared partition shows up with a folder symbol in my file system.

**Shared file properties**: My shared partition is /dev/hda4 (or /share).  The output of sudo /etc/fstab was this:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0    1
/dev/hda4       /share          vfat    defaults,uid=1000,gid=1000 0       0
/dev/hda3       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

Thanks again for all of your help!  It seems like I don't have much to worry about with my installation (so long as I don't write to my Windows partition while in Ubuntu).  Hopefully we can clear up the little shared file properties issue. I really do like how much faster my computer is with Ubuntu, and I've already had a lot fun customizing how my desktop appears. 

Oh, and one other slight issue that probably belongs in a different post: I'm using amaroK (with the Xine engine) to play my mp3s, but I don't think the sound is as good as it was in Windows' iTunes--some of the "complexity" seems to have been stripped in my music, and my subwoofer doesn't seem to be as active.  Any suggestions on how to fix that?  

Best,
Daniel

---

### Post by RRS on 2006-08-07
Bootable flag and MBR;
The MBR is a small bit of software at the beginning of your windows partition that the computer uses to start the operating system so only that partition needs the flag.
Grub is a linux program that identifies and selects from the operating systems installed. The portion of grub that displays and allows the operator to select a system was installed in the MBR by the Ubuntu installer.
Since my knowledge is still less then complete I hope I haven't "oversimplified" my explanation, I simply want to assure you all is normal and correct in you set-up.

As for your partition mounting questions;
Mounting as /media/xxxx displays the partition on the desktop, as you have your windows partion while simply mounting as /xxxx shows as a folder.
Either can be changed, along with the displayed name (windows instead of hda1 for example) by editing your fstab file.
You can also edit the vfat line to:
vfat iocharset=utf8,umask=000,uid=1000,gid=1000 0 0

This will give the user full read/write permissions.

[Aysiu's site]("http://www.psychocats.net/ubuntu/index.php") has an excellent guide to editing fstab [here]("http://www.psychocats.net/ubuntu/mountwindows.php").

Hope this helps clarify things for you.

---

### Post by coffeecat on 2006-08-07
The MBR (master boot record) as I understand it is the first 512 bytes - the first sector - of your HD. The BIOS passes control to this during bootup. Windows puts a small piece of code there which passes control to the Windows bootloader which is somewhere in the Windows partition. Grub is an OS-neutral bootloader - think of it as a mini-operating system which can boot any OS. Strictly speaking it is not part of Linux. For all the gory details, see the Grub manual [here]("http://www.gnu.org/software/grub/manual/"). :) Simply put, stage 1 of Grub is written to the mbr, which calls up stage 1.5 and 2 which can be found in your Linux partition (in /boot/grub to be precise). The file /boot/grub/menu.lst will have an entry for Windows in your setup, and this chainloads the Windows loader. The articles you read recommending you do not install Grub to the mbr (I doubt they were strongly recommending) were probably referring to situations where you don't want this. For example, in a multiboot where you already have Grub and a suitable menu.lst set up somewhere. But in your situation, putting Grub stage 1 to the mbr is the easiest option - else how are you going to boot Ubuntu? Some people would use a floppy for booting up Linux, but I think this is an inelegant way of doing things. The only disadvantage that I can think of with what you have ended up with is the extremely unlikely eventuality of you wanting to ditch Linux. :wink: All you have to do then is to repair the Windows mbr with a 'fixmbr' from a Windows install CD. And if you don't have one you can always borrow one or there are other ways of repairing the mbr.

I concur with RRS' suggestion for your fstab line. In fact you can make it even more straightforward. Here is mine from my Windows/Ubuntu/Fedora multiboot (it's the Ubuntu line, changed for your mount point. It's the umask=000 that solves the permissions issue):


```
/dev/hda4    /share    vfat    defaults,utf8,umask=000    0  0
``` 
If, as RRS suggests, you want a desktop icon rather than a folder in filesystem, change /share to /media/hda4, but first do:

sudo mkdir /media/hda4

in a terminal if there is not already a /media/hda4 folder.

---

### Post by ddshih on 2006-08-07
Thanks to both of you for your help!  I did as you suggested, and everything seems to be fixed. The shared hard drive now appears on my desktop and as a partition rather than a folder. The Windows partition, since I disabled it, doesn't even show up in my file system when I boot up. This is great! :D Man, the support for Linux really is top-notch.

---

### Post by themusicwave on 2006-08-07
Hey glad you got it all working.

I am also new to Ubuntu, but I thoguht you might like to know that Ubuntu can read NTFS partitions just fine.  It's the writing that is an issue.  Writing is experimental I think.

I'm not sure exactly how I setup the partition for read access, someone else helped me.  But I bet you could easily find an answer out there.  If you can't let me know and I will look it up for you.

---

