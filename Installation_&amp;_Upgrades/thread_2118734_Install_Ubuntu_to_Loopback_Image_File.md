---
title: "Install Ubuntu to Loopback Image File"
date: 2013-02-22
forum: Installation &amp; Upgrades
---

### Post by amanisdude on 2013-02-22
**Hi all!**

The title says it all. I want to install Ubuntu (specifically Lubuntu for now, but maybe another flavor later) to a raw loopback image file (IMG, not ISO). 

The image file will reside on my FAT32-formatted USB stick at the maximum allowed size: 4,294,967,295 (or 2³²&#8722;1) bytes. (FAT32 is for Grub4Dos compatibility.)

I know [Wubi]("https://wiki.ubuntu.com/WubiGuide")/[Mint4Win]("http://usbtux.hostzi.com/mint4win") does something like this inside Windows, so I know it's possible; I've just never found a good resource that clearly documents the process.

Any help would be much appreciated! Thanks!

-***amanisdude***
___________________

***Note:** This question was asked before on this thread but was never answered: [http://ubuntuforums.org/showthread.php?t=1289533](http://ubuntuforums.org/showthread.php?t=1289533)*
___________________

---

### Post by dino99 on 2013-02-22
might help :p

[http://askubuntu.com/questions/128995/grub2-loopback-booting-ubuntu-server-iso](http://askubuntu.com/questions/128995/grub2-loopback-booting-ubuntu-server-iso)

---

### Post by amanisdude on 2013-02-22
Hi dino99,

Thanks for the reply. :D Unfortunately, I don't think the link quite answers my question. I am trying to install Ubuntu onto a raw disk image file similar to [the one Wubi, Lubi, and MINT4WIN creates]("http://en.wikipedia.org/wiki/Wubi_%28Ubuntu_installer%29") on an existing filesystem, not to an ISO.

The main advantage of this is that the host file is easily editable by the operating system, unlike ISOs which have write issues when live.

My main problem is getting the Ubuntu installation onto the image file in the first place, not necessarily booting it (which I already do with ISOs on my USB stick). Also, GRUB4DOS is actually a build of Grub1, not Grub2.

If you have any thoughts on how to do this, please let me know. The answer may well be in the link, but I just don't see it. Thanks again!


-[B][I]amanisdude
[/I][/B]___________________

---

### Post by oldfred on 2013-02-22
You can use wubi and boot with grub2.

I do not think this was a recommendation, but just a proof that it can be done.

       See also this thread, you technically do not need windows to use wubi.
Posts by meierfra. to use grub2 to directly boot wubi
[http://ubuntuforums.org/showthread.php?p=8903013](http://ubuntuforums.org/showthread.php?p=8903013)

---

### Post by amanisdude on 2013-02-22
Thanks for the reply OldFred!


Hmm... It feels like I'm not fully being understood here. Let me try and clarify my question. :)

&#8594; I have a bootable 32GiB USB Flash Drive
&#8594; The flash drive uses Syslinux to chainload Grub4DOS
&#8594; Grub4DOS then boots one of several ISO files on the flash drive as if they were CDs (See: [Multiboot ISOs]("http://www.pendrivelinux.com/tag/multiboot-iso/"))
&#8594; I want to do the same with a *dynamic installation* of Ubuntu on a *virtual disk image file* on my *flash drive*, _not_ hard drive
[COLOR=#F7F6F5]&#8594; [/COLOR](i.e., I want Grub4DOS to boot a virtual disk file on my USB Flash Drive as if it were a hard drive partition, not an ISO which acts more like a CD)
&#8594; If I were to do this, I would probably have no trouble booting the file with the existing Grub4DOS bootloader on my flash drive
&#8594; The problem is getting Ubuntu installed on the virtual disk file in the first place


Are you suggesting that I install Wubi then take the *root.disk* image file it creates and copy it over to my Flash Drive? I was hoping there would be a more elegant solution, but I suppose it is doable.

The only issue is that I already have Wubi installed in Windows, so I would have to archive the existing installation, reinstall Wubi, shrink down the resulting *root.disk* file to the maximum file size allowed by FAT32 (~4GiB), boot into it, remove *swap.disk* from */etc/fstab*, copy *root.disk* over to my USB Flash Drive, link it to Grub4DOS, and restore my original Wubi installation. Yuck!


Does anybody have an idea on how to do this in one fell swoop (or at least several feller swoops)? I mean, assume I am someone who does not have nor wants to install Wubi and does not want to mess with existing HDD bootloaders. How would I go about it this way?

Thanks for all the help, guys! You guys rock!


-***amanisdude***
_________________

---

### Post by oldfred on 2013-02-22
I have not tried virtual installs, just dual booting.

But why not a full install to your flash drive then. I have a full install of 12.04.2 on my 16GB flash in an 8GB partition and 8GB for data. Some minor changes to reduce writes, not real speedy but functional. Once system & apps are in memory not really different than my hard drive installs.

       Pros & cons of persistent install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

---

### Post by amanisdude on 2013-02-23
> **oldfred said:**
> I have not tried virtual installs, just dual booting.

But why not a full install to your flash drive then. I have a full install of 12.04.2 on my 16GB flash in an 8GB partition and 8GB for data. Some minor changes to reduce writes, not real speedy but functional. Once system & apps are in memory not really different than my hard drive installs.

       Pros & cons of persistent install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

Thanks for your help, Paul. :D I agree with all the points in that thread, which is why I opted for a multiboot persistent image install on my pen drive.

My main reason for a virtual install is portability. If I decide to move the install to another medium, it's pretty simple; all I need to do is move the file and configure the new bootloader.

The second reason is because the flash drive has so many other operating systems on it in the form of Live CD ISOs that a virtual install makes the most sense. Furthermore, it is easy to make a backup snapshot of the installation for my archives in case I mess something up, or to make a quick temporary clone of the install.

At any rate, do you know if there might be a tool to make a virtual install like I'm looking for, or someone who I might be able to ask? Maybe I could somehow pipe the output file of [Lubi]("http://lubi.sourceforge.net/lubi.html") into [Bubackup]("http://lubi.sourceforge.net/bubakup.html") and do it that way, or just maybe run [Bubackup]("http://lubi.sourceforge.net/bubakup.html") in a temporary virtualized instance and just copy the resulting image file? Thanks for the help, guys! ^_^

-[I][B]amanisdude
[/B][/I]___________________

---

### Post by amanisdude on 2013-02-26
***[[ post temporarily revoked until fully tested ]]***
__________________________

[COLOR="Silver"]Whelp, I finally did it. I can't say it was an elegant solution, but it worked. :)

First, I used ***Virtualbox*** to create a **new virtual machine** with a new **virtual disk **(*.vdi) file a bit smaller than the **maximum size** allowed by FAT32(4,294,967,295 bytes). I then **installed Lubuntu** onto the VDI using the Lubuntu ISO.

On the final step of the install *before* rebooting the machine, I **Alt+Ctrl+F1**'d into a background TTY and added my USB drive into the *VirtualBox* instance. I mounted the USB volume to a directory and [FONT=Courier New]***dd***[/FONT]**'d the whole virtual disk** ([FONT=Courier New]/dev/sda[/FONT], _not_ [FONT=Courier New]/dev/sda1[/FONT]) to a new file on the USB drive.

Once complete, I **unmounted the flash drive** and ate it. (*Note: Do not eat your flash drive.*) I also unmounted it from *VirtualBox*, which returns it to the host operating system.

Finally, I returned to the GUI (Alt+Ctrl+F7) in the guest virtual  machine and allowed the instance to reboot. (You don't have to do this,  just **power off the virtual machine** and delete it.)

The next step was to make sure that the file I created on my USB drive was **contiguous**. Since I was using *Windows* to do this, I downloaded ***[Contig.exe]("http://technet.microsoft.com/en-us/sysinternals/bb897428.aspx")** *(part of the *Microsoft SysInternals Suite*) and ran it on the file to check if it was fragmented. (If you're not comfortable with the command line stuff, you can use ***[WinContig]("http://wincontig.mdtzone.it/en/")*** instead.) I also ran an analysis on the file again after it completed to make sure it was fully defragmented, several times of which it wasn't.

__________________

**Note: **If you're host OS is Unix-type distro, you can use a Perl script called [defragfs]("http://sourceforge.net/projects/defragfs/") to do much the same thing.

**Note II:** For me, the file was still fragmented after running both of those utilities, so I used *Contig.exe* to create **another file** of the **same byte size**, which turned out to be a single fragment, and copied the contents of the old file over to the new one using *dd* and *[FONT=Courier New]conv=notrunc[/FONT]* as a parameter. You can also re-copy [FONT=Courier New]/dev/sda[/FONT] in the virtual machine to the new file using the same *[FONT=Courier New]conv=notrunc[/FONT]*. Then I deleted the old file.
___________________


Once that completed, I simply set the following entry in the [FONT=Courier New]***menu.lst***[/FONT] file for **Grub4DOS**:

```

title Lubuntu 12.10 Persistent Install
find --set-root *<image file path>*
map --unsafe-boot *<image file path>* (hd0)
map --hook
chainloader (hd0)+1
rootnoverify (hd0)
root

```And that was that! It worked! I tested it in an actual boot, and my computer exploded into persistent Lubuntu awesomeness! :D

Anywhoos, I hope my endeavors will help someone out there. I may even start an independent thread about this as a tutorial. This is a bit of a hack, really, so if there is a better way to do it, please let me know. (Or, better yet, pester [Geza Kovacs]("http://gkovacs.github.com/")—the maker of [Lubi]("http://lubi.sourceforge.net/")—to make a verson of Wubi/Lubi that can do this straight out of the box. :lol: )


Cheers!

–***amanisdude***
_________________

P.S. I somehow managed to get two forums confused and inadvertently called you Paul in my last post, Fred. Sorry about that. :lol:
_________________[/COLOR]

---

### Post by bcbc on 2013-02-26
You can download a preinstalled compressed disk image (ubuntu, not lubuntu), and then replace ubuntu-desktop with lubuntu-desktop.

Here they are: [http://releases.ubuntu.com/12.10/ubuntu-12.10-wubi-amd64.tar.xz](http://releases.ubuntu.com/12.10/ubuntu-12.10-wubi-amd64.tar.xz)
and [http://releases.ubuntu.com/12.10/ubuntu-12.10-wubi-i386.tar.xz](http://releases.ubuntu.com/12.10/ubuntu-12.10-wubi-i386.tar.xz)

I guess you just uncompress it and use resize2fs to get it to the size you want.

---

