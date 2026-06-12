---
title: "Partitioning question, after the installation"
date: 2007-06-26
forum: Installation &amp; Upgrades
---

### Post by jbysmith on 2007-06-26
I have a question about re-doing one of my partitions, after Ubuntu is installed and running.

Originally, I wasn't sure if I would be staying with Linux in general. I have three hard drives.  The first I set up purely as a Windows XP partition, just as a fallback in case something I needed didn't run well in Linux.  The second drive is Ubuntu's root partition, and the third (largest) is the /home partition.

Well after a few weeks of experimentations, a lot of Google, etc etc I've gotten Ubuntu working exactly how I want it.  I'm even playing World of Warcraft and Guild Wars and the like with no issues... I haven't touched that XP partition since I originally created it.  The only thing I use that cant be run natively is Delphi 2007, and I'm running that just fine in VirtualBox.

So, I'm ready to kick this Windows XP partition to the curb and reformat it for extra storage, maybe keep downloads and such on it.  What I'd *like* to do is just blast the partition and make a new one for Linux.  But, as my Linux system is on the 2nd and 3rd drives.. well I'm a little nervous, to say the least.  I know this would utterly destroy a Windows system.

Can I just delete that partition and make a new one without messing up my Linux system?  Will that affect the boot loader?  I could use some advice on this, as I *really* don't want to start over again.  Thanks

---

### Post by dabl on 2007-06-26
> **jbysmith said:**
> The second drive is Ubuntu's root partition

You have an entire hard drive for root?  If it is larger than 10 GB, you're wasting a lot of space on that one.

The only problem with re-using your third (Win XP) drive is that you only get one /home partition in your filesystem, and you've already used it.  You can make it something else -- "/home#2" if you want, and use it that way, but it will be just a storage media location in your filesystem.

I like the GParted live CD for disk partitioning -- get it here: [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

:)

---

### Post by nate22 on 2007-06-26
hey how did you get WOW and GW to start? i cant seem to figure that one out...

---

### Post by jbysmith on 2007-06-26
Whups, let me clarify a litle bit.

Three drives (IDE).  Primary master is an old 40GB, thats the Windows XP partition.
Second drive, primary slave, also an older 40GB is Linux root.   (Actually I've been filling that thing up rather quickly)
Third drive, secondary slave, is the /home partition, 500GB as I'm a MP3 and MPeg junkie.

Knew I wouldn't be able to add a second /home or anything.. I was just figuring to mount it as say /downloads or some other "junk storage" folder.

I'm comfortable with the actual partitioning and mounting process, no worries there.  What I'm concerned about is mostly the boot loader.  If I repartition that first drive, will it also zap the boot loader, and render my Linux partition on the 2nd drive unbootable?

---

### Post by jbysmith on 2007-06-26
> **nate22 said:**
> hey how did you get WOW and GW to start? i cant seem to figure that one out...

I can't comment on Wine, haven't tried them in that one, but I picked up a subscription to Cedega, and they're playing beautifully.  I had to adjust the settings a tad to optimize the performance, thats after fussing around with the AGP drivers and such too.  (Blacklisting my nForce2's AGP driver and forcing it to use the one from the nVidia video card's drivers, making sure sideband and fastwrites were on, etc etc)  Vistually it's a hair slower.. down 2 or 3 FPS.. but the load times are ridiculously fast.  (Running from, for example, Ironforge to the Deeprun Tram, nearly instant, blink and you might miss it)  I had *horrible* results with my old ATI card, but I chalk that up to crummy drivers.

Guild Wars I had problems initially getting it to start.  I found that on their forums sometimes it helps to tell Cedega to force it into a window, set your in-game visual settings, then you're ok to let it run full screen again.  (Worked for me anyway) Check their forums, a lot of good tips to be found.

---

### Post by dabl on 2007-06-26
> **jbysmith said:**
> Whups, let me clarify a litle bit.
Actually I've been filling that thing up rather quickly

If you will occasionally run ```
sudo apt-get autoclean
``` and ```
sudo apt-get autoremove
``` I don't think root can ever amount to more than about 5 GB.

>  If I repartition that first drive, will it also zap the boot loader, and render my Linux partition on the 2nd drive unbootable?

I think that's a "YES" ...

I'm not 100% sure on this -- better check me out.  But I think each hard drive can have 1 partition marked "bootable", and so you've got a bootable first (Win XP) drive/partition and also a bootable second (Ubuntu) drive/partition. When you re-format the Win XP drive for Linux, it's going to take out the master boot record, I think, and you'll be left un-bootable.  Maybe the better approach would be to delete everything that you don't need EXCEPT the Win XP OS, then do disk cleanup, then defrag, then use GParted to shrink that Win XP partition down to as small as seems safe -- maybe 8 GB or so.  Then you can use the space you freed up for Linux, without disruption of your boot menu and MBR.  :)

---

### Post by jbysmith on 2007-06-26
> **dabl said:**
> I'm not 100% sure on this -- better check me out.  But I think each hard drive can have 1 partition marked "bootable", and so you've got a bootable first (Win XP) drive/partition and also a bootable second (Ubuntu) drive/partition. When you re-format the Win XP drive for Linux, it's going to take out the master boot record, I think, and you'll be left un-bootable.  Maybe the better approach would be to delete everything that you don't need EXCEPT the Win XP OS, then do disk cleanup, then defrag, then use GParted to shrink that Win XP partition down to as small as seems safe -- maybe 8 GB or so.  Then you can use the space you freed up for Linux, without disruption of your boot menu and MBR.  :)

Hmm that's a thought.  Yea I was kind of figuring it was going to blast the MBR but I don't know too much on the Linux technicalities yet.  Ok, how about this.  Can I re-partition then re-build the MBR and boot loader with a Live CD? (Ubuntu or other, don't care) Not a re-install mind you, as I want to preserver my current setup.  Lots of hours with Google to get it just right :)  Or, as an alternative, can I simply remove that first drive entirely, and again with the LiveCD rebuild my MBR and boot loaders?  (I can put that drive to better use possibly in one of my servers.)

As far as the root space goes, I see your point.  Perhaps a re-install might be the thing to do down the road and set it up better the first time around.  (Altho to be honest, right now I'm not worried about it, I have buckets of free space in /home, if space becomes an issue I may re-do it)

---

