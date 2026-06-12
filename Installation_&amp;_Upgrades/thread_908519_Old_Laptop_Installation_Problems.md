---
title: "Old Laptop Installation Problems"
date: 2008-09-02
forum: Installation &amp; Upgrades
---

### Post by fueljeta on 2008-09-02
I have an old Averatec 3250h that I am trying to put Ubuntu on.  I downloaded the newest version today and no matter what I do I can't pass the command prompt of the 'running local scripts' line.  At the command prompt, startx gives me the monitor error (on the install menu option) and on the livecd option it just hangs.  This is my second attempt at installing linux on this laptop and the second time I am close to saying forget it.  I get a 'no monitor found' error and have tried to edit the file with the refresh rates but my file system doesn't work like the others on here that have had issues.  
Any help, please?

---

### Post by oilchangeguy on 2008-09-02
define old laptop. system specs please.

---

### Post by fueljeta on 2008-09-02
> **oilchangeguy said:**
> define old laptop. system specs please.
It's an AMD Athlon XP-M 2200+ (1.5Ghz) running XP SP3 on 1 GB of ram...not that old.  Just tired of XP and I want it gone.  I want a clean install and a decent laptop back.  :-k

Just to be more specific...I never get to any setup screens.  I never set the time zone or have the option to format.  If I try it from the live cd it stops dead after blinking 4 times and I get *Running local boot scripts...  then nothing else.  Have to hard reset.
Upon running the installation it ends up at a command prompt and if I type xstart, I get a 'no screen error' so, I try to edit the resolution by typing the following:
sudo vim /etc/X11/xorg.conf
then, I am supposed to find the monitor section by using the up and down keys, well all I have is a black screen with little blue ~ down the left side and all the way at the bottom there is this: "etc/x11/xorg.conf" [NEW DIRECTORY]
Where do I find the 'monitor section'?  I am totally lost lost.
Help!

---

### Post by oilchangeguy on 2008-09-02
> **fueljeta said:**
> I have an old Averatec 3250h that I am trying to put Ubuntu on.  I downloaded the newest version today and no matter what I do I can't pass the command prompt of the 'running local scripts' line.  At the command prompt, startx gives me the monitor error (on the install menu option) and on the livecd option it just hangs.  This is my second attempt at installing linux on this laptop and the second time I am close to saying forget it.  I get a 'no monitor found' error and have tried to edit the file with the refresh rates but my file system doesn't work like the others on here that have had issues.  
Any help, please?

as good as most versions of linux are, they're not a cure-all. some computers trying to get linux installed is just more trouble than it's worth. i'd suggest back up your data, and do a fresh xp install. and this time keep it maintained, and use up to date virus and spyware protection. yes windows has it's faults, it's a fine operating system as long as it's properly maintained. and all of your hardware and software will work with out having to pull your hair out.

---

### Post by fueljeta on 2008-09-02
Bump.

---

### Post by fueljeta on 2008-09-02
> **oilchangeguy said:**
> as good as most versions of linux are, they're not a cure-all. some computers trying to get linux installed is just more trouble than it's worth. i'd suggest back up your data, and do a fresh xp install. and this time keep it maintained, and use up to date virus and spyware protection. yes windows has it's faults, it's a fine operating system as long as it's properly maintained. and all of your hardware and software will work with out having to pull your hair out.

I am a Windows system builder and very very familiar with the O/S and the proper maintenance of the PC.  I did a clean install less than a year ago and upon doing the updates the system slows right down again.  I think that Windows builds a good product but I wanted to try something new.  So, no hope for Linux?

---

### Post by oilchangeguy on 2008-09-02
> **fueljeta said:**
> I am a Windows system builder and very very familiar with the O/S and the proper maintenance of the PC.  I did a clean install less than a year ago and upon doing the updates the system slows right down again.  I think that Windows builds a good product but I wanted to try something new.  So, no hope for Linux?

in doing the custom updates don't install the direct x updates, just do the critical, hardware, and media player 11.

---

### Post by fueljeta on 2008-09-02
> **oilchangeguy said:**
> in doing the custom updates don't install the direct x updates, just do the critical, hardware, and media player 11.
Really, I was hoping to just try out Linux and came here for help.  My computer only running the criticals now and it's still slow.  Seems that Adobe Acrobat Viewer kills this thing, but again, it's beside the point.  Just wanted to try the Linux. :popcorn:

---

### Post by mocoloco on 2008-09-02
As Yoda put it "I cannot teach him, the boy has no patience."  You're thread was started less than an hour ago and you're already bumping.  :)

Have you tried starting the liveCD in "safe graphics mode" (by hitting F4)?  Have you tried any of the numerous boot options like vga=771, noapic, etc?  From the boot menu hit F1, then F6 to see some of them.

Have you searched [these forums]("http://ubuntuforums.org/showthread.php?t=14025") or [googled]("http://www.linux-laptop.net/averatec.html")?  I know those results are a couple of years old but I would imagine things would be better now, now worse.

If you're interested enough to get this far don't give up now, the set up is usually the toughest part, then it's all fun from there :D

---

### Post by fueljeta on 2008-09-02
> **mocoloco said:**
> As Yoda put it "I cannot teach him, the boy has no patience."  You're thread was started less than an hour ago and you're already bumping.  :)

Have you tried starting the liveCD in "safe graphics mode" (by hitting F4)?  Have you tried any of the numerous boot options like vga=771, noapic, etc?  From the boot menu hit F1, then F6 to see some of them.

Have you searched [these forums]("http://ubuntuforums.org/showthread.php?t=14025") or [googled]("http://www.linux-laptop.net/averatec.html")?  I know those results are a couple of years old but I would imagine things would be better now, now worse.

If you're interested enough to get this far don't give up now, the set up is usually the toughest part, then it's all fun from there :D

That's a great link and I will have a look at it.  I also have tried the alternate boot options like safe-graphics and the vga=771 option.  Neither of those worked.  I read and read prior to posting here and search the archives.  I did not find the averatec link but again, I will look at it.  I'm mostly :rolleyes: patient...I just happen to be on the computer today working on this, today.  This is fast forum!

---

