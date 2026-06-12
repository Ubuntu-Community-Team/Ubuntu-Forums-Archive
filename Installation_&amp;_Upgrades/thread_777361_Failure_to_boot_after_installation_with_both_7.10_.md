---
title: "Failure to boot after installation with both 7.10 and 8.04"
date: 2008-05-01
forum: Installation &amp; Upgrades
---

### Post by starlight763 on 2008-05-01
Hi Guys,

I have been having trouble for about 2 weeks with this. I recently purchased a new motherboard/cpu/RAM (see specs below). Now, it all seems to be fine with Windows XP, however, I have been completely unsuccessful in getting linux to work on it.

My new kit is as below (see link for more info): -

J&W IP35 Pro Motherboard 
Intel Core 2 Duo E6750 "LGA775 Conroe" 2.66GHz (1333FSB)
OCZ 2GB (2x1GB) PC2-8500C5 1066MHz SLI-Ready Edition DDR2

[http://www.overclockers.co.uk/showproduct.php?prodid=BU-106-OC&groupid=701&catid=339&subcat=944](http://www.overclockers.co.uk/showproduct.php?prodid=BU-106-OC&groupid=701&catid=339&subcat=944)


My existing kit: -

ATI Radeon X1800XT
2 Western digital SATA drives
1 Maxtor PATA drive
1 Sony DVD-RQ PATA drive


I initially got the same problem that I have seen reported elsewhere, in that I could not even boot the LiveCD and received the error "ata3.0 failed to set xfermode". However, after following the advice I saw in some other posts I set the "all_generic_ide" option when booting the LiveCD and it worked.

I was then able to successfully install the OS. However, it then fails to boot even if I specify the "all_generic_ide" option to GRUB. I have tried this with both Kubuntu 7.10 and 8.04. With 8.04 I managed to get it to boot after removing my PATA devices but even then it wouldn't start KDE. However, even if I got KDE working, that is not an acceptable work around because I need my CD-ROM. 

Any ideas? I'm all out and was about to send my motherboard back to get a different one! It seems the JMicron chip on Intel chipset motherboards has been a general source of problems for linux in the past.

Thanks in advance for any help you can provide!

---

