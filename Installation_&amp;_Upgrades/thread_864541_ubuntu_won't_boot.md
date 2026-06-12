---
title: "ubuntu won't boot"
date: 2008-07-19
forum: Installation &amp; Upgrades
---

### Post by snowe2010 on 2008-07-19
"
I upgraded to ubuntu 8.01 or whatever it is a couple months ago, and it suddenly wouldn't start anymore. It would get to the black screen with the loading bar and the orange bar would just move back and forth never loading. Well I let it sit for a couple months because i didn't know what to do and then i started it up the other day. It worked and then when I shut it off it wouldnt' work anymore. Now when I can get it to the loading screen and to load it, it says at the bottom while it is loading that it is performing a check. If i choose to skip the check then it goes to a black screen with white text and says:
Starting up ...
Loading, please wait...
usplash: Setting mode 1600x1200 failed
usplash: Setting mode 1280x1024 failed
usplash: Setting mode 1152x864 failed
usplash: Setting mode 1024x768 failed
usplash: Using mode 800x600
kinit: name_to_dex_t(/dev/disk/by-uuid/4fc30ad1-7fd0-41d4-ad72-b7f35e6e2fd5) = sda5(8,5)
kinit: trying to resume from /dev/disk/by-uuid/4fc30ad1-7fd0-41d4-ad72-b7f35e6e2fd5
kinit: No resume image, doing normal boot...

Ubuntu 8.04.1 tylersubuntu tty1

tylersubuntu login: 


then when I put my username and password it it says all this information about my system and then it just stays in the terminal without loading any sort of desktop or login screen or anything. I think its called a BIOS screen?



Then if I turn off my computer and start it up again sometimes it won't load anything and the orange bar just moves back and forth.. Several on/offs later... I let it perform the check I was talking about earlier,it says in orange letters
Routine check of drives: /dev/sda1...
press ESC to skip 72%(stage 1/5,2953/21171)

at the loading screen and when it gets 72% it goes to that black screen again and says


entry 'X0' in /tmp/.X11-unix (1916929) has an incorrect filetype (was 6, should be 2)

/dev/sda1: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
(i.e., without -a or -p options)
fsxk died with exit status 4
Checking drive /dev/sda1: 72% (stage 2/5, 2953/21171)
[fail]
then in a red star it says
* An automatic file system check (fsck) of the root filesystem failed. A manual fsck must be performed, then the system restarted. The fsck should be performed in maintenance mode with the root filesystem mounted in read-only mode.

then in an orange star it says

*The root filesystem is currently mounted in read-only moed. A maintenance shell will now be started. 
After performing system maintenance, press CONTROL-D
to terminate the maintenance shell and restart the system.
bash no job control in this shell
bash: groups: command not found
bash: lesspipe: command not found
bash: Command: command not found
bash: The: command not found
bash: dircolors: command not found
bash: Command: command not found
bash: The: command not found
root@tylersubuntu:~#

and I can't find anything on the internet to fix it. Please help.
"

okay i used init 1 and it went through all these commands and now i have a blue screen with a white window that says 
could not start the x server (your graphical environment) due to some internal error. ... In the meantime this display will be disabled. Please restart GDM when the problem is corrected.
and then right below it two black bars came up showing part of the terminal.

"tylersubuntu login: "
is in one of the black bars

what do I do now?

---

### Post by Pumalite on 2008-07-19
Did you try Ctrl-D?

---

### Post by steveneddy on 2008-07-19
This is a dual thread.

Please only post one thread per subject.

The other one is getting good traffic though.

Why don't you delete or close this one?

---

### Post by jimv on 2008-07-20
Boot into the Live CD and run fsck on your Ubuntu partition.

---

