---
title: "dual boot problem with windows xp"
date: 2006-10-30
forum: Installation &amp; Upgrades
---

### Post by kadaaz on 2006-10-30
Hello,
New to Linux.
I just installed EdgyEft on my laptop. I can no longer access my xp operating system. I get this when I try to acces xp: "Error 29: Disk write error"
I was very careful about which partition to use. 
Is there a way to solve this without having to reinstall windows?
Any help would be greatly appreciated.

---

### Post by blind0wl on 2006-10-30
What configuration are you running...ie, do you have two seperate hard drives with an OS on each or have you just partioned a single HDD.  Also when installing do you remember whether you installed grub on the MBR or on the OS partition?  If you installed your grub on the MBR, post the contents of /boot/grub/menu.lst

Blindy

---

### Post by Herman on 2006-10-30
First, I agree with what Blindy had to say, (above). :D

In the meantime, if you are in a hurry to boot Windows and Ubuntu for now, you can use a Super Grub Disk, it is free software, and only a 541 kb download from [http://adrian15.raulete.net/grub/tiki-index.php](http://adrian15.raulete.net/grub/tiki-index.php)
You can do quite a lot with Super Grub Disk besides at least booting Windows and Ubuntu for now. Super Grub Disk can be used to install Grub to MBR for you  presuming you want that, or repair your old Windows boot in MBR for you. Is is also useful for accessing Grub's [COLOR=#33ff33][Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli")[COLOR=Black], which can be useful for testing and troubleshooting.

Here's what the latest Gnu Grub Manual says about error 29, [/COLOR][/COLOR]
> 29 : Disk write error This error is returned if there is a disk write error when trying to write to a particular disk. This would generally only occur during an install of set active partition command.         Please keep us posted on how you get along. :D

Regards, Herman :D

---

### Post by kadaaz on 2006-10-30
Thanks blindowl and Herman for answering so quickly. I am so new to linux that it took me forever to find the contents of the boot/grub/menu.lst but I did. I am pretty sure I installed grub on the MBR.:

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=1e5d6f5b-f875-48c1-bab9-7747d99c2cde ro
# kopt_2_6=root=/dev/sda2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda2 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda2 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows XP Media Center Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by blind0wl on 2006-10-30
Great, can you now post the output of

```
fdisk /dev/hda
```

Type 'p' when you get the menu...It should look like this

```
fdisk /dev/sda

The number of cylinders for this disk is set to 1044.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): p
```

```
Disk /dev/sda: 8589 MB, 8589934592 bytes
255 heads, 63 sectors/track, 1044 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         997     8008371   83  Linux
/dev/hda2             998        1044      377527+   5  Extended
/dev/hda5             998        1044      377496   82  Linux swap / Solaris
```

Of course it wont look exactly like that but just post whatever is in the above table.

I'd say, as Herman suggested it is a active partition problem

Cheers

Blindy

---

### Post by adrian15 on 2006-10-31
> **kadaaz said:**
> 
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
```

title		Windows XP Media Center Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```



```

title		Windows XP Media Center Edition
rootnoverify		(hd0,0)
chainloader	+1
boot

```

Can you try with this grub entry instead and tell us if you can boot windows right now?

adrian15

---

### Post by kadaaz on 2006-10-31
Hi Adrian15,
You said to try a Grub entry.
Please tell me how to do that. Where do I go to type the code?

BlindOwl,
How do I get the output you suggested I post?

fdisk /dev/hda


I tried booting with the Master Grub disk Herman suggested but got the same error 29.

---

### Post by randell6564 on 2006-10-31
> **kadaaz said:**
> ## ## End Default Options ##

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda2 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda2 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows XP Media Center Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1
I would be willing to bet that GRUB was installed onto your Ubuntu drive instead of to the MBR!
Do you have two Sata drives or one ide and one sata?  Linux will often only recognize the ide when trying to dual boot, and subsequently place GRUB to that HD.

---

### Post by kadaaz on 2006-10-31
Mine is a Toshiba Laptop with only one hard drive.

---

### Post by Zyphrexi on 2006-10-31
oooh. I never heard of super-grub. Man that would have helped me out a couple years ago when I wrote over my mbr. ;P

---

### Post by Herman on 2006-10-31
> oooh. I never heard of super-grub. Man that would have helped me out a couple years ago when I wrote over my mbr. ;P Yes, Super Grub Disk is now helping a lot of people solve most booting problems easily and quickly.

If Super Grub Disk can't boot Windows for you, kadaaz, it might not be a Grub problem, but you might still be able to use Super Grub to fix it. But first we need to get some more information.
Try 'sudo fdisk -lu' instead of 'fdisk /dev/hda' then, and see if that one will work better for you, ```
sudo fdisk -lu
``` If we can see the output of that, we might see how to help you better. Super Grub Disk has the function of making 'active' a partition, it that is the problem. But it might be some other problem. We have not properly identified the problem yet.

If even Super Grub can't boot Windows, you may be able to boot it with a Windows XP boot floppy disk, or a boot floppy disk for your version of Windows. You can make one of those yourself, by following these instructions, [How to Create a Boot Disk for an NTFS or FAT partition in Windows XP.]("http://support.microsoft.com/kb/305595/EN-US/")
Those are the most powerful method for booting Windows that I know of. They will boot Windows even if the Windows boot sector is corrupt, and you have no boot.ini file.

Regards, Herman :D

---

### Post by kadaaz on 2006-10-31
Here's what it looks like


sudo fdisk -lu

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   126126314    63063126    7  HPFS/NTFS
/dev/sda2   *   126126315   229488524    51681105   83  Linux
/dev/sda3       229488525   233922464     2216970    5  Extended
/dev/sda4       233922465   234436544      257040   88  Linux plaintext
/dev/sda5       229488588   233922464     2216938+  82  Linux swap / Solaris

---

### Post by confused57 on 2006-10-31
> **kadaaz said:**
> Hi Adrian15,
You said to try a Grub entry.
Please tell me how to do that. Where do I go to type the code?


Until Herman gets back(by the way, you probably have the most knowledgable grub expert helping you in Herman), here's how to try adrian15's entry:
Open a terminal(Applications---Accessories---Terminal), enter the following one line at a time, press "enter" after each line:
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
gksudo gedit menu.lst
```
If you type the commands(best to copy & paste), menu.lst is short for menu.list, not menu.first.
You can just add the Windows entry to the very end of the file, without deleting the Windows entry you already have...if it doesn't work, you can just go back into the menu.lst file and delete it.  At the grub menu during bootup, try the 2nd Windows entry to boot from the added entry.

---

### Post by kadaaz on 2006-10-31
Thanks Confused57. I had just figured out that terminal was where I had to go in order to answer the questions these guys were asking me. I made a few mistakes typing the wrong thing but got it done after a while.

---

### Post by dhawk312 on 2006-10-31
ive been having the same problem...i posted here [http://www.ubuntuforums.org/showthread.php?t=290184](http://www.ubuntuforums.org/showthread.php?t=290184)

here is my "sudo fdisk -lu" output

Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders, total 117210240 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1              63   116680094    58340016    5  Extended
/dev/hda4       116680095   117210239      265072+  82  Linux swap / Solaris
/dev/hda5   *         126    31680179    15840027    7  HPFS/NTFS
/dev/hda6        31680243    73690154    21004956   83  Linux
/dev/hda7        73690218    95345774    10827778+  83  Linux
/dev/hda8        95345838   116680094    10667128+  83  Linux

---

### Post by Herman on 2006-11-01
sudo fdisk -lu (kadaaz)

```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes

Device_______Boot__________Start___________End__________Blocks______Id______System
/dev/sda1____________________63______126126314______63063126_______7______HPFS/NTFS
/dev/sda2______*______126126315______229488524______51681105______83______Linux
/dev/sda3_____________229488525______233922464_______2216970_______5______Extended
/dev/sda4_____________233922465______234436544________257040______88______Linux plaintext
/dev/sda5_____________229488588______233922464_______2216938+_____82______Linux swap / Solaris
``` Well, kadazz, I can see from that that you clearly have a bootable flag alright, it's on one of your Linux partitions at the moment, probably because that's the partition you had booted at the time. Grub can normally shift that with the 'makeactive' command (set active).

I don't see any partition overlap, where one partition could be occupying some of the first sectors of the next, that can interfere with booting.  
The only thing there I don't know anything about is your /dev/sda4, which is called a Linux plaintext type partition, I haven't seen one of those before. It probably has nothing to do with your booting problem, but just in case, can you explain a little more about that one to me please?
Basically, that looks okay, and thanks for posting that for me. :D

The next thing you could try is booting your Windows from Grub's [command line interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli"), (press your 'c' key from your grub menu). Here's how to boot Windows from grub's command line, [click here]("http://users.bigpond.net.au/hermanzone/p15.htm#How_To_boot_Windows_using_GRUBs_CLI"). 
I will be interested to find out if you can boot Windows from the command line or if not, what error messages you will get. Will you get an error message after the 'makeactive' command? Grub's command line is useful because it's more interactive and gives immediate feedback.

Actually, it is adrian15 who is much more advanced with Grub commands than I am, I see that he has asked you to test basically the same series of commands without the 'savedefault' and 'makeactive' commands. You could test those by editing your menu.lst, but it would be easier to test them by running them from the Command Line.
adrian15 might have though of something I hadn't though of yet, the 'savedefault' command can be safely omitted. It just causes Grub to write to a special file in the boot directory called 'default', which is how Grub remembers the operating system you want booted by default. I seem to remember now, getting a similar error when tying to [make my own Grub CD.]("http://users.bigpond.net.au/hermanzone/p15.htm#HOW_TO_MAKE_A_GRUB_CD")
Grub gave me an error because it couldn't write to the CD, so I had to delete all the 'savedefault' commands from the CD version of menu.lst.
Hmmm :-k. I would need time to test that and see if it's error number 29 for sure or not, my memory is not good enough. Hmmm :-k

That's all for now, Regards Herman :-D

[dhawk312]("http://www.ubuntuforums.org/member.php?u=103194") 					, I'll get to your problem, but I just need a little sleep first, then I'll 'coffee up' and look at yours. I'll be back soon, unless you solve it or get help from someone else in the meantime.

---

### Post by kadaaz on 2006-11-01
Thank you all soo much for wasting your time with me. I really appreciate it.
Herman, I will try what you said later on today after work.
I will also do what adrian15 asked me to try. The only reason I didn't give that a shot was that I didn't know where to find the info. Now I know and I'll post it later.:-D

---

### Post by Herman on 2006-11-01
I don't consider it a waste of time at all, it's my hobby and I love it. Thank you for your patience and perseverance, you are doing great! I'm very interested to find out what's causing this and helping you solve it. It may help someone else who may happen to get the same error some day. Grub error 29 is not so common. 
I will have more time on the weekend too. As soon as I get time I'll try some experiments to see if I can get my computer to produce the same error number. 
I'm wondering if that 'linux plaintext' partition might happen to have Grub installed in it, and Grub can't write to that maybe, so if omitting  the 'savedefault' command fixes it, then that might be why.

Regards, Herman :D

---

### Post by kadaaz on 2006-11-01
Thanks Herman, you're a kind man.
I have just a minute right now and rand the grub commands Adrian15 suggested I ran, without the "savedefault" and "makeactive". Result:

Starting up....
Invalid System Disk
Replace the disk, and Then press any key.


I pressed a key. A window opened: Express Media Player.
I was asked to chose a language, after that it said "please insert the disk" then nothing. I Had to power off to restart.

I don't know if all this helps.
I got to run but I'll have more time in a couple of hours.
Peace!!

---

### Post by kadaaz on 2006-11-02
No luck with booting from Grub's command line.
I am having a lot of fun using Ubuntu though and starting to wonder if I actually want to get back to Windows.;)

---

### Post by Herman on 2006-11-02
>  I pressed a key. A window opened: Express Media Player.Aha! That's your problem! :D

Would this be a Toshiba M35-s456 laptop, or similar model? The 'Express Media Player' partition, conflicts with GRUB, as it uses the first track of the hard disk.  :(
Grub needs the first 15 sectors following the MBR for stage1_5 to be installed there.  Normally nothing uses the first track of the hard disk except bootloaders. The Express Media Player is not aware of or has chosen to ignore this rule or convention. This is an issue I have read about elsewhere here in Ubuntu Web Forums.

Does Super Grub Disk not boot Windows for you either? Have you tried it?

If not, and if you still want Windows, you will probably need to consider trying to restore your old Windows bootloader code in your MBR and hopefully that will make everything work the way it used to again.
Then, you will have to use Super Grub Disk to boot Ubuntu each time instead, I am afraid, if you don't want to delete your 'Express Media Player' from your first track of your hard disk. 

You may want to restore the Windows Bootloader with Super Grub Disk. [[FONT=Bitstream Vera Sans Mono]English Super Grub Disk[/FONT]]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#English_Super_Grub_Disk_Menu")-->[[FONT=Bitstream Vera Sans Mono]               Windows[/FONT]]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#Windows") --> [Fix Boot of Windows]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#Fix_Boot_of_Windows")

There are lots of other ways to restore the Windows bootloader code to MBR as well. See this web page for more if you need to, [Un-install Page]("http://www.users.bigpond.net.au/hermanzone/p18.htm").

Let me know how you get along, and good luck with it, I hope your 'Express Media Player' will still work alright. I'll do a little searching for more info on this subject for you, and let you know as soon as I find something helpful.

EDIT: On second thoughts, maybe it will be best to just wait and see what we can dig  up here. Don't do anything too hasty until we find all the info we can.

EDIT TWO: Here are a few links I have found on the subject by searching Ubuntu Forums so far:
 [http://www.ubuntuforums.org/showthread.php?t=168564&highlight=Express+Media+Player](http://www.ubuntuforums.org/showthread.php?t=168564&highlight=Express+Media+Player)
[http://www.ubuntuforums.org/showthread.php?t=165028&highlight=Express+Media+Player](http://www.ubuntuforums.org/showthread.php?t=165028&highlight=Express+Media+Player)
[http://www.ubuntuforums.org/showthread.php?t=3306&highlight=Express+Media+Player](http://www.ubuntuforums.org/showthread.php?t=3306&highlight=Express+Media+Player)

I think we still need to learn more before we do anything, I'll try some googling next...
[http://eu.computers.toshiba-europe.com/cgi-bin/ToshibaCSG/jsp/seriesHomepage.do?service=EU&SERIES_ID=113430&banner_id=topbanner_SATP100_DUO_OCT06_TEG](http://eu.computers.toshiba-europe.com/cgi-bin/ToshibaCSG/jsp/seriesHomepage.do?service=EU&SERIES_ID=113430&banner_id=topbanner_SATP100_DUO_OCT06_TEG)
[http://forums.computers.toshiba-europe.com/jive3/thread.jspa?threadID=14395](http://forums.computers.toshiba-europe.com/jive3/thread.jspa?threadID=14395)
The install instructions for Express Media Player given in the above link's sub-links say to make a 100 to 150 mb partition at the end of the hard disk to install the player to. I presume that's what your 'linux plaintext partition would be, I think yours would be 250 MB or so. Perhaps I am wrong about the Express Media Player being in the way.
But why would Express Media Player try to boot when you did the following,
> I have just a minute right now and rand the grub commands Adrian15 suggested I ran, without the "savedefault" and "makeactive". Result:

Starting up....
Invalid System Disk
Replace the disk, and Then press any key.


I pressed a key. A window opened: Express Media Player.
I was asked to chose a language, after that it said "please insert the disk" then nothing. I Had to power off to restart.
 That would seem to me to imply that your Express Media Player has code in your Windows boot sector. :confused:

What happens when you try adrian15's commands but just omit the 'savedefault' and leave in the 'makeactive' command?

Regards, Herman :D

---

### Post by kadaaz on 2006-11-02
Hello Herman,
I have the feeling that "Express Media Player" is the culprit.
My computer comes with it pre-loaded and I am definitely not fond of it. I don't even use it.
I have another desktop pc at home with Windows XP (without Express Media) and Ubuntu co-existing peacefully:) .
I don't know if I should start from scratch on my Toshiba Satellite A105 series by using the recovery disk it came with, uninstall Express Media Player and re-install Ubuntu. Since this is a new computer, I don't really have a lot of data to recover.
  "What happens when you try adrian15's commands but just omit the 'savedefault' and leave in the 'makeactive' command?"

When I try booting this way, I get the same Error 29: Disk write error.

I will check the other links you giving me later.


Thanks for your help.

---

### Post by kadaaz on 2006-11-02
I am at work without my laptop. Found this site through Google: [http://www.crhc.uiuc.edu/~mjmille2/howtos/dual-boot-linux-and-windows/]("http://www.crhc.uiuc.edu/~mjmille2/howtos/dual-boot-linux-and-windows/")
I may give it a shot when I get home.

---

### Post by Herman on 2006-11-02
kadazz,
You can try [http://www.crhc.uiuc.edu/~mjmille2/h...x-and-windows/]("http://www.crhc.uiuc.edu/%7Emjmille2/howtos/dual-boot-linux-and-windows/") if you want, but several people have had difficulties and frustrations trying to follow that how-to. It might work okay for you. 

If you do decide keep trying with Grub and spend the two hours or so to back up and re-install completely, but without the "Express Media Player" if it comes to that, everything should work fine. (Then, you can bet that someone will come along with a solution where one or two quick commands would have fixed it in less than thirty seconds).
I don't want to be wasting too much of your time with troubleshooting and experiments either, when another way might be faster. I hate to give up and admit defeat though.
If I had the a Toshiba laptop myself that I could investigate and test I would have a much better chance of solving the problem from my end, and probably I'd already know all about it.

I succeeded in producing the grub error 29 with my grub CD making efforts. 
With the 'savedefault' command and no 'default' file, I get Grub error 15: file not found, when attempting to boot from the CD.
If I include a copy on my /boot/grub/default file in the CD, I get grub error 29: Disk write error, because the CD can't be written to like a hard disk. I can't see anything that has in common with your problem though.

Well, it's your time and your computer, you should decide what you think will be best for you. I'll keep working on it for a while longer and see if I can find out anything more in the meantime.

Regards, Herman :D

---

### Post by kadaaz on 2006-11-02
[I]"I succeeded in producing the grub error 29 with my grub CD making efforts.
With the 'savedefault' command and no 'default' file, I get Grub error 15: file not found, when attempting to boot from the CD."[/I]

I got the same results when I tried to boot from the Super Grub Disk.

I am going to continue and try different solutions before I resort to re-installing

---

### Post by adrian15 on 2006-11-05
> **Herman said:**
> Aha! That's your problem! :D

Would this be a Toshiba M35-s456 laptop, or similar model? The 'Express Media Player' partition, conflicts with GRUB, as it uses the first track of the hard disk.  :(
Grub needs the first 15 sectors following the MBR for stage1_5 to be installed there.

Hey Kadaaz try #8 on [Super Grub Disk FAQ]("http://adrian15.raulete.net/grub/tiki-index.php?page=EnFaq") then.

adrian15

---

### Post by kadaaz on 2006-11-06
A heartfelt thanks to all of you for your interest and help.
I decided to re-install ubuntu and get rid of windows xp on my laptop.So.. no need to dual boot on this computer right now.

After "test-driving" it for a week, I found that Ubuntu did everything I wanted my computer to do, plus the learning potential here is tremendous and challenging.
I have been reading and trying all sorts of things that I was never tempted to do with Windows.

Besides I have a desktop at home with the 2 Operating systems co-existing peacefully.

---

### Post by Harmshi on 2006-11-07
For the people who still run in to this problem:

I've had the same Grub error (29). This may be caused by a BIOS setting of your system. Some BIOSes have an option for boot-record security/protection. If this option is enabled, Grub cannot write, and produces error 29: disk write error.

After disabling boot-record security/protection in the BIOS, I was able to boot Windows XP (NTFS) AND Ubuntu without any problems!

Hope this helps for some...

---

### Post by ncc386 on 2006-11-07
You can also fix Windows XP by booting from Setup disks or an identical version Setup CD-ROM, dropping to the Recovery Console, and running "fixmbr". You can also type "help" to see a list of other commands that can help get Windows up and running again. Sorry I can't be of any help as to how to fix Ubuntu and Windows dual-booting.

---

