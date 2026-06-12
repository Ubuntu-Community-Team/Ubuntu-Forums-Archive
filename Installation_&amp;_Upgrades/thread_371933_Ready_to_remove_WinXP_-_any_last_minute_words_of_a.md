---
title: "Ready to remove WinXP - any last minute words of advice?"
date: 2007-02-27
forum: Installation &amp; Upgrades
---

### Post by gtratter on 2007-02-27
All right, 
Within the last 3 weeks I installed Dapper, upgraded to Edgy and with the help of many of you explored the world of Linux. The result: I LOVE it.
I have now everything working the way I want it and I am amazed about all the new useful things I learn daily. 

I still have XP installed on a partition and made up my mind that I want to do a clean re-install. This for two reasons:
1) to get rid of Windows
2) to setup the Ubuntu install correctly, including a /swap and /home partition which I neglected earlier.

I backed up important document files and folders to a USB stick. Is there anything else I should think about or just go for it?

---

### Post by srt4play on 2007-02-27
Just go for it.

---

### Post by wakady on 2007-02-27
i wish i can do it too....
hope that i'll follow u soon..
PS. whats diff between setting one partition / & setting a /home, /usr, /var and for sure a /
????

---

### Post by Doomedelite on 2007-02-27
You can do it!:guitar:

---

### Post by bulldog on 2007-02-27
Don't do it!!!:) 

Just dual boot for a while to see if you're happy in a few months.
Some weeks are not enough to know if you can manage everything.


Just some words of advice.

---

### Post by Irony on 2007-02-27
If you've paid for XP I don't see the point of removing it - perhaps when it becomes really out of date.

I had XP on my 200 GB drive but over time I shrank it down to 10 GB - actually I've got about 13 partitions on my main drive for storage and copies!

---

### Post by floke on 2007-02-27
As much as it pains me, I agree - wait a while - there's no rush just yet - better to have a backup so you can get to the forums in case anything goes wrong until you know how to rescue yourself from any tricky situations.

Reinstall Ubuntu over the existing one if you have to - it should have set up a swap file before - are you sure you haven't got one.

If you want to create a home directory then post your partition details here and we'll sort you out. You can always shrink your Windows partition down further and use the space there as a new home.

But if you do decide to do it - savour the moment.

---

### Post by gtratter on 2007-02-27
> **wakady said:**
> i wish i can do it too....
hope that i'll follow u soon..
PS. whats diff between setting one partition / & setting a /home, /usr, /var and for sure a /
????

From what I understand reading in these forums the only two partition which really affect my level of use are the /swap and the /home partitions.

I want to have the /home partition so I can upgrade in the future without losing all my personal settings (or at the very least it will make it much easier)

As far as the /swap - there are mixed opinions even on this forum - but the general consensus is that if you can spare the space give it a /swap - so I will

---

### Post by gh0st on 2007-02-27
I dumped Windows a while ago and I haven't looked back. I have 3 partitions on my hard disk. 

1. A root file system one "/"
2. A "/home" partition for all my personal files
3. A "/swap" partition.

It was easy to set up with the partitions in the installer, I had been using other Linux distributions for a while though so I suppose I wasn't a complete newb.

You can do it though, just think positive and use the forums when you need help, it's a great resource. Let us know if you need anything.

Good luck :)

---

### Post by bulldog on 2007-02-27
> **gtratter said:**
> From what I understand reading in these forums the only two partition which really affect my level of use are the /swap and the /home partitions.

I want to have the /home partition so I can upgrade in the future without losing all my personal settings (or at the very least it will make it much easier)

As far as the /swap - there are mixed opinions even on this forum - but the general consensus is that if you can spare the space give it a /swap - so I will

If you don't have a separate /home,you can always copy your settings to a USB device or something like that and copy it back afterwards.

But I strongly advice to wait a bit longer,before deleting your windows.
If you run Linux a year or longer and you don't need the forums to solve your problems,you can think about removing windows.

---

### Post by gtratter on 2007-02-27
> **Steve.K said:**
> As much as it pains me, I agree - wait a while - there's no rush just yet - better to have a backup so you can get to the forums in case anything goes wrong until you know how to rescue yourself from any tricky situations.

Reinstall Ubuntu over the existing one if you have to - it should have set up a swap file before - are you sure you haven't got one.

If you want to create a home directory then post your partition details here and we'll sort you out. You can always shrink your Windows partition down further and use the space there as a new home.

But if you do decide to do it - savour the moment.

Steve,
I am positive I don't have one - here is  the output of fstab
```
gt@gt-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4 -- converted during upgrade to edgy
UUID=952149f1-e441-4bea-80af-51d6ed8734bc / ext3 defaults,errors=remount-ro 0 1
# /dev/sda1 -- converted during upgrade to edgy
UUID=07D5-0B18 /media/sda1 vfat defaults,utf8,umask=007,gid=46 0 1
# /dev/sda2 -- converted during upgrade to edgy
UUID=98C8A2D3C8A2AEC6 /media/sda2 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
/dev/sda3       /media/sda3     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/proc/bus/usb/  /proc/bus/usb/  usbfs    none        0       0
gt@gt-laptop:~$ 

```

---

### Post by gtratter on 2007-02-27
> **bulldog said:**
> If you don't have a separate /home,you can always copy your settings to a USB device or something like that and copy it back afterwards.

But I strongly advice to wait a bit longer,before deleting your windows.
If you run Linux a year or longer and you don't need the forums to solve your problems,you can think about removing windows.

**Bulldog**
I am on the forums daily to read up on advice - so I will heed yours - and just ignore the windows partition for a year!

---

### Post by floke on 2007-02-27
That's wierd about the swap partition - how did you install Ubuntu?
As for the year wait - that personally feels a bit long: I decided that when I began using Ubuntu I would give it 6 months without needing to use Windows or until I ran out of disc space - whichever came soonest. Last weekend I had an irresistible urge to destroy windows (have been using Ubuntu since end October last year, so around 4 months); there are so many things that I haven't a clue about (though I learn something new every day just by browsing the forums!), but I know that I can dig myself out of the worst hole through a collection of LiveCDs and a good backup policy.

I've also learned (dual booting Edgy amd Feisty now) that its good to have more than one OS on your PC; it makes life more interesting and you always have that backup there - just as long as it's not Windows :) 

So I'd give it a few more months until you felt comfortable, and just ignore it. I found that I never needed mine, and every time I went into it (progressive shrinking policy) I would get ever more annoyed at how useless it was compared to Ubuntu.

Lets see if we can sort your swap file out...

** EDIT ** Returned with info..
Ok, so I found this useful looking thread: [http://ubuntuforums.org/showthread.php?t=265051&highlight=swap+file](http://ubuntuforums.org/showthread.php?t=265051&highlight=swap+file)
Basically confirms what I suspected you would have to do - create an extended partition if you don't already have one, and create a swap file within it.
Your partition table looks strange though: sda4 is ext3; but sda1&3 are vfat and sda1 is ntfs - and they are all labelled as having changed in an upgrade to edgy?
What's the story??

---

### Post by gtratter on 2007-02-27
> **Steve.K said:**
> That's wierd about the swap partition - how did you install Ubuntu?

>>>snip snip snip >>>>>

Lets see if we can sort your swap file out...

Steve,
originally from a dapper *.iso wich I downloaded and burned. Before I ran the install I defraged the disk 3 times, then let the install CD take over. I now know that I should have 
/
/swap
My guess is it had something to do with my allocating disc space incorrectly but I can't remember it all to well what I did or didn't do :(

The thing is even with that - the system runs rock solid, start up is about a minute shorter compared to windows, d-base and spreadsheets are blazing fast and I never run out of new things to learn...

---

### Post by floke on 2007-02-27
Ok, so its no biggy then - your swap file only gets used if extra memory is needed, so clearly you don't need it!

However, to set up a home partition you will still need to create an extended partition - which means that one of your existing partitions will probably have to go (you can only have four primary partitions on a hard drive, and it looks like you already have four).

How big are they, and what are they used for?

---

### Post by gtratter on 2007-02-27
> **Steve.K said:**
> Ok, so its no biggy then - your swap file only gets used if extra memory is needed, so clearly you don't need it!

However, to set up a home partition you will still need to create an extended partition - which means that one of your existing partitions will probably have to go (you can only have four primary partitions on a hard drive, and it looks like you already have four).

How big are they, and what are they used for?

Let's see: (this is a Dell XPS-M140 laptop)
sda4 is ext3 > this is where I have Ubuntu ~ 35 GB
sda 1 & 3 are vfat > this is 'Dell Restore' and 'Dell Utility' Space ~ combined 10 GB
sda2 is ntfs > Win XP resides here ~ 35 GB

> **Steve.K said:**
> and they are all labelled as having changed in an upgrade to edgy?
What's the story??

not sure about the story. Originally I installed Ubuntu Dapper on a very small partition - then I upgraded to Edgy and after that used *gparted* to increase the space for Ubuntu

```

gt@gt-laptop:~$ sudo fdisk -l
Password:

Disk /dev/sda: 78.7 GB, 78732380160 bytes
255 heads, 63 sectors/track, 9572 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2   *           6        4240    34017637+   7  HPFS/NTFS
/dev/sda3            8966        9571     4867695   db  CP/M / CTOS / ...
/dev/sda4            4241        8965    37953562+  83  Linux

Partition table entries are not in disk order
gt@gt-laptop:~$ 


```

---

### Post by floke on 2007-02-28
Are the dell utility spaces on one partition or two separate ones?
The problem in creating a home directory is that you need to create a new partition (an extended partition, within which you can then put home and a swap file), but can have no more than four primary partitions - which it looks like you already have!
One option would be to do away with one of the Dell spaces: how much do you need them?

---

### Post by gtratter on 2007-02-28
Steve,
I am uncertain what they are for - they came pre-installed. I will do some reading up on it today and report back with the results.

---

### Post by gtratter on 2007-02-28
**Steve**

here is what I found about the Dell Restore partition....

*[INDENT]....that would like to do a fresh install of Windows are going to be surprised to find that you don’t get an Operating system CD like you used to. Dell instead includes a restore partition that takes up about 5GB of your drive. The partition is activated by pressing CTRL + F11 at boot. A DOS based program runs and installs your OS as new, bloatware and all. I have tested it and it does work. The restore partition has a huge Achilles heel though. If anything would happen to the Master Boot Record (MBR) your left with a system and no restore. You can’t alter the partition sizes in any way either and lastly they don’t give you a way to burn the Ghost image to DVD for safe keeping. Fortunately you can contact Dell and they will send you the OS and software CD’s. ......[/INDENT]*

I have all of the CD's, so I am not dependent on the restore partition. So, I think what I could do is, run the gparted live CD, shrink my / direcotry by 5 gig, increase the Restore partition by that amount, change the file type and make it a nice 10 GB  /home
Your thoughts?

---

### Post by floke on 2007-03-01
Yep, sounds good.
I had a problem when resizing, in that I could only resize (on Gparted) from left to right, and not from right to left , since data was stored on the partition from left to right (if this makes any sense) - so a bit like....

[XX    -- -- -- -- -  ] [XX  -- -- -- -- -    ] [XX -- -- - -- -         ]

(XX= data) would mean that I would be able to - eg. - delete the right hand partition and expand the middle one to the right, but I couldn't do it the other way around. I think you can actually move partitions though, but don't know how. Still, if you can create a 10G of consecutive space then you can certainly create a new ext3 partition there and use that.

Does this sound any good?

---

### Post by gtratter on 2007-03-01
Sounds good to me - I will do that today time permitting and will report back with the result

---

### Post by gtratter on 2007-03-01
**Steve**

- it is done - thank you for your guidance.
Here is what I did:
1. I used a live *gparted* CD to shrink my existing ext3 partition by 6 GiB
2. I then grew the Dell Restore partition to fill the gained space
3. Then changed the file format from NTFS to ext3
4. Applied all changes and exited the Live CD
5. Booted back into Ubuntu
6. Followed [ [COLOR="Red"]this great guide to create a sparate /home partition since I already had Ubuntu installed without one[/COLOR]]("http://www.psychocats.net/ubuntu/separatehome")
7. Now my file system looks like this
> 
Disk /dev/sda: 78.7 GB, 78732380160 bytes
255 heads, 63 sectors/track, 9572 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2   *           6        4240    34017637+   7  HPFS/NTFS
/dev/sda3            8201        9571    11012557+  83  Linux
/dev/sda4            4241        8200    31808700   83  Linux


8. and now all of my /home entries happily reside on their very own /home partition on sda3    :popcorn:

9. With this I leave WinXP alone for about 6 months and if I don't HAVE to use it during this time I will completely remove. In the meantime I have much to  learn about Linux and really look forward to it.

10. **Thanks to all who guided me through this decision!!!**

---

### Post by floke on 2007-03-01
Glad to hear it all worked out for you.
When (not if) you decide you ditch your XP partition, you could simply delete it, turn the space into an ext3, and test drive the latest version of ubuntu, which will be 7.10 by then. That way, you'll always have 2 separate OS (versions of ubuntu) on your system in case one of them gets borked. 

That's my plan anyway. Keep one cutting edge version and one 'stabler' one available in case it's needed. With the home partitions you don't have to worry about backing everything up and reloading it all.

Vive la Ubuntu!

---

### Post by gtratter on 2007-03-01
good plan - see you around the forums!

---

### Post by Toadmund on 2007-03-31
I like this idea of a separate partition for /home files.

Couple Q's:
Is the /home files saved on the boot partition *and* the separate home partition?
Does one have to export the home files manually to the separate /home partition?

When my feisty upgrade finishes, I will (grudgingly) go back to windows and try and free up another partition, to put another Ubuntu on it.

I am leaving windows too, but not deleting it yet, just giving it WAY less disk space (I need it for Linux now!
:guitar:

---

### Post by Trackieman on 2007-06-01
For a long time I had WinXP and Linux as a dual boot.
The partitions started as 25% Linux 75% Windows.
That value changed over time to whereby Windows XP had barely enough free space to boot!
Then I swapped my motherboard and graphics card for an entirely different chipset.
With just one line changed in /etc/X11/xorg.conf my Linux machine was working with the new hardware.
I knew Windows would not boot now and would blue screen with "Inaccessible boot device"
Not to mention the "Your hardware has changed significantly - reactivation required"

Ditch Windows, before it ditches you along with your data!

For me I'm finished with Microsoft Windows.

---

