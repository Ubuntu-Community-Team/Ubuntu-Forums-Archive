---
title: "Suggestions for partitioning a new Acer 5920"
date: 2007-12-11
forum: Installation &amp; Upgrades
---

### Post by Bartender on 2007-12-11
Good morning!
I'm excited and nervous as hell at the same time.  Just bought an Acer 5920 lappy.  2GB RAM, 200GB HDD, Intel Centrino.  I sure hope 7.10 works on it!

There's a 9.76 GB "EISA Configuration" partition at the front of the drive, then a C:\ drive "Windows" partition, then a D:\ drive "Data" partition, then a 3.24 GB "EISA Configuration" partition at the tail of the drive.  Not sure about this, but I believe the "EISA" partitions are for the Acer software, extra keys on the keyboard, etc. (?)  

Already made a set of Recovery DVD's.  Sheesh, the "recovery" data used to fit on a CD or maybe two, now it's two DVD's?!?

For now I want to keep the dreaded Vista instead of removing it.  Does anyone have some suggestions for where to install Ubuntu?  It seems like the best place would be the "Data" partition, but don't know if Vista will keep trying to write documents, music, etc. to the "D" partition.

Thanks!

---

### Post by Partyboi2 on 2007-12-11
Me personally I would resize C: (Vista) and then use the free space to install ubuntu.

---

### Post by ajgreeny on 2007-12-11
I think you are right about the EISA partitions being for recovery of the acer software on the disk at purchase time, so probably best to leave them alone, unless you want to remove windows completely, and keep it away for the life of the machine.  I had the same on an acer travelmate laptop, though only one EISA partition, which I left alone.  Disk C and D were there, as on yours, so I used disk D for ubuntu (Mint actually to try it) as it was empty at the time.  Worked out great.  Both windows XP and linux boot with no problems, though Linux Mint is so much faster.

---

### Post by Bartender on 2007-12-11
I tossed in an Ubuntu 7.10 LiveCD just a few minutes ago.
 
I prefer a dedicated GPartedLiveCD for actual surgery, but the Ubuntu LiveCD was sufficient for just looking. 

Now I'm thinking about resizing the Windows partition (C) down to 30GB or so.  Then re-sizing and moving the Data partition (D) so that it's shoved up against the Windows partition and no larger than 30GB.  Then I should have free space between the Data partition and that second EISA partition to create a large (roughly 100+GB) extended partition with /, swap, and /home.
Theory being nothing goes sideways on me if Windows wants to save personal data to the D drive.

In the LiveCD environment there was no entry for a wireless device in "Network".  The Intel 4965AGN wireless card showed up when I ran lspci.  I've got zero experience with wireless - I hope to God it works when I've installed Ubuntu!!

---

### Post by errenay on 2007-12-11
I have deleted D: partition (Data). There are some problems with E-recovery in such case, but without deleting D: I have had problems with (K)ubuntu installation because there were 4 partitions (EISA with recovery data, C:, D:, and Acer Arcade partition) - too much to create another logical partition for Linux.

---

### Post by Bartender on 2007-12-14
Hi, errenay -
Didn't see your post til too late.  Resized C and D, then gparted would not let me proceed, as you describe.  I shoulda thought of that. Sure wish the manufacturers would stop hogging the entire drive with their own agenda.

Got out of gparted but now Windows won't come up.  Endlessly going thru BIOS screen, then shutting down and restarting.
And my recovery DVD's aren't working either!  
Get a message saying, "Loading Windows Files" then the PC just sits there, with the HDD blinking every few seconds but nothing's progressing.  The optical drive is functioning.  Will wipe the drive clean, then try the recovery DVD again.  That's what the kid at Circuit City (where I bought it) suggested.

---

### Post by errenay on 2007-12-22
AFAIK, resizing NTFS partition (created by Vista) may be difficult and cause errors. MS has changed something in NTFS file system... I hope your laptop is OK now.

---

### Post by Bartender on 2007-12-22
Hi, errenay -
Thanks for the reply.  Lster and I have been working together on figuring out some partitioning stuff with these Acers.  I hope to put our experiences together in the next few days and post.
And, yeah, the Acer is working OK except for that annoying "Cannot allocate..." message during boot and unbalanced sound from the laptop's speakers.  Headphones sound fine but only get sound from the right speaker when playing a CD or using system sounds.  They work fine in Vista.
Have read some posts where people had problems with wireless, hope to test that out at the library in the next couple of days.  I know nothing about configuring wireless so crossing my fingers.
Also read some ominous posts about the DVD Multi-drive not working in DMA.  Haven't tried to burn anything yet.
Any feedback appreciated.  Do you have the 5920 or 5920G?

---

### Post by errenay on 2007-12-23
> Also read some ominous posts about the DVD Multi-drive not working in DMA. Haven't tried to burn anything yet.
No problems with burning CDs or DVDs. I have problem with the drive when I have used Kubuntu 7.04.
> Do you have the 5920 or 5920G?
As far as I know, Acer 5920G (T7300, NVidia 8600M GT, 2 GB, 160 GB HDD, DVD Super Multi DL, Subwoofer, 1GB Intel Turbo Memory). What is the difference between "G" and "no G"? The more detailed number version is AS5920G-302G16N.

---

### Post by Bartender on 2007-12-24
I think "G" is Acer's nomenclature for "gaming".  My 5920 has plain old Intel 965 Mobile graphics and a T5150 CPU.  Also no Turbo Memory (whatever that is) and no HDMI output on side of the chassis.  There are probly a few other differences, but those are the obvious ones.

---

### Post by errenay on 2007-12-25
Thank you for the information. And about Turbo Memory [see here]("http://www.intel.com/design/flash/nand/turbomemory/index.htm"). At this time it is useless in Linux :(

---

### Post by NegativeCreep on 2008-01-29
Here's what did with my 5920. I can't remember exactly how I did this since it's been a few months but this should sum it up. 

I can dual boot into Vista and Gutsy without having any boot options upon powering on.  Pressing the power button boots into Vista. Pressing the Acer Arcade button when the computer is off boots into Ubuntu.  To do this I had to get rid of the Acer Arcade partition, butI found that useless anyways.  The Acer Arcade still works fine in Vista, I just got rid of the separate partition it can boot to with just the Arcade.


Here's what I did:

Resized the data(3rd) partition to leave 20gigs of space after it (including the 4 or whatever  the Acer Arcade took up)

Formatted the Acer arcade(4th) partition as EXT3. This is the partition the system boots to when pressing the Acer Arcade button when the laptop is off.

Installed 7.10 from the alternate installation CD and chose lilo as my boot loader

Grub would not work with the partition setup being used. This could be due to a problem with grub booting over the 137 GB point of the hard drive.  I really didn't feel like researching the problem so I just used lilo and it worked.

I don't remember exactly but at some point when it asked where to install lilo I specified **NOT **to install it to the MBR.  Instead I had it installed to sda4.  

After everything was running I uncommented the "compact” line in the lilo.conf file. If this isn't done you'll get to sit there for 2-3 minutes  watching dots going across the screen every boot up.


There are only a few problems I've found with this setup.  

First is that I don't have a swap partition. I may blow out the recovery partition, make it a gig or 2 swap partition and resize the windows partition to fill the rest of the space, but I haven't seen any need for a swap partition yet. 

The second problem isn’t a big deal, but is annoying when I forget about it.  When rebooting in Ubuntu, the computer will load the boot loader from the MBR and Vista will boot up instead.  So I always have to do a shutdown when wanting to boot into linux

Third, No graphical boot screen because lilo was used instead of grub.  Not that I care. I've seen postings about maybe possible fixes for this, but this isn't that important to me, so unless someone puts an easy 5 second fix in front of me, I'll be perfectly content with the text boot up.

---

### Post by Bartender on 2008-02-07
Starting Linux from the ACER Arcade button?  I love it!

---

### Post by joseph_sp on 2008-03-14
My config is:
- partition for vista recovery
- windows XP pro (removed Vista from C)
- Linux ext3 partition
- swap file (about 3GB)
- Acer Arcade partition 

The acer Arcade partition after I installed Windows Xp doesn't work. When I press the Acer Arcade button it boots in Windows Xp that I have installed. Anyway i will probably remove the arcade partition because even with the Vista didn't work properly. It was strange the fact that Acer Arcade was installed in a separate Windows Xp partition ( from the box the laptop had 4 partitions::):):) recovery, C, D, and the Acer arcade in windows Xp):)

---

### Post by FokkerCharlie on 2008-05-14
Hi All

I have just installed Ubuntu on my new 5920- but now I can't boot into Vista.  (Not such a great problem, OK, but you never know...)

I used GParted to move the partitions- deleted the recovery partition (which as far as I can tell, I don't need, as I have the recovery DVDs), and the D partition created on installation.  I also moved the Vista C partition to the right of the drive, as far as I could up against the Acer Arcade partition.

After this, Vista stopped booting- getting just past the BIOS screen, then restarting, over and over again.

However, I thought that GRUB would sort it out- Vista was detected by the Ubuntu installer (although no user accounts were found), and Vista appears in the GRUB menu.  Selecting this results in a reboot, tho.

Any ideas?  The main good news is that Ubuntu seems to be working well!

Cheers
Charlie

---

### Post by FokkerCharlie on 2008-05-15
OK- I am now dual-booting- here's how I did it:

But first, the disclaimer:  below I describe as best as I can recall the steps I took to get Ubuntu and Vista dual-booting.  Ensure that you backup your data before doing anything else, and I cannot be held responsible if this method does not work for you.

First, install Vista.  Make recovery DVDs from the eRecovery software as per the Acer manual.  Also, it's a good idea to make the Applications and setings disk from the same program.

At this stage, you also find a Vista installation disk.  I think that more or less any flavour will do, but the recovery disk won't. We'll need it later to repair the Vista boot settings, so won't get nearly as far as setting up Windows in earnest with it.  My laptop came with Vista Home Premium installed, but I found a Vista Lite installation iso on a torrent that worked fine.

Uninstall any software that you don't want (Office trial, Norton etc), delete any leftover files, defragment.  Time to put the kettle on (several times) while that goes on.

Here's the risky bit, make sure you're backed up now.

Boot up the System Restore CD- you will need to remove the HDD from the boot list in the BIOS.  If you don't have the System Restore CD, get it here:  [http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page) .
Press enter to boot, select your keyboard layout, then at the prompt, type 'startx'.
Open GParted - disk icon on the right hand side of the screen.  More detailed instructions on GParted are available elsewhere.

Arrange the partitions as you wish- this is how I did mine:

Delete recovery partition- I don't think it's necessary if you have the recovery DVDs.  Delete D drive.
Resize C, and move it to the right, up next to the Acer Arcade partition.  I have left Arcade alone in the hope that I can use it another day.

At this stage, Vista is still on the drive, but you won't be able to boot it.  We'll fix that later.

You should now have a large unused space on the left of the drive.  This is where we will put Ubuntu.

Reboot using the Ubuntu installation CD.  Install using your preferred settings- when the partitioner starts, choose 'Guided - use largest continuous unused space' or similar words.

The installer should detect Vista and XP, allow that to continue.  On my setup, it didn't detect any user settings, but no matter.

Once installation is complete, reboot onto the HDD (you will need to change the BIOS settings again) and check that Ubuntu is working properly.  Make a copy of /etc/boot/grub/menu.lst - put it somewhere convenient, your desktop will do.  Have a look through the file for the name of the partition that Ubuntu is installed on- eg

```
title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,4)
```

In this case, we're interested in (hd0,4)

If you like, you can reboot and see if Vista works with grub.  I don't think it will, but if it does, then you can stop now!

Now it's time to repair the Vista boot settings.  Reboot again into the Vista CD that you downloaded (ie not the recovery disk).  Follow the options for your location and keyboard.  Select 'Repair Computer' and NOT 'Install Windows'!
In the dialog, click the relevant (Vista) OS, and 'Next'.
In the System Recovery Options, choose 'Command Prompt'.

This brings up a terminal - try this:
```
> Bootrec.exe /RebuildBcd
> Bootrec.exe /FixBoot
> Bootrec.exe /FixMbr
```

If you get an error with one of these, try another, and then go back and try again- I can't remember which order they needed to go in.  In the end, you should have been able to run each of these without an error being returned.

Reboot again to the HDD- you should now have Vista working again.  No grub or option to run Ubuntu, so that's what we will fix next.

Boot into the Ubuntu installation CD (via the BIOS settings again, probably).  Choose the option to try Ubuntu without changing your system.
Choose Applications > Accessories > Terminal

```
~> sudo grub
grub> root (hd0,4)     (or whatever your menu.lst told you earlier)
grub> setup (hd0)
grub> quit
~> exit
```

Reboot, and reap the rewards of your labour!  If it's all gone right.
I wrote this guide based on help from The Acer Guy : [http://www.theacerguy.com/2007/09/17/user-review-aspire-5920-from-canada/#comment-3503](http://www.theacerguy.com/2007/09/17/user-review-aspire-5920-from-canada/#comment-3503)
Windows:
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
And APC Mag:
[http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm)

I hope this helps somebody.  If you can offer a correction, addition or comment, please do not hesitate to do so.

Charlie

---

