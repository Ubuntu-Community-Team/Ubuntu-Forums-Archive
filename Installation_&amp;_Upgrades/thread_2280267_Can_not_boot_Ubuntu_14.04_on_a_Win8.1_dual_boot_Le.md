---
title: "Can not boot Ubuntu 14.04 on a Win8.1 dual boot Lenovo Z510"
date: 2015-05-29
forum: Installation &amp; Upgrades
---

### Post by Joel_Andersson on 2015-05-29
Hi,

**UPDATE: I gave up and seem to be able to restore to factory settings. Hope I did not waste anyone's time too much.** **I really can't work without Ubuntu so any advice for the inevitable reinstall to come is still appreciated.**

This is my first query here on Ubuntu forums so be nice. :)

I (unfortunately) bought a Lenovo Z510 with Windows 8 pre-installed last year and after a vast amount of trouble shooting I managed to install Ubuntu 14.04 alongside Windows 8. I am otherwise mostly used to building my own PC:s with no garbage Lenovo-stuff pre-installed.

Anyhow, as I only use the laptop when working abroad I had no major problems with the setup until a few weeks ago. However it did have trouble to install automatic updates both in Ubuntu and Windows. I believe it was after I did an update, either in Ubuntu or Windows, that it became impossible to boot Ubuntu again. In detail:

- I can get to GRUB2, and from there I can get into Windows, Advanced Ubuntu and System Setup without problems.

- When I try to boot Ubuntu it just stops at the loading screen where it appears to be loading forever (those dots keep blinking/moving). Pressing ESC displays the same 8 output lines over and over (a new set each time I press ESC):
```
Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
Skipping profile in /etc/apparmor.d/disable: usr.sbin.rsyslogd
* Starting AppArmor profiles
* Setting up X socket directories...
* speech-dispatcher disabled: edit /etc/default/speech-dispatcher
saned disabled; edit /etc/default/saned
* Restoring resolver state...
$Starting up Cisco AnyConnect Secure Mobility Client Agent
```

- Windows seems to be working ok, had some BSOD around the same time as Ubuntu stopped working though.

- I have tried various things, such as described here: [http://www.howtogeek.com/196740/how-to-fix-an-ubuntu-system-when-it-wont-boot/](http://www.howtogeek.com/196740/how-to-fix-an-ubuntu-system-when-it-wont-boot/)

- However, I am not able to run any live-USB at start-up. So I have not been able to try Boot-Repair or Ubuntu live-cd in order to reinstall.

- I have tried to change settings in (the very sparse?) Lenovo-EFI. Switch from UEFI to Legacy boot with bootable-USB just gives me errors such as "Boot error" or "No bootable device -- insert boot disk and press any key". I also tried to change other available settings, such as SATA Controller Mode and OS Optimized Defaults but it does not seem to help. Security Boot is Disabled by default. I might have missed the perfect combo of settings though?

- In GRUB2 command line, with USB plugged in (UEFI), "ls" output "error: failure reading sector 0x0 from `cd0'." or similar. Can also see (hd0), (cd0) and (hd0,gpt1) to (hd0,gpt10). In (Legacy) "ls" outputs the same error at the end but also displays (hd0) (cd0) (hd0,msdos1) and then (hd1), (hd1,gpt1) to (hd1,gpt10). Can this help me to boot from a live-USB?

- If I go into recovery mode it behaves differently depending on boot mode (UEFI/Legacy). "clean" offers me to free 193MB of space by attempting to remove linux-image-extra-3.13.0-27-generic and linux-image-3.13.0-27-generic. However, if selecting YES it outputs a bunch of lines and end with error: "E: Sub-process /usr/bin/dpkg returned an error code (1)"

- "dpkg" has similar issues, can not download and upgrade what it wants. "failsafeX" only lets me pass console errors when booting in Legacy mode but I still can not start in Low Graphics Mode or troubleshoot, eventually kicks me back to the recovery menu. 

- "fsck" detects some corrupt data and automatically removes dirty bit. 

- I can go into a root shell prompt but no Network mode. 

- Resume normal boot in best case get me to console login (after fsck has been run it seems) and I can login there. I can however not install boot-repair for example, error similar as the one described when running "clean" or "dpkg" in recovery menu.

- All in all it seems to "do a bit more" when going into recovery mode in Legacy boot.

Any ideas? If so, please describe them in more rather than less detail. If you believe it is simply easier to dig out the recovery cd for the laptop I could do that as I have backup of everything important but I remember it being hell to install Ubuntu in the first place. Question is if that hell is better/worse than trying to fix the error.

---

### Post by oldfred on 2015-05-31
If Windows is UEFI, much better to have Ubuntu in UEFI boot mode. You could have Ubuntu in CSM/legacy mode, but have to directly boot from UEFI and may have to turn on/off UEFI or legacy settings each time you switch.

       [SOLVED] Error 1962: No operating system found. Lenovo K430  only boot Ubuntu, rename files
[http://ubuntuforums.org/showthread.php?t=2243715](http://ubuntuforums.org/showthread.php?t=2243715)
Some Lenovos comes with a physical switch that enables you to select which graphics adapter to use.
 Lenovo Z510 Laptop & Ubuntu 
[http://ubuntuforums.org/showthread.php?t=2232124](http://ubuntuforums.org/showthread.php?t=2232124)
Installing GNU/Linux on a 2014 Lenovo Thinkpad X1 Carbon UEFI/BIOS suspend to RAM issue
[http://mako.cc/copyrighteous/installing-gnulinux-on-an-2014-lenovo-thinkpad-x1-carbon](http://mako.cc/copyrighteous/installing-gnulinux-on-an-2014-lenovo-thinkpad-x1-carbon)

Issues are often common across models as vendor has one UEFI only slightly customized based on what hardware that model has.
      
 [http://ubuntuforums.org/showthread.php?t=2275652](http://ubuntuforums.org/showthread.php?t=2275652)
Lenovo has a 'Novo' button that is used to power up to access the BIOS
[http://askubuntu.com/questions/624723/bios-access-problems-on-lenovo-xubuntu-installed-over-a-deleted-windows-8](http://askubuntu.com/questions/624723/bios-access-problems-on-lenovo-xubuntu-installed-over-a-deleted-windows-8)
Lenovo S20-30 BIOS install only
[http://ubuntuforums.org/showthread.php?t=2277003](http://ubuntuforums.org/showthread.php?t=2277003)
T540 works but UEFI settings critical or it may brick
[https://docs.google.com/document/d/1hFTArhNbmpmEBRkwRg0DMbEzLBCl43F1HXoXtJ8cm0k/edit?pli=1](https://docs.google.com/document/d/1hFTArhNbmpmEBRkwRg0DMbEzLBCl43F1HXoXtJ8cm0k/edit?pli=1)


 Lenovo Thinkpad E531 - turn off locked boot order setting in UEFI
[http://ubuntuforums.org/showthread.php?t=2255746](http://ubuntuforums.org/showthread.php?t=2255746)
[SOLVED] Error 1962: No operating system found. Lenovo K430  only boot Ubuntu, rename files
[http://ubuntuforums.org/showthread.php?t=2243715](http://ubuntuforums.org/showthread.php?t=2243715)

---

