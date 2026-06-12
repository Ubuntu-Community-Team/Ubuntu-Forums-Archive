---
title: "why won't 10.04 boot?"
date: 2010-05-01
forum: Installation &amp; Upgrades
---

### Post by stef-l on 2010-05-01
Well I've been tearing my hair out all day with this one.  Followed various strands and posts & tried a lot of things but no joy.
(I have dual boot with XP SP3)
Last night upgraded from 8.04 to 10.04 using update manager, so I don't have a CD.  Worked fine till the very end of the install, but 10.04 will not boot - I get 'starting up' black screen, flash of green screen & then it all hangs - black screen, sometimes flashing cursor, sometimes frozen cursor.

It loaded 10.04 once, and the system worked.
It wouldn't turn off - just hanging splashscreen.
So had to power off.

Thought it was a graphics card issue (nvidia 6200) but it isn't.

From variosu advice have been trying to tweak the grub screen with 'nomodeset' but this hasn't had any effect.  Partly instructions I've been reading haven't been clear, and it doesn't seem possible to get the grub screen to save the 'nomodeset' instruction.

I have discovered that if I boot from my live 8.04 CD I can access the drive and the files on which 10.04 is installed.

Can anyone help me out of this madness?  When it works I love ubuntu, but every upgrade I've ever tried has been frustrating; I don't want to have to go back to XP which drives me nuts

Please help

stef-l

---

### Post by Rup.Xamqon on 2010-05-01
I had the very same problem - Dell XPS M1330, Nvidia GeForce 8400M GS graphics card, upgraded from 9.10 to 10.04, same result: no booting possible. After hitting several Ctrl-Alt-Del and Ctrl-Alt-Backspace and Enter's somehow Lucid started - don't ask me how...

Searching around I started meddling with Grub:
**sudo gedit /etc/default/grub**

I found the following two lines:
[INDENT]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="vga=792 splash quiet"[/INDENT]

Someone suggested deleting "quiet splash" and replacing by "nomodeset". That did not work for me. What worked was commenting the second line:
[INDENT]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
#GRUB_CMDLINE_LINUX="vga=792 splash quiet"[/INDENT]

It seems that my card does not like "vga=792".

BTW, thanks to [http://ubuntuforums.org/showthread.php?t=1446132]("http://ubuntuforums.org/showthread.php?t=1446132") I fixed my boot screen resolution:
[INDENT]GRUB_GFXMODE=1280x800x32[/INDENT]
and editing /etc/grub.d/00_header as suggested there.

---

### Post by stef-l on 2010-05-01
when I explored the 10.04 files after booting via the live 8.04 CD I was looking for lines like this in GRUB but did not find anything like them.  There seemed to be several different folders under GRUB, numbered 00, 10, 20, 30, 40 and I looked in all of them

I will have yet another look - quite honestly I am prepared to try anything

stef-l

---

### Post by oldfred on 2010-05-01
I think you were looking in the wrong place.
 GRUB 2 has three main parts:

   1. /etc/default/grub - the file containing GRUB 2 menu settings.
   2. /etc/grub.d/ - the directory containing GRUB 2 menu creating scripts.
   3. /boot/grub/grub.cfg - the GRUB 2 configuration file, not editable.

You need to look at /etc/default/grub, a file with config settings. The vga=XXX has been obsoleted so you have to change as Rup.Xamqon commented.

---

### Post by jplinderman on 2010-05-01
Since you mentioned NVIDIA and a blank screen, I had a similar problem.  I'd do a grub boot, wait a few seconds, and then my ASUS screen would report NO DVI SIGNAL.  I had to do the NVIDIA driver install via

System > Administration > Hardware drivers

but that can (as far as I know) only be done via gui (as root).  No drivers, no gui, no gui, no drivers.  I eventually installed a VGA card long enough to boot, login as root, and run the above sequence.  After that, the DVI input worked fine upon boot.  A good indication that this is the problem is that you may hear the Ubuntu login "music" even though your screen is blank.  -- jpl

---

### Post by nitstorm on 2010-05-01
<Sorry, dumb post>

---

### Post by stef-l on 2010-05-01
Right - I think somehow thanks to everyone's suggestions, I have managed to update the grub and can now load 10.04!!  - now I also need to ask why 10.04 won't shut down!
It gets as far as the splashscreen & then hangs, so I have to power off, which obviously isn't good.

Any thoughts?

Many thanks for everyone's patience

stef-l

---

### Post by sergik128 on 2010-05-01
I have similar problem but trying to boot from Live CD (I haven't tried  to install it yet). Just a low-res screen with Ubuntu logo with five  dots and then monitor goes to sleep. Ctrl-Alt-Del doesn't help, so I  have to power down my PC.

My configuration:
Asus P6T, Core i7 920 (no overclock), 6Gb Corsair, ATI Radeon 5850  (Asus, no overclock)

 - I checked CD for errors in Ubuntu 10.04 menu (no errors)
   - I checked RAM for errors in Ubuntu 10.04 menu (no errors)
  - I tried nomodeset option alone and several others from F6 menu  (didn't help)
 - I tried the same CD on my very old Pentium M laptop and my other Core  2 Duo desktop and it worked fine.
 - I tried Ubuntu's previous 9.10 Live CD on the same machine and it  worked fine.

I burnt CD using native capability of Win7 as advised by Ubuntu howto  page.

So I don't really know what to do next... I probably won't be trying to  install it until this and other issues (with grub config and loading to  another OS) are resolved...

---

### Post by stef-l on 2010-05-01
well  thought it was all sorted, but no!  10.04 won't always load, sometimes it will and other times it just hangs exactly as I described earlier..

I wish someone had a clear idea what I could do

I don't think having to use power off so often is helping the system either.

At the moment I have a ubuntu that's worse than useless: don't know if it will boot,and can't turn it off properly if it does...

does bill gates really have to win?

stef-l (getting very fed up now)

---

### Post by frantid on 2010-05-01
can you run the bootinfo script and put the results here inside code tags.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by stef-l on 2010-05-01
Well you've got me a bit foxed here, as I've never heard of boot info script before, but if you can tell me how I access it and I can get the 10.04 to boot up, I will have a go

stef-l

---

### Post by oldfred on 2010-05-01
frantid post is a link to the script that can be run from your system or from a liveCD.

If you are powering down to shutdown that may be the problem. It may want to run filechecks on reboot. With ext4 the files checks are quick but if you have several partitions it may take a while.

Not sure what is causing power down issues. Did you check log files for any errors?

---

### Post by frantid on 2010-05-01
> **stef-l said:**
> Well you've got me a bit foxed here, as I've never heard of boot info script before, but if you can tell me how I access it and I can get the 10.04 to boot up, I will have a go

stef-l


Hit the link from the LiveCD, there's a set of instructions on the page how to run it.

---

### Post by stef-l on 2010-05-02
sorry, but as I put in an earlierpost, I upgraded via update manager, so I don't have a 10.04 live CD, only an 8.04 one

stef-l

---

### Post by frantid on 2010-05-02
> **stef-l said:**
> sorry, but as I put in an earlierpost, I upgraded via update manager, so I don't have a 10.04 live CD, only an 8.04 one

stef-l


You can use an  8.04 cd.  The script just gives us information about your system, there's no way to really give suggestions without knowing more about your system.  Just download the script to somewhere on your harddrive, the use the terminal to run the script as the instructions on the net list.

Have you looked at this thread:
[http://ubuntuforums.org/showthread.php?t=1463294&highlight=grub](http://ubuntuforums.org/showthread.php?t=1463294&highlight=grub)

What type of video card do you have?

---

