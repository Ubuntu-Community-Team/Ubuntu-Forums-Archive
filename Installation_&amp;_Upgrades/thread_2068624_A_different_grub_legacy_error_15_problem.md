---
title: "A different grub legacy error 15 problem"
date: 2012-10-09
forum: Installation &amp; Upgrades
---

### Post by 316479 on 2012-10-09
I was  trying to install an 12.04.1 LTS system on a computer with
an existing 10.04.4 system.

I was trying to be very careful not to wreck my existing 10.04.4 
system so I did

        grub-install  /dev/sdb

where the separate boot partition for my new 12.04.1 system was on /dev/sdc1 and my existing 10.04.4 system had grub installed on /dev/sda

I was unable to boot using the grub installed on /dev/sdb,
I kept getting error 15 (file not found) when trying to load
stage 1.5   This error 15 did not correspond to any of the
Error 15 reports that I could find on the web.

THE SOLUTION

It appears that legacy grub does not correctly handle the case
of booting from an MBR that is on a different disk from the
/boot partition.  

My fix was to do

            grub-install /dev/sdc 

so grub was booting from the MBR of the disk that contained the /boot partition.  After changing the BIOS to boot from /dev/sdc
I was able to successfully boot my 12.04.1 system using
the legacy grub that I'd installed.

---

