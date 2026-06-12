---
title: "Thank you for the help in 8.04 to 10.04 BUT..."
date: 2011-06-13
forum: Installation &amp; Upgrades
---

### Post by RifRaf1961 on 2011-06-13
Hello,
I sincerely appreciate the help you supplied in this thread:

[http://ubuntuforums.org/showthread.php?t=1687962&highlight=upgrade+hardy+wine&page=3](http://ubuntuforums.org/showthread.php?t=1687962&highlight=upgrade+hardy+wine&page=3)

However, my situation is similar, but different. He had Hardy installed by itself on the drive. I have a dual boot WinXP and Hardy setup on a 250GB drive partitioned in half. Each O/S live on their own half of the drive. I really like the detailed explanation you provided, but if I follow those directions am I going to run into problems with Grub and Grub 2? Will I still be able to boot into all three O/S's? I seldom use WinXP but I still need it for Magic Jack. I've spent the last three years getting Hardy to do everything I want and I would hate to lose access to either O/S while I'm getting Lucid to work the way I want. I ran the live CD in test mode and I really would like to upgrade!

I've been reading upgrade threads for over a week and I prefer your method... I just need to make sure it applies to my dual boot configuration too.

Per your request, I've tested the Install CD and it verified okay.
Also enclosed are the screen outputs for gparted and fdisk -l.

 ```
rif@dads-linux:~$ sudo fdisk -l
[sudo] password for rif: 

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcee1a335

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       15200   122093968+   7  HPFS/NTFS
/dev/sda2           15201       30401   122102032+   5  Extended
/dev/sda5           15201       29834   117547573+  83  Linux
/dev/sda6           29835       30401     4554396   82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
16 heads, 63 sectors/track, 620181 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x97464cdb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      206726   104189872+   7  HPFS/NTFS
/dev/sdb2          206727      413452   104189904    7  HPFS/NTFS
/dev/sdb3          413453      620178   104189904    7  HPFS/NTFS

rif@dads-linux:~$ 
```

---

### Post by RifRaf1961 on 2011-06-14
I also have another question too if that is okay. I know there are versions of Ubuntu in the 11.xx range out now too. I've always only "played" with beta releases before and seriously "used" LTS versions. Is the difference between 10.04 LTS and the 11's that great I should wait for a newer LTS to upgrade? I've used my 10.04 install CD in test mode and I am extremely impressed with what they have done since my currently installed 8.04. I am just curious if you think it is worth the wait.

BTW, I didn't show any gparted images of my USB drives because I didn't feel they have any impact on the upgrade. I just use them for storage.

I was hoping to use the method you described before of splitting my Linux partition and sharing the same swap partition if possible.

Thank you...

---

### Post by mastablasta on 2011-06-14
what exactly do you want to do?
 
11.04 has a different user interface. Changes are quite big. it works well for some, some experienced problems or had trouble adjusting and switched to classic desktop (which won't be available in next release), other switched to new desktop environment (KDE, XFCE...)

---

### Post by kansasnoob on 2011-06-14
Sorry to disappear for so long, and thanks for the PM.

I did something stupid yesterday. I have a few nasty food allergies and I ended up eating a piece of pie that landed me in the hospital overnight.

Then I returned home to a broken AC unit, so please be patient while I get my AC working and get my sea legs back under me :)

I want to be sure and look things over closely when my mind is clear.

---

### Post by RifRaf1961 on 2011-06-14
I'm sorry to hear of your hospital adventure kansasnoob. I hate going to the doctor or hospital. Maybe because I spent so much time in them after a motorcycle accident I had in my teens. Be sure to take care of yourself first! My upgrade concerns have waited awhile... they can wait longer without any problem. Like I said before, my 8.04 LTS install does everything I want... I would just "like" to upgrade to a newer version. Please be sure to take care of yourself and needs first!

Thank you for the reply mastablasta. As stated, I downloaded and tried the 10.04 LTS CD in demo mode. I saw how much better it was and decided it would be really nice to upgrade. I was just curious if 11.xx was even that much better than 10.04 LTS and I would find myself wanting to upgrade right away again. Last I looked there wasn't a 11.xx LTS version and I don't like using beta's for anything more than playing with. BTW, I like the Gnome GUI and have never really liked KDE or others I tried.

---

### Post by mastablasta on 2011-06-15
> **RifRaf1961 said:**
> I'm sorry to hear of your hospital adventure kansasnoob. I hate going to the doctor or hospital. Maybe because I spent so much time in them after a motorcycle accident I had in my teens. Be sure to take care of yourself first! My upgrade concerns have waited awhile... they can wait longer without any problem. Like I said before, my 8.04 LTS install does everything I want... I would just "like" to upgrade to a newer version. Please be sure to take care of yourself and needs first!
 

 
ok but what is the reason that you can't upgrade thorugh internet? Also a home folder backup and fresh install might be an easier option. depending on how many extra things you have on your instalation.
 
 > 
Thank you for the reply mastablasta. As stated, I downloaded and tried the 10.04 LTS CD in demo mode. I saw how much better it was and decided it would be really nice to upgrade. I was just curious if 11.xx was even that much better than 10.04 LTS and I would find myself wanting to upgrade right away again. Last I looked there wasn't a 11.xx LTS version and I don't like using beta's for anything more than playing with. BTW, I like the Gnome GUI and have never really liked KDE or others I tried.
 
11.xx has a completelly different interface. also for some reson i can't get it to work on my computer. that is not to say that it' crappy.. it's just very much beta. the new interface lack many features. thoguh they have classic gnome as fallback it wont' be there in October when new version is launched.
 
KDE changed a lot lately. XFCE is kind of like Gnome 2.x (the gnome you know), while Gnome (ver 3) is now complely changed from what it was in 8.04 days. The original Gnome is going to have gnomeshell interface while Cannonical developed unity as they had a fallout with Gnome shell developers :-)  have a look and new Gnome and Gnome shell: [http://www.gnome.org/](http://www.gnome.org/)
 
It's already part of latest Fedora and it will be part of Ubuntu in 11.10 (still not an LTS)

---

### Post by RifRaf1961 on 2011-06-15
Thank you mastablasta, I think you have helped me to decided on using the 10.04 LTS version. I have old hardware. My BIOs is copyright 1994. I also have an old TV Card which "TV Time" detected and works perfectly. My networked Canon Printer is not supported by Canon for Linux. I found drivers in China that work just fine. I had similar issues with other hardware and software. I even had to update my WINE to version 1.2 for a couple Windows programs I needed that wouldn't work in the default 1.0 version. My PC is plenty fast, AMD 2900 and works fine with everything I need so there is no reason to upgrade hardware.

I don't want to dump my perfectly working 8.04 LTS to find out I can't get a Beta version working at all... and I still have my doubts about even the 10.04 LTS working right for awhile, if at all. That is why I want to keep my version and add stuff to the other at my leisure. Maybe when it is running right I can copy off it's home, do a fresh install and replace it.

I'm 50 years old and have played the upgrade game on PC's since 286's (I actually started with Commodores). I can't tell you how many 1000's I've spent over the years to stay current. I even spent $1,200 on 32MB (yes, Meg) of RAM for my long forgotten 486-66. This PC works and is fast enough for my needs. When it isn't anymore, then I'll upgrade.

---

### Post by mörgæs on 2011-06-15
> **RifRaf1961 said:**
> ... and I still have my doubts about even the 10.04 LTS working ...

Then the solution is simply to boot in live mode and see how it goes.

---

### Post by RifRaf1961 on 2011-06-15
I have booted from the 10.04 CD in "test mode". I viewed the different menus, ran a few programs and decided I really like the new GUI. That is why I decided it was time to consider an upgrade. However, in demo you can't really install anything to insure the new O/S is going to work with all my devices and programs I want and need to use. The only way I would consider doing an upgrade thats wipes, alters or damages my current Linux half of the drive would be if I made an image of it first that I could do a complete restore of later if needed.

---

### Post by mörgæs on 2011-06-15
If you want, you can make an image using Clonezilla before you throw away 8.04, but if it was my computer, I don't think I would bother. 10.04 has now matured one year since release.

---

### Post by mastablasta on 2011-06-16
> **RifRaf1961 said:**
>  However, in demo you can't really install anything to insure the new O/S is going to work with all my devices and programs I want and need to use. 
.
 
I believe you can for the most part. problem is it is lost during reboot.
 
> 
The only way I would consider doing an upgrade thats wipes, alters or damages my current Linux half of the drive would be if I made an image of it first that I could do a complete restore of later if needed.
 
I see where you are comming from - if it works why change. The only reaosn here is support. it's much easier to maintain if you have software support.
 
And yes an option is to make a clone of the disk with clonezilla. 
Also i am not sure how well Mint backup would work on this oldie... but if it did it would be great as it backup all settings and also i think programmes. and it's really easy  to handle as it has basicly only 4 buttons. 2 to back up and 2 to restore.

---

### Post by RifRaf1961 on 2011-06-16
I think I would actually use Ghost. I have a solid version that boots from floppy so no part of the O/S is in use and can't be copied. It will write a single file out to DVD (spanning multiple if needed), to USB device like my Western Digital external drives I use for backup and storage or another drive in the computer or network. Ghost doesn't care which O/S is being backed up. Just a couple mouse clicks and it does it very fast. You can even verify the file integrity too. It has different levels of compression but I always select maximum because it doesn't take any longer on my system. I've never had any problems with it on restores either. They are very fast and have always worked perfectly in the past.

BTW, I did attempt installing a few things on the test drives of 10.04. They said they installed but they didn't do anything. One example was Flash for Firefox. I think another was the nvidia upgrade drivers but don't quote me on that one. Every time I went to something needing Flash it kept saying I needed to install it even though I had... a few times.

---

### Post by kansasnoob on 2011-06-17
Sorry for the long delay, it's taken a while to really begin getting the wind back in my sails :)

**[COLOR="Red"]Please read this all before beginning[/COLOR]** and if you have any questions at all just shout. Better safe than sorry.

Anyway, I think 10.04 makes a great deal of sense for you ATM. It will be supported until April 2013 which means it is the longest supported version of Ubuntu still using Gnome version 2. Also, since it's had a bit over a year to mature, most show-stopper bugs should be fixed by now.

Natty (11.04) still uses gnome2 but defaults to the Unity DE which some people love, some people hate, and others (including myself) find simply confusing. Natty does however include the ability to boot into either the classic DE or classic w/o effects, but still it's only supported until October 2012, so Lucid (10.04) gives you an additional 6 months of support.

From Oneiric (11.10) forward Ubuntu will use gnome3 with the Unity DE as default, although both the classic "mode" and gnome's gnome-shell DE will be somewhat easy to obtain ...... but IMHO gnome3 is lacking in many areas ATM. So much so that I've begun to shift my early development testing onto Lubuntu/LXDE.

Anyway, regarding a multi-boot as an option rather than just an upgrade or a replacement installation, it has the clear advantage of allowing you to continue using your old OS until you manage to work through any unexpected problems you might encounter, eg; video drivers, package installation, etc. Another cool thing is that, once you have your new Lucid purring like a kitten, you can easily replace the old Hardy with something new like Natty or Oneiric to see what you think of Unity and gnome3.

I notice you voiced some concern about grub/grub2 and that's wise on your part. IMHO grub2 is about the best thing since sliced bread but it's different. I only recently discovered that Super Grub Disk has produced a Super Grub2 Disk:

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

You'll notice that it says there:

> Does not fix GRUB
Does not fix GRUB2
**[COLOR="Red"]Boots into many systems and GRUB2 ones![/COLOR]**
Can’t regenerate grub menues
Can’t check filesystems and fix them
Does not fix Windows MBR

Yeah, that's what we want! I've never liked using anything but Ubuntu to "fix" Ubuntu's grub or grub2. Using the old SGD or the new Rescatux disc may work, but I just don't like it.

OTOH that new Super Grub2 Disk has only one purpose, to boot things when your bootloader gets messed up. That way you're not stuck in a panic if or when things go wrong. Then once you get booted you can both continue working and it's generally easier to fix grub (regardless of version) once you're booted into the OS.

So, if it's not inconvenient, I highly recommend that you (or anyone) add that Super Grub2 Disk to your arsenal of super important tools. It's always better to be prepared ;)

Now, the next thing one must understand before considering a multi-boot is Ubuntu/Linux device designations. Let's just look at your layout:

```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcee1a335

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       15200   122093968+   7  HPFS/NTFS
/dev/sda2           15201       30401   122102032+   5  Extended
/dev/sda5           15201       29834   117547573+  83  Linux
/dev/sda6           29835       30401     4554396   82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
16 heads, 63 sectors/track, 620181 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x97464cdb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      206726   104189872+   7  HPFS/NTFS
/dev/sdb2          206727      413452   104189904    7  HPFS/NTFS
/dev/sdb3          413453      620178   104189904    7  HPFS/NTFS

```

Each device has a designation, eg; /dev/sda or /dev/sda1. The **/dev/** quite simply indicates "device" and the **sd** simply indicates "hard drive". At one time drives used both "hd" or "sd" to indicate the type of drive but most modern Linux distros have begun using "sd" to indicate all hard drives. The next two characters in the designations are very important, but should be simple to understand. 

The first character following **sd** indicates the drive designation. In your case "sda" indicates the 250GB drive and "sdb" indicates the 320GB drive. Get it? The **a** basically indicates drive #1 and the **b** indicates drive #2.

Then the partitions are indicated by the next character which is always numeric, eg; 1, 2, etc. So we can see that your 320GB drive (sdb) has 3 primary partitions of equal size: sdb1, sdb2, & sdb3 which are obviously all data partitions. Of course you want to leave all of those partitions untouched!

Now, your 250GB drive has 4 partitions. The first (sda1) is obviously the Windows partition and it's a primary partition. You also want to leave that partition untouched! The next 3 partitions are as follows:

sda2 = extended partition
sda5 = ext3 (obviously your Ubuntu 8.04)
sda6 = SWAP

Just a brief explanation, Linux loves to use extended partitions which is a great thing. By default hard drives will only allow 4 primary partitions, but the use of an extended partition will allow the creation of a large number of "logical" partitions. 

Basically the extended partition is like a "shell" that can contain a large number of logical partitions, and you might wonder why the numbering jumps from sda2 to sda5. Basically the extended partition is recognized the same as a primary partition, and primary partitions are typically numbered 1 thru 4, whereas logical partition numbering begins with 5.

**[COLOR="Red"]Note[/COLOR]**: *While it's doubtful you'll encounter this, you still need to know that occasionally Ubuntu will recognize hard drives in a different order upon reboot. I discussed it here when I first encountered it*:

[http://ubuntuforums.org/showthread.php?t=1659542](http://ubuntuforums.org/showthread.php?t=1659542)

*In your case it would be easily noticed because the partition you want to resize is sda5 and you have no sdb5. I just want you to be aware of any pitfalls.*

Anyway your partition sda5 appears to be your Ubuntu partition and since it's about 112GB with 96GB free space that would be the one you'd want to resize for the new install. To do that you'd want to boot the Live CD, choosing to try rather than install, and in the live desktop open Gparted.

Once in Gparted you'll first need to right click on the SWAP partition (sda6) and select "swapoff". That is necessary so the extended partition will be unmounted. Then right click on sda5 and select "resize/move", then drag the right side to the left as far as you choose (I suggest giving each about equal space). Then click on the green arrow/Apply, to apply the resize. The graphics in this post may be helpful:

[http://ubuntuforums.org/showpost.php?p=10487161&postcount=24](http://ubuntuforums.org/showpost.php?p=10487161&postcount=24)

Next you'll want to right click on the newly created free space and select "new", and next select "add". (You can just accept the defaults because you'll be asked again during installation of 10.04). And once again click on apply. The graphics here may be helpful:

[http://ubuntuforums.org/showpost.php?p=10487444&postcount=26](http://ubuntuforums.org/showpost.php?p=10487444&postcount=26)

I'd expect the new partition to be numbered "sda7". Whatever that new designation is you need to remember or make a note off it because that's where you'll want to install the new 10.04. The installation process is reviewed in that last link.

An additional note about grub installation, when you get to the last installation screen:

[ATTACH]195349[/ATTACH]

If you click on the advanced button you can change where to install grub. By default grub will install to sda, **that should be correct** so I recommend leaving it alone! Should you later find that grub needs to be installed elsewhere we can cross that bridge when we come to it.

Never, ever install grub to a Windows partition! It borks Windows!

Have I confused you yet?

---

### Post by RifRaf1961 on 2011-06-17
Hi kansasnoob... glad you are feeling better and no, you haven't confused me yet.

However, I've read a few of your guides and I don't ever remember seeing this step:

> Once in Gparted you'll first need to right click on the SWAP partition (sda6) and select "swapoff". That is necessary so the extended partition will be unmounted.

By, "so the extended partition will be unmounted" do you mean the one I will be resizing?

Also you said:
> I notice you voiced some concern about grub/grub2 and that's wise on your part. IMHO grub2 is about the best thing since sliced bread but it's different. I only recently discovered that Super Grub Disk has produced a Super Grub2 Disk

I downloaded and made a Super Grub 2 disk as suggested. I just hope I won't need it. I've always heard 8.04 uses Grub and 10.04 uses Grub 2.  Do they play well together or am I later going to be manually editing one or the other so everything will boot?

Thanks

---

### Post by RifRaf1961 on 2011-06-18
Hi again,
Just thought I'd let you know I have a triple boot system now. WinXP still lives on it's half of the 250GB drive and I split the Linux half in two. You were right kansasnoob, 10.04.2 LTS lives in the new ext3 partition "sda7" and shares the same swap partition "sda6" with my fully functional 8.04 LTS install in "sda5".  When I did the install tonight, 10.04.2 couldn't find any compatible O/S to import settings from; so I have a lot of work ahead of me to get it the way I want (useable like my old version). I can't begin to tell you how glad I am I decided to do it this way verses a wipe and install.

I don't seem to have any problems with Grub versions. I've used all three O/S's tonight a few times each and there were no issues at all.  This was really my main concern about doing the upgrade.  I didn't want to end up with a system that had three O/S's installed but refused to boot.

Perhaps I should have put something in the thread title about triple boot system and not be quite as vague by referring to another of your thread replies. 

I didn't mention I have a degree in Computer Science and went back recently and got another degree in Network Administration. I've also worked as a Network / Computer Administrator for over 20 years. I understand your guides are written (quite well) so anyone can follow them and were not directed totally for my benefit.  Regardless, I want to thank you and the others that posted in this thread for all the help and advice.

I consider this thread closed unless you care to answer the two questions in my directly previous post.

Thanks again!

---

### Post by mörgæs on 2011-06-18
Good, then please mark it closed using 'thread tools'. Have fun in 10.04.

---

