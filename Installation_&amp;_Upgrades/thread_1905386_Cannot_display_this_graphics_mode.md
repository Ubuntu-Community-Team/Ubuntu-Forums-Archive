---
title: "Cannot display this graphics mode"
date: 2012-01-06
forum: Installation &amp; Upgrades
---

### Post by burnsmicro on 2012-01-06
As an absolute beginner, I first searched the Absolute Beginner forum with little success, not realizing that the searches DO NOT span forums. Then, I posted on the AB forum, with good initial success thanks to Fantab ([http://ubuntuforums.org/showthread.php?t=1888642&highlight=burnsmicro](http://ubuntuforums.org/showthread.php?t=1888642&highlight=burnsmicro), posting #4) who recommended placing a link in /etc/X11/Xsession.d/ to a fixresolution.sh script.

 Unfortunately the “Cannot display..” issue resurfaced when I fired up my PC after the holidays. The Fantab fix no longer works and the AB forum could not help, other than referring me to this forum.
   
 The problem is this forum is overwhelming to a beginner, with 900 postings to “[Graphics Resolution- Upgrade /Blank Screen after reboot]("http://ubuntuforums.org/showthread.php?t=1743535&highlight=display+video+mode") ”!

 I did attempt the step wise approach outlined by [MAFoElffen]("http://ubuntuforums.org/member.php?u=1044547") in his sticky post, but I am unable to [Shift] access Grub when booting from the HD and I do not know how to reinstall Grub from the LiveCD (or other source). Reinstalling Ubuntu-11.10 did not help. Neither did uncommenting “# GRUB_HIDDEN_TIMEOUT=00” from /etc/default/grub or editing “GRUB_CMDLINE_LINUX_DEFAULT =..” in the same file ..all done through the Ctrl-Alt-F1 CI.
 
 /home/username/.xsession_errors showed a ton of warnings and errors, beyond my comprehension, starting with  
```
Loading X session script /etc/X11/Xsession.d/99x11-common-start
 gnome-session[1438]: Warning: Session 'ubuntu' runnable check failed: Exited with code 1

``` Other efforts that failed:
 
[LIST]
[*]Changing the resolution restoring script to set a lower resolution from 1280x1024 60 to 1024x768 60 used successfully by the Ubuntu-11.10 LiveCD.
[*]Uncommenting “# GRUB_GFXMODE=640x480” in /etc/defaults/grub.
[/LIST]
The LiveCD works fine and the [HD] boot screen seems to work fine too. That is, I get a Bios screen --> black screen --> purple --> purple + "Ubuntu", dots and some text --> Black + "Cannot display..". I gather Linux has loaded because I can access the CI with Ctrl-Alt-F1.

 I did get my display working briefly, 2 days ago, after reinstalling [over] Ubuntu-11.10 with updates and 3rd party s/w. It rebooted fine from the HD. But I broke it again when I "apt-get updated" and then I "apt-get upgraded". I also tried to update the graphics driver through System Settings --> Drivers, but I got an error and it did not install (yet it had installed without a hitch about a month ago). Not sure which broke Ubuntu. On rebooting, I got the dreaded "Cannot display..". Subsequent attempts to install Ubuntu-11.10 (replace Ubuntu-11.10 by Ubuntu-11.10) have all failed to resolve the "Cannot display.." issue. I have yet to do a clean  Ubuntu-11.10 install.

Other info: 64 bit AMD PC with ATI/AMD proprietary FGLRX graphics on the motherboard.

 In short, my PC is unusable until I can get the screen to work again. 

 I cannot say how grateful I would be for some help. There must be a solution, in the 900 postings. But, how can I narrow it down and, do I have the expertise to understand it?

---

