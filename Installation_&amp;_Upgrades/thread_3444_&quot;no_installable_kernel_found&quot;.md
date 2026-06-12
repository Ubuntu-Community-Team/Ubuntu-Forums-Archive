---
title: "&quot;no installable kernel found&quot;"
date: 2004-11-06
forum: Installation &amp; Upgrades
---

### Post by francis on 2004-11-06
I listed this post previously and have not  received much infomation other than
reference to bug report #3196. 
After 82% or 86% install progress it displays "no installable kernel was found in the 
defined APT sources. Current default package is 'linux -386' .  You may try to continue though this strange error is probably fatal".  It  then  re-starts base install,
and again stops at  82%  or 86%. 
The CD-ROM was purchased from a very reputable dealer. My computer is a Dell 
450 mhz PIII with 128megs ram and 6 gig hard drive.  It normally runs Debian 3.0,
 Slackware 10.0,  or FreeBSD 5.2.

Should I wait for another revision of Ubuntu or ask dealer for another copy since I
don't have really high speed to download an iso, or a CD burner?  Am really anxious
to run Ubuntu after reading all the good reviews. I would assume my computer 
meets minimum specs.  My network will not configure either, but I will worry about
that after I get Ubuntu installed and running!

Asking for advice. Thanks.

---

### Post by az on 2004-11-06
Most likely, your cd or your cd reader is bad.  You meet the minimum requirements for sure...

---

### Post by Mighty Mik on 2004-11-07
Nope...this is a known bug.

[QUOTE=azz]Most likely, your cd or your cd reader is bad.  You meet the minimum requirements for sure...[/QUOTE]

---

### Post by cuebei on 2004-11-29
I too am having this problem.  I'm on a VIA C3 (933 MHz) powered laptop.  It's currently running Fedora Core 3, so I know it's capable, but I'm all Fedora'ed out man.

Any fix in sight?

---

### Post by SuperLou on 2005-05-16
I have already tried multiple CDs and had the same problem.  Does ubuntu use an internet connection to apt-get the kernel?

---

### Post by obaeko on 2005-06-23
[QUOTE=azz]Most likely, your cd or your cd reader is bad.  You meet the minimum requirements for sure...[/QUOTE]
 I have the same problem.
I have used this CD to install on a IBM thinkpad earlier. No problem.

Any idea on how to get around this?

---

### Post by obaeko on 2005-06-23
Hi Again.
I solved the problem on my computer anyway...

The symptoms were as follows:
- Installation were running as expected to about 68%.
- The CD-ROM stops spinning, probably because of timeout since last read operation, as the computer is busy configuring.
- When the installation program tries to read from the CD-ROM again, the CD is only spinning at very low speed. It is just like it can't get started again.
- Then I get the error message: "no installable kernel found"

I had to change my hardware configuration to get it to work.
I had the following set up:
IDE primary, Master: A hard drive
IDE primary, Slave: A hard drive
IDE Secondary, Master: CD RW
IDE Secondary, Slave: Empty

New configuration:
IDE primary, Master: A hard drive
IDE primary, Slave: CD RW
IDE Secondary, Master: Empty
IDE Secondary, Slave: Empty

Then it all works!!! :-)


Hope this can help some one else!!!!

---

### Post by reedlaw on 2005-08-11
I've had this problem doing a network install on multiple computers, all of the same hardware configuration, but just one or two of them would have the error "no installable kernel found".  I just re-ran the base system install and sometimes it would work, other times I had to try three or four times and finally it worked on every system.  Strange bug, I wish I could tell you more about why it happens but I'm clueless too.

---

### Post by snteran on 2005-10-10
Danger!!!!

> I had to change my hardware configuration to get it to work.
I had the following set up:
IDE primary, Master: A hard drive
IDE primary, Slave: A hard drive
IDE Secondary, Master: CD RW
IDE Secondary, Slave: Empty

New configuration:
IDE primary, Master: A hard drive
IDE primary, Slave: CD RW
IDE Secondary, Master: Empty
IDE Secondary, Slave: Empty

Then it all works!!!

I tried this setup and it crashed my computer.  I restarted the computer and it no longer detected my CD-Drive.  Went through setup again and set back to old configuration in order to get my CD drive back.  This was my experience with a Dell optiplex gx240 desktop.

Still having install problems.  Trying somethings, might try using a different flavor of Linux just to see if I can get one to install.

Serge

---

### Post by Oldan on 2005-12-06
[QUOTE=francis]After 82% or 86% install progress it displays "no installable kernel was found in the defined APT sources. Current default package is 'linux -386' .  You may try to continue though this strange error is probably fatal".  It  then  re-starts base install, and again stops at  82%  or 86%. 
[/QUOTE]

I'm having the exact same problem on an AMD64 install.

It's pretty annoying since the 5.04 install went so smoothly that I figured it would be an easy upgrade.:( 
--Oldan

---

### Post by Oldan on 2005-12-10
Well, I found a note in another [thread]("http://www.ubuntuforums.org/showthread.php?t=100203&highlight=installable+kernel") that indicated recording the CD at the slowest rate would change your life. I re-did the CD and it installed!

I'd still like my own partitioning scheme better than the one provided by default.. but it's good enough for now.

--Oldan

---

### Post by Patrick Shannon on 2005-12-25
I ran into this problem as well.  My fix was to update the CMOS clock.
I hit a ctrl-alt-f something and saw an error that mentioned that the gpg key was 6000000ish seconds newer than the current date. 

-Patrick

---

### Post by neqton's Cat on 2006-01-01
[QUOTE=obaeko]Hi Again.
I solved the problem on my computer anyway...

The symptoms were as follows:
- Installation were running as expected to about 68%.
- The CD-ROM stops spinning, probably because of timeout since last read operation, as the computer is busy configuring.
- When the installation program tries to read from the CD-ROM again, the CD is only spinning at very low speed. It is just like it can't get started again.
- Then I get the error message: "no installable kernel found"

I had to change my hardware configuration to get it to work.
I had the following set up:
IDE primary, Master: A hard drive
IDE primary, Slave: A hard drive
IDE Secondary, Master: CD RW
IDE Secondary, Slave: Empty

New configuration:
IDE primary, Master: A hard drive
IDE primary, Slave: CD RW
IDE Secondary, Master: Empty
IDE Secondary, Slave: Empty

Then it all works!!! :-)


Hope this can help some one else!!!![/QUOTE]

Thanx! I wish I'd seen this yesterday!

Puter (an old Compaq Pentium Deskpro 2000) had CD-ROM as Master on Secondary IDE - and I kept getting the 'No Installable Kernel Found ...' message. Tried fitting a different HD & CD-ROM - removed SCSI, Sound, & Network cards - changed cables, and so on. Still got the damned message!

Put CD-ROM as Slave on Primary IDE - hey presto! It all works!

---

### Post by Newton's Cat on 2006-01-01
"neqton's Cat" !!!

I was so excited about finally getting Ubuntu to install me brain didn't see what me fingers were doin'!

---

### Post by skralljt on 2007-01-29
I followed some of the suggestions in this thread, I tried re-installing the base package and got a selection box where it gave me a choice of ten different kernels to use.  I chose the generic 386 one and continued, but then the installation flummoxed when installing the software.  It always stalled at 6%.  I tried booting up after that and got a prompt, and tried to install xubuntu-desktop that way, but I kept getting I/O errors.  Having tried burning several different copies of ubuntu in the last week, I tried them all and got errors in different sectors.  
After getting a different cdrom and putting it as slave on the first ide channel,  I got through the base install just great and managed to avoid the issue with a missing kernel, but it stalled again on the 6% of the software.  It was a fairly new computer, maybe 900 mhz.  Only 6 years old!  
On a different note, the alternate install cd is essential, because the regular ones make you boot into a gnome environment and it absolutely crawls!  On this old 1 ghz machine, it took about 20 minutes for the first install prompt to appear.  Ubuntu must not be one of the distros focused on rehabilitating old computers with winME on them!  Guess I should try DSL or something..

---

### Post by migraineman on 2007-04-28
I had multiple instances of the "no installable kernel found in defined APT sources."  The 7.0.4 versions of ubuntu, edubuntu, and xubuntu all failed the same way (which wasn't much of a surprise.)  I did manage to get the installation working, however.

With the "no installable kernel" message on the display, I switched to an alternate console using Alt-F3.  From there, I executed "chroot /target" to switch linux's focus to the target installation.  I then ran "aptitude" for the text-based package installer.  From the installation tree, I seleted "not instaled" then "base", "main", and finally "linux-image-2.6.20-15 ..."  Mark that package for installation with an "I" (capital-eye).  Aptitude was kind enough to resolve dependencies, and  pressing "g" sent the installer on it's way.  There were mesages about lilo configuration requirements, but I didn't do anything with those.

When aptitude was done installing, I returned to the main installation (Alt-F1) and let it proceed.  It continuted to completion - which previous installs didn't do because of the missing kernel.  Upon reboot, I was greeted with the grub startup message, followed by linux trying to boot into xubuntu.  I assume that the grub installation took care of the lilo issues cited earlier.  Like I said, I didn't address those in the hopes that the installer would take care of it.  Apparently it did.  

My final issue was one of configuration of the display resolution.  My ancient hardware doesn't support 24-bit color (which is the default,) so the video driver couldn't find a matching mode.  Took a while to find the right file - /etc/X11/xorg.conf.  I had to change the DefaultDepth parameter from 24 to 8, and now I boot properly into the Xfce graphical environment.

So there you have it.  I've seen lots of folks on the web asking about how to fix this issue.  That's how I slogged through it (no guarantee it'll work for anyone else ...)  I know someone will ask about the components, so  -

 xubuntu 7.0.4 alternate desktop
Neoware EON2000E thin client with 8MB Disk-on-Chip removed
---National Geode GX1 @ 300MHz
---160MB SDRAM (32MB sodimm + 128MB PC133 stick)
---Generic CD-ROM drive dangling out the side
---4.3GB Maxtor hard drive precariously perched atop the CD-ROM drive

---

### Post by jaseatthebar on 2008-01-20
Thanks Migraineman!
I have a similar setup.  Installing Xubuntu on a Geode GX1.  6GB hard-drive also precariously perched on the CD drive.  I've very little experience with Linux and have spent 2wks swapping HW trying to get around the "no installable kernel" problem.
I followed your clear instructions and now have a working installation.

---

