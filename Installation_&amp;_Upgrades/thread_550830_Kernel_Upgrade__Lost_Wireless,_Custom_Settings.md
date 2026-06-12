---
title: "Kernel Upgrade | Lost Wireless, Custom Settings"
date: 2007-09-14
forum: Installation &amp; Upgrades
---

### Post by sammermpc on 2007-09-14
At the prompting of the update-manager, I upgraded my Ubuntu system (Feisty) on an IBM X40 laptop to the latest kernel, (2.6.20-16 generic version), everything worked perfectly, but after the restart, I am getting a "device not found" error on my wireless card.  It is as if it isn't there.  In addition -- just as this might be a help in troubleshooting, after a reset, the default mouse speed/sensitivty settings are restored.

If I boot into the previous kernel version, 2.6.17-11, everything works perfectly, the networking AND mouse settings are stored.  I wonder if the two are related.

Thanks for any help or ideas of how to troubleshoot this, I am decently competent but enough so to figure something like this out on my own.

---

### Post by jnorthr on 2007-09-14
Have a similar problem here - if i use 2.6.20-16 then no wireless but dropping back to 2.6.20-15 works ok, so i'm gonna stick with -15 until gutsy is ready.

---

### Post by sammermpc on 2007-09-14
Yeah, I would not even complain except that in 2.6.17-11 my computer only wakes up from sleep about half of the time.  Half isn't bad though.

---

### Post by travislepp on 2007-09-19
Hi all,
I have an acer Aspire 5630 with the same issue, it's a real shame doe anyone have a solution to this?

---

### Post by Seisen on 2007-09-19
Did your wireless work really good out of the box or did you have to do some tinkering? I had a d-link wireless card that would work so-so on dapper then when I upgraded to edgy it  didn't work at all and I had to use ndiswrapper to get it working.

---

### Post by WakkaDojo on 2007-09-19
Well I compiled a kernel and had similar issues with modules. The problem might be that your drivers aren't in the new firmware directories that came with the kernel upgrades.

Try this:
```
sudo -s && cd /lib/firmware
```
Once in the directory, backup your current firmware for the most updated kernel -- I'll presume it's 2.6.20-16-generic, but the versions will differ.
```
mv 2.6.20-15-generic 2.6.20-15-generic.bak
```
And finally, make it so when the computer accesses the /lib/firmware/2.6.20-16-generic directory, it actually accesses your old directory. Since the first post used kernel 2.6.17-11, I'll use that in my example. But of course this will vary:
```
ln -s 2.6.17-11-generic 2.6.20-15-generic
```
And restart your computer.

Note that I assumed you're running the old kernel version named 2.6.17-11-generic and trying to get the new version 2.6.20-16-generic running. If this doesn't work then just remove the symbolic link to 2.6.17-11-generic and move the backed up 2.6.20-16-generic to its original name, and seek another solution!

---

### Post by sammermpc on 2007-09-25
Thanks for the help -- the linking solution didn't seem to work.  I have managed a work around (at least so that I can use 2.6.20).

I updated the sources, apt-get update, I think was the command.  Then I downloaded the generic versions of everything.  I'm running:
Linux sam-laptop 2.6.20-16-generic #2 SMP Sun Sep 23 19:50:39 UTC 2007 i686 GNU/Linux

While in all previous versions, I was using 2.6.20-16-386.  I'm not sure what the difference is between the kernels and I'd appreciate enlightenment if anyone knows what is going on.  I was looking at various bug reports, and it seems like a lot of people have had this issue; something to do with the restricted section of the multiverse and wireless drivers.

---

