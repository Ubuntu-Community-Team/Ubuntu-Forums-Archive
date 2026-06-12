---
title: "Ubuntu / Win8 dual boot help"
date: 2013-05-09
forum: Installation &amp; Upgrades
---

### Post by spenwah on 2013-05-09
This UEFI thing is kicking my ass, too.

This is a Toshiba Satellite S855D-S5148 which came preloaded with Windows 8.
Ubuntu Studio 13.04, 64bit
I installed from the live disc. The only thing strange I noticed was that it failed to find any other OS installed. I picked the third option of do something else, shrunk the big NTFS partition, created an ext3 for root, some swap, and a big FAT32 for shared media.
My Ubuntu Studio is running smoothly, but the Windows GRUB options don't do anything except complain "can't load image."
First there was only one option for Windows. After running boot-repair, now there are three apparent Windows options, but all lead to the same "can't load image" errors.
I ran boot-repair first from the installed Linux OS, then I tried again from a Live CD. Here is the pastebin URL from my most recent attempt.... many thanks in advance for your help!

[http://paste.ubuntu.com/5646830](http://paste.ubuntu.com/5646830)

---

### Post by mreyna16 on 2013-05-09
> **spenwah said:**
> This UEFI thing is kicking my ass, too.

This is a Toshiba Satellite S855D-S5148 which came preloaded with Windows 8.
Ubuntu Studio 13.04, 64bit
My Ubuntu Studio is running smoothly, but the Windows GRUB options don't go anywhere.
First there was only one option for Windows. After running boot-repair, now there are three apparent Windows options, but all lead to the same "can't load image" errors.
I ran boot-repair first from the installed Linux OS, then I tried again from a Live CD. Here is the pastebin URL from my most recent attempt.... many thanks in advance for your help!

[http://paste.ubuntu.com/5646830](http://paste.ubuntu.com/5646830)

I am having the same problem

If anyone can help,here is my URL from boot-repair: [Http://paste.ubuntu.com/5646729/](Http://paste.ubuntu.com/5646729/) 

@spenwah, not trying to steal your thread, I just thought there's no need to clutter the forum with the same problem. If you feel theres a problem, simply let me know and ill edit my post and create a new thread.


EDIT: Both Windows 8 and Ubuntu are UEFI installations

---

### Post by amahi on 2013-05-09
hey 

I just used this tutorial 

[https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition)

it works perfect now!

---

### Post by mreyna16 on 2013-05-09
> **amahi said:**
> hey 

I just used this tutorial 

[https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition)

it works perfect now!

got stuck on step 4, cant shrink my partition where ubuntu is

---

### Post by oldfred on 2013-05-09
@spenwah
Line 97 of [BootInfo]("http://ubuntuforums.org/BootInfo.html")
Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1           2,048       923,647       921,600 Windows Recovery Environment (Windows)
/dev/sda2         923,648     1,456,127       532,480 [COLOR=#ff0000]EFI System partition[/COLOR]
/dev/sda3       1,456,128     1,718,271       262,144 Microsoft Reserved Partition (Windows)
/dev/sda4       1,718,272   759,833,506   758,115,235 [COLOR=#ff0000]EFI System partition[/COLOR]

We are trying to fix a bug we think is in Boot-Repair. You can only have one EFI partition. But the rules on boot flags are different for UEFI/gpt and BIOS/MBR. With gpt partitioning you can only have one boot flag on the efi partition (your sda2). With BIOS/MBR you have the boot flag on the Windows partition with the boot files (your sda4). 
You actually have both which is wrong. 
Did you boot Boot-Repair in BIOS mode from UEFI menu and not check that it was an efi install? It did the repair as if it was a BIOS Windows install and installed a Windows boot loader to the MBR and put a boot flag on the Windows partition sda4. But with gpt partitioning, Windows can only boot with UEFI, and with gpt the boot flag can only be on the efi partition. Actually the boot flag is what gparted uses to make a partition an efi partition.

So use gparted from Ubuntu liveCD/DVD/Flash and click on sda4, then right click manage flags and remove boot flag from sda4. 
Then see if you can boot from UEFI menu with either secure boot on or secure boot off.

      
 Two efi partitions bug
[https://bugs.launchpad.net/boot-repair/+bug/1177474](https://bugs.launchpad.net/boot-repair/+bug/1177474)

---

### Post by spenwah on 2013-05-09
oldfred!
Many thanks for your quick fix. I am a dual-booter again and my stress level has lowered considerably.
As to your questions.... no, I don't think so. I did look at the BIOS screen to see that it booted in UEFI, but I'm 95% sure that I didn't change anything there before trying the install...
I ran Boot Repair once, with default settings, from the installed OS (the notification about UEFI popped up, I remember); this added two more options to the GRUB menu but didn't fix the nonbooting problem. I was following conflicting pieces of advice at first; another thread suggested I should go to advance options and check to "Restore MBR." I tried this, again from the installed OS, with no change in symptoms. Then I found more advice saying that I needed to do Boot Repair from a live disc OS. So, I tried again a third time, from the live CD using all defaults "Recommended Repair." Again, no change in symptoms. It was this third run of Boot Repair that generated the log you were kind enough to review for me. I hope this extra information is helpful for you! Now my only (very minor) annoyance is that there are two extraneous Windows boot options in my GRUB that just lead to error screens.

Amahi:
Thanks for the tip, it was a useful read. But the laptop I am on already has several small partitions right at the front of the hard disc, and I was too nervous about messing up my new machine even more to attempt any of the suggestions there.

I marked this thread as SOLVED, but I guess we shall see if mreyna16 still has issues.

---

### Post by oldfred on 2013-05-09
Glad that worked.

If you want to turn off os-prober you can, until they fix that with grub. And all the entries in 25_custom are from Boot-Repair, so if you only want some you can delete (backup first) extra entries. If you backup be sure to turn off execute bit as otherwise grub will run the backup also creating duplicates. It runs any two number with _ files with execute bit on, so I changed my backup suggestion to but bkup at start of file, so it not think it will run.

 # I add this line to grub configuration or turn off the execute bit on 30_os-prober
gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER=true
or turn off executable bit
sudo chmod a-x /etc/grub.d/30_os-prober
# Then do:
sudo update-grub
Or one liner
 sudo echo GRUB_DISABLE_OS_PROBER=true >> /etc/default/grub 
sudo update-grub

   sudo cp -a /etc/grub.d/25_custom /etc/grub.d/bkup25_custom
gksudo gedit /etc/grub.d/25_custom
Then do:
sudo update-grub

---

### Post by amahi on 2013-05-09
Glad that worked,too.
;)

---

### Post by mreyna16 on 2013-05-09
> **spenwah said:**
> oldfred!
Many thanks for your quick fix. I am a dual-booter again and my stress level has lowered considerably.
As to your questions.... no, I don't think so. I did look at the BIOS screen to see that it booted in UEFI, but I'm 95% sure that I didn't change anything there before trying the install...
I ran Boot Repair once, with default settings, from the installed OS (the notification about UEFI popped up, I remember); this added two more options to the GRUB menu but didn't fix the nonbooting problem. I was following conflicting pieces of advice at first; another thread suggested I should go to advance options and check to "Restore MBR." I tried this, again from the installed OS, with no change in symptoms. Then I found more advice saying that I needed to do Boot Repair from a live disc OS. So, I tried again a third time, from the live CD using all defaults "Recommended Repair." Again, no change in symptoms. It was this third run of Boot Repair that generated the log you were kind enough to review for me. I hope this extra information is helpful for you! Now my only (very minor) annoyance is that there are two extraneous Windows boot options in my GRUB that just lead to error screens.

Amahi:
Thanks for the tip, it was a useful read. But the laptop I am on already has several small partitions right at the front of the hard disc, and I was too nervous about messing up my new machine even more to attempt any of the suggestions there.

I marked this thread as SOLVED, but I guess we shall see if mreyna16 still has issues.

does the fix you did also apply to me? i dont wanna mess anything up on my end lol

---

### Post by mreyna16 on 2013-05-09
well ive been trying different tutorials and running boot-repair a cpl of times now so i decided to run it again and post the new link it gives me see if somebody can help...

[http://paste.ubuntu.com/5649050/](http://paste.ubuntu.com/5649050/)

---

### Post by oldfred on 2013-05-09
@mreyna16
Yours is more complicated. 
You have an UltraBook with uses RAID for the SSD or Intel SRT. But it looks like grub has installed in efi partition. Are you able to boot to grub menu? 
All UltraBooks also have dual video which has its own issues. You can use Bumblebee once installed. nVidia just released a new driver that offers some support but may need next Linux kernel in 13.10 and may not work for all things.
Can you set in UEFI to only use Intel or nVidia to boot? Some have settings for that.

May be better to start your own thread.

---

### Post by mreyna16 on 2013-05-09
> **oldfred said:**
> @mreyna16
Yours is more complicated. 
You have an UltraBook with uses RAID for the SSD or Intel SRT. But it looks like grub has installed in efi partition. Are you able to boot to grub menu? 
All UltraBooks also have dual video which has its own issues. You can use Bumblebee once installed. nVidia just released a new driver that offers some support but may need next Linux kernel in 13.10 and may not work for all things.
Can you set in UEFI to only use Intel or nVidia to boot? Some have settings for that.

May be better to start your own thread.

thanks for the reply oldfred

yes im able to load grub and i have about 3 entries for windows (need to check how they are listed in grub) and none let me boot into windows... sorry i am a noob but what is bumblebee? and ill try your advice and start a new thread

---

