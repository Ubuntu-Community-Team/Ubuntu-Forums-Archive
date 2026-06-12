---
title: "[SOLVED] Added memory, dapper runs more slowly !!"
date: 2007-12-05
forum: Installation &amp; Upgrades
---

### Post by dbyrne on 2007-12-05
Very strange, although it rings a bell I can't quite figure out what the reason could be.

I'm running dapper drake (6.06) on a dual-cpu PIII 500Mhz/512Mb box that has got a whole new lease of life since being 'upgraded' from win2k :)

I decided that some additional memory might be a good idea, and replaced the 4x128Mb PC100 SDRAM sticks with 4x256Mb PC100 sticks - essentially identical except for the higher capacity. Same speed, neither ECC etc.

Now however the system is noticeably slower to use and feels very sluggish. For example opening a Terminal window from the desktop takes 5-10 seconds whereas previously it was instantaneous. The window pops up with a black background, but then nothing happens for a short while until the background goes to white and the shell prompt appears. Similar for other apps e.g. Firefox takes 5-10 seconds before anything appears on screen.

I've literally done nothing more than shutdown/replace memory/power up - should I do anything more ? BIOS check and top show all the memory being recognised. I'll probably put the old memory back in tonight just to get things back up to speed again until I figure out the answer/someone kind responds with blinding intuition or the benefit of bitter experience !!

---

### Post by MikeEvans on 2007-12-05
Could be a bad module.  You should run a memory test.  You could also test each module individually.

---

### Post by dbyrne on 2007-12-05
Great minds think alike ... left a memory test running when I left this morning, maybe it'll show something by the time I get home from work.

---

### Post by dbyrne on 2007-12-06
Found a bit of the problem - one of the modules WAS bad. However the system still runs slowly even with the orgininal memory installed ... at least I can troubleshoot it at the process level now.

---

### Post by MikeEvans on 2007-12-06
This sounds tricky. I'm wondering if you made any configuration changes after the initial RAM change out.   If not there is no reason it should be running slower, as far as I know.  Maybe someone with knowlege of what linux does when it detects RAM changes could confirm that.  One thing that might factor in here is the age of the hardware.  I'm talking about dust and corrosion build up.  If you haven't, give your RAM and the RAM slots a good cleaning.  Use compressed air for the slots and for the RAM use a standard pencil eraser (like on a #2).  After the eraser you could also wipe the connectors with a alcohol dampened paper towel.  If you notice debris in the slots use something non-conductive to get it out like a toothpick.  Don't use a brush.  

Something else to check is you swap file.  Just confirm that it is working.
```
swapon -s
```
Good luck  ;)

---

