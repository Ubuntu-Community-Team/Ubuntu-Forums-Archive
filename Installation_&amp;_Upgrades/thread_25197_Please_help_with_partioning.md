---
title: "Please help with partioning"
date: 2005-04-09
forum: Installation &amp; Upgrades
---

### Post by pterandon on 2005-04-09
Hello, first let me introduce myself.  I'm a computer whiz kid (age 40) when it comes to getting an existing application to do cool things, but I'm unusually dense when it comes to understanding hardware.  Perhaps I shouldn't have tried linux as it may be over my head, but I was drawn to ubuntu for the political / humanitarian agenda underlying it.

I have a new IBM Aptiva  with 3.2 GHz chip and 160 GB HDD.

I saw that ubuntu installation could automatically do the partitioning but my fear is that you all have left enough rope for dummies such as myself to hang myself, and I have done just that.

It originally was showing two partitions,  one at 4.0 GB and one at 156.0GB.

Now my hunch is that if Linux works out for me I'll use it maybe 70% of the time, but I'm guessing I'll occasionally and eventually need to fall back to Windows XP. 

Could someone puulllllease   ](*,)  ](*,)   help me figure out how to partition, just tell me what to do:

RIght now after much unintelligent goofing around the system says:


SCSI1 (0,0,0)  (sda) - 160.0 GB ATA Maxtor 6Y16OMO
  #1 primary 60.0 GB   (black smiley)  lvm
  #2 primary 96.0 GB   (down lightning bolt) (skull crossbones)  fat32
  #3 primary  4.0 GB     fat32.


Based on a guess of using this PC 70% of the time for linux, please tell me how to change the above so that ubuntu will install.  I don't even know if 60:96:4 GB makes any sense at all.

Thanks kindly.

My frustration level is extremely high but I know I'm doing something over my head and have been in other freeware communities (povray) where I've grown to appreciate the necessity of understanding that online-helpers are helping out of the goodness of their heart and no obligation, so thanks in advance, even though I am compelled to put a row of emoticons:

 ](*,)  ](*,)  ](*,)  ](*,)  ](*,)  ](*,) 


Greg M. Johnson

---

### Post by Lustiger Lurch on 2005-04-09
you bought the stuff right away and have no data on the hd?

then make ist 10-15 GB for Windows (NTFS oder FAT32), 10-15 GB for Linux (ext) and the Rest for Data Storage (FAT32) used by both Systems


at first u install windows, then ubuntu (which will set up a boot manager for you)

---

### Post by az on 2005-04-09
Decide how much space you want window to have, then decide how much you want Ubuntu to have.

Install windows.

Boot the Ubuntu installer and make your way to partitioning.  Go to the manual partitioning option.

Select the window spartition to shrink and give it a smaller size.  Make it go.

You will now be brought back to the listing and see free space.  Chose guided partitioning and it will calculate and suggest a partitioning scheme with that.

---

### Post by pterandon on 2005-04-09
Thanks kindly for two speedy replies.  8-)  8-) 

FWIW, the PC came with WinXP installed & fully operational.  I was just clueless about the partitioning I was doing with the help of the ubuntu installer.   I'm assuming that doesn't negate any advice given.   

Thanks, will try it tonite. 

Q: does the black smiley, down lightning bolt, and skull & crossbones have any meaning?

Stupid Q: say I were to have some files which are essentially ascii text.  Would they then be fully reachable by  applications running under <b>both</b> a WinXP boot and a ubuntu linux boot? 

THanks.

---

### Post by gflores on 2005-04-09
1. I'm not entirely sure, but I believe that the smiley means that it is a formatted drive and the lightning bolt represents a GRUB-installed partition. I forget what the skull & bones means. I believe there is some documentation in the installation process (under partitioning guide). 

2. Do you mean, if you were to create a text file in either Linux or XP, would you be able to read it from the other OS? The answer is yes. However, you will not be able to write (make changes) to files in your XP partition and vice versa. You can make copies of them, however. 

If you're using ext3 as your filesystem in Ubuntu, then to read the files there from within XP, you can try this program. [Explore2fs](http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm)

To read files from WindowsXP partition, you have to mount the drive. Read here.
[http://ubuntuguide.org/#windows](http://ubuntuguide.org/#windows)

Edit: Here's my setup, so that you can look at.

I created a new partition when I reinstalled WindowsXP and allocated about ~30gb of free space for Linux. Then when I came to install Ubuntu, from that free space, I created the swap partition (1gb), a root partition (14gb), and home partition (15gb). That was it.

---

### Post by jerome bettis on 2005-04-09
the lightning bolt means the bootable flag is on.  this only needs to be the case for your root partition, unless you set up a seperate /boot partition which would need the flag instead.  you can read files from your FAT32 partitions in either system, but windows can't see your linux ext3 files, at least not without third party software.  i think the skull and bones means it's getting formatted, and the smiley faces ummm i forget the differences, but i think one of them is for when you're keeping the existing data.

160 gigs is a lot of space, and partitioning is not something you want to do twice.  that said, give this some serious thought before you rush off and do it.

if you plan to use windows more often, you'll want that closer to the beginning of the drive, linux can go behind it.  or vice versa.

personally, i would set up a 2 gig primary partition at the beginning of the drive for / (root partition).  this is the fastest part of the drive, you want the kernel and libraries here.  2 gigs is definately enough if you make seperate /usr /var /boot and /home partitions.  after that, i'd make an extended partition, which contains logical partitions: at least 10 gigs for /usr, about 5 for /var (i have 2 for this and have ran out), 50 megs for /boot (set the flag) and however much you want for /home.  actually in between /boot and /home it's probably a good space for your swap partition, which should be 2x the size of your ram (it will probably never get used anyway).  ext3 is a great file system, i would use that across the board except for /boot is so small ext2 is ok.

that scheme works pretty well with ubuntu, but it's just my suggestion.  you might be doing something totally different than i do, and might want to come up with your own scheme.

after that you need a primary partition on the first hard drive in the system for windows - at least 10 gigs but proably a lot more.  i also have a 1g FAT 32 partition in the very end of my drive which i use for sharing files between the two (mp3s and such).

you might want to consider leaving some empty space at the end of the drive after windows, so if you want to try some other distros later on, you can do that easily without backing anything up.  plus you'll be able to share the /boot and /home directories among distros which is really nice! 

i actually boot into gentoo and have a script which starts my ubuntu desktop in a chrooted environment.  it's really slick, the best of both worlds - everything i like about ubuntu running on a faster base.

---

### Post by pterandon on 2005-04-09
The repartitioning that I tried hung up. Empty blue screen with no crunching, nothing, for a long time (5 minutes at least).  So (okay, was I an idiot?)  unplugged it.  Now there's 'missing operating system' when I tried to go straight to Windows just to check how it was. 

So I'm formatting whole disk, using that option in the installer.

Fortunately, I've got a new PC for which I can be **completely** laid back about the potential loss of data, 'cuz I ain't got no data on it. And it's to be my hobby, hobby PC. 

This is a completely brave new voyage  for me, and I've sort of already drowned.  Not giving up, but it's kind of liberating to be already dead.   O:)

---

### Post by benplaut on 2005-04-09
[QUOTE=pterandon]The repartitioning that I tried hung up. Empty blue screen with no crunching, nothing, for a long time (5 minutes at least). So (okay, was I an idiot?) unplugged it. Now there's 'missing operating system' when I tried to go straight to Windows just to check how it was. 

So I'm formatting whole disk, using that option in the installer.

Fortunately, I've got a new PC for which I can be **completely** laid back about the potential loss of data, 'cuz I ain't got no data on it. And it's to be my hobby, hobby PC. 

This is a completely brave new voyage for me, and I've sort of already drowned. Not giving up, but it's kind of liberating to be already dead. O:)[/QUOTE]

thout shalt be ressurected by [img]http://commons.wikimedia.org/upload/thumb/5/5f/20px-Tux.png[/img]

---

