---
title: "Can't start up windows on 2nd hard drive after upgrade to 10.04"
date: 2010-06-06
forum: Installation &amp; Upgrades
---

### Post by duhglas on 2010-06-06
Hey I just upgraded to 10.04. I went with the option of upgrading grub as well, should of just stuck with the old one I guess. I have 2 seperate physical hard drives, and now I can't get vista running on my other drive. I get to grub, choose the run vista option, and now it just blinks one underscore line in the top left corner of the black screen, and goes nowhere. When I was installing the upgrade, and when I got to the grub upgrade i tried to upgrade all teh different options in grub. All of them worked except the last one, and it warned me, that one of boot options in grub didn't install properly and may cause my OS not to start up. I guess that must of been the vista option.

I'm wondering what I should do, I was thinking of reinstalling grub, but I'd appreciate some input before i go making another rash decision. Thanks ahead of time for the input.

---

### Post by Mark Phelps on 2010-06-07
If you have Vista installed to a separate drive, suggest you do the following:
1) Disconnect the Ubuntu drive
2) Insert a Vista Repair CD, boot from that
3) Run startup repair until it finds no more problems (usually, three passes are enough)
4) Reboot from the Vista drive, confirming it will work
5) Reconnect the Ubuntu drive -- but boot from that
6) Once inside Ubuntu, open a terminal and enter "sudo update-grub".  This will auto-generate the grub.cfg file and add an entry for Vista.
7) Reboot and you should be OK

Since you probably do NOT have a Vista Repair CD, go to the site below, download the proper image, and burn it to CD:

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/")

---

