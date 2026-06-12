---
title: "Install is now looping at the bootmenu (dual boot)"
date: 2006-11-16
forum: Installation &amp; Upgrades
---

### Post by vivi the mage on 2006-11-16
I have windows xp installed on  30gb partition, with a 10 gb partition available. 
I booted to the CD, installed, chose the other portion of the partition. 

Installed successfully, then I restart, boot into windows (choosing windows from the boot menu), I get in okay. It says that the hardware was changed (it made the partition for the Ubuntu install bigger which was okay, I only have 4gb used on windows xp).

I now try to boot up and it just loops right after bios at the point where it lets me choose which OS to go too. XP, Ubuntu, Memtest, etc.

so I guess my question is...how do I change the boot so it works...I am in the Live CD version of ubuntu looking for a way, but I see nothing much to help with that. I also checked GNOME partition Editor and it says my boot is on my NTFS partition.

another off topic question is ... I have

/dev/sda1 NTFS              23,84gb 
/dev/sda2 ext3              12.83gb 
/dev/sda3 extended          596mb 
     /dev/sda5 linux-swap   596mb

my qestion is : Is ext3 the portion where my ubuntu is installed?

also, whats with the extended 596mb? can I partition to get back into the NTFS, or the ext3?

also, this is where it says under flags that NTFS has the boot.

EDIT : should I just reinstall Ubuntu would that fix it?

---

### Post by vivi the mage on 2006-11-16
any guesses?

---

### Post by vivi the mage on 2006-11-16
so I reformatted and everything was working okay!

then it said something was loaded again so I had to reboot (happened to me last time as well).

Why does it happen?

RIGHT after the format, booting into ubuntu was fine, logged in and tested it, OK!

then I rebooted, logged into windows and i said something was just installed, so please reboot, I did so...now its looping again :s....is there something wrong with the boot config file? I dont know which boot.config it reads, can I just edit it? I dont know how though haaha...ideas?!

I am talking to myself here -_-

---

### Post by Herman on 2006-11-16
>  /dev/sda1 NTFS              23,84gb 
/dev/sda2 ext3              12.83gb 
/dev/sda3 extended          596mb 
     /dev/sda5 linux-swap   596mb>  my qestion is : Is ext3 the portion where my ubuntu is installed?Yes.
>  also, whats with the extended 596mb? can I partition to get back into the NTFS, or the ext3? well, you can, but you shouldn't.  Your 'extended' partition is kind of like a box, that can have logical partitions inside it. Your swap area is a logical partition. It is possible to create a swap area as a primary partition, but normally they are created as logical ones by default. It would probably be best just to leave things how they are.
>  also, this is where it says under flags that NTFS has the boot That's okay, Grub shifts the boot flag around automatically as needed. 
>  I am talking to myself here -_- Sorry, you are not alone. It's just that I can't imagine what could possibly be causing your main problem, I haven't seen the symptoms you describe before. More information will be needed before anyone will be able to be much help.
>  then it said something was loaded again so I had to reboot (happened to me last time as well).
Why does it happen?
RIGHT after the format, booting into ubuntu was fine, logged in and tested it, OK!
then I rebooted, logged into windows and i said something was just installed Telling people *exactly* what the messages you received said would be a help maybe. Just that 'something' was loaded or 'something' was installed is better than nothing, but really, to help, it might be important to know exaclty what that 'something' is. Even if it's something you can't understand, if you could write down the exact message, it might help someone to help you. Anyway, don't worry about it for now, there are other ways to gather information that might help.
Can you start the Live CD and post the output from 'sudo fdisk -lu' please? ```
sudo fdisk -lu
``` Also, the boot.config file you asked about is /boot/grub/menu.lst, if you can also post at least the bottom part of that it may help. You will probably need to 'mount' your Ubuntu partition in the Live CD in order to get the menu.lst file. Here's how to do that, [Click Here]("http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD").

Really, it seems like a very mysterious and unusual problem to me. Any other info you can provide might also help. For example, how did you install Ubuntu? I mean, what CD did you use, and did you follow any particular installation instructions or just do it by common sense and instinct? What disk partitioning software was used? The partitioner in the install CD? Anything else you can add that might be a clue?

Regards, Herman :confused:

---

### Post by vivi the mage on 2006-11-17
okay, I am totally reinstalling Ubuntu again to get that message.

I have a 40 gb drive, partitioned (via grub in Ubuntu livecd) and made 5gb unallocated for the linux install. I picked 'use the largest continuous free space' as what the disk space is under.

I am installing from the CD ISO of the newest 6.10 ubuntu.

reinstall was good, I restarted, the boot manager came up with these options :

Ubuntu, kernal 2.6.17-10-generic
Ubuntu, kernal 2.6.17-10-generic (recovery mode)
Ubuntu, memtest86+
Other Operation systems :
Microsoft Windows XP Professional

I am now entering XP Pro for the first time since I installed Ubuntu. 
It is now checking file systems on C:
IT is checking it for consistency....
CHKDSK is verifying files, indexes, consistancy.
It restarts and I get the same boot menu options.

I am now loading XP and it is allowing me to log in like I normally would if ubuntu was not installed.

now this is where the issues happen! 
I am into windows and it says "SYSTEM SETTING CHANGE"
> 
Windows has finished installing new deices, the software that supports your device requires that you retart your computer. You must restart your computer before the new settings will take effect.

Do you want to restart nw? YES NO

I will click no, because I dont want it to start looping again. Is there a way to edit the boot.ini while I am in windows before I restart to the death loop I once got?

---

### Post by vivi the mage on 2006-11-17
thank you for the reply btw herman!

also, I go into msconfig and look under the boot.ini and it does not have Ubuntu on there anywhere, just my normal option of Windows XP Pro.

So my conclusion of that is that its the linux partition that is holding the boot.

I will go back and load livecd and see if I can get the last portion of the boot.config for you to look at.

let me add one more thing, I am in the filesystem on the LIVECD now becuase I am getting the looping death again...

I can get into the boot folder...but there is no grub folder. 

In the boot folder I have abi.2.6.17-10-generic, config-2.6.17.10-generic, memtest86+.bin, system.map-2.6.17-10-generic, vmlinuz-2.6.17.10-generic.

---

### Post by bulldog on 2006-11-17
If you're on the live cd you have to mount your Ubuntu partition.
Type in a terminal```
sudo mkdir /mnt/rescue
```
This will create a mount directory.
Then in your terminal```
sudo mount /dev/sda2 /mnt/rescue
```
This will mount Ubuntu.

Now to get to your menu.lst we first make a copy for safety.
```
sudo cp /mnt/rescue/boot/grub/menu.lst /mnt/rescue/boot/grub/menu.lst_backup
```
Now to list your menu.lst and to copy it to the forum like Herman asked you,```
gedit /mnt/rescue/boot/grub/menu.lst
```
It will be read only thus no worry,you can't change anything here,just copy the relevant part to the forum.

Okay can you tell a bit more about windows?
Who installed it and did he use a normal install disk.
Windows will not detect Ubuntu so there's no need for windows to install anything or to reboot for that matter.
I'm just curious how windows detect any change,because even resizing your disk shouldn't be a concern to Windows,only when you go fiddling with the system files of windows,it can put up a complain,but generally it won't boot anymore.

---

### Post by FLPCGuy on 2006-11-17
It never hurts to add an extra line or two at the bottom of boot.ini if you are adding partitions.  Increment only the partition number.  This gives you a chance to get into Windows after the partition number has been changed.  If Windows can't find the system files from the info in boot.ini it won't run.

[boot loader]
timeout=8
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows Server 2003 for Small Business Server" /fastdetect
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Windows Server 2003 for Small Business Server" /fastdetect

Sorry, I don't know enough about GRUB yet to help with it.  I'm still learning Linux.

---

### Post by vivi the mage on 2006-11-17
This would be the bottom of what I have.

> ## ## END DEFAULT OPTIONS ##

title ubuntu, kernal 2.6.17.10-generic
root (hd0,1)
kernal /boot/vmlinuz-2.6.17.10-generic root=/dev/sda2 ro quiet splash
initrd /boot/inistrd.img-2.6.17.10-generic
quiet
savedefault
boot

title ubuntu, kernal 2.6.17.10-generic (recovery mode)
root (hd0,1)
kernal /boot/vmlinuz-2.6.17.10-generic root=/dev/sda2 ro single
initrd /boot/initrd.img-2.6.17.10-generic
boot

title ubuntu, memtest86+ 
root (hd0,1)
kernal /boot/memtest86+.bin
quiet
boot

## #END DEBIAN AUTOMAGIC KERNALS LIST

#This is a divider, added to separate the menus items below from the debian ones

title Other operating systems:
root

#this entry automatically added by the debian installer for a non-linux OS
#on /dev/sda1
title Microsoft Windows XP professional
root (hd0,0)
savedefault
makeactive
chainloader +1


as for the windows installation it is a normal Dell PC, so it came standard on it. Then I loaded the LIVECD and partition 6gb unallocated, then Ubuntu installed into that 6gb.


I was the one who installed it, with Dells installation disk.

---

### Post by bulldog on 2006-11-17
Did you defragment windows properly before you freed up space for Ubuntu?

Because,like I said before,windows shouldn't react on your Ubuntu install.
But if you didn't fragment well,it could be some files are messed up when you resized the hard disk.
This could be a wild guess,but I've seen stranger things happened.

---

### Post by vivi the mage on 2006-11-17
see, but I can still get into windows without an issue after I install Ubuntu....

I am looking at the loop right now and it says, right after bios, GRUB:Loading stage 1.5

then it restarts

---

### Post by bulldog on 2006-11-17
If you boot from the live cd you can reinstall GRUB in about 5 minutes.

But you stated,after you boot windows it had detect changes,and had to reboot,than the looping starts.
Windows did alter something and then GRUB is gone.
Try to reinstall GRUB and don't boot windows,just try Ubuntu and see if this works.
If so there's something wrong with your windows install.

Boot into the live Ubuntu cd. 

When you get to the desktop open a terminal and enter. 
```
sudo grub
```
This will get you a "grub>" prompt 
```
find /boot/grub/stage1
```
This will return a location which you have to use in the next commands. 
```
root (hd?,?)
```
Next enter the command to install grub to the mbr
```
setup (hd0)
```
Finally exit the grub shell
```
quit
```
That is it. Grub will be installed to the mbr.
[/code]

---

### Post by vivi the mage on 2006-11-17
I deleted the Ubuntu partition via liveCDs GENO, then reinstalled.

I restarted, GRUB was good, I opened up Ubuntu for the first time, logged in, everything was good.
Restarted , booted to Live CD, ran what you said with no problems. 
I get to the Grub screen again, boot to windows, this time it doesnt ask to reboot, but I reboot to test it, and it loops all over, hmprh.

I booted back into LiveCD and reran your steps and it worked fine, I was able to see grub and choose what OS to boot to. I am getting into windows right now to test it out, and I will reboot again to see if it gives me the loop of death all over, wow this is weird. still looping..

It definatly seems like something with windows, can I add a line to the boot in windows to fix this from resetting everytime?

---

### Post by Herman on 2006-11-17
Thanks  vivi the mage, 
Now it's getting interesting...:-k
Normally, after Windows gets resized, neither Ubuntu nor Grub touch any part of anyone's Windows partition. It is odd that Windows would detect any changes and run a CHKDSK or any other utility. 

The only possible reason for that I can think of would be if, due to an error in the partitioning, you have a 'partition overlap', which is a condition which is quite rare nowadays, I haven't seen an example of that for a long time.
We can see if that might be the problem if you can send a copy of the output from running the command 'sudo fdisk -lu', from a terminal in the LiveCD, ```
sudo fdisk -lu
``` Thanks, that might also give us some other clues, or maybe not, but it often is a big help.
Thanks for your copy of the bottom of your menu.lst too.

You will see from the output of 'sudo fdisk -lu', that your first partition never begins until sector 63, which is right after the end of the first track of our hard disks. (There are 63 sectors per track, but the first one is number 0, so it starts counting from zero, making your Windows bootsector the first sector of the next track.

Grub doesn't touch your Windows partition at all, it only installs a small bit of (stage1) code in your MBR, Grub's 'stage1' is basically just a pointer, to make the MBR point to the Ubuntu partition, where the main part of Grub lives. The MBR belongs to your hard disk, which belongs to you, it does not belong to Windows, it is not part of the Windows partition. However, Windows used to have its own version of a 'stage1' in your MBR until you installed Grub. 

Following the MBR, Grub also installs stage1_5 in the next 15 sectors of the first track, which is code for helping Grub understand filesystems, so it can search for the files it needs on your hard disk easier. Grub can search for files by filename.

None of these things normally affect Windows at all, so I suspect some kind of partitioning error, but it's too early to tell for sure.  A bad burn or a scratch or smudge on a CD can cause odd problems, or it could be some other cause.

Windows boot.ini and NTLDR would not be affected by Grub, that's for sure, but they can also be used a a sort of rough, primitive form of bootloader. I have WinGrub installed in my Windows XP at the moment, to try it out. It's working very well, I like it.  In my case, I have WinGrub configured to boot via boot,ini, although WinGrub can also be  optionally installed to MBR.  That's another story though, and has very little to do with the issue under discussion.

Just one more thing, you can boot Ubuntu with Super Grub Disk even if you have no other bootloader at all, as long as you have at least a kernel and an initrd.img in your /boot directory. It might make it easier for you to try booting your installed Ubuntu system that way. The LiveCD is good, but later on if this takes any longer to solve, the next tests to try to find out what's wrong will be to try booting with Super Grub. So you can (if you want to), get a Super Grub Disk ready. [Super Grub Disk : En]("http://adrian15.raulete.net/grub/tiki-index.php")

That's all for now
Regards, Herman :D

---

### Post by vivi the mage on 2006-11-17
I will go ahead and get super grub if this doesnt work out :).

/dev/sda1(DEVICE)  *(BOOT)     63(START)    68276249(END)     34138093+(BLOCKS)     7(ID)   HPFS/NTFS(SYSTEM)
/dev/sda2(DEVICE) 68276250(START) 77642144(END) 4682947+(BLOCKS) 83(ID) LINUX(SYSTEM)
/dev/sda3(DEVICE) 77642145(START) 78124094(END) 240975(BLOCKS) 5(ID) Extended(SYSTEM)
/dev/sda5/(DEVICE) 77642208(START) 78124094(END) 240943+(BLOCKS) 82(ID) Linux swap/Solaris(SYSTEM)

those are the numbers , its a  table...but you cant make tables too well in forums so I just threw on what each header was in parenthesis.

---

### Post by Herman on 2006-11-17
```
<DEVICE>__<Boot>__<Start>______<End>______<Blocks>_____<ID>____<System>_
/dev/sda1____*_____________63____68276249_____34138093+_______7_____HPFS/NTFS
/dev/sda2__________68276250____77642144______4682947+______83_____LINUX
/dev/sda3__________77642145____78124094_______240975_______ 5_____Extended(SYSTEM)
/dev/sda5__________77642208____78124094_______240943+______82_____Linux swap/Solaris(SYSTEM)
``` Well, the good news is you have no partition overlap. :D

---

### Post by patience on 2006-11-19
Forgive me for jumping into the middle of this thread. I'm experiencing the same endless loop problem between the bios screen and the grub menu.

In some other linux forums, I've found references to "vendor rescue partitions" and suggestions that they may be at fault.

My system is a Dell Latitude D600. Does your system happen to be a Dell too?  If that's the case, I'm wondering if there is some diagnostic program that runs in that mystery partition when Windows boots that could be corrupting the grub menu.

Thanks

Edit:  Apparently, this is an existing bug. [https://launchpad.net/distros/ubuntu/+source/grub/+bug/26058]("https://launchpad.net/distros/ubuntu/+source/grub/+bug/26058")

---

### Post by vivi the mage on 2006-11-20
Busy weekend at home! I picked up 4 PS3's and 2 nintendo wiis and a  xbox 360 from a friend for only 2000$ and will sell a few of these off for a nice little gain!

back on topic...I used an XP CD becuase I hate the bloatware Dell installs. There is no recovery disk partition.

Hmmm, I am still kind of baffled why its doing this! Anyone think of anything else? haha

---

### Post by Herman on 2006-11-20
Try turning off (just temporarily), all antivirus and similar type apps you may have running in Windows, (keep off the internet until you are ready to turn them on again).
Restore Grub the way bulldog suggested, (because that's faster and easier than re-installing).
See if it still happens.
There also might be 'MBR protection' (anti bootsector virus) features in the BIOS, but I doubt if that would be the problem,  normally they prevent the MBR from being written to in the first places. You could try looking for one of those though too, and  disable it for now .

---

### Post by vivi the mage on 2006-11-20
I have SAV, but that doesnt do anything AFAIK.

---

### Post by Herman on 2006-11-21
vivi the mage,
I just made a new how-to about making your own personal Grub floppy disk. For now I think that's the best thing to do. Although it doesn't directly solve your problem, it will make life easier for your for now.

 NEW! How to make your own personalized Grub Floppy Disk (or USB thumb drive). [GO]("http://users.bigpond.net.au/hermanzone/p15.htm#grub_floppy_howto_make")
 
And, just in case you don't have a floppy disk drive, here's my how-to for a Grub CD,
                                         How to make your own personalized Grub CD-RW..........................................................[GO]("http://users.bigpond.net.au/hermanzone/p15.htm#HOW_TO_MAKE_A_GRUB_CD")

(You just copy and paste the commands, no need to type any yourself)

I'm sure that Windows won't be able to eat your Grub anymore now! 8)

I'm out of ideas for now on how to actually fix your problem, but maybe someone will think of something that will solve it sooner or later, I hope.

Regards, Herman :D

---

### Post by vivi the mage on 2006-11-21
I got that boot to CD to work, but It does kind of suck having to boot to CD everytime!


Something interesting :

I used the configfile version to work with an update if there was one on Ubuntu, but if I clicked on Windows XP (the menu with configfile, basically the boot iso CD) It says a file is missing...interesting, Error 15: File not found press any key to continue.

but I will click Ubuntu ConfigFileBoot then another Grub menu comes up (im guessing the up to date one)

and I will click XP Pro and it works fine! hmmm, interesting. Maybe that will help you out?

BTW : thank you very much for that boot CD Herman, its a start :).

---

### Post by Herman on 2006-11-21
vivi the mage,
>  but I will click Ubuntu ConfigFileBoot then another Grub menu comes up (im guessing the up to date one) Yes, I really like that 'configfile' command, that brings up your current Grub menu in your hard disk installed /boot/grub, in Ubuntu, so it's your own up to date Grub menu. That's a good way to boot up.
I'm not sure what you mean about when you 'clicked on Windows XP (the menu with configfile, basically the boot iso CD) It says a file is missing...interesting, Error 15: File not found press any key to continue.'
I will take a good look into that. Maybe my how-to needs a few improvments to make it a liitle easier to follow too. Thanks for your feedback. Everytime I get feedback like this it enables me to make things better for others in the future. Thanks again. :D

Regards, Herman

---

### Post by vivi the mage on 2006-11-22
basicaly with this boot CD there are two screens. The boot CD screen and the second screen (my guess is the HD grub)

In the first screen I try to boot to Windows XP Professional (this screen is the boot grub off of the CD) and when I enter that it gives me that error, BUT if I enter the configfile on the BOOTCD Grub menu I can select XP Professional with no issues.

---

### Post by Herman on 2006-11-22
> basicaly with this boot CD there are two screens. The boot CD screen and the second screen (my guess is the HD grub) That's right, that's the way it should be when you are booting Ubuntu from your Grub CD. 
The first Grub menu is the one that belongs to the CD, and can be configured by the menu.lst in the CD, before the files are made into an .iso file. I have a splashimage in my CD.
When I choose Ubuntu, it boots Ubuntu directly from the CD.
If I select Windows, mine boots up Windows XP by the first sector of the Windows partition (chainloader +1), directly from the CD.
When we use 'configfile boot', that brings up the Grub menu from your hard disk installed Grub. Then you have another chance to select Ubuntu or Windows again. If you get a kernel update, this option will be able to boot  your newest kernel, maybe I should amend that how-to and make the 'configfile boot' at the top of the menu, because really it's the best choice when using a Grub CD, 
That's really weird that your Windows will not boot from the CD, but will boot up from your hard disk installed Grub. :confused:
It does seem to be a clue, but I'm not sure what that means. I was thinking that over yesterday on my way to work. Hmmm. :-k
I don't really know if this will help for sure or if it will do nothing at all, but you couild try running Windows [recovery console]("http://www.kellys-korner-xp.com/win_xp_rec.htm") if you want to, and running 'fixboot', and 'fixmbr', just to see if it will help at all. I don't really think it will, but I might be surprised. I think it might be more likely to do with some setting or application within Windows itself, It seems to be running 'fixmbr' by itself, without your permission. That's what it seems like to me.  I might take a look in my Windows install later and see if I can find anything. I don't have 'XP Professional though, mine's only 'Home Edition', so it's obviously a little different.

---

### Post by vivi the mage on 2006-11-24
okay, I did both 'fixboot', and 'fixmbr' and now the grub screen is gone. It automatically chooses windows XP Professional with no options.


of course I can use my grub CD to load Ubuntu on...is there a way to edit windows boot to show Ubuntu as well as XP ?

---

### Post by adrian15 on 2006-11-24
> **vivi the mage said:**
> 

I now try to boot up and it just loops right after bios at the point where it lets me choose which OS to go too. XP, Ubuntu, Memtest, etc.

vivi the mage... I think the solution for your problem is following #8 on [http://adrian15.raulete.net/grub/tiki-index.php?page=EnFaq]("http://adrian15.raulete.net/grub/tiki-index.php?page=EnFaq").

Tell Herman to explain you how to do this from the live cd. He is better than me for this kind of issues.
[I]
Herman: He cannot use the grub-install command or update-grub he must use the root and setup commands.

We don't need any stage1_5* files and those commands "reinstall" them on /boot/grub.

My explanation for this sort of problems is that windows changes something just after the stage1 (mbr) position but not the mbr.
So if you let windows to boot it will "fix" grub's stage1_5.
The truth is that you do not need this grub's stage1_5 at all.

I actually want to add a rescue option for SGD so that it installs grub without linking stage1 to stage1_5 but directly to stage2. Who knows if I'll have spare time this weekend for implementing it.
[/I]

adrian15

---

