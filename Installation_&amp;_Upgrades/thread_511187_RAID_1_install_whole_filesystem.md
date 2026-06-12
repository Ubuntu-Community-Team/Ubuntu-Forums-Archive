---
title: "RAID 1 install whole filesystem"
date: 2007-07-27
forum: Installation &amp; Upgrades
---

### Post by jaffamuffin on 2007-07-27
I would like to install Ubuntu on my system with the view of keeping it running for years. I don't want to have to reinstall my main OS again ever.  

My Plan obviously is to have a separate home partition, this way I can in theory keep all my settings etc  and also, I can NFS mount this from another machine and keep my same settings / profiles / docs on any machine I use.


The other part of my plan is redundancy.  I Have available 2 x 160GB disks for use as my system drives.

Would the best way forward be:

On both drives:
Method 1

40GB partition /md0 (mount at / )   Use SW RAID 1
120GB partition  /md1  (mount at /home)  Also SW RAID 1


Alternatively I could
Method2
on both drives
160GB /md0  RAID1 -> LVM -> 40GB root and 120GB home
advantages/disadvantageS?

But this introduces complexity .

I'd rather keep it simple as possible. 


Using method 1 do I need to do anything special like e.g. install grub on both drives (can ubuntu do that or do I have to get jiggly with configs?)

In theory Could I unplug a drive and plug into another machine and boot up from it? (or read data from it in another host machine)

What about booting up, is it OK, to run the root system on a RAID1, kernel and modules are all OK on a RAID1?

I'd also need to set up some kind of RAID monitor - are there any Gnome utils for this?

If a disk went down, could I literally remove dodgy disk, plug in new disk and reboot? = sorted?


Does anybody have this setup?

Any thoughts?

Thanks all

---

### Post by CopaceticOpus on 2007-08-06
I'm not too experienced, but I've set up a couple systems using software raid. I set up three raid partitions on each drive - one for root, one for swap and one for /home. Then I tie them together into raid devices.

I don't remember the exact menu commands, but I believe you need to use the Ubuntu Server installation disk, because the graphical partitioner doesn't do software raid. I think if you try it you'll figure it out.

Once you have the server installed it's a simple command to install ubuntu-desktop or kubuntu-desktop.

---

### Post by white3454 on 2007-08-07
So I found this link posted all over the forum (I have to admit there is not a lot of people using a RAID 1 desktop environment)

[http://users.piuha.net/martti/comp/ubuntu/raid.html](http://users.piuha.net/martti/comp/ubuntu/raid.html)

These directions took me a while to figure out, but after I did things seemed to go pretty well...  I created 3 partitions 10GB Root, 270.01 GB /home and 10GB swap...  

After formatting the drive which 300GB took about 45-60 minutes I installed Ubuntu 7.04 from the Alternate CD configured my SW RAID 1 and upon reboot the OS never came up.

I did not attempt to continue, cause I have a lexmark 8350 all in one printer and while researching how to setup my printer during the hour long wait for the disks to format I found that Lexmark SUCKS!!! at linux support.  So I had to put windoze back on, until I get a supported printer.

I hope this helps you get where I could not...

---

