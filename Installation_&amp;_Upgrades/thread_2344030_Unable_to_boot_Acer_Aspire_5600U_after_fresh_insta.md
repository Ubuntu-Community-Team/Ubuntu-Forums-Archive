---
title: "Unable to boot Acer Aspire 5600U after fresh install of Ubuntu"
date: 2016-11-21
forum: Installation &amp; Upgrades
---

### Post by ravitejab4u on 2016-11-21
Hello all,

Need help in fixing my computer. It started as a fun project and became nightmare. I'm new to linux falvor of platforms. Need help in fixing my computer. I've installed Ubuntu from USB drive on my hard drive, after the installation when the computer is booted it displays message "**Reboot and select proper Boot Device or Insert Boot Media in selected device and press a key ".  **I tried boot repair tool with no luck. I'm pretty sure i might be doing something wrong but i had to give up on ubutnu and thought going back to windows OS. so, i created a bootable Windows OS USB and my computer does not recognize that either. So, i'm not sure what i have to do at this point. I would like the Ubuntu OS to be working if it is possible. Please help.

Here is the boot repair log. [http://paste2.org/7KJvfUse](http://paste2.org/7KJvfUse) 

Any help would be greatly appreicated.

-r

---

### Post by oldfred on 2016-11-22
You have an Acer with UEFI.

Acer has a unique requirement of setting an UEFI password and then enabling "trust" on the .efi boot files in the ESP - efi system partition from within the UEFI.
Some older threads mention downgrading UEFI to have it work. But newer threads say that newest UEFI from Acer works. So make sure you have current UEFI from Acer to avoid issues.

That is actually a lot better than many systems that use description as part of boot which is specifically NOT allowed by UEFI standard. And only valid description is "Windows Boot Manager". So many work arounds depending on configuration have been found.

 Acer Cloudbook shows screen for selecting trust
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392](http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392)

Instructions in every thread, seem to be same, but some give more details or explain it better.
 Acer Trust Settings - details:
[https://ubuntuforums.org/showthread.php?t=2342323](https://ubuntuforums.org/showthread.php?t=2342323)
[http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
[URL="http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757"]http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757
[/URL]
 Acer Very latest UEFI/BIOS works, downgrade not required:
[http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141](http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141)
Acer E5-573G, downgrade UEFI, supervisor password & trust on Ubuntu efi boot files.
[http://askubuntu.com/questions/706912/getting-a-black-screen-when-installing-or-live-booting-ubuntu-any-version-in-m?noredirect=1#comment1039248_706912](http://askubuntu.com/questions/706912/getting-a-black-screen-when-installing-or-live-booting-ubuntu-any-version-in-m?noredirect=1#comment1039248_706912)
Acer Aspire E15 will not dual boot, many details Trust settings in step 35
[http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot](http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot) [URL="http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757"]
[/URL]

---

