---
title: "Booting processed stopped ureadahead-other error"
date: 2010-03-03
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Yahoé on 2010-03-03
Bonjour / Hi,

Booting processed stopped at: ureadahead-other error main process terminated with status 4.

This problem occurred first on a Lucid Alpha 2 system, and now on the same computer cleanly reinstalled with Lucid Alpha 3.

It doesn't happen for every boot.

These morning the system finally did boot "normally" on the third reboot.

An approach I have been using when experiencing this issue is to boot from recovery mode, and launch gdm manually from prompt. That works every time.

System is stable otherwise.

---

### Post by ratcheer on 2010-03-03
Don't feel too bad, it happens to me every single time with Lucid. I boot the same way you do (Recovery Mode to Root Prompt to start gdm).

Tim

---

### Post by ljrmorgan on 2010-03-10
I also have this problem. I upgraded from Karmic, and now when gdm should start I get two messages about ureadahead-other errors instead. I do hear the drum noise that I used to get when gdm started on karmic, and I have a mouse pointer on an otherwise black screen (apart from the error messages).

I just hit Ctrl+Alt+F1 to go to a terminal and logged in there, then I hit Ctrl+Alt+F7 to see the error messages so I could post them here, and instead gdm was there waiting for me! I logged in as usual and everything seems to be working. I didn't try this before, so maybe it was just a fluke, but if anyone has the same problem give this a shot, it might work!

---

### Post by Terrycymru on 2010-03-11
I am having exactly the same issue as Yahoé. Has this been reported as a bug?

---

### Post by grumpymole on 2010-03-11
Try pressing enter when you see the messages.  I get them all the time, but I *think* that hitting enter gets me passed.

---

### Post by Terrycymru on 2010-03-11
Since today's update boot seems to be OK for me. I have booted several times and not seen the ureadahead-other message - but it may be too early to say it is definitely fixed!

---

### Post by teh603 on 2010-03-11
Have you tried using Synaptic to uninstall Plymouth? That got rid of the ureadahead errors in my system as well as the autologin failure and boot failures, although it now causes some annoying error messages about Plymouth terminating with Status 2.

Whatever the heck Status 2 is.

---

### Post by dino99 on 2010-03-11
> **teh603 said:**
> Have you tried using Synaptic to uninstall Plymouth? That got rid of the ureadahead errors in my system as well as the autologin failure and boot failures, although it now causes some annoying error messages about Plymouth terminating with Status 2.

Whatever the heck Status 2 is.

No doubt about Plymouth's errors, it's not the first one and not the last too

---

### Post by anaconda on 2010-03-12
I have the same problem. 
Boot hangs right after grub every time. Luckily booting to recovery mode works. From there I can run startx to get to grephical environment.

When booting normally, it hangs, and even Ctrl-Alt-F1 wont work...

---

### Post by Lucretius on 2010-03-12
i have this problem and found pressing "enter" when it hangs allows the booting process to continue

---

### Post by dino99 on 2010-03-12
when things gone wrong, i'll first clean my system:

- run bleachbit as root (carefully, don't check everything)
- uninstall/purge packages giving errors, then reinstall.

Usually that's working.

---

### Post by Terrycymru on 2010-03-12
> **Lucretius said:**
> i have this problem and found pressing "enter" when it hangs allows the booting process to continue

Unfortunately, the problem is back today.

Lucretius thanks for the tip. Pressing "enter" when it hangs works for me too. :)

---

### Post by zika on 2010-03-12
Simply, ```
sudo aptitude purge plymouth
```and enjoy...

---

### Post by keybuk on 2010-03-12
> **zika said:**
> Simply, ```
sudo aptitude purge plymouth
```and enjoy...

This is really bad advice.

Without plymouth, you'll have no information during boot about fscks (you'll just sit at a blank screen wondering what's going on) - and you'll have no ability to recover if there's issues checking or mounting filesystems.

---

### Post by zika on 2010-03-13
> **keybuk said:**
> This is really bad advice.

Without plymouth, you'll have no information during boot about fscks (you'll just sit at a blank screen wondering what's going on) - and you'll have no ability to recover if there's issues checking or mounting filesystems.OK. You're right. But, in last few weeks that was the only way I could get trouble-free boot. Even without plymouth I still do not have proper shutdown and KMS will get me to crash in any time from several minutes to several hours or days. So, having bigger problems I chose to eliminate one that is pertinent to boot time, only. Since I was trouble-shooting, and since, just this morning new version of gdm came that solved problem of plymouth staying up, even though boot finished, that advice was kind of OK, at the time it was given...

---

### Post by ratcheer on 2010-03-13
> **zika said:**
> OK. You're right. But...

Spoken like a true gentleman.

Tim

---

### Post by zika on 2010-03-13
> **keybuk said:**
> This is really bad advice.

Without plymouth, you'll have no information during boot about fscks (you'll just sit at a blank screen wondering what's going on) - and you'll have no ability to recover if there's issues checking or mounting filesystems.I've reinstalled plymouth today. It seems it made a significant progress... It's staying, for now...

---

### Post by Yahoé on 2010-03-20
I have now done a fresh install of Lucid Beta 1. The ureadahead-other error flashes but the system goes into GDM without any problem so far.

Yahoé

---

### Post by Yahoé on 2010-03-22
Everything has been fixed with Lucid Beta 1.

I suggest that everyone with questions about ureadahead read this thread:

[http://ubuntuforums.org/showthread.php?t=1434502](http://ubuntuforums.org/showthread.php?t=1434502)

Regards

---

