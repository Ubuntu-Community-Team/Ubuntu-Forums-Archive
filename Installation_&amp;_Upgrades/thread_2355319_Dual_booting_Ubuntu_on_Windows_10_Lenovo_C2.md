---
title: "Dual booting Ubuntu on Windows 10 Lenovo C2"
date: 2017-03-11
forum: Installation &amp; Upgrades
---

### Post by searcheruk on 2017-03-11
Hi there

New to hear - have in the past succesfully dual booted 2 laptops in the past with Windows and Ubuntu - have now acquired a Lenovo C2 and wanted to see if I could do the same  as I really prefer Ubuntu - any help would be appreciated 

Thanks in advance

---

### Post by oldfred on 2017-03-11
Is this a new UEFI system? What are specs. Google search says the C2 is a phone?

If so a bit more complex as now you have both the new UEFI boot mode and the legacy BIOS/CSM boot mode.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode  

And then UEFI uses the new gpt partitioning, not the 35 year old MBR configuration.

      
 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

See also link below for lots more info on UEFI install.

---

### Post by searcheruk on 2017-03-13
Thanks for replying - sorry it was a C20 compact Desktop but I think your info is sound [http://www3.lenovo.com/gb/en/desktops-and-all-in-ones/ideacentre/c-series-/Lenovo-C20-00/p/FF3KF3C0224](http://www3.lenovo.com/gb/en/desktops-and-all-in-ones/ideacentre/c-series-/Lenovo-C20-00/p/FF3KF3C0224)

If you have any other info it would be appreciated

Thank you for your time :)

---

### Post by oldfred on 2017-03-13
General install instructions are in link in my signature.
Be sure to follow the steps.

Some other Lenovo. Issues often common by brand, but these are probably older models.
 Lenovo Thinkpad E531 - turn off locked boot order setting in UEFI
[http://ubuntuforums.org/showthread.php?t=2255746](http://ubuntuforums.org/showthread.php?t=2255746)
[SOLVED] Error 1962: No operating system found. Lenovo K430  only boot Ubuntu, rename files
[URL="http://ubuntuforums.org/showthread.php?t=2243715"]http://ubuntuforums.org/showthread.php?t=2243715
[/URL]
 Lenovo rename files
[http://ubuntuforums.org/showthread.php?t=2302170](http://ubuntuforums.org/showthread.php?t=2302170) 

Some Lenovos comes with a physical switch that enables you to select which graphics adapter to use.
 Lenovo Z510 Laptop & Ubuntu 
[http://ubuntuforums.org/showthread.php?t=2232124](http://ubuntuforums.org/showthread.php?t=2232124)
Installing GNU/Linux on a 2014 Lenovo Thinkpad X1 Carbon UEFI/BIOS suspend to RAM issue
[http://mako.cc/copyrighteous/installing-gnulinux-on-an-2014-lenovo-thinkpad-x1-carbon](http://mako.cc/copyrighteous/installing-gnulinux-on-an-2014-lenovo-thinkpad-x1-carbon)

---

