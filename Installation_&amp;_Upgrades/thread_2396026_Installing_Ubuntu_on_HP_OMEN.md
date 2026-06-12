---
title: "Installing Ubuntu on HP OMEN"
date: 2018-07-10
forum: Installation &amp; Upgrades
---

### Post by SAAlqallaf on 2018-07-10
Hi, 

I just bought a new gaming machine HP OMEN and tried to replace the preinstalled WIN10 with ubuntu 18.04 but with no luck. The machine has a 256GB SDD and 1TB HDD with UEFI. I disabled the Secure boot but the installer won't start (just freezes up at the initial steps of the setup). I then changed the boot option to **nomodeset -- **and the installer started perfectly. After installation was done (first time was on the HDD). After rebooting the system started in GRUB Bash screen. Did the installation again on the SDD, same thing  just happened again. I tried to do boot-repair and it gave me that there was an error but no repair was done. Changed the partition (moved /home to HDD), still the same? :frown::frown::frown: I don't know what to do?

---

### Post by yancek on 2018-07-10
The link below is the Ubuntu documentation on dual booting with windows 10 using UEFI.  Even though you are not using windows, reading the first part, general principles, should be useful.

 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

You indicated that you used boot repair and saw an error but did not post what the error was so there's not much we can do but guess.  The boot repair software has an option to Create BootInfo Summary.  That's what you should do then post the link you get when it finishes here at the forums so we have some information on your system.

---

