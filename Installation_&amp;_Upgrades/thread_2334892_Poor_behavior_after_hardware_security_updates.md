---
title: "Poor behavior after hardware security updates"
date: 2016-08-23
forum: Installation &amp; Upgrades
---

### Post by raequin on 2016-08-23
This morning Ubuntu showed me a pop-up window that stated a security update was available for my hardware.  At least that's my recollection of what it said.  I installed the updates and now the keyboard illumination is always on and the hard drive is always spinning.  The command ```
top
``` gives me

```
  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND                                                                                                                                          
 1523 rae       20   0 1581952  89264  21628 D  67.2  1.1   4:36.46 mediascanner-se
```

Since that command (mediascanner-se) starts with an m, I'll also include the fact that I added the following keyboard shortcut command, which didn't work.

```
/usr/local/MATLAB/R2015a/bin/matlab . &
```

The accelerator (or keyboard shortcut) for this was "ctrl+alt+M" and MATLAB would show its splash screen but never open and the hard drive would just keep spinning.

I logged out and restarted my computer several times to see if the spinning hard drive problem would go away but it persisted.  However, in the time that I've been writing this mediascanner-se no longer shows up with ```
top
``` and the hard drive has quit spinning.  The keyboard illumination is still on.

---

### Post by mook765 on 2016-08-23
My hard-drive is spinnig 24/7 and i would get crazy if it would stop spinning...
Anyway, here is a thread that seems to be related to your problem.
[https://ubuntuforums.org/showthread.php?t=2206377](https://ubuntuforums.org/showthread.php?t=2206377)
Open the file /var/log/apt/history.log in your text-editor, far down at the end of the file you will find informations about the packages installed during that update.
Kind regards...

---

### Post by raequin on 2016-08-23
Thanks for the link, @mook765!

The keyboard illumination is also puzzling.

---

### Post by raequin on 2016-08-24
This is a non-issue since I found the button for illumination.  It would be nice to know why it is on by default now, but since I can easily turn it off I'll close this thread.

---

