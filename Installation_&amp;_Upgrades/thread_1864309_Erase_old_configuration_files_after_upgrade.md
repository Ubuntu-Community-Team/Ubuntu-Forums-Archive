---
title: "Erase old configuration files after upgrade"
date: 2011-10-18
forum: Installation &amp; Upgrades
---

### Post by marsgorski on 2011-10-18
Hi everyone,

I just upgraded from 11.04 to 11.10, but the process didn't quite finish: Towards the very end of installing configuration files, the system spent hours (>12hrs) trying to recompile the squidguard data base (a while ago I tried, unsuccessfully, to configure squidguards, and I created this huge database that takes hours to compile). Ultimately, the screen froze so I rebooted using ctrl+alt+f1 and executing sudo reboot. The system seems to be working normally (so far), but the upgrade process never got to the "delete old configuration files" stage. Is there a way (and a reason) to erase this files? What should I do?

Thanks to all

---

### Post by collisionystm on 2011-10-18
> **marsgorski said:**
> Hi everyone,

I just upgraded from 11.04 to 11.10, but the process didn't quite finish: Towards the very end of installing configuration files, the system spent hours (>12hrs) trying to recompile the squidguard data base (a while ago I tried, unsuccessfully, to configure squidguards, and I created this huge database that takes hours to compile). Ultimately, the screen froze so I rebooted using ctrl+alt+f1 and executing sudo reboot. The system seems to be working normally (so far), but the upgrade process never got to the "delete old configuration files" stage. Is there a way (and a reason) to erase this files? What should I do?

Thanks to all

It depends on where they are I guess. You could try

sudo apt-get clean

to clear out downloaded packages

---

### Post by collisionystm on 2011-10-18
If you are trying to located big files on your harddrive to help hunt down things, open terminal

```
sudo bash
```

View the folders and files by size. Largest to smallest.

```
du -k /* | sort -nr | cut -f2 | xargs -d '\n' du -sh
```

Hopefully you can find your way from there?

---

### Post by marsgorski on 2011-10-18
The real noob in me is going to come out here: I executed the du command but I cannot scroll up a certain number of lines, so I cannot scroll up to those big-size folders :s

Alternatively, would using BleachBit somehow be helpful here?

Thanks

---

### Post by collisionystm on 2011-10-19
> **marsgorski said:**
> The real noob in me is going to come out here: I executed the du command but I cannot scroll up a certain number of lines, so I cannot scroll up to those big-size folders :s

Alternatively, would using BleachBit somehow be helpful here?

Thanks

You can go into terminal preferences and set the scrollback to unlimited

be careful with bleachbit, I have never used it but hear you can break things easily.

---

### Post by marsgorski on 2011-10-20
Thanks for the tip. I have looked at the output of the command you suggested and I see some potential folders that maybe I could erase. But I am not absolutely sure of what exactly I would be erasing so I didn't I also ran successfully apt-get clean, but I'm not sure if that erased everything that would have been erased during to upgrade to 11.10.

I am also inclined to run "apt-get autoclean" and "apt-get autoremove", but when I try to run these commands I get the error 
```
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
```

So I follow the terminal's suggestion and run "dpgk --configure -a", every thing seems to be running normal but then it gets to the point ```
Re-building SquidGuard database (this can take a while)...

``` which is exactly the same point I interrupted the upgrade to 11.10 (as I explained in my first post.) So I press ctrl+C and it skips that step, and the command "dpkg --configure -a" finishes the rest. Then I am able to run "apt-get autoclean" and "apt-get autoremove" but for both of these It tries to rebuild the squidguard database again, so I have to interrupt the process. However, it apparently it does seem to remove a big chunk of things. Should I consider my problem solved now? The original problem being manually performing the "removing old configuration files" step during the upgrade process.

Thanks for the help, I really appreciate it!

---

### Post by arpanaut on 2011-10-20
I know nothing about squid or squid-guard but I found the following page that may help:

[https://help.ubuntu.com/community/SquidGuard](https://help.ubuntu.com/community/SquidGuard)  (old info but the troubleshooting  bit should work)

Scroll down to the troubleshooting section and see what's up.
Sounds like it may be permission problems or database errors.
Also some good linkage at the end of page.

---

### Post by marsgorski on 2011-10-24
Here's a surprising development:

I can open the Update Manager, and it tells me my upgrade probably did not finalize (which is correct), so it asks if I want to resume it!! That's very cool because now I can let it finish and clean up the old files. The problem is that I haven't been able to que rid of squid, so the upgrade process still gets stuck for many many hours at "Re-building SquidGuard database (this can take a while)..." I'll continue to look around for information on how to disable SquidGuard, so far I haven't had much luck.

---

### Post by slickw on 2012-10-19
I ran into the same issue when upgrading from Natty to Precise. My case is a little different than your, but maybe this will help.

I took the default squidGuard.conf file from the Precise package and replaced the config file in /etc/squid/.
Then I ran the "dpkg --configure a" again and it completed without any other issues.

Once you get the update completed, I would remove the squidGuard package, if you are not using it, so you don't get stuck here again.

---

### Post by marsgorski on 2012-10-19
Thanks a lot for the response. I was able to to solve the issue eventually. If I remember correctly, I made a fresh install of ubuntu from a usb.

---

