---
title: "I can't install Ubuntu due to some errors."
date: 2015-03-16
forum: Installation &amp; Upgrades
---

### Post by NistorCristian on 2015-03-16
Hello, I just bought a new laptop taday and I'm trying to install Ubuntu 14.04 64bit.

Here are my problems:

       I'm trying to install Ubuntu 14.04 on a new laptop. But  installation takes way too long. I'm at Detecting file systems ... and  the last message from terminal says:
  Mar 16 21:35:12 ubuntu kernel [5970.634780] rtl8821ae-0: rtl8821ae_phyPswitch_wirelessband(): <0-0> 2.4 G
Mar 16 21:35:12 ubuntu kernel [5970.634780] rtl8821ae-0: rtl8821ae_phyPswitch_wirelessband(): <0-0> 5 G
  Those 2 lines appear after each minute ... only those 2
  It has been more than 25 minutes.
  ...
  I tried to install again. And I get this message:
  /dev/sda contains GPT signatures, indicating that it has a GPT table.
However, it does not have a valid fake msdos partition table, as it should.
Perhaps it was corrupted -- possibly by a program that doesn't understand GPT
partition tables. Or perhaps you deleted the GPT table, and are now using an
msdos partition table. Is this a GPT partition table?
  I can choose Yes or No.
  EDIT:
  I tried to use Try ubuntu but it doesn't work. It simply sends me back to Boot from Cd.

Someone asked me: Is this a UEFI computer? Are you using 64 bit Ubuntu?                                                                              
                             Unfortunately I don't know if it is UEFI. Yes I'm using 64 bit Ubuntu. I just bought it today. It came with Free DOS                                                                       
                            When I have to select Try  Ubuntu without installing, Install Ubuntu at top of the screen is says:   GNU GRUB version 2.02~beta2-9ubuntu1 ... if that helps you                 

Thank you

---

### Post by grahammechanical on 2015-03-16
Is this machine normally sold with a version Windows 8. If so then it has a UEFI boot system and not a BIOS boot system. This wiki page will help understand the action we can take.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Regards.

---

