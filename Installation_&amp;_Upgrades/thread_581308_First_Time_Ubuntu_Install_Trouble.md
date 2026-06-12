---
title: "First Time Ubuntu Install Trouble"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by snwbrder0721 on 2007-10-19
Hello everyone, I'm completely new to linux, so be gentle. Here's what I'm trying to do:

*Desired end result: I have an old machine I want to turn into a linux based "tivo", probably using "freevo"*

I formatted some old HDs to use in it, and figured using my main machine (HP, running XP, 2gb ram, 160gb HD, 3 ghz intel) I could just pop one in my external usb HD box and then pop the 7.10 live CD in and install to the external drive... apparently not. 

Ubuntu loads the CD in XP, "installs" then restarts. On restart I choose "install or select ubuntu" and the loading screen shows. It hangs up on the very same spot (tried it about 5 times now), after the loading bar goes back and forth it begins filling up like a typical loading bar and gets about 1 inch across the screen, then hangs up (not sure if that's useful info). 

I checked the CD integrity, it's good. I tried graphics safe mode, same result.

I haven't done any prep (i.e. partitioning, etc) since I don't want to do anything to my main machine, nor do I know what to do. I just want to install to the external drive, pop the external drive in the old machine, and get it to boot.

Is there a better strategy for this through the old machine? maybe a boot disk? It loads up the bios, but I can't get it to boot to the CD and I don't have a floppy to put in it to try another boot method.

Thanks for any help you can give me.

---

### Post by Original Brownster on 2007-10-19
Hi,
I don't think you will be able to use another machine to carry out the install and just transfer the hard drive, the set up routines will configure the os for the hardware on the first machine so it will not work on the old box.

What spec is the old box? To run ubuntu it will want to have a minimum 128mb ram and a 400mhz processor IMO
Is the bios so old there is no boot from cd option or will it just not boot from the cd? might be worth trying a cdr if you're trying a cdrw 
failing this there is a super boot manager you can download onto a floppy that will instigate a boot from cd.

---

### Post by djrobthaman on 2007-10-19
Sometimes, when the regular install CD fails you can download the "Alternate" install CD and that works.  Maybe if you give it a try it will work.

Also, I believe that there should be a way to alter how the liveCD actually boots up by adding extra parameters to (or taking some default parameters out from) the boot command.  I vaguely remember on the feisty install there being an "edit boot options" option or something.  If you find that, then you should see a long command that tells ubuntu how to load up.  Just delete anything refering to silent or splash and then it should show all the output.  That might help you figure out what the problem is.

While I'm going here, maybe you should disconnect all your hardware connected by usb.  That used to give problems sometimes.  Maybe it still does.

Other than that, I'm not sure of what else you could do.

---

