---
title: "[SOLVED] 8.10 Beta won't install"
date: 2008-10-03
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by rbjscv on 2008-10-03
Downloaded Intrepid 8.10 Beta this morning, all excited about the things I've been reading.  I wanted to give it a trial to see if it was time to switch.  Apparently my machine says no way.

Burned the image at 2X on a DVD and then a CD.  I've tried 2 drives, twice each and every time it hangs at the opening scroll-bar. My machine is then locked up, won't reboot or respond in anyway.  I have to hold the power button to kill it and then turn it on again.  Same thing has happened with every prior release of Intrepid I tried. 

Hardy loaded fine.  Any ideas as to what is happening.  Is there someone I should report this to?  Is it just me?

unhappy and confused

---

### Post by Sef on 2008-10-03
1) Moved to Ibex forum.

2) Did you md5sum the download?

3) What happens when you 'Check Disk for Errors'?  Instead of installing or booting into the Live CD, go down to 'Check Disk for Errors'.

---

### Post by rbjscv on 2008-10-03
Check for my download showed:

574c9b48dbb5cf471b05ff18a9adc082  ubuntu-8.10-beta-desktop-i386.iso

574c9b48dbb5cf471b05ff18a9adc082 *ubuntu-8.10-beta-desktop-i386.iso : from website where I downloaded which was: mirrors.gigenet.com/ubuntu

Unless I'm mis-reading ( a distinct possibility) the two lines match.

Tried to Check Disk for Errors and still got hung at orange scroll bar.  Did power button routine, etc.

---

### Post by rocknrolf77 on 2008-10-03
Press F6 before you load ubuntu and remove quiet and splash. At least you can see what the problem is.

---

### Post by Perpetual on 2008-10-03
I have the same problem with the progress bar freezing about 1/3 of the way in.  There is a [bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/272247") opened about this.  I have to hold down a key then boot will resume.  I have other issues beyond that though with video.

---

### Post by rbjscv on 2008-10-03
Perpetual, what key do you hold down?  I'll try anything once.  And sometimes more.

---

### Post by iponeverything on 2008-10-03
It is hard to say what the cause is without seeing the boot messages and event then, sometimes it not easy.

you could try to boot with the option acpi=off

---

### Post by Perpetual on 2008-10-03
> **rbjscv said:**
> Perpetual, what key do you hold down?  I'll try anything once.  And sometimes more.

Any key.  I have used ctrl, alt, ctrl+alt.  If I let go of the key, it stops booting.

---

### Post by Sef on 2008-10-03
>  Tried to Check Disk for Errors and still got hung at orange scroll bar.  Did power button routine, etc.

You could have had a bad burn or a bad cd.   Is there another computer that you could check the Live CD on?  If it works on that one, then it would be a problem limited to your computer.

---

### Post by Perpetual on 2008-10-03
Not the OP but I did numerous burns with each Alpha on different machines.  Burnt on Ubuntu 8.04 and on Vista.  No difference.  All fail and all fail as the OP said even when trying to check the disc.  They work on my other laptop which is an older Dell.  I can not install any distribution with the 2.6.27 kernel.  Mandriva is the same, I have to hold a key in order for the boot process to complete.

---

### Post by rbjscv on 2008-10-03
With acpi=off i received this msg:

[    0.000000] Bios bug, no explicit IRQ entries, using default uptable *(think this correct word - can't read my writing)*  (tell you hw vendor)

---

### Post by rbjscv on 2008-10-03
> **rocknrolf77 said:**
> Press F6 before you load ubuntu and remove quiet and splash. At least you can see what the problem is.

Usual startup text then,

Yield was:

kjournald starting. commit interval 5 seconds
EXT-3 -fs:  mounted filesystem with ordered mode

BusyBox v.1.10.2 (ubuntu1:1.10.2-1ubuntu6) built-in shell (ash)
enter help....(etc, etc)

(initramfs)

---

### Post by beetlejuice321 on 2008-10-11
I have the exact same problem.  And yeah it looks like this is a known bug but they still haven't fixed it yet.  Hopefully by the the the official release is out they will!

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/272247](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/272247)

By the way why does this thread say [Solved]???  Did someone figure out a way to install Ubuntu 8.10 and have it boot successfully?

Also I did try installing 8.4, then upgrading to 8.10.  The installation completed successfully, but after rebooting my system locked up just like with the CD.  So this definitely is quit an annoying kernel bug.

---

### Post by rbjscv on 2008-10-12
I've no idea why this is marked solved.   No 8.10 has loaded for me still.  So now I've just given up on it.

---

