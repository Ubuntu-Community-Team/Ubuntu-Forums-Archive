---
title: "Clone install to smaller drive"
date: 2010-01-02
forum: Installation &amp; Upgrades
---

### Post by abumaia on 2010-01-02
Hi guys.
I've been using Ubuntu fairly exclusively over the last few weeks, and I'm about ready to take the leap and get rid of my windows installations.  There's one snag though.  On my laptop 150GB hard drive, I have Vista and Win7 installed.  To try out Ubuntu, I installed it on my external 1TB drive with a 300GB partition.  This is a rather precarious situation, because if the power outlet gets bumped, or there's a power outage, my laptop will stay on with the internal batteries, but the hard drive with Ubuntu on it won't.  So I want to move my Ubuntu install onto my laptop hard drive.  Since the external partition is double the size of the internal drive, how do I move the OS across and keep all my settings and files?

---

### Post by Warren Watts on 2010-01-02
You can use [clonezilla live]("http://www.clonezilla.org/clonezilla-live/#about") to clone the partition and copy it to your internal HD, but you will have to change your grub menu.lst file to reflect the new location.

---

### Post by Moozillaaa on 2010-01-02
I think he can do this with his install CD also.

Boot the install CD, start GParted partition utility, find the 300 G partition, unmount it, then reduce it to the size you want. This might take an hour or so...

Then, while still on install CD, open a terminal, type in 
```
cp  /dev/sdxx  /dev/sdyy
```
where sdxx is the external partition to copy, and sdyy is the local partition to copy TO.

That will take an hour too. There's NO progress indicator in the CLI window as this is done. When it is done, the user prompt will return.

And you'll have to edit GRUB like WW said.

---

### Post by abumaia on 2010-01-08
Thanks for the help.  Only now I've waited too long, and the ubuntu partition is now too big (even after shrinking) to fit on the internal hard drive. >_<  So I think I'll leave it as is for now, and just try to be careful not to bump the external drive.  Maybe at some point I can get a bigger laptop drive to use.
****

---

### Post by Mark Phelps on 2010-01-09
For future reference, Clonezilla can NOT be used to clone to a smaller drive.  The destination drive has to be as large or bigger than the source drive.

---

### Post by abumaia on 2010-01-10
well, by moving some pictures and music off of the ubuntu partition and onto the external drive, I got it small enough to copy across as you said.  However, I was then unable to boot into either partition afterward.  So I just went with it and did a clean install to the laptop internal drive.  
Now I have a working install on the laptop, and a non-working install on the external drive.  Is there any way to copy the programs and settings across in this situation?

---

### Post by Return Privacy on 2010-10-11
Hi all,
I just did an install of Ubuntu 10.04 on a Dell. It is the only thing on the internal drive. I spent a lot of time configuring and setting up some custom stuff to get it working just right on my home network. This is just the Ubuntu install, so I know it can't be very big at all. I want to move it to a smaller drive, and have that drive be ONLY the Ubuntu OS. I'll use another drive for files and programs. I made a backup of the Ubuntu drive with Image for Linux, and it easily fit on 1 DVD, with only about 25% of the DVD surface actually burned. I then replaced the original drive with a smaller one, that I KNOW is more than large enough for this, but it would not restore to the smaller drive. It is looking for a drive that is at least as large as the original (even though the original drive only had the Ubuntu installation on it, and the rest of the drive wasn't used)
My question, is how do I move this Ubuntu installation to a smaller (but easily big enough) drive?
It is ridiculous to have to use a large drive for such a small installation.
Thanks

---

### Post by mister_p_1998 on 2010-10-11
> **Mark Phelps said:**
> For future reference, Clonezilla can NOT be used to clone to a smaller drive.  The destination drive has to be as large or bigger than the source drive.

I thought he said the Ubuntu partion was 300GB? that should fit on a 150GB drive just fine!

Steve

---

### Post by Mark Phelps on 2010-10-11
Perhaps, since you obviously do NOT believe what I said, you will believe THIS (taken directly from the Clonezilla FAQ):

> Why Clonezilla can _NOT_ image from a large drive to a smaller drive ?
It's not easy to implement such a feature, since Clonezilla now is a partition "imaging" tool, by "imaging", it means clonezilla actually does not know the files themself, clonezilla just knows where the used blocks are. Because of this reason, the target partiton size must be equal or larger than the original one so that clonezilla can restore the used blocks on that partition. If the target partitioin size is smaller, then it will go wrong.
Unless Clonezilla has file-based function in the future. Maybe... 

---

### Post by Return Privacy on 2010-10-12
Hi Mark,
I certainly believe what you are saying about Clonezilla. I even tried using Image For Linux, and it does an image, but will only restore to a drive of at least the same size, regardless of what is actually used on the drive.  I just wonder if there is any other way to do this? I was wondering about a copy command in linux or some other clone tool that would adjust for size? Like I said, my Ubuntu install is very small, and should be able to fit on the smallest hard drive. I made the mistake of doing this install on a blank, large 250gb drive, and then did all the configurations. I didn't put any files on it yet, only the setup and configurations I needed. I want to just move this setup the way it is, onto a smaller, say 40 or 80gb drive, to be used ONLY for the OS. I'll use the larger drive for files and such. 
If I knew what I was doing, I would just pull the drive, put in the smaller one, and do another fresh install. The problem is, I followed some very good tutorials on here (and other places), and setup a custom AFP/Avahi stuff, to make the 2nd internal drive to be seen by an iMac and be used as a Time Machine backup location over the network. Believe me, it was hard to get that working correctly, and I don't want to try to do that again. (I still don't know how or why it works....lol)
Am I stuck using this large drive for the OS only?
thanks-

---

### Post by mister_p_1998 on 2010-10-12
> **Mark Phelps said:**
> Perhaps, since you obviously do NOT believe what I said, you will believe THIS (taken directly from the Clonezilla FAQ):

Lets see... going from a 300GB partition to a 150GB partition.. hmm I think that fits FOUR times! he's going from partition to partition.. NOT drive to drive! he's not doing a full drive clone.
Steve

---

### Post by antiram on 2010-10-12
boot a live cd for cloning and clone with tar to prevent all rights, timestamps etc.

eg. source is mounted in /source
target is mounted on /target
and clone with
```

cd /source
tar cf - * | ( cd /target; tar xfp -)

```
but this will not boot. to repair the bootmanager i would use a chroot to overtake the clone with
```

for fs in proc sys dev dev/pts; do sudo mount --bind /$fs /target/$fs; done
chroot /target

```
and repair bootsector and grub with "grub-install /dev/sda" if /dev/sda is your disk with target partition and then "update-grub"

also etc/fstab needs a repair. use "blkid /dev/sda1" to get the UUID from the target partition if sda1 is your target partition.

and you need new swap partition, make one with mkswap /dev/sda2, if sda2 is your new swap and update fstab. update /etc/uswsusp.conf to get suspend to disk working.

maybe its easier to use synaptic and export a package list script ("file" menu in synaptic) from the old install. then make a new installation and use the script to install all packages from previous install and copy your /home/<usename> data with tar or "cp -a"

---

### Post by Return Privacy on 2010-10-12
You know, I was just thinking. (*always* gets me in trouble....) Is there a way to just copy the special configurations and things I added when I installed the AFP and Avahi stuff to my Ubuntu 10.04 install? If so, then I could just do a new install on an appropriate sized small hard drive, and then put the configurations and changed files in that for AFP and Avahi? I don't remember exactly what I changed, and how many lines of things I had to add. I had to follow quite a few "how to" articles to get that all working correctly. It was not easy, and it required several changes. (this was all to get Time Machine to back up to the Ubuntu's secondary drive from the iMac on the home network. 
That's why I am so hesitant to mess with this install, other than the waste of a good large hard drive.
Does anyone know of what things I should copy from this install, to move to a fresh install and have it all work again? That might be an easier way to go.
Thanks-

---

### Post by antiram on 2010-10-13
normally all configuration files are in /etc or /home/<username>
you can get the file list, including config files, from a installed package with synaptic or eg.
dpkg --listfiles avahi-autoipd
dpkg --listfiles avahi-daemon
dpkg --listfiles netatalk
copy the listed /etc files to new installation.

or have you added config files after after install, eg. selfmade hooks in /etc/dhcp3/dhclient-enter-hooks.d or so? then copy it also.

i would copy everything in 
/etc/avahi/
/etc/dhcp3/
/etc/network
/etc/dbus-1/system.d/avahi-dbus.conf
/etc/default/avahi-daemon
/etc/init.d/avahi-daemon
/etc/init/avahi-daemon.conf
for avahi-autoipd and avahi-autoipd. look self for netatalk /etc files

or copy the whole /etc to the new installation. but this includes lost config files from packages which you have installed and later uninstalled, but not purged.

---

### Post by CharlesA on 2010-10-13
> **mister_p_1998 said:**
> Lets see... going from a 300GB partition to a 150GB partition.. hmm I think that fits FOUR times! he's going from partition to partition.. NOT drive to drive! he's not doing a full drive clone.
Steve

What are you talking about?

The OP of the thread was trying to move an install from a 300GB partition to a partition that is half that size - 150GB. Clonezilla cannot do that, since the destination partition would be smaller then the source.

> **Return Privacy said:**
> 
My question, is how do I move this Ubuntu installation to a smaller (but easily big enough) drive?
It is ridiculous to have to use a large drive for such a small installation.
Thanks

Check out remastersys. It can create an install medium of your install of Ubuntu, so you can install it whenever you want.

---

### Post by Mark Phelps on 2010-10-13
> **mister_p_1998 said:**
> Lets see... going from a 300GB partition to a 150GB partition.. hmm I think that fits FOUR times!

Why do you folks keep arguing this???  

Fromm 300 to 150 is FROM larger TO smaller ... and Clonezilla can NOT do that kind of cloning -- even their own FAQ says so.

---

### Post by Return Privacy on 2010-10-14
Thank you Antiram,

I will give that a try, and see if it moves my custom configuration changes to a new install on a smaller drive.

-RP

---

### Post by robert shearer on 2010-10-14
> **CharlesA said:**
> 
Check out remastersys. It can create an install medium of your install of Ubuntu, so you can install it whenever you want.

+1 for Remastersys
[http://www.geekconnection.org/remastersys/ubuntu.html](http://www.geekconnection.org/remastersys/ubuntu.html)

**move** all your music,photos,vids,data etc to an external backup
.Unmount it and remove any thumb drives etc.
Then run ```
sudo apt-get clean
``` to further reduce extraneous files (note.. you may want to  back-up to **apton-cd** first.. In the repos)

You are trying to reduce to the O/S and apps .Then the system can be compressed to the live iso 

Then your installed system and its user-modified configuration can be written to a custom live dvd using remastersys.

Some research.... 
```
site:ubuntuforums.org remastersys
``` in your browser should give enough hits :)
[http://ubuntuforums.org/showthread.php?t=1514043](http://ubuntuforums.org/showthread.php?t=1514043)

Note that it doesn't save your configuration for graphics-cards and you will have to reconfigure those.

Now you will have a customised live dvd that clones your **current install** and can be re-installed on most hardware just as you would the standard Ubuntu install cd.

---

### Post by mister_p_1998 on 2010-10-14
> **Mark Phelps said:**
> Why do you folks keep arguing this???  

Fromm 300 to 150 is FROM larger TO smaller ... and Clonezilla can NOT do that kind of cloning -- even their own FAQ says so.


Just re-read this and youre right! coulda sworn he wrote 1500GB!! need new glasses!!
Steve

---

### Post by aysiu on 2010-10-14
Remastersys is definitely the way to go. It makes your Ubuntu installation into a live/installer CD/USB.

---

