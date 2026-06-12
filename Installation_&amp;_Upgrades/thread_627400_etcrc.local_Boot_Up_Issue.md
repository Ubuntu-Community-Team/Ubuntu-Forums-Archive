---
title: "/etc/rc.local Boot Up Issue"
date: 2007-11-30
forum: Installation &amp; Upgrades
---

### Post by arch3angel on 2007-11-30
I want to first say thank you for a great distro, all my computers in my house work flawless.  However, my server at work has it's problems...

This is a brand new server running all Intel based parts.  [Raid 5 (4 - 250GB SATA Drives), Xeon 3.0Ghz, 2GB RAM]

First install we tried 6.06 LTS 64bit Server (Install went through no problems), we tried to patch the kernel with GRSecurity and during the recompile no major issues.  When we went to reboot to the new kernel it would not boot.  Surfing the net we decided to back down to the 32bit version.

Reformatted the system and installed 6.06 LTS 32bit Server and just as the 64bit the install went fine.  We decided to hold off on GRSecurity till we have done more testing on our development machine.

During the boot up process it seems hang on "Running boot scripts (/etc/rc.local)" - I figured it was just running through its new setup and I left it alone.  Came back about 15-20 minutes later to find it still was at that stage.  I tried to reboot the system which resulted in the same thing.  On that reboot I hit Enter and the login prompt appeared, I tried to log in and it would not let anything be typed.  Then all of a sudden a bunch of login prompts appear and then login failed.  I typed it slow and it allowed me to log in however it was responding extremely slow.

If I go alt-f2 the login prompt is ready and it responds normal, once logged in it responds normal for the first few commands and then it begins to do this extremely slow response to my commands.

I was able to get SSH setup so I went back to my desk and tried SSH.  This logged in perfect and never had reduced response, used it all night without fail.

I have researched forums, google, friends, all without a solution.  I know log files will be helpful for everyone to help with a solution, but I am at home now and do not have access to those now.  If someone wants to view a certain log file please let me know and I will post it very quickly.

Any and all help is greatly appreciated because I have to get this server into production before the end of the weekend.

Thank You!!!

---

### Post by arch3angel on 2007-11-30
I know it has not been very long since the post and I do appologize, but this matter is really holding me up and I am in a bind.  

Can someone please help...

---

