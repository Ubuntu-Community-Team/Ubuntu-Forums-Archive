---
title: "Can't dual boot XP and Ubuntu 11.04"
date: 2011-10-26
forum: Installation &amp; Upgrades
---

### Post by dkubarek on 2011-10-26
Hello all,
I've been trying to get Ubuntu and XP to work as a dual boot but I can't get the screen that allows it to appear.

I first installed XP pro sp3 and then Ubuntu wubi, uninstalled that and then installed 11.04 secured remix. I've tried using Boot-Repair, testdisk and Windows fixboot in the installer but all I end up with is one OS or the other. 

What can I post to help diagnose the problem? Thanks.

---

### Post by jnorthr on 2011-10-26
It may be that your master boot record has lost the plot, in that it does not know or remember which o/s's are installed. There is a tool called grub or version 2 of this is called grub2 which has the ability to refresh logic in the MBR. 

Is there any chance of reinstalling ubuntu again and avoid killing your windows partitions ? This might refresh the bootstrap with a smarter bootstrap that will able to detect your combination of o/s's and offer a reasonable startup screen where you can then select which o/s to boot into.

---

### Post by oldfred on 2011-10-26
Boot-repair can run the boot info script. Post the link it generates to document your system.

Wubi is just a file inside your Windows and boots from the Windows boot loader. When you installed the secured remix was that a full install to a partition? Boot script will show details.

---

### Post by critin on 2011-10-26
Try searching 

Sub-Forums : Tutorials & Tips

There's some good ones there on boot issues.

---

### Post by dkubarek on 2011-10-26
Here is the link to BootDisk. I ran it since then using the default setttings and got XP back in the process but this will help profile my system:

[http://paste.ubuntu.com/718069/](http://paste.ubuntu.com/718069/) 

Yes, I did first use the wubi that worked quite well but I wanted to try the full install. I booted from the disk at startup and installed using Ubuntu's disk partition slider tool. I originally tried to get it to install on Partition E, which I made using Windows partition tools in XP but it gave an error when I tried to install it. I think I wanted to make the partition primary NOT logical but I didn't know if you could have 2 primary partitions. 

It would be very easy to reinstall. I can see the Ubuntu partition in XP and format it but I'm not sure if that will help. If that's what needs to be done, it is very easy to do.

---

### Post by dkubarek on 2011-10-26
I have also tried a good bit of searching but it seems like each booting issue is unique. I tried reinstalling grub and updating it (I may have failed to do this correctly), Testdisk, Bootdisk and Fixboot and still can't solve it.

Thanks for looking into this. One thing that's possible is that the boot screen may be hidden. Bootdisk on default is supposed to fix this. If I can't solve it then I will go back to the wubi but I heard that disk utilization is horrible. One guy said 55% and I'm a neat and tidy kind of guy. 

Thanks for the replies! Been using Ubuntu for a few months and really love it.

---

### Post by critin on 2011-10-26
Boot-Repair is something I always install when trying a new distro.  It is a wonderful tool.  It comes with the new version, so keep a good live iso handy.

---

### Post by oldfred on 2011-10-26
Boot script as posted looks correct.

Do you get a grub menu? With Ubuntu & XP as choices? It looks like it should boot to the menu. Then other settings for video or system may be required.

---

### Post by dkubarek on 2011-10-26
I do not get a menu (that's visible at least) that lists the 2 OS like I did when I used the Wubi.

---

### Post by oldfred on 2011-10-26
Yes you should get a menu like the second one you had with wubi. The first was  a Windows choice.

Are you able to boot into Ubuntu at any point? Or what does happen when you boot.

---

### Post by dkubarek on 2011-10-26
When I boot I get the Dell BIOS prompts and then screens go blinky and right to the XP load screen. If I want to boot into Ubuntu I need to boot from the CD. I've been able to make Ubuntu boot from the hard drive but I always lose Windows in the process.

---

### Post by oldfred on 2011-10-26
If you can reinstall grub2's boot loader to the MBR with either Ubuntu liveCD or boot-repair then try this.

sudo update-grub

that should update the menu to include XP. The version of boot info should have been correct as it had grub2's boot loader in the MBR and the menu showed an XP entry so then the menu should appear. If it only finds one install of Ubuntu it by-passes the menu and you have to hold down shift from BIOS until menu appears to get a menu.

There may be a BIOS setting interfering but lets get Ubuntu booting first.
I turned on AHCI in my system and Ubuntu kept working but then I could not boot XP - but for me now that is no loss.:)

---

### Post by dkubarek on 2011-10-26
I'll try to reinstall grub and update it. 

What is the best way to do this? I boot from the Ubuntu disk and then should I run BootDisk with the default settings? 

Or should I use the terminal and this method?

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Thanks again!

---

### Post by dkubarek on 2011-10-26
I tried to reinstall grub before but I don't think I did it correctly after reading that post.

---

### Post by dkubarek on 2011-10-26
Oldfred, agreed about XP being crappy. I actually find it stable for what I do but it looks terrible and isn't user friendly like Ubuntu. I run a business and use Photoshop, InDesign and QuarkXpress for designing purposes and don't want to use Wine to do it. 

Soon I'll get a Mac, which I use at my full-time job, and I'll be rid of Windows altogether.

---

### Post by Theferris on 2011-10-26
If your still having trouble reinstall the whole thing but install ubuntu first. Its something to do with the boot loader being a microsoft one not an open one.

---

### Post by dkubarek on 2011-10-26
reinstalling everything is something I probably wont do. I have a lot of stuff on XP and I'm lazy.

---

### Post by Theferris on 2011-10-26
In XP if you right click on computer, go to properties, advanced, startup and recovery settings, you can edit the windows boot loader.
Im not to sure how it works but you should be able to add an entry for ubuntu.

you could try this
[http://bkpavan.wordpress.com/2008/04/02/how-to-boot-linux-using-windows-bootloader-xp/](http://bkpavan.wordpress.com/2008/04/02/how-to-boot-linux-using-windows-bootloader-xp/)

---

### Post by oldfred on 2011-10-26
You really should not  have to reinstall anything. Where are you at. Post new boot script.

---

### Post by dkubarek on 2011-10-26
I'm at work tonight on the East Coast in the States. 

I'll post script late tonight. How do I grab the booting script? Should I just click on the create Boot Info summary thing in Boot-Repair? If I use that program, I'll have to boot using the Ubuntu CD.

---

### Post by oldfred on 2011-10-26
You can use that program which used to download the script but I think it now includes the script or download the script and post results.txt here.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

This is another program that often lets you boot otherwise working systems.

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
[http://www.supergrubdisk.org/wiki/Main_Page](http://www.supergrubdisk.org/wiki/Main_Page)

---

### Post by dkubarek on 2011-10-29
I made some changes and problem is still the same.

When I installed the secure Ubuntu 11.04 32 bit disk it got stuck at the "saving logs" part of the install so I thought maybe my installation wasn't complete. I wiped that partition (but perhaps didn't get the scratch disk) merged it with my primary C drive and then did the Ubuntu reinstall with the AMD 64 bit install. (I have that 64 bit AMD processor). I tried Boot-Repair and StartUp-Manager and neither fixed it.

Here is my most recent log:
  	 	 	 	 	 	  [http://paste.ubuntu.com/722341/](http://paste.ubuntu.com/722341/)
 
Thanks for looking, everyone.

---

### Post by oldfred on 2011-10-29
Does Linux boot? That part of script does look ok. 

But you have installed the grub2 boot loader to sda1, it should never be installed to a Windows partition as that has to have Windows boot code. But NTFS keeps a backup, so if you only installed once you can restore form the backup.

Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:

This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

Your sda1:
> sda1: ___________________

    File system:       ntfs
    Boot sector type:  [COLOR=Red]Grub2 (v1.99)[/COLOR]
    Boot sector info:   [COLOR=Red]Grub2 (v1.99) is installed in the boot sector of sda1 
                       and looks at sector 550335792 of the same hard drive 
                       for core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.[/COLOR]
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM




---

### Post by dkubarek on 2011-10-29
Linux boots now but XP doesn't, so that makes sense what you said. If I do what that link says will that restore my Windows boot on sda1? When I installed Ubuntu fresh it booted OK but didn't give options for XP after several restarts. That's when I tried Boot-Repair. That didn't work either but I think the default is to install grub to sda1 but it has an option to force install to sda5.

In addition to following that link is there something I need to do to revert to the boot stuff I had on sda1? Thanks!

---

### Post by oldfred on 2011-10-29
If the backup boot sector is good that should restore booting to sda1. If you have run update grub then you may have to rerun it to make sure it sees XP.

```
sudo update-grub
```

---

### Post by dkubarek on 2011-10-29
"If the backup boot sector is good that should restore booting to sda1."

Is this an automatic process or do I need to do something?

---

### Post by oldfred on 2011-10-30
See post #23. Testdisk will tell you if it is valid or not. It may not tell you it is really the one you want. 

If not then you have to run Windows repairs. But often have to create a NTFS boot sector with testdisk as Windows will not repair a PBR with grub in it. It assumes it is not Windows.

---

### Post by dkubarek on 2011-10-30
I did the testdisk and didn't get an option to "backup BS". It said that my second boot sector was bad so I used the "org" option that copied the first boot sector to the backup, making them identical. 

What should I try next? Should I try to rebuild the BS in testdisk or use Windows to run Fixboot? Thanks again!

---

### Post by oldfred on 2011-10-30
If backup was bad, and you now copied the grub to the backup, you have what testdisk says is good, but grub in a NTFS partition will never boot windows.

I do not think Windows fixboot works on a NTFS partition with grub as it cannot even see it. I would use testdisk to create a NTFS partition , but that will probably not be bootable. Then add the boot flag to the partition and run Windows repairs.

If you get it fully repaired, go back into testdisk and copy the new correct bootsector to the backup.

Both chkdsk & fixBoot seems to modify PBR and each seems to depend on the  other, so you may have to run each more than once.

XP CD fixboot 
[http://www.ehow.com/how_4891476_reinstall-xp-bootloader.html](http://www.ehow.com/how_4891476_reinstall-xp-bootloader.html)
Description of the Windows XP Recovery Console for advanced users list of commands
[http://support.microsoft.com/kb/314058/](http://support.microsoft.com/kb/314058/)
To run the Recovery Console from the Windows XP startup disks or the Windows XP CD-ROM, follow these steps:
1.    Insert the Windows XP startup disk into the floppy disk drive, or insert the Windows XP CD-ROM into the CD-ROM drive, and then restart the computer.

Click to select any options that are required to start the computer from the CD-ROM drive if you are prompted.
2.    When the "Welcome to Setup" screen appears, press R to start the Recovery Console.
3.    If you have a dual-boot or multiple-boot computer, select the installation that you must access from the Recovery Console.
4.    When you are prompted, type the Administrator password. If the administrator password is blank, just press ENTER.
5.    At the command prompt, type commands one at a time.

FIXMBR  C:  #do not run if you still want grub in the MBR
[COLOR=Red]FIXBOOT  C:[/COLOR]
BOOTCFG  /rebuild  # rebuilds boot.ini
[COLOR=Red]chkdsk c: /r[/COLOR]

---

### Post by dkubarek on 2011-10-30
I'm not quite sure how to do this stuff.

"I do not think Windows fixboot works on a NTFS partition with grub as it  cannot even see it. I would use testdisk to create a NTFS partition ,  but that will probably not be bootable. Then add the boot flag to the  partition and run Windows repairs.

If you get it fully repaired, go back into testdisk and copy the new correct bootsector to the backup."

Are there any tutorials?

---

### Post by oldfred on 2011-10-30
You were just in testdisk. Click on the rebuidBS. Choose drive, Intel,  Advanced, Choose Windows partition, select Boot, Rebuild BS. To exit hit q multiple times. That should give you a basic NTFS Boot Sector.

I posted links & instructions on using Windows to repair the Boot sector above. Be sure to move boot flag with gparted first.

If all this is too much back up all your data and just reinstall. You will have to totally reformat partition to get it to be a NTFS partition with the boot flag so it knows where to install.

---

### Post by dkubarek on 2011-10-30
I was able to restore XP with fixboot. it gave me problems but I ran chkdsk and that fixed it. Now no Ubuntu :-(

What does this mean: "Be sure to move boot flag with gparted first."

It is easy to reinstall XP and Ubuntu but I don't want to do it and get the same problem. Is it possible with my setup to run them both without these issues. My XP install was recent and clean (from a low level format) and then I did Ubuntu and had immediate problems.

---

### Post by oldfred on 2011-10-30
So does XP boot normally? If you ran all the commands you ran fixMBR which just puts the Windows boot loader back into the MBR. You can easily restore the grub2 boot loader to the MBR and then should be able to boot both systems.

I do not think XP would repair itself without boot flag. Windows only boots using boot flag to know which partition is the active (boot flag) partition. Perhaps your repairs with testdisk moved it?

Your install was in sda6 and I would think that should not have changed.

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD/usb, Ubuntu install on sda6 and want grub2's bootloader in drive sda's MBR:
#Find linux partition, change sda6 if not correct:
sudo fdisk -l
#confirm that linux is sda6
[COLOR=Red]sudo mount /dev/sda6 /mnt[/COLOR]

#If grub 1.99 with Natty uses boot not root.
[COLOR=Red]sudo grub-install --boot-directory=/mnt/boot /dev/sda[/COLOR]

# If no errors on previous commands reboot into working system and run this:
sudo update-grub

That should make sure XP is in your menu.

---

### Post by dkubarek on 2011-10-30
Here is what that first command tells me:

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       33456   268733372    7  HPFS/NTFS
/dev/sda2           36283       38914    21131264    7  HPFS/NTFS
/dev/sda3           33456       36283    22705153    5  Extended
/dev/sda5           36030       36283     2028544   82  Linux swap / Solaris
/dev/sda6           33456       35778    18646016   83  Linux
/dev/sda7           35778       36029     2022400   82  Linux swap / Solaris

Do I have too many partitions or is that normal?

---

### Post by dkubarek on 2011-10-30
I did the commands you said and it returned no errors. I didn;t know about this one:

#If grub 1.99 with Natty uses boot not root.
[COLOR=Red]sudo grub-install --boot-directory=/mnt/boot /dev/sda[/COLOR]

I didn't know if it used boot or root so I ran it anyway.

Now, I get the grub dos menu when I start up. How can I advance that? Thanks again

---

### Post by dkubarek on 2011-10-30
if I can't find a fix I would really like to reinstall windows and then make a partition for Linux. I tried that at first and it gave me an error when I tried to use the advanced install option instead of the partition wizard. Ideally, I'd like for XP to boot up and have a button configuration (like prompt my boot menu with F12 and then go to the partition Ubuntu is on) or at least have the option like I did in the wubi.

Thanks again for all your help. I know I'm a noob.

---

### Post by dkubarek on 2011-10-30
Oldfred, because I was worried that all this partitioning and repartitioning I did was going to cause problems later I did a fresh XP install, leaving 30 gig for Ubuntu. I had couple file system errors but the file was in a torrent, highly suspect anyway.

I have a tutorial on the advance partitioning tool in Ubuntu and I'll try that.

[https://help.ubuntu.com/8.04/switching/installing-partitioning.html](https://help.ubuntu.com/8.04/switching/installing-partitioning.html)

If that doesn't work then I'll just use the wubi and use the space for storage.

I'll report back when I'm up and running. Thanks for all your patience and help.

---

### Post by oldfred on 2011-10-31
If you got grub menu what was your problem? That should have been the final solution to boot either Ubuntu or Windows?

---

### Post by dkubarek on 2011-10-31
I didn't realize that was the menu I was looking for. It was DOS and said "tab" for commands. There weren't many commands and none of them seemed correct. I assumed that I had to do something after that.

How could I have used that DOS menu to boot?

---

### Post by oldfred on 2011-10-31
That does not sound like the menu, but a grub issue on booting. Did you get either grub rescue or grub> ?

From grub rescue you can often manually boot if grub.cfg is correct. Otherwise it may just be a reinstall of grub to the MBR. Sometimes it is more complicated and you have to chroot (lots of commands but doable). Some then elect to reinstall Ubuntu as that usually takes less than an hour. (If you have good backups).

---

### Post by dkubarek on 2011-10-31
I'm not sure what menu I was in. It said Grub 1.99 and seemed like something I shouldn't be in. My computing skills are pretty basic though.

I did a fresh install and I'm back to the same place. Ubuntu boots and I get this when I do the boot scan.

[http://paste.ubuntu.com/724495/](http://paste.ubuntu.com/724495/)

Anything look out of the ordinary? I tried update-grub and that read linux and XP but when I restarted it gave me problems with hanging up. I used XP to do fixboot but I still got back to Ubuntu somehow..

---

### Post by oldfred on 2011-10-31
Boot script looks normal. You do seem to have a large / (root) which only needs to be 10-20GB when you have a separate /home. And then your /home is small.

So what does work? Is it only XP that does not boot now?

Windows configuration from grub looks correct. What error message or screen do you get when you try to boot XP?

If you want to, you can install the XP boot loader to the MBR, but I would expect to get the same error. The Windows boot loader just jumps to the PBR in the same way grub chainloads to the Windows PBR, so it is very rare for there to be anything grub has done to change the Windows boot.

Did you also run chkdsk?

My Windows XP has quit working (now no excuses for me as I said I would stop using it.) But that was because I changed BIOS AHCI mode and XP needs extra drivers to work then.

---

### Post by dkubarek on 2011-10-31
Yea I realized quickly my partition error. Should I reinstall to fix that or can I resize the partitions in Ubuntu. I imagine I can.

XP doesn't boot. No error. I get the blinking cursor for awhile and then Ubuntu boots.

Should I run check disk from the XP disk?

---

### Post by oldfred on 2011-10-31
I would try chkdsk from the XP and rerun the fixBoot. They are interrelated as I have run the Windows 7 chkdsk and it wrote a Windows 7 boot sector. It still booted my XP but I was able to use the repair CD to write a new XP boot sector. There are differences with NTFS and XP & Windows 7 boot sectors.

You can resize relatively easy since you do not have a lot of data in the partitions. When you have lots of data it can be slow. Just shrink / and move /home left into the unallocated. If you still have the two swaps you can delete one, but if it is the one in your fstab you will have to update the fstab entry with the new UUID.

Resizing an Ubuntu System Partition Use liveCD so everything is unmounted & swapoff if neccesary
[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)
[http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html)

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

### Post by dkubarek on 2011-11-01
Fixed partitions. Thanks for that. Really love all the tools that come with Linux. The XP partition thing is horrible.

I figured out that I can use Boot Repair to rewrite the MBR for XP or for Linux and boot successfully after that but it's one or the other still.

Here's the latest log:
[http://paste.ubuntu.com/725672/](http://paste.ubuntu.com/725672/)

I'm in Ubuntu now. When I tried to update grub it found both OS but on reboot it hung up for a long time (a few minutes) then I restarted and Ubuntu came up.

---

### Post by oldfred on 2011-11-01
Script looks normal.

So if you now install the Windows boot loader Windows works. And if you install grub2's boot loader Ubuntu boots. But using the Windows entry in grub's menu does not. That is a bit unusual. Usually when grub does not boot Windows it is a Windows issue.

Is this an older computer? If more than about 6 years old some BIOS would not boot a partition beyond 137GB. But if you get Ubuntu to boot then that must not be the issue.

When you ran chkdsk from Windows did it show any errors. Ubuntu/grub/gparted do not like NTFS partitions that need a chkdsk to prevent further corruption that chkdsk then might not fix. But chkdsk does not fix everything on one pass. I had my XP boot (thru grub) but gparted would not see it until I ran chkdsk. Then XP booted better/faster also.

---

### Post by dkubarek on 2011-11-01
The computer is about 4 years old. The hard drive is stock so I'm good there.

I almost gave up but then I switched back to XP and had a ****-ton of updates and then various errors from programs I uninstalled, etc. Ugh!

I might try to install 11.10 or the wubi. I really like the superkey search/launch for everything and I think that begins with 11.04. The wubi was fine but I was hoping to have some security with dual boot. If my Windows breaks I could use Linux to grab my files.

I didn't notice if check disk found errors. Maybe I'll run it again while in XP.

---

### Post by oldfred on 2011-11-01
You can invest in another drive, before they go up in price. (Another said they have shortages & will have price increases.) Or you can just use a larger flash drive as a full drive. I have a full install on a 16GB flash drive and it is not speedy but very functional.

HOW TO Avoid Wubi & Install Ubuntu on USB Drive -amjjawad
[http://ubuntuforums.org/showthread.php?t=1650699](http://ubuntuforums.org/showthread.php?t=1650699)

It does not have to be encrypted BIOS based system:
Standard full install with screenshots to flash or SSD:
Ubuntu Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)

With multiple drives, it is always best to partition in advance and use manual install. Otherwise grub2's boot loader will just default to sda which is then often the wrong drive.

---

### Post by dkubarek on 2011-11-01
I have drives coming out of my ears so I might just do that. I live near Penn State and computer parts are easy to come by. I need SATA but it would be easy to find one. I'll try that. 

You think I would have the same issues with other versions? I tried 11.10 and I really think it has some major efficiency issues. It ran poorly on my laptop and my desktop.

If you run 10.10, does it have the classic layout or the one with the icon bar at left and the superkey that finds and launches everything? Thanks a ton for all the info.

---

### Post by oldfred on 2011-11-01
I am still on Maverick, but when I installed Natty and used the classic based on Gnome 2, I could see very little difference. With Oneiric it changed to Gnome 3 and the fallback is similar but a lot of things have moved. Unity looks ok if you are just a consumer of data, a portable or similar device. But for a desktop I want custom-ability and have a work flow that I can modify but not totally disrupt. I think I can live with fallback and will plan on 12.04. My wife has complained about too many updates and those were the minor changes from 9.04 thru 10.10 every 6 months. I could not even attempt to explain Unity to her.

---

### Post by dkubarek on 2011-11-02
I'm going to try these fixes and see if anything works:

[http://shrewdgeek.com/2011/05/11/ubuntu-windows-xp-dual-boot/](http://shrewdgeek.com/2011/05/11/ubuntu-windows-xp-dual-boot/)

perhaps the same as the first but:
[http://www.techsupportforum.com/forums/f64/solved-dual-boot-winxp-ubuntu-11-04-a-591749.html](http://www.techsupportforum.com/forums/f64/solved-dual-boot-winxp-ubuntu-11-04-a-591749.html)

and lastly I'll try EasyBCD, a windows bases program that manages the boot order of several operating systems. The program looks easy enough but who knows at this point if it will work.

I actually need a USB drive so I'll buy one that's big enough to use and try it. I'm worried that it will be slow but I really like the idea of having one Ubuntu to customize on my netbook and desktop. Both, I think, have boot from USB in the BIOS.

---

### Post by dkubarek on 2011-11-02
I tried updating grub from the Live CD as noted in that second link and I got this error:

/usr/sbin/grub-probe: error: cannot stat `aufs'.


It appears that issue isn't fixed and others have the same problem.

---

### Post by oldfred on 2011-11-02
I posted the commands to reinstall grub2's boot loader in post #33. But now your install is in sda3 per last boot script.

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD/usb, Ubuntu install on sda3 and want grub2's bootloader in drive sda's MBR:
#Find linux partition, change sda3 if not correct:
sudo fdisk -l
#confirm that linux is sda3
[COLOR=Red]sudo mount /dev/sda3 /mnt[/COLOR]

#If grub 1.99 with Natty uses boot not root.
[COLOR=Red]sudo grub-install --boot-directory=/mnt/boot /dev/sda[/COLOR]

# If no errors on previous commands reboot into working system and run this:
sudo update-grub

#More info here
[https://help.ubuntu.com/community/Grub2#Copy_LiveCD_Files](https://help.ubuntu.com/community/Grub2#Copy_LiveCD_Files)
#How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
#Reinstall grub2 - Short version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

---

### Post by dkubarek on 2011-11-02
When I ran the commands I get no errors but a prompt about FlexNet:

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       35058   281603353+   7  HPFS/NTFS
/dev/sda2           35059       35545     3906251    f  W95 Ext'd (LBA)
/dev/sda3           35545       36437     7168000   83  Linux
/dev/sda4           36437       38914    19892224   83  Linux
/dev/sda5           35059       35545     3906250   82  Linux swap / Solaris
ubuntu@ubuntu:~$ sudo mount /dev/sda3 /mnt
ubuntu@ubuntu:~$ sudo grub-install --boot-directory=/mnt/boot /dev/sda
/usr/sbin/grub-setup: warn: Sector 32 is already in use by FlexNet; avoiding it.  This software may cause boot or other problems in future.  Please ask its authors not to store data in the boot track.
Installation finished. No error reported.
ubuntu@ubuntu:~$

---

### Post by oldfred on 2011-11-02
Flexnet used to be problem, but grub worked around it. Flexnet would just overwrite grub and vice-versa causing huge problems.

Adobe Photoshop, CAD/CAM, Rosetta Stone, Matlab others 
 see google search on others with same issue: flexnet site:ubuntuforums.org
Sector 32 is already in use by FlexNet
[http://www.amazon.com/Adobe-Photoshop-Extended-CS4-VERSION/product-reviews/B001EUDGO2](http://www.amazon.com/Adobe-Photoshop-Extended-CS4-VERSION/product-reviews/B001EUDGO2)
The problem turned out to be Adobe's digital rights management software [DRM]. Do your own search for "FlexNet," formerly known as "SafeCast." What I have read is that FlexNet is a viral rootkit that replicates in multiple locations whenever a CS3 or CS4 product is installed, including trial versions.
Erase flexnet, if not using protected windows software anymore:
[http://ubuntuforums.org/showthread.php?t=1661254](http://ubuntuforums.org/showthread.php?t=1661254)

---

### Post by dkubarek on 2011-11-02
I did the grub install you suggested and it did work. I was able to boot into Ubuntu without an issue but still no XP, even after sudo update-grub. 

I have an external hard drive. It's an old Western Digital 150 gig ATA to USB I think. Might have fire wire. Think that would be faster than a thumb drive? I do a lot of video and photo editing and ripping so speed is a concern. BUT that bootable thumb drive sounds awesome so I'll try that too.

---

### Post by oldfred on 2011-11-02
Windows partition looks ok, all I know is the chkdsk & fixBoot commands posted before. Perhaps the flexnet is not the only proprietary thing you have in XP?

---

### Post by dkubarek on 2011-11-02
I have a pretty clean install on XP but i did add a few programs and Norton Antivirus. Maybe it is something there. It's a bummer because I love Ubuntu.

The Easy BCD program is supposed to be a bootloader for everything but it runs in Windows 7. Next, I plan to wipe Ubuntu., install Tiny 7 and see if I can get all 3 systems working. That sounds like disaster but Easy BCD is supposed to allow you to install many OSs and boot with it. We'll see.

---

### Post by dkubarek on 2011-11-03
the Live USB worked pretty easily. It's nice to have only one copy for my desktop and laptop too. It runs a bit slow during certain tasks but it's surprisingly less of a burden than I thought. I'm checking with my techie friend for ways to speed it up. He says increasing the page filing to the RAM or something will help. 

I guess this is sorta solved. I'll report back if my Windows 7 and Easy BCD booter plan works but I know that's far from ideal. Thanks again for all your help.

---

### Post by oldfred on 2011-11-03
Glad you got something working.

I do not know about EasyBCD. A few here do use it & I think it has its own forum.

Have you made some settings on the flash drive to reduce writes. With flash reading is pretty good, it is the writes that slow it down. I try to avoid large programs on flash also. The lighter weight apps may work better if you want to use it a lot. Mine is more as a backup and another system to boot in emergency..

[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)
Use ext2 or ext4 without journal:
sudo tune2fs -O ^has_journal /dev/sda1
sudo tune2fs -o discard /dev/sda1
No swap or set swapiness or install 'Dynamic Swap Space Manager' from the Ubuntu Software Center
After installing, change the fstab so that everything gets mounted with noatime.
change to noop i/o scheduler

---

### Post by dkubarek on 2011-11-04
So I figured out that all my stuff will run in Windows 7 so I just wiped the drive and installed that. Do you think I would have the same problems if I install Ubuntu on the second partition I have already created?

Or is my problem likely to occur with any Windows OS because the boot loaders are the same? Also, if I do the Advanced install on a partition, WHERE should I install grub? I think it gives you an option to put it in the Windows partition or the Ubuntu partition but I'm not clear on that since it's been a few days.

---

### Post by dkubarek on 2011-11-04
This is the screen I am referring to as per the grub install:

[http://farm5.static.flickr.com/4131/4837104879_7b9c388b3b_o.png](http://farm5.static.flickr.com/4131/4837104879_7b9c388b3b_o.png)

---

### Post by dkubarek on 2011-11-04
Is this issue related to my problem?

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/614309](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/614309)

---

### Post by oldfred on 2011-11-04
You should be installing the grub2 boot loader to the MBR. Then the bug report of any partition changes does not even matter.

One advantage of partitioning in advance.

If you install grub2's boot loader to the PBR of Windows, it overwrites the Windows partition code which you should not ever modify. You can replace the MBR boot code.

Only if using something like EasyBCD would you install grub to the /(root) partition of Ubuntu. But then you may have to reinstall on every grub2 update, as it uses blocklists and that is hard coded addresses to find the rest of grub. Any change to where the grub files are on the hard drive will cause a boot failure.

---

### Post by dkubarek on 2011-11-05
after looking at the EasyBCD tutorial it looks like it doesn't really solve boot issues, it just cleans it up a bit. In that case, I think I'll skip it. I'll try to install Ubuntu now that I have Windows 7 and see what happens. I'll partition in advance.

---

