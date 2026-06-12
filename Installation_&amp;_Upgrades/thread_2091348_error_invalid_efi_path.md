---
title: "error: invalid efi path"
date: 2012-12-04
forum: Installation &amp; Upgrades
---

### Post by acidreign on 2012-12-04
Yet another of the same error I've seen on this forum many times. All other solutions have not worked for me.

I initially had Windows 7 installed on a SSD. Then I installed a separate drive, put 12.10 on it, and suddenly I cannot boot into Windows and get this error: invalid efi path.

My motherboard is an Asus P9X79 with the most current bios.

As of right now I've tried the latest version of boot-repair (recommended repair) and it hasn't helped.

Here is my boot info (newest first):
[http://paste.ubuntu.com/1411687](http://paste.ubuntu.com/1411687)
[http://paste.ubuntu.com/1411620](http://paste.ubuntu.com/1411620)
[http://paste.ubuntu.com/1393550](http://paste.ubuntu.com/1393550)

I've been to launchpad and marked myself as affected by bug #1024383.

Please, anyone... I miss my games. :) I'm open to any suggestion.

Thank you!

---

### Post by oldfred on 2012-12-05
I do not think you can mix BIOS and UEFI.

You have Windows in BIOS boot mode in sda and Ubuntu in UEFI boot mode in sdb. I think BIOS or UEFI do write some info that when booting is expected in certain places on hard drive. So trying to chain from an efi Ubuntu install to a BIOS Windows install, then Windows cannot find the BIOS data.

From BIOS/UEFI you should be able to boot Windows in BIOS mode or from UEFI boot Ubuntu but you have to switch from UEFI to legacy/BIOS/AHCI or whatevery your system calls it every time.

At this point probably easiest just to reinstall Ubuntu in BIOS mode. You can use gpt with Ubuntu in BIOS mode but it will need (and I think it creates) a bios_grub partition. To install in BIOS mode you have to boot installer in BIOS mode. Windows only boots from gpt drives with UEFI, but Ubuntu works either way.

---

### Post by YannBuntu on 2012-12-05
> **oldfred said:**
> At this point probably easiest just to reinstall Ubuntu in BIOS mode.

+1
IMHO the easiest way here is to:
1) via Gparted, format the sdb1 partition. In the free space, create a BIOS-Boot partition ( see [https://help.ubuntu.com/community/DiskSpace#BIOS-Boot_or_EFI_partition_.28required_on_GPT_disks.29](https://help.ubuntu.com/community/DiskSpace#BIOS-Boot_or_EFI_partition_.28required_on_GPT_disks.29) )
2) Use Boot-Repair's Recommended Repair. (It should convert your Ubuntu into Legacy mode.) Indicate us the new URL that will appear.
3) reboot the computer and tell us what you observe.

---

### Post by oldfred on 2012-12-05
Thanks Yann, I knew Boot-Repair could convert a BIOS install to UEFI, but did not know it could do the reverse.

I use the bios_grub partition as I only have BIOS but use gpt. I only needs to be 1MB and has to be unformatted. Then grub-pc will install correctly. 

In UEFI mode you use grub-efi and in BIOS mode you use grub-pc but the Ubuntu install is identical.

---

### Post by acidreign on 2012-12-05
Awesome, thanks Yann & oldfred for both of your replies.

I'm gonna attack this in about an hour and I'll be sure to reply with the results. Fingers crossed!

---

### Post by acidreign on 2012-12-06
Well... it worked!

I pretty much followed the instructions given and they were spot on. I can now boot into both Windows 7 and Ubuntu.

One small annoyance is when booting into Ubuntu I get this message:

"The disk drive for /boot/efi is not ready yet or not present.
Press S to skip or M for manual recovery"

Pressing S works fine and Ubuntu continues to load. But I'd rather not have to do this each time.

Here is my updated boot info: paste.ubuntu.com/1416156

Thanks so much guys, you saved me hours!

---

### Post by oldfred on 2012-12-06
It may be related to this:
> 
/dev/sda1 ends after the last sector of /dev/sda 

Now that is from the protective MBR of sda, not the gpt table which is ok. So the protective MBR is only used to show tools like fdisk that are not updated to gpt to see that the drive is used. 

Download from repository and run gdisk. Sometimes it auto repairs things.

sudo apt-get install gdisk

       sudo gdisk -l /dev/sda
    
       repair gpt:
[http://www.rodsbooks.com/gdisk/repairing.html](http://www.rodsbooks.com/gdisk/repairing.html)

    
Not sure if gdisk will update protective MBR or not?

---

### Post by YannBuntu on 2012-12-07
Hi
> **acidreign said:**
> "The disk drive for /boot/efi is not ready yet or not present.

That is because Boot-Repair didn't manage to comment the /boot/efi line in your fstab.
I just uploaded a fix in the PPA (boot-sav 3.195~ppa27).
You can fix this issue manually, or by updating Boot-Repair then use Recommended Repair.

---

### Post by acidreign on 2012-12-10
Cool, you guys are infinitely helpful. I'll comment that line later tonight when I have time.


I should probably also mention for anyone reading this who might have the same issue: I had to disable "quick boot" in my bios for the initial fix to work. Even now, if I re-enable it - nothing works!

---

### Post by YannBuntu on 2012-12-10
> **acidreign said:**
> I had to disable "quick boot" in my bios for the initial fix to work. Even now, if I re-enable it - nothing works!

Thanks for the feedback!

---

### Post by hamiltonpb on 2013-01-13
> **YannBuntu said:**
> +1
IMHO the easiest way here is to:
1) via Gparted, format the sdb1 partition. In the free space, create a BIOS-Boot partition ( see [https://help.ubuntu.com/community/DiskSpace#BIOS-Boot_or_EFI_partition_.28required_on_GPT_disks.29](https://help.ubuntu.com/community/DiskSpace#BIOS-Boot_or_EFI_partition_.28required_on_GPT_disks.29) )
2) Use Boot-Repair's Recommended Repair. (It should convert your Ubuntu into Legacy mode.) Indicate us the new URL that will appear.
3) reboot the computer and tell us what you observe.

I had Windows 7 pre-installed in my laptop. (So, I do not have any recovery DVD). When trying to install Ubuntu 12.10 somehow my bootloader went broken. I've tried to use Boot-repair's recommended repair. However, it didn't find sda7 after I wrote the instruction on terminal. [http://paste.ubuntu.com/1529385/](http://paste.ubuntu.com/1529385/) 
So, I am able to boot neither Windows 7 nor Ubuntu. 

Any suggestion?

---

### Post by YannBuntu on 2013-01-13
@hamiltonpb: welcome among us! please create your own thread, so that we don't mix everything, and you get better help.

---

### Post by AdamTudor on 2013-04-30
To acid reign

if you a still reading this thread, ........

I'm  a windows user planning to switch to Ubuntu 

my knowledge level , plan to buy a new workhorse windows laptop and fears on dual boot etc are expressed here 
[http://ubuntuforums.org/showthread.php?t=2140574&p=12626203#post12626203](http://ubuntuforums.org/showthread.php?t=2140574&p=12626203#post12626203)

could you please give a step by step instruction on 
a. **How to identify** ; How does one know that his laptop is UEFI or some such scary four letter thingy and not the easy BIOS which just allows you to flick a function key and start a dual boot ? 
B. **what to do** : once identified a step by step instruction list on what to do  ?
c. The exchange above is all interesting but not a step by step for a novice like me ...so please help 


thanks in advance 

--------
regards

---

