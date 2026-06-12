---
title: "Delete Ubuntu 14.X on dual-boot laptop"
date: 2016-10-05
forum: Installation &amp; Upgrades
---

### Post by Malmberg on 2016-10-05
Hi Experts,

I have a laptop with Ubuntu 16.x AND 14.X installed - and I would like to delete Ubuntu 14.x - is there a safe way?

History goes as follows:
Some weeks ago there was an update for V16.x - I did that, and rebooted my old (very, very old) laptop as suggested.
Left the laptop to go and get a cup of coffee. When I came back the fan was going mental and after a while the machine shut down.
I then thought: " *WHAT the xxxx happened here? - what was in that update? - how do I roll back?*"

Anyhow I panicked, I did a lot of searching for issues regarding the update, but could not find anything!
I was so clever that I had NOT a backup of two documents I should use for work.
So I installed V14.X along v16.X - same story - Booting/Mental fan/Shut down.

OK - so late (too late) I ran "Sensors" - and the temperatures was rising as a frying pan.
Off cause: The heat-pipe for the GPU died during my update of v16.x.

Got a new heat-pipe - Und alles in ordnung!

Now I would like to uninstall v14.x - Is this possible??

Many Thanks in advance.

---

### Post by TheFu on 2016-10-05
If they are in different partitions, just delete the 14.04 main partition.  If there is UEFI, don't touch that partition. Also, don't touch the /home partition.

Really, it depends on how you really installed the stuff - can't tell from what has been written above.  The output from **sudo parted -l** would be helpful. Please use *code tags* when posting so it is readable.

---

### Post by Bucky Ball on 2016-10-05
For an even better idea of what you have there you could try running the [boot info script]("http://bootinfoscript.sourceforge.net/"). Post the output between [code] tags (see the green link in my signature at the bottom of this post).

---

### Post by Malmberg on 2016-10-05
> **Bucky Ball said:**
> For an even better idea of what you have there you could try running the [boot info script]("http://bootinfoscript.sourceforge.net/"). Post the output between ```
 tags (see the green link in my signature at the bottom of this post).

Thanks!

Is this enough from the txt file?

Your help is so appreciated!!!

[CODE]
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 97 for .

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 16.04.1 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 14.04.5 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________
Disk /dev/sda: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   514,841,652   514,839,605  83 Linux
/dev/sda2         514,842,622   976,771,071   461,928,450   5 Extended
/dev/sda5         972,582,912   976,771,071     4,188,160  82 Linux swap / Solaris
/dev/sda6         514,842,624   972,582,911   457,740,288  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        5b79830f-974a-41b3-98eb-83e09e15aa17   ext4       
/dev/sda5        a1f0645e-c819-4ec3-b6a1-d731a59fc30b   swap       
/dev/sda6        1b00613e-5edb-4729-809b-04874cf28a8c   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,relatime,errors=remount-ro,data=ordered)


=========================== sda1/boot/grub/grub.cfg: ===========================

```

---

### Post by Malmberg on 2016-10-05
> **TheFu said:**
> If they are in different partitions, just delete the 14.04 main partition.  If there is UEFI, don't touch that partition. Also, don't touch the /home partition.

Really, it depends on how you really installed the stuff - can't tell from what has been written above.  The output from **sudo parted -l** would be helpful. Please use *code tags* when posting so it is readable.

Hi TheFu - thanks!

---

### Post by TheFu on 2016-10-05
You can delete sda6 if you don't need any of those files - is the /home inside there or did you create a new /home for 16.04?

Then you can just always boot into 16.04 with no bad results expected.  Eventually, there will be a something that runs update-grub and the 14.04 menu will be removed. If you like, run **sudo grub-update** and it should be removed.

Do all of this booted into the 16.04 instance.

Then you can decide what you'd like to do with the open space. If you don't need it now, I wouldn't do anything.

---

### Post by Malmberg on 2016-10-05
Hi TheFu

Yes - I did create a new /home for 14.X?

Cheers

---

### Post by Bucky Ball on 2016-10-05
So, if 16.04 has its own /home, then I would *back up anything you don't want to lose before proceeding*. :)

Then I'd open Gparted (install if not installed already), launch it and right click the /swap and choose /swapoff. Right click sda6 and unmount.

Then I'd delete sda5 and sda6 and then create a data partition in the free space leaving 2Gb free at the end of the extended partition (if that takes up the whole drive) to recreate the /swap partition. 2Gb is all you need.

Hope that helps and good luck.

PS: Before you do any of this, I'd make absolutely sure you have grub controlled by the 16.04 install. If that was installed last that should be the case. Once you've deleted the 14.04 you should boot to 16.04 and open a terminal then:

```
sudo update-grub
```

That will clean up grub and get rid of 14.04 entries.

(Just realised TheFu had mentioned this already. Ninja-ed! :))

---

### Post by TheFu on 2016-10-06
I'm a believer in 4G swap.  On low-RAM systems, 2G just isn't enough. I've been burned and think it is due to modern, bloated, browsers using 2G by themselves.  This assumes there isn't any hibernation going on. If there is, swap needs to be a tiny bit larger than RAM, but besides that 4G swap seems to be the optimal for 2G - 32G desktop systems.

Servers are different. Those should have the RAM tuned so 0 swap is needed.  Gotta know the workload.

---

### Post by Malmberg on 2016-10-06
> **Bucky Ball said:**
> So, if 16.04 has its own /home, then I would *back up anything you don't want to lose before proceeding*. :)



PS: Before you do any of this, I'd make absolutely sure you have grub controlled by the 16.04 install. If that was installed last that should be the case. Once you've deleted the 14.04 you should boot to 16.04 and open a terminal then:


(Just realised TheFu had mentioned this already. Ninja-ed! :))

Hi Sir,

Thanks so much!

16.04 was installed FIRST - 14.x last!
Is this vital??

Cheers

---

### Post by Bucky Ball on 2016-10-06
Boot into 16.04 and run the command I gave, then:

```
sudo update-grub
```

That should give 16.04 control of the grub so when you get rid of 14.04 you won't have to mess with getting it to boot. If you leave 14.04 with control of the grub and you remove it you will need to fiddle about getting 16.04 to boot.

---

### Post by Malmberg on 2016-10-06
> **Bucky Ball said:**
> Boot into 16.04 and run the command I gave, then:

```
sudo update-grub
```

That should give 16.04 control of the grub so when you get rid of 14.04 you won't have to mess with getting it to boot. If you leave 14.04 with control of the grub and you remove it you will need to fiddle about getting 16.04 to boot.

Okay - just to be Dxxx sure - its this you mean by command:

[I]Then I'd open Gparted (install if not installed already), launch it and  right click the /swap and choose /swapoff. Right click sda6 and unmount.

Then I'd delete sda5 and sda6 and then create a data partition in the  free space leaving 2Gb free at the end of the extended partition (if  that takes up the whole drive) to recreate the /swap partition. 2Gb is  all you need.[/I]

Remember I'm so new to this :-)

---

### Post by TheFu on 2016-10-06
There is no single, best, answer at this point. It is opinion.  Bucky's opinion is good, but we have different experiences which lead to different recommendations.
You can screw with the swap later.  You can remove sda6, sda5, and sda2 later ... then resize or add partitions for a new, larger, /home/ that appears to be inside sda1.

We both agree you need to boot into 16.04 and do all this work.  The resize of sda1 is the only thing that cannot happen while booted there.  We both agree that gparted is the easiest tool to use as well.

Really the only thing we have different experiences about is the best, minimal size of the swap file for a desktop system.  2G can lead to issues. I've seen this.  4G seems to solve the issue. If you have 4G or less RAM, be very careful using a smaller swap.  Just sayin'.

---

### Post by Bucky Ball on 2016-10-06
As TheFu says, but I think what you're asking *me* about specifically is the 'command'. Do this now.

Boot to 16.04
Open a terminal
Run this _***command***_

```
sudo update-grub
```

Close the terminal and proceed to delete 14.04.

---

### Post by Malmberg on 2016-10-06
Heureka!!!!!!

@ Bucky Ball
@ TheFu

- I did as you said, and I now have a Laptop with only on OS = 16.04 / 4GB Swap - its alive and kicking - many, many thanks!!

PS: I think the boot time is substantively longer than it use to be! - but, I can easily live with it, laptop is back!

PPS: do you know a way to solve the problem with the issue that WiFi dies after a while?
I do know that&#8217;s its a common issue :D

---

### Post by Bucky Ball on 2016-10-06
> **Malmberg said:**
> 
PPS: do you know a way to solve the problem with the issue that WiFi dies after a while?
I do know that&#8217;s its a common issue :D

Please post another thread about that in [Networking and Wireless]("https://ubuntuforums.org/forumdisplay.php?f=336") as not related to this or the title of the thread. Try and post as much relevant info as possible for best effect. Please mark this one as 'solved' using 'Thread Tools' at top right or follow the link in my signature for how.

Open a terminal and:

```
sudo update-grub
```

Reboot. That may speed up the boot. 

Good news you got it happening, good job, and no probs. :)

---

