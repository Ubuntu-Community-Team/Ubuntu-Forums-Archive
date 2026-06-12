---
title: "GRUB or partition problem"
date: 2012-11-02
forum: Installation &amp; Upgrades
---

### Post by Boomslang7 on 2012-11-02
My old Pentium III with an 80GB drive has suddenly lost its ability to boot. It has been running Ubuntu for several years, and is now on Ubuntu 12.04

I get "Error 18: Selected cylinder exceeds maximum supported by BIOS"

Occasionally this afternoon it will try to boot, but never gets all the way.

Sometimes it gives the error: "inconsistent file system structure"
and then offers a list of which OS to boot, but it just returns the "inconsistent file system structure" error for each item on the list.

Naturally, I tried to boot from CD (Ubuntu 9.1 and Ubuntu 10.10 is what I have on hand, but neither one will successfully boot to CD so I can pull my data off or fix GRUB.

Any advice on accessing my data or restoring GRUB if I cannot boot from CD?

Thanks . . .

---

### Post by Boomslang7 on 2012-11-03
I downloaded and burned a CD -- Debian's Boot Repair ISO -- which ought to boot and repair GRUB 2.

It boots the PC, and the Memory Test runs beautifully, but hangs when trying to boot either 32 bit or 32 bit failsafe modes.

---

### Post by oldfred on 2012-11-03
Error 18 is from grub legacy. Grub2 does not use error codes.

[http://members.iinet.net.au/~herman546/p15.html#18](http://members.iinet.net.au/~herman546/p15.html#18)

Old BIOS had a limit of 137GB, Herman discusses really old limits also. But your drive is 80GB?

This really only repairs grub2 issues but gives a good report on system configuration.

Post the link to the BootInfo report that this creates.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Full RepairCD with Boot-Repair (for newer computers) 
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

Or if you are in a working liveCD you can just download the bootinfoscript and run it. Not quite as much info but very useful.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Boot Info Script 0.61 is released April 2, 2012
boot_info_script.sh" file renamed to "bootinfoscript
[http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.61/](http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.61/)
Page with instructions and link to above new download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
Install these before running script:
sudo apt-get install gawk
sudo apt-get install xz-utils

---

### Post by Boomslang7 on 2012-11-03
Good to know it is legacy GRUB. I upgraded this installation from Ubuntu 10.10, so the GRUB version is likely 1.5. Perhaps I can get a Live boot from a CD with an earlier Ubuntu version than 12.04

Boot Repair that you mention I now have, since it is included on the Ubuntu-Rescue-Remix CD I just burned. The problem is, I can't access it. That CD boots to a command prompt which just says--   

boot:

and when I type in "live" (the default) to get Ubuntu Live I get a blank white screen with a blinking cursor. I did a MemTest and that passed 100%, so I am beginning to think it's the motherboard.

At this point I only hope to read the hard drive to pull some recent work off it which I really don't want to have to do over.

What other options or commands do I have at the  boot:  prompt of the Ubuntu-Rescue-Remix CD?

It's a Pentium 4 made in 2005, and an 80GB Western Digital SATA drive that's only half full.

Thanks for any advice,

---

### Post by Boomslang7 on 2012-11-03
I tried booting a Live CD, versions 11.1, 10.10, and 9.10. The Ubuntu 9.10 is the only one that got all the way to a menu screen before freezing the PC.

Ubuntu 9.10 allowed me to select either "Try Ubuntu without changing your computer" or "Boot from first Hard Disk" but it freezes the PC before it finishes loading a live environment.

---

### Post by oldfred on 2012-11-03
Computer may be old enough that you do not have PAE? Or the extensions to run more than 3GB of RAM in 32bit.

[http://ubuntuforums.org/showthread.php?t=1951653](http://ubuntuforums.org/showthread.php?t=1951653)
Ubuntu, Kubuntu, and probably Edubuntu will ship with the PAE kernel in 12.04, but both Lubuntu and Xubuntu will ship with non-pae

How To Install Ubuntu 12.04 On Non-PAE Capable Hardware.
[http://www.webupd8.org/2012/05/how-to-install-ubuntu-1204-on-non-pae.html#more](http://www.webupd8.org/2012/05/how-to-install-ubuntu-1204-on-non-pae.html#more)
To see processor
lscpu
grep --color=always -i PAE /proc/cpuinfo

If you do not have PAE your need Lubuntu or Xubuntu.

[http://en.wikipedia.org/wiki/Physical_Address_Extension](http://en.wikipedia.org/wiki/Physical_Address_Extension)
PAE is provided by Intel Pentium Pro and above CPUs, including all later Pentium-series processors (except most 400 MHz-bus versions of the Pentium M)

---

### Post by Boomslang7 on 2012-11-03
Thanks for the info. This is an older Pentium 4, and won't allow booting from a USB stick. Could be on-PAE.

I will try the mini-ISO to see if it offers the option of "Try Ubuntu without any change to your computer" so I can pull my data off the old drive. That's my primary concern at this point. Installing 12.04 will happen on a newer computer.

fyi, just out of curiosity I popped in a couple of old Windows XP CD's and a bootable DOS CD to see if they would boot the PC. Not for installing, but just to see if the box would boot to anything. None of them finished; the PC just froze up. That makes me suspicious of the hardware.

Let me work through these suggestions this evening, and I'll reply when it's done.

Thanks again,

---

### Post by Boomslang7 on 2012-11-04
No luck with anything, not the mini-ISO burn nor the Rescue disk. I even tried to boot from an old Debian CD, but it would also freeze the PC before getting to any prompt or GUI screen to act upon.

I've retired this hardworking old Pentium, kept the CD drive and HDD. I'll get a USB to SATA adapter from Newegg and see if I can talk to my data that way. The HDD is probably not hopeless, since it occasionally did try to boot up the last couple days.

This was not an Ubuntu problem but something with the motherboard, I think.

This case is closed.

Thanks again for the advice!

---

### Post by gordintoronto on 2012-11-04
> **Boomslang7 said:**
> ...I've retired this hardworking old Pentium, kept the CD drive and HDD. I'll get a USB to SATA adapter from Newegg and see if I can talk to my data that way....

Good plan, except for one small thing. Given the age of the computer, my bet is that the hard drive is IDE, not SATA. I recently got an adapter from Amazon which handles both. Cables only, no case, but quite cheap.

---

