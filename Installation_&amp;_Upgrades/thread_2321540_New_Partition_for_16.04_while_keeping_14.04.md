---
title: "New Partition for 16.04 while keeping 14.04"
date: 2016-04-22
forum: Installation &amp; Upgrades
---

### Post by flyingsolo on 2016-04-22
My current desktop setup is a Dual Boot of Win 10 with 14.04 with separate / and /home partitions.
It is working just great so the last thing I want to do is pooch the system. (it is backed up; DejaDup)
I've "trialled" 16.04 via a bootable USB and all seems good, though admittedly it's a limited testing.
Rather than wait for the Upgrade option to appear in a few months, I'm considering creating another partition for 16.04 that, hopefully, can access the same /home that already exists.
So my thinking is, use gparted to create another partition from /home (which is ~1.5TB of a 2 TB drive) and install 16.04 to it. Which looks too easy and maybe it is but I'm looking for advice to anticipate trip-up points in this process. Ultimately and assuming 16.04 works fine, it would become my day to day Ubuntu system and next time an LTS is released, it would be installed on/over the current 14.04 partition.
Can you find fault with my thinking or advise a better way? Will the bootloader possibly be a problem? (I'm not sophisticated enough to predict y/n!)

Below is my current list of partitions (the WIN7 is really WIN10 but the original name has persisted after upgrading to Win 10):

/dev/sda1  ntfs    Recovery (not mounted)  
/dev/sda2  ntfs    WIN7     (not mounted)  
/dev/sda3  ntfs    DATA     (not mounted)  
/dev/sda5  ext4             /              
/dev/sda6  ext4             /home

Thanks for suggestions!

---

### Post by Bucky Ball on 2016-04-22
Nope. It's that easy. As long as you have free space for 16.04 LTS, install to that.

When you get to the partitioning section choose 'Something Else' (might be 'manual' or something else in 16.04 but you want the option to partition manually). Set the unallocated space as the / partition of the new install.

Now for the neat part. 'Change' the existing /home and click 'use this partition' but in the main window 'Format' column DON'T tick to format, obviously enough. The existing /swap will be picked up and used by the new install without you doing anything. You don't need a second one (even if you have five installs, they can all use the same /swap, and /home for that matter). 

I presume you have an EFI install?

---

### Post by flyingsolo on 2016-04-23
Yes, EFI installation.
Thanks for the reassurance--a little hand-holding sometimes is needed since I don't go through partitioning and installations very often since the advantage of an LTS version is to give you a solid performing OS that is low maintenance.

---

### Post by Impavidus on 2016-04-23
Running 14.04 and 16.04 alongside each other will be no problem. There are a few things to note though.

The bootloader (grub) will be controlled by the last system installed, which will be 16.04. So after a kernel upgrade in 14.04 grub will only offer to boot the new kernel after update-grub has run in 16.04. After an upgrade to grub itself (which rarely happens), 14.04 may take back control over grub.

Using the same partition as /home partition in both systems can sometimes give problems. You'll have different versions of the same applications writing to the same config files. For some applications this may cause strange results. Even if this applies to you, you may be able to find a hack around it.

---

### Post by flyingsolo on 2016-04-23
> **Bucky Ball said:**
> Nope. It's that easy. As long as you have free space for 16.04 LTS, install to that.

When you said 'free', well I was going to shrink /home (/dev/sda6 in my configuration) to create the space for 16.04, allotting ~30 or 40 GB.

In gparted, I can't seem to do that; maybe I need to unmount that partition before resizing?

---

### Post by ubfan1 on 2016-04-23
+1 on Impavidus' suggestions/warnings about sharing a home with different systems -- a common data partition avoids any conflicts with different versions of things like firefox,... which store some config info in the (hidden) dot files in your home directory.

The details of shrinking a partition can be messy.  Definitely shrink it from the end, not the beginning.  Definitely shrink the filesystem it contains before you shrink the partition.  Definitely check that no files in the filesystem have blocks sitting in the part you are removing from the filesystem.  There are howtos around for doing all that.  Not easy to follow, I messed up the last time I tried on an unused system when I tried it.  Do have backups before doing this.

---

### Post by Bucky Ball on 2016-04-24
Boot from live install media to do this. Don't try doing it running your installed system. Gparted is included by default on live media. 

Boot from media, 'Try Ubuntu', launch Gparted, make sure /home is unmounted (right click and unmount), resize.

---

### Post by flyingsolo on 2016-05-02
I was away for a week so I'm picking up where I left off.

I've resized my /home to provide space for 16.04 and formatted the new partition to ext4 and labelled it U-16.04; it is /dev/sda8 partition.

Now I'm running the install and chosen 'Something else' as advised. When you say "Use the unallocated space as the / partition of the new install, do you mean the newly freed up space (that I just describe above) or the unallocated space where  the original 14.04 has / ? (It is 119 MB of unallocated space between /dev/sda5 which is my 14.04 and /dev/sda6 which is my existing /home.)
If I choose this space, I'm given the option to create a New partition at beginning or end of existing space of 116 MB and to choose ext4 etc including swap and to choose a mount point, which I presume is, /.

Just trying to be *very* careful.

---

### Post by Bucky Ball on 2016-05-02
If the partition is 14.04's / partition, it is not unallocated space. Use the space you just freed up by shrinking the other partition (" ... the newly freed up space ...").

You choose mountpoint /, EXT4, don't do anything about /swap (don't need to create new one if you already have one as that will be picked up and used by the new install 'automagically'). Make sure the only thing that is ticked to format is the new / partition you are installing 16.04 to. 

Along the bottom of the 'Something Else' screen you will see an option for where you want grub. If you install to sda, your new install will run grub (i.e. when you boot the machine the list of OSs will be generated by the 16.04 install). If you install the grub to the same partition as you are installing the OS (i.e. the 16.04 /) then 14.04 will keep control and you'll need to boot into 14.04 and

```
sudo update-grub
```

... after install, reboot and 16.04 should be on the list. If you go with the 14.04 grub, though, if you decide to remove 14.04 at any time you will need to boot to 16.04 and install its grub to sda. That's easy enough and one line of code. 

Good luck.

---

### Post by flyingsolo on 2016-05-05
Well, I've had partial success I suppose.
I've got 16.04 installed with its own swap (the install process required this) and own partition. When I open 16.04, I don't have access to all the files etc that I had on my 14.04 install. Also, it sounds as if the disk is always spinning when in 16.04; if I restart into the old 14.04, this isn't the case and I have access to all my old files etc.
Also, the boot list when starting includes 16.04 at top and 14.04 lower down but my Win 10 install isn't available.
My current partitioning is (sda8 is U-16.04):

NAME   FSTYPE LABEL    UUID                                 MOUNTPOINT
sda                                                         
&#9500;&#9472;sda1 ntfs   Recovery 38F8A645F8A6016C                     
&#9500;&#9472;sda2 ntfs   Win10    01CD294BE19A3C40                     
&#9500;&#9472;sda3 ntfs   DATA     01CD2A5DF0C61190                     
&#9500;&#9472;sda4                                                      
&#9500;&#9472;sda5 ext4   U-14.04  63bd3ff6-d898-40c1-8726-50b0441bb7a0 
&#9500;&#9472;sda6 ext4   home     6d43e929-bebb-48cb-bfcb-b1eccd2bc1f4 
&#9500;&#9472;sda7                                                      
&#9500;&#9472;sda8 ext4            e3ec815c-e5c8-47b1-866d-6bf8fc7abca6 /
&#9492;&#9472;sda9 swap            cc8275ff-a9c1-4f43-a21c-042efd52d353 [SWAP]

Thanks for your patience!

---

### Post by oldfred on 2016-05-05
If not seeing files, did you not follow Bucky's advice in post #2 and mount, but not format /home as part of your install of 16.04?

You can add it by editing fstab, probably easiest to copy fstab entry from your 14.04 install into your 16.04 install.

---

### Post by Bucky Ball on 2016-05-05
> **Bucky Ball said:**
> ... don't do anything about /swap (don't need to create new one if you already have one as that will be picked up and used by the new install 'automagically').

You missed this? Two /swap partitions is redundant. You only need one as you can't use both install simultaneously. :)

If you don't have access to some files, is the partition they reside on mounted?

Open a terminal and:

```
sudo update-grub
```

Reboot. Is Windows there?

(* Didn't see oldfred's post there. That too. :))

---

### Post by flyingsolo on 2016-05-06
Oldfred, I think you're right, I didn't follow instructions to the letter, probably as I've been attending to this in evenings (tired) and got confused a bit as the Ubuntu install was requesting a swap space. I did think it strange to need to duplicate this but did it anyway, relative noob that I am!

sudo update-grub did re-establish access to the Win 10 install, so thanks again for that.

I'm wondering if maybe I should just go back a few steps by taking my recently created 2nd swap space and U 16.04 install space, wipe them and join them in one partition space, in order to try the install again, following BuckyBall's original instructions more carefully.

Sound like a plan or am I risking creating more pain? Being a fresh install of 16.04, nothing is there yet of value to keep at this point.

---

### Post by oldfred on 2016-05-06
As long as you use Something Else to install you should be ok.

Its just in forum we like to fix things, even if a re-install is easier. I now have an install to partitions prepared in advance from an  ISO on HDD to SSD in 10 Minutes. Another 10-20 for downloads and a configuration script & in less than an hour I can have it totally configured.

---

### Post by flyingsolo on 2016-05-06
Thanks. I think I'll go the re-install path!

FWIW, I *did* use the Something Else installation the first time but I likely got perplexed by the request to create a swap space that I thought it was going to recognize as being there already.

---

### Post by Bucky Ball on 2016-05-06
* HAHA. Disregard the following as you posted you'd gone the reinstall before I got it up! LOL. Anyway, hopefully it will help others. 
___

If you only want to eradicate the second /swap, expand / into the space you've left and use the old /swap, you don't need a reinstall, just a bit of tweaking and possibly some help from us.

It goes like this. Open Gparted, right click the NEW /swap and 'swapoff' then delete the /swap partition. Don't worry, nothing will happen. Now for the (slightly) tricky bit. You open the /etc/fstab file and edit the line concerning /swap to reference your original /swap rather than the new, deleted one.

Open your /etc/fstab file and look for the line that includes /swap somewhere in it. That is the line that boots /swap and points the system to it at start up.

Your /swap line will look something like this:

```
# swap was on /dev/sda7 during installation
UUID=63d86782-bff4-41c1-924f-37d093fbe371 none            swap    sw           $
```

See this number? '63d86782-bff4-41c1-924f-37d093fbe371'? Yours will be different, but that's the one you want to replace. That will be an entry for the /swap you created with the new install (making sure you are running from the new install), now deleted and you want to replace it with the old one's UUID. Easy(!). Run this:

```
sudo blkid
```

In that list, look for your /swap partition. It will look something like this:

```
/dev/sda7: UUID="63d86782-bff4-41c1-924f-37d093fbe371" TYPE="swap" PARTUUID="f4a0f721-07"
```

Notice how the UUID number for my /swap is the same in the output of this command as the number in my /etc/fstab? Yours won't be as your original /swap is deleted. You're getting it? 

Now:

```
sudo nano /etc/fstab
```

Find that /swap line we looked at to start, remove the original UUID number and replace with the UUID of your original /swap. Save and exit the file, reboot, launch Gparted, right click the old /swap and check it is set as /swapon. If not, something's wrong. 

Hope that's of some help and saves a reinstall. Looks a lot here but really quite straightforward and doesn't take long. Good luck. ;)

___

An example. If your old /swap UUID (which you want to use) is '865e6caa-b7bf-49b5-8d41-bf7e8d03be32' and your new one (which you don't want and deleted) was same as mine, then you would change this:


```
# swap was on /dev/sda7 during installation
UUID=63d86782-bff4-41c1-924f-37d093fbe371 none            swap    sw           $
```

... to this:

```
# swap was on /dev/sda7 during installation
UUID=865e6caa-b7bf-49b5-8d41-bf7e8d03be32 none            swap    sw           $
```

:)

---

### Post by flyingsolo on 2016-05-07
Before the latest post here of BuckyBall, I had decided to do the reinstall anyway. I'm trying to be certain to follow your original advice and have chosen the available free space for / but where you said to select the existing /home and "Use this partition", well, I don't get that option.
If I highlight /home and click Change, the default is "Do not use the partition" and all the listed options are various formattings of ext4, ext3, est2,btrfs journaling, JFS etc... including swap, EFI System Partition. The option i *don't* get offered is "Use this partition".
So, I'm not sure how to follow the advice you gave in one of the earliest posts and was probably the problem I encountered when I first installed 16.04.
Still stymied, I guess. Bedtime here, so I'll check for replies tomorrow.
Thanks.

---

### Post by Bucky Ball on 2016-05-07
You simply right click the existing /home, tick 'Use this partition', go back to the main change and DON"T tick 'Format' in the Format column for the /home partition. The install will then 'automagically' use the existing /swap and won't create a new one, either partition or folder in /.

Same with /swap. If you have one, simply don't create one and the install will pick it up. You don't need to tick the 'Format' or 'Use the Partition' for /swap. It just does it. 'mazing. ;)

Goes without saying, but I'll say it: this is when using the 'Something Else' option.

---

### Post by flyingsolo on 2016-05-08
> **Bucky Ball said:**
> You simply right click the existing /home, tick 'Use this partition', go back to the main change and DON"T tick 'Format' in the Format column for the /home partition. 

But my main problem is I don't get the option, 'Use this partition', when I do as you say. In fact, right clicking does nothing (no response) so I highlight the partition and click the 'Change..." button below where I get the list of options I mentioned earlier which is defaulted to 'Do not use this partition' and I can right click that list and see all the various formatting options but no entry to 'Use this partition'.
So, this is my dilemma!

---

### Post by flyingsolo on 2016-05-08
Maybe I've been taking your instructions too literally. I've tried the following:
-highlight existing /home
-click 'Change'
-in box 'Use as:', I've ticked Ext4, but NOT ticked Format option and then chosen for Mount point: /home

I think this is probably what you meant b/c simply right clicking the /home partition didn't present the option to Use this partition but only gave its opposite.

---

### Post by Bucky Ball on 2016-05-08
You untick 'Don't use this partition!' :D

Yes, sorry, my mistake. You highlight the partition the 'Change' and the option is there, not right click for the options. Doh! I was thinking of Gparted. :|

Don't do 'Use as' or change ANYTHING else. Leave EVERYTHING else as it is. Just highlight partition, change, make sure 'Do not use partition' is unticked, get out of there. That is all. Change nothing else.

---

### Post by flyingsolo on 2016-05-08
All is right with my (ubuntu) world again!
Thanks again to Oldfred and BuckyBall. I was pretty sure I had it correctly interpreted so I went ahead with the install.

My only residual issue is really a separate thing and probably warrants some digging around the forums but the 16.04 install does cause the fans on computer to be running  constantly which makes it loud and annoying and I'm sure they aren't necessary for heat dissipation b/c the system is just idling, doing nothing at all. Is this perhaps a known problem?
Anyway, thanks for your respect help and patience.

---

### Post by Bucky Ball on 2016-05-09
All good. Please mark this as solved (Thread Tools at top right or link in my signature for how) and post a new thread for the fan whirring issue, please. Good luck. :)

---

### Post by flyingsolo on 2016-05-09
Yes, I was intending to mark this but just waited a bit to use the new setup a couple of times to be sure it was good to go.
One last thing, any suggestions of where's best to post re continuing fan for best attention? 
Cheers,

---

### Post by Bucky Ball on 2016-05-10
***General Help*** or ***Hardware*** might be best.

---

