---
title: "NVidia problems on installation: black screen, flashing login screen, low graphics"
date: 2010-08-25
forum: Installation &amp; Upgrades
---

### Post by Futurulus on 2010-08-25
Hi everyone,
 
I've been using Ubuntu on my desktop for a year or two now and have been quite happy with it. I upgraded to 10.04 recently on the desktop with only minor issues. Now I'm trying to install 10.04 on my laptop and am having problems with the graphics drivers. I've come across tons of similar issues on other threads, and none of the solutions have quite worked, so I signed up for the forum to start with a clean slate and see if you could help me with my specific set of issues.
 
The laptop: Toshiba A505-S6040, NVidia GeForce GT 330M with 1GB of GDDR3, Intel Core i7 (quad-core, 64-bit).
 
Here are the problems I've had, the solutions I've tried, and my results.
 
Problem: from a Wubi install, screen is blank (completely black, as if off) right after leaving GRUB.
Hypothesis: automatic mode setting for the nouveau drivers isn't working.
Attempted solution: boot with 'nomodeset'. <[http://www.ubuntugeek.com/how-to-fix-ubuntu-10-04-lts-lucid-blank-screen-at-startup.html](http://www.ubuntugeek.com/how-to-fix-ubuntu-10-04-lts-lucid-blank-screen-at-startup.html)>
Results: boots successfully into an apparently low-graphics mode.
 
Problem: resolution won't go above 800x600 on my 1366x768 screen.
Hypothesis: either disabling mode setting or the current low-graphics state prevents better resolutions.
Attempted solution: install NVidia restricted drivers to avoid needing 'nomodeset'; reboot.
 
Results/New Problem: after splash screen, boot freezes with blank screen and the following message flashing/blinking for a fraction of a second every five seconds or so:
```
Ubuntu 10.04 LTS ubuntu tty1
 
Ubuntu login: _
```
A cursor appears, but will only accept keys pressed in that fraction of a second when the message appears. Booting with 'nomodeset' moves this message to the bottom of the screen but otherwise no change. Somewhat reminiscent of this thread <[http://ubuntuforums.org/showthread.php?t=1305459](http://ubuntuforums.org/showthread.php?t=1305459)> but I'm not sure which of the myriad solutions offered I should try, especially since the thread seems mostly for 9.10.
 
(Not really a) Hypothesis: I realize I did a Wubi install when what I really want is a true dual-boot.
Attempted solution: uninstall Wubi, make a Live CD, install. Hope like heck this fixes the graphics too.
Results: it doesn't fix the graphics. I do, however, now have Ubuntu on a separate partition, as it should be.
 
Problem: same as above.
Hypothesis: booting into failsafe graphics mode will let me configure my system.
Attempted solution: booted into recovery mode with 'failsafeX'.
Results: back to low-res but working GUI.
 
Problem: still 800x600, now requires failsafe graphics to access.
Hypothesis: NVidia driver is the wrong one for my system.
Attempted solution: install a specific driver manually. <[http://trycatch.iblogger.org/tips-n-tricks/how-to-install-nvidia-drivers-in-ubuntu-10-04-lucid-lynx](http://trycatch.iblogger.org/tips-n-tricks/how-to-install-nvidia-drivers-in-ubuntu-10-04-lucid-lynx)>
Results: blinking screen, but instead of 'Ubuntu login' over a blank screen, 'Ubuntu login' flashes over 'Checking battery...' and a few other diagnostics.
 
Hypothesis: specific driver I installed is the wrong one for my system. (aka I'm an idiot)
Attempted solution: various combinations of 'sudo apt-get purge'ing nvidia drivers, following the official documentation <[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)>, and using the Hardware Drivers utility.
Results: no longer requires failsafe graphics/'nomodeset' to run, but...
 
Problem:
**Ubuntu is running in low-graphics mode**
The following error was encountered. You may need to update your configuration to solve this.
(EE) NVIDIA: Failed to load the NVIDIA kernel module. Please check your
(EE) NVIDIA: system's kernel log for additional error messages.
(EE) Failed to load module "nvidia" (module-specific error, 0)
(EE) No drivers available.
 
Attempted solution: click 'OK', run in low-graphics mode.
Results: back to low-res Ubuntu, "NVidia Accelerated etc. etc." official-looking entry in Hardware Drivers with a description is replaced with a bare "nvidia_current".
 
Does anyone have any other hypotheses I should try / posts I should look at / lines starting with 'sudo' I should trustingly plug into my terminal? I'm beginning to worry Ubuntu will never fully work on this laptop.
 
Thanks and sorry for my n00bosity,
 
Futurulus

---

### Post by GenBattle on 2010-08-25
I had the exact same problem with my machine when i upgraded from 9.10 to 10.04 (but with an ati card). I think it's a problem with the driver installation and its ability to overwrite various components (don't ask me?).

I was, like you, trying to install the proprietary driver i downloaded from the manufacturer's website. I then decided to (for the hell of it) install the driver from the repo (using the software center in low graphics mode), but this had the same problem, complained about missing components and files. I then rebooted, uninstalled the driver i had installed from the software center. After another reboot i installed my downloaded ati driver again, but this time it worked.

My theory is that uninstalling the repo driver cleaned out stuff that the ati installer couldn't. This might not work for you (since you've already done some purging via apt), but it's always worth giving it a go.

I also had a similar problem with booting and getting a blank screen (although my screen would turn off and on periodically as well as being blank). I found a number of related problems, and a number of solutions.
[http://ubuntuforums.org/showpost.php?p=9766336&postcount=8](http://ubuntuforums.org/showpost.php?p=9766336&postcount=8)

---

### Post by Futurulus on 2010-08-25
Hmm...to be clear, I haven't downloaded anything directly off a website through a browser.  I've done everything with apt-get, Hardware Drivers, and occasionally Synaptic.  I was considering going to NVidia's website, but all the posts I saw about that seemed to imply that the installation was complex and the drivers were buggy.
 
I didn't try the Software Center.  I'll see if I can get something there that works, or use it to somehow undo what I've done so far.
 
As for the black screen, 'nomodeset' and (I believe) 'xforcevesa' both work for me, but they only get me in with 800x600 resolution (blurry and stretched).  I'm hoping I'll be able to get the full 1366 out of it with the right software...

---

### Post by Futurulus on 2010-08-25
Okay, messing around with the Software Center and reinstalling 'nvidia-common' got me back to where the Hardware Drivers window had the full name "NVIDIA accelerated graphics driver (version current)" in the drivers list.  I activated it and was able to return to an important intermediate result.  This is the error I get when booting into recovery mode, failsafe graphics with the NVidia drivers installed correctly through Hardware Drivers:
 
**Ubuntu is running in low-graphics mode**
 
The following error was encountered.  You may need to update your configuration to solve this.
 
(EE) Aug 25 20:12:09 NVIDIA(0): The NVIDIA kernel module does not appear to be receiving
(EE) Aug 25 20:12:09 NVIDIA(0):    interrupts generated by the NVIDIA graphics device
(EE) Aug 25 20:12:09 NVIDIA(0):    PCI:1:0:0.  Please see Chapter 8: Common Problems in the
(EE) Aug 25 20:12:09 NVIDIA(0):    README for additional information.
(EE) Aug 25 20:12:09 NVIDIA(0): Failed to initialize the NVIDIA graphics device!
(EE) Screen(s) found, but none have a usable configuration.
 
I'm going to try uninstalling nouveau and using nv, which has worked like a charm on my desktop.  Let me know if you're familiar with this error message.

---

### Post by GenBattle on 2010-08-25
> (EE) Aug 25 20:12:09 NVIDIA(0): PCI:1:0:0. Please see Chapter 8: Common Problems in the
(EE) Aug 25 20:12:09 NVIDIA(0): README for additional information.

That looks interesting. There must be a readme file somewhere amongst the files installed with the driver. If you go to the package properties in synaptic you can get a list of installed files and their locations. See if you can find the readme, and see if it gives any useful information.

I knew how to fix the error with the kernel module missing, but i have no idea about this one, sorry.

---

### Post by Futurulus on 2010-08-26
Okay, here it is, hidden inside a giant, gzipped file in /usr/share/doc/nvidia-current:

```
Q. My X server fails to start, and my X log file contains the error:
   
   (EE) NVIDIA(0): The NVIDIA kernel module does not appear to
   (EE) NVIDIA(0):      be receiving interrupts generated by the NVIDIA
   graphics
   (EE) NVIDIA(0):      device PCI:x:x:x. Please see the COMMON PROBLEMS
   (EE) NVIDIA(0):      section in the README for additional information.
   
   
A. This can be caused by a variety of problems, such as PCI IRQ routing
   errors, I/O APIC problems or conflicts with other devices sharing the IRQ
   (or their drivers).

   If possible, configure your system such that your graphics card does not
   share its IRQ with other devices (try moving the graphics card to another
   slot if applicable, unload/disable the driver(s) for the device(s) sharing
   the card's IRQ, or remove/disable the device(s)).

   Depending on the nature of the problem, one of (or a combination of) these
   kernel parameters might also help:
   
       Parameter         Behavior
       --------------    ---------------------------------------------------
       pci=noacpi        don't use ACPI for PCI IRQ routing
       pci=biosirq       use PCI BIOS calls to retrieve the IRQ routing
                         table
       noapic            don't use I/O APICs present in the system
       acpi=off          disable ACPI
```
Hardware is definitely not my forte... what's "ACPI"?  What happens if I disable it?  I'm not going to go yanking out my graphics card, I can tell you that.

I also tried editing xorg.conf and replacing "nvidia" with "nv".  That gave me a much shorter, meaner error, something like "(EE) No devices found."  (I decided not to uninstall nouveau, since that is the default driver and removing it could make it impossible to return to clean install state.)

---

### Post by GenBattle on 2010-08-26
[http://en.wikipedia.org/wiki/Advanced_Configuration_and_Power_Interface](http://en.wikipedia.org/wiki/Advanced_Configuration_and_Power_Interface)

I wouldn't worry too much about disabling ACPI, chances are it'll only be until the next release of Ubuntu (which is only 2 months away).

> noapic            don't use I/O APICs present in the system
       acpi=off          disable ACPI
I would suggest you try both of these first, one at a time, then together.

---

### Post by Futurulus on 2010-08-26
Okay, major progress!  Here's what I did:

- Activated and then deactivated the NVIDIA drivers through Hardware Drivers (Jockey, as I'm seeing it called in other places).  This was to reactivate the default nouveau drivers.
- Restarted.
- Booted with 'acpi=off' at the end of the kernel grub command.

Miraculously, this boot was perfect!  Full 1366x768 resolution, quick boot (there were delays earlier, sometimes saying "Power Manager" was not responding) -- it even fixed what seemed to be an unrelated issue with my wireless connection.

Ecstatic, I choose "Shut Down" to make sure I had solved the problem.  Bad omen #1: system hung on shutdown, right after the message (I'm making the number up):

```
[26.034663] System halted.
```

The power button responded, though, turning my computer off.  I turned it back on, put 'acpi=off' into grub again ... and this time it froze during boot, right after some messages that had to do with running scripts.  After waiting for a while it gave me a message that said something like "soft lock: CPU#0 has been frozen for 61 seconds!"  Nothing responded except the power button.

I can still get the perfect boot back, but here's what I have to do:

- Boot with 'nomodeset' into 800x600 mode.
- Reboot (with "Restart", not with "Shut Down").
- Boot with 'acpi=off'.

As long as I keep restarting and not shutting down, I only need to do 'acpi=off', but as soon as I want to shut down, I have to go through the whole thing again.  Obviously still unacceptable for daily use, but at least I know there's a workaround of sorts.  I'll do some more Googling; tell me if you know of a solution.

---

### Post by Futurulus on 2010-08-26
Recorded the exact message for the lockup on boot; it was

```
[73.019951] BUG: soft lockup - CPU#0 stuck for 61s! [modprobe:296]
```

Everywhere I'm seeing, the solution to the shutdown problem seems to be 'acpi=force', which is in direct conflict with the 'acpi=off' that solved the original problem!

I'm going to try one last thing: shutting down with 'sudo shutdown now'.  After that I'm going to bed (it's almost midnight here) and letting my poor laptop recover from the dozens of reboots it's had to do today.

---

### Post by anonomo on 2010-08-26
Hi i&#7743; total noob with exact same graphics card, and same kind of problem.
booting through grub with nomodeset allows me to see using driver preinstalled with 10.04
however in (very low) low graphics mode (like 10fps video)
and hibernating or suspending laptop doesn´t work have to reboot through Grub.

installing Nvidia proprietary driver from their website tells me
> (EE) no display services...
(EE) screen found but none have usable configuration
but actually once you get past that it seems to display with plenty resolution
the problem is that it makes the edge of the screen go in the middle,
lol truly 360´ grapics.

so uh, keep me posted what you come up with
and if anyone wants to point me to some more basic help 
eg. where to find appropriate driver in repositories, 
most fully apreciated

---

### Post by GenBattle on 2010-08-26
Did you try "noapic", that may solve the problem without disabling ACPI?

---

### Post by Futurulus on 2010-08-26
@anonomo: Well, so far the best I can find is: deactivate the NVIDIA drivers, boot with nomodeset, restart, then boot with 'acpi=off' (in place of nomodeset).  ACPI seems to be a whole-laptop thing, though, not just a graphics thing, so if you're not using at least a Toshiba, don't be surprised if that doesn't help you out.  I haven't gotten that "rotated-screen" thing either -- I'm a noob too, but that seems like it would be a horizontal sync issue.  Not that that gives me any clue how to solve it...

@GenBattle: Yeah, tried 'noapic', then tried both of them -- seems 'noapic' doesn't have any effect.  Still blank screen with 'noapic' alone, and still works only on restart with 'noapic acpi=off'.  I didn't try 'noapic nomodeset', although I'd be willing to bet it would work in low resolution, as before.

I think I'll go dig up my old 8.04 (Hardy) live CD and see if I can boot from that.  Maybe it'll work with a 32-bit version.

---

### Post by Futurulus on 2010-08-26
Hardy live CD didn't work (ran some shell called 'initramfs' instead of Ubuntu, I wasn't willing to go look it up).  I *have*, however, gotten it down to minimal hassle, to a point where I can use Ubuntu mostly normally.

Here's what's required to get Ubuntu 64-bit to run with all systems "go" on my Toshiba A505-S6040, NVIDIA GeForce GT 330M, Intel Core i7, 6GB memory laptop:

- Turn on.
- Hit [C] in GRUB to get a command line.
- Type 'reboot' [ENTER].
- Hit [E] when GRUB returns to edit the default linux command.
- Add 'acpi=off' at the end of the line ending in 'quiet splash'.
- Hit [Ctrl][X] to boot.

That's my concise solution for other Googling newbies.  I've edited the GRUB defaults to add the 'acpi=off' automatically and to include "Reboot" as a menu option.  If anyone knows one a solution that's better (i.e. doesn't require rebooting every time), please let me know!

edit: @GenBattle - Thank you so much for all your help!

---

