---
title: "boot live image into text mode?"
date: 2011-12-07
forum: Installation &amp; Upgrades
---

### Post by gcbzzzz on 2011-12-07
I want to start ubuntu 11.10 live image with text mode.

so i tried the old trick of appending "init 1" to the boot... but it seems i'm too old that that's not the way to do it.

my thinkpad e425 seems to boot ok until the graphic card get's used. then the screen just goes blank. i even get the boot up sound at some point. but then i just hold power 4sec and turn it off to try again.

it's probably setting the main screen as the VGA port or the HDMI one... i can probably work this out on xorg or the module after i have a system up.

but how can i even boot without graphics to use the text mode installer?

...is there even a text mode installer yet?

...and damn the first person that though splash boot would be cool. just cost us 100 reboots more per bogus install with zero added benefit.

update: appending "Single" to the kernel options also does nothing to help me with this. As soon as the boot messages are done and i would have either Login or gdm, i get nothing on the screen.

update 2: there's NO option on the boot menu. typing even "rescue" gives me a not found message.

update 3: adding "xforcevesa radeon.modeset=0" did the trick. don't know wich one as i used both...

---

### Post by darkod on 2011-12-07
It seems you found a parameter that helped booting, just to remind you that the alternate install image is text based and installs the same system as the desktop image (live cd).

---

### Post by gcbzzzz on 2011-12-08
about the alternate install... i already downloaded one huge ISO file, that all it needs is some boot parameters and anaconda, that uses what? 3-4mb total?

it's kinda crazy to download yet another huge iso with mostly the same data... but i will make a mental note to always download that one first. if i can remember that next year when i will do another install :/

I didn't find a solution, but i solved my need for that. sadly i had to use a serial cable and console...

it was a bad SD card. some hashes where bad so it locked up trying to fix some ethernet firmware over and over... never seem something like that before. just flashing it again solved the issue.

---

### Post by drs305 on 2011-12-08
I've read there is an unofficial kernel option in Ubuntu that you can add to the end of the 'linux' line: *text*
That should boot it to the terminal login screen, if that is what you are looking for. 

If you want to make it permanent, add it to the *GRUB_CMDLINE_LINUX_DEFAULT=* line in /etc/default/grub and then run "sudo update-grub".

---

### Post by gcbzzzz on 2011-12-12
> **drs305 said:**
> I've read there is an unofficial kernel option in Ubuntu that you can add to the end of the 'linux' line: *text*
That should boot it to the terminal login screen, if that is what you are looking for. 

If you want to make it permanent, add it to the *GRUB_CMDLINE_LINUX_DEFAULT=* line in /etc/default/grub and then run "sudo update-grub".

that was what i was looking for. my blame for being old. i was used to "1" or "single" instead of "text". thanks

---

