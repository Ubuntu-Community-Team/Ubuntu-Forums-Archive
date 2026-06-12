---
title: "BUG: soft lockup while updating in recovery mode"
date: 2011-07-02
forum: Installation &amp; Upgrades
---

### Post by etbebl on 2011-07-02
Hi, so I encountered this error while trying to update to Natty Narwhal:

"BUG: soft lockup - CPU#0 stuck for 61s! [kswapd0:26]"

Let me explain. I'm a new ubuntu user, of about 2 months. I originally installed the Desktop Edition from the disc as a dual boot, along with windows 7, on an old dell inspiron 1501 laptop. This worked fine after a few tries. When I tried to update through the GUI, it kept freezing / crashing and eventually it wouldn't start normally, so I used the recovery mode from the GRUB menu. From there the update seemed to be working, so I left it, but when I came back the error above was on the screen and repeating every minute or so. What should I do? I don't want to lose any data. Remember, I'm new to this.

---

### Post by mörgæs on 2011-07-03
Hi, welcome to the fora.

What happens if you boot the computer and run

```
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```

? 

Please post the error messages, if any.

---

### Post by etbebl on 2011-07-03
Thanks for replying. Will try that tonight.

---

### Post by etbebl on 2011-07-03
OK, here are my findings:

1. Version 11.04 is partially installed, but I can't log in. First, it gave me an error message: 
"It seems that you do not have the hardware required to run Unity. Please choose Ubuntu Classic at the logon screen and you will be using the traditional environment."
But after choosing Ubuntu Classic, it still wouldn't log in.

2. I booted to recovery mode and entered the root prompt. I then ran the three commands, omitting sudo since I was running them as root. 
[LIST]
[*]apt-get clean ran with no error.
[*]apt-get update returned the error: "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem." I ran that command and it completed with no error.
[*]apt-get upgrade ran for about 10 minutes, then started returning the soft lockup bug. Here is the exact wording and format:
[/LIST]

```
[ xxxx.xxxxxx] BUG: soft lockup - CPU#0 stuck for 61s! [kswapd0:26]
[ xxxx.xxxxxx] Process kswapd0 (pid 26, ti=f6628000 task=f6533f70 task.ti=f6628000)
[ xxxx.xxxxxx] Stack:
[ xxxx.xxxxxx] Call Trace:
[ xxxx.xxxxxx] Code: [long series of 2-digit hex numbers]
```

I hope this helps diagnose the problem.

---

### Post by mörgæs on 2011-07-04
Soft lockups can be hard to diagnose, but chances are good that a fresh install will solve the problem.

If the computer is too old to run Unity, you could consider Xubuntu 11.04. In addition to being lighter than Ubuntu, is is also less buggy.

---

### Post by etbebl on 2011-07-04
Thanks morages, a clean install did the trick.:D I installed xubuntu 11.04 and now it's working great. I did run into a little problem when I deleted the ubuntu partitions and I was left with a confused grub, but that was resolved when I booted from the xubuntu live-disc and installed it.
Thanks again!

---

