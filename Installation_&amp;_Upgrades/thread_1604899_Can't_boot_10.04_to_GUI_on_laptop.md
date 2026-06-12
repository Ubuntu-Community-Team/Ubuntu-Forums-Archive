---
title: "Can't boot 10.04 to GUI on laptop"
date: 2010-10-24
forum: Installation &amp; Upgrades
---

### Post by acrosome99 on 2010-10-24
Since my wife just bought a new laptop I decided to polish her old (decrepit) machine a little and let my daughter have it.  It was dual partitioned XP and Ubuntu 8.04 (which worked flawlessly).  I figured that since it was older I'd load Xubuntu.  I made a DVD of Xubuntu 10.04 that passed checksum.  When I tried to boot from the DVD I got as far as the menu asking me if I wanted to boot from the DVD, install from the DVD, etc.  Whatever I picked the machine seemed to think a while, then hang on a black screen.

So, I got an Ubuntu 10.04 CD from a book I'd just bought, and tried that.  It behaved identically- after the option menu whether I tried to boot from CD or install, it hung on a black screen.

So, I booted 8.04, and fired up the Update Manager, and loaded all recommended updates (as is generally my habit).  Then I clicked the button to update to 10.04, all of which progressed as expected over the course of  a few hours, until the reboot.  At this point it did the same thing!  GRUB loads, and I pick Ubuntu 10.04, then I get the word "Ubuntu" in the middle of the screen with several dots under it (the boot splash?) for a split second, then it hangs on a black screen.

If I boot Ubuntu 10.04 in recovery mode that DOES seem to work, and I get a command prompt.  But fixing this via command prompt is WAY beyond my weak Ubuntu kung-fu.

The machine is: 

Averatec 1000 series
Intel Celeron (R)M 1.00GHz
504MB RAM
Intel(R) 82852/82855 GM/GME graphics controller

Which seems to meet minimum system requirements.

Oh, and XP SP3 boots just fine.

But I'd be happy if I could single-install some version of Ubuntu, and screw the dual-boot capability with XP, if that makes any difference.

---

### Post by oldfred on 2010-10-24
I have nvidia and had to do this with f6 on startup of liveCD:

I have nvidia and my monitor went to standby & had to do this:
boot from the cd, press F6 and then select the nomodeset option.
(I acutally edited my grub.cfg as I use grub2 to directly boot ISO on USB, or in USB's syslinux.cfg or text.cfg)
then
On first boot after install, press e on getting the GRUB bootloader menu. (hold shift key from BIOS if not shown)
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

Your setting may be the intel older one?
Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
    * Older Intel video card: i915.modeset=1 or i915.modeset=0
    * nVidia: nomodeset 
    * Generic: xforcevesa or nouveau.modeset=0
    * Radeon: radeon.modeset=0

---

### Post by acrosome99 on 2010-10-24
Victory!

Thanks, oldfred.  It took me a while to figure out what that website was saying but at least I have 10.04 booted.  But I can't find a file called /etc/default/grub to make the change permanent, as it says!

What I can find is a file called /etc/grub.d/10_linux which has a few lines that look like:

>   linux_entry "${OS}" "${version}" false \
      "${GRUB_CMDLINE_LINUX} ${GRUB_CMDLINE_EXTRA} ${GRUB_CMDLINE_LINUX_DEFAULT}" \
      quiet
  if [ "x${GRUB_DISABLE_LINUX_RECOVERY}" != "xtrue" ]; then
    linux_entry "${OS}" "${version}" true \
    "single ${GRUB_CMDLINE_LINUX}"
  fi


Is this what I need to change?

---

### Post by oldfred on 2010-10-24
I do not think so. I have only edited the code once to limit Ubuntu kernels to two from drs305 site.

 GRUB 2  has three main parts plus a boot loader installed to the MBR:

   1. /etc/default/grub - the file containing GRUB 2 menu settings.
   2. /etc/grub.d/ - the directory containing GRUB 2 menu creating scripts. And a place for totally custom entries 40_custom.
   3. /boot/grub/grub.cfg - the GRUB 2 configuration file, not editable.

You want to edit /etc/default/grub
gksudo gedit /etc/default/grub
then 
sudo update-grub


For more info on customizing:
Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)

---

### Post by acrosome99 on 2010-10-24
I wasn't kidding when I said that there is no such file as /etc/default/grub.  I don't have one.

I tried typing gksudo gedit /etc/default/grub and a little window opened showing a blank page- no text.

I'm probably running legacy GRUB, not GRUB2, on this machine.  Does that make a difference?

---

### Post by acrosome99 on 2010-10-24
Well, now I've really screwed the pooch.

I figured I would go ahead and install Xubuntu, as I had wanted to originally.  Changing those GRUB settings worked, I was able to boot Xubuntu from CD and install it as the sole OS.  Now I can't boot it.  I never see a GRUB menu- it just progresses to the black screen hang.

I tried holding Esc to get the GRUB menu, but it didn't work.  On the off change that the install also installed GRUB2 I tried holding Shift at boot- also no dice.

---

### Post by acrosome99 on 2010-10-24
SOLVED

Aw, yeah!  Thanks for pointing me at that website, oldfred!  When I did the new install of Xubuntu it installed GRUB2, as I thought it might.  I'm not sure why Shift didn't work before, but it did now, and I was able to correct everything as described above.  (And, yes, GRUB Legacy uses different file names.)

Thanks again.

Now I just have to figure out how to change the status of this thread to "SOLVED"...

---

