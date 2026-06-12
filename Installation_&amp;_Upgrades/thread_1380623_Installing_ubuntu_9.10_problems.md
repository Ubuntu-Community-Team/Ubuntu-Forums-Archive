---
title: "Installing ubuntu 9.10 problems"
date: 2010-01-13
forum: Installation &amp; Upgrades
---

### Post by RaymondS on 2010-01-13
I have searched for (and found) similar threads on this but I am still having troubles.......

I have installed ubuntu on a _brand_new_ hard-drive and I am running into troubles!!!

This should be a complete shoe-in... but alas, it is not working that way.


After a "successful" installation, I am receiving an error:

error: no such device: <a very nasty string>

  Failed to boot default entries


I have booted off the CD rom (install ISO) and made sure that the harddrive was bootable via the ubuntu disk util

I even modified the boot script - from directions from two other similar threads... but I am still running into troubles.

When I boot and am presented with the selection screen and press 'e' and remove the line:

search --no floppy --fs-uuid.......

then all boots up fine!!!

I also modified my grub-mkconfig-lib as per instructions on another post too...  and still no luck!!!

Help!

We are really trying here but slowly my son is turning back to the "dark side" (otherwise known as  Windoze) and I am trying to save him! <grin>

Many thanks for any help!
-Raymond

---

### Post by Varingo on 2010-01-14
Wow, same for me (ubuntuserver 9.10), I got initially got the [B]grub rescue> messages when I installed using LVM.  Re-installed without LVM got rid of that - and just the problem detailed here.
Deleted the line as per OP, and much to my delight boot!
System uses a VIA chipset, if that is at all relevant.  (Has been an issue for me with NVIDIA vdpau in mythbuntu)  Also there is no floppy drive, if that is at all relevant.
OK, do a quick sudo apt-get update  and sudo apt-get upgrade
Optomistically....Reboot....Same problem again.....
Hmmm.
Press e while Grub loading for the grub editor....yep that lines back there...ok Delete.  Boots again.
Get an error message that ACPI: I/O resource via686a conflicts with ACPI region.  Hmmm.
I might try commenting out the same line that is in grub.cfg (2 times - lines 52 and 61)  
Booting is slow....but yep that overcame the initial error message issue - so at least now I can do an auto reboot however seems this hack can probably be improved on!
Addendum:  having read some more about this it may also be relevant this is using a 320G HDD however the BIOS only reports ~ [/B]139G[B]b which may be why a file is not found?
[/B]

---

### Post by RaymondS on 2010-01-14
Thanks Varingo,

At least I don't feel alone... but this is not exactly fun either  :-)

I will keep editing the script for now...

It appears like some others are having this trouble as well but their solutions have not worked for me so far...

Thanks,
-Raymond

---

### Post by Varingo on 2010-01-15
Weird, I just tried adding another ubuntu box onto the same shared ATEN KVM Switch CS-84A and got a similar grub login failure using mythbuntu 9.10.  Changing it back to the original ATEN Petite KVM it will start again....so check if a KVM is part of the problem?

---

### Post by Leppie on 2010-01-15
could you boot with the livecd and [download and run meierfra's script]("http://sourceforge.net/projects/bootinfoscript/") and post the generated RESULTS.txt?

---

### Post by joplass on 2010-01-15
Same type of issues here.  I have tried to install 9.10 on two different machines both installation failed.  I am now downloading a new CD to see what the trouble is but I have the feeling that the CD is not my problem.

---

### Post by Varingo on 2010-01-15
I hope this helps, as attached.

---

### Post by Leppie on 2010-01-15
are you using a customized kernel?
vmlinuz-2.6.31-14-generic-pae isn't a generic kernel

---

### Post by U_Academical on 2010-01-15
To state the obvious try burning the CD at a low speed, my own experiance of the Karmic Koala update was anything but Karmic.

I am using Cornominals (#!) Crunchbang distribution of Ubuntu with the OpenBox desktop manager and someone told me to update would be as simple as installing the Update Manager and clicking check for update, which I did & then all hell broke loose!

For some reason, it installs Xsplash instead of Usplash, so say goodbye to X booting you to the lovely skinned GDM Theme you have set-up as your desktop greeting, then after you fight with it for about 2 hours you'll finally figure out you can get a shell by pressing ALT+CTRL and one of the F-Keys to bring you to a terminal login, then you have the resounding pleasure of having to replace, XFCE, LXDE or OpenBox with a full install of Gnome at which point you'll find much as I did that at last you get a Graphical log-on but the splash theme wont be your nice custom one anymore!

Worse the GDM Theme utility is gone as this was supposedly a speed increase according to the Ubuntu /devs and you now have Grub 2 which I found was a little slower than Grub 1.5

After you try to fix X you may find yourself borking the system to death much as I myself did (and that was after fixing gnome!), I feel I must point out as I am not a support Guru that when things start to go wrong, they can go very wrong very quickly.

In the end a complete re-install only to have to reinstall all the Applications and custom packages that you may have spent weeks downloading and building and tweaking by hand.

Oh what fun!:popcorn:

If you have a working system, set-up & lovingly tweeked the way you want it, then avoid upgrading just for upgradings sake as it is far from Karmic and you'll be wondering what god of the ancient tao you've managed to upset so badly that they would want to inflict such suffering upon you!

---

### Post by Varingo on 2010-01-15
> **Leppie said:**
> are you using a customized kernel?

This is standard ubuntuserver 9.10 with default updates as offered.
   (Not that the updates made any difference)

---

### Post by Varingo on 2010-01-15
> **Varingo said:**
> This is standard ubuntuserver 9.10 with default updates as offered.
   (Not that the updates made any difference)

Woops, sorry that was run from the HDD and not the Live CD.  I'll run the live CD and see if I can do the same if you want?  Please confirm.

---

### Post by Leppie on 2010-01-15
> **Varingo said:**
> Woops, sorry that was run from the HDD and not the Live CD.  I'll run the live CD and see if I can do the same if you want?  Please confirm.
no, don't worry. i needed the information for your installed system. but i thought you weren't able to boot your installed system?

---

### Post by Varingo on 2010-01-15
> **Leppie said:**
> i thought you weren't able to boot your installed system?

It boots with the two lines commented out in sda1/boot/grub/grub.cfg

#    search --no-floppy --fs-uuid --set 25e79fed-79ee-485c-9789-ce4d9dec2df0

The boot process is not the usual fast one, it goes

GRUB loading.

(single dot), times out, flashes some error text really fast and then boots...

---

### Post by Leppie on 2010-01-15
try disabling the UUID option in the grub defaults file. open the file with your editor:
```
gksudo gedit /etc/default/grub
```
uncomment the GRUB_DISABLE_LINUX_UUID line like this:
```
GRUB_DISABLE_LINUX_UUID=true
```
regenerate your grub.cfg:
```
sudo update-grub
```
reboot to see if it boots normally now

---

### Post by Varingo on 2010-01-15
OK did that, needed "sudo update-grub", unfortunately is a regression as it boots with "error: no such device: {ID} Failed to boot default entries.  Press any key to continue....

I see the --no-floppy line is back in the "e" editor, deleting that line again makes it boot.

---

### Post by Leppie on 2010-01-15
> **Varingo said:**
> OK did that, needed "sudo update-grub", unfortunately is a regression as it boots with "error: no such device: {ID} Failed to boot default entries.  Press any key to continue....

I see the --no-floppy line is back in the "e" editor, deleting that line again makes it boot.
yeah, sorry about the typo.
if you look at your grub.cfg, are the UUID's still there?

---

### Post by Varingo on 2010-01-15
I think so, as attached.  (My old commented out lines now gone)

---

### Post by Varingo on 2010-01-15
Leppie, firstly thank you for coming along and looking to help work it out.  (Nice surprise thank you)
The BIOS reports only 136G of a 320G HDD, could it be related to stuff being in space > than the 136G the BIOS detects - and if so would a small boot and / or grub partition fix the problem?  (Thats what I was going to try next if i could figure out the partitioning to achieve this)

---

### Post by Leppie on 2010-01-16
> **Varingo said:**
> Leppie, firstly thank you for coming along and looking to help work it out.  (Nice surprise thank you)
The BIOS reports only 136G of a 320G HDD, could it be related to stuff being in space > than the 136G the BIOS detects - and if so would a small boot and / or grub partition fix the problem?  (Thats what I was going to try next if i could figure out the partitioning to achieve this)
you're welcome, we're here to help each other out ;)

the issue with bios is not causing this, as old bios's cannot boot beyond cylinder 1024 but modern layout makes it possible to use larger disks with older bios's.

i think it has to do with your initial lvm setup. are you still using lvm, or do you still want to use it? or you just want to use a plain system with the old device indicators?

---

### Post by RaymondS on 2010-01-16
Hi Leppie,

OP here... do you have any ideas on my error?

This was a new install of ubuntu (downloaded as an ISO) on a totally clean (brand new) hard-drive - I thought it would have been a total shoe-in... but go figure!

When I first boot, I receive:

> 
error: no such device: a13e.......

  Failed to boot default entries.

Press any key to continue...


After pressing ctrl-alt-delete it comes up to the GRUB menu

When I at the GNU GRUB 1.97~beta4 menu and select Unbuntu, Linux 2.6.31-14-generic and try to boot, I receive this error: (slightly different from above)

> 
error: no such device: a13e.......

Press any key to continue...


I then ctrl-alt-delete again to come back to the GRUB menu and then I 'e'  on the "Unbuntu, Linux 2.6.31-14-generic" menu item and remove the following line:

```

search --no-floppy --fs-uuid --set a13e.......

``` 

I then ctrl-x to boot and Ubuntu comes up fine...

When I shut-down and then power back up, it all starts over...

Any help is appreciated,
-Raymond

---

### Post by Varingo on 2010-01-16
> **Leppie said:**
> i think it has to do with your initial lvm setup. are you still using lvm?

No, I twigged it might be to do with this, so reinstalled using a plain system relatively early on now...!

> **Leppie said:**
> Do you still want to use it?

Don't really need it for probably years...

> **Leppie said:**
> or you just want to use a plain system with the old device indicators?

I am now.  Can there be hangover stuff on the HDD from the initial LVM install, as best I can tell a full re-install and complete repartition of the drive should deal to any LVM stuff.  

Odd the GRUB_DISABLE_LINUX_UUID=true seemed to fail.

Is there a reference to the individual grub(2) commands involved somewhere?

---

### Post by Varingo on 2010-01-17
RaymondS and Joplass - are you using KVM's at all?  I am wondering if that is related.

---

### Post by RaymondS on 2010-01-17
Hi Varingo,

It could be that I am too tired or that the coffee has not yet kicked in... but could you expand KVM please?  :)

My system/environment is so plain it is painful... Ubuntu desktop 9.10 burned to ISO (like three days ago), installed on a brand new/virgin 160 GB hard-drive in a HP Pavilion zt3000.

-Raymond

---

### Post by Leppie on 2010-01-17
grub2 can handle lvm, but it needs a module loaded for that (insmod lvm).

the thing that really puzzles me is to why grub2 still uses uuid even though it's explicitly told not to do so. i was about to file a bug, but ran into this bug report: [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/499483](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/499483)
some sort of patch is attached, but the only thing it does is removing the "search ..." line from all the entries.
i am still looking into this, will get back when i find something new.

---

### Post by RaymondS on 2010-01-17
Thanks for the update Leppie.

Is this effecting all brand-new users who have downloaded 9.10 or am I just "lucky"???

Thanks again for the help!
-Raymond

---

### Post by Leppie on 2010-01-17
> **RaymondS said:**
> Thanks for the update Leppie.

Is this effecting all brand-new users who have downloaded 9.10 or am I just "lucky"???

Thanks again for the help!
-Raymond
you're welcome RaymondS.
i think you have just been "lucky" :(
i have 3 machines at home running karmic, none of them have issues with the UUID's (1 is about 3 yrs old, 1 is yr old, and the 3rd is about half a year old). i've read somewhere that the issue with UUID's is related to upgrades from jaunty to karmic. i know you did clean installs, however i've seen several times that karmic installs a mix of grub legacy and grub2. maybe this is related to the same issue.
so, the one thing you guys could try now is completely remove all grub related items and then reinstall grub2:
```
sudo apt-get purge grub grub-pc grub-common
sudo apt-get install grub-pc grub-common
```

---

### Post by RaymondS on 2010-01-17
Hey Leppie,

OK, used your code to remove grub (ran successfully) and then installed grub (also with success)

did a normal and full shut down

powered back up ... but unfortunately, I still came up with the same grub error:

> 
error: no such device: a13e.....

Failed to boot default entries.

Press any key to continue...


After some more coffee... maybe I will re-install from the ISO image  (maybe I will even burn a new ISO...) - your thoughts?????

What is the best way to wipe everything out and "start over"?

Thanks,
-Raymond

---

### Post by Leppie on 2010-01-17
to start with a clean system, you could do the following:
- download a new ubuntu image
- have a coffee while downloading
- check the image against the md5sum
- burn the image at the lowest offered speed (inferior to 10x)
- have some more coffee while burning the image
- check the image against the md5sum
- format the drive to ntfs
- go drink lots of coffee while the drive is being formatted ;)
- boot off the newly created livecd
- check the livecd for errors
- start installation from the livecd
- go have more coffee while your system is installing
- if you did not have a heart-attack yet, enjoy the ubuntu system ;)

---

### Post by Varingo on 2010-01-17
> **RaymondS said:**
> Hi Varingo,

It could be that I am too tired or that the coffee has not yet kicked in... but could you expand KVM please?  :)



See [http://en.wikipedia.org/wiki/KVM_switch](http://en.wikipedia.org/wiki/KVM_switch)    I removed the mouse (that not needed in that case!) and keyboard KVM mini DIN's, plugged in a normal keyboard, rebooted ok(!)  all be it with the detailed changes herein on board.

Reattached the KVM and it is still booting normally now.  No other changes made.  Something about art and science going on here?

> **RaymondS said:**
> 

 installed on a brand new/virgin 160 GB hard-drive in a HP Pavilion zt3000.


I wonder if HDD size is related also, this is also > 136G however I also note Leppie comments about this.

---

### Post by Varingo on 2010-01-17
Actually another random observation and consideration here, when I rebooted I normally was warm rebooting (sudo shutdown -r now) however changing the KVM mean't I did a cold boot (sudo shutdown -h now, wait some time, press power button) 

Could warm booting retain something that interfered with the "uncommented GRUB_DISABLE_LINUX_UUID line"?  Are you guys cold or warm booting also?

If warm, try cold...     I just tried again having had the machine off since my last post....again boots ok.

Also FWIW I've had this issue on two quite old machines = 400 and 866Mhz Intel CPU's.  I've also installed maybe 3 mythbuntu 9.10's in much newer 3G+ CPU systems with no grub2 issues.  What are your cpu's guys?

---

### Post by Varingo on 2010-01-17
> **Leppie said:**
> to start with a clean system, you could do the following:
.....
- format the drive to ntfs
.....;)

That's an interesting step Leppie.  

I infer a simple full re-install (full repartition) does not fully clean the drive on its own, something I've suspected (from previous grub issues with ~8.10 or ~9.04 on a different PC)  Is that the reason?

How would you suggest formatting the drive with NTFS, other than installing XP?

---

### Post by Leppie on 2010-01-17
you could even use the livecd, but before being able to do so you would have to install the ntfsprogs package:
```
sudo apt-get install ntfsprogs
```
you can then format using gparted:
```
sudo gparted
```

---

### Post by Leppie on 2010-01-17
> **Varingo said:**
> That's an interesting step Leppie.  

I infer a simple full re-install (full repartition) does not fully clean the drive on its own, something I've suspected (from previous grub issues with ~8.10 or ~9.04 on a different PC)  Is that the reason?
i am not 100% sure, but these were my experiences as well. adding the fact that a complete format of a 100+gb drive/partition to for example ext3/4 or whatever only takes a fraction of the time required when formatting to ntfs. with linux filesystems it only takes a couple of minutes, whereas formatting to ntfs could leave you enough time to have dinner before having your coffee as well.

---

### Post by RaymondS on 2010-01-17
Just some notes that might help other noobs  :)

Well, thanks to my cd/dvd burner not being all to happy on my main/development machine... I had to figure out how to download the iso image onto my database server (no GUI, command line interface only).

```

wget -c http://mirrors.easynews.com/linux/ubuntu-releases/karmic/ubuntu-9.10-desktop-i386.iso

```

I checked the md5 hash sums and it came out OK...

```

md5sum ubuntu-9.10-desktop-i386.iso

```

I also needed to figure out how to burn that newly downloaded iso image to disc...

```

cdrecord -v -pad speed=1 dev=ATAPI:0,0,0 ubuntu-9.10-desktop-i386.iso

```

and I am continuing to work my way down Leppie's list... and writing this post since I have lots of time while ntfs format is doing its thing.........

> 
to start with a clean system, you could do the following:
- download a new ubuntu image
- have a coffee while downloading
- check the image against the md5sum
- burn the image at the lowest offered speed (inferior to 10x)
- have some more coffee while burning the image
- check the image against the md5sum
- format the drive to ntfs
- go drink lots of coffee while the drive is being formatted :wink:


The coffee is wearing off ... but I am getting close 90% of the way!!!  The previous steps are all done and I have my new iso disc in hot little hand!!!

> - boot off the newly created livecd
- check the livecd for errors
- start installation from the livecd
- go have more coffee while your system is installing
- if you did not have a heart-attack yet, enjoy the ubuntu system :wink:
 		                   		  		  		 		 			 				

... chomping at the bit to follow the rest of these.... 91%....

Thanks again for the help!
-Raymond

---

### Post by RaymondS on 2010-01-17
I followed the remaining steps from Leppie and all went (fairly) well except the end result is the same.....  :(


> - boot off the newly created livecd
- check the livecd for errors
- start installation from the livecd
- go have more coffee while your system is installing
- if you did not have a heart-attack yet, enjoy the ubuntu system :wink:


I did note one interesting thing during the install... I was prompted by the following (this may be 100% normal but I thought I would ask...

> 
If you continue, the changes listed below will be written to the disks.

Otherwise, you will be able to make further changes manually.

WARNING: This will destroy all data on any partitions you have removed as well as on the partitions that are going to be formatted.

The partition table of the following devices are changed:
 SCSI1 (0,0,0)9sda)

The following partitions are going to be formatted:
partition #1 of SCSI1 (0,0,0)(sda) as ext4
partition #5 of SCSI1 (0,0,0)(sda) as swap



Just like before, on my first "real" boot (not off of CD) the grub error occurred (see previous posts)... I did the ctrl-alt-delete and it came up to the grub menu

There I used 'e' to edit the script and removed the following line:

> 
search --no-floppy --fs-uuid --set 540905a1-....


I hit crrl-x to continue on and it booted fine... but this was where I was before... an endless loop of:

-PowerUp
-error
-ctrl-alt-delete
-grub menu
-'e' edit to remove floppy uuid stuff
-ctrl-x
-successful Ubuntu startup
-shut-down/powerdown

... and then it starts all over again!!!

Coffee has gone and the body and mind are spent... I take up the fight again tomorrow...

-Raymond

---

### Post by Varingo on 2010-01-17
> **Leppie said:**
> i am not 100% sure, but these were my experiences as well. adding the fact that a complete format of a 100+gb drive/partition to for example ext3/4 or whatever only takes a fraction of the time required when formatting to ntfs. with linux filesystems it only takes a couple of minutes, whereas formatting to ntfs could leave you enough time to have dinner before having your coffee as well.

Interesting.  My assumption is that *any* new format will erase the disc - even DOS would probably do the same - and DOS boot discs can be readily downloaded.  Also the Ultimate Boot disc has something on it to erase HDD's so that might be an alternative.   Still the ntfs commands you advise should probably also work!

RaymondS.  Try Leppies advice about commenting out the  GRUB_DISABLE_LINUX_UUID line, I guess you are getting to that tomorrow.  It may now be working for me!

---

### Post by Leppie on 2010-01-17
> **RaymondS said:**
> Coffee has gone and the body and mind are spent... I take up the fight again tomorrow...
i'm sorry it gave you the same result, have you tried updating the system already?
since i did my karmic install, several grub2 updates have come through.

alternatively you could always modify your grub system to ignore the "search" statement:
```
gksudo gedit /usr/lib/grub/grub-mkconfig_lib
```look for the following part:
```
  # If there's a filesystem UUID that GRUB is capable of identifying, use it;
  # otherwise set root as per value in device.map.
```just underneath should be the if statement to modify:
```
  if fs_uuid="`${grub_probe} --device ${device} --target=fs_uuid 2> /dev/null`" ; then
    echo "search --no-floppy --fs-uuid --set ${fs_uuid}"
  fi
```if you modify like this, you should be able to easily change it back using the grub defaults file when a solution is found:
```
  if [ ! "x${GRUB_DISABLE_LINUX_UUID}" = "xtrue" ] ;then
      if fs_uuid="`${grub_probe} --device ${device} --target=fs_uuid 2> /dev/null`" ; then
      echo "search --no-floppy --fs-uuid --set ${fs_uuid}"
      fi
  fi

```

after that you have to run update grub:
```
sudo update-grub
```

---

### Post by Leppie on 2010-01-18
Raymond, could you post the output of this command:
```
sudo blkid -c /dev/null
```

---

### Post by Leppie on 2010-01-18
> **Varingo said:**
> See [http://en.wikipedia.org/wiki/KVM_switch](http://en.wikipedia.org/wiki/KVM_switch)    I removed the mouse (that not needed in that case!) and keyboard KVM mini DIN's, plugged in a normal keyboard, rebooted ok(!)  all be it with the detailed changes herein on board.

Reattached the KVM and it is still booting normally now.  No other changes made.  Something about art and science going on here?
i am absolutely baffled... your kvm switch should not have any influence on UUID's as this would be something like changing your keyboard or mouse will assign new UUID's to your partitions. and this would have huge consequences for laptop/netbook users.
it makes absolutely no sense, maybe we're looking in the wrong place and there's some bugs with the UUID system.

---

### Post by RaymondS on 2010-01-18
I am back with coffee in hand!  :)


@Leppie, 

sudo blkid -c /dev/null returned this:

> 
/dev/sda1: UUID="540905a1....." TYPE="ext4"
/dev/sda5: UUID="9930e55c....." TYPE="swap"


Note: I have not yet commented out the  GRUB_DISABLE_LINUX_UUID line... I thought I would get this back to you first before doing anything else! 

Many thanks,
-Raymond

---

### Post by stabface on 2010-01-18
For the record. 

I grabbed a new 320 gig  HD, popped it into an old emachine laptop.  

installed ubuntu, 9.10  ext4. used the entire disk. 

I am getting this exact same problem. nothing to do with a KVM switch or anything.

I installed 8.10 on this machine with the failed HD and it installed flawlessly. 

exact same problem as above, removing the search line and Ctrl -x gets me into the system.

if i find anything else i will post here.

---

### Post by Leppie on 2010-01-18
Raymond,
thanks for getting back at me.
did you make a backup of your system? you could then try to update your system...

---

### Post by Leppie on 2010-01-18
> **stabface said:**
> I installed 8.10 on this machine with the failed HD and it installed flawlessly. 

exact same problem as above, removing the search line and Ctrl -x gets me into the system.
what happens if you remove grub legacy and install grub2 on your jaunty system?

---

### Post by RaymondS on 2010-01-18
Hi Leppie!

Sorry for the delays... I am checking the boards and replying while working, which is really keeping me moving! :)

I hate to show how much of a noob I am... but here goes!

> 
did you make a backup of your system? you could then try to update your system... 	

Hmmm, I did a quick search... but my guess is that I need to run some more terminal commands here...

Is there a command to backup or will I just be using 'cp ' to make physical copies on my disk? 

And I am assuming that I will be using more 'apt-get install' commands similar to the grup update you had me try, to actually update my system...correct???

Many thanks,
-Raymond

---

### Post by Leppie on 2010-01-19
> **RaymondS said:**
> Hmmm, I did a quick search... but my guess is that I need to run some more terminal commands here...

Is there a command to backup or will I just be using 'cp ' to make physical copies on my disk? 

And I am assuming that I will be using more 'apt-get install' commands similar to the grup update you had me try, to actually update my system...correct???

Many thanks,
-Raymond
sorry for the delay...
a simple way of backing up would be using the dd command:
```
sudo dd if=/dev/sdaX of=/path/to/image
```or, if you want a zipped image:
```
sudo apt-get install gzip
sudo dd if=/dev/sdaX | gzip > /path/to/image.gz
```


To get back on the old bios & cylinder 1024 talk, is one of you guys willing to create a boot partition and test like that?

---

### Post by Varingo on 2010-01-20
> **Leppie said:**
> To get back on the old bios & cylinder 1024 talk, is one of you guys willing to create a boot partition and test like that?

I think what you are saying here is a separate small partition on the HDD?

The original PC that I first found the problem on is free here, I just need a HDD that reproduces the problem.  I presume I'll need a HDD > 136G, not sure I have a spare one of those....   If a 20G will do it no problem, can run up one of those up if you think it might help?

---

### Post by Leppie on 2010-01-20
> **Varingo said:**
> I think what you are saying here is a separate small partition on the HDD?

The original PC that I first found the problem on is free here, I just need a HDD that reproduces the problem.  I presume I'll need a HDD > 136G, not sure I have a spare one of those....   If a 20G will do it no problem, can run up one of those up if you think it might help?
thanks :)
i just wanted to properly eliminate the 1024 cylinder (or 136gb) limit.
i have disks available, unfortunately on my systems it all works without any issues (or should i say fortunately?)

---

### Post by Varingo on 2010-01-20
> **Leppie said:**
> thanks :)
i just wanted to properly eliminate the 1024 cylinder (or 136gb) limit.
i have disks available, unfortunately on my systems it all works without any issues (or should i say fortunately?)

OK I think we're in sync here, I'll see if I can find one that repros the problem and get back when I am.  (The 320G HDD is now in production use) Gotta be some ways I can contribute / give back somehow to the fantastic effort that goes on here with this nixware that just keeps getting better!

---

### Post by Varingo on 2010-01-21
> **Leppie said:**
> is one of you guys willing to create a boot partition and test like that?

OK setup a 250G on the original PC, seems to start the same....with similar issues, except seems worse as the "e" trick does not seem to even work(!)  

It starts off

GRUB loading.
_   (Flashing)

I can't seem to get past this point this time.

We can do what we like with this HDD for now.  How can I help now?

---

### Post by Leppie on 2010-01-21
> **Varingo said:**
> OK setup a 250G on the original PC, seems to start the same....with similar issues, except seems worse as the "e" trick does not seem to even work(!)  

It starts off

GRUB loading.
_   (Flashing)

I can't seem to get past this point this time.

We can do what we like with this HDD for now.  How can I help now?
did assign a /boot partition in the lower regions of this drive?
if grub doesn't continue loading, it's not been installed properly into the mbr.

---

### Post by Varingo on 2010-01-21
> **Leppie said:**
> did assign a /boot partition in the lower regions of this drive?
if grub doesn't continue loading, it's not been installed properly into the mbr.

I just  did the standard install for a start to see that we were still in the same ball park.  Seems we are!  I did watch during the end of the install where it said it was installing grub, it even did a grub update, which was a little surprising.

I'll run up again.  Any suggestions how to partition it exactly?  Do I just do a separate partition for /boot?  Which format? I guess 20M be ok.

---

### Post by Varingo on 2010-01-21
Actually I'll just do two partitions, and put the whole thing in say under 20G, which is way under the 136, and just have a large spare one.  Should be enough to test?

---

### Post by gxlzrsk397 on 2010-01-21
That sounds painful what you have gone through but I think it may have answered a question I was going to ask.  I was going to ask whether there is any serious need to update from Ubuntu 9.04 to 9.10?
And from what you have said there, it seems that there is more serious reason not to upgrade...
The assumption being that newer is improved, superior and more bug free, etc...
By the way, I have been updating online from within UBUNTU 9.04...
Is there any benefit to using a copy of UBUNTU 9.10 on a disk??
OK.. I am out of here...  I am new so just learning but enjoying ..no real problems....

---

### Post by Leppie on 2010-01-21
> **Varingo said:**
> Actually I'll just do two partitions, and put the whole thing in say under 20G, which is way under the 136, and just have a large spare one.  Should be enough to test?
i would say so, thanks for testing :)

in essence it doesn't matter much if the whole system is under cylinder 1024 or just boot, i'd say it should have the same result.

---

### Post by Varingo on 2010-01-22
OK, I reinstalled, and it seems I added a new partition onto /dev/sda1 of 40G, this is just adjusting the previous install and installing on that new 40G.  This is not a full disk wipe / install which I might do next.  However I am given various boot options, of which one is booting from the newly created sda1 - which happens as I would expect, so I am guessing something about the partition size is important here.  I am also given the option of booting off the original large partition and that still fails, this time coming up with the error of error: no such device: {SSID}....    What now?

---

### Post by Leppie on 2010-01-22
> **Varingo said:**
> OK, I reinstalled, and it seems I added a new partition onto /dev/sda1 of 40G, this is just adjusting the previous install and installing on that new 40G.  This is not a full disk wipe / install which I might do next.  However I am given various boot options, of which one is booting from the newly created sda1 - which happens as I would expect, so I am guessing something about the partition size is important here.
so it does boot off the partition located in the lower regions of the disk?

> **Varingo said:**
> I am also given the option of booting off the original large partition and that still fails, this time coming up with the error of error: no such device: {SSID}....    What now?
SSID usually has something to do with wireless, not sure how this would be connected to this issue...

---

### Post by Varingo on 2010-01-22
> **Leppie said:**
> so it does boot off the partition located in the lower regions of the disk?


Its booting (with help) off sda1 on the 250G disc somewhere, just not sure where the 40G is!  Looks like it is the first blocks.  (I did do a DOS fdisk but without the format, and then turned the power on and it still ran, so I just re-installed.)

> 
sudo /sbin/fdisk -l
[sudo] password for me:

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4d5455ef

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        4864    39070048+  83  Linux
/dev/sda2            4865       30401   205125952+   5  Extended
/dev/sda3   *         964       16709   126471240    c  W95 FAT32 (LBA)
Partition 3 does not end on cylinder boundary.
/dev/sda5           30122       30401     2249068+  82  Linux swap / Solaris
/dev/sda6            4865       29841   200627689+  83  Linux
/dev/sda7           29842       30121     2249068+  82  Linux swap / Solaris

Partition table entries are not in disk order


It says its booting from sda1.  

I can clean format the disc and re-install a clean one if you want, this might be enough though?

> **Leppie said:**
> 
SSID usually has something to do with wireless, not sure how this would be connected to this issue...

Woops, sorry, its the UUID I think , just was trying not to type out the long string like this one: uuid --set 25e79fed-79ee-485c-9789-ce4d9dec2df0

---

### Post by Leppie on 2010-01-22
> **Varingo said:**
> Its booting (with help)
what do you mean "it's booting (with help)"?

 > **Varingo said:**
> off sda1 on the 250G disc somewhere, just not sure where the 40G is!  Looks like it is the first blocks.
sda1 starts at cylinder 1:
> Device Boot      [COLOR=Red]Start[/COLOR]         End      Blocks   Id  System
/dev/sda1               [COLOR=Red]1[/COLOR]        4864    39070048+  83  Linux> **Varingo said:**
> Woops, sorry, its the UUID I think , just was trying not to type out the long string like this one: uuid --set 25e79fed-79ee-485c-9789-ce4d9dec2df0
ok, was already getting worried about other bugs... lol

---

### Post by 00_Spykes on 2010-01-22
Just a thought; Check if the UUID's in /etc/fstab matches those in the grub config. Or you could just create an fstab and a grub conf without UUID's I guess... Not sure how that works, but I'm always suspicious of anything automagical. ;)

Good luck!

Edit: Try without UUID's and see if that works, I've heard of people having problems with that.

---

### Post by Varingo on 2010-01-22
> **Leppie said:**
> what do you mean "it's booting (with help)"?


That means I have to select the sda1 partition from the menu shown, if I could capture the boot screen text would help, however seems its not logged anywhere.  Its the "GNU GRUB  version 1.97~beta4" menu.

---

### Post by Leppie on 2010-01-22
> **Varingo said:**
> That means I have to select the sda1 partition from the menu shown, if I could capture the boot screen text would help, however seems its not logged anywhere.  Its the "GNU GRUB  version 1.97~beta4" menu.
you mean it doesn't boot automatically into the system installed on sda1, but once selected it will boot normally without problems (and further intervention like removing the "search" line)?

---

### Post by Varingo on 2010-01-22
> **Leppie said:**
> you mean it doesn't boot automatically into the system installed on sda1, but once selected it will boot normally without problems (and further intervention like removing the "search" line)?

Yes Leppie, that's correct.

---

### Post by Leppie on 2010-01-23
well, so it seems that either grub or the UUID system has a bug with larger filesystems and older bioses.

could someone else try the same thing? create a small boot or ubuntu partition under the 136gb limit?

---

### Post by Varingo on 2010-01-23
> **Leppie said:**
> could someone else try the same thing? create a small boot or ubuntu partition under the 136gb limit?

I am not sure the goal of that, however anyone wishing to do so please fell free to do so.  

I am mindful I've had two reasonably old and different (PII 400/BX Chipset and PIII 866 / VIA Chipset) systems do the same thing with a 320G and 250G HDD, I don't mind running it up on another but I think we've already concluded that:

> **Leppie said:**
> well, so it seems that either grub or the UUID system has a bug with larger filesystems and older bioses.


I think we need to work out what next to move this forward?  Get some more logging or debugging happening?  If someone would tell me what to do from here in that direction I'd be pleased to help.

---

### Post by Leppie on 2010-01-23
> **Varingo said:**
> I think we need to work out what next to move this forward?  Get some more logging or debugging happening?  If someone would tell me what to do from here in that direction I'd be pleased to help.
have you checked dmesg for the system that needs modification at boot?
try to boot into that system, let the error come up and then reboot into the other install to check the dmesg log. if there's anything it should be at the start of the log.

---

### Post by cariboo on 2010-01-23
Have a look [here]("https://wiki.ubuntu.com/Grub2") for a grub2 howto. Your problem looks reproducible, so I would suggest filing a bug, run:

```
ubuntu-bug grub2
```

on the system with the problem, once the Launchpad bug page opens provide a detailed explanation of what you are doing.

---

### Post by Varingo on 2010-01-23
> **Leppie said:**
> have you checked dmesg for the system that needs modification at boot?
try to boot into that system, let the error come up and then reboot into the other install to check the dmesg log. if there's anything it should be at the start of the log.

dmesg is attached. (saved as odt so can upload.)  Can you make something of this?  Looks to me this is recording from the time the boot drive is elected - and not before during grub run up?  Boot is empty.

---

### Post by Varingo on 2010-01-23
> **cariboo907 said:**
> Have a look [here]("https://wiki.ubuntu.com/Grub2") for a grub2 howto. Your problem looks reproducible, so I would suggest filing a bug, run:

```
ubuntu-bug grub2
```on the system with the problem, once the Launchpad bug page opens provide a detailed explanation of what you are doing.

OK doing that found [https://bugs.launchpad.net/grub/+bug/403408](https://bugs.launchpad.net/grub/+bug/403408) which seems to be a reproduction and also advancement on the issue.  It seems a later GRUB2 version might fix it.

---

### Post by Leppie on 2010-01-23
> **Varingo said:**
> dmesg is attached. (saved as odt so can upload.)  Can you make something of this?  Looks to me this is recording from the time the boot drive is elected - and not before during grub run up?  Boot is empty.
thanks, this actually the dmesg log from the system on sda1 :P

i found something funny though:
```
[    0.044433] weird, boot CPU (#0) not listed by the BIOS.
```
is this a 32bit install on a 64bit machine?

---

### Post by Varingo on 2010-01-23
> **Leppie said:**
> thanks, this actually the dmesg log from the system on sda1 :P


Isn't this what you were expecting?


> **Leppie said:**
> thanks, this actually the dmesg log from the system on sda1 :P

i found something funny though:
```
[    0.044433] weird, boot CPU (#0) not listed by the BIOS.
```is this a 32bit install on a 64bit machine?

No, 32bit install on a very 32bit Pentium 400!  (Compaq BIOS - Deskpro EP 6400)

---

### Post by Varingo on 2010-01-23
> **Leppie said:**
> 
```
[    0.044433] weird, boot CPU (#0) not listed by the BIOS.
```is this a 32bit install on a 64bit machine?

Interesting, that weird message is present in dmesg on both machines that exhibit the problem.  (And not on another recent 9.10 that boots fine)

---

### Post by Leppie on 2010-01-23
> **Varingo said:**
> Isn't this what you were expecting?
no, could you post the one on the system producing the error?

> **Varingo said:**
> No, 32bit install on a very 32bit Pentium 400!  (Compaq BIOS - Deskpro EP 6400)
strange... maybe you can file another bug... lol

---

### Post by Varingo on 2010-01-23
> **Leppie said:**
> no, could you post the one on the system producing the error?


Leppie, I did, (see post #65) what makes you think it isn't from that P400 - that might be a clue to whats going on?

---

### Post by Leppie on 2010-01-23
> **Varingo said:**
> Leppie, I did, (see post #65) what makes you think it isn't from that P400 - that might be a clue to whats going on?
ok, i think we have a miscommunication.
i thought you had created a new 40gb partition on a drive with karmic already installed in another partition (not booting properly). but if you deleted that first install don't worry.

---

### Post by Varingo on 2010-01-23
As best I understand that dmesg is from the 40G partition on the test machine with the 250G HDD.  (Called ubuntutest)  The original 320G drive is called ubuntuserver.  perhaps I misunderstand which dmseg you sought?  For completeness I attach the dmesg from ubuntuserver (original problem 320G HDD) and in case that is the dmesg you mean't?

---

### Post by Varingo on 2010-01-23
For what its worth it seems to me the grub problem is occurring before dmesg starts - its starts logging and running up the kernal that was manually selected by the grub2 interface.  I think we need a log of what grub2 is doing.  Not sure we can get that though.

---

### Post by Leppie on 2010-01-23
> **Varingo said:**
> For what its worth it seems to me the grub problem is occurring before dmesg starts - its starts logging and running up the kernal that was manually selected by the grub2 interface.  I think we need a log of what grub2 is doing.  Not sure we can get that though.
yeah, i think i got some things mixed up...

---

### Post by Varingo on 2010-01-24
OK done some more things.
Installed 9.10 server on a 80G HDD, as expected works fine.
[http://grub.enbug.org/FrontPage](http://grub.enbug.org/FrontPage) says there are two more recent GRUB versions that are also out of beta.  I therefore tried installing Lucid alpha 2 on the 80G, it also gets past the GRUB without issue but does not finish booting, hanging in the clean step.  It might be worth trying to apply the alpha's updated grub to the 250G drive, however I've not figured out its version yet.  A newer GRUB version may be all I need?

---

### Post by Leppie on 2010-01-24
> **Varingo said:**
> OK done some more things.
Installed 9.10 server on a 80G HDD, as expected works fine.
[http://grub.enbug.org/FrontPage](http://grub.enbug.org/FrontPage) says there are two more recent GRUB versions that are also out of beta.  I therefore tried installing Lucid alpha 2 on the 80G, it also gets past the GRUB without issue but does not finish booting, hanging in the clean step.  It might be worth trying to apply the alpha's updated grub to the 250G drive, however I've not figured out its version yet.  A newer GRUB version may be all I need?
well, that's what i figured a while back in this thread. but i think Raymond said his troubles started after updating...

---

