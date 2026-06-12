---
title: "Hosed GRUB trying to install Mate 16.04, can't boot"
date: 2016-05-15
forum: Installation &amp; Upgrades
---

### Post by watchpocket on 2016-05-15
So I tried to install Ubuntu Mate 16.04 earlier tonight from a live USB flash drive to a standalone SSD drive (plugged into another USB port on my desktop machine).  

I selected the correct drive during the installation process (the SSD drive, *sde*), but I think my mistake was that, when the installation prompted to enter a username and a computer name, I entered my computer's name but got a warning that that name was already being used (by, I think it said "another computer", forget the exact wording).  It's the name my computer -- or my current Ubuntu -- has, and I wanted to keep the same name.

**Instead of entering a different name, I went with the same name anyway.  That was probably my mistake.**  The install process continued, but when I tried to boot from the SSD drive, it wouldn't boot. 

Then I tried to boot normally, with both the USB drive and the SSD drive unplugged.  Normally I'm put at my custom GRUB menu that allows me to select one of two internal drives (one drive with Ubuntu 14.04, the other with Ubuntu 12.04).  (If I do nothing, 14.04 automatically boots after 5 seconds.)

Instead of seeing the GRUB menu, all I got was:

[COLOR=#0000ff][I][B]error: no such device: [long UUID]
Entering rescue mode . . .
grub rescue>_[/B][/I][/COLOR]

The only command that I knew to enter here that returned anything was ***ls***, which returned:

[B][I](hd0) (hd0, msdos2) (hd0, msdos1)
(hd1) (hd1, msdos2) (hd1, msdos1)
(hd2) (hd2) (hd2, msdos1)

[/I][/B]I have three one-terabyte spinning drives in my desktop unit, the third drive has no OS and is only for data storage.

I'm only able to post this message by booting into my live USB flashdrive's ubuntuMATE "Try Ubuntu MATE" interface, using its Firefox.  The only thing I can boot from at the moment is the live USB flash drive.

All three of my internal drives appear to be intact, but [I][B]what do I need to do to be able to boot normally into my 14.04 and 12.04 drives.
[/B][/I]
i.e., [I][B]how do I get my GRUB menu back?

[/B][/I]Very uncertain & somewhat desperate about this turn of events, thanks for any clear steerage.

---

### Post by Bucky Ball on 2016-05-15
[Boot Repair]("https://help.ubuntu.com/community/Boot-Repair") may be your friend, but first, it gives you the option to run the bootinfo script on the first screen (from memory). Do that and post the link it gives you when it's finished, please.

You can install it directly in a live session. Just follow the instructions on that link. If you reboot you will need to go through it all again as anything you install on a live session will be lost on boot (but you probably know that). ;)

---

### Post by watchpocket on 2016-05-15
> **Bucky Ball said:**
> [Boot Repair]("https://help.ubuntu.com/community/Boot-Repair") may be your friend, but first, it gives you the option to run the bootinfo script on the first screen (from memory). Do that and post the link it gives you when it's finished, please.

You can install it directly in a live session. Just follow the instructions on that link. If you reboot you will need to go through it all again as anything you install on a live session will be lost on boot (but you probably know that). ;)


Thanks loads!  here's the pastebin link to the bootinfo summary:

[http://paste2.org/0BO478M9](http://paste2.org/0BO478M9)

---

### Post by Bucky Ball on 2016-05-15
Well, you have 14.04 on sda1, 12.04 on sdb1 and 16.04 nowhere. It's not installed. The problem could be with sdd1, a mystery partition. Don't know what that is but looks to be causing an issue. Is it the partition you were trying to install to? It is 'busy' and looks to be holding things up. If external, unplug it and any other external drives. 

In boot repair, there is an option to reinstall grub to a location of your choice. Choose to install grub to sda then reboot and see where you get to. Any different?

PS: You don't need multiple /swap files. You can use the same one for all installs as they are not booting at the same time. When installing, simply choose 'Something Else' and point the install to the existing /swap (in other words, do nothing about swap). If there is a /swap there, it will be used 'automagically'.

You can change where an OSs looks for /swap by changing the /etc/fstab file, but that's for later and another thread perhaps. ;)

---

### Post by watchpocket on 2016-05-15
***sdd*** is a total mistake and only got there earlier tonight.  Whatever it is, it shouldn't be there.  It is not external.   It's definitely not what I was trying to install 16.04 to.  

But it looks like ***sdd ***is what **some mutant instance of 16.04 WAS **installed to.

I was trying to install 16.04 Mate on a standalone SSD drive, which is definitely not connected now.

The "Disks" utility program shows sdd and has named it:

[I][B]1.6 GB Loop Device
/cdrom/casper/filesystem.squashfs

[/B][/I]Size: 1.6 GB
Device: /dev/loop0 (Read-Only)
Contents: Unknown (squashfs 4.0) -- Mounted at /rofs[I][B]


GParted shows /dev/sdd (15.29 GiB) as follows:

[/B][COLOR=#0000ff]Partition: /dev/sdd1;
file system: unknown
Label: Ubunt-MATE 16.04 LTS amd64
Size 4.00 KiB

Partition: unallocated
File System: unallocated
Size 1.47 GiB

Partition: /dev/sdd2
File system: fat16
Size 2.31 MiB; Used 2.30 MiB; Unused: 8.00 KiB

Partition: unallocated
File System: unallocated
Size 13.82 GiB
[/COLOR][/I]
I should probably remove ***sdd***, but will wait on that for now.

I'll go ahead and use the Boot Repair util to install grub to sda and re-boot, and report back.  Thanks for the help.

---

### Post by watchpocket on 2016-05-15
***WHEW !!!***   

I'm back to normal.  Simply locating GRUB per your suggestion on sda, using the Boot Repair util, has given me the GRUB menu back completely intact.

(It looks just a bit different in that it now includes additional choices, but that's fine.)

Also, according to both the "Disks" util and GParted, ***sdd ***has **vanished**.  And that's fine by me.

Thank you for being there, Bucky.  

Time now for some sleep. Tomorrow when I re-group I'll need to make sure I have a better handle on just how I'm installing, and where I'm installing to.  Thanks again - you guys are totally giving of the great unwashed multitudes of us who trip over our own elbows.

---

### Post by Bucky Ball on 2016-05-15
Hehe. All good and glad I could help. Great that you're getting somewhere with it. Yes, Boot Repair is your friend! (Got me out of many a tight situation. You could do it all with a terminal, but ...)

Last tip: Have a good luck at what you have already on those drives in there, specifically the drive you are intending to install to. Draw a 'mud-map' of the drive and how you'd like it to look when you've finished partitioning. This can be of great help in 'the heat of the moment' when installing, so to speak. ;)

And remember, you only need the one /swap partition. No need to create a new one. In fact, depending on how much RAM you have, no /swap at all will work fine. Not that's that what you want, but reassuring in as much as if anything goes amiss with the /swap during install but you manage to install Ubuntu, you can always point it to use whatever /swap you want later by editing /etc/fstab. 

PS: I notice you have marked this as solved. That's fine as the original issue is solved, but advise you now post a new thread if you have any further issues with installing. Post a link to that here if you like and I'll see if there's anything I can help with. Good luck and let us know how it goes.

---

### Post by watchpocket on 2016-05-15
> **Bucky Ball said:**
>  . . . Have a good luck at what you have already on those drives in there, specifically the drive you are intending to install to. 

I have a new, empty, outboard standalone SSD drive as the drive I want to install UbuntuMATE-16.04 to -- [a Sandisk Ultra II 960 GB SATA III drive]("http://www.amazon.com/SanDisk-Ultra-2-5-Inch-Height-SDSSDHII-960G-G25/dp/B00M8ABHVQ?ie=UTF8&psc=1&redirect=true&ref_=oh_aui_detailpage_o04_s00").  (Actually it's no longer empty because of a previous botched install-attempt, but everything that's on it now can be wiped.)

> **Bucky Ball said:**
> Draw a 'mud-map' of the drive and how you'd like it to look when you've finished partitioning. This can be of great help in 'the heat of the moment' when installing, so to speak. ;) 

All I want on that SSD is one large partition for both / and /home, with about 10 GB of unallocated space (maximum) and maybe 8 or 10 GB of swapspace.

But I'm a bit unclear as to how and when to format it, because I did format it that way, but then, the installation process appears to format it again, or in addition to the original formatting, inserting extra things -- partitions, swapspace -- that I don't want or need.  (More on this in a separate post.)
  
> **Bucky Ball said:**
>  And remember, you only need the one /swap partition. 

***Per drive***, correct?  If I boot 14.04 on sda, the swapspace on the unmounted sdb drive isn't going to do me any good (even if sdb is mounted, yes?) and isn't available to me at all when I'm booted to sda.

PS:> **Bucky Ball said:**
>   I notice you have marked this as solved. That's fine as the original issue is solved, but advise you now post a new thread if you have any further issues with installing. 

Yes, I've been planning to do that as a separate discussion.

> **Bucky Ball said:**
>  Post a link to that here if you like and I'll see if there's anything I can help with. Good luck and let us know how it goes.

Will do, thanks again!

---

### Post by Bucky Ball on 2016-05-15
You need a /swap partition, 2Gb unless you are hibernating, a /home if you are having one (although I let it install in / as a partition and put symlinks in there to a data partition on another drive), and / for the OS. 

Choose 'Something Else' at the partitioning section of the install and you can assign mountpoints and partitions/partition sizes there.

Doesn't matter where the /swap is. Same drive, different drive to /, doesn't matter. Just point fstab to wherever it is. I repeat: If there is a /swap partition anywhere during install, the install should see it and use it. If it doesn't, not an issue. It can be set up later.

---

### Post by watchpocket on 2016-05-16
> **Bucky Ball said:**
> You need a /swap partition, 2Gb unless you are hibernating, a /home if you are having one (although I let it install in / as a partition and put symlinks in there to a data partition on another drive), and / for the OS. 

Choose 'Something Else' at the partitioning section of the install and you can assign mountpoints and partitions/partition sizes there.

Doesn't matter where the /swap is. Same drive, different drive to /, doesn't matter. Just point fstab to wherever it is. I repeat: If there is a /swap partition anywhere during install, the install should see it and use it. If it doesn't, not an issue. It can be set up later.

So first I re-formatted the SSD -- I made one large partition, with a 10 GB swap area, and 10 GB unallocated.  (See attached pic to see what it looks like in GParted.)  Last night I didn't even have the boot flag activated.

[ATTACH=CONFIG]269109[/ATTACH]

Then I re-installed MATE 16.04, choosing "Something else," and selected not to have the partitions changed.  the install process seemed to go OK.  When prompted to define the root file system, I went into the installer's partition menu and told it to go to ***sde***.  Swap was already defined.

Two things about the install process I thought seemed a bit off were:

 (a) the notice saying swap would be formatted to sda2, sdb2, and sde2.  Fine, but I get worried when it starts talking about sda and sdb. Swap was already defined in those drives, I want the installer not to touch sda and sdb.  I selected to install to sde.

(b) when I entered the name of the computer for the network to see, I couldn't put the pre-existing name in, so this time I changed the spelling of it. (But maybe that's not so important & maybe I can change it later.)

Re-booting without the SSD plugged in is no problem, the grub menu appears as it should.  

But when I re-boot with the SSD connected via USB, instead of 16.04 booting, I see this:

[I][B]error: invalid arch-independent ELF magic.
Entering rescue mode . . .
grub rescue . . . 

[/B][/I]At this point I'm not sure how to get the SSD to boot into 16.04.  Any & all tips appreciated, as always.

(Btw, I made a Boot-Repair-Disk today on a spare flashdrive, after last night's experience.[I][B])
[/B][/I]

---

### Post by watchpocket on 2016-05-16
Btw, in wanting to boot to the external SSD via USB, I'm just doing this to make sure I have UbuntuMATE 16.04 correctly installed and up & running and bootable from the SSD.  

My main goal is to remove the internal spinner HDD drive ***sdb***, on which Ubuntu 12.04 now resides, and replace that HDD with the SSD as the main bootable drive, in which I'd like the SSD with 16.04 on it to then be drive*** sda***.  

What is now ***sda*** with UbuntuMATE 14.04 would then be my made my ***sdb***.

The drive that now has 12.04 on it would be wiped, and put in an enclosure to be used as an external storage drive.

So that [COLOR=#0000ff]**new**[/COLOR] 16.04 would be the default boot from the internal SSD (which would then be made drive ***sda***), and **[COLOR=#0000ff]old[/COLOR]** 14.04 would be the alternative boot from the internal spinning HDD (what is now ***sda*** but will be changed to ***sdb***)[I].

[/I]Meanwhile searching right now on the ELF error message, I think I somhow need my grub, which is on sda, to recognize sde when it's connected.  Still searching.

---

### Post by Bucky Ball on 2016-05-16
Sorry, but you don't seem to be getting this bit.  

A/ you don't ever need more than one /swap. I have mentioned this a number of times so can't figure out why you are now creating one, and creating a 10Gb one at that. How large is your installed RAM and do you intend hibernating???

B/ At the bottom of the 'Something Else' screen you will see a drop down asking where you want to put grub. Install it to the same partition as you are install 16.04. Once installed, boot and your other install will appear. Boot into that, open a terminal and:

> sudo grub-update

That will pick up the new install and add it to the menu.

The other option is to install grub to sda (NOT a partition on sda) and then 16.04 will have control of the grub. You may need to run the above command on first boot.

---

### Post by watchpocket on 2016-05-16
> **Bucky Ball said:**
>  Doesn't matter where the /swap is. Same drive, different drive to /,  doesn't matter. Just point fstab to wherever it is. I repeat: If there  is a /swap partition anywhere during install, the install should see it  and use it. 

> **Bucky Ball said:**
>  A/ you don't ever need more than one /swap. I have mentioned this a number of times so can't figure out why you are now creating one, 

Most of the time in my computer use, I have only one hard drive mounted. 

Are you saying that ***mounted drive A*** is [COLOR=#ff0000]actually able to use[/COLOR] the swap partition that is on ***[COLOR=#0000ff]unmounted[/COLOR] drive B***?  

How can it use the /swap on an **unmounted** drive?  I didn't think that was possible.  That's why I have a swap partition on both drives that contain an OS.

> **Bucky Ball said:**
>   and creating a 10Gb one at that. 

I'll either get rid of the swap partition on the SSD or reduce it 2 GB.

> **Bucky Ball said:**
>  How large is your installed RAM and do you intend hibernating??? 

I have 8 GB of RAM, I never hibernate and don't plan to.

> **Bucky Ball said:**
>  B/ At the bottom of the 'Something Else' screen you will see a drop down asking where you want to put grub. Install it to the same partition as you are install 16.04. Once installed, boot and your other install will appear. Boot into that, open a terminal and:

                                                         *sudo grub-update                      *

That will pick up the new install and add it to the menu. 

Got it, will do.   Mucho thanks.

---

### Post by Bucky Ball on 2016-05-16
No, in that case, can't use /swap partition on an unmounted drive. :)

But hang on. After rereading earlier posts, if I've got it right, I think I may have misled. You are installing Ubuntu on the SSD? You have no other installs on the other drive that are going to be included?

If this is the case, just let it roll. Don't worry about pointing grub anywhere during 'Something Else', let it do that 'automagically'.

---

### Post by watchpocket on 2016-05-16
> **Bucky Ball said:**
> You are installing Ubuntu on the SSD? 

That's correct.  I've already installed UbuntuMATE [COLOR=#008000]***16.04***[/COLOR] on my new 960 GB SSD.  

(I just haven't been able to boot to it yet, so I'm not totally sure 16.04 is installed there correctly, but I think -- I hope -- it is.)  

> **Bucky Ball said:**
>  You have no other installs on the other drive that are going to be included? 

I do have one other (previous) install (and I'm not, btw, trying to install right now anything other than MATE 16.04, which, as mentioned above, should already be on the SSD) -- I have UbuntuMATE [COLOR=#008000]***14.04 ***[/COLOR]on another (internal) drive. (Currently, that's drive*** sda***. Drive ***sda*** is a one-terabyte mechanical spinning HDD.)



So far, I've been trying to install MATE 16.04 on the SSD with the SSD being used as ***an external drive plugged into a USB port***.

What I'm going to do -- though this will have to wait a few days, until Thursday -- is the following:

[COLOR=#0000ff]***(a)***[/COLOR]   install the SSD into the inside of my desktop box as an internal drive, and make the SSD my ***[COLOR=#ff0000]drive[/COLOR] [COLOR=#ff0000]sda[/COLOR]***.  This will have MATE [COLOR=#008000]***16.04 ***[/COLOR]on it, and will be the drive I'll want to boot to by default;

[COLOR=#0000ff]***(b) ***[/COLOR]  make it so the spinner drive containing MATE ***[COLOR=#008000]14.04[/COLOR]***  -- currently drive ***sda*** -- will, in the new set-up, be ***[COLOR=#ff0000]drive[/COLOR] [COLOR=#ff0000]sdb[/COLOR]*** (and I'll leave 14.04 on that drive);

[COLOR=#0000ff]***(c)***[/COLOR]   leave my third hard drive -- another one-terabyte spinner -- which has no OS on it, but is only for data storage, I'll leave that as my ***[COLOR=#ff0000]drive[/COLOR] [COLOR=#ff0000]sdc[/COLOR]***;

[COLOR=#0000ff]***(d)***[/COLOR]   at that point I'll need to make sure my GRUB is set up correctly.  I'll want GRUB to be on ***[COLOR=#ff0000]drive[/COLOR] [COLOR=#ff0000]sda[/COLOR]*** -- the SSD -- and my thought is that I may be able to put GRUB on [COLOR=#ff0000]***sda***[/COLOR] by using Boot-Repair, using the same "locate" feature that served me well on your advice a couple of nights ago. 

 Or, I may not be able to do that -- I may have to re-install 16.04 onto the SSD in order to have GRUB working so that GRUB will (1) present a menu to choose to boot into either 16.04 or 14.04; and (2) auto-boot into 16.04 after five seconds.  What I don't know is, with this new set-up, whether GRUB should be placed on*** [COLOR=#ff0000]sda[/COLOR]***, or on*** [COLOR=#ff0000]sda1[/COLOR]***.

I'll report back after I've attempted the above, thanks as always.

---

### Post by Bucky Ball on 2016-05-17
Ok. My suggestion would be to put the SSD in the computer first up. A number of reasons for this.

Some laptops will only want to boot from sda. Trying to get them to do otherwise can be time consuming and unsuccessful. Also, if you manage to install 16.04 correctly on sdb (which you may already have) then the grub set up will be totally out of whack. It will see the internal HDD as sda, the external SSD as sdb, and when you swap them over, probably chaos as sdb is now sda (that will happen automatically without you changing anything) and sda, the HDD, is now sdb. The machine will attempt to boot from sda (which is originally sdb) but your active grub is actually on what is now sdb, the external HDD. Follow me?

There is also always the possibility that while trying to install on the external SSD, there's a rush of blood and you end up doing something disasterous to the HDD. If the SSD is in the box, the HDD can be completely unplugged and removed from danger. :)

If you don't get this kind of mix up I described above, likely there will be something amiss. Might be easily fixable, might take days, so easier to have the hardware where you want it to end up, then proceed. 

If you are booted to a live session of Ubuntu, could you open Gparted and take a screenshot of the SSD (sdb, you'll find it in the drop-down list at top right of Gparted window) and post here. We'll be able to see if you have 16.04 installed in there. If that is the case, you may just be able to install the SSD to the computer, tweak the grub with Boot Repair and off you go.

---

### Post by watchpocket on 2016-05-17
> **Bucky Ball said:**
>  Some laptops will only want to boot from sda. Trying to get them to do otherwise can be time consuming and unsuccessful. 

With luck, this shouldn't be a worry, since I'm working only with my desktop unit. (I don't have a laptop.)

> **Bucky Ball said:**
> Also, if you manage to install 16.04 correctly on sdb (which you may already have) 

16.04 won't actually be on sdb (neither old nor new sdb). I should provide you with a look at my full configuration, which I don't think I've done yet:

[COLOR=#0000ff]***CURRENT:***[/COLOR]

I have three identical (same make & model), internal, one-terabyte HDDs (spinners):

***sda*** contains UbuntuMATE 14.04;
***sdb*** contains Ubuntu 12.04; 
***sdc*** is storage.

The solid-state drive right now is still an external drive, in an enclosure.


[COLOR=#0000ff]***FUTURE:***[/COLOR] (what I plan to do this weekend)

[COLOR=#ff0000]***sda***[/COLOR] will be the solid-state drive (it will now be internal) and it will contain UbuntuMATE ***16.04***;
[COLOR=#ff0000]***sdb***[/COLOR] will be an internal HDD, and it will contain UbuntuMATE ***14.04***  (This is what is ***sda*** right now. Current ***sda*** will become new [COLOR=#ff0000]***sdb***[/COLOR]);
[COLOR=#ff0000]***sdc***[/COLOR] will remain (internal) storage.

The HDD that currently contains Ubuntu 12.04 (current ***sdb***) will be put into an enclosure and will be an external storage drive.


> **Bucky Ball said:**
>  then the grub set up will be totally out of whack. 

Right -- I'm kind of anticipating that.

> **Bucky Ball said:**
>  There is also always the possibility that while trying to install on the external SSD, there's a rush of blood and you end up doing something disasterous to the HDD. If the SSD is in the box, the HDD can be completely unplugged and removed from danger. :)  

Yes, the old Ubuntu blood-rush. I know it well.

> **Bucky Ball said:**
>  If you are booted to a live session of Ubuntu, could you open Gparted and take a screenshot of the SSD (sdb, you'll find it in the drop-down list at top right of Gparted window) and post here. 

OK, the solid-state drive is actually still an external drive (so it's /dev/sdd in Gparted), but I took two screenshots: 

The one on the left is the folder that opens when I plug the solid-state drive into a USB port.

The one on the right is from Gparted -- again with the solid-state drive plugged in to a USB port. (You'll see that I haven't had a chance yet to do anything with changing the swap partition size -- it's still 10 GB, I may tweak that downward a bit.)

[ATTACH=CONFIG]269136[/ATTACH][ATTACH=CONFIG]269137[/ATTACH]

Thanks again!

---

### Post by watchpocket on 2016-05-19
> **Bucky Ball said:**
>  . . . take a screenshot of the SSD (sdb, you'll find it in the drop-down list at top right of Gparted window) and post here. We'll be able to see if you have 16.04 installed in there.

Just wondering if those shots in my previous post look like 16.04 was installed on the external SSD all right.  And is it normal to have that 35 MB "link to Raw image there?" Thanks.

---

### Post by Bucky Ball on 2016-05-19
It looks like it was installed, but can you boot to it? Do you even want to as you'll be swapping these over (or are they already swapped). I'm presuming you're taking these shots from the install on the other drive. 

I'd swap them over now and tackle the issue of the SSD spinning (which wouldn't have been the case had you swapped them over first) as anything else you do is going to be kinda redundant when sdd changes to sdb.

Who knows, you may plop the SSD in the machine and it boots up just like that! But I have my doubts.

---

### Post by watchpocket on 2016-05-22
> **Bucky Ball said:**
> It looks like it was installed, but can you boot to it? 

Short answer: Yes.  

UbuntuMATE-16.04 is now on my solid-state drive, and that solid-state drive is now internal -- it's secured into the inside-the-box drive bay at ***sdb*** (where previously the HDD containing Ubuntu-12.04 was). 

(That's for now.  Later I'll want to have the SSD/16.04 at ***sda***, after I get 16.04 set up a bit nicer)[B].
[/B]
I can indeed boot to 16.04 from my current grub menu (the one on ***sda*** where UbuntuMATE 14.04 -- which I'm logged into -- is), **but boot time into 16.04 is unusually long -- a minute & 42 seconds from when I select it in the grub menu.**

However, something interesting is that I now have the old 12.04 HDD pulled out of the computer (it** was *sdb***), and it's now in an external enclosure. When I boot to that external HDD, I get ***that*** system's (different) grub menu. When I choose "Ubuntu 12.04 (Precise Pangolin)*"* in that grub menu,[I] it boots me **not** into 12.04 but [COLOR=#000000]**into 16.04**[/COLOR][B], [COLOR=#0000ff]and, more importantly, [/COLOR][COLOR=#0000ff]with NO delay[/COLOR]. 

[/B][/I]I'd like to be able to boot that quickly to 16.04 from the grub menu on*** sda.***
> **Bucky Ball said:**
> Who knows, you may plop the SSD in the machine and it boots up just like that! 

That*'s *basically what happened, except that there's this long boot time.   I think I'll be fine if I can just straighten out the grub issues. 

Also, I edited my fstab, because on booting to 14.04, I was getting a warning that a drive was missing (12.04's swap UUID was listed).  I got rid of that warning by removing 12.04's swap UUID from fstab.  

But in editing fstab, **I've messed up fstab:** 

(The UUID for 16.04 is commented-out here (line number 13) because with it active, the SSD (16.04) doesn't appear in the 14.04 "Places" menu and is not accessible generally.)

```
  1 # /etc/fstab: static file system information.
  2 #
  3 # Use 'blkid' to print the universally unique identifier for a
  4 # device; this may be used with UUID= as a more robust way to name devices
  5 # that works even if disks are added and removed. See fstab(5).
  6 #
  7 #            <file system>           <mount point>    <type>     <options>     <dump>  <pass>
  8 # UbuntuMATE-14.04:
  9 UUID=1742aa67-b8ce-45d2-94ca-05e3579f7e2f   /          ext4    errors=remount-ro   0     1    # /dev/sda1
 10 UUID=a88c33fd-88b5-43b2-92f6-457430d206fd   none       swap    sw                  0     0    # /dev/sda2
 11 #
 12 # UbuntuMATE-16.04:
 13 [COLOR=#0000ff]# UUID=010dab65-d950-47dc-ac77-a3760775104d   /          ext4    errors=remount-ro   0     1    # /dev/sdb1[/COLOR]
 14 UUID=d6a2bc73-6ec4-4465-a9ab-8447e13ac6f9   none       swap    sw                  0     0    # /dev/sdb2
```

Here also is my */etc/default/grub *on 14.04:[I]
```
  1 # If you change this file, run 'sudo update-grub' afterwards to update /boot/grub/grub.cfg.
  2 # For full documentation of the options in this file, see:
  3 #   info -f grub -n 'Simple configuration'
  4 
  5 GRUB_DEFAULT=0
  6 GRUB_TIMEOUT=10
  7 #GRUB_HIDDEN_TIMEOUT=0
  8 GRUB_HIDDEN_TIMEOUT_QUIET=true
  9 GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
 10 GRUB_CMDLINE_LINUX_DEFAULT="nomodeset=1 #=1 quiet splash video=uvesafb:mode_option=1600x1200-32,mtrr=3,scroll=ywrap"
 11 GRUB_CMDLINE_LINUX=""
 12 GRUB_FONT=/boot/grub/DejaVuSansMono.pf2
 13 
 14 # The resolution used on graphical terminal:
 15 # Note that you can use only modes which your graphic card supports via VBE.
 16 # You can see them in real GRUB with the command `vbeinfo'.
 17 GRUB_GFXMODE=1600x1200-32
 18 
 19 # Uncomment to enable BadRAM filtering, modify to suit your needs.
 20 # This works with Linux (no patch required) and with any kernel that obtains
 21 # the memory-map information from GRUB (GNU Mach, kernel of FreeBSD ...)
 22 #GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"
 23 
 24 # Uncomment to disable graphical terminal (grub-pc only)
 25 #GRUB_TERMINAL=console
 26 
 27 # Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux:
 28 #GRUB_DISABLE_LINUX_UUID=true
 29 
 30 # Uncomment to disable generation of recovery mode menu entries:
 31 #GRUB_DISABLE_RECOVERY=true
 32 
 33 # Uncomment to get a beep at grub start:
 34 #GRUB_INIT_TUNE="480 440 1"
 35 GRUB_GFXPAYLOAD_LINUX=keep
```

[/I]And, FWIW, here is a Boot Info Summary link:

(In this boot info summary: 
***sda*** is 14.04; 
***sdb*** is 16.04 on the internal SSD; 
***sdc*** is the internal storage HDD; [I][B]
sdd[/B][/I] is the live-USB with the Boot-Repair Disk program on it; and [I][B]
sde[/B][/I] is the external HDD with 12.04 on it.)

[http://paste.ubuntu.com/16619259/](http://paste.ubuntu.com/16619259/)

Many thanks for reading.

---

### Post by watchpocket on 2016-05-23
My last post didn't actually ask a question.  The question would be how can I (a) set up grub to boot to sdb/16.04 quickly (as the 2nd choice in the grub menu) and (b) make sure my fstab is error-free. Thanks.

---

### Post by oldfred on 2016-05-23
I agree with Bucky that it probably would just be easier to install new SSD into system and install Ubuntu to it.
Grub likes to install to sda.
When plugging drives in, be sure to start at SATA0 which will be sda, and use all ports in order. I have had many issues when I skipped a port. Flash drive that was sdf would become sdb on reboot. Then using device to mount, I had to be careful which drive I was working with. 

Whenever editing fstab always run this before rebooting. It remounts everything per new fstab. If no errors, then ok. If errors you must fix before rebooting.
sudo mount -a

You can boot a partition, not an install and then you do not have to do double update-grub once in second install and once in main boot from sda or first install.
       How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)

I typically turn off os-prober and use my own 40_custom entries to boot.
And with multiple drives I had default install & boot on sdc or later sdd, so my test installs that wanted to default to sda, I would just let them install to sda, but normally did not use it. BIOS was set to boot from sdc.

A bit late now, but with only Linux, I prefer gpt partitioning. And if later a new system as I had planned that would be UEFI, I included both an ESP - efi system partition for future UEFI boot and a bios_grub partition for current BIOS boot. Then drive worked in older BIOS system, but could be moved to a new UEFI system without total re-formatting & partitioning.


       
 GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)

---

### Post by Bashing-om on 2016-05-23
watchpocket; Hey .. and hello again .

In a multi-boot system I am a firm believer in maintaining ONE install as the primary system and that is the way my mind works.
What system is your preference as the primary ?

> 
 (a) set up grub to boot to sdb/16.04 quickly 

Then we would want to see updated:
```

sudo blkid
sudo fdisk -lu
sudo parted -l
cat /etc/fstab
cat /boot/grub/grub.cfg

```
Setting that primary can be a thing of patience . Resetting grub in each install .. and turning os_proper off in all but that primary control system .

> 
and (b) make sure my fstab is error-free. Thanks.

remains to be seen from the above .. then we do as oldfred advised and run:
```

mount -a

```
having the system verify the file and is in a happy state.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by watchpocket on 2016-05-23
> **Bashing-om said:**
> What system is your preference as the primary ?
Currently the primary system is UbuntMATE-14.04 on an HDD drive at ***sda***.

But my preference *now* for the primary system will be UbuntuMATE-***16.04***, which is on a recently-installed solid-state drive, at ***sdb***.  (Maybe it'll be appropriate to then make that solid-state drive ***sda***. I'll see as I go along, I suppose.)

(Even though 16.04 has just been installed and is still very raw, this will be the primary system for future use, so I figure I should set it up to be the primary now.)
> **Bashing-om said:**
> Then we would want to see updated:
```

sudo blkid
sudo fdisk -lu
sudo parted -l
cat /etc/fstab
cat /boot/grub/grub.cfg

```

I'll report back with results of the above commands later tonight when I get home. 

I think the info for some of it --* blkid, **/boot/grub/grub.cfg* and */etc/fstab --* are above in post number 20 (*fstab* in the post itself, *blkid*, I think, and */boot/grub/grup.cfg* for sure, are in the Boot Info Summary linked to at the bottom of that post).

I'm ever grateful, please stay tuned, more to come in about 4 hours.  Thanks once again.

---

### Post by watchpocket on 2016-05-24
> **Bashing-om said:**
> Then we would want to see updated:
```

sudo blkid
sudo fdisk -lu
sudo parted -l
cat /etc/fstab
cat /boot/grub/grub.cfg

```
OK, here is the output of the above commands:
```
**--> [COLOR=#0000ff]*sudo blkid*[/COLOR]**
[sudo] password for rj: 
/dev/sda1: LABEL="UbuntuMATE-14.04" UUID="1742aa67-b8ce-45d2-94ca-05e3579f7e2f" TYPE="ext4" 
/dev/sda2: UUID="a88c33fd-88b5-43b2-92f6-457430d206fd" TYPE="swap" 
/dev/sdb1: LABEL="UbuntuMATE-16.04" UUID="010dab65-d950-47dc-ac77-a3760775104d" TYPE="ext4" 
/dev/sdb2: UUID="d6a2bc73-6ec4-4465-a9ab-8447e13ac6f9" TYPE="swap" 
/dev/sdc1: LABEL="WeirdBeard" UUID="c801726e-7a01-4963-989a-38482e6658cf" TYPE="ext4"

**--> [COLOR=#0000ff]*sudo fdisk -lu*[/COLOR]**
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x3aec6e77

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048  1932552191   966275072   83  Linux
/dev/sda2      1932552192  1953525167    10486488   82  Linux swap / Solaris

Disk /dev/sdb: 960.2 GB, 960197124096 bytes
255 heads, 63 sectors/track, 116737 cylinders, total 1875385008 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b53b4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048  1833400319   916699136   83  Linux
/dev/sdb2      1833400320  1854412799    10506240   82  Linux swap / Solaris

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x41031e20

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048  1953523711   976760832   83  Linux
```


```
**--> [COLOR=#0000ff]*sudo parted -l*[/COLOR]** 
Model: ATA ST31000528AS (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system     Flags
 1      1049kB  989GB   989GB   primary  ext4            boot
 2      989GB   1000GB  10.7GB  primary  linux-swap(v1)


Model: ATA SanDisk SDSSDHII (scsi)
Disk /dev/sdb: 960GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type     File system     Flags
 1      1049kB  939GB  939GB   primary  ext4            boot
 2      939GB   949GB  10.8GB  primary  linux-swap(v1)


Model: ATA ST31000528AS (scsi)
Disk /dev/sdc: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  1000GB  1000GB  primary  ext4 
```

 ```
**--> [COLOR=#0000ff]*cat /etc/fstab*[/COLOR]**
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
#            <file system>           <mount point>    <type>     <options>     <dump>  <pass>
# UbuntuMATE-14.04:
UUID=1742aa67-b8ce-45d2-94ca-05e3579f7e2f   /          ext4    errors=remount-ro   0     1    # /dev/sda1
UUID=a88c33fd-88b5-43b2-92f6-457430d206fd   none       swap    sw                  0     0    # /dev/sda2
# 
# UbuntuMATE-16.04:
[COLOR=#800000]# UUID=010dab65-d950-47dc-ac77-a3760775104d   /          ext4    errors=remount-ro   0     1    # /dev/sdb1[/COLOR]
UUID=d6a2bc73-6ec4-4465-a9ab-8447e13ac6f9   none       swap    sw                  0     0    # /dev/sdb2 
```

As mentioned in my post number 20 above, the UUID for 16.04 is commented-out in */etc/fstab* (at line number 13, highlighted in [COLOR=#800000]brown[/COLOR]) because with  it active, the SSD (16.04) doesn't appear in the 14.04 "Places" menu and  is not accessible generally. (Probably because I didn't know to run *sudo mount -a* and re-boot after editing *fstab.)*

```
**--> [COLOR=#0000ff]*cat /boot/grub/grub.cfg*[/COLOR]**
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
if [ "${next_entry}" ] ; then
   set default="${next_entry}"
   set next_entry=
   save_env next_entry
   set boot_once=true
else
   set default="0"
fi

if [ x"${feature_menuentry_id}" = xy ]; then
  menuentry_id_option="--id"
else
  menuentry_id_option=""
fi

export menuentry_id_option

if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}
function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}
function load_video {
  if [ x$feature_all_video_module = xy ]; then
    insmod all_video
  else
    insmod efi_gop
    insmod efi_uga
    insmod ieee1275_fb
    insmod vbe
    insmod vga
    insmod video_bochs
    insmod video_cirrus
  fi
}

insmod part_msdos
insmod ext2
set root='hd0,msdos1'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  1742aa67-b8ce-45d2-94ca-05e3579f7e2f
else
  search --no-floppy --fs-uuid --set=root 1742aa67-b8ce-45d2-94ca-05e3579f7e2f
fi
if loadfont /boot/grub/DejaVuSansMono.pf2 ; then
  set gfxmode=1600x1200-32
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ] ; then
  set timeout=30
else
  if [ x$feature_timeout_style = xy ] ; then
    set timeout_style=menu
    set timeout=10
  # Fallback normal timeout code in case the timeout_style feature is
  # unavailable.
  else
    set timeout=10
  fi
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod part_msdos
insmod ext2
set root='hd0,msdos1'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  1742aa67-b8ce-45d2-94ca-05e3579f7e2f
else
  search --no-floppy --fs-uuid --set=root 1742aa67-b8ce-45d2-94ca-05e3579f7e2f
fi
insmod jpeg
if background_image /boot/grub/darkwood-1920x1200-wallpaper.jpg; then
 set color_normal=light-blue/black
 set menu_color_normal=light-gray/black
 set menu_color_highlight=white/light-blue
  true
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
  if background_color 60,59,55; then
    clear
  fi
  
  color_normal=light-gray/black
   
  if [ -e ${prefix}/themes/ubuntu-mate/theme.txt ]; then
    insmod png
    theme=${prefix}/themes/ubuntu-mate/theme.txt
  fi
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/06_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Ubuntu-MATE 14.04 (Trusty Tahr)" {
    set root=(hd0,1)
        linux /vmlinuz root=/dev/sda1 ro quiet splash
        initrd /initrd.img
}
menuentry "Ubuntu-MATE 14.04 (Trusty Tahr) (Recovery Mode)" {
    set root=(hd0,1)
        linux /vmlinuz root=/dev/sda1 ro recovery nomodeset
        initrd /initrd.img
}
menuentry "Ubuntu 12.04 (Precise Pangolin)" {
    set root=(hd1,1)
        linux /vmlinuz root=/dev/sdb1 ro quiet splash
        initrd /initrd.img
}
menuentry "Ubuntu 12.04 (Precise Pangolin) (Recovery Mode)" {
    set root=(hd1,1)
        linux /vmlinuz root=/dev/sdb1 ro single
        initrd /initrd.img
}
### END /etc/grub.d/06_custom ###

### BEGIN /etc/grub.d/10_linux ###
function gfxmode {
    set gfxpayload="${1}"
    if [ "${1}" = "keep" ]; then
        set vt_handoff=vt.handoff=7
    else
        set vt_handoff=
    fi
}
set linux_gfx_mode=keep
export linux_gfx_mode
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-1742aa67-b8ce-45d2-94ca-05e3579f7e2f' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  1742aa67-b8ce-45d2-94ca-05e3579f7e2f
    else
      search --no-floppy --fs-uuid --set=root 1742aa67-b8ce-45d2-94ca-05e3579f7e2f
    fi
    linux    /boot/vmlinuz-3.13.0-86-generic root=UUID=1742aa67-b8ce-45d2-94ca-05e3579f7e2f ro  nomodeset=1 #=1 quiet splash video=uvesafb:mode_option=1600x1200-32,mtrr=3,scroll=ywrap $vt_handoff
    initrd    /boot/initrd.img-3.13.0-86-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-1742aa67-b8ce-45d2-94ca-05e3579f7e2f' {
    menuentry 'Ubuntu, with Linux 3.13.0-86-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-86-generic-advanced-1742aa67-b8ce-45d2-94ca-05e3579f7e2f' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  1742aa67-b8ce-45d2-94ca-05e3579f7e2f
        else
          search --no-floppy --fs-uuid --set=root 1742aa67-b8ce-45d2-94ca-05e3579f7e2f
        fi
        echo    'Loading Linux 3.13.0-86-generic ...'
        linux    /boot/vmlinuz-3.13.0-86-generic root=UUID=1742aa67-b8ce-45d2-94ca-05e3579f7e2f ro  nomodeset=1 #=1 quiet splash video=uvesafb:mode_option=1600x1200-32,mtrr=3,scroll=ywrap $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-86-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-86-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-86-generic-recovery-1742aa67-b8ce-45d2-94ca-05e3579f7e2f' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  1742aa67-b8ce-45d2-94ca-05e3579f7e2f
        else
          search --no-floppy --fs-uuid --set=root 1742aa67-b8ce-45d2-94ca-05e3579f7e2f
        fi
        echo    'Loading Linux 3.13.0-86-generic ...'
        linux    /boot/vmlinuz-3.13.0-86-generic root=UUID=1742aa67-b8ce-45d2-94ca-05e3579f7e2f ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-86-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-85-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-85-generic-advanced-1742aa67-b8ce-45d2-94ca-05e3579f7e2f' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  1742aa67-b8ce-45d2-94ca-05e3579f7e2f
        else
          search --no-floppy --fs-uuid --set=root 1742aa67-b8ce-45d2-94ca-05e3579f7e2f
        fi
        echo    'Loading Linux 3.13.0-85-generic ...'
        linux    /boot/vmlinuz-3.13.0-85-generic root=UUID=1742aa67-b8ce-45d2-94ca-05e3579f7e2f ro  nomodeset=1 #=1 quiet splash video=uvesafb:mode_option=1600x1200-32,mtrr=3,scroll=ywrap $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-85-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-85-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-85-generic-recovery-1742aa67-b8ce-45d2-94ca-05e3579f7e2f' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  1742aa67-b8ce-45d2-94ca-05e3579f7e2f
        else
          search --no-floppy --fs-uuid --set=root 1742aa67-b8ce-45d2-94ca-05e3579f7e2f
        fi
        echo    'Loading Linux 3.13.0-85-generic ...'
        linux    /boot/vmlinuz-3.13.0-85-generic root=UUID=1742aa67-b8ce-45d2-94ca-05e3579f7e2f ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-85-generic
    }
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Ubuntu 16.04 LTS (16.04) (on /dev/sdb1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-010dab65-d950-47dc-ac77-a3760775104d' {
    insmod part_msdos
    insmod ext2
    set root='hd1,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  010dab65-d950-47dc-ac77-a3760775104d
    else
      search --no-floppy --fs-uuid --set=root 010dab65-d950-47dc-ac77-a3760775104d
    fi
    linux /boot/vmlinuz-4.4.0-22-generic root=UUID=010dab65-d950-47dc-ac77-a3760775104d ro quiet splash $vt_handoff
    initrd /boot/initrd.img-4.4.0-22-generic
}
submenu 'Advanced options for Ubuntu 16.04 LTS (16.04) (on /dev/sdb1)' $menuentry_id_option 'osprober-gnulinux-advanced-010dab65-d950-47dc-ac77-a3760775104d' {
    menuentry 'Ubuntu (on /dev/sdb1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-4.4.0-22-generic--010dab65-d950-47dc-ac77-a3760775104d' {
        insmod part_msdos
        insmod ext2
        set root='hd1,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  010dab65-d950-47dc-ac77-a3760775104d
        else
          search --no-floppy --fs-uuid --set=root 010dab65-d950-47dc-ac77-a3760775104d
        fi
        linux /boot/vmlinuz-4.4.0-22-generic root=UUID=010dab65-d950-47dc-ac77-a3760775104d ro quiet splash $vt_handoff
        initrd /boot/initrd.img-4.4.0-22-generic
    }
    menuentry 'Ubuntu, with Linux 4.4.0-22-generic (on /dev/sdb1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-4.4.0-22-generic--010dab65-d950-47dc-ac77-a3760775104d' {
        insmod part_msdos
        insmod ext2
        set root='hd1,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  010dab65-d950-47dc-ac77-a3760775104d
        else
          search --no-floppy --fs-uuid --set=root 010dab65-d950-47dc-ac77-a3760775104d
        fi
        linux /boot/vmlinuz-4.4.0-22-generic root=UUID=010dab65-d950-47dc-ac77-a3760775104d ro quiet splash $vt_handoff
        initrd /boot/initrd.img-4.4.0-22-generic
    }
    menuentry 'Ubuntu, with Linux 4.4.0-22-generic (recovery mode) (on /dev/sdb1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-4.4.0-22-generic-root=UUID=010dab65-d950-47dc-ac77-a3760775104d ro recovery nomodeset-010dab65-d950-47dc-ac77-a3760775104d' {
        insmod part_msdos
        insmod ext2
        set root='hd1,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  010dab65-d950-47dc-ac77-a3760775104d
        else
          search --no-floppy --fs-uuid --set=root 010dab65-d950-47dc-ac77-a3760775104d
        fi
        linux /boot/vmlinuz-4.4.0-22-generic root=UUID=010dab65-d950-47dc-ac77-a3760775104d ro recovery nomodeset
        initrd /boot/initrd.img-4.4.0-22-generic
    }
    menuentry 'Ubuntu, with Linux 4.4.0-21-generic (on /dev/sdb1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-4.4.0-21-generic--010dab65-d950-47dc-ac77-a3760775104d' {
        insmod part_msdos
        insmod ext2
        set root='hd1,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  010dab65-d950-47dc-ac77-a3760775104d
        else
          search --no-floppy --fs-uuid --set=root 010dab65-d950-47dc-ac77-a3760775104d
        fi
        linux /boot/vmlinuz-4.4.0-21-generic root=UUID=010dab65-d950-47dc-ac77-a3760775104d ro quiet splash $vt_handoff
        initrd /boot/initrd.img-4.4.0-21-generic
    }
    menuentry 'Ubuntu, with Linux 4.4.0-21-generic (recovery mode) (on /dev/sdb1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-4.4.0-21-generic-root=UUID=010dab65-d950-47dc-ac77-a3760775104d ro recovery nomodeset-010dab65-d950-47dc-ac77-a3760775104d' {
        insmod part_msdos
        insmod ext2
        set root='hd1,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  010dab65-d950-47dc-ac77-a3760775104d
        else
          search --no-floppy --fs-uuid --set=root 010dab65-d950-47dc-ac77-a3760775104d
        fi
        linux /boot/vmlinuz-4.4.0-21-generic root=UUID=010dab65-d950-47dc-ac77-a3760775104d ro recovery nomodeset
        initrd /boot/initrd.img-4.4.0-21-generic
    }
}

set timeout_style=menu
if [ "${timeout}" = 0 ]; then
  set timeout=10
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/30_uefi-firmware ###
### END /etc/grub.d/30_uefi-firmware ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Ubuntu 12.04 (Precise Pangolin)" {
    set root=(hd1,1)
        linux /vmlinuz root=/dev/sdb1 ro quiet splash
        initrd /initrd.img
}
menuentry "Ubuntu 12.04 (Precise Pangolin) (Recovery Mode)" {
    set root=(hd1,1)
        linux /vmlinuz root=/dev/sdb1 ro single
        initrd /initrd.img
}
menuentry "Ubuntu-MATE 14.04 (Trusty Tahr)" {
    set root=(hd0,1)
        linux /vmlinuz root=/dev/sda1 ro quiet splash
        initrd /initrd.img
}
menuentry "Ubuntu-MATE 14.04 (Trusty Tahr) (Recovery Mode)" {
    set root=(hd0,1)
        linux /vmlinuz root=/dev/sda1 ro recovery nomodeset
        initrd /initrd.img
}
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  ${config_directory}/custom.cfg ]; then
  source ${config_directory}/custom.cfg
elif [ -z "${config_directory}" -a -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

``` Thanks, as always, for taking a look.

---

### Post by oldfred on 2016-05-24
I would just boot into your Ubuntu Mate and install grub to the MBR of the same drive if sdb:
       #reinstall from working (not liveCD/DVD/USB) system - first find Ubuntu drive (example is drive sdb but use your drive not partitions):
sudo parted -l
#if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
#If that returns any errors run:
sudo grub-install --recheck /dev/sdb
sudo update-grub 
    
Then set BIOS to boot from sdb or whichever drive that install is.

I prefer to have an install on every drive and its boot loader in the MBR of that drive.

But grub remembers which drive it installed into originally and on a major update may reinstall to that MBR. So second installs may overwrite your preferred version of grub.
Best to check and change if required.
       #To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc # for BIOS with grub-pc 
It will show drive model & serial number
to see similar drive info
sudo lshw -C Disk -short  
    sudo grub-probe -t device /boot/grub 
   #to get grub2 to remember where to reinstall on major updates
sudo dpkg-reconfigure grub-pc 
#Enter thru first pages,tab to ok, spacebar to choose/unchoose drive, enter to accept, do not choose partitions
[http://ubuntuforums.org/showthread.php?t=2189643](http://ubuntuforums.org/showthread.php?t=2189643)
Not even sure this works for UEFI
dpkg-reconfigure grub-efi-amd64

---

### Post by Bucky Ball on 2016-05-24
Today I did this on my own machine. 

To begin I had:
sda = internal HDD
sdb = internal SSD (in an optical drive bay dock where the DVD used to be)

I then:
Pulled out sda and sdb, put sdb in place of sda. So now I have the SSD in the internal hard drive bay in the laptop, not the optical drive bay. 

Boot the machine. Problem. Boot from a Boot Repair USB, install grub to sda (Advanced Options> Grub Location). Reboot the machine. Good to go. The SSD, which was sdb, is now sda. Exactly what you are after. 

Install HDD, previously sda, into optical drive bay. Boot machine, check Gparted, HDD is now sdb. So I now have:

sda = SSD
sdb = HDD

14.04 LTS on the SSD is now first on the list. Previously I had to jump through hoops to get there (boot the machine> hit F12 to get to boot device list> choose FDD(!)> choose correct sdb entry from that grub).

---

### Post by Bashing-om on 2016-05-24
watchpocket; Hey;

You have the greatest of advise there is .. there is little I can add.
For your reference and consideration; My system:
```

sysop@1404mini:~$ sudo fdisk -lu
[sudo] password for sysop: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00065f5e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    10242047     5120000   83  Linux
/dev/sda2        10244096    30724095    10240000   83  Linux
/dev/sda3        34207742   976771071   471281665    5  Extended
/dev/sda5       443795688   443811689        8001   82  Linux swap / Solaris
/dev/sda6       443811753   597409154    76798701   83  Linux
/dev/sda7       597409792   976771071   189680640   83  Linux
/dev/sda8        34207744    44447743     5120000   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002ea65

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048   102402438    51200195+  83  Linux
/dev/sdb2   *   102404096   204804095    51200000   83  Linux
/dev/sdb3       204806144   266246143    30720000   83  Linux

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x502a9772

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63   976768064   488384001   83  Linux
sysop@1404mini:~$ 

sysop@1404mini:~$ sudo blkid
/dev/sda1: LABEL="1404mroot" UUID="3a47f1f1-ed1f-4134-b6aa-be101a7d97b4" TYPE="ext4" 
/dev/sda2: LABEL="1404mhome" UUID="29a6fc4f-ff12-4cac-8eb1-e98e50f1107f" TYPE="ext4" 
/dev/sda5: UUID="192a4783-56fa-4fd0-a62f-c45a14c08482" TYPE="swap" 
/dev/sda6: LABEL="DATA" UUID="3ad091a1-5036-463b-ba4e-88e98e41b07a" TYPE="ext4" 
/dev/sda7: LABEL="LUBU1404" UUID="4e6cd96d-49bd-47f0-9dfe-8eeebad4cf9d" TYPE="ext4" 
/dev/sda8: LABEL="1404mvar" UUID="136af805-5758-4880-acc4-0e1d35e2c266" TYPE="ext4" 
/dev/sdb1: LABEL="ubie14.04std" UUID="345cab2e-22e7-4f89-8781-05cc0f7628a2" TYPE="ext4" 
/dev/sdb2: LABEL="ubie1204" UUID="7dd23297-30ea-417a-8f69-3e2df76f3192" TYPE="ext4" 
/dev/sdb3: LABEL="ubie15.10" UUID="2ec4733f-db40-4db0-aef8-5c54e54085ab" TYPE="ext4" 
/dev/sdc1: LABEL="my_stuff" UUID="6a24777c-8191-4230-81f1-376f31b321e5" TYPE="ext4" 
sysop@1404mini:~$

```

Now, controlling and keeping track of the bootloader can be a pain .. I do highly recommend Cavsfan's solution :
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
If you do not want the aggravation of maintaining grubs .

[INDENT][INDENT]nothing to it but
[INDENT][INDENT][INDENT]lay your ears back and do it
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by oldfred on 2016-05-24
+1 on Cavsfan's link for Maintenance Free grub booting.

I also learned about the same time from Ranch Hand, but Cavsfan documented it and maintains the documentation.

---

### Post by watchpocket on 2016-05-24
Wow thanks for the input everybody.  I'll read through all this slowly and soberly over the next day or so (along with the Cavsfan & other links) before I make a move.

One quick question:  I can achieve the same kind of swapping that Bucky Ball did, can I not, simply by unplugging the SATA cable from the back of the ***sda*** drive and plugging it into the ***sdb*** drive, and vice-versa, right?  

I'll still have to use Boot Repair to move GRUB, but I'm guessing that just switching the SATA cables will make ***sdb*** become*** sda*** and vice-versa.

Thanks again.

---

### Post by Bashing-om on 2016-05-24
watchpocket; Uh Huh.

> **watchpocket said:**
> Wow thanks for the input everybody.  I'll read through all this slowly and soberly over the next day or so (along with the Cavsfan & other links) before I make a move.

One quick question:  I can achieve the same kind of swapping that Bucky Ball did, can I not, simply by unplugging the SATA cable from the back of the ***sda*** drive and plugging it into the ***sdb*** drive, and vice-versa, right?  

I'll still have to use Boot Repair to move GRUB, but I'm guessing that just switching the SATA cables will make ***sdb*** become*** sda*** and vice-versa.

Thanks again.

Yep .. if you are using UUIDs universally .. I would not expect a problem.
As oldfred advised, best not to skip about sata ports .
I like:
sata port 1 for sda primary booting system
sata port 2 as sdb
sata port 3 as sdc
sata port 4 as sdd
Just for the mind set control .

[INDENT][INDENT]KISS always applies
[INDENT][INDENT][INDENT]then there is Murphy's Law
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by watchpocket on 2016-05-24
How can I tell which SATA port is which?  I see the SATA plugs on my motherboard that I have the drives plugged into, but I can't tell from looking at those which is which.

---

### Post by Bashing-om on 2016-05-24
watchpocket; Humm ...

They - the sata ports - "should" be labeled .
My old Abit board .. as one looks at the sata controller ..
port 1 lower right ( 2 rows on the controller)
port 4 lower left
port 8 upper left.

Then one can generally find the spec sheet for the mainboard on the net .

[INDENT][INDENT]hope this helps [/INDENT][/INDENT]

---

### Post by LostFarmer on 2016-05-24
On your post #25:
    >  As mentioned in my post number 20 above, the UUID for 16.04 is commented-out in */etc/fstab* (at line number 13, highlighted in [COLOR=#800000]brown[/COLOR])  because with  it active, the SSD (16.04) doesn't appear in the 14.04  "Places" menu and  is not accessible generally. (Probably because I  didn't know to run *sudo mount -a* and re-boot after editing *fstab.)*


     
> # /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
#            <file system>           <mount point>    <type>     <options>     <dump>  <pass>
# UbuntuMATE-14.04:
UUID=1742aa67-b8ce-45d2-94ca-05e3579f7e2f   /          ext4    errors=remount-ro   0     1    # /dev/sda1
UUID=a88c33fd-88b5-43b2-92f6-457430d206fd   none       swap    sw                  0     0    # /dev/sda2
# 
# UbuntuMATE-16.04:
[COLOR=#800000]# UUID=010dab65-d950-47dc-ac77-a3760775104d   /          ext4    errors=remount-ro   0     1    # /dev/sdb1[/COLOR]
UUID=d6a2bc73-6ec4-4465-a9ab-8447e13ac6f9   none       swap    sw                  0     0    # /dev/sdb2 


You can NOT have the same mount point for 2 different partitions and never at '  /  '.

---

### Post by Bucky Ball on 2016-05-24
You don't need to know what the SATA sockets on the board are labeled. If one is showing you sda and one sdb, that is telling you what they are. If you have one as sda and one as sdb, swap the cables over.

I should have suggested this before but forgot you were on a desktop and not a laptop. The drive that is showing up now as sda should become sdb when you swap the two cables around. Give it a shot.

---

### Post by watchpocket on 2016-05-25
Lostfarmer wrote:
> [I]You can NOT have the same mount point for 2 different partitions and never at '  /  '.

[/I]Even if those partitions are on different drives?

---

### Post by watchpocket on 2016-05-25
> **Bucky Ball said:**
> You don't need to know what the SATA sockets on the board are labeled. If one is showing you sda and one sdb, that is telling you what they are. 

I kinda figured that was really all I'd need to know (after asking the question of course).

> **Bucky Ball said:**
> If you have one as sda and one as sdb, swap the cables over. [...] Give it a shot.

Will do, thanks!

---

### Post by LostFarmer on 2016-05-25
> Even if those partitions are on different drives?                   I am very poor at explaining so will give part of my 'fstab': 


```
/dev/disk/by-uuid/EEE20F43E20F100F   /mnt/Storage  auto nosuid,nodev,nofail,x-gvfs-show 0 0
/dev/disk/by-uuid/66FEA5AE3AC6800A    /mnt/Sermon  auto nosuid,nodev,nofail,x-gvfs-show,x-gvfs-name=Sermon 0 0
``` I have that in each of my 'fstab' Linux  install , that is fine.

```
/dev/disk/by-uuid/[COLOR=#b22222]EEE20F43E20F100F[/COLOR]    [COLOR=#0000cd]/mnt/Storage[/COLOR] auto nosuid,nodev,nofail,x-gvfs-show 0 0
/dev/disk/by-uuid/[COLOR=#b22222]66FEA5AE3AC6800A [/COLOR]   [COLOR=#0000cd]/mnt/Storage[/COLOR] auto nosuid,nodev,nofail,x-gvfs-show 0 0
```  This would not be permitted.  Have 2 different partitions (by uuid) mounted at /mnt/Storage at the same time..

 
I notice you have 2 active swaps, sda2 and sdb2,  that is permitted.  swap partitions are handled differently.

---

### Post by watchpocket on 2016-05-25
> **LostFarmer said:**
> I notice you have 2 active swaps, sda2 and sdb2,  that is permitted.  swap partitions are handled differently.

So my *fstab* above is OK then, yes?  (OK if I un-comment the brown-highlighted line, I mean.) 

As long as that mount point of root is on totally separate hard drives?

---

### Post by Bashing-om on 2016-05-25
watchpocket; Nope;

As LostFarmer has pointed out .. you can not mount 2 devices to the same mount point; " /mnt/Storage >> EEE20F43E20F100F , 66FEA5AE3AC6800A .

Only one will be recognized.

[INDENT][INDENT]keep all the ducks in a row
[/INDENT][/INDENT]

---

### Post by watchpocket on 2016-05-25
Got it. Major props to both of you for clueing me in.

---

### Post by Bucky Ball on 2016-05-26
Just coming back to this and a note. If you are booting into one OS, why would you want to mount another partition with another OS on at boot? Why exactly do you want an entry for the other OS in the fstab?

For instance, an example. sda1 has an OS. sda5 has an OS. If you boot to the install on sda1 and you want to access files on the install on sda5, simply click on the entry for sda5 in the side pane of the file manager and the partition should mount 'automagically'. Same with any other partitions on the same or other drives which aren't included in the fstab.

So, which partitions do you actually want to mount at boot??? I have /, /Data and /swap in my fstab. That is it. No reason to have a bunch of partitions mounting at boot which I may or not use (and the / partition from another OS is not what I would normally be accessing when booted in to any other install as all my personal data is on /Data, a partition on another drive accessible by all installs). 

The only reason I have /Data in the fstab is because I have symlinks in my /home directory inside / which point to directories in /Data. Otherwise I could just click /Data in the side pane of the file manager and it would mount.

Just throwing that in.

---

### Post by oldfred on 2016-05-26
I do the same as Bucky.

I label my other partitions, so I know which is which. I have installs, backup, ISO partitions for grub loopmounting and some others that I only want to mount on occasion. But use fstab for my /mnt/data partition.

```
fred@Z170N:~$ ls -l /dev/disk/by-label
total 0
lrwxrwxrwx 1 root root 10 May 24 12:52 backup_b -> ../../sdb4
lrwxrwxrwx 1 root root 10 May 24 12:52 data -> ../../sdb6
lrwxrwxrwx 1 root root 10 May 24 12:52 data64 -> ../../sdc3
lrwxrwxrwx 1 root root 10 May 24 12:52 efi64 -> ../../sdc1
lrwxrwxrwx 1 root root 10 May 24 12:52 ESP -> ../../sda1
lrwxrwxrwx 1 root root 10 May 24 12:52 ESP_B -> ../../sdb1
lrwxrwxrwx 1 root root 10 May 24 12:52 ISO -> ../../sda3
lrwxrwxrwx 1 root root 10 May 24 12:52 ISO_b -> ../../sdb3
lrwxrwxrwx 1 root root 10 May 24 12:52 root_b -> ../../sdb2
lrwxrwxrwx 1 root root 10 May 24 12:52 yakkety -> ../../sdc2
```

---

### Post by watchpocket on 2016-05-26
> **Bucky Ball said:**
> If you are booting into one OS, why would you want to mount another partition with another OS on at boot? Why exactly do you want an entry for the other OS in the fstab?

Your question assumes I even had any real idea of what I was doing when I made the fstab entry that I later commented-out.  I put it there almost as a kind of placeholder to be reviewed later, knowing that I didn't know what I was doing. I just made it look like the one above it. 

 Winging it -- making entries when I don't know they're correct, or that I don't understand -- is (obviously) never a good idea.

But both your and oldfred's examples will be a big help when I get back to this in a day or two.

---

### Post by watchpocket on 2016-06-16
Getting back to this, I fixed and simplified my two fstab files (the first on an HDD, the 2nd on an SSD):

```
  1 # /etc/fstab: static file system information.
  2 #
  3 # Use 'blkid' to print the universally unique identifier for a
  4 # device; this may be used with UUID= as a more robust way to name devices
  5 # that works even if disks are added and removed. See fstab(5).
  6 #
  7 #   UbuntuMATE-14.04:
  8 #             <file system>           <mount point>   <type>      <options>     <dump>  <pass>
  9 UUID=1742aa67-b8ce-45d2-94ca-05e3579f7e2f   /          ext4    errors=remount-ro   0     1    # /dev/sda1
 10 UUID=a88c33fd-88b5-43b2-92f6-457430d206fd   none       swap    sw                  0     0    # /dev/sda2
```

```
  1 # /etc/fstab: static file system information.
  2 #
  3 # Use 'blkid' to print the universally unique identifier for a
  4 # device; this may be used with UUID= as a more robust way to name devices
  5 # that works even if disks are added and removed. See fstab(5).
  6 #
  7 #   Ubuntu-MATE-16.04:
  8 #             <file system>              <mount point>   <type>  <options>                <dump>  <pass>
  9 UUID=010dab65-d950-47dc-ac77-a3760775104d /               ext4   noatime,errors=remount-ro  0        1    # /dev/sdb1
 10 UUID=d6a2bc73-6ec4-4465-a9ab-8447e13ac6f9 none            swap    sw                        0        0    # /dev/sdb2
```

For the SSD, I put into place some of the SSD-optimization advice [given here]("https://sites.google.com/site/easylinuxtipsproject/ssd").  Specifically, I added "noatime" to fstab; added the line "fstrim /" to rc.local; disabled the weekly cron job with this command: ```
[COLOR=#0000FF]sudo mv -v /etc/cron.weekly/fstrim /fstrim[/COLOR]
``` (transferring the script file fstrim to the root directory, thus disabling it); and, in /etc/sysctl.conf, reduced *vm.swappiness* to 10 and *vm.vfs_cache_pressure* to 50.

I decided to let my HDD continue to be the sda drive, since 14.04 is on the HDD and since 14.04 will continue to be my main working OS for quite awhile, until I get 16.04 set up and customized.  So GRUB is booting directly into 14.04. Once I start to use 16.04 more than 14.04, I'll just change the *GRUB_DEFAULT* setting in */etc/default/grub* from "0" to "3" (which is the position-location in my custom GRUB menu for 16.04 on the SSD).  So things are working well, thread marked "solved."

---

### Post by Bashing-om on 2016-06-16
watchpocket; Good Job !

Pleased ya got it all sorted out .. and provided your "procedure" .

sounds like a plan to me .

[INDENT][INDENT]just keep on keep'n on
[/INDENT][/INDENT]

---

