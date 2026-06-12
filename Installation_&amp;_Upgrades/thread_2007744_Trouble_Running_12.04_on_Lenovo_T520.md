---
title: "Trouble Running 12.04 on Lenovo T520"
date: 2012-06-21
forum: Installation &amp; Upgrades
---

### Post by Spaceman Spiff on 2012-06-21
Hi all,
  I am at my wits end, I was hoping I could get some support on setting up my 12.04 correctly.  I am going to write up my approach in hopes of getting support from the community... or developers.


**Install Ubuntu 12.04 64 bit on T520**
  -  1) Prepare T520 for Ubuntu.
  - -    a) Set graphics card as Discrete Only (turns off Optimus)
  - -    b) Disable OS detection as well
  - 2) Insert 12.04 64 bit disk, and begin install
  - -    a) hangs if no user input, attempts to start ubuntu without success
  - - -        i) Press any button when you see the screen turn purple, a language menu pops up.
  - -    b) At language menu, press Esc, press "Install Ubuntu".  Hangs with a black screen, blinking cursor at top left.
  - - -        i) Turned off my computer for a while, tried again.  It worked (strange inconsistency)
  - - -        ii) T520 is attached to a dock, could that be the problem?  Notice that its working on my external monitor.
  - -    c) Ubuntu starts loading, reach a black screen ... nothing on any monitor.
  - - -        i) Hold power button, turn off pc (the only way to deal with all the errors I am going to encounter.)
  - - -        ii) Remove T520 from dock, attack eth cable and power cable to it.  Trying to do step (a) ... keyboard doesn't respond, stuck at black screen with blinking cursor, powercycling (again)
  - -    d) Trying again, removing external keyboard, keyboard responds, "Install Ubuntu", blinking cursor again black screen, nothing happens, power cycling again.
  - - -        i) After letting it sit turned off for around 1 minute, attempt (d) again, blinking cursor at black screen again, but this time it continues.
  - -    e) Ubuntu 12.04 64 bit finally loads from the Live CD ... took me around 6 attempts and 3 power cycles, but hey... we got there
  - - -        i) Dont be connected to a dock
  - - -        ii) If you want your keyboard to respond, don't have an external keyboard attached
  - -    f) Ubuntu installing...
  - - -        i) Installing on an ext4 partition, using / as mount point
  - -    g) 12.04 Booted successfully.

** Running Ubuntu 12.04 On T520 **
- 1) I would like to get consistent boot ups and restarts... thus
- - i) Note, I upgraded the kernel image and header first through the update manager ... some threads noted more stability.
- - ii) Performing requested restart from update manager... Failure.  Stuck on purple screen after selecting new kernel in grub
- - iii) Power cycling again, adding "nomodeset" through grub edit, pressing ctrl-x ... Failure.  Blinking cursor top left of screen.
- - iv) Power cycling again.  Waiting 2 minutes. Selecting kernel ... Successfully booted into Ubuntu 12.04.
- - v) Shutdown computer from inside 12.04.  Booting again immediately... Success (splash screen was messed up though)
- - vi) Restarting computer from inside 12.04... Failed.  Stuck on purple screen again. Power cycling.
- - vii) Waiting a few minutes before powering on.... Failed.  Stuck on blinking cursor. Power cycling.
- - viii) Didn't wait at all this time, went to blinking cursor and worked.
- 2) Attached my lenovo back to its dock.  It froze. Power cycling.
- - i) Initial power cycle works! Plymouth screen is messed up.
- - ii) With the dock on, one of my displays showed the ubuntu desktop at a terrible resolution.  Went to displays in settings, it found my monitors set them at 1920x1080 for both... apply, nothing.  I get black screens on both.  Power cycling again. (Nice trend yeah?)
- - iii) Boot up failed, stuck at purple screen on laptop monitor.  Power cycling. (still attached to dock, external monitors not getting signals.)
- - iv) Boot up failed, stuck at black screen with blinking cursor. Power cycling.
- - v) Boot up successful, but again I'm stuck with two black screens... I guess I messed up my xorg.conf. Power cycling.
- - vi) Boot successfully into recovery mode, and "Resume boot."  Installing the ppa drivers in hopes of running 12.04 with two monitors.
- - vii)Boot failed, stuck on purple screen... Power cycling.
- - viii) Booted successfully.  So I set double monitors using sudo nvidia-settings.  Also added nomodeset in GFX_MODE_DEFAULT_LINUX
- - ix) Booted failed, stuck at purple screen.  Power cycling.
- - x) Booted failed, stuck at cursor blinking screen. Power cycling.
- - xi) Boot successful.  Didn't save my double monitor configuration though.

---

### Post by dino99 on 2012-06-21
maybe you can mail this lucky user with the same hardware:

[http://ubuntuforums.org/showthread.php?t=1999612](http://ubuntuforums.org/showthread.php?t=1999612)

and/or follow different options to boot:

[https://wiki.ubuntu.com/BootOptions](https://wiki.ubuntu.com/BootOptions)

but you have not said how you have installed the system, specially which partition format is used (ext4 ?)

---

### Post by Spaceman Spiff on 2012-06-21
Thank you for your response.  I made some further attempts, and examined my xorg log file.  The graphics driver is apparently having trouble, and can't find the NVidia device.

---

### Post by dino99 on 2012-06-21
nowadays the kernel directly deal with X, so often an old xorg.conf conflict and give unexpected issues.

from synaptic:
- purge All the installed graphic drivers
- reinstall the one you need

from a terminal:

sudo rm /etc/X11/xorg.conf*

sudo shutdown -R now

---

### Post by Spaceman Spiff on 2012-06-21
Hey Dino99 once, again I appreciate the response... 11.10 is doing the same exact **** (pardon my french.)  So I'm going to attempt this from scratch and write it up for other poor Lenovo users.

As of right now I am staring a 12.04 64 bi Install on my Lenovo

The current problem:  Immediately, the Live CD does not work.  I have to press a button and see the LIveCD menu.  Then I set nomodeset.  Press "Install Ubuntu" hangs on a black screen with white cursor.

---

### Post by Spaceman Spiff on 2012-06-21
I am currently stuck on Installing Ubuntu 12.04 64 bit on my laptop, could anyone offer some advice?  My top post is outlining my current state .... currently I am sitting around waiting hoping that if I let it sit long enough ... something will happen.

Edit:  Okay apparently, sitting around for 1 minute with the computer off worked ... Why?

---

### Post by Spaceman Spiff on 2012-06-21
Hi all, after installing and upgrading my 12.04, I cannot consistently boot into the kernel anymore.  I am stuck on a blank purple screen after the grub selection.  Could anyone offer some advice on what to do next?

My steps so far have been outlined above in my first post...  This is a fresh install, nothing proprietary.

---

### Post by Spaceman Spiff on 2012-06-21
Could anyone give me some advice on where I can find error messages that would relate to my problems so I can start somewhere and tackle my problems?  The only solution I have so far is power cycling, and that's obviously not healthy.  Thank you.

---

### Post by Spaceman Spiff on 2012-06-22
Awesome, thanks for the help!

---

### Post by oldfred on 2012-06-23
Do not power cycle, remember the elephants.

Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)

Often nomodeset or other kernal parameters are required.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
I had to do this with my Nvidia 9600GT:
To install Ubuntu, boot from the cd press any key at accessibility circle and keyboard, press F6 and then select the nomodeset option.
USB boot - At the menu press tab on the first option to edit the boot options and replaced the 'splash' option with 'nomodeset'. 
then
On first boot after install, press e on getting the GRUB bootloader. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode), install nVidia driver suggested my Ubuntu

---

### Post by Spaceman Spiff on 2012-06-24
Good evening Oldfred, I appreciate the "elephants" approach.  I will give it a shot next time my 12.04 freezes at boot.

I have the nomodeset parameter set, I will gladly remove the "quiet splash" parameters as well.  Lastly, I would like to note that I have blacklisted all the nouveau (sp?) drivers, and added "nouveau.blacklist=1" to my boot parameters.

As of writing this post, the problem of the purple screen of blank, and the blinking cursor screen are still occurring.

---

### Post by oldfred on 2012-06-24
You can remove quiet & splash to see the boot details, but they are recorded in log files. You may want to look at the log files after an error and see the difference between previous boot and most recent. I look for a task repeating and failing, then timing out, or one taking a very long time.

If Unity I think you just search for log file viewer. With gnome panel it is applications, System tools, log file viewer.  I usually look at dmesg as it has the times a task was loaded as the first entry.

---

### Post by Ubu4u on 2012-07-05
Having the same issue with 12.04 64-bit on a Lenovo T520. I've opened [this ticket]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1005349") which describes the problem.

The ticket was opened a month ago, but hasn't been assigned yet. It would be great to have it assigned to someone and have it looked at. I'd be happy to help in any way I can.

@Spaceman Spiff: If you seem to be affected by the same issue, I don't think it would hurt to add to the ticket. I'm not sure what else can be done to address the issue. :confused:

---

### Post by Spaceman Spiff on 2012-07-06
I would like to add that Alt+SysReq REISUB does not work, which only adds to giant middle-finger I feel Ubuntu giving me.

Ubu4u, when I get a moment at work I would love to do that.  Sadly, I get don't get paid to learn why Ubuntu 12.04 decided to take giant strides backwards.

---

