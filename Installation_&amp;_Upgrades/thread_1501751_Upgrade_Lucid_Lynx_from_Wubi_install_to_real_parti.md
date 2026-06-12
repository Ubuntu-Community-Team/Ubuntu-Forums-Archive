---
title: "Upgrade Lucid Lynx from Wubi install to real partition"
date: 2010-06-04
forum: Installation &amp; Upgrades
---

### Post by pbenerjee on 2010-06-04
Hi All,

I have been using Lucid Lynx for almost 2 weeks and have got everything working, thanks to the "ubuntu" spirit in this forum. Now I am ready to upgrade my Wubi install to its separate partition. I have searched the forum and googled to find a way to do this, but I am still stuck.:(

I used lvpm (despite knowing that there is no confirmation of its working on Lucid Lynx), it didn't work. The installation happened alright but it wasn't able to show up the login screen (GDM?). It was stuck around the screen before that (Xsplash?).

There is this thread [http://ubuntuforums.org/showthread.php?t=438591](http://ubuntuforums.org/showthread.php?t=438591) that explains this process very well but remains silent on Lucid Lynx version.

I am sure there must be many other first timers who wanted to get their  feet wet the easy way using wubi and would like to make it "permament" OS on their computers.

Is there anyone who can suggest if :

1. There is any way I can still use lvpm to transfer wubi install to separate installation (Ubuntu 10.04 release) ?
2. Any other way I can do this ??

Looking for helping hand here:)

Many Thanks
Partho

---

### Post by bcbc on 2010-06-04
I managed to get a test install of wubi transferred to a partition using LVPM. I didn't run the process to completion though as I noticed it was installing grub legacy and didn't want to deal with that.

What I did was chroot into the install afterwards, remove grub legacy, reinstall grub 2, run updates, and then I had it working.  I think I also had to update the fstab as well.

I don't recommend this though (obviously) - and am currently working on modifying a shell script that will migrate 9.10 or later wubi installs (but don't hold your breath as I don't have a lot of time right now). 

So, we can try and repair the install you have right now, or you can try other options for example, a fresh install and then copy your wubi /home over your new home with rsync. (I haven't done this one though, but in theory it should work).

What do you want to do?

---

### Post by pbenerjee on 2010-06-04
Thank you very much for the reply.
Although I haven't played with grub before, I would still prefer to repair the fresh new install. That offcourse, with all the help I can get :)

 I have attached the screenshot of GParted window

I have XP on C: drive with device string /dev/sda1 which also hosts the Ubuntu wubi installation.
This is Lucid Lynx 10.04.. The new Wubi install is on /dev/sda6 and I had checked in the 'Boot' flag before starting the lvpm install. The swap partition is /dev/sda5 and its double the RAM size. Also, the partition /dev/sda7 is unallocated which I may use to mount or use for Ubuntu only.

Any help from you will be much appreciated.

Many Thanks
Partho

---

### Post by bcbc on 2010-06-05
> **pbenerjee said:**
> Thank you very much for the reply.
Although I haven't played with grub before, I would still prefer to repair the fresh new install. That offcourse, with all the help I can get :)

 I have attached the screenshot of GParted window

I have XP on C: drive with device string /dev/sda1 which also hosts the Ubuntu wubi installation.
This is Lucid Lynx 10.04.. The new Wubi install is on /dev/sda6 and I had checked in the 'Boot' flag before starting the lvpm install. The swap partition is /dev/sda5 and its double the RAM size. Also, the partition /dev/sda7 is unallocated which I may use to mount or use for Ubuntu only.

Any help from you will be much appreciated.

Many Thanks
Partho
Ok, so you'll need to boot ubuntu from wubi for these instructions - and make sure you are connected to the internet.

Then chroot into your new install:
```
sudo mount /dev/sda6 /mnt
for i in dev proc sys dev/pts; do sudo mount --bind  /$i /mnt/$i;done
sudo cp /etc/resolv.conf /mnt/etc
sudo chroot /mnt
```

So now you're in your new install as root. You'll can now remove grub and install grub2.
```
apt-get update
apt-get purge grub grub-common
mv /boot/grub /boot/grubold
apt-get install grub-pc grub-common
update-grub
```

NOTE: when you install grub, you will get a popup asking you which devices to install grub to. It will show you /dev/sda, as well as all the partitions /dev/sda1, /dev/sda2... etc.
Only select the **drive** you boot from e.g. /dev/sda. **Never select any partition(e.g. /dev/sda1, /dev/sda2 etc.)**.

Because LVPM has already installed the grub-legacy bootloader, you need to replace this with the grub2 bootloader. If you make a mistake and end up at a grub rescue prompt, don't worry it's easily fixed with a live CD - see [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708).

You should also check and update /etc/fstab
```
blkid
cat /etc/fstab
```

Check if it looks good - it should have root (/) mounted on /dev/sda6 and swap on /dev/sda5 by UUID (check the UUID and file system against output of blkid). Edit with nano if required (nano /etc/fstab)
e.g.
```
UUID=xxx  /               ext3        defaults,errors=remount-ro    0   1
UUID=yyy      none            swap        sw          0   0
```

If you are not sure, then you can replace "UUID=xxx" with "/dev/sda6" and "UUID=yyy" with "/dev/sda5" but this shouldn't be necessary.

Now you can exit chroot, back to your wubi environment. 
```
exit
for i in dev/pts dev proc sys; do sudo umount /mnt/$i;done 
```

Update your wubi grub menu and make sure it finds your new install:
```
sudo update-grub
```
You should see something like this:
```
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.33-22-generic
Found initrd image: /boot/initrd.img-2.6.33-22-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Professional on /dev/sda1
**Found Ubuntu 10.04 LTS (10.04) on /dev/sda6**
done

```
The important part is in bold.

Exit your terminal, reboot, select Ubuntu from the Windows menu, and then arrow down (below the Windows entry) to your new install and see if it boots OK.

WARNING: there are some risks in the above process and I cannot guarantee there are no errors (either typo or other mistakes). Please use your own judgement, check things along the way, and do not proceed if you're unsure. Also it's a good idea to back up important data.

Good luck.

If for any reason you end up at a grub rescue> prompt after doing this, reinstalling the windows bootloader will get you back into windows.

---

### Post by pbenerjee on 2010-06-05
In addition to the above info, I want to add this as I was sharing this info on another thread.
**During boot, I get stuck at fsck check** and it eternally hangs, I waited 20 mins  before pressing Esc key. It then jumped to the default Ubuntu dotted progress  status window (Xsplash?) and just hangs. If I press Esc key again. it  goes back to fsck window again !! This ding-dong toggling happens with each Esc key press.

The only way to come out was power off  :sad:
Just to ealborate on where it hangs.

Thanks again for offering to help :)

---

### Post by pbenerjee on 2010-06-05
Sorry I did not see your post before posting my last one, just few mins before.
I am going to try your instructions and report back.

Thanks a lot for your post. Much appreciated.:)

---

### Post by bcbc on 2010-06-05
> **pbenerjee said:**
> In addition to the above info, I want to add this as I was sharing this info on another thread.
**During boot, I get stuck at fsck check** and it eternally hangs, I waited 20 mins  before pressing Esc key. It then jumped to the default Ubuntu dotted progress  status window (Xsplash?) and just hangs. If I press Esc key again. it  goes back to fsck window again !! This ding-dong toggling happens with each Esc key press.

The only way to come out was power off  :sad:
Just to ealborate on where it hangs.

Thanks again for offering to help :)

OK. I can't recall exactly what happened to me, but my /etc/fstab was messed up after running lvpm, so maybe that's the reason for the weird behaviour. In any case, you'll find out if it's messed when you try and mount it. In which case you can run fsck before attempting the repair.

---

### Post by bcbc on 2010-06-05
> **pbenerjee said:**
> Sorry I did not see your post before posting my last one, just few mins before.
I am going to try your instructions and report back.

Thanks a lot for your post. Much appreciated.:)

Good luck - I hope everything works out :) 

Unfortunately, I've got to sign off, but I'll pick it up in the morning.

---

### Post by bcbc on 2010-06-05
One last thing... I assumed you still have the windows boot loader, in other words, you boot straight to your windows menu (choices are windows or ubuntu).

But I realised that lvpm may have installed the grub bootloader if you ran it to completion. If this is the case, you need to either replace the windows bootloader or install the grub2 bootloader to /dev/sda.

To reinstall the windows (equivalent) bootloader, do this from your wubi install:
Enable the universe repository (System, Administration, Software Sources, then check the second box).
From terminal:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```

I don't recommend installing the grub2 bootloader until you are sure everything is working in your new install, but it should also work.

---

### Post by bcbc on 2010-06-05
> **pbenerjee said:**
> The new Wubi install is on /dev/sda6 and I had checked in the 'Boot' flag before starting the lvpm install. 

The boot flag must always be on the windows partition. The windows bootloader needs it. Grub does not.

---

### Post by pbenerjee on 2010-06-08
Sorry for the delay in posting. I tried the steps on the same day you posted the instructions. Unfortunately my windows boot loader got overwritten/corrupted. My laptop was locked out as I kept getting Grub error 15. With a local help, I somehow managed to get into the system again, did a Wubi reinstall and got the previous packages up and running:p

Now I am back to the same level I was 4 days ago !! And ready to have another go!!
Just wanted to give you this feedback.. I got into Grub error 15 at system start up
As I maintained before, my XP install and Wubi were on same windows partition i.e. C: drive
After the crash, I have now installed Wubi on a separate windows drive (offcourse its NTFS)

Any idea  how to prevent grub from overwriting the main system boot loader?

---

### Post by pbenerjee on 2010-06-08
Acbc, I want to specifically point out that I took special care to not install grub on any existing drive, definitely not /dev/sda1 per your advice. Somehow, it "seems" to have still fiddled with /dev/sda1. After system restart, it was straightaway going to the grub and ran into Grub error 15 thereafter.

---

### Post by pbenerjee on 2010-06-08
Attached is the GParted screenshot after the new wubi install....
As you can see, The /host is on /dev/sda7 and there is nothing else on that drive (its showing a high used space as I allocated around 10 gb during wubi installation) though I am not using it yet.

/dev/sda6 is my proposed swap partition and /dev/sda5 I would like to mount later

---

### Post by bcbc on 2010-06-08
grub error 15 - according to the manual indicates that you have grub legacy installed to the MBR and grub2 installed in /boot. My instructions were to not overwrite the MBR with grub2, however I assume you already had grub-legacy installed to the MBR

But let's see if we can get this sorted out. If you reinstalled wubi, you had to uninstall the old wubi. This means that your old ubuntu only exists on /dev/sda6 - so if you have critical data/settings you should consider backing these up. 

I'm also sorry about your troubles - before you make any more changes you definitely need to have an ubuntu install cd on hand that you can boot from in 'live cd' mode ("try without any changes"), so you can at least get back online and post to ubuntuforums in case something goes wrong. You could also have used it to repair the bootloader in the MBR.

Anyway, let's see if we can boot up your ubuntu install on /dev/sda6. First run the [bootinfoscript]("bootinfoscript.sourceforge.net/") and post the results so I can see what's really going on.

---

### Post by bcbc on 2010-06-08
> **pbenerjee said:**
> Attached is the GPated screenshot after the new wubi install....
As you can see, The /host is on /dev/sda7 and there is nothing else on that drive (its showing a high used space as I allocated around 10 gb during wubi installation) though I am not using it yet.

/dev/sda6 is my proposed swap partition and /dev/sda5 I would like to mount later

Ok I'm confused - your old /dev/sda6 is gone?

---

### Post by bcbc on 2010-06-08
It looks like you've reformatted your logical partitions so your ubuntu install with LVPM is gone. Your wubi reinstall probably took out the old wubi.

So unless you backed up your wubi, are you looking to do a new install of ubuntu direct to partition? 

Please confirm what you want to do?

---

### Post by pbenerjee on 2010-06-09
> **bcbc said:**
> It looks like you've reformatted your logical partitions so your ubuntu install with LVPM is gone. Your wubi reinstall probably took out the old wubi.

So unless you backed up your wubi, are you looking to do a new install of ubuntu direct to partition? 

Please confirm what you want to do?

Yes you are right about the previous LVPM install.. those logical partitions are gone. Old Wubi was gone even before my new install. Thankfully, I had the list of packages from previous install.
Unfortunately, my cd/dvd drive has not been working since 2 months now hence I am forced to take Wubi install route.

At this stage, I gave you all this info as feedback and to suggest the best route ahead. My aim is to "rescue" wubi install from window's clutches. CD install is ruled out. Hence the need to move wubi to a real "unix" partition:p

---

### Post by pbenerjee on 2010-06-09
Output of boot_info_script055.sh attached.

---

### Post by bcbc on 2010-06-09
I saw someone post a link the other day on how to use grub to boot from a .iso image. I think this could work for you. The down side is that if you end up not being able to boot, you'll be stuck.

Can you not boot from a USB? Get a 1GB USB and from within wubi go to System, Administration, USB startup disk creator. 
Then you can just install from that and you also have the ability to boot a 'live USB' environment when needed.

---

### Post by pbenerjee on 2010-06-09
> **bcbc said:**
> I saw someone post a link the other day on how to use grub to boot from a .iso image. I think this could work for you. The down side is that if you end up not being able to boot, you'll be stuck.

Can you not boot from a USB? Get a 1GB USB and from within wubi go to System, Administration, USB startup disk creator. 
Then you can just install from that and you also have the ability to boot a 'live USB' environment when needed.

Yes, I have a 4GB usb stick and can try that. yes. 
So, if I take "startup disk creator" route, is there any real possibility of recurrence of startup booting issue, assuming I don't do anything that even remotely suggest touching any boot/grub files outside USB ?

I mean will it touch any boot loader/grub on hard disk?

---

### Post by bcbc on 2010-06-09
> **pbenerjee said:**
> Yes, I have a 4GB usb stick and can try that. yes. 
So, if I take "startup disk creator" route, is there any real possibility of recurrence of startup booting issue, assuming I don't do anything that even remotely suggest touching any boot/grub files outside USB ?

I mean will it touch any boot loader/grub on hard disk?

Well, you will have to install the grub2 bootloader to the hard disk MBR. (There are alternatives, but this seems to be the simplest way, in my view.)

Grub2 is fairly flexible, for example, you could have it boot windows by default without showing the menu at all (and then you just hold down SHIFT when you want to see the menu to boot ubuntu). Or you can create a simplified menu similar to the windows boot menu (e.g. just Windows and Ubuntu as options and default to Windows).

Just don't install grub2 to any partition boot sector.

---

### Post by pbenerjee on 2010-06-09
Ok gathering my breath before the bungee jump from few hundred feet height:p
Just taking a poise. Will report tomorrow.

---

### Post by pbenerjee on 2010-06-22
Hi Bcbc,

Sorry for taking so long to post my feedback. 
Well, good news is: Its success finally.

Offcouse, it didn't happen in the planned fashion but I guess end justifes the means.
Okay, to begin with I successfully created a bootable USB stick (jetflash from Transcend) in my first attempt from the Main Menu -> Administration -> Startup Disk Creator (I used the .iso image)
  :guitar:

Then I used lvpm to "copy" my wubi installation to a new partition. Then I ran the command that you posted in page 1, starting from mounting directories to new lvpm install till updating grub in new install (while staying with chroot). 
I also changed the entry in menu.lst under /boot/grub to make it point to the partition with new install (though it shouldn't be necessary in grub2). Then I did the reboot. I got grub error 15 again !!!

I pulled out the bootable USB, changed the BIOS setting on my laptop to accept USB as first bootable option and it worked after making me wait for good 15 anxious seconds.
It gave me options to install or just run Ubuntu from USB. I chose to do the install. It did show up XP AS WELL AS the new lvpm options (as existing OS). So it picked up the windows and my new /dev/sda3 (lvpm) install both as existing OS .

I okayed the new installation with default values. This installation corrected the window boot loader corruption/error (which let me to wubi earlier) and gave me legitimate access to my new lvpm install as a separate menu option. So I now have the new hard disk install (from USB) +  XP + Wubi + LVPM 

The LVPM install is what I wanted as it had all my packages/data/settings from wubi. I changed the /etc/default/grub in the new (USB) install to make LVPM install as my default OS:guitar:
Then I ran update-grub for the above change to take effect.


Now I am going to nuke the wubi install and use the freed space in my new LVPM install.

So, I guess for people wanting to upgrade Wubi install of 10.04 to a new partition, the work around is :

1. Do lvpm instal of existing wubi
2. Keep a bootable CD/USB handy (if you don't have it, create is as mentioned above)
3. Execute the commands mentioned by bcbc in page 1 (this also creates grub menu options which are respected by new the CD/USB install)
4. Reboot (it will get into booting errors here, I went into Error 12 & 13 before finally seeing error 15)
5. Reboot again, this time from the CD/USB and do a fresh installion from the same (don't select 'use entire disk option')
6. Once done, it will prompt to reboot. Do it. After reboot, you get the grup menu for the LVPM installation also (which contains all the packages/data/confiuration from the wubi install)

The major downside I see here is that you are forced to have another installation of Ubuntu. One way to minimize this downside is to select minimum space e.g. 3 GB for the new CD install.  Another downside is for any booting related changes, you have to login to the new install. 

Untill lvpm is updated/patched to work "as is" for 10.04, this option has worked for me.

 :guitar:


Thanks Bcbc for your instructions and interest.
Let me know what you think of it. My workaround is newbie version. I am sure you will have a lot to add/correct.

---

### Post by bcbc on 2010-06-22
> **pbenerjee said:**
> Hi Bcbc,

Sorry for taking so long to post my feedback. 
Well, good news is: Its success finally.

Offcouse, it didn't happen in the planned fashion but I guess end justifes the means.
Okay, to begin with I successfully created a bootable USB stick (jetflash from Transcend) in my first attempt from the Main Menu -> Administration -> Startup Disk Creator (I used the .iso image)
  :guitar:

Then I used lvpm to "copy" my wubi installation to a new partition. Then I ran the command that you posted in page 1, starting from mounting directories to new lvpm install till updating grub in new install (while staying with chroot). 
I also changed the entry in menu.lst under /boot/grub to make it point to the partition with new install (though it shouldn't be necessary in grub2). Then I did the reboot. I got grub error 15 again !!!

I pulled out the bootable USB, changed the BIOS setting on my laptop to accept USB as first bootable option and it worked after making me wait for good 15 anxious seconds.
It gave me options to install or just run Ubuntu from USB. I chose to do the install. It did show up XP AS WELL AS the new lvpm options (as existing OS). So it picked up the windows and my new /dev/sda3 (lvpm) install both as existing OS .

I okayed the new installation with default values. This installation corrected the window boot loader corruption/error (which let me to wubi earlier) and gave me legitimate access to my new lvpm install as a separate menu option. So I now have the new hard disk install (from USB) +  XP + Wubi + LVPM 

The LVPM install is what I wanted as it had all my packages/data/settings from wubi. I changed the /etc/default/grub in the new (USB) install to make LVPM install as my default OS:guitar:
Then I ran update-grub for the above change to take effect.


Now I am going to nuke the wubi install and use the freed space in my new LVPM install.

So, I guess for people wanting to upgrade Wubi install of 10.04 to a new partition, the work around is :

1. Do lvpm instal of existing wubi
2. Keep a bootable CD/USB handy (if you don't have it, create is as mentioned above)
3. Execute the commands mentioned by bcbc in page 1 (this also creates grub menu options which are respected by new the CD/USB install)
4. Reboot (it will get into booting errors here, I went into Error 12 & 13 before finally seeing error 15)
5. Reboot again, this time from the CD/USB and do a fresh installion from the same (don't select 'use entire disk option')
6. Once done, it will prompt to reboot. Do it. After reboot, you get the grup menu for the LVPM installation also (which contains all the packages/data/confiuration from the wubi install)

The major downside I see here is that you are forced to have another installation of Ubuntu. One way to minimize this downside is to select minimum space e.g. 3 GB for the new CD install.  Another downside is for any booting related changes, you have to login to the new install. 

Untill lvpm is updated/patched to work "as is" for 10.04, this option has worked for me.

 :guitar:


Thanks Bcbc for your instructions and interest.
Let me know what you think of it. My workaround is newbie version. I am sure you will have a lot to add/correct.

Hi, thanks for the update. You did a good job getting it to work. Unfortunately I did make a mistake and set you up to fail. When I used lvpm, I was monitoring it and as it started to install grub-legacy I aborted the process. The difference between you and me is that grub-legacy didn't install the bootloader for me, but for you it did. 
Then when I told you not to install the grub2 bootloader I left you in that broken state. So I am going to edit my post above to say that you have to install the grub2 bootloader. If you had done that, I am certain it would have worked perfectly. And without the additional install.

So apologies about that. In the meantime, I've got a working script to migrate a wubi install to partition, rather than this workaround. But it still hasn't been tested enough.

Anyway - good job figuring that all out.

---

### Post by pbenerjee on 2010-06-22
Yes, I figured out today that perhaps if I had selected to install grub2 it would have been more interesting.
bcbc : You got me started and I learned few things. It was never meant to be a cake-walk
Also, early movers do carry a risk. I did. For various reasons, 10.04 is dubious on wubi to partition transfer.
I am sure your script will make life easier for lots of people and I am looking forward to it:popcorn:

Guys, as bcbc has updated his instructions in page 1, you shouldn't need the workaround in my last post
His script will be a great tool for this LTS version and hopefully later ones

---

### Post by bcbc on 2010-06-22
> **pbenerjee said:**
> Yes, I figured out today that perhaps if I had selected to install grub2 it would have been more interesting.
bcbc : You got me started and I learned few things. It was never meant to be a cake-walk
Also, early movers do carry a risk. I did. For various reasons, 10.04 is dubious on wubi to partition transfer.
I am sure your script will make life easier for lots of people and I am looking forward to it:popcorn:

Guys, as bcbc has updated his instructions in page 1, you shouldn't need the workaround in my last post
His script will be a great tool for this LTS version and hopefully later ones
You've got a great attitude! Perfect for learning ubuntu. :)

Anyway - FYI - I've uploaded the latest version of *my* script (wubi-move) that I feel is in good shape. I uploaded it to a [launchpad bug report]("https://bugs.launchpad.net/wubi/+bug/456549") for the original wubi-move-to-partition script from the wubi guide. 

It's a bit late for you, but in case you are interested.

(*my* - the script is just Agostino's original with my mods. I'll take credit for any new bugs.)

---

