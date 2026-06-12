---
title: "Dual Boot Broken After Upgrading to Ubuntu 10.04 [URGENT]"
date: 2010-04-12
forum: Installation &amp; Upgrades
---

### Post by bird1992 on 2010-04-12
I just upgraded to Ubuntu 10.04 from 9.10 and now my Windows XP will not boot from grub.  It shows up on the grub boot list but when I select it, all I get is a black screen.  It worked perfectly just minutes before the upgrade, but now I cannot use windows, which I need really badly at this point.

---

### Post by Slim Odds on 2010-04-12
There are no urgent messages in these forums

Some more info about the process that you used might help

---

### Post by pastalavista on 2010-04-12
10.04 is still in beta. A beta tester should expect things like this.

---

### Post by bird1992 on 2010-04-12
there is just a problem with the grub2 I think, but I don't know how to get it to recognize my windows partition.  Ubuntu works fine, but I can't boot windows.

---

### Post by drreed on 2010-04-12
It sounds like you ran the upgrade (which I haven't done yet) and yyou chose the option to install grub on your mbr of the drive where you boot windows, right?

What you should have done, was leave it alone, and after the install, boot from a live CD, mount the linux root partition, and manually create your grub entry following procedures specific to grub 1.97, found elsewhere in excruciating detail in this forum. 

But that's besides the point. Don't feel bad, I've done it too.

Please verify this procedure with others before doing it! I've mangled a few windows installs fooling around with grub! :P

**before you do the stuff below, try updating grub, I thinks it's $grub-update or something like that. It's supposed to scan your system for other operating systems and add them to the menu.**

I booted from a windows cd, got a DOS prompt, and ran fixboot and fixmbr (the order you run them is important so double check that)

That will get windows back unless there's something else wrong.

About the time you become comfortable with all things grubby, they'll change it to grub3 and you'll start all over again with the next upgrade. (lol - thats what happened to me, I thought I was an expert on the old grub, then it changed)

---

### Post by bird1992 on 2010-04-12
Thanks!
update-grub does not help.
which windows cd do I need? I have the recovery one, but that does not give me a dos prompt.

---

### Post by JoseHChicago on 2010-04-12
This happened to me as well when i upgraded to 9.10 last time. I'm afraid it will happend again when I upgrade to 10.04
 
My computer had a 'Windows Restore Partition' that was still good. So I restored my windows and it restored the windows loader - but Grub2 was gone.

Then I reinstalled GRUB2 via the Ubuntu Live CD. Grub was back and it also found by Windows install.
 
I've noticed that Windows 7 and Ubuntu don't play nice on the same disk using double book with Grub2. Sometimes my Windows 7 restarts while i'm booting up and I have to restart & reboot like 3 times before it loads again.
 
Good luck.

---

### Post by drreed on 2010-04-12
> **bird1992 said:**
> Thanks!
update-grub does not help.
which windows cd do I need? I have the recovery one, but that does not give me a dos prompt.

The regular one. (I'm a little ashamed to admit it, but I've never used a recovery disk, should have a few timesm but I hv no idea what it does)

At some point in the beginning of install you can choose exit or dos prompt. It might even be 'cancel install'.

It'll put you at a DOS prompt where all you'll have are a few basic DOS commands. It'll probably say "C:\"

AT that prompt do it. Make sure to verify which one you should do first (search around, it's here somewhere) I think it's fixmbr then fixboot. Double check.

That will rewrite your windows boot record, and I seem to recall will also break grub. When you reboot you may go straight into windows. If so, you'll need to re-install grub when your crises is over. (just boot your liveCD and run your grub-install manually from the command line. That's always worked for me. Well, almost always.:confused:

---

### Post by oldfred on 2010-04-12
This is the standard set of windows fixes that I and many others post:

Always run chkdsk and run again until there are no errors, that may be all that is required
How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
Repair often does not work, some say run 3 times others recommend the command line bootrec.exe

You will need to boot with your Vista/Windows 7 installation disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands: 
BootRec.exe /fixmbr   #updates MBR master boot record  do not run if you still want grub
chkdsk /r 
BootRec.exe /FixBoot  #updates PBR partition boot 
BootRec.exe /ScanOs 
BootRec.exe /RebuildBcd

---

### Post by PRC09 on 2010-04-13
Before you use the RECOVERY DISKS or the RECOVERY Partition be sure that you have everything off the drive because the recovery process WILL restore your machine to factory default....Minus your data.......You will need an XP install disk to fix the boot problem and then the Ubuntu disk to install Grub...... I also think the command to repair XP from repair console are fixboot and fixmbr......

---

### Post by oldfred on 2010-04-13
I missed the XP and posted instructions for Vista/7. While similar they are different:

To run the Recovery Console from the Windows XP startup disks or the Windows XP CD-ROM, follow these steps:
1.    Insert the Windows XP startup disk into the floppy disk drive, or insert the Windows XP CD-ROM into the CD-ROM drive, and then restart the computer.

Click to select any options that are required to start the computer from the CD-ROM drive if you are prompted.
2.    When the "Welcome to Setup" screen appears, press R to start the Recovery Console.
3.    If you have a dual-boot or multiple-boot computer, select the installation that you must access from the Recovery Console.
4.    When you are prompted, type the Administrator password. If the administrator password is blank, just press ENTER.
5.    At the command prompt, type this commands one at a time.

FIXMBR  C:
FIXBOOT  C:
COPY [CDDRIVE]:\I386\NTLDR  C:\
COPY [CDDRIVE]:\I386\NTDETECT.COM  C:\
or:
Can you boot into Ubuntu? If so you can mount your Windows drive and navigate to C:\windows\ServicePackFiles\i386 folder and copy
ntdetect.com and ntldr to root of C:\.

---

### Post by bird1992 on 2010-04-13
Thank you guys so much! I was so distraught yesterday about this. Sorry about calling it urgent, i have windows working (with all data in tact), but now I need to install grub so how exactly do I do this. I know I boot with the live cd, but then how do I mount linux and everything else so that I don't lose windows again.

---

### Post by oldfred on 2010-04-13
As an upgrade did it keep grub legacy (0.97) or did you convert to grub2? 
The instructions are different and if you follow the wrong instructions it is even more difficult to recover.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by bird1992 on 2010-04-16
I got the windows partition back and just doing a fresh install of ubuntu. Thanks guys! You can mark this as solved.

---

### Post by bird1992 on 2010-04-16
Dual boot now working perfectly :) and I really like 10.04 the startup and shutdown times are incredibly fast!

---

### Post by Zintha on 2010-04-16
I had the same problem

Fixed by booting XP disc, using Recovery console and FIXBOOT C: was all I needed.

---

### Post by donw35 on 2010-04-30
Did the upgrade on my dual boot machine, after upgrading to 10.04. Windows 7 64bit no longer worked, easyly fixed using this process below.
Boot with Windows 7 DVD and select repair command prompt.
BootRec.exe /FixBoot #updates PBR partition boot
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd

---

### Post by sunewbie on 2010-09-26
> **bird1992 said:**
> I just upgraded to Ubuntu 10.04 from 9.10 and now my Windows XP will not boot from grub.  It shows up on the grub boot list but when I select it, all I get is a black screen.  It worked perfectly just minutes before the upgrade, but now I cannot use windows, which I need really badly at this point.


Hi,

I have not upgraded to 10.04 but i faced the problem when i upgraded grub.

here are some tips which i hope they will work in 10.04. It worked in 9.1 karmic koala 

This works if you have installed win XP first, then ubuntu and later upgraded the grub. Ubuntu works but when you select XP grub says 

"no such signature
press any key to continue"

open grub2 via gedit - sudo gedit /boot/grub/grub.cfg

(if you cannot edit, try this

in the terminal i.e. applications --> accessories --> terminal 

type (or copy paste --> right click menu works or do ctrl +shift + v )

ls -l /boot/grub/grub.cfg

if you see

-r--r--r--

It is read only. Every time Grub2 updates the file it changes its permissions into read only.

Type

sudo chmod 644 /boot/grub/grub.cfg

which changes the permissions to

-rw-r--r--r--

now type

sudo gedit /boot/grub/grub.cfg   

)


just add this line at the bottom

--------------

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (loader) (on /dev/sda1)" {
	set root=(hd0,1)
	chainloader +1
}

--------------

if you want to make XP as default OS to boot then

Copy the above lines to the top so that the xp is the first option e.g.

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (loader) (on /dev/sda1)" {
	set root=(hd0,1)
	chainloader +1
}

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-22-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	linux	/boot/vmlinuz-2.6.31-22-generic root=/dev/sdb9 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-22-generic
}

Tip: 

you can change title in the quotes i.e. "Microsoft Windows XP Professional (loader) (on /dev/sda1)" to anything you like, but let it be sensible

source:
[http://ubuntuforums.org/showthread.php?t=1200600](http://ubuntuforums.org/showthread.php?t=1200600)

---

