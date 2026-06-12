---
title: "USB HDD with Saucy boots to a black screen"
date: 2013-11-21
forum: Installation &amp; Upgrades
---

### Post by alessio-popoli on 2013-11-21
Hello everybody, I've already seen a lot of threads about the same problem I have, but so far none of the solutions I read worked.
Let's start from the very beginning. I have this Verbatim HDD on which I had installed Oneiric and later upgraded to Precise and then Raring, but one day it fell... its sound after I plugged it into my PC was unmistakable: a hard drive failure.
So I bought a new one (to tell the truth, I bought a used internal HDD, opened my old one up and replaced the internal HDD that was inside) and created two partitions: one (90GB) formatted in EXT3, the other (~200GB, all the remaining space) formatted in FAT32.
Then, I downloaded the Saucy Salamander ISO for x64 systems (my PC has a 64-bit architecture) and burnt it onto a DVD. The first strange thing was that this DVD was apparently not bootable: every time I tried to boot from it, after some 5 seconds of black screen, I got redirected to the boot device selection. Of course both Windows and Ubuntu Live could show the content of the DVD, so it was burnt correctly.
Well, I had an old MicroSD card, so I used UNetBootin to put the Saucy ISO on it. It booted up just fine, and I installed the system to the EXT3 partition on my external HDD. Then I tried to boot from it. I only got a blinking underscore on a black screen, hanging forever (I leaved it like that for about one hour, nothing happened).
What I've tried so far:
-Disconnecting all other USB devices, in case my computer tried to boot from those instead.
-Pressing SHIFT at the black screen; at first nothing happens, but if I wait for about 10-15 seconds, I get a beeping noise (this happens with any button I press).
-Pressing CTRL+ALT+F1 or any other combination that could bring up a terminal or anything else with some kind of interactivity, but none of them worked.
-Re-installing Grub using my old Oneiric Live CD (I don't have any other at the moment, as the Saucy DVD doesn't work).
-Plugging the drive into a different port.
-Booting from another USB hard drive to see if that worked. Well, my main OS is Windows 8, it is on an external HDD and I'm using it now, so yes, it works.
-Repairing the boot via Ubuntu Live. I had to do that anyways; everytime  I update Grub I get a "Unknown filesystem" error on boot, and no matter  what I do, only re-installing Grub works. Why do I need Grub on my Windows 8 HDD? Because there is another partition with BackTrack on it.

I don't know what to do now. I think I've tried pretty much everything I found on the Internet, I'm frankly discouraged from continuing, but before giving up I wanted to ask for help here. Thank you all in advance.

---

### Post by oldfred on 2013-11-21
Not sure if Boot issue or Video issue. Best to see if boot issue and see details.

 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

### Post by alessio-popoli on 2013-11-21
You won't believe this, but it really looks like generating the BootInfo alone solved my problem (although it can't be, can it?). When I rebooted I forgot to plug in the correct external HDD - so the one with Ubuntu was connected - and it booted up just fine. Well, better for me. Thank you anyways!

---

### Post by oldfred on 2013-11-21
It was not running the Bootinfo report, it was the magic dust it uses. :)

---

