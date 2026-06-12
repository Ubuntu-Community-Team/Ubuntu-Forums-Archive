---
title: "Upgrade from Dapper 6.06 to 6.10"
date: 2006-10-27
forum: Installation &amp; Upgrades
---

### Post by rgeddes on 2006-10-27
I was running :

Xubuntu, Dapper 6.06, Kernel 2.6.15.27.686 on a 
P3 Katmai, 512 MB Memory, 100 GB HDD
I made myself a member of sudo.

I ran synaptic this morning and noticed I could upgrade to Dapper 6.10....  it said it would take about 30 minutes to download, so I went about some other chores...

I came back an hour later and found my screensaver was activated, so I proceeded to enter my password... Sorry!  It would not accept my password.  The screensaver would not allow me to change the user id to root.. I was stuck with an upgrade, whose state I did not know, and a screensaver that would not let me login again.

After an hour of trying to dupe screensaver into letting me into my own system, I realized I had no choice but to hit the hardware reboot.  On reboot, I prayed (Ubuntu has religious connotations, after all) the upgrade had completed successfully and I would proceed without a hitch.

Known announced failures on reboot:
Loading hardware drivers
Mounting local filesystem

The system was not in a known good state, and now I have to find my way back.  Any help getting to a known good state would really be appreciated.

Fortunately, I have a dual boot system and am writing from my Win2k side.  I still have some files in my reiser filesystem that I use on a daily basis

Thanks

---

### Post by rgeddes on 2006-10-29
I got my system back to a "working"... not necessarily a known good state.  After reading the "caveats" for upgrading to 6.10, I realized that Xubuntu has a small but dedicated (as in, only Xubuntu issues) website.  I followed the 2nd entry in the following thread:

[http://ubuntuforums.org/showthread.php?t=286599](http://ubuntuforums.org/showthread.php?t=286599)

it's by magicfab

There I found instructions on how to get my system working again... basically my system booted with the two failure messages and eventually stopped with an underscore.  Then I followed the instructions:

1. Got to a virtual console (ctrl-alt-F2)

2. Logged in as myself(not root). Notice that you have to be a member of sudo to perform root tasks with a non-root user id.  Also when I logged in I got an infinite loop "Permission denied: /dev/null", which I stopped with a ctrl-c.

3. Ran 
        sudo dpkg --configure -a

It took about an hour for the process to finish... and there were some questions about upgrading or keeping certain configurations... I'm experimenting so I answered yes to all.

4. Finally I ran

         sudo halt

to shutdown my computer... actually, it never really  shutdown my computer... it just stops "chugging", and I take that as a sign to power off.

5. Powered up again and found, to my surprise, that I got a working system... don't know how the finer details are affected by this upgrade... I'm sure I'll find out.

Thanks

---

