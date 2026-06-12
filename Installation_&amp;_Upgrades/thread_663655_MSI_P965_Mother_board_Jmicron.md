---
title: "MSI P965 Mother board Jmicron"
date: 2008-01-10
forum: Installation &amp; Upgrades
---

### Post by GavinZac on 2008-01-10
Intel 965 Chipset
Pentium 4 3.0ghz
Maxtor 80GB IDE/PATA
Western 300GB SATA
2GB ram
Nvidia 21.6800 Graphics
Typhoon TV card
MSI P965 NeoF motherboard
JMicron PCI-Express to SATA/IDE controller

ubuntu installed to the 80GB IDE drive.

I can't get this system to boot. It drops dead at the GRUB loading stage with error 21 (disk problem). As far as I can tell, this is because of the JMicron controller thing which is definately making me think this motherboard was a bad purchase.

Has any else solved this? Has anyone gotten a bootable system, beyond the LiveCD which works fine?

---

### Post by GavinZac on 2008-01-10
i've located this "patch" for grub:

[http://www.mail-archive.com/bug-grub@gnu.org/msg11081.html](http://www.mail-archive.com/bug-grub@gnu.org/msg11081.html)

anyone want to help me implement it?

---

### Post by GavinZac on 2008-01-10
i've just realised that in an entire year here at ubuntuforums, no-one has responded to my threads. oh well.

anyway, i've given up (the options for my next step were to upgrade my bios which required windows, or to upgrade the jmircon bios, which needed a floppy disk, or to patch and recompile grub turning off some error checking) and I'm now going to try installing onto the SATA drive, with home on the IDE drive (not ideal, but at least it might bloody boot). Will post further updates as this is apparantly quite riveting.

---

### Post by GavinZac on 2008-01-10
installing onto SATA did not work, further pursuing the BIOS option. It seems the most popular way of upgrading the Jmicron bios is using the motherboard bios upgrade... except that all of those were with ASUS motherboards, not MSI. MSI motherboard drivers make no mention of Jmicron in their "change log".

Anyone know how to go about upgrading the motherboard bios without windows or a floppy disk?

---

### Post by GavinZac on 2008-01-10
I have a POS floppy disk drive in a box somewhere am going to have to dig it out and make a floppy disk with the bios on it. cannot believe it has come to this. Future ubuntu users: AVOID JMICRON LIKE THE PLAGUE

---

### Post by GavinZac on 2008-01-11
turns out you cant update the BIOS without windows. fantastic. someone is bringing over a copy for a temporary install to see if that will work.

Meanwhile, I did some reading and apparantly, only 1 of the sata slots is controlled by Jmicron, so I moved the hdd with ubuntu on it to a motherboard one, and I got past grub and got a flash of the ubuntu logo!... but it crashed to busybox. pursuing this now but will probably end up having to update the BIOS anyway as I would like my PC to be set up properly rather than just avoiding the problem with an inferior set up.

I;ve gotten the previously crashing to busybox fixed by removing the quiet splash items and replacing them with all_generic_ide in the boot options in Grub. However, I think I will probably end up abandoning this and installing XP temporarily to fix the BIOS

---

### Post by trentend on 2008-01-11
Hello there fellow sufferer.

I had what may be a related problem.

[http://ubuntuforums.org/showthread.php?t=489342](http://ubuntuforums.org/showthread.php?t=489342)

Six months, and a new version of Ubuntu, later and I'm no nearer to getting a bootable system. My new (ish) hardware is now old, and worth much less than I paid for it.  It still hasn't done a days work.  I've just spent the last three days trying to get a system up and running - to no effect.

It's got me beat.  I'm going to buy a copy of Vista, and get something useful out of my machine.

I can't say, in all honesty, that the level of assistance and support here is either very knowledgeable, or interested on helping. It's a lack of reasonable support, that undermines the usefulness of Linux despite it being, in most respects, superior to the mainstream operating systems.

As much as I hate windows, and the problems imposed by it's architecture, I'd kill for an authoritative Linux resource akin to micro$oft's knowledge base.

Really frustrating.

---

### Post by GavinZac on 2008-01-11
loading XP didnt work as the motherboard manufacturer doesnt carry the latest software for the JMicron controller. I'm beginning to suspect I'll just be buying a new motherboard.

I'm now trying to install using LILO instead of GRUB. Unfortunately, there appears to be no way of telling Ubuntu not to use grub at all, and when i do get my system to use LILO, it then dumps me back to busybox and will not let me continue because "this system doesnt have /sbin/init".

Ok im guessing LILO is using the wrong disk. Dunno how to change that, and research has gotten me nowhere so its time for another install, this time doing the advanced LILO set up.

This is the last time i put my PC before a date. Honest.

---

### Post by jrusso2 on 2008-01-11
Maybe its time to consider a version of Linux without the jmicron bug?

---

### Post by GavinZac on 2008-01-11
> **jrusso2 said:**
> Maybe its time to consider a version of Linux without the jmicron bug?

there aren't any, as far as I can tell. Especially with me being unable to update the JMicron bios since my motherboard manufacturer doesnt feature this update in their own BIOS update (whereas ASUS do). Apparantly those lucky ASUS/Jmicron users who have install ubuntu 'just' needed to update their motherboards BIOS through windows first.

---

### Post by GavinZac on 2008-01-11
Ok the LILO installation actually worked correctly, and installed on the right disk; the problem being, of course, that even though it loads up from the disk, it cannot see the disk; like GRUB, and like Super GRUB, and indeed, like my BIOS which must load Jmicron before it sees the disks.

What I will be trying next, is editing (via LiveCD) the LILO configuration once it has been installed, to see if there is any way to get it to boot correctly,

---

### Post by GavinZac on 2008-01-11
I've given up now, and I can't afford another motherboard, so its back to the idea of booting from one of the on-board SATA sockets, on the 300GB disk instead of the 80GB one. Because I dont particularly want an 80GB drive just hanging around on the machine, I'll take it out and put it in my server, which already has an 80GB drive. I might attempt RAID0 on those, if possible (most likely, not). 

I'll partition the 300GB drive 36GB to /, 4GB to swap and 260GB to /home/, and I'll install Hardy Heron on the 36GB; that way I'll have the newest kernel and if anything screws up I can keep the 260GB partition. I will just have to suffer the bizzarely long boot times while boot-up complains about the presence of the JMicron controller.

Final word: Don't buy the MSI P965 Neo-F, ever. If possible, avoid JMicron controllers altogether. And don't expect very many people to help you on ubuntuforums if its a rather obscure piece of hardware! ;)

---

### Post by Shazaam on 2008-01-11
Look at this post (300)  by Pixman (at the bottom. I don't know if it will help.

[http://ubuntuforums.org/showthread.php?t=234706&highlight=ICH8R&page=30](http://ubuntuforums.org/showthread.php?t=234706&highlight=ICH8R&page=30)

---

### Post by GavinZac on 2008-01-12
> **Shazaam said:**
> Look at this post (300)  by Pixman (at the bottom. I don't know if it will help.

[http://ubuntuforums.org/showthread.php?t=234706&highlight=ICH8R&page=30](http://ubuntuforums.org/showthread.php?t=234706&highlight=ICH8R&page=30)

Thanks, I read that thread, but I have a different motherboard, I can't find any such option in my BIOS set up.

Having problems now in that GRUB isn't playing nice, so I have to remove my hard drive from the boot up sequence, and later (possibly related?) the alternative installer can't see my hard drive where once it did even when it was plugged into the JMicron.

---

### Post by GavinZac on 2008-01-12
Now, for some reason, my previous solution of putting the SATA drive on the onboard SATA rather than the JMicron sata no longer works. The alternative install cd doesnt even see the SATA drive.

I'm going crazy. I think I will just buy another motherboard and deal with my debt when the bill comes.

---

### Post by sbuelter on 2008-02-02
Hey Gavin....have you been able to solve your problem?  I have the P965 and am suffering the same issue with the P956.  I have boiled down the issue to the hard drive controllers...but I am not sure it is specific to the JMicron.  I have tried a 300gb SATA drive and an 80GB IDE together and both by themselves.  Neither has worked.  I have also tried using the SATA in slot 1, 3,4,6,7 none of which solve the issue either.  To be frank, I think the motherboard is a POS as Windows does not work exceptionally well with the SATA drive either.  I did find this post, which seems to suggest a TON of other boards have similar issues...many of which use the same chip set.

OK....I am back to windows for the time being......

Scott

---

### Post by CarBlanco on 2008-02-10
I have an MSI P965 Neo F motherboard with a 500 GB SATA hard drive and a PATA CD/DVD Player. 

I am a complete newbie.  After going through posts and bug reports, here is what I came up with to make Ubuntu 7.10 work for me:

1.  I moved the hard drive SATA connection from the second port to the last port.  Before I did this, the live install CD would fail to load and go into busy box.

2.  After moving the port I installed Ubuntu.  

3.  When it refused to load correctly off the hard drive, I went into the recovery console.  I typed init 5 and the logon screen came up.  I logged in.

4.  I edited the /etc/apt/sources.list file by adding the following line so that I could see the newest hardy kernel in the Synaptic package manager:

     deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy main restricted

5.  I then ran the following command to update the list of packages

    sudo apt-get update

6.  I opened up the Synaptic package manager and went to base system.  I installed a newer kernel using the following packages:

    linux-image-2.6.24-7-generic
    linux-ubuntu-modules-2.6.24-7-generic

7.  Since I have an ATI video card, I also installed the following package containing a driver.

   linux-restricted-module-2.6.24-7-generic

8.  I went back to the /etc/apt/sources.list and commented out the line I added above.  I did this so that all the extra under development items would not show up when I tried to update the system.

9.  I Rebooted the computer and selected the newer kernel.  The system loaded fine.  While the system is loading, the screen blanked out but the hard drive kept spinning.  After about 30-40 seconds the login window appeared.  I installed all updates on the system.

I am now using Ubuntu for the first time.  It seems to be working fine.  However, being a complete newbie, I can't say for sure.

---

### Post by Peturrr on 2008-03-27
WHen using Wubi with a p965 neo-f the only way I got it working is by completely(!) disabling the USB controller...

---

### Post by bernardaukema on 2008-04-10
Solution!
I tried Wubi (Ubuntu 8.04) using the Jmicron-SATA connector (not the standard ICH8 connector)
My MSI P965 Neo-f was running linux for the first time today!:D

---

### Post by ballerh3 on 2008-05-03
> **Peturrr said:**
> WHen using Wubi with a p965 neo-f the only way I got it working is by completely(!) disabling the USB controller...

Both my SATA hard drives are not connected to SATA 1 and after completely disabling the USB controller, I am to boot up correctly with the LiveCD with no problems.

---

### Post by mediajunkie on 2008-06-05
HI all fellow digiboys.

I've been struggling myself with the jMicron chip for SATA. (MSI-P965 Neo series - MS7235) I've tried GenToo, Ubuntu, Kubuntu, Debian, CentOS. None of them could really work with the SATA drive. To be honest. all the halfa.ss solutions by disabling the USB and such, I find going back-wards. 

The only distribution I found working was SUSE 10.1 Enterprise, and for $80 or something it saves you a whole lot of grieve. I've downloaded the DVD (4GB install DVD) popped it in and loaded it with no problems at all. Actually I have multiple boot with XP-home, XP-Pro, and Suse Enterprise, all on a SATA drive with JMicron chip set. 

maybe an important note: I did do all the Bios updates and struff after loading XP on first partition. Then I loaded XP pro on the second partition. Finally I tried every Linux distro you can find basically to end up with SUSE 10.1 Enterprise. BTW, openSuSe, didn't work either. 

I hope you have something out of my experience. And if any might have found other, new or beter solutions for this Issue Please be so kind and post it for your fellow computians. LOL

---

