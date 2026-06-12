---
title: "Vista bootup problem after ubuntu install"
date: 2010-03-08
forum: Installation &amp; Upgrades
---

### Post by tilixibr on 2010-03-08
Hello,
I have a Compaq CQ60 laptop that came with 250GB of memory and...ugh.... Windows Vista. I decided to install Ubuntu, so I resized the Windows partition and installed Linux in that small remaining free space (about 25GB) from a freshly made Live CD, after a complete, clean and error-less install, Windows began to have problems starting... Here's what happens when I turn on the laptop: 
1- Shows the Compaq logo screen (normal)
2- Goes into the GRUB (1.97) boot menu(normal)
3- After selecting the Windows partition, it shows the scrolling green bars as it always did (normal)
here's the weird part:
4- Out of nowhere, the screen flashes and the computer restarts for no reason
5- I try to load Windows again, and it gives me a screen telling that the last start-up failed (as I expected...)
6- I select "Start Windows Normally"
7-The same thing from 4 to 5 happens again......
 I'll keep on doing this for at least 5 times before I can finally run Windows...
 
It doesn't always do that, sometimes it'll load normally without any issues.

My question is: How do I solve this? Does it have anything with me resizing the Windows partition?

I will appreciate any help given :)

---

### Post by Mark Phelps on 2010-03-08
> **tilixibr said:**
> .. Does it have anything with me resizing the Windows partition?
If you resized the Vista partition using the Ubuntu installer, or did it manually using GParted, that is most likely the culprit as that sometimes results in Vista OS partition corruption.

If you have a Vista installation DVD, boot from that and run Startup Repair repeatedly until it reports nothing left to repair.

If you don't have a Vista installation DVD, visit the NeoSmart Technology forums, download and burn the proper Vista Repair CD, and boot using that.

---

### Post by ar87 on 2010-03-08
I had exactly the same problem. While searching for a solution I saw that there were other people who also had this problem. At the end of the day, I had to revert back to Grub legacy for my windows to boot. Maybe this is a bug in grub2, I just don't have time to report it.

---

### Post by Mark Phelps on 2010-03-09
> **ar87 said:**
> ... I had to revert back to Grub legacy for my windows to boot....

This is NOT a GRUB2 vs. Grub Legacy problem, per se.

I have setups dual-booting with Vista, Win7, and various flavors of Ubuntu -- and all of them boot fine using GRUB2.

---

### Post by tilixibr on 2010-03-09
actually i resized the partition from Windows with a partition manager, beacuse I couldnt do it with GParted. Did that delete something that was on the area being formatted that is messing up Windows?

---

### Post by tilixibr on 2010-03-09
My laptop came with a rescue partition, but I left it untouched, will it work if I try to fix the Windows partition?

---

### Post by tilixibr on 2010-03-09
#3 that's what my dad thought too, but the problem is i had another laptop that had Ubuntu and XP, and It also had GRUB2, but it never had any problems, and I resized the partition from the Live CD partition manager during installation...

---

### Post by tilixibr on 2010-03-11
One more question: Could I have prevented this by defragmenting the Windows partition before I formatted it? I mean, it could have moved those supposedly lost files to a safe location, right?

---

### Post by superarthur on 2010-03-11
When I dual boot, there are 2 windows vista partitions
window vista in /dev/sda1 and window vista in /dev/sda2
The one in /dev/sda1 is Windows Recovery Environment, so don't select that.
The one in /dev/sda2 is the normal one you should select.

Maybe it's not relevant at all. :P

---

### Post by tilixibr on 2010-03-11
actually /dev/sda1 is the normal partition and /dev/sda2 is the recovery partition, at least for me.....

---

### Post by superarthur on 2010-03-11
weird windows, that's why microsoft is evil :P

---

### Post by tilixibr on 2010-03-19
I know! I'm the only one in my house that runs Linux, because I had enough of Vista, and I don't feel like coming back to Windows just to try Windows 7.....
My family has been monopolized by M$ :-(

---

### Post by Slim Odds on 2010-03-19
Both Vista and Windows 7 install with two partitions (one is hidden).

Most new laptops actually come with 3 partitions pre-installed. 2 for windows and 1 more "system recovery" partition that has everything needed to recreate the original setup.

You have to make sure you know which one is which.

My Gateway had the first partition of 12G as their system recovery data. Partition 2 was the hidden Windows 7 partition and partition 3 was the "C:" drive.

These new laptops also have a program to create recovery DVD's. I **HIGHLY** recommend that you create those **IMMEDIATELY**. Because, if for some reason, your hard drive craps out then the recovery partition will be dead and you can't recover.

I actually reformatted my recovery partition and installed Ubuntu. I put GRUB in the Ubuntu partition and I use the Windows boot loader to select the OS at boot time.

---

### Post by tilixibr on 2010-03-20
> **Slim Odds said:**
>  I put GRUB in the Ubuntu partition and I use the Windows boot loader to select the OS at boot time.
How do i put GRUB in the Ubuntu partition? I know that I can select which partition to install GRUB, in the last step before installing Ubuntu, by clicking "Advanced". But I don't know which partition to choose, the only option I remember seeing is hd0, which I think that's not even a partition, just the name of the hard drive to install GRUB.... In my situation, it seems GRUB has modified MBR, so does that mean all I have to do is use the Recovery Disc to restore MBR to its factory condition?

---

### Post by Rasa1111 on 2010-03-20
> **tilixibr said:**
> One more question: Could I have prevented this by defragmenting the Windows partition before I formatted it? I mean, it could have moved those supposedly lost files to a safe location, right?

 I dont know if it would have prevented it,
but you really should have defragged your HD first. 

> If you resized the Vista partition using the Ubuntu installer, or did it manually using GParted, that is most likely the culprit** as that sometimes results in Vista OS partition corruption.**
boy, window$ i$ awe$ome.

---

### Post by Slim Odds on 2010-03-20
> **tilixibr said:**
> How do i put GRUB in the Ubuntu partition? I know that I can select which partition to install GRUB, in the last step before installing Ubuntu, by clicking "Advanced". But I don't know which partition to choose, the only option I remember seeing is hd0, which I think that's not even a partition, just the name of the hard drive to install GRUB.... In my situation, it seems GRUB has modified MBR, so does that mean all I have to do is use the Recovery Disc to restore MBR to its factory condition?

You can boot the LiveCD and use gpartd to identify the partitions. So instead of (hd0) which is the MBR, I selected /dev/sda1 which was the first partition (where I installed Ubuntu).

Yes, unfortunately, if you already installed GRUB on the MBR you will have to restore it from the recovery disk.

---

### Post by tilixibr on 2010-03-27
Now it got worse! Now It's impossible to boot to Windows, right after I choose the windows partition the laptop restarts. It began doing it after I upgraded the Ubuntu installed on an external hard drive: I booted from the external HD and upgraded. after restarting, I had to reinstall grub because I couldn't boot to any OS if the external hard drive was connected...
Now grub loads fine without it, but now it won't boot windows....:confused:
Did reinstalling grub cause this? I hope that using the Vista Recovery Disc I downloaded fixes this [-o<
My worst case scenario would be having to do a complete Ubuntu reinstall after fixing the MBR, then install grub in the ubuntu partition... 

Sometimes windows acts too sensitive for my standards :neutral:

---

### Post by RJARRRPCGP on 2010-03-27
> **tilixibr said:**
> Now it got worse! Now It's impossible to boot to Windows, right after I choose the windows partition the laptop restarts. It began doing it after I upgraded the Ubuntu installed on an external hard drive: I booted from the external HD and upgraded. after restarting, I had to reinstall grub because I couldn't boot to any OS if the external hard drive was connected...
Now grub loads fine without it, but now it won't boot windows....:confused:
Did reinstalling grub cause this? I hope that using the Vista Recovery Disc I downloaded fixes this [-o<
My worst case scenario would be having to do a complete Ubuntu reinstall after fixing the MBR, then install grub in the ubuntu partition... 

Sometimes windows acts too sensitive for my standards :neutral:

Sounds like a bad HDD. Sorry. :(

---

### Post by Mark Phelps on 2010-03-27
You really interested in restoring your Vista boot ... or are you just interested in having fun bashing MS along with the others on this thread?

If you're really interested in the first, then say so.  Maybe I can help.

---

### Post by tilixibr on 2010-03-29
> **RJARRRPCGP said:**
> Sounds like a bad HDD. Sorry. :(
It's not a bad HDD, the laptop is not even 6 months old.

I use my Vista partition to study, since my language course uses IE and flash to work. And my family just don't get along with Linux, too...

---

