---
title: "Win10 with UEFI boot, Ubuntu with Legacy (CSM) boot - is this a good idea?"
date: 2015-08-31
forum: Installation &amp; Upgrades
---

### Post by hans12345 on 2015-08-31
I have been trying for some time to have a dual boot Win 10 and Ubuntu on 2 new PCs, one ACER XC 605 and the other a Lenovo All In One C260.

I have tried all the usual UEFI dual boot solutions to no avail.

But I rarely want to use Win 10, so maybe I should just install Ubuntu in Legacy mode (BIOS set to CSM) ? This would make booting in Win 10 a slower process (entering BIOS and changing parameters) but if this only happens occasionally, this is no big deal.

My questions are
- is it easy to install Ubuntu in Legacy mode on a UEFI system with Win 10 already installed?
- are there particular dangers that I should be aware off?

Thanks for your help

---

### Post by oldfred on 2015-08-31
It is better to be in UEFI mode, but some have used Legacy. Do not know of any specific issues beyond the normal Windows issues.
Make sure fast start up is off in Windows.

Acer requires you to set a supervisor password and that opens of more settings. And after you install you have to set "trust" on the grub/Ubuntu boot files.
       Acer Aspire ES1-512-C39M Details on supervisor password and settings to enable trust on ubuntu entries Also R14 model same fix
[http://ubuntuforums.org/showthread.php?t=2291335](http://ubuntuforums.org/showthread.php?t=2291335)
[http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044](http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044)
[http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot](http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot)
[http://acer.custhelp.com/app/answers/detail/a_id/29349/](http://acer.custhelp.com/app/answers/detail/a_id/29349/)
[http://ubuntuforums.org/showthread.php?t=2290594](http://ubuntuforums.org/showthread.php?t=2290594)
Details on password & trust setting:
[URL="http://askubuntu.com/questions/597213/bootable-device-not-found-after-clean-install-of-ubuntu-14-04-uefi"]http://askubuntu.com/questions/597213/bootable-device-not-found-after-clean-install-of-ubuntu-14-04-uefi
[/URL]
 Acer Windows UEFI & Ubuntu BIOS
[URL="http://ubuntuforums.org/showthread.php?t=2292242"]http://ubuntuforums.org/showthread.php?t=2292242

[/URL]
 Lenovo Laptops there is NOVO button on left side
Lenovo S20-30 BIOS install only
[http://ubuntuforums.org/showthread.php?t=2277003](http://ubuntuforums.org/showthread.php?t=2277003)
T540 works but UEFI settings critical or it may brick
[https://docs.google.com/document/d/1hFTArhNbmpmEBRkwRg0DMbEzLBCl43F1HXoXtJ8cm0k/edit?pli=1](https://docs.google.com/document/d/1hFTArhNbmpmEBRkwRg0DMbEzLBCl43F1HXoXtJ8cm0k/edit?pli=1)
Lenovo Thinkpad E531 - turn off locked boot order setting in UEFI
[http://ubuntuforums.org/showthread.php?t=2255746](http://ubuntuforums.org/showthread.php?t=2255746)
[SOLVED] Error 1962: No operating system found. Lenovo K430  only boot Ubuntu, rename files
[URL="http://ubuntuforums.org/showthread.php?t=2243715"]http://ubuntuforums.org/showthread.php?t=2243715

[/URL]

[URL="http://ubuntuforums.org/showthread.php?t=2292242"]
[/URL]

[URL="http://askubuntu.com/questions/597213/bootable-device-not-found-after-clean-install-of-ubuntu-14-04-uefi"]
[/URL]

---

### Post by hans12345 on 2015-09-01
Thanks OldFred

As you will know, we are finally making progress with the USB boot problem on the ACER, so maybe this idea of mine (posted when I was getting very frustrated with being unable to boot from the USB) becomes unnecessary.

I will keep it open for the time being just in case I cannot make the Lenovo USB work.

This thread is PAUSED !

---

### Post by hans12345 on 2015-10-01
Finally, this solution with Win10 via UEFI boot, Ubuntu via Legacy (CSM) boot is my chosen solution for my Lenovo C260 (but I did get my ACER to work with UEFI).

See my thread:
[http://ubuntuforums.org/showthread.php?t=2294833](http://ubuntuforums.org/showthread.php?t=2294833)

---

