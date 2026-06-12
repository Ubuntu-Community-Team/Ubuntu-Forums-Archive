---
title: "Problem with installation possibly related to graphics card."
date: 2016-11-27
forum: Installation &amp; Upgrades
---

### Post by amirpas on 2016-11-27
Okay,

so i got my usb with ubuntu gnome all set up, but one problem:
when i press on "check for errors on drive" or "try without installing"  my screen goes black until i reset my comp and my monitor dosent get a signal from the computer (it shows as if nothing is connected to it)
i suspect that its because i have a gtx 970 and some google searches point out thats its not officially supported.
but i also tried disabling it and it still shows nothing.
can you guys please tell me what else to try?

also im new btw so sorry if i wont get you.

---

### Post by oldfred on 2016-11-27
You will want the proprietary driver once installed.
But to install you need to add nomodeset as a boot parameter.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)

Older now obsolete install, but issues should be similar.
      Asus z97-A with nVidia GTX 970 Maxwell Ubuntu  15.04
[http://askubuntu.com/questions/615896/ubuntu-15-04-uefi-cannot-install-blank-screen-no-signal?noredirect=1#615896](http://askubuntu.com/questions/615896/ubuntu-15-04-uefi-cannot-install-blank-screen-no-signal?noredirect=1#615896) 

  4 Multi Monitor Setup Nvidia GTX 970 works finally
[https://ubuntuforums.org/showthread.php?t=2338494](https://ubuntuforums.org/showthread.php?t=2338494)
NVIDIA 970  with 14.04 - Bucky Ball
[https://ubuntuforums.org/showthread.php?t=2336142&p=13540433#post13540433](https://ubuntuforums.org/showthread.php?t=2336142&p=13540433#post13540433) 
    [URL="https://wiki.ubuntu.com/Kernel/KernelBootParameters"]
[/URL]

---

### Post by amirpas on 2016-11-28
Thank you!

---

