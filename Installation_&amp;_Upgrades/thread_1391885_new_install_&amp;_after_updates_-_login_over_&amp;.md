---
title: "new install &amp; after updates - login over &amp; over"
date: 2010-01-27
forum: Installation &amp; Upgrades
---

### Post by mikebp on 2010-01-27
Brand new install 9.10. Success. Connected and downloaded a slew of updates. Required Restart.
 
After restart, I seem to be in an infinite loop of logging into the Desktop. - so far 10+ times. After each login, it appears to doing something briefly - then resets the display - then back to the desktop login prompt again.
 
???? IS this a fault or is this normal behavior as it installs each update....???
 
HELP!! :confused:

---

### Post by oldfolks on 2010-01-27
I had the same thing happen to me, had to finally hit reset on computer and the next startup was okay.
I only hope it doesn't happen again.
Remedy ?????

---

### Post by lallalla on 2010-01-27
I stopped updating my system after a similar experience and it has been very stable. for some reason I tried just one or two minor updates recently and since then my screen cannot be locked. SO no more updates for me until I am really bored and do not mind reinstalling the whole system......

---

### Post by dabl on 2010-01-27
There are several known causes of "login loops", including:

- full filesystem
- running X as root (changes permissions on ~/.ICEauthority and ~/.Xauthority)

---

### Post by mikebp on 2010-01-27
I also found after extensive hunting that CRT's/video settings dependancies so I did a complete re-installed - rebooted many times successfully - then did all updates - and tested again - all ok.  
 
From everything I read it appears that changing display settings is the root cause.  I will not change video settings until I review precisely all the gotchas regarding makingthese changes so the infinite login loop does not happen again.
 
....haven't made any video changes yet - until I fully confirm that the boot is stable (a week or so).
 
If anyone knows the correct & safe way to modify display settings w/o causing this login loop - please post it here!!!
 
Thanks!!

---

### Post by dabl on 2010-01-27
> **mikebp said:**
> 
 
If anyone knows the correct & safe way to modify display settings w/o causing this login loop - please post it here!!!
 


That's going to depend on your video hardware and driver.  Can you post the "vga" section of the output of ```
lspci -v
```?

---

### Post by mikebp on 2010-01-28
Here's the output. I REALLY need to change the display settings - my eyeballs  are falling out!  :sad:

01:00.0 VGA compatible controller: nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro] (rev 15)
    Subsystem: nVidia Corporation Device 0001
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 11
    Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
    Memory at f2000000 (32-bit, prefetchable) [size=32M]
    Expansion ROM at fe9f0000 [disabled] [size=64K]
    Capabilities: <access denied>
    Kernel modules: nvidiafb, rivafb

---

### Post by surnj1 on 2010-01-31
I partially solved this problem by pressing :
wait for 3 cycle then
first: Alt+Ctl+F1 then
second: Alt+Ctl+F9

then it will bring me to login /password page

I have to  find the final solution so it will not occur on next reboot.

---

