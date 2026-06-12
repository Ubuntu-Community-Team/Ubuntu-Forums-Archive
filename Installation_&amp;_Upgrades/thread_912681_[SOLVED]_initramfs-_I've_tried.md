---
title: "[SOLVED] initramfs- I've tried"
date: 2008-09-07
forum: Installation &amp; Upgrades
---

### Post by fewjr on 2008-09-07
Hello All,
     I built a new from scratch computer and have been trying to install Ubuntu 8.04 Hardy Heron. I have it on an older computer and have been getting to like it alot. When I click on install Ubuntu I get this message:

BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)

I researched the forum as best I could for a couple of hours and found a few things to try. What I ended up doing was going to F6 and removing 'quiet splash' or whatever that is called and adding 'all_generic_ide' to the end of the command line. This is after I tryed to install in all three SATA modes that are available in my BIOS (IDE, AHCI & RAID). The appended command did the trick for letting it install. I had set it back to ide in the BIOS and it formatted the 1st drive and installed with no problem until reboot. When reboot was done I ended back to the same end as before:

BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)

Has anyone figured out what the deal is with SATA drives and Hardy Heron? I wanted to do fakeraid, but thats another question I'll save for later. My new system is as follows:

Gigabyte GA-M78SM-S2H AM2+/AM2 nVidia GeForce 8200 motherboard  

AMD Athlon 64 X2 5000+ Brisbane 2.6GHz Dualcore processor

4GB G.Skill DDR2 800 (PC2 6400) Dual Channel RAM

2- Hitachi Deskstar P7K500- 500 GB SATA harddrives

Sony Optiarc DVDROM and Pioneer DVDR Burner master & slave 
on Primary IDE Channel (only IDE Channel)

USB Card reader in floppy bay
 
                                        Thanks in Advance,
                                             fewjr

---

### Post by kentbower on 2008-09-07
My situation was different, since I successfully installed ubuntu before having the initramfs prompt problem, but it might be worth a try.
 
In WinXP, have you tried this? :

**chkdsk c: /f**

(you may need to 'schedule' the chkdsk and reboot windows)

That finally fixed my initramfs problem that happened after my laptop ran out of battery while ubuntu was running.

I was getting:
ALERT! /host/ubuntu/disk/root.disk does not exist

and then the 

initramfs_ prompt

---

### Post by epidemiks on 2008-09-08
> **fewjr said:**
>  What I ended up doing was going to F6 and removing 'quiet splash' or whatever that is called and adding 'all_generic_ide' to the end of the command line. 

...

Has anyone figured out what the deal is with SATA drives and Hardy Heron? 

I had major headaches with the initramfs/busybox after upgrading 7.10 to 8.04, so much so, that I gave up for 3 months!

When I managed to drum up the strength to try again it was really simple.

For my system, I firstly removed the original drive ubuntu was on, and added "all_generic_ide floppy=off irqpoll" to the install line (and then in grub after installation). 
Now, I know I tried the boot options previously, but hadn't tried a different hard disk & with the problem drive (IDE by the way) out of the system, everything ran like a dream.. 

so, I'd advise trying those other boot options, and trying the install with just one drive - remove the other while trying the install and switch if the first fails.. it may be one of those disks is faulty?
Good luck!

---

### Post by fewjr on 2008-09-08
> For my system, I firstly removed the original drive ubuntu was on, and added "all_generic_ide floppy=off irqpoll" to the install line (and then in grub after installation). 

     I didn't do anything to Grub yet. As I stated before I was able to install to my 1st SATA drive after I added 'all_generic_ide', only to end back up at Busybox/initramfs after I was instructed to remove cd from drive and reboot. Could it be that Grub needs to be configured also to see the boot drive. I have no idea how I would do that when I can't boot into OS. Maybe I could try as you say to remove one of the SATA HDs and install again. Thank you. Is there maybe any more suggestions out there. I'm a little perplexed.

---

### Post by epidemiks on 2008-09-08
> **fewjr said:**
> I didn't do anything to Grub yet. As I stated before I was able to install to my 1st SATA drive after I added 'all_generic_ide', only to end back up at Busybox/initramfs after I was instructed to remove cd from drive and reboot. Could it be that Grub needs to be configured also to see the boot drive. I have no idea how I would do that when I can't boot into OS. Maybe I could try as you say to remove one of the SATA HDs and install again. Thank you. Is there maybe any more suggestions out there. I'm a little perplexed.

Ah, sorry, misread your post.
In that case, I'd try the same boot option at GRUB.. same way "F6", then "e" to edit command line and add 'all_generic_ide'

If it boots you can modify your menu.lst by using

```
gksudo gedit /boot/grub/menu.lst
```

in the terminal

---

### Post by fewjr on 2008-09-08
Ahh....well thank you for that. I am at work, but I will give that a try and post results when done. It will probably do the trick. I would still like to understand why I'm having this problem. I have one computer running lastest Ubuntu, but to tell you the truth I'm not sure if that one has a SATA drive or not. I'll have to crack it open and look. If it does I just don't understand what is causing the trouble with this new computer. Is it because I'm using SATA drives or because I'm installing with two SATA drives installed, etc, etc? I was going to run this with Fakeraid and maybe duelboot with XP. I guess I'll just have to live and learn and try to have fun with it all instead of getting too frustrated.:) Thank you epidemiks. I'll let you know what happens.

---

### Post by fewjr on 2008-09-14
Okay....I'm back. I'm sorry it took a week to get to this. Night work and 5 daughters takes up time. So epidemiks you said:

> In that case, I'd try the same boot option at GRUB.. same way "F6", then "e" to edit command line and add 'all_generic_ide'

If it boots you can modify your menu.lst by using

Code:

gksudo gedit /boot/grub/menu.lst

in the terminal

So last night I tried to boot harddisk. When Grub loaded, I hit esc to enter Grub. These are the entries under Grub:

Ubuntu 8.04, kernel 2.6.24-16-generic
Ubuntu 8.04, kernel 2.6.24.16-generic (recovery mode)
Ubuntu 8.04, memtest86t

I hit "e" to edit, the entries are:

root (hd0,0)
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=3f5cd6c3-59e3-4c83->
initrd /boot/initrd.img-2.6.24.16-generic
quiet

     I selected 2nd entry and hit "e" to edit and added all_generic_ide to the end of the command string.It only ended back up at the Busybox screen. Now if I boot to the livecd again and get to the partitioner, if I choose manuel instead of guided I see that my SATA drives are listed as dev/sda & /dev/sdb. So I did try the install again....and this time when I did it I selected guided-use whole disk. Then at the ready to install screen I hit the advanced button, which I did not do the first time. Then it says Device for boot loader installation. In the drop-down menu it had hd0 listed. I selected /dev/sda instead of leaving it at hd0 this time. Then when it finished installing, even with all_generic_ide I still ended up at Busybox.
     During boot I noticed a message flash on the screen right after Grub counts down and had to boot half a dozen to write it down...lol. 

MP BIOS Bug: 8254 timer not connected to IO-APIC

I did some researching on this fine forum and found that it is a common problem for new hardware due to the timer being moved to a different place that Ubuntu hasn't been apprised of yet....maybe in the next version huh. So anyway, I tried booting the livedisk again and selected the first entry to try without installing, which wouldn't work before. I edited and added "all_generic_ide noapic nolapic" and it allowed me to run it. So I tried to edit with these parameters to boot my harddisk, but it still would not boot into Ubuntu (Busybox). So I tried everything I can think of. Anymore help would be appreciated.

                                             fewjr

---

### Post by capnahab on 2008-09-14
Hi , I am a very new ubuntu user and was having the same problems. I had done the all_generic_ide stuff etc and was beating my head against the wall.
I got the impression it was a hardware incompatibilty problem, so started changing components where possible.
I removed the dvd drive and put in an old Cd drive. That got me away from the initramfs problem and furtehr towards a full install. I then gor into a video driver problem with my nvidia 7800 gt card so installed using F4 at boot - safe video mode. Now just have nvidia driver probs.
May not help you but hey.
I only have one daughter, so you get my respect.

---

### Post by fewjr on 2008-09-15
Thanks for the reply. Earlier in my post I stated that I got Ubuntu to install using the all_generic_ide parameters. So I don't think I need to change my optical drive. I was toying with the idea of disconnecting one of the SATA HDs and reinstalling, but after the "MP BIOS Bug: 8254 timer not connected to IO-APIC" message I figured that may be causing my issue. noapic is supposed to take care of that I thought. It allowed me to use livecd without installing but adding that in Grub doesn't let me boot my install. Please help me someone!

                                          fewjr

---

### Post by fewjr on 2008-09-16
I'm being patient, but......Bump.

---

### Post by deanjm1963 on 2008-09-20
I'm thinking about getting the same mobo very soon and did a search...

This thread [http://ubuntuforums.org/showthread.php?t=820161]("http://ubuntuforums.org/showthread.php?t=820161") might be helpful to you.

---

### Post by fewjr on 2008-09-20
Hello Deanjm1963,
     I have to tell you, you have made me very happy here in Maryland, USA. I have been searching the forum and waiting to see if anyone could help me. Your suggestion to check that thread did the trick. I changed to AHCI in BIOS- added pci=nomsi and it installed with no problem. Here is the funny part though. I thought I would have to edit my menu.lst file, adding pci=nomsi but it boots root0 without that. I don't know if thats normal or not. Anyway....thank you very, very much! My new computer is up and running. Now all I have to do is figure out why my wireless won't connect...](*,). Always something.

                                               Regards,
                                                fewjr

---

### Post by Francewhoa on 2010-03-11
Same here. **The following worked for me** [http://ubuntuforums.org/showthread.php?p=8952609#post8952609](http://ubuntuforums.org/showthread.php?p=8952609#post8952609)

---

