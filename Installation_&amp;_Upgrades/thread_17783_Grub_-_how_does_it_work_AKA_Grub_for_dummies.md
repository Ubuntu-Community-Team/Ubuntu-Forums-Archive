---
title: "Grub - how does it work? AKA Grub for dummies"
date: 2005-03-02
forum: Installation &amp; Upgrades
---

### Post by pigpen on 2005-03-02
Ok, so I can sorta use Grub, now I'm trying to fully grasp the basic logic of how Grub *actually* works, since it is such an important aspect for dual (or triple) booting it'll help immensely in troubleshooting problems. Misunderstanding of Grub, is often a leading cause in installation failures and booting problems, often rendering your computer unusable, unless you know how to fix it.

So *please* correct me if I'm wrong in any of this. I'm far from a *nix guru and just a newbie that has MUCH to learn.

Grub is a bootloader that can recognize different filesystems and can launch different OS's. Ok, thats easy to understand.

Harder to understand is actually how it does this.  I've read a [lot](http://www.gnu.org/software/grub/manual/grub.html)  and in layman terms, Grub is really not one program, but actually made of separate components (stages).   When Grub is installed to the MBR, master boot record, of your hard drive, a part of Grub is executed (launched) during the booting process of your computer.  All Grub knows at this point is where the rest of the Grub files are located, and upon finding these files, it executes them, and this part of Grub actually loads up the important stuff like your grub menu.1st settings, the Grub menu, etc.  For details, read [this](http://users.ameritech.net/gholmer/booting.html) 

What I'm a bit unclear is how Grub functions when it is NOT installed to the MBR, but rather to another partition, ie your '/' root partition or a small '/boot' partition. From what I understand Grub is installed in the first bootable sector of this partition, so how does your computer know to start Grub, and not use the info from the MBR, if Grub does not reside in the MBR? Is it because you have to make the partition that Grub is on,  a bootable (or active) partition?.  

So does Grub work like this? Computer powers on, bios executes code, looks at MBR, if Grub is found, find the rest of Grub files and execute these Grub components. If Grub is not found in MBR, then look in the boot sector of the ACTIVE(?) BOOTABLE(?) partition and if Grub is found, execute Grub (and the rest of the stages of Grub). Is that how it works in a nutshell? Is Active, Primary, Bootable partitions mean the same thing, in regards to running Grub?

So if this is how Grub works, is the following is true?

1) As long as Grub is either in the MBR, or in a boot sector of an Active partition, it can run? What if Grub is on a non-active partition. Grub can swap active and non-active partitions, but can *itself* be execute from a *non-active* partition providing Grub does not reside in the MBR. See [this](http://www.gnu.org/software/grub/manual/grub.html#DOS%2fWindows)  on swapping partitions with grub.

2) On old computers, if your BIOS has the infamous 1024 cylinder limit, Grub (or any boot loader) must reside with the 1024 cylinder limit, that is within the 8.5GB of your primary (active) partition of your first hard drive. Or can it reside in any hard drive & partition within the 1024 limit? See [this](http://www.ubuntulinux.org/wiki/WartyWarthogInstallNotes)  and [this](http://www.geocities.com/epark/linux/grub-w2k-HOWTO.html)  for more on this and suggested workarounds. 

Important things to note. Because Grub is comprised of different components (pieces of code), and execute in a certain order (stages), the first part of Grub points to where the rest of your Grub files reside. This first part of Grub may reside in the MBR or your boot sector of your partition.  

So this brings up the issue, how do you install, move, or delete Grub since I can't manually edit this first part of Grub? Well, I believe the only way is to re-install Grub which will overwrite the old Grub (or anything else) in your MBR, or boot sector of your partition. Changing Grub from MBR to a boot partition, may also involve you restoring the MBR to its original state (ie. with fixmbr or fdisk /mbr, depending on your OS) and then installing Grub to your new boot partition.  

*Important tidbit btw, to fix Windows MBRs use the correct DOS command. fixmbr restores Windows 2000 and Windows XP MBRs, while fdisk /mbr fixes Windows 98/95 MBRs. I've seen people get confused and often suggest (to much potential harm) the wrong command to people. Read one person using the Win95/98 mbr command to render his WindowsXP MBR useless.

SO............................do I have this all correct? Please feel more than free to correct any of this.  I had originally thought that regardless if you install Grub to a partition and not the MBR, that still some code of Grub gets installed to the MBR, the first part of Grub that tells the bios where to look for the rest of grub, but I now believe that isn't true. If you install Grub to a partition, the MBR does indeed remain untouched.  *I think*. 8-[ 

Phew...so Linux Gurus or more knowledgeable Ubuntu folk, please comment on these issues so us newbie Linux users can get a handle on the Grisly Beast known as Grub.

---

### Post by az on 2005-03-02
Pretty much correct.

You worry too much about silly things like putting grub somewhere else than the MBR.  You would only need to worry about that if you really needed to do that.  I am pretty sure that you do not, and never will.

An important comaprison to make is lilo and grub.  Lilo is a bootloader than is installed and comfigured by running the command lilo. At that time, the configuration file is read and the information is written to your mrb.  This is in contrast to grub which reads the configuration each time you boot.
1-  You can change the configuration for grub and not have to run anything for it to take effect.  This is a classic problem with lilo - you edit the lilo config and forget to re-run lilo.  You are stuck having an unbootable computer...
2-  Grub's configuration can be changed at boot time by you (using grub's editor).  very cool.  You will never get into trouble again.  Unless you bugger up your mbr...

---

### Post by rkn on 2005-03-03
Grub is a tiny operating system with many features and commands can be run interactively.
There is a good manual online here:
[http://www.gnu.org/software/grub/manual/grub.html](http://www.gnu.org/software/grub/manual/grub.html)
I install grub in each root partition of each distro.  Grub in the boot partition of hda uses chainload to start a bootloader in a root partition.
It is also a good idea to create a grub boot floppy, then you can always rescue from a grub prompt with:
[COLOR=Blue]
grub> root (hd0,0)
grub> setup (hd0)
grub> quit
[/COLOR]

Bob

---

### Post by pugrit on 2005-03-03
if in dual boot then you deleted the partion for ubuntu and when you restart your computer..grub is still there but wont load any OS at all anymore..even the xp which was not deleted.

how can i fix this?and wuld it b epossible to change loaders even if you already have grub..say lilo?how?
thanks

---

### Post by pigpen on 2005-03-03
azz & rkn: thanks for the input. I learned some stuff.

 And you're right azz, I shouldn't worry about the MBR, I just wanted to know exactly all the options of what GRUB can do. After manually installing grub a few times to MBRs and separate partitions, I think I have a good grasp on how GRUB works and what it does. Repairing MBR's seems, in my experience, fairly easy to do in case if things go bad, in most times, the ideal place to put GRUB, unless you know what you are doing.

rkn,  thanks for the tip about chaining grub boatloaders. I'll have to try that now that I feel comfortable with using grub to install itself in the MBR or in different partitions.

As to fix MBR or restore Windows MBR, I take it these are the two most popular methods.  For Win95/98/ME in DOS (off a dos boot disk perhaps) [fdisk /mbr](http://support.microsoft.com/kb/q69013/)  and for WinXP/2k, using the recovery console (or a winxp/2k bootdisk), run [fixmbr](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx)
What is the recommended solution to fix MBR's for Linux only filesystems? Is there a recovery tool to backup the original Linux MBR?  I heard there was some switch in Lilo to recover the old MBR, but I'm not aware if GRUB can do this.  BTW, for window users reading this, if you had made ERD's during your windows installation, which are emergency recovery disks, they will restore a backup of your MBR as well. 

One thing that might seem obvious to others, but not to a newbies (like me) is that if you are dual booting Linux with a pre-WinXP/2K/NT system, like Win98/95/ME, you have to have atleast 1 mulit-os bootloader *installed in the MBR*. Whether that is GRUB, some 3rd party DOS/Windows Boot loader, that boot loader in the MBR has to be there to inturn either launch your OS, or launch another boot loader if you had installed it, like GRUB, into a separate partition. While there is always a boot loader of some sort put into the MBR, regardless of OS (otherwise you'd never be able to boot at all), the default Win98/95/ME boot loader can't handle multi-OS boot loading, therefore you need to install another one in the MBR.

However, with Windows XP/2000 (and I think NT variants like NT 4.0), by default they have a boot loader than can handle multi-OS boot loading...sort of.  You actually chain load it, that is the WinXP/2K boot loader will launch another boot loader, like GRUB, that has been installed in a different partition. This way you can keep original MBR intact which contains your original WinXP/2K boot loader. You just have to add an option to the WinXP/2k boot loader to launch GRUB (or LILO or whatever bootloader) which will then in turn launch Linux (or whatever OS). I had already posted the relevant links in my first post, but this goes into it some [more](http://www.geocities.com/epark/linux/grub-w2k-HOWTO.html) and as [this](http://www.gnu.org/software/grub/manual/grub.html#DOS%2fWindows) does too.  

Another way of thinking about this is, if you install GRUB into the MBR, then you're fine, you basically don't have much to worry about. If you install GRUB to a separate partition, like the '/' root partition of your distro installation (like Ubuntu), then you'll need to a) configure your main boot loader (WinXP/2k default, lilo, GRUB etc) in the MBR to launch this partition-installed GRUB or Ubuntu directly, or b) install another boot loader (like another copy of GRUB) into your MBR and configure it to do the same as option a), that is to launch the partition-installed GRUB or Ubuntu.

I'm assuming what GRUB, when it becomes actually responsible for launching an an OS, as opposed to chain loading another boot loader, is that it executes the  kernel of the OS, in this case Ubuntu's kernel (as well as other things like swap, hide, make active your partition, etc).

Again I hope I got all of this straight as well.

pugrit: if you had read this whole post =) hopefully you have found a solution to your question. Basicially depending on what OS you are using you can restore your Windows MBR easily. See the links in my 4th paragraph. As to changing loaders if you already had GRUB, I believe it just a matter of installing Lilo into the MBR and it will overwrite and effectively erase GRUB.  I've never used Lilo so I don't know the details on how to install Lilo, but according the GRUB manual, this is one way on how you can remove GRUB (or by restoring/fixing your MBR).

---

### Post by ShortyG on 2005-03-03
:o  All i know is i click on the operating system i want and it boots. lol.

---

