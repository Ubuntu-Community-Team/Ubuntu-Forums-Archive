---
title: "Ubuntu won't boot"
date: 2008-07-19
forum: Installation &amp; Upgrades
---

### Post by snowe2010 on 2008-07-19
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
press ESC to skip                      72%(stage 1/5,2953/21171)

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

---

### Post by OscarPapa on 2008-07-19
Try running the command "init 1" (Entering maintenance mode) and running fsck manually (as the error message instructed). Good luck!

---

### Post by snowe2010 on 2008-07-19
okay so like
init 1
then sudo fsck
?
or just fsck

---

### Post by snowe2010 on 2008-07-19
okay i used init 1 and it went through all these commands and now i have a blue screen with a white window that says 
could not start the x server (your graphical environment) due to some internal error. ... In the meantime this display will be disabled. Please restart GDM when the problem is corrected.
and then right below it two black bars came up showing part of the terminal.

tylersubuntu login: is in one of the black bars

---

### Post by OscarPapa on 2008-07-19
When you are in runlevel 1, you will only be allowed to log in as root and most of the day-to-day features you use will not be loaded, as it is reserved for maintenance (Think of it as something like safe-mode in Windows). You can also pass 1 to grub so it starts runlevel 1, and perform your tasks. 

I would suggest you read up on the manual pages for fsck (man fsck in a terminal).

---

### Post by themightymegatron on 2008-07-19
I'm getting similar issues now, but only after switching from my internal laptop HDD to my new external. It's a clean install, and whenever I boot it does the fsck like above, I get the EXACT error after that, including the missing commands, and then I either login or press CTRL+D. Whenever I CTRL+D it loads xserver and goes through my automated login. I can then use ubuntu as normal. This just happened shortly ago, so I'm going to reboot now and run a manual fsck. Probably going to run something like this:

> 
root@machine # init 1
root@machine # e2fsck -Dfp [drive]


for the original poster, the above commands are what I would suggest running. The -D option isn't necessary but what it does is to optimize the directory structure of your filesystem. Just a little known tweak to e2fsck that I don't see used often enough. definitely use the -f [force full check] and -p [auto-repair] options, though.

Good luck, and I'll report back soon if I don't screw something up!

---

