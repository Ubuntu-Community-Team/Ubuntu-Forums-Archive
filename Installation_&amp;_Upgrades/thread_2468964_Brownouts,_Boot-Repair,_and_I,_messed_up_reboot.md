---
title: "Brownouts, Boot-Repair, and I, messed up reboot"
date: 2021-11-15
forum: Installation &amp; Upgrades
---

### Post by 5circles on 2021-11-15
I'm in a hiatus cause by other business activities taking precedence - with a multi partition system (multiple Ubuntu versions, plus windows 8 - I think - from the original system).  The goal is to have 18.04 and 20.04 able to boot and use a single /data partition to make things easier when I move to 22.04 in a few months.

I've had help in another thread [https://ubuntuforums.org/showthread.php?t=2468446](https://ubuntuforums.org/showthread.php?t=2468446) and have the /data partition working in part.  Then I tried to have a single copy of MySql data.  More advice on the other thread, and I changed plans - at least temporarily - to mainly boot to 18.04 and use that for MySQL because the internal blog posts are critical.  I used Grub Customizer to make that work, with the default OS as 18.04 on /dev/sda8.  That worked fine for a week or two.

The problem for this post started with brownouts.  When I was able to reboot, the system booted from the Windows partition.  I then did some things without researching properly, including changing the boot from UEFI to Legacy.  

Next, I booted from a live 18.04 Ubuntu USB, and ran boot-repair.  I don't think I did everything properly (almost certainly didn't switch back to UEFI until later), but what I documented was that entries seen when booting didn't have a match between the text and the real partition.  I realized that I hadn't done things correctly, switched back to UEFI, and reran boot-repair from either 18.04 or 20.04.  I was able to reboot consistently to the desired version, although the text to partition map was still odd.  I planned to investigate properly when the other tasks were no longer higher priority.  That happened this morning, just before more brownouts, then a power outage.  The office is on generator power, waiting for power restoration.

When I restarted after the generator came on line, the system booted from a different partition and came up in Ubuntu 14.04.  I also have two versions of 16.04 on the drive.  The inconsistency between the text and the partitions still exists.  Not sure, but it looks to me like some of what I'm seeing is because partitions were manipulated after the first usage of that version of Ubuntu, and that changes made by boot-repair and/or Grub Customizer have not been propagated to different bootable partitions.  I could be totally wrong.  As can be seen from the above, thinking straight doesn't seem to be what I've been doing.

I'm looking for help with the best approach going forward, if possible someway to avoid brownouts causing future issues.

Here is the output from os-prober, run from Ubuntu 18.04 on /dev/sda8.

sudo os-prober
/dev/sda1@/EFI/Microsoft/Boot/bootmgfw.efi:Windows Boot Manager:Windows:efi
/dev/sda10:Ubuntu 16.04.3 LTS (16.04):Ubuntu:linux
/dev/sda11:Ubuntu 16.04.4 LTS (16.04):Ubuntu1:linux
/dev/sda12:Ubuntu 20.04.3 LTS (20.04):Ubuntu2:linux
/dev/sda7:Ubuntu 14.04.5 LTS (14.04):Ubuntu3:linux

Thanks!

---

### Post by ActionParsnip on 2021-11-16
If power is flakey then I can suggest you buy a UPS for your system(s). End user systems should be laptop based as they have a battery as well

---

### Post by yancek on 2021-11-16
>   I then did some things without researching properly, including changing the boot from UEFI to Legacy.  

Sorry, but that was a bad idea and I can't imagine any reliable source suggesting that.

Where did 14.04 come into the picture?  I'm sure you are aware it has not been supported for 2 years?  In any case, since you already have boot repair, you should run it with the Create BootInfo Summary option and post the link output you get when it finishes here at the forums.  There are a number of members here who are very familiar with boot repair and its contents and should be able to help.  

>  /dev/sda1@/EFI/Microsoft/Boot/bootmgfw.efi:Windows Boot Manager:Windows:efi 

The quote above shows definitively that your windows is an EFI install.  Running boot repair should show if any of your Ubuntu installs are EFI installs and which are if any.

---

### Post by TheFu on 2021-11-16
Get a UPS.
Computers, especially servers, don't like having the power unplugged at random.
Why are so many out of support systems still installed?  I'd clean up those. Don't leave unused junk connected.

If you used virtualization, none of these booting issues would happen, BTW. There's be 1 OS physically on the hardware and all the others would be virtual machines.

---

### Post by 5circles on 2021-11-16
Thanks for the advice.

Yes, a UPS is an essential.  I haven't had one for a while, and there have been very few issues since I moved. So I just had it as low priority and became complacent, and now we are entering storm season.  The old saying about buying a generator means it won't be needed was pretty true at the old place.  Not true here.

Old OS versions.  I'm in process of cleaning up, but it's taking too long.  I have the old versions still on the drive because I haven't consolidated all data yet - on the Ubuntu server and the separate NAS.  14.04, 16.04 (both) should not be active.

Virtualization to help with transition.  Sure, but again I'm time limited.

What I really wanted to know was how to clear up for booting, and if that would be just a band-aid or a long term answer.
[LIST]
[*]Can I run grub-customizer from the 18.04 boot and do that right?
[LIST]
[*]Eliminate all entries other than 18.04, 20.04, and Windows
[*]Set default to be 18.04 or the last OS booted?
[/LIST]
[*]Do I have to repeat using grub-customizer on 20.04? 
[*]Or, what's the best way to build an new grub.cfg from scratch and then save to MBR?  Assuming that's a good approach to clean up?
[/LIST]

Is there something about brownouts that might cause starting the wrong OS to happen anyway?  In other words, am I still at risk until I get a UPS?  I know there are risks anyway, but the risk of a brownout causing the wrong OS to start, or power cycling / after outage causing the wrong OS to start?

---

### Post by TheFu on 2021-11-16
I've never used grub-customizer.  Does it even work with UEFI booting?
18.04 shouldn't be deployed to any new systems at this point. Bite the bullet and start with 20.04.  Sooner or later, that will happen and 22.04 shouldn't be used in production until late July-August next year.

Any electric power interruption is hard on computers.  Under-volting equipment is bad.

We don't know what this stuff is for. 
If this is just a home setup - do whatever you want.
If this is related to any business needs, then do it right. Get a UPS and clean up the extra OS junk ASAP.  Every OS removed is one less to be confused or deal with at boot time.

Being time-limited often means people skip learning the core things that would make them more efficient every day later.  Do you script installs? Do you save off the steps when you did a manual install and can reproduce it for the next year or two?  Do you have devops tool skillz that will make setup of a system 15 min or less?

---

### Post by grahammechanical on 2021-11-16
You are asking too many questions and giving too much history. First, be clear in your mind what you want to do. Write it down as a list of headings then then expand each heading with its own needed actions to complete your purpose.

From what you have written you have not completed backing up data that you want to keep. You seem to have only one hard drive. Create space for a Data partition and in that data partition create folders and in those folders stuff everything from the various home folders of the various installations that you want to keep and start deleting the installations you do not need.

You only need to keep 20.04. As you work save stuff to the data partition.

It is not easy, I know that. I am not a disciplined worker myself. I have two drives and multiple installs of Linux. With a common Data drive I have two installs of Ubuntu I can work from should my usual Ubuntu break. As regards the other installs of Linux they are there for curiosity and I make sure I do not keep useful data in them. In this way I have no problem removing installations and re-partitioning the drives.

Regards

---

### Post by 5circles on 2021-11-16
Thanks @GrahamMechanical.  

Yes, perhaps too much history.  I did that because the bigger picture involves a lot of consolidation, with too many almost copies on multiple systems (including a new NAS).  Maybe that's not all that relevant, but there are multiple drives including in the Ubuntu system (one destined for the NAS), external, in docks, but not enough spare space until consolidation gets farther along.  That's why I need a reliable Ubuntu system to do some of the juggling and continue my internal documentation for this and other projects.  And that's why I'll stick with 18.04 as the main OS until I have time to investigate virtualization for MySQL (or MariaDB). or just migrate all the databases to 20.04.  I don't usually take this long to move to a later Ubuntu version (the next one within sight), and yes, I wait until a few months after .04 to let things settle down.  Again, TMI - sorry.

What I want (to achieve and help with), seems fairly straightforward.

1. Reliable booting to 18.04 (assuming no brownouts before I deal with power issues), and if possible to 20.04 under the "default = last OS booted" setting.  I think I've got that working now.
2. Overcome brownout issues with UPS.  That's on me, and is what I'll be doing later this evening.  If anyone has links to offer for choosing UPS that would be great - it's been a long time - but I'm not expecting it.  It's probably TMI, but the outages yesterday were very severe in the US Pacific Northwest, and I think that booting to 14.04 / the option in Grub - happened as a result of the power issues.
3. In case I didn't make this clear, I would also like to know if there is a way to rebuild the grub configuration and the resulting MBR from the ground up - whether it's by using Grub Customizer or CLI tools.  I think I'll be evaluating the system after power issues and consolidation are sorted out, and at a minimum getting a new drive.  In any case, a cleaned up system is appropriate.

Mike
'

---

### Post by TheFu on 2021-11-17
If the outdated 14.04 **WAS NOT** ON THE SYSTEM, then it couldn't be accidentally booted.

The way to get a new grub setup is to wipe the HDD/SSD - only have 1 connected - and perform a fresh install.  Having 1 OS on the system is THE answer. Then you can put all the other OSes into virtual machines.  I've outlined, in a few threads here, how to restore backups (or just take the relevant information from prior installs) to achieve that.  The only trick is that you need to boot into each install and dump the manually installed packages/snaps to text.  **apt-mark showmanual**  is the command for APT and **snap list** is the command for snaps, but there should only be 1-5 of those. Ensure those files with the lists can be accessed along with the data and configs for the OS/users.

[Https://ubuntuforums.org/showthread.php?t=2389631&p=13757986#post13757986](Https://ubuntuforums.org/showthread.php?t=2389631&p=13757986#post13757986) is about restores. It works.

---

### Post by 5circles on 2021-11-18
Thanks @TheFu - for the advice in your direct reply, and also the post about backup and restores.  I'll be looking at that when I get past a few other steps - first is the UPS.  There are still many people without power after one of the worst storms in memory, so thanks to the forum for (forceful) advice.

FYI, 14.04 _was_ on a partition, but it wasn't in the grub.cfg that should have been in effect.  That's not the case now after boot-repair, and only doing partial clean up with grub-customizer.

---

### Post by TheFu on 2021-11-18
Be very careful using boot-repair with UEFI setups. It can cause more boot problems.

If you don't want an OS to be booted, but still want to keep it around (why, I don't know), create a directory in the / **of the partition **and move everything under that.  Or just move it to storage that can be disconnected.  The key is to not allow /boot or /etc or /boot/efi to be found in the expected placed on any partition that you don't want to boot.

---

