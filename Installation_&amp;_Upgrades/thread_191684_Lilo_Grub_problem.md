---
title: "Lilo/ Grub problem"
date: 2006-06-07
forum: Installation &amp; Upgrades
---

### Post by Foxblood on 2006-06-07
I currently dual-boot XP and Breezy. It was a botched operation and as a total newb, I didn't want to mess things up any further. The result was that I have to hold down Shift as my pc boots to get to the Lilo menu. Adequate at best.
Today I installed Dapper, in the vain hope that the installation, as well as giving me a new OS would also repair my Lilo. Result: Dapper is installed but no changes were made to my Lilo so I still have the choice of XP or Breezy, but how am I to run Dapper?
I've searched around and even used a Knoppix disc to learn more. My problem is that I get bogged down reading about Grub, Lilo, MBR etc etc.
As it stands, I want to protect my XP installation at all costs - I have no XP disc. I'm prepared to erase everything else if needs be, but, obviously, this would be a last resort. Can anyone point in the direction of getting my three OS's to boot, whether under Lilo or anything else

---

### Post by tonyr on 2006-06-07
Some questions:
Can you still boot to Breezy?
Did you install Dapper to a different partition, or did you just upgrade from Breezy?

A fresh dapper installation will install **grub** for you, unless you tell it not to, and
the process is smart enough to recognize WIndows as a boot choice.

---

### Post by Kapre on 2006-06-07
[QUOTE=Foxblood]I currently dual-boot XP and Breezy. It was a botched operation and as a total newb, I didn't want to mess things up any further. The result was that I have to hold down Shift as my pc boots to get to the Lilo menu. Adequate at best.
Today I installed Dapper, in the vain hope that the installation, as well as giving me a new OS would also repair my Lilo. Result: Dapper is installed but no changes were made to my Lilo so I still have the choice of XP or Breezy, but how am I to run Dapper?
I've searched around and even used a Knoppix disc to learn more. My problem is that I get bogged down reading about Grub, Lilo, MBR etc etc.
As it stands, I want to protect my XP installation at all costs - I have no XP disc. I'm prepared to erase everything else if needs be, but, obviously, this would be a last resort. Can anyone point in the direction of getting my three OS's to boot, whether under Lilo or anything else[/QUOTE]

Foxblood - when installing, make sure to read on the options when installing the bootloader. Make sure that GRUB (which is the default bootloader) takes care of your MBR. I myself am Quad-booting (Fed, Ubuntu, Kub and XP-Pro). 

K

---

### Post by Foxblood on 2006-06-07
Yes, I can still boot to Breezy. I didn't want to upgrade because I've messed up Breezy pretty badly, with installing things I don't want or need. Dapper is in a new partition.

---

### Post by Foxblood on 2006-06-07
If I reinstall Grub, will it overwrite Lilo or make things worse? I feel that I need to have one program booting. Either Lilo or Grub, but which one and how to do this?
Or, going back to my worse case scenario, how to get rid of everything except XP so I can then do a fresh Dapper install?

---

### Post by tonyr on 2006-06-07
[QUOTE=Foxblood]Yes, I can still boot to Breezy. I didn't want to upgrade because I've messed up Breezy pretty badly, with installing things I don't want or need. Dapper is in a new partition.[/QUOTE]

OK, I assume your Lilo control is in Breezy.  There should be a file **/etc/lilo.conf**.
If that is the case, you can add some lines to that to describe the Dapper boot 
configuration.  I'm going to assume that you have one hard drive with all the partitions
on it.  In a terminal to
```

fdisk -l /dev/hda

```

and post the results here.  If the **lilo.conf** file exists, post that here, too. If all
of this checks out, we should be able to "git 'er done".

---

### Post by tonyr on 2006-06-07
[QUOTE=Foxblood]If I reinstall Grub, will it overwrite Lilo or make things worse? I feel that I need to have one program booting. Either Lilo or Grub, but which one and how to do this?
Or, going back to my worse case scenario, how to get rid of everything except XP so I can then do a fresh Dapper install?[/QUOTE]

OK, I can do two conversations at the same time.  

**grub** will "overwrite" **lilo**  (this is somewhat of a simplification), but **grub** 
is a more flexible boot loader and less hassle in general.  Reinstalling Dapper and letting
**grub** install should solve the problem.  As I recall, the installation process reports
what other OSes it finds when it's in the bootloader stage.  There are some things you can do to save the MBR before you start, and replace it if things go south (a very unlikely
scenario), but that would be easiest if you have a floppy drive.

---

### Post by Foxblood on 2006-06-07
Thanks for the ray of hope. I've been at this since eleven o'clock this morning and it's now three am. I'll have to leave this until tomorrow after work. I'll let you know then. Thanks again, I really do appreciate your efforts.

---

### Post by Foxblood on 2006-06-08
Ok, here's what the results were from fdisk -l /dev/hda : 

Disk /dev/hda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        1275    10241406    7  HPFS/NTFS
/dev/hda2            1276        6374    40957717+   7  HPFS/NTFS
/dev/hda3            6375       10797    35527747+  83  Linux
/dev/hda4           10798       14946    33326842+   5  Extended
/dev/hda5           14854       14946      746991   82  Linux swap / Solaris
/dev/hda6   *       10798       14760    31832734+  83  Linux
/dev/hda7           14761       14853      746991   82  Linux swap / Solaris

The one marked with an asterisk is where Dapper is. I think. Also, I searched for the lilo.conf , but to no avail. At least not where you said it should be. There's one listed in /usr/share/doc/memtest86+/examples but it appears to be a sample and not the one that's being used.

---

### Post by tonyr on 2006-06-09
Well, that's confusing...
At this point we could spend some time trying to figure out what's what, or we could
just plow right on through.

When you installed Dapper, do you remember what you did about the bootloader?
Did you choose **Lilo** or **Grub**, or did you just skip it?

My advice here is to re-install Dapper, choose manual partitioning (more on this in 
a moment), and when it gets to the bootloader step, choose **Grub**.  I'm not 
sure whether or not the installation process is smart enough to recognize that Lilo 
is currently being used.  On a fresh install (new disk or Windows only disk), the default
selection is Grub. As **Kapre** pointed out, pay close attention to what the 
default selection is, and change it if necessary.  Before it actually installs **Grub**, 
it should tell you something about what other OSes it found.  Up until you let it 
install **Grub**, nothing about booting will have changed.  If you don't like what 
you see, you can simply stop.

At the **partition** step choose manual partioning.  You may have to scroll the
highlight bar down (with arrow keys) to see all of the partitioning choices.  It will show 
you a list of the partitions.  Scroll the bar to **hda6**. It should show a mount point 
of **/media/hda6**. Hit **return**.  
I don't recall exactly the sequence of events here.  I think at this point
it asks you to specify a mount point and a label.  The mount point should be "/", and the
label can be whatever you want (I think the default label is "/", also).  Then scroll the
highlight bar down to where it says something like "Done partitioning" and hit 
**return**.  At some point it will ask you about formatting options for that partition.
Choose the one that says **format**.  Then let it go on.

I'm thinking that this may not be the clearest explanation.  I haven't gone through the
installation process in several weeks.  I'll look around to see if I can find a more
comprehensive set of manual partitioning instructions.

---

### Post by tonyr on 2006-06-09
Here is a better set of instructions.  This article is primarily about a new Ubuntu
installation on a Windows system, which you can mostly ignore, but the section 
about **partitioning** is very nice.
[WindowsToUbuntu]("http://psychocats.net/ubuntu/windowstoubuntu.html")

Here's another good one (it references the other one, too).
[http://users.bigpond.net.au/hermanzone/]("http://users.bigpond.net.au/hermanzone/")

---

### Post by Foxblood on 2006-06-13
I tried to reinstall Dapper. Three times. It installs about 22% then crashes. Is the former installation still intact? If so, is it possible to edit lilo/conf to make it see Dapper? Failing that, is there any advice you can give as to how to get the installation to work?

Here's the bug report: 
Public bug reported:

Traceback (most recent call last):
 File "/usr/bin/ubiquity", line 130, in ?
   install(sys.argv[1])
 File "/usr/bin/ubiquity", line 55, in install
   ret = wizard.run()
 File "/usr/lib/python2.4/site-packages/ubiquity/frontend/gtkui.py", line 266, in run
   self.process_step()
 File "/usr/lib/python2.4/site-packages/ubiquity/frontend/gtkui.py", line 741, in process_step
   self.mountpoints_to_summary()
 File "/usr/lib/python2.4/site-packages/ubiquity/frontend/gtkui.py", line 1029, in mountpoints_to_summary
   self.progress_loop()
 File "/usr/lib/python2.4/site-packages/ubiquity/frontend/gtkui.py", line 538, in progress_loop
   raise RuntimeError, ("Install failed with exit code %s; see "
RuntimeError: Install failed with exit code 1; see /var/log/installer/syslog and /var/log/syslog

** Affects: ubiquity (Ubuntu)
    Importance: Untriaged
        Status: Unconfirmed

Thanks for the links, btw.

---

### Post by tonyr on 2006-06-13
You are using the Desktop CD (Ubuntu 6.0.6 LTS) to install?

Does the crash happen at the same place every time?

The last line of the bug report says to check two files, **/var/log/installer/syslog** 
and **/var/log/syslog**. Did you happen to look at those?  Is it possible to
copy those and attach them here?

I've never seen a crash like this during install.  My guess is that the original Dapper
install is gone, especially if you allowed the partition to be formatted.

---

### Post by Foxblood on 2006-07-07
Ok, this is how the never-ending trail of woe is. I failed to obtain the files that you, and the bug-report people, asked for. That search generated more error messages. I decided to eliminate the partitions with the failed Dapper installation together with it's swap file. Then I attempted to upgrade the existing Breezy install. Bad move. I've never seen so many asterisks and red print before, when I rebooted. Suffice it to say, that's a non-runner. I then eliminated everything except the partitions that XP uses. When I attempted to install Dapper all seemed to go well, but when I rebooted I gained the dubious pleasure of seeing even more red print. "Failed to load" seemed to figure prominently.
Basically, what I'm asking is is there such a thing as a step-by-step way to install? I want to know where the problem lies and what I can do to fix it. The lines of results, when I boot fly by way too quickly for me to ascertain exactly where the problem lies. I f my pc was ok for Breezy, surely it'd be ok for Dapper?

---

### Post by Foxblood on 2006-07-07
Is there a way to install Dapper without first having to run it Live?

---

### Post by tonyr on 2006-07-07
What does your partition table show now? Is it still like it was 
in the previous post?  From the Live CD, you can still do
**sudo fdisk -l**.

---

### Post by Herman on 2006-07-07
Sorry, I didn't mean to butt in, post deleted, (Herman)

---

### Post by Foxblood on 2006-07-07
I'm not sure from your question, what exactly you need to know. All that's left is the partitions that XP uses. I know I'm going to sound retarded but can you explain further your "sudo fdisk -l." post? I know you can't see, but I write in Crayons........

---

### Post by Herman on 2006-07-07
> I then eliminated everything except the partitions that XP uses. When I attempted to install Dapper all seemed to go well, but when I rebooted I gained the dubious pleasure of seeing even more red print. "Failed to load" seemed to figure prominently. You did the right thing there, (deleteing the partitions that are no good), that's exactly what I would have done.
>  Basically, what I'm asking is is there such a thing as a step-by-step way to install? I want to know where the problem lies and what I can do to fix it. The lines of results, when I boot fly by way too quickly for me to ascertain exactly where the problem lies. I f my pc was ok for Breezy, surely it'd be ok for Dapper? I am sure that if your pc was okay for 'Breezy', it will be okay for Dapper. There is a step by step way to install. More on that shortly.> Is there a way to install Dapper without first having to run it Live?Yes, the Ubuntu Dapper 'Alternate' install CD featues an installer with a text based partitioner more like the one you used to install 'Breezy'. It is not difficult to use, and offers more options and choices, especially regarding the bootloader (which one and where you want to install the 'IPL' for it. It also runs better in computers with less RAM. (This is roughly what I deleted from the earlier post).

Nowdays most people prefer to install GRUB to MBR because GRUB has the ability to to automatically update itself when our Ubuntu system gets a new kernel added when Ubuntu has an update. Ubuntu will be in GRUB's 'Automajic kernels list'. As far as I know, no other bootloader has that ability, and your system may become temporarily unbootable after an update until you manually edit the bootloader files of whatever other (non grub) bootloader you install.
I like to install LiLo though, but only to the first sector of my Ubuntu partition for a secondary boot method in case something happens to GRUB, (usually something I do wrong myself to GRUB), so I have an emergency boot method using [GAG Boot Manager]("http://users.bigpond.net.au/hermanzone/p12.htm") and LiLo.

Another feature of the 'Alternate CD' is the 'Rescue a Broken System' mode, with which you can re-install a bootloader, or install it to another location, which can be quite helpful.
You can probably download the 'Alternate .iso from the same place you downloaded the 'Desktop' Live/Install .iso from and burn it to a CD. For an illustrated web site dedicated to the 'Alternate' CD installer, [*Click Here.*]("http://users.bigpond.net.au/hermanzone/")

Sudo fdisk -l : You can run this command from either the Live CD or a Ubuntu install. Linux fdisk is a partition table editing software. The sudo fdisk -l or sudo fdisk -lu command is for printing out details of your partition table. It is one of the most often used commands and the information is often needed before making up another command to do something else, or for edtiting an operating system file of some kind or for diagnosing problems.  You won't need that now though.
Regards, Herman :D

---

### Post by tonyr on 2006-07-07
Sorry.  Been offline for awhile, suppertime her on US west oast. Thanks, 
**Herman**, for carrying on.

**sudo fdisk -l** is run, as **Herman** indicated, from the
command line.  Open a terminal (**Appplications->Accessories->Terminal**)
and type that fdisk stuff.

---

### Post by Foxblood on 2006-07-26
I downloaded the Alternative ISO, burnt it and installed. Essentially, it leaves me where I started. I ran dpkg-configure -a. This seemed to reduce the number of errors and failures at boot. However, my main problem remains: no xserver. At startup i82365 fails to load. Also, failed to load lib/modules 2.6.10-f-386. I'm not too sure about the accuracy of that last part, the lines are difficult to read as they flash past. 
Any ideas why this/these won't load? Or how to repair the installation? The Alternate cd has a "Repair damaged installation" option that I tried to use but before long it leaves me baffled and nervous about wrecking the installation totally.

---

### Post by manish_jain on 2006-07-26
u can press Ctrl+Alt+F11 / Ctrl+Alt+F10 to get a list of server errors and init outputs. ( one of them is also shown by the cmd dmesg).

that can help troubleshoot the problem

---

### Post by Foxblood on 2006-07-26
I tried the Ctrl+Alt+F11/F10 to no avail. Nothing happens. dmesg got results but nothing really relevant. I searched around the forums and tried dpkg-reconfigure xserver-xorg and dpkg-reconfiguregdm. The attempt to reconfigure the Gdm gave me this;
Gtk-Warning cannot open display at /usr/share/per15/Debconf/FrontEnd/Gnome.pm line 54
I don't know if that's helpful or not.

---

### Post by Foxblood on 2006-08-04
Sometimes, things work out. I got so frustrated with the whole thing that I decided to go with a different brand of Linux. Gentoo, Fedora, Dream,Yoper and another one whose name I forget. None would work. In desperation, I again tried to install Dapper. All went well until I rebooted. No Dapper. But more importantly, no Lilo. The pc booted straight into XP. So, I searched the forums and read a bit of advice about booting from the xp install disc and running repairmbr or something similar by rebooting and when the "hit any key to boot from cd " hit a key. I rebooted with the disc in and when the "Hit any key" came up I didn't and was amazed to see grub materialise. 
Now, I just leave the disc in and I can dual boot. Ok, it's far from ideal, but at least I have a functional dual-boot pc. I've learned an awful lot these last few days and no doubt I'll learn more.

So, I'd like to thank Kapre, Herman, manish_jain and. most of all,tonyr. 
I truly appreciate your efforts and I know, sooner or later, I'll be talking to you again.

---

