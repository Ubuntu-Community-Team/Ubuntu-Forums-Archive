---
title: "A question about USB startup disks..."
date: 2009-11-15
forum: Installation &amp; Upgrades
---

### Post by squashpup on 2009-11-15
When you start it up, you get a slider to adjust the amount of space for "documents and settings".

Does this include installed programs?  In other words, if I set the slider to the max, does that give me more space available for the programs I wish to install later, or does that decrease the space available for new programs?

I'm GUESSING that all programs you install would be included with "documents and settings", therefore setting the slider to the max will give me the most space available.  Am I right?  

Thanks!

---

### Post by darkod on 2009-11-15
Just for clarification, you are referring to a situation when using the Try Ubuntu option, so called live cd, right?
Because when you install properly the system with Install Ubuntu what you chose with the slider has no effect at all. It is working from the hdd from that point on and saving everything to hdd.
Try Ubuntu option is just that, to try. Not sure how many programs it can carry inside, but you might giving it a go with the slider all the way to the end. Use the whole USB stick in other words.

---

### Post by squashpup on 2009-11-15
No, I'm talking about plugging in a USB thumb drive, and then going to System>Administration>USB Startup Disk Creator, and writing an Ubuntu image to my USB stick.  

I always seem to get low disk space issues after installing just a few packages.  But, I never use the whole 4gb thumb drive, either, but partition it 3/4-1/4 (in other words, a 3gb partition for the install, and a 1gb partition to store whatever else I want).  

What if I made one partition and used the maximum allowable space for "documents and settings"?  Would that allow more room to install programs as well?  

Thanks!

---

### Post by darkod on 2009-11-15
OK, you are creating an ubuntu startup usb. But the space for documents and settings means that when you boot up with that usb and select Try ubuntu option, any document or setting created during that live environment will be saved on the usb stick because running the Try Ubuntu option does not write anything on the hdd.

What you wrote sounds more like you are actually installing ubuntu to a usb stick because just creating the startup stick takes 690MB like the image size.

It might be a dumb question, but why do you want to install packages in the live environment? To test if they can work?

---

### Post by parkland on 2009-11-15
I had played with live usb sticks a bit.

You can install and update, I even installed virtualbox and had winXP running all from the usb stick.

Problem is, I know that reading around on the internet, you find lots of topics on "how long does a usb stick last", referring to the digital storage IC, when in fact, every "boot usb" stick I've used for more than a month, is now dead.

1st one down, I assumed maybe it got jarred, or abused in some way.
2nd one gone, I started assuming that it might be these cheap brand of USB sticks I was using.
3rd & last dead usb stick, I experienced extreme rage, cold sweats, and I started seeing a stress councillor. After I got out of jail, for trying to set fire to kingstons main headquarters building, I set out to find what was going on.

One of these sticks was only booted about 4 times, which is not nearly close to what someone would consider a reasonable service life. Another died after I ran a batch file to copy files on and off of it. 

After cracking one open, I am disappointed to see that the tiny board has nice clean contact points, as if it is completely anticipated that people's usb stick dies, and then they pay money to have their data recovered. 
I believe the culprit on some sticks is the USB interface IC chip. I guess it overheats, and dies.

---

### Post by phillw on 2009-11-15
> **parkland said:**
> I had played with live usb sticks a bit.

You can install and update, I even installed virtualbox and had winXP running all from the usb stick.

Problem is, I know that reading around on the internet, you find lots of topics on "how long does a usb stick last", referring to the digital storage IC, when in fact, every "boot usb" stick I've used for more than a month, is now dead.

1st one down, I assumed maybe it got jarred, or abused in some way.
2nd one gone, I started assuming that it might be these cheap brand of USB sticks I was using.
3rd & last dead usb stick, I experienced extreme rage, cold sweats, and I started seeing a stress councillor. After I got out of jail, for trying to set fire to kingstons main headquarters building, I set out to find what was going on.

One of these sticks was only booted about 4 times, which is not nearly close to what someone would consider a reasonable service life. Another died after I ran a batch file to copy files on and off of it. 

After cracking one open, I am disappointed to see that the tiny board has nice clean contact points, as if it is completely anticipated that people's usb stick dies, and then they pay money to have their data recovered. 
I believe the culprit on some sticks is the USB interface IC chip. I guess it overheats, and dies.

Now, that is a most interesting pont.  Never really thought about it before, but ....
When I wanted a 'memory-boost' usb stick for my Vista instal - Only certain, more expensive ones are suitable. You could well have a point, as those ones certified for Vista would be expected to be accessed constantly as vista 'swap' area. Maybe why I've never had problems when I popped Unbuntu onto it - it was already of the spec to allow re-writing often & fast without getting 'upset'.

Those sticks will have 'Vista Memory Boost' or words to that effect in their advertising.

Phill.

---

### Post by parkland on 2009-11-15
Yes, those sticks might be better.

Again, I believe the weakness is in the little usb interface chip, really, booting an OS is mostly reading, but it seems even reading off the stick gets it pretty warm.

To do this on a regular basis, I'd probably say go with a solid state HD, some have usb right on them.

---

### Post by phillw on 2009-11-15
I guess that is why it is an 'real' aluminium case, not plastic, to act as a heat sink .... Quite a simple idea, really :p

Phill.

---

### Post by efflandt on 2009-11-15
The slider in USB Startup Disk Creator is to set the amount of persistent data, which can include config settings, browser plugins, programs, etc.  It is an ext3 loop mounted filesytem.  NOTE: Do not put the slider all the way to the right or the installation may fail to complete (down a click should work).  Apparently due to files not quite ending on sector boundaries it may slightly under estimate the space it really needs.  If you leave more space, that will be regular fat space that Windows can read/write (mounted as /cdrom on live Ubuntu).

You can loop mount the casper-rw file(system) from a running Linux system.  Just create a mount point like **sudo mkdir /vdisk** then

**sudo mount -o loop /path-to/casper-rw /vdisk**

Just curious what brand of USB sticks failed?  My Palm TX uses flashOS and has worked for years (wireless news reader in my bathroom).  Flash should typically last 100,000 erase/write cycles (some new ones 1 million cycles).  But that does not assure that other circuitry is not substandard or overrated.

I have used a 4 GB USB back and forth between 32 and 64-bit 9.10 for installation and on the road with a company laptop. I also put 64-bit 9.10 on 2 GB microSD the size of your fingernail was just to see how it works.  Slow boot, but works fine after that.  I have never had a failure of any flash (USB, SD, microSD, CF).

Due to live booting to superuser with no password (and no way found to override that), I was thinking about putting a regular installed system on flash.  But for now simply shunk the partition on WD Passport USB HD and used that space instead.  **NOTE:** If you do complete install to USB, the **default grub location is the mbr of your main drive**.  Use the **Advanced** button near the end of install to put grub/grub2 on the USB drive.  Failure to do that will mean failure of USB drive to boot on any other computer.

---

