---
title: "Installing Edgy using fakeraid (AMD64)"
date: 2006-12-10
forum: Installation &amp; Upgrades
---

### Post by Psylocke on 2006-12-10
I am trying to install Edgy (AMD64) on Nvidia fakeraid using the following guide: [https://wiki.ubuntu.com/FakeRaidEdgy](https://wiki.ubuntu.com/FakeRaidEdgy)

I'm having a problem to get the raid in /dev/mapper, I think because of the following:

When running dmraid -s, it says it found Nvidia stripe nvidia_abfcacai but when I do ls /dev/mapper, it says there is no folder /dev/mapper.

When I run dmraid -V, it says it has libselinux and libsepol, but no device-mapper (it says unknown). I also installed devmapper from cd, but that doesn't differ.

Anyone knows how to fix this?

---

### Post by njko on 2006-12-12
Same problem here :(  
but dmraid_1.0.0.rc13-2 works better with nvidia stripe than 1.0.0.rc9

---

### Post by Psylocke on 2006-12-20
I got a little further with the following:

Download from [https://launchpad.net/distros/ubuntu/feisty/amd64/dmraid/1.0.0.rc13-2ubuntu1](https://launchpad.net/distros/ubuntu/feisty/amd64/dmraid/1.0.0.rc13-2ubuntu1) :
- libc6
- libsepol
- libselinux
- libdevmapper
- dmraid

(I downloaded the normal .deb files and copied them to usb)

Started the Installer from Alternate CD till Partition disks and choose abort
Start shell
Install:
- libc6
- libsepol
- libselinux
- libdevmapper
- dmraid

Run "modprobe dm-mod"
Run "dmraid -ay"
Run "ls /dev/mapper" to see what devices you have
Type exit, now you will get to the patitioner and choose manual partitioning
After this the system installs on my RAID device till it gives an error with lilo (don't care about this, want to install GRUB later on.
Go back to shell again
- nano /target/etc/apt/sources.list (enable universe)
- chroot /target
- bash
Now I need to install dmraid, I tried "apt-get install dmraid" which tries to install raid but gives an error it is unable to start dmraid using /etc/init.d/dmraid.
I also tried to install the files I already downloaded above, this gave the same error.

Anyone know how to fix this?

---

### Post by Rizado on 2006-12-26
YES thank you VERY MUCH! i've been pulling my hair over this for a few days now. Haven't been able to get dmraid installed during install.

Anyway I think I have the solution to your problem. Before going to chroot you need to mount proc and sys and dev.

mount --bin /dev /target/dev
mount -t proc proc /target/proc
mount -t sysfs sysfs /target/sys

You probably need to create those directorys first. If you still get the same error exit chroot and remount proc and sys, they seem to unmount sometimes. chroot again and do dpkg-reconfigure dmraid and hopefully it'll work.

EDIT: I'm now running kubuntu on a raid array just fine :) One thing I noticed was neccesarry is removing the "savedefault" line from grub or it will complain about a missing file.

---

### Post by tomm3h on 2007-02-16
> **Psylocke said:**
> I got a little further with the following:

Download from [https://launchpad.net/distros/ubuntu/feisty/amd64/dmraid/1.0.0.rc13-2ubuntu1](https://launchpad.net/distros/ubuntu/feisty/amd64/dmraid/1.0.0.rc13-2ubuntu1) :
- libc6
- libsepol
- libselinux
- libdevmapper
- dmraid

(I downloaded the normal .deb files and copied them to usb)

Started the Installer from Alternate CD till Partition disks and choose abort
Start shell
Install:
- libc6
- libsepol
- libselinux
- libdevmapper
- dmraid

Run "modprobe dm-mod"
Run "dmraid -ay"
Run "ls /dev/mapper" to see what devices you have
Type exit, now you will get to the patitioner and choose manual partitioning
After this the system installs on my RAID device till it gives an error with lilo (don't care about this, want to install GRUB later on.
Go back to shell again
- nano /target/etc/apt/sources.list (enable universe)
- chroot /target
- bash
Now I need to install dmraid, I tried "apt-get install dmraid" which tries to install raid but gives an error it is unable to start dmraid using /etc/init.d/dmraid.
I also tried to install the files I already downloaded above, this gave the same error.

Anyone know how to fix this?

> **Rizado said:**
> YES thank you VERY MUCH! i've been pulling my hair over this for a few days now. Haven't been able to get dmraid installed during install.

Anyway I think I have the solution to your problem. Before going to chroot you need to mount proc and sys and dev.

mount --bin /dev /target/dev
mount -t proc proc /target/proc
mount -t sysfs sysfs /target/sys

You probably need to create those directorys first. If you still get the same error exit chroot and remount proc and sys, they seem to unmount sometimes. chroot again and do dpkg-reconfigure dmraid and hopefully it'll work.

EDIT: I'm now running kubuntu on a raid array just fine :) One thing I noticed was neccesarry is removing the "savedefault" line from grub or it will complain about a missing file.

Guys, firstly my hat is off to the pair of you. You two alone gave me the knowledge and wisdom with which to install onto my Sil3112A RAID0 set with Edgy.

However, I had a few issues and I'd like to contribute my experiences in case anyone else comes along with similar experience.

Firstly, prior to partitioning, when instructed to exit to the shell and install dmraid via gdpkg, I found that if installed anything other than libdevmapper and dmraid that it actually caused the partitioning portion of the installer to give an error and fail.

Through trial and error I found that installing libsepol and libselinux caused this (I can't comment on libc6 [edit: see below], as I can't quite remember. I have a feeling it was Ok, but I'm pretty sure I was OK with just libdevmapper and dmraid).

At that point I had all my partitions (already created with the live CD) under /dev/mapper, and I was able to continue the installation.

The second point I got really stuck on, was when installing dmraid the second time (onto /target, via apt-get). I found that re-mounting /proc and /sys wasn't really helping, so I had a look at the error dpkg was giving when trying to install dmraid.

Basically, it came down to dependancies -- I ran apt-get -f install, and it told me what needed to be done. Uninstallation of ubuntu-minimal and installation of libc6 (I *think*), but certainly ubuntu-minimal had to come out. I thought this was odd, and possibly suicidal but at that point I would've tried anything.

Hey presto, it worked. Installing the rest of the system went off without a hitch -- until the bootloader.

To install grub I concentrated on the [https://help.ubuntu.com/community/FakeRaidHowto]("https://help.ubuntu.com/community/FakeRaidHowto") article, which details how to install grub manually. The FakeRaidEdgy article was very vague on this portion (eg. "*maybe* I tried this at some point") and, as in the aforementioned article; grub-installer doesn't work for toffee.

Thankfully grub is a little more dmraid-aware since Dapper, and the version included in Edgy seemed to require a lot less tweaking of the menu.lst for it to work. update-grub guessed almost every setting, save for the 'savedefault' attribute that needs to be removed.

So hopefully that might help anyone else following in my footsteps. I did try out Feisty's Herd 3 alternate CD, but got stuck in loops of errors in the installer. Maybe when it's released dmraid support will be native in both the installer and grub. We're nearly there anyway.

Thanks again, and good luck to all :)

---

### Post by vizerei on 2007-03-07
I was installing edgy with fakeraid when I came across this post.

Absolutely amazing, you 3 have got me further than I have gone yet and I've been banging my head against the keyboard for 2 days straight(day and late into the night).

However, I have some things to add as I still had issues:

**When installing the dmraid, libdevmapper, etc.  I found that I got the same error for the partitioner as the above guy.**

The fix: don't modify the partition table, just include the packages and go straight into the partitioner, you will get 1 shot to partition everything and move on or it will error on you.  If you have to edit the parition table and happen to get the error for whatever reason just reboot, install the libs and dmraid again, and go into the partitioner.

However, I believe this can be avoided by heeding the next issue I had, which involves NOT installing libc6.

**When going to install the base system, I got an error just like with the partitioner. **

The fix:  after parsing the debug logs, I found something interesting.  There was a reference to libc6 and how it was attempting to call dpkg instead of udpkg.  I looked into the [https://wiki.ubuntu.com/FakeRaidEdgy]("https://wiki.ubuntu.com/FakeRaidEdgy") post and what libraries he was installing, I noticed that when using the "Alternate" Edgy CD, he did not install "libc6."  I attempted to install libsepol, libselinux, libdevmapper, and dmraid WITHOUT installing libc6. 

udpkg pitched a fit but, as in the FakeRaidEdgy wiki, the meat of the package was installed.  I followed the rest of the directions and the base installation system now installs.

I'm writing this as it's installing and I hope all goes well.

Thanks again for the post guys, you rock.

---

### Post by tomm3h on 2007-03-09
> **vizerei said:**
> I was installing edgy with fakeraid when I came across this post.

Absolutely amazing, you 3 have got me further than I have gone yet and I've been banging my head against the keyboard for 2 days straight(day and late into the night).

However, I have some things to add as I still had issues:

**When installing the dmraid, libdevmapper, etc.  I found that I got the same error for the partitioner as the above guy.**

The fix: don't modify the partition table, just include the packages and go straight into the partitioner, you will get 1 shot to partition everything and move on or it will error on you.  If you have to edit the parition table and happen to get the error for whatever reason just reboot, install the libs and dmraid again, and go into the partitioner.

However, I believe this can be avoided by heeding the next issue I had, which involves NOT installing libc6.

**When going to install the base system, I got an error just like with the partitioner. **

The fix:  after parsing the debug logs, I found something interesting.  There was a reference to libc6 and how it was attempting to call dpkg instead of udpkg.  I looked into the [https://wiki.ubuntu.com/FakeRaidEdgy]("https://wiki.ubuntu.com/FakeRaidEdgy") post and what libraries he was installing, I noticed that when using the "Alternate" Edgy CD, he did not install "libc6."  I attempted to install libsepol, libselinux, libdevmapper, and dmraid WITHOUT installing libc6. 

udpkg pitched a fit but, as in the FakeRaidEdgy wiki, the meat of the package was installed.  I followed the rest of the directions and the base installation system now installs.

I'm writing this as it's installing and I hope all goes well.

Thanks again for the post guys, you rock.
Glad you've had success, and that we could've helped!

I wasn't too clear on whether I installed libc6 or not, but from what you've said -- I can't have done. The install went as smooth as a button with only libdevmapper and dmraid installed prior to partitioning/mounting/formating. :)

Installing anything else and I couldn't even reach the partitioner once :(

I'm glad to have helped in some way!

---

### Post by t_anjan on 2007-03-21
Thank you to all you guys. I've used input from this thread in conjunction with the FakeRAIDEdgy wiki to get Edgy installed on my RAID system.

I've modified the FakeRAIDEdgy wiki. Now, I think, it is a completely working guide.

---

### Post by zaubara on 2007-03-21
Incredible, I have the same problem and I was playing around for two days aswell.
I'll try all that later this evening and report back, thank you all!

edit:

This worked really great for me, thank you so much!!
I think the only thing I left out was modprobing dm-mod ;) But still, it all worked out fine finally!

Thanks again!

edit #2:

Well, I guess I was a little too excited when I saw that little bar moving ;), but it still does work now :)

Theres one thing that didn't work for me: grub-gfxboot :(
update-grub threw an error, although I did most things like in the tutorial (the copy-files-from-root-to-chroot didn't work exactly that way because I dl'ed all files through wget :)), so I had to improvise:
I removed grub-gfxboot again, apt-get'ed inside the chroot the normal grub and - only on the second try, the one I added the universe-repo - I was finally able to install grub.

For anything else it worked out like intended.

Thank you!

---

### Post by t_anjan on 2007-03-22
Maybe I didn't understand you properly.........were you able to get dmraid to work without modprobing dm-mod?

Could you explain what error "update-grub" threw up? And what do you mean by 'copy files from root to chroot'? 

If you could say what the error was exactly, maybe we could use it to improve the wiki.

---

### Post by tomm3h on 2007-03-22
> **t_anjan said:**
> Thank you to all you guys. I've used input from this thread in conjunction with the FakeRAIDEdgy wiki to get Edgy installed on my RAID system.

I've modified the FakeRAIDEdgy wiki. Now, I think, it is a completely working guide.

That's a good job you've done with the wiki, nice one :)

Has anyone tried the latest Feisty alt-install CD yet? Would be cool to see if it detects fakeraid arrays right out of the box!

---

### Post by t_anjan on 2007-03-23
Doesn't seem like Feisty is going to include dmraid by default. :(

---

### Post by el mariachi on 2007-03-24
Hi guys! Nice job job all of you, but I'm still banging my head at the keyboard lol

I'm following the Fakeraidedgy Guide. I didn't install the optional packages (lisbepoll, lisbelinux and zlib1g). everything goes fine until i get to the pertiotioner... It shows me two RAID arrays (I think) a nvidia_hcaaedaa and a nvidia_hcaaedaa1. The first one says it has a primary partition but it doesn't identifies it as a NTFS one, that is, when I select it, the installer asks me if I want to create a partition (there is no option for resizing). The second one doesn't have any partition.

It's a RAID0 array with one NTFS partition with WindowsXP, that fully occupies it.

I also tried the Feisty ALT CD but it gives me the same results.

---

### Post by el mariachi on 2007-03-24
[IMG]http://img126.imageshack.us/img126/1455/screenshotlp2.png[/IMG]
pressed the wrong button but i think it's more or less visible. It was taken running Feisty. it identifies the RAID devices, shows a partition, let's me mount it as /windows but doesn't allow me to resize it so i can make room for /root and /home partitions...

---

### Post by tomm3h on 2007-03-24
> **el mariachi said:**
> 
pressed the wrong button but i think it's more or less visible. It was taken running Feisty. it identifies the RAID devices, shows a partition, let's me mount it as /windows but doesn't allow me to resize it so i can make room for /root and /home partitions...
I really cannot make out that image, but I do believe you need to have your partitions setup with either fdisk or cfdisk, prior to performing the install.

The wiki's also recommend that you use the alternate installation disc, not the standard disc.

The standard disc is useful for initially installing dmraid and configuring your partitions (I like cfdisk), but after that, I'd use the alternate installer.

I do  remember that once I had dmraid installed on the alternate installation run, my partition and volume options were incredibly confusing -- however, I think it would help greatly if your partitions were already setup prior to reaching the partition/mount point options.

---

### Post by el mariachi on 2007-03-25
thanks! I installed Ubuntu on another disk though... it was too confusing to set it up using fakeRAID...:(

But it's working and that's all i care about! (it has some issues tho...):mad:

---

