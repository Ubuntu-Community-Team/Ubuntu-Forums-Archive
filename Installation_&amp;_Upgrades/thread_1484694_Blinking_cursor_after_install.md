---
title: "Blinking cursor after install"
date: 2010-05-16
forum: Installation &amp; Upgrades
---

### Post by sandpvrr on 2010-05-16
Hello All,
      eMachines Intel ATOM powered netbook refuses to boot 10.04 netbook remix, if I install or go into the live cd and install from there. Numerous attempts - one or two got as far as booting one time, but locked up soon after and would not restart. Been pounding my head on this one. I have an usual install workflow, I burn the ISO to a CD and use a USB cdrom drive to install. Don't think this matters, but figured I'd mention it. Had 9.10 on this same netbook with no problems. Have changed the SATA setting in BIOS from its default to IDE and back, no difference. Also have downloaded the ISO twice, two different sources / methods - no difference - burned at least three copies, no difference either.
       Grabbed a CD with Mandriva on it, worked like a charm. Machine itself is ok, but either I'm doing something wrong or I'm missing something.
       Thanks in advance!
         -Joey

---

### Post by Catharsis on 2010-05-16
Can you boot into recovery mode?

---

### Post by sandpvrr on 2010-05-16
Oh yes - forgot to mention I installed to an Eee PC with the same CD, USB cdrom drive, etc. Worked flawlessly. Not sure what it is with this eMachines netbook. 
       Thanks!
        -Joey

---

### Post by sandpvrr on 2010-05-16
> **Catharsis said:**
> Can you boot into recovery mode?

No - I cannot boot into anything - just get a black screen, white blinking cursor and the machine locks up. (Must be hard restarted).
      -Joey

---

### Post by sandpvrr on 2010-05-16
Bump....Thoughts?

---

### Post by darkod on 2010-05-16
Video issue?

Follow the instructions here:
[http://ubuntuforums.org/showpost.php?p=9308664&postcount=13](http://ubuntuforums.org/showpost.php?p=9308664&postcount=13)

to try and boot with 'nomodeset' added. If that works, you have instructions how to make it permanent or maybe you won't even need to if the fist boot into ubuntu offers to download new video drivers.

---

### Post by sandpvrr on 2010-05-16
I'm double checking by reinstalling now - (I had put Mandriva on just to use it) but I don't recall seeing GRUB come up either.....

---

### Post by darkod on 2010-05-16
> **sandpvrr said:**
> I'm double checking by reinstalling now - (I had put Mandriva on just to use it) but I don't recall seeing GRUB come up either.....

In single boot systems (when not dual booting with another OS) the boot menu doesn't show up to speed up booting because there is no other OS to select.

In this case, for 10.04 and Grub2 press (or start hitting Shift) after the BIOS POST finishes, at the start of booting. That will make a grub menu show.

---

### Post by sandpvrr on 2010-05-16
> **darkod said:**
> In single boot systems (when not dual booting with another OS) the boot menu doesn't show up to speed up booting because there is no other OS to select.

In this case, for 10.04 and Grub2 press (or start hitting Shift) after the BIOS POST finishes, at the start of booting. That will make a grub menu show.

Well I'll be danged. I have no idea what caused it, but while hitting the shift key, the blasted netbook booted. As a matter of fact, I'm typing this on it now. First thing I did was to install the wireless network card drivers, then all updates available and I'm working on my base install of software packages. Thanks for the help, but not sure if that did it or not!
-Joey

---

### Post by KL007 on 2010-06-15
I got the exact same behavior: Fresh installed Ubuntu 10.04, rebooted for the first time as requested by the install and got a blinking cursor on a black screen and a frozen system for my trouble.  I had to power off the machine, and then held the shift key while it rebooted as suggested in this thread - and viola - now my system boots every time without keyboard assistance.  
 
It may not be that the shift key helped as much as booting again (first boot failure for some reason).  But now the world will never know.  It's very odd that I'd get a boot failure right after install in any case....

---

### Post by Palmerin on 2010-06-16
Hi all, 
I was having the same exact problem on a Dell Mini laptop.
Upon highlighting Linux on Grub, pressing "e" to edit and adding "nomode", it boots up just fine.

---

### Post by fabiofloyd on 2010-09-06
i have the same issue after install kububtu or ubuntu 10.10 and when i try to enter grub (holding shift) it freeze at GRUB loading.

---

### Post by cbanakis on 2010-11-01
Baaahhhh!!!!

I have the same problem, except shift seems to have no effect.

I had 10.04 installed with no problems.

Formatted and installed 10.10, and no luck.

After initial reboot, black screen with blinking curser.

Eventually gave up, and put 10.04 back on, USING THE SAME DISC I USED THE FIRST TIME....

And I got the same blinking cursor even after going back to 10.04 ?!?!?!?!?!

WTF?

Someone please help...

At the end of my freakin rope here :(

---

### Post by cbanakis on 2010-11-01
Ah Ha!!!

I figured out my issue.

I have 3 hard drives in my box.

1 Performance drive for the OS
2 Large drives in RAID 0 for storage

Seems that somehow, even though I installed Ubuntu on the performance drive...

It seems to have put the boot loader on the RAID array ????

So I had to tell my BIOS to boot to the array 1st, instead of my OS drive.

Thats pretty dam strange, but at least all is well now :)

---

### Post by leeber303 on 2010-11-07
Just adding that the above solution of changing your boot order to your first RAID drive, even though the OS is installed on another drive, will boot the OS.

Weird

---

### Post by GadZooks on 2010-11-29
Thank you [cbanakis]("http://ubuntuforums.org/member.php?u=824651")!!!

I had the exact same problem - Ubuntu 10.10 installed to the wrong drive.

You're the bee's knees.

---

### Post by Yousufullah on 2011-02-12
This Thread is amazing I'm new to Ubuntu and couldn't work out why my installation didn't work[IMG]http://ubuntuforums.org/images/icons/icon4.gif[/IMG]

I had two hard drives installed and the boot drivers were installed onto my other hard drive.
Why did this happen[IMG]http://ubuntuforums.org/images/icons/icon5.gif[/IMG] I don't know but Ubuntu seriously needs to sort this glitch out with the Installer LOL

Anyhow thanks to Mr bees knees [IMG]http://ubuntuforums.org/images/icons/icon14.gif[/IMG] for finding this out or I would have kept trying all sorts of unconventional things [IMG]http://ubuntuforums.org/images/icons/icon13.gif[/IMG]

Many Thanks

Yousuf

---

### Post by sixstrum on 2011-03-03
i was sure this thread would be the answer to my problem, but so far i'm still stuck at the blinking cursor screen.  ...I've tried the "shift" button thing, didn't help.

i don't think the installation guide installs GRUB, so I'm thinking that means i don't have GRUB - is that why this is happening?

i followed the steps from the Ubuntu website step by step.  

please help!

---

### Post by sixstrum on 2011-03-05
My bad ....didn't realize I still had the SD card in the computer and that's where the boot was being installed.   Took that out, really installed, all is well.

---

### Post by cbanakis on 2011-04-29
> **sixstrum said:**
> My bad ....didn't realize I still had the SD card in the computer and that's where the boot was being installed.   Took that out, really installed, all is well.

LOL

Glad you got it working

Maybe Ubuntu just installs the boot-loader on whatever drive it believes to be the fastest?

On mine, the os was installed on the right drive, it was just that my RAID array had to be set as the 1st drive in my bios boot order.

I'm glad I got mine, and others working, but I'm still not 100% sure why it works?

---

### Post by cbanakis on 2011-05-02
Just a quick update.

I did a clean install to upgrade to 11.04 and determined that Ubuntu likes to install the boot loader to the lowest drive#

So with my setup, I had 2 - 750 GB drives in RAID 0 and a 150 GB Velociraptor.

The drives were configured as follows.

Drive0 750 GB (RAID 0 Component)
Drive1 150 GB Velociraptor
Drive2 750 GB (RAID 0 Component) 

If you do custom partition setup, you can tell it where to put the boot loader.
Otherwise, it just uses Drive0 (Or whatever is the lowest)

I did not want to mess with the partition settings, so I just cracked open the computer and moved my connections around to make my Velociraptor Drive0.

And now everything is setup correctly.

Yay.

---

### Post by volkswagner on 2011-06-05
I had the same annoying blinking cursor.  My system would fully boot, as I was only running a CLI, no GUI.  I could ssh into the box, and I could get tty1-tty6 with no problem.

I tried various fixes on the net.

What did it for me was removing "splash" from grub line.

```
GRUB_CMDLINE_LINUX_DEFAULT="splash nomodeset acpi=force"
```

to

```
GRUB_CMDLINE_LINUX_DEFAULT="nomodeset acpi=force"
```

I first tried moving "splash" after my custom additions.  I also tried just removing "quiet". 

So much for Plymouth!

I hope someone finds this work around useful, as I have spent way to many hours figuring this out.

---

### Post by Wraiths82 on 2011-08-23
Hello All,
 
I am having this problem on a brand new Dell Studio XPS.  I had to put in an older video card as I couldn't even get to the installation menu with the new one.  After installation and restart I get the blinking cursor in the top left of my screen and I can not get it to boot.  Shift or any of the other fixes didn't work for me.  I can reboot it with ctrl alt del but it just reboots to the cursor again.  I have it on a hardware raid and they are mirrored.  Any suggestions would be greatly appreciated.
 
Thanks,
 
James

---

### Post by MSTRZ on 2011-08-24
Yeah, I had this problem too, with Wubi, but it still hangs even after I press "install ubuntu" from the boot menu.
I do the shift thing into the grub menu, and it launches me into the boot screen, where i press "install ubuntu", it gets to a certain point and then hangs.
Do i just need to wait longer?

---

