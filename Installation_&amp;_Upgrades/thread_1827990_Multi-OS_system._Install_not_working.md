---
title: "Multi-OS system. Install not working"
date: 2011-08-18
forum: Installation &amp; Upgrades
---

### Post by mikebode on 2011-08-18
I have a DELL 360 that has Win2003 Server and XP installed. I now need some software that runs under Linux, and I was told to install Ubuntu to set up a dual boot system (found it on web: [http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm?page=2](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm?page=2)

They say to use Ubuntu 9.4, but I can't find it so I downloaded 11.04 and burned it to a CD. When booting the PC with the CD, Ubuntu shows up with the 5 dots (progress bar). At some point (about 3 minutes), the bar simply stops changing, the CD drive quiets down, and nothing happens. I never get a dialog that says done or asks for installation questions. When I take out the CD and reboot, I get my original boot options (Win2003 and XP), nothing else.

How do I get Linux installed on a PC that already has 2 Windows OSes installed?

Or am I barking at the wrong tree? Should I use something else but Ubuntu?

Thanks for your help.

mike

---

### Post by IWantFroyo on 2011-08-18
I would suggest using Ubuntu 10.04 (Long Term Support).

If you need to install a specific program on Ubuntu, 10.04 is most likely to have tutorials.

To get the image, just go [here]("http://www.ubuntu.com/download/ubuntu/download") and select Ubuntu 10.04 from the Download Options.

If you want to try 11.04, hit the escape key while the purple dots are doing their thing, select the preferred language, and hit F6 (think that's it) to experiment with boot parameters. Sometimes computers won't boot up unless acpi is off, and such.

---

### Post by mikebode on 2011-08-18
Thanks for the tip, but I have the same problem with 10.04. This time I pressed the Esc button, and I see a whole page full of error messages. Can I capture them somehow?

The last line is: "Starting Common Linux Printing system: cupsd", then nothing.

I see a bunch modules where the compilation was aborted,  number of times it says "Unknown user: ubuntu".

I waited about 10 minutes, took out the CD, then pushed the power button. It hen came back with more pages of error message ("can't find block xxxx"). 

Do I need to wait longer? Or is it not possible to install Ubuntu on a system that has win2003 on it?

---

### Post by mikebode on 2011-08-18
Ok, now it is getting really weird. I just replaced the hard disk with one that I had lying around (120 GB). Ubuntu 10.04 would not install. So I thought, perhaps I need Windows present, ad installed Win XP first. No problem. Win XP installs flawlessly and I can boot it from the hard disk without any problems. Then I put the Ubuntu 10.04 CD back in. Nothing but error messages (Input/Output errors, chroot issues, kernel panic).

What do I have to do to install Ubuntu?

](*,)

---

### Post by zealibib slaughter on 2011-08-18
First check the ubuntu disk by checking the md5sum of the downloaded iso file. See this page and scroll to md5sum in windows: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
If that checks out then check the disk with the check disk feature.  You may have a bad ISO download or disk burn.

---

### Post by mikebode on 2011-08-18
Umm, stupid question: How do I run md5sum when I have no Linux or Ubuntu installation? Is there a windows version?

Also, I had previously downloaded 11.04. Same problem.

Ahh, never mind. Found a winmd5 utility. Downloading iso file again right now. Will check back in when I have it.

---

### Post by mikebode on 2011-08-18
Allright, I have not finished downloading the iso yet, but I figured I could check the CD for integrity. So I boot with the Ubuntu CD and select "Check disk for integrity".

After a minute or so I get a message "checking for integrity, this may take a while". Immediately after that I get a message:

chroot: cannot execute debconf-communicate: input/output error

Does that mean the CD is not OK?

---

### Post by zealibib slaughter on 2011-08-18
> **mikebode said:**
> Allright, I have not finished downloading the iso yet, but I figured I could check the CD for integrity. So I boot with the Ubuntu CD and select "Check disk for integrity".
 
After a minute or so I get a message "checking for integrity, this may take a while". Immediately after that I get a message:
 
chroot: cannot execute debconf-communicate: input/output error
 
Does that mean the CD is not OK?
 
It's more than likely the cd is corrupt.

---

### Post by IWantFroyo on 2011-08-18
Probably. Burning a new disc with a new image, making sure speed is around 4x, is your best bet.

---

### Post by mikebode on 2011-08-18
Thanks, everybody. I think I have it now. It seems that I have to burn the iso file to a DVD, not a CD. The DVD checked out OK, and I am installing now...

:p

---

### Post by IWantFroyo on 2011-08-18
Congrats! I still wonder why you would need to use a DVD. Many of my successful Linux installations have been off CDs. I bought some DVD-RWs, and they mess up my install if I use them more than once...

---

### Post by mikebode on 2011-08-19
Yeah, I don't know either. I only know that it worked. My guess is that my DVD Writer on one machine might not be 100% compatible with the reader on the other machine when I write CDs. But it's working now. 

Onwards to the software I really want to install. I only had time to take a quick look at the CD (maybe I have to re-burn that one also...), and didn't see an "Install" or "Setup" icon. Is there a specific way that software gets installed under Linux? The software is "Asterisk", by the way, a telephony application.

---

### Post by Hakunka-Matata on 2011-08-19
There are several common methods of installing packages, programs, applications, in Ubuntu.


[LIST]
[*]System > Administration > Synaptic Package Manager is probably the most thorough and clean method.
[*]Ubuntu Software center under Applications
[*]search for and download .deb packages, programs.  They install by simply double clicking the file after it's downloaded.  That is assuming of course that you got the correct package for your Release, natty, maverick, etc.
[/LIST]

---

