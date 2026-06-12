---
title: "Let me know when grub2 works on fakeraid"
date: 2009-11-26
forum: Installation &amp; Upgrades
---

### Post by Marco7 on 2009-11-26
The live instalation Cd for Ubuntu 9.10 x6bit Karmic Koala worked great. It recognised my fakeraid RAID-0 parition table and install the system, just like it should, no dmraid needed.  My enthusium was short lived, however, because as you can probably can guess, grub2 instalation failed.  Installing grub via the "fakeraidhowto" is easy enough but there seems to be no similar solution for grub2.  I can't remember where but I read this, but it seems to be an "open bug", i.e. has no present fix.  

I feel like it's close though.  I'm hoping that within six months it's fixed and the install Cd will just work, or that there will be a method like that outlined in the fakeraidhowto for installing grub2.

---

### Post by whoop on 2009-11-26
Just out of interest why don't you use software raid? My mobo supports fake raid but I just use software raid because fake raid and software raid are both done with the cpu anyway and fake raid is not supported by ubuntu. Also I find software raid more flexible.

---

### Post by Marco7 on 2009-11-27
I dual boot with Windows XP x64.  As far I knew that was just how it was done in Windows.  I have a DFI NF4 board and use the corresponding nvidia raid drivers, with the raid controller set to on in the BIOS.

I would be happy to run my raid set via another method if it worked for both windows and ubuntu.

This is my understanding:

The new distribution of Ubuntu 9.10 does what it predecessors can not by recognising an array like mine, and reading it's pre-existing partition table, without having to install dmraid.  Installing dmraid isn't a big deal, but the grub instalation would still fail, and must be installed manually, via the method out lined in the "fakeraidhowto".

Grub2, however, is incompatible with fakeraid and will not run within a fake raid installation.  (Is this correct?!?)

Also if the fakeraidhowto wasn't updated for Karmic and grub2 I probably couldn't figure out how to install it manually.:(

---

### Post by whoop on 2009-11-28
> **Marco7 said:**
> I dual boot with Windows XP x64.  As far I knew that was just how it was done in Windows.  I have a DFI NF4 board and use the corresponding nvidia raid drivers, with the raid controller set to on in the BIOS.

I would be happy to run my raid set via another method if it worked for both windows and ubuntu.

This is my understanding:

The new distribution of Ubuntu 9.10 does what it predecessors can not by recognising an array like mine, and reading it's pre-existing partition table, without having to install dmraid.  Installing dmraid isn't a big deal, but the grub instalation would still fail, and must be installed manually, via the method out lined in the "fakeraidhowto".

Grub2, however, is incompatible with fakeraid and will not run within a fake raid installation.  (Is this correct?!?)

Also if the fakeraidhowto wasn't updated for Karmic and grub2 I probably couldn't figure out how to install it manually.:(

Well if you intend to use the raid array in both windows and linux, software raid is not the way to go. You need hardware or fake raid for that...

---

### Post by jpichie on 2009-12-03
I am in the same boat, and I have been searching the globe to get this to dual boot with Windows 7 on fakeraid. You think this would have been something they tested... BEFORE releasing it. I got it working, but not like I wanted, by installing Ubuntu 9.10 to my 500GB backup drive (not RAID).
Maybe they will get it right with 10.04 in 5 months from now...

---

### Post by darkod on 2009-12-03
One solution I've seen is to create 100MB /boot partition outside of the array.
And as far as raid support goes for 9.10, ubuntu says to use the alternate install cd for LVM and/or RAID, not the standard desktop /livecd. Haven't tried installing on raid myself, but they clearly say to use alternate install image. Maybe it makes a difference.

---

### Post by jpichie on 2009-12-03
Tried it, it doesn't.
Both Grub and LILO will not install on the fakeraid partitions.
As for the 100mb boot partition, when you say outside of the array, do you mean on a separate HDD?

---

### Post by darkod on 2009-12-03
OK. Maybe /boot partition outside the raid is the answer, maybe it doesn't work anyhow on fakeraid. Not too familiar what fakeraid exactly is, but it sounds fake. :)
I saw one thread where they managed to install on software raid but if you want to dual boot with windows that might not support it. Not experienced with raids.

---

### Post by jpichie on 2009-12-03
I got dual boot working when I installed Ubuntu and grub on a seperate hard drive.
Also, the alternate CD recognizes that you have a SATA RAID setup, and asks if you want to use DMRAID. 
Grub still will not install.

I am hoping that Ubuntu 10.04 will have fixed this. Alpha starts in 6 days.

---

### Post by darkod on 2009-12-03
If you are impatient for 10.04, they have daily-build here [http://cdimage.ubuntu.com](http://cdimage.ubuntu.com) in the daily-builds folder. Of course, not sure what you can expect from it in this stage.

---

### Post by jpichie on 2009-12-03
Why couldn't this just be simple...
Install Windows 7, then install Ubuntu and overwrite the MBR...
Beta software should not be the default in a stable release.

---

### Post by rDwyP44y on 2009-12-06
Ok I've read this, but it still seems unclear to me what "FakeRaid" is.

But I do understand that it doesnt work with Grub2...

but i am still in search for a result from my previous post
[http://ubuntuforums.org/showthread.php?p=8449985#post8449985]("http://ubuntuforums.org/showthread.php?p=8449985#post8449985")

I really would like to know how go about this from my post..

---

### Post by jpichie on 2009-12-06
So I created a 100mb partition on a non-raid HDD I use for backups. Installed /boot to it, and grub2 installed fine. I was able to reboot and use Kubuntu 9.10 no problems. Problem is, now I could not get into Windows 7. Kept giving me "Error: Invalid Signature". Went into Kubuntu again, ran update-grub2, gave me a mapping error on my fakeraid Windows install.

Looks like I will be waiting until Lucid Lynx, or a Grub2 fix.

---

### Post by danwood76 on 2009-12-07
Guys just install grub1.

Grub 2 doesnt yet support Dmraid but there is no real advantage as of yet to use grub2 over grub1.

I have been using grub 1 in my dual boot Ubuntu and Windows since early alphas and re installed when the full release came out.

@ Jpichie
The invalid signature thing can be sorted by editing the grub config files, this happened on my laptop. I fixed it by removing the lines locking it into a specific UUID.

---

### Post by jpichie on 2009-12-07
So is there a way to install grub-legacy without using a liveCD (letting GRUB2 fail install first)? Or will I have to install it, and then boot into a LiveCD, mount my linux partition, and chroot into it?

---

### Post by wkulecz on 2009-12-07
> Grub 2 doesnt yet support Dmraid but there is no real advantage as of yet to use grub2 over grub1.


The fly in the ointment is by default the 9.10 installer wants to use ext4.  Grub1 doesn't support ext4.

I agree DMraid is the inferiour software raid option, but its the only option if the array to be be shared with Windows.

--wally.

---

### Post by danwood76 on 2009-12-07
> **wkulecz said:**
> The fly in the ointment is by default the 9.10 installer wants to use ext4.  Grub1 doesn't support ext4.

I agree DMraid is the inferiour software raid option, but its the only option if the array to be be shared with Windows.

--wally.

Dmraid is not inferior to software RAID, it is infact the opposite as it allows booting off of soft RAID0/5/10 volumes. I have been using dmraid since I started using Linux and its never failed me.

Grub1 loves Ext4, I am using Ext4 for all my partitions.
Please get your facts correct before posting.

The only way to install grub1 is to chroot into the install. Fortunately when the installer crashes it leaves the /target dir ready for you to chroot into. (I'm fairly sure everything is mounted too)

Just follow the fakeraidhowto for jaunty in the community docs to install from the live CD. (its virtually copy and paste)
[https://help.ubuntu.com/community/FakeRaidHowto#Live%20CD%20Installation%20%28Ubiquity%20graphical%20installer%29](https://help.ubuntu.com/community/FakeRaidHowto#Live%20CD%20Installation%20%28Ubiquity%20graphical%20installer%29)

---

### Post by wkulecz on 2009-12-07
> Grub1 loves Ext4, I am using Ext4 for all my partitions.
Please get your facts correct before posting.


from  [http://kernelnewbies.org/Ext4](http://kernelnewbies.org/Ext4)
"One very important thing to keep in mind is that there is NOT Ext4 GRUB support. Well, that wasn't exactly true: There is grub support, but it's not very spread in the currently available distros. There's ext4 support in the GRUB2 development branch, but since GRUB2 is not stable, most of distros are using the 0.9x versions."

If this has changed recently I stand corrected, but then I put the use of grub2 over grub1 in 9.10 clearly in the "more trouble that its worth" department that will PO a lot of people who uprade from 8.04 to 10.04 without having played with 9.10, when they discover that everything they know about grub is wrong!  I was willing to accept grub1 not supporting ext4 as a valid excuse for foisting grub2 on the unsuspecting Ubuntu 9.10 user, if this is untrue its a black eye for Ubutu IMHO.

Moving from lilo to grub was painful, but at least the benefits were clearly obvious once you got over the initial learning curve. So far all I can say is why grub2?

The other is a matter of opinion depending on what is most important to you.  DMraid is essential to share a raid with Windows.   But in a pure Linux situation, I'd bet most admins would wish DMraid would just go away.

Personally after using raid1 and raid5 on 6.06 I've relagated raid to the more trouble than its worth category too.  YMMV.

--wally.

---

### Post by jpichie on 2009-12-07
I'm starting to think it would just be easier to install 9.04 with Grub, and do an update to 9.10.
I mean the only huges differences in 9.10 is ext4 and grub2, and obviously grub2 is pooched.

Anyone know if Lucid Lynx is working with grub2/raid yet?

---

### Post by danwood76 on 2009-12-08
Gurb 1 has supported Ext4 since the start of the year. (with a patch) but has been available since jaunty in Ubuntu.
Grub2 is better in many ways from better autodetection scripts to a better and quicker boot.
Also grub1 is very old grub2 is new and more Ubuntu style!

Jpichie you still have to use the fakeraid howto I think and chroot.
At least I did in jaunty anyway.

Grub2 + dmraid should be working in lynx now. Here is the associated bug:
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/392136](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/392136)

---

### Post by wkulecz on 2009-12-08
> Also grub1 is very old grub2 is new and more Ubuntu style!

Old?  If it ain't broke, don't fix it!

Style? Nobody cares about the boot loader unless it screws up!

The docs and recovery/reinstall howtos should be on the Live CD with a desktop link pointing to them, whenever some fundamental change like this is made.  

Grub 2 broke on my 9.10 install.  Without another working computer available to Google with, I'd have thrown 9.10 straight to the trash.  While it was easy to fix, it was also a total waste of my time doing so.  Linux has no hope for adoption by the average computer user if this kind of arcane knowledge continues to be required.

An awful lot of the threads here involve grub2 issues.  Clearly it was not yet ready for "prime time".

For a couple of releases during the move from lilo to grub, RedHat/Fedora installers asked to choose lilo or grub.  I choose lilo until I learned enough about grub to trust it.  Ubuntu should have done the same with grub/grub2.

--wally.

---

### Post by jpichie on 2009-12-08
Any chance that the Grub2 fix for Lucid Lynx made it's way into the daily builds?
I'll give it a shot today.

---

### Post by danwood76 on 2009-12-08
@wkulecz

Ubuntu is a cutting edge (pretty much bleeding edge) distro built on unstable debian. Gurb 2 was always a move that had to happen and it just so happens they took the jump before the LTS release so it could be tested before hand. It was also in Jaunty and all testers OK'd it. (Including me!)

Grub2 is fine but its configuration is mainly automagic and manually editing it isnt well documented like Grub 1. But on my laptop it found all OS' and can boot each one just fine, it is better in Grub 1 in that respect and so the move should be a good one.

IMO installing grub 1 during the install of 9.10 was exactly the same as installing it in previous versions of Ubuntu with dmraid. No issues from me.

@jpichie

It looks like the bug has the "Fix Released" status as of yesterday which means it should be in the daily builds today (if not updatable via synaptic). But I am not on the Lynx yet due to having a lot of work on at the moment so I can't gaurantee it.

---

### Post by jpichie on 2009-12-08
Thanks for the help guys, you said the dmraid guide that was linked in here should help me get the install of 9.10 with grub-legacy working correct? I'd rather do that, as I love KDE compared to GNOME. I will give it a shot, but I will also try out the 10.04 Alpha to see how that goes.

---

### Post by jpichie on 2009-12-08
Just as an FYI, I tried Lucid Lynx daily from today... still a no go.

---

### Post by jpichie on 2009-12-08
Hey Guys:
I'm in the middle of installing grub through the Jaunty FakeRaid setup, but now I am getting "Unknown Partition Table Signature" when going into grub, as well as "Error 15: File Not Found" when trying to install grub. I even created a /boot/grub/device.map file with my EXT4 partition.
Help PLEASE! I am so close!!

Could it be the EXT4?
NVM, same errors with EXT3, any ideas?

---

### Post by cedric.driard on 2009-12-19
Hello
In first, I'm sorry but I'm french and my english isn't so good

I would like to know if you think if this installation is possible
 - ubuntu 9.10 karmic koala (with grub 2) in dual boot with WXP SP3
 - a fakeraid for raid 1
 - both OS on the same hard disque

like this :
 - install ubuntu with the alternate CD
 - choice installation without soft boot
 - finish installation
 - start with the live CD
 - load grub legacy and the patch for grub 1 on ext4 partition
 - install grub legacy and the patch
 - restart computer


best regard

---

### Post by danwood76 on 2009-12-20
Hi There,

Your english is fine!

You dont actually need to use the alternate CD.
You can install from the Live CD to save CD media and downloading images.

The patch I spoke of is already integrated into grub so theres no need to download sperately. You just need to follow the fakeraid howto to install via the live CD.
[https://help.ubuntu.com/community/FakeRaidHowto#Live%20CD%20Installation%20%28Ubiquity%20graphical%20installer%29](https://help.ubuntu.com/community/FakeRaidHowto#Live%20CD%20Installation%20%28Ubiquity%20graphical%20installer%29)

Note in karmic (9.10) that you don't need to "sudo modprobe dm-raid4-5" (step 4.a) and for step 6 I would use gparted which is the partition editor in the System -> Admin menu.

And the rest is pretty much copy and paste.

Good luck!

---

### Post by gilson585 on 2009-12-20
if you want updated instructions for installing 9.10 onto fakeraid check out my post here [http://ubuntuforums.org/showthread.php?t=1360445](http://ubuntuforums.org/showthread.php?t=1360445)

---

### Post by cedric.driard on 2009-12-21
Thank for your responses, but I have got some questions yet

Gilson585 : in your instructions, you don't say if it's a dual boot and if the root must be an ext3 partition or if it can be an ext4, can you adjust it

Danwood76 : I know this instructions, I installed karmic with it but with the alternate cd, I think it was more easy (no code) but grub 2 didn't installed, I think it's because grub2 don't accept fakeraid, so I have karmic with no boot sequence. 
Now I read precisely instructions with live cd and I anderstand why it must be work like this so I going to test but it will not be easy
But the only point which is not clear is with this instructions if gub legacy will accept ext4 or I will have to load a patch ?

Thanks for this very good forum it is better better and better than the french one and I suppose I will speak a better english few time ago with it :P

---

### Post by danwood76 on 2009-12-21
The grub legacy (just grub in the package manager) will work with ext4.
Follow the guide that gilson pointed to as it looks fairly complete.

Also you must use the karmic (Ubuntu 9.10) version of the live CD.

You can then add the dual boot portion the normal grub way which is posted all over the internet. (it will hopefully do it for you I think)

---

### Post by gilson585 on 2009-12-21
Yes danwood is correct it works with ext4, also it will detect a dual or triple boot automaticly. Also if linux was installed first and later you install windows and lose grub you can use this to recover it.

---

### Post by cedric.driard on 2009-12-22
many thanks

I just have to try now (but after Christmas day) :P

---

### Post by jpichie on 2010-01-21
By the looks of it, FAKERAID and GRUB2 still does not work in Ubuntu 10.04 Alpha1 or Alpha2.
Has anyone else had any luck with this?

---

### Post by LinuxTAd on 2010-03-30
I am struggling now with it. I am not trying to install to the fakeraid, I simply want to boot to it and am having no luck with the raid 0.

I jumped to 9.10 to get the "module updates" that were not present in Jaunty repos. I am half tempted to jump to Lucid, by reading this thread (and I could be wrong) it seems there are patches being released for it and not 9.10 or 9.04...

---

### Post by kniklawski on 2010-04-09
I am also having the same problem.  I just got a new Sony Vaio Z Series, which is by far the best computer I have ever owned.  Of course the first thing I try to do is install Ubuntu (because my existence depends upon it) and to my dismay, the bootloader won't install.

I've been searching everywhere for a solution for this, and still no luck.  

If anyone finds an answer to this, please post ASAP, and I'll do the same.

I've heard that you NEED to use the alternate install, and I've heard you NEED to use the live cd.  I've tried both unsuccessfully.

---

### Post by trashmonkey on 2010-04-17
I just installed 10.04 beta2 with fakeraid and Grub2 on ext4.  What I had to do was use the LiveCD to install with.  The AlternateCD doesn't have the better install option.  What I mean by this is go through the liveCD installation, just before you set all of your parameters, it should ask you where you want to install Grub2.  Click ADVANCED.  That's the difference.  It will allow you then to choose your \boot partition and then it should install fine.  Did for me!

---

### Post by cedric.driard on 2010-05-06
So do we are able to say that grub2 is working with fakeraid
is there anybody tried this test ?
is someone tried to make an update of ubuntu 9.10 with grub legacy to ubuntu 10.04 with grub legacy and after make an updtae of grub legacy to grub 2 ?

---

### Post by danwood76 on 2010-05-06
Today I installed Lucid from the Live CD.

The installer worked perfectly and I now have grub2 and my dmraid RAID0 working perfectly. This is on a jmicron RAID (I had to modify dmraid to get it to work but that is unrelated to grub).

I am booting straight of my RAID0 partition.
All I had to do was modify the advanced settings of the last step of the installer so it installed grub to /dev/mapper/jmicron_XXX

I would expect that if your system works with dmraid then you should have no issues.

---

### Post by gilson585 on 2010-05-09
my friend ashakeandfrys was able to get it to install on his machine as well. no fuss worked right after the install. Lucid 64bit desktop, Asus P5N-D, NVRaid0 on Nvidia 750i SLI chipset. It was such a headache in the past to get it to work and now it just does like it should.

---

### Post by Klark1988 on 2010-05-13
> **gilson585 said:**
> my friend ashakeandfrys was able to get it to install on his machine as well. no fuss worked right after the install. Lucid 64bit desktop, Asus P5N-D, NVRaid0 on Nvidia 750i SLI chipset. It was such a headache in the past to get it to work and now it just does like it should.

I just installed 10.04 on my fakeraid system on the GA-MA770 (RD770 chipset). It worked without any problems.

So, I think we finally can say grub2 works on fakeraid!

---

### Post by jpichie on 2010-05-14
I tried install Ubuntu 10.04 on my main rig (3x 500GB drives in RAID0).
It sees everything fine during install, even sees the /dev/mapper partitions when asking me where to install grub2. Problem is, I pick /dev/mapper/mapperlettershere/windows1 and it tries to install it to /dev/sda and fails... Any ideas here people?
Thanks,

---

### Post by quequotion on 2010-05-20
> **danwood76 said:**
> Today I installed Lucid from the Live CD.

The installer worked perfectly and I now have grub2 and my dmraid RAID0 working perfectly. This is on a jmicron RAID (I had to modify dmraid to get it to work but that is unrelated to grub).

I am booting straight of my RAID0 partition.
All I had to do was modify the advanced settings of the last step of the installer so it installed grub to /dev/mapper/jmicron_XXX

I would expect that if your system works with dmraid then you should have no issues.

Is it possible to do this with an existing install?

I've upgraded from Intrepid to Jaunty to Karmic to Lucid and I still use Grub legacy.
As I see it, the biggest hurdle to overcome is that grub is currently installed in the bootsector of /dev/sda....

I also have a RAID:0 consisting of /dev/sda1, sdb1, sdc1, and sdd1.... I don't really understand the mechanics of grub being installed on only one of the partitions either (?_?) but I think that's the reason I get a lot of warnings in syslog that /dev/sda1's sectors are out of range (it has the whole 2TB raid's map but the drive itself is only 500GB)...

Everything works just fine at the moment (even ext4!), but I've heard grub2 might boot faster so if possible I'd like to upgrade.

---

### Post by cgb223 on 2010-05-27
so does this mean it works or it still has issues? I would like to install this soon, but i cant risk crashing my computer a few days before exams.

---

### Post by ronparent on 2010-05-27
My understanding is that if you are installing to the raid, in screen 8 you have to select 'advanced' and then enter /dev/mapper/<yourraidarray> (as found in location /dev/mapper/) as the point to install the grub MBR to. You might want to wait until after exams.

---

### Post by piteer1 on 2011-10-12
I see no reponse for long time. Did anybody managed to install ubuntu with grub 2 on fakeraid?
I know that everyobdy is speaking about software raid but it's not an option for dual boot. For me instalation wasn't a problem but i'm having now one while booting. I'm getting: initramfs prompt - disk by uuid does not exist. I didn't have time yet to try to generate correct uuid by hand and put it int the config, but does grub2 supports now fakeraid at all?
Still I think if this method succedess I will have to replace config everytime the kernel changes (as I remember it always calls grub-update).

---

### Post by gilson585 on 2011-10-12
Fakeraid on ext4 using grub2 does indeed work out of the box using 10.4 and newer. There are 2 catches though. I'm fairly certain you must use the livecd and you must click advanced at step 8 of 8 during install and select the correct location for grub to install (/dev/mapper/<yourraidarray>) For example the output would have shown "nvidia_cffbdeda, nvidia_cffbdeda1,  nvidia_cffbdeda2" where nvidia_cffbdeda is the hdd. All the others  listing a # on the end are the partitions, pick the hdd. It's been a while since I have needed to do this but if need be you can also re-install grub if you like just follow the instructions in the following post.

---

### Post by gilson585 on 2011-10-12
Using your livecd boot the pc and "try ubuntu"

1. Open a terminal: Applications, Accessories, Terminal.

2. [B]ls /dev/mapper
[/B]In this example the output would have shown "nvidia_cffbdeda,  nvidia_cffbdeda1, nvidia_cffbdeda2" where nvidia_cffbdeda is the hdd.  All the others listing a # on the end are the partitions. If you don't  know what partition is the root of your installation check out *gparted* or **sudo fdisk -l** I will use nvidia_cffbdeda1 in the following steps as an example for mounting and chrooting into the installation.
  
  3. Mount the installation
**sudo mount /dev/mapper/nvidia_cffbdeda1 /mnt**
*If this fails use *nautilus* (*thunar* in xbuntu) to mount your Ubuntu root partition then use **mount** to find the mount location. This location will be used in place of **/mnt** in the following steps.[FONT=monospace]
[/FONT]**for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt$i; done**

4. Login into the installation
**sudo chroot /mnt**

5.Fetch most recent package lists[B]
apt-get update[/B]

6. ##Not required but optional if it's trashed beyond use
    Remove GRUB2
**apt-get purge grub2 grub-pc grub-common**
**rm -R /boot/grub**
##The system will be unbootable until another bootloader is installed.

      7. Install GRUB2
**apt-get install grub-pc**
**update-grub**
[B]grub-install /dev/mapper/xxx
grub-install --recheck [/B]**/dev/mapper/xxx**##note please substitute your hdd in this line (mine would have been *nvidia_cffbdeda*)

8. Exit *chroot*
**CTRL-D** on keyboard or **exit**

9. Unmount virtual filesystems. Run the following as a single command
**for i in /sys /proc /dev/pts /dev; do sudo umount /mnt$i; done**

10. Unmount the Ubuntu partition
**sudo umount /dev/mapper/xxx**

11. Reboot

BIOS boot order can also affect your machine so make sure it's correct
In some extreme cases it's necessary to remove other hard drives from  the sys as some cheap motherboards lack the understanding of fakeraid  and tell IDE devices to boot first.

If you still have problems look around, here are some good links to try
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[https://help.ubuntu.com/community/FakeRaidHowto#Live%20CD%20Installation%20%28Ubiquity%20graphical%20installer%29]("https://help.ubuntu.com/community/FakeRaidHowto#Live%20CD%20Installation%20%28Ubiquity%20graphical%20installer%29")

---

