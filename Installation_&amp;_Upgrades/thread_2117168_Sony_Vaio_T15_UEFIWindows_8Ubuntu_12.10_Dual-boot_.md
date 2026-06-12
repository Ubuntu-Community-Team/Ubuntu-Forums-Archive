---
title: "Sony Vaio T15 UEFI/Windows 8/Ubuntu 12.10 Dual-boot can't boot Windows 8"
date: 2013-02-17
forum: Installation &amp; Upgrades
---

### Post by csete on 2013-02-17
Hello,

It sounds like many of these problems are not too unusual at the moment.  I picked up a new Sony VAIO T15 laptop.  This is a Windows 8 machine with a 1TB HD + SDD cache drive arrangement.  I used Windows Disk Management to resize the Windows space to allow Ubuntu 12.10 to be installed for dual-boot.  When I boot, I see the GRUB menu and I'm able to boot into Ubuntu (hooray!).  However, none of the Windows 8 menu items work for me (boo).  I get a variety of errors dependent on the menu item.  The error for the primary Windows 8 entry is a complaint about the "drivemap".

I ran boot-repair and took the default options, yielding a number of new UEFI menu items.  None of these items work either, yielding different errors.  The resulting boot info is located at [http://paste.ubuntu.com/1673959/](http://paste.ubuntu.com/1673959/) .  I'm not seeing any difference in behavior if I enable or disable secure boot.

Any help in getting Windows 8 booting for the point at which I need it would be greatly appreciated!

Thanks,
Craig

---

### Post by oldfred on 2013-02-18
Do you have secure boot off. And fast boot off?

Are you booting from the new entries Boot-Repair added? 

       grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
type of entry from Boot-Repair that should work.
'Windows UEFI loader'
Type of entry that does not work:
'Windows ...) (on /dev/sdXY)'

---

### Post by csete on 2013-02-18
Thanks oldfred.

While I could have sworn that I had disabled secure boot and had the same behavior, I attempted it again and it worked fine.  I'm now able to boot into Windows as long as secure boot is disabled.

Reading the Launchpad entry, I'm unclear if it is possible to fix things so that grub can chain to Windows 8 with secure boot enabled with some changes to grub configuration? 

Now that I've disabled fast-boot, is it possible to use the SSD for any caching in Ubuntu?

Thanks,
Craig

---

### Post by oldfred on 2013-02-18
Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)

Brand of computer does not really matter as it is the Intel standard.

Some of have either installed to SSD or have reimplemented it. I think fast boot is just the bypassing of the UEFI boot or the hibernation (or both).

 Intel SRT - Dell XPS Screen shots of Intel SRT screens & lots of details 
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2036204](http://ubuntuforums.org/showthread.php?t=2036204)

   Some info on re-instating  details in post #9
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2070491](http://ubuntuforums.org/showthread.php?t=2070491)

---

### Post by csete on 2013-02-24
Thanks for all of the information oldfred.  For the moment, I'm just going to ignore the SSD.  Somewhat a waste, but for the moment things are stable and I'd like to keep them that way.

---

