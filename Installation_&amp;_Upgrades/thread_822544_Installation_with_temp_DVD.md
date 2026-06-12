---
title: "Installation with temp DVD"
date: 2008-06-08
forum: Installation &amp; Upgrades
---

### Post by Claude.Hubert on 2008-06-08
Hello everyone,

As part of a effort to bring help to an impoverished village in Romania, I am preparing several PCs (PIII 800 Mhz w/256 Mb RAM) donated by a friend that will be given to the village's school. (they'll be used by kids of all grades). I've chosen to install Ubuntu 8.04 LST desktop edition for a number of reasons (available in Romanian, free, includes good set of software and tools, etc.), but I only have 1 DVD DL burner (I've just upgraded mine to a faster one, so I'm donating my previous drive).

I proceeded to build the 1st machine (which will be the teacher's machine), performed all the updates, checked that it works (which it does, sound and all), switched the language to Romanian, rebooted to make sure everything was still ok, then I shut it down and pulled the DVD drive out.

Then I put the DVD drive in the 2nd PC, installed Ubuntu just as I did with the first one (updates, change language, etc), then shut it down and removed the DVD drive. I rebooted the machine but keep ending up in the BusyBox. I know it has to do with the fact the DVD drive is no longer found, but I don't know how to override it or how I might fix it.

I've spent all day reading throught the forums trying to figure out how I might do this, and I've tried a number of things, but I just crashed my test machine (not surprising as I'm a novice when it comes to Linux).

Can anyone help and let me know what I need to do for Ubuntu to boot normally into the GUI after the installation is complete and I've removed the DVD drive?

Any help would be greatly appreciated, plus it's for a good cause.

Kind regards,
Claude.

---

### Post by logos34 on 2008-06-08
> **Claude.Hubert said:**
> then shut it down and removed the DVD drive. I rebooted the machine but keep ending up in the BusyBox. I know it has to do with the fact the DVD drive is no longer found, but I don't know how to override it or how I might fix it.

go into the bios and check the device boot order, set it to 1) hard disk.  maybe even though the dvd drive is no longer there it's still listed first and causing the error

There might also be a workaround/solution in [this thread]("http://ubuntuforums.org/showthread.php?t=765195&highlight=busybox") (yes it's long), but you've probably already checked it out

---

### Post by Claude.Hubert on 2008-06-09
> **logos34 said:**
> go into the bios and check the device boot order, set it to 1) hard disk.  maybe even though the dvd drive is no longer there it's still listed first and causing the error

There might also be a workaround/solution in [this thread]("http://ubuntuforums.org/showthread.php?t=765195&highlight=busybox") (yes it's long), but you've probably already checked it out

Already tried that thread and I've checked the BIOS as well, but it didn't work.

Just as an FYI, the computer is an older Compaq Deskpro ENP866 (866 Mhz PIII) with 256 Mb RAM and a 15 Gb hard drive.

---

### Post by mc4man on 2008-06-09
Usually in the bios setup there is a listing of the drives with a way turn off or disable any of them individually. Look for secondary drive - it may say cd-rom or something similar. You should be able to highlight it, press enter and select off, disable, ect. Don't know if it would help, worth trying.
I would try this with drive still connected

---

### Post by Claude.Hubert on 2008-06-13
None of the settings in the bios have changed anything. If there's anyone out there who can help, it would be greatly appreaciated.

Kind regards
Claude Hubert.

---

### Post by Claude.Hubert on 2008-06-30
In the end, I could not get the computers to boot correctly without the DVD drive, so as a last ressort I went out and purchased a DVD drive for each of the computers, which I then installed - Problem solved... Not quite how I had planned on getting it to work, though, but at least it's for a good cause...  :-)

---

