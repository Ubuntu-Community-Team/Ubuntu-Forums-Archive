---
title: "GRUB is gone, Ubuntu inaccesible"
date: 2006-08-18
forum: Installation &amp; Upgrades
---

### Post by MachineBucket on 2006-08-18
I have a laptop running Windows XP and Ubuntu Dapper Drake. XP is the primary OS and I recently tried to restore causing the MBR to be rewritten. Now GRUB is gone and I have no way to get to my Ubuntu partion. Is there someway I can reinstall GRUB to the HD from windows, or do I need a seperate boot loader to get to Linux and then install it. I have tried using Smart Boot Manager on a boot CD but that didn't work. I can't remember the message it gave me at the moment. Thanks for the help.

---

### Post by ciscosurfer on 2006-08-18
Chcek this: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

And this:[ https://wiki.ubuntu.com/phbc50/howtos/how-to_reinstall_grub]("https://wiki.ubuntu.com/phbc50/howtos/how-to_reinstall_grub?highlight=%28grub%29")

And check my signature as well for info on GRUB

---

### Post by MachineBucket on 2006-08-18
Thanks! I'll check these out and see if they help.

---

### Post by xybermaster on 2006-08-18
> **MachineBucket said:**
> I have a laptop running Windows XP and Ubuntu Dapper Drake. XP is the primary OS and I recently tried to restore causing the MBR to be rewritten. Now GRUB is gone and I have no way to get to my Ubuntu partion. Is there someway I can reinstall GRUB to the HD from windows, or do I need a seperate boot loader to get to Linux and then install it. I have tried using Smart Boot Manager on a boot CD but that didn't work. I can't remember the message it gave me at the moment. Thanks for the help.

I use acronis OS selector to choose which os I was to boot. You can try that. Its a windows program. It detects all OS installatons on a system and put them on a nice GUI list.

---

### Post by Herman on 2006-08-18
Hello, MachineBucket, I agree with ciscosurfer, but would also like to add  the following. 
You should try out Super Grub DIsk, which is free, and only around 500 kb. or so to download. You can find Super Grub DIsk at [FONT=serif][http://adrian15.raulete.net/grub/tiki-index.php](http://adrian15.raulete.net/grub/tiki-index.php)[/FONT]  Super Grub is available as a bz2, gz file or a ZIP file. I think you need the ZIP file if you need to open it and burn it from a Windows systems, but if you have another computer with Linux, you can use either the .bz2 or .gz files.

Super Grub Disk can perform the largest variety of functions to do with restoring Grub or booting a Linux system that has a bootloader problem, or a Windows system if it has some problems with being booted by the (newly) installed Grub.
Here are the docs for Super Grub Disk,  [Super Grub Disk Page]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html")  (so you can see all the things Super Grub Disk can do).

Regards, Herman :D

---

### Post by Ziox on 2006-08-18
you can also try gag, it's a graphical boot manager (in french it's GAG)...

this is the link: [http://gag.sourceforge.net/](http://gag.sourceforge.net/)

---

### Post by Drakkor on 2006-08-19
I wouldn't recomend GAG,that's what messed my machine up,and there is no help,all the questions go unanswered, I looked ! I would go with this,by catlett:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
Good Luck ! :)

---

### Post by ciscosurfer on 2006-08-19
@Drakkor

The link you posted is valuable.   And if we sift through it all, we can learn a thing or two.  However, in my first post I gave a link where [all of this is documented already]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") @ help.ubuntu.com.  And yes, I'm sure that page was modified from the GRUB manual at gnu.org...

But, just for the record, I did enjoy reading through the thread you listed to see what kinds of problems people were having; I just thought I'd mention my previous post just in case you were unaware of it -- :-D

---

### Post by Drakkor on 2006-08-19
@ciscosurfer
I agree that probably somewhere at sometime,there was some sort of document or guide to everything Ubuntu and Debian and Linux, but I guess that's why a forum is good,and search in a forum is good. I do beleive people should try to help themselves and not expect everyone else to solve all their problems. Hey,I also get tired of the same questions asked over and over,just by the next person.But in some cases it would turn off prospective users to have to sift through page after page of documentation to try to do one simple thing, when another person might easily show them the way, usually because they've been there before. Cheers ! :-D

---

### Post by Herman on 2006-08-19
> you can also try gag, it's a graphical boot manager (in french it's GAG)...
this is the link: [http://gag.sourceforge.net/](http://gag.sourceforge.net/)Hello, Ziox. I also use and recommend GAG, I even wrote a web page to help people to use it, [*Click Here*]("http://users.bigpond.net.au/hermanzone/p12.htm").
If someone has trouble using GAG, you may pass on that link. :D

Drakkor, GAG Boot Manager is a great boot manager, it helps lots of people because it is graphical so it's easy to reconfigure for people who re-arrange their disks and OSes often, and is operating system independant. (Does not get deleted when an operating system is deleted or gets formatted).
The reason why you couldn't use GAG Boot Manager is because you need to have a bootloader installed in the first sector of the Linux partition for teh GAG Boot Manager to load. Otherwise the Boot Manager has no bootloader so it returns an error like: "boot device missing or invalid."   :D
I am sorry I wasn't around on the day, or didn't notice your request for help or I would have been able to help you with GAG. It really is very good for certian purposes but... you need to read the documentation...:D

I hope you take this in good humour, it is written and intended in a humourous mood. :D
All the best, regards, Herman :D

---

### Post by Drakkor on 2006-08-19
Ok,thought it was maybe because I had Ubuntu and XP on different drives and gub was on the mbr to dual boot. Ok,read the docs and have put grub on the linux partition. And it will boot into whatever I want running the GAG CD. Question: I installed,I think GAG,but when I boot to my main hd it will automatically boot to Ubuntu, shouldn't I get a choice from GAG as to what I want booted without booting from the GAG CD ? Thanks ! :)

---

### Post by Ziox on 2006-08-19
> **Herman said:**
> Hello, Ziox. I also use and recommend GAG, I even wrote a web page to help people to use it, [*Click Here*]("http://users.bigpond.net.au/hermanzone/p12.htm").
If someone has trouble using GAG, you may pass on that link. :D

Drakkor, GAG Boot Manager is a great boot manager, it helps lots of people because it is graphical so it's easy to reconfigure for people who re-arrange their disks and OSes often, and is operating system independant. (Does not get deleted when an operating system is deleted or gets formatted).
The reason why you couldn't use GAG Boot Manager is because you need to have a bootloader installed in the first sector of the Linux partition for teh GAG Boot Manager to load. Otherwise the Boot Manager has no bootloader so it returns an error like: "boot device missing or invalid."   :D
I am sorry I wasn't around on the day, or didn't notice your request for help or I would have been able to help you with GAG. It really is very good for certian purposes but... you need to read the documentation...:D

I hope you take this in good humour, it is written and intended in a humourous mood. :D
All the best, regards, Herman :D

Sweet and excellent guide!!! :p  That was the guide I used to install GAG on my computer...Thanks

---

### Post by Ziox on 2006-08-19
> **Drakkor said:**
> Ok,thought it was maybe because I had Ubuntu and XP on different drives and gub was on the mbr to dual boot. Ok,read the docs and have put grub on the linux partition. And it will boot into whatever I want running the GAG CD. Question: I installed,I think GAG,but when I boot to my main hd it will automatically boot to Ubuntu, shouldn't I get a choice from GAG as to what I want booted without booting from the GAG CD ? Thanks ! :)

are you sure that you'ved saved your configuration on your hard drive?

---

### Post by Herman on 2006-08-19
My appologies for the double post - (keyboard clumsiness).

---

### Post by Herman on 2006-08-19
> Anyone know how I can install a bootloader installed in the first sector of the Linux partition ? Thanks ! :smile:Drakkor, Sure, :D.
To install Lilo in an already installed and working Ubuntu partition, (even if you already have GRUB on MBR), follow this how-to: [Install Lilo from terminal.]("http://users.bigpond.net.au/hermanzone/p12.htm#Install_Lilo_from_terminal")

I know Grub is generally the best on MBR, but I like to use Lilo as well on the first sector so I can boot with GAG in the event that Grub becomes disabled in some way. (For example if I try some experiment with it that backfires on me). :D
That way I will have a completely different bootloader on standby so if one's no good, the other will still be there. 
Regards, Herman :D

---

### Post by Drakkor on 2006-08-19
Oops,Herman, another mis-step I guess already put grub on the Ubuntu partition from the terminal,it was quite easy,lol ! :)
Edit: Jeez,thought I woulda hosed my whole system by now,lol :p

---

### Post by mhbell on 2006-08-19
> **ciscosurfer said:**
> Chcek this: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

And this:[ https://wiki.ubuntu.com/phbc50/howtos/how-to_reinstall_grub]("https://wiki.ubuntu.com/phbc50/howtos/how-to_reinstall_grub?highlight=%28grub%29")

And check my signature as well for info on GRUB

THank You Thank You for the links and Info and thanks to whoever wrote the instructions. It saved my Bacon Big Time. I did a ubuntu install from a live DVD and could not get to a prompt to do a Expert install. It over wrote my MBR with Grub which I wanted in the Ubuntu Root Partition and not the MBR. I use a 3rd party Boot Loader to boot several Linux Distro's and WXP Pro. When I reinstalled my 3rd Party Boot Loader could not access my Ubuntu. This (how to) Saved the day and let me recover the Grub bootloader to the root partition of Ubuntu.
Thanks again everyone.
Mel
:-D

---

### Post by Herman on 2006-08-19
> Oops,Herman, another mis-step I guess already put grub on the Ubuntu partition from the terminal,it was quite easy,lol ! :smile:
Edit: Jeez,thought I woulda hosed my whole system by now,lol :razz: Drakkor, No matter, I install Grub, then Lilo, then Grub again to the partition's first sectors.  To my MBR I install Grub from one operating system, then overwrite it with Grub from another, maybe install Lilo to it for a while, then Windows again, then back to Grub, then ...
I just love playing with bootloaders. I haven't worn anything out yet. :D

Just leave Grub there for now if you want. Grub's good.

Besides, we can always just boot our kernels directly with [CLI grub]("http://users.bigpond.net.au/hermanzone/p15.htm#cli") anyway so it doesn't really matter what we do, as long as we have Grub we can always boot somehow. :D
Regards, Herman

mhbell, I'm glad something in this thread was useful to someone, happy booting! :D

---

### Post by Drakkor on 2006-08-20
Ok,Herman finally got GAG installed.... :) I had forgot to enter "H" to save it to the HD,lol. So now when I boot from my first HD I get the GAG menu !! YAY !! :p And can boot from Ubuntu or Windows or floppy. Ok, now I have installed DSL (Damn Small Linux) on hda7,and installed grub on it. But when I put it in GAG, it will boot to Ubuntu !! Any ideas ? Thanks ! 
Edit here's this:
Maybe because it's a logical partition ? When I GParted it,it would not give me the option to make it primary.

drakkor@drakkor:~$ sudo fdisk -lu 
Password:

Disk /dev/hda: 80.0 GB, 80054059008 bytes
255 heads, 63 sectors/track, 9732 cylinders, total 156355584 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          63    22989014    11494476    7  HPFS/NTFS
/dev/hda2        22989015   156344579    66677782+   f  W95 Ext'd (LBA)
/dev/hda5        22989078    85610384    31310653+   7  HPFS/NTFS
/dev/hda6        94157028   156344579    31093776    b  W95 FAT32
/dev/hda7        85610448    94156964     4273258+  83  Linux

Partition table entries are not in disk order

Disk /dev/hdb: 60.0 GB, 60040544256 bytes
255 heads, 63 sectors/track, 7299 cylinders, total 117266688 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *          63    42267014    21133476   83  Linux
/dev/hdb2       114254280   117258434     1502077+   f  W95 Ext'd (LBA)
/dev/hdb3        42267015   114254279    35993632+  83  Linux
/dev/hdb5       114254343   117258434     1502046   82  Linux swap / Solaris

Partition table entries are not in disk order
drakkor@drakkor:~$

---

### Post by Herman on 2006-08-20
Hello,Drakkor, I just installed dsl too, on a logical partition and I just booted mine with GAG.
dsl didn't give me the option to install Grub to the root of the partition on install, it overwrote my MBR bootloader. That's okay. So I booted dsl, opened an ATerm, and got a grub prompt.```
grub
```
Then I did ```
find /boot/grub/stage1
```I didn't really need to do that, I already know the answers, but it's good practice. Then I did ```
root (hd0,6)
``````
setup (hd0,6)
``````
quit
```That installed Grub to the first sector of the dsl partition. 
We need dsl's bootloader at the root of dsl's partition in order for GAG to be able to load dsl. 
I'm not sure what would happen if I did the same thing from Ubuntu, I'll test that later, (install Grub in dsl from Ubuntu - will it be Ubuntu's grub, or dsl's grub?)
Anyhow, it boots up fine from GAG. 
Try again and good luck, Regards, Herman :D

---

### Post by Herman on 2006-08-20
drakkor, if you need to be able to boot dsl first, in order to be able to open your ATerm and install dsl's Grub to dsl's first sector, you should try out Super Grub DIsk, which is free, and only around 500 kb. or so to download. You can find Super Grub Disk at [http://adrian15.raulete.net/grub/tiki-index.php](http://adrian15.raulete.net/grub/tiki-index.php) 
Super Grub Disk will boot dsl for you (for now), then you can fix dsl's grub (instll it where you want).
Regards, Herman :D

---

### Post by Drakkor on 2006-08-20
Yeah,I just booted to the DSL live CD and was going to try to to the terminal there,but I guess that wouldn't work. I will try the Super Grub disk,
Thanks :)

---

### Post by Drakkor on 2006-08-20
Hmmmmmm..... can't seem to use the "Super Grub Disc" to boot to dsl ! 
Another thing I did a
drakkor@drakkor:~$ sudo grub-install /dev/hda7
Man I must have rebooted this thing about 100 times,glad I got a good Antec
430 watt power supply,lol. Any help ?  Thanks ! :(

---

### Post by Drakkor on 2006-08-21
*bump*

---

### Post by Herman on 2006-08-21
Drakkor, My appologies for the slow reply, I just got home from work. :D

It should work to use the same commands as [here]("http://www.ubuntuforums.org/showpost.php?p=1401799&postcount=20") from the dsl (or another Linux live CD that has Grub, to install dsl's Grub to dsl's first sector. 

I just tested Super Grub at booting dsl and I had some trouble using it in menu mode too. I'm still investigating why. The next release of Super Grub will be better.

I am booting in grub CLI mode (press 'c' key when in a grub menu) you can do that either from your hard disk- installed Grub menu or with a menu in Super Grub Disk. 

At the Grub prompt, type,```
root (hd0,6)
```you should get some feedback about the filesystem on hd0,6 partition.
next, after the grub prompt, type ```
kernel /boot/linux24 root=/dev/hda7 
```Then after the grub prompt, type ```
boot
``` Regards, Herman :D

---

### Post by Roberto Rosselli on 2006-08-21
Hi Herman, I'd very much appreciate if you could find the time to look at my post on similar problems ([http://www.ubuntuforums.org/showthread.php?t=240614](http://www.ubuntuforums.org/showthread.php?t=240614)) after Drakkor has solved his. Thanks in advance, and thanks for your tutorial page on grub!

Roberto

---

