---
title: "Ubuntu installer doesn't correctly see my partitions?"
date: 2010-10-06
forum: Installation &amp; Upgrades
---

### Post by eurostyle360 on 2010-10-06
So Gparted seems to correctly identify my drives and partitions but for some reason...
[IMG]http://img.photobucket.com/albums/v334/aldableep3/Screenshot--dev-sda-GParted.png[/IMG]

The actual installer does not.
[IMG]http://img.photobucket.com/albums/v334/aldableep3/Screenshot-Install.png[/IMG]

The installer tells me that there is no prior OS installed (lie) and doesn't acknowledge my windows drive.  It suggests using my terabyte data drive but doesn't automatically detect the free space I made for it on my Windows drive.  So I select to specify the partitions manually and end up with this:
[IMG]http://img.photobucket.com/albums/v334/aldableep3/Screenshot-Install-1.png[/IMG]

Anyone know what's going on?  That last screenshot confuses me.  Obviously somethings not right here.  It's only detecting two out of my three hard drives (1 for OS, two other for data.)  It seems to get my 1.5 TB drive info correct, but tells me that I have 250 GB free out of my 250 GB OS drive.  Is there something I'm totally missing here?

EDIT:
Now that I look closer it seems to be telling me that I have a 500 GB stripe.  That *used* to be true, but now isn't.  I have three drives, two of which are exactly identical by model number.  One dedicated to OS an the other for data.  Could the installer think I have a RAID when really it's just two identical drives?  These drives used to be striped in a RAID in ubuntu and windows before, but are now completely independent; could there be some residual boot data that's making the installer think it's still a RAID array?

---

### Post by P4man on 2010-10-06
> **eurostyle360 said:**
>  could there be some residual boot data that's making the installer think it's still a RAID array?

Yes, IM pretty sure thats at least part of whats going on. Metadata for the raid is written to MBR I think, and its probably still there.

Have you tried running the live session with the "no-dmraid" option ? Just press a key right after the livecd boot to show a menu, then in options select the no-dmraid.

---

### Post by eurostyle360 on 2010-10-06
> **P4man said:**
> Yes, IM pretty sure thats at least part of whats going on. Metadata for the raid is written to MBR I think, and its probably still there.

Have you tried running the live session with the "no-dmraid" option ? Just press a key right after the livecd boot to show a menu, then in options select the no-dmraid.

Cool thanks for the advice.  I will try this as soon as I get home.  If not, how would I go about clearing the MBR on my data drive?

---

### Post by P4man on 2010-10-06
Good question. I dont know. 

Id have a look in "disk utility" (if you boot with dmraid). The brute force way would be zero-ing the drive with dd, but then you also lose all data. Then again it could also be the bios playing tricks with you, if you have a soft/bios raid.

---

### Post by oldfred on 2010-10-06
DO NOT run this if you have RAID of any type. This is if you have a drive that was RAID and is not now.

Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
Also check BIOS for raid settings
More discussion:
[http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738](http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738)

---

### Post by eurostyle360 on 2010-10-06
> **oldfred said:**
> DO NOT run this if you have RAID of any type. This is if you have a drive that was RAID and is not now.

Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
Also check BIOS for raid settings
More discussion:
[http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738](http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738)

Cool this looks promising.  I do not currently have a raid, but I used to.  Now all my drives are independent of each other and my BIOS settings are set to regular SATA non-RAID.  I just want to get through the install process cleanly, so this might help.  If nothing else, I have enough free space on my 1.5 TB data drive to back up the other two drives, which I can then zero out, I suppose.  I'll see what I can do :)

---

### Post by eurostyle360 on 2010-10-06
Just an update; I tried the above suggestion and it worked perfectly.  All I did was type those commands into the terminal for each of my problematic drives and restarted and I was able to install to the largest continuous free space.  Finally!  Thanks for the help!

---

### Post by oldfred on 2010-10-06
Glad it worked.

Whenever were see the device /mapper we know you have RAID or LVM or something special and if you really do not then it has old data still in the drive that can cause issues.

---

