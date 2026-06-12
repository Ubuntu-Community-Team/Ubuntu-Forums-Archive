---
title: "Reinstall Windows XP Boot Manager?"
date: 2005-04-05
forum: Installation &amp; Upgrades
---

### Post by sfdxsm on 2005-04-05
I apoligize as I saw a similiar thread below but it did not answer my question.

This is my second round with Ubuntu as before I formatted I was running the previous 4.x build.

My only other experience was a one stop and my system dived test of RedHat right before it moved to the Fedora Project. One of the neat features about that build was the support of RPM packages that basically installed themselves similar to Windows. I have a decent background with computers in general as well as programming so this time around I like to build the programs myself.

At any rate with RedHat, when you would select to load the GRUB Boot Manager to a Floppy disk, it would leave your Windows Boot Records alone. Thus the system would automatically boot to Windows UNLESS I popped in the boot disk for GRUB.

On this round I loaded GRUB during installation to a floppy expecting the same outcome. Not so as I found that when the system loads it cannot find any operating system at all. I was a little disappointed (and scared at first) that GRUB, although loaded to a floppy erased any boot info along with it. So without this "trusty" floppy (I'm moving it to a CD as I do not trust floppy drives anymore, lol) I have no system. 

GRUB just does fine by detecting Ubuntu, Ubuntu "safe mode" as it lists it, and my Windows XP. This is a single HD (NTFS) split up using Partition magic 8. Although it doesn't hurt me to leave the disk in, I'd rather have had the system stay in tact without any hint of a Linux install. (sometimes my Mom or g/f will use my system and they become very confused.)

Is there any way to return the system to the original boot record WITHOUT a reinstall of both OS's and/or a format? The only XP disks I own do not allow a simple OS reinstall. They are recovery disks and will only format the system.

Also, is there a post or specifics to removing a Linux install properly? My only method usually (when I still had my normal boot record and the GRUB to load Linux on Floppy) was to simply delete the partition and be done with it.

Thank you for your help.

---

### Post by bored2k on 2005-04-05
The more intelligent sollution is this: 
1) Install GRUB in your computer.
2) Install grubconf (graphical interface to something newbies should stay away from)
3) Make Windows boot first.
4) After doing so, clicking on hide the menu. This will (duh!) hide the menu, only showing a small text for 3 seconds, that will only show the menu by pressing escape. I havent done this in a while but I think that is how it works.

---

### Post by alastair on 2005-04-05
You used to be able to rewrite the MBR (boot record) via :

fdisk /mbr

So, if you can boot DOS (for instance), this will rewrite the MBR. However, XP might be different.

I recently installed Hoary on a friends desktop and used "expert" mode. I wrote GRUB to a floppy and it works fine (didn't touch the hard disk MBR).

---

### Post by sfdxsm on 2005-04-05
thank you for your reply but this mirrors another person's post.

We do NOT want GRUB unless we specifically boot to it. (We referring to a post below mine) I understand that many of the visitors here prefer or have a bias against Windows so consider using the word intelligent relevant to the person and situation. Thus, my situation is I use Linux from time to do, and sometimes I remove it all together. In return I'd like my system to operate as it did before.

I am also still curious to why GRUB even when directed to use a floppy disk ERASED the original boot record. I could see if GRUB was placed onto the system physically (in the sense of its files) but it was set to a floppy. So without it, the computer doesn't even HAVE a boot record. That to me, sounds like a bug IMO. (and reminds me of MS tactics which many push to eliminate with Linux)

I am still curious to whether there is a why to restore the original configuration and only use the floppy disk as a boot loader when wanted without a reinstall or reformat of Windows. Also, if anyone has any info on GRUB to Floppy but erasing any boot record, post away.

Thanks for that tip though. It is an idea.

---

### Post by sfdxsm on 2005-04-05
[QUOTE=alastair]You used to be able to rewrite the MBR (boot record) via :

fdisk /mbr

So, if you can boot DOS (for instance), this will rewrite the MBR. However, XP might be different.

I recently installed Hoary on a friends desktop and used "expert" mode. I wrote GRUB to a floppy and it works fine (didn't touch the hard disk MBR).[/QUOTE]

that would be the situation I am looking for. So I either edited a setting I shouldn't have or there is a bug in the steps I took.

---

### Post by stepper on 2005-04-05
If u need grub boot floppy u can get the images from [here](http://www.zevils.com/~matthewg/grub/) . Be sure to use a good floppy and use rawrite to write the image to floppy.

---

### Post by sfdxsm on 2005-04-05
It seems in my install I may have set the Linux partition to be bootable and some how this set my windows partition to be inactive. My Linux partition was reading as bootable, my windows partition had no status. Using Partition Magic 8, I set the windows partition to Active. Now all is happy. I assume this was my error in setup so be careful.

---

### Post by SquireSCA on 2005-04-07
Boot from the WinXP CD, select "recovery console".

It will dump you at a command prompt, and you just type "fixmbr" and it will rewrite the WinXP boot sector.

Reboot into WinXP goodness.

---

### Post by Raven-sb on 2005-04-08
I've read that using fixmbr with windows xp is dangerious as it can stuff up your harddisk. Having said that I've found another method on a LUG mailing list  for getting Windoze up and running if you need it.

How to Unstalling linux and recover windows xp partition.

Anyways, here's the procedure:
1.Boot with the windowsXP cd
2.Follow through the prompts UNTIL you reach installation options (along
the way you will have the option to format your ext2 partition to
NTFS).  DO NOT USE THE "RESTORE USING PROMPT" OPTION UNLESS YOU ARE WELL
VERSED WITH THE COMMAND PROMPT AND LOOKING TO RESTORE FILES.  It
involves a long series of commands.  Choose to install a "new" copy of
Windows XP on C: instead.
3.DO NOT FORMAT C:  Just elect to install the "new" copy.  The option
will soon come along to restore the installation on c:.  Select that.
4. Sit back and wait a while, continuing to enter information as windows
requests.  You'll have only WinXP booting in no time.

Hope this helps,

Raven

---

### Post by emry on 2006-09-20
fdisk /mbr:
This option no longer works in Windows.  The last version it worked under was Windows 98.

fixmbr:
This option seems functional, however the recovery console is not a cooperative piece of equipment.  You must I repeat MUST install it after you install the OS, but before installing ANY real updates.  You cannot allow the update manager to do anything before installing it.

The reason is, that if the windows version on your hard drive does not return the exact same revision numbers as the version on the CD, windows will refuse to install the console at all.  It will claim that it would be dangerouse to do so.

Also, I am pretty sure I installed it on one of my systems, but the option went away after a few updates.

Windows XP doesn't make anything easy for you.

The last time I was in a mess where I legitimately had to rewrite the boot record, I had to tell lilo to do it.  Lilo has an option to "write a windows bootable boot sector."

XP is annoying enough that I would drop it all together if I didn't keep finding myself using different applications that are windows specific... Then there is the whole game issue.  I blame two factors: The developers who insist on developing for one platform, and myself for being to dependant on the games. ^_^

---

### Post by bigken on 2006-09-20
you can download the [xp boot]("http://www.microsoft.com/downloads/details.aspx?FamilyID=e8fe6868-6e4f-471c-b455-bd5afee126d8&DisplayLang=en") floppies i think its six in total this will allow you to go to repair console the commands are fixmbr then fixboot
then exit reboot the pc

---

