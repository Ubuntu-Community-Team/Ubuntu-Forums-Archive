---
title: "Lucid Arrandale Suspend/Resume"
date: 2010-03-12
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Chenzo on 2010-03-12
I'm running Lucid on a ThinkPad T410 with the new Arrandale processor and integrated intel graphics (core i5).

Everything, for the most part, works great. However, I have a strange suspend/resume bug that I don't know how to report.

About 9/10 times, it works perfect. 1/10 times, when I try to resume from suspend, it tries to resume, then 5 seconds later, goes back to sleep (the glowy light starts pulsing as if it were sleeping). I then try one more time, and this time it goes to a post screen, but hangs there. I have to power down again, then the computer boots fine. After the computer boots, networking is usually disabled and I have to re-enable it with the checkbox (weird right?), but things work fine.

These are very strange symptoms, and I have not been able to figure out what is causing it so I don't know how to file the bug report.

In summary: When I suspend, 10% of the time, on resume, I get this:
1. tries to resume, after 5 seconds, goes back to sleep.
2. Hit resume button again, goes to POST screen, hangs.
3. power down, turn it back on, boots fine.

My questions are:
1. Is anyone else having similar problems with core i3/5/7 (arrandale)? 
2. How should I go about submitting a bug report for something like this?

Thanks!

---

### Post by tekstr1der on 2010-03-12
Please do follow up by filing a bug against gnome-power-manager for this issue. I will receive my Thinkpad X201s on Wed 17th with Core i7-640LM and will be testing these type of issues thoroughly, of course.

On a side note, does it suspend on lid-close. That's been broken since Intrepid for me on my current laptop. See this OLD bug if it's broken for you:

[https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/44058](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/44058)

I'd rather you tell me it's working properly, though!!

---

### Post by Chenzo on 2010-03-12
Yes, it does suspend on lid-close.

I'll file a bug against gnome-power-manager. 

Are there any files I should include? I wouldn't know what log files to include that might help determine the cause of the issue.

---

### Post by tekstr1der on 2010-03-12
> **Chenzo said:**
> Are there any files I should include? I wouldn't know what log files to include that might help determine the cause of the issue.

Apport will automatically collect relevant files. Just use
```

apport-bug gnome-power-manager
```

to file and provide the details you mentioned in the original post.

---

### Post by pferraro on 2010-03-12
> **Chenzo said:**
> I'm running Lucid on a ThinkPad T410 with the new Arrandale processor and integrated intel graphics (core i5).

Everything, for the most part, works great. However, I have a strange suspend/resume bug that I don't know how to report.

About 9/10 times, it works perfect. 1/10 times, when I try to resume from suspend, it tries to resume, then 5 seconds later, goes back to sleep (the glowy light starts pulsing as if it were sleeping). I then try one more time, and this time it goes to a post screen, but hangs there. I have to power down again, then the computer boots fine. After the computer boots, networking is usually disabled and I have to re-enable it with the checkbox (weird right?), but things work fine.

These are very strange symptoms, and I have not been able to figure out what is causing it so I don't know how to file the bug report.

In summary: When I suspend, 10% of the time, on resume, I get this:
1. tries to resume, after 5 seconds, goes back to sleep.
2. Hit resume button again, goes to POST screen, hangs.
3. power down, turn it back on, boots fine.

My questions are:
1. Is anyone else having similar problems with core i3/5/7 (arrandale)? 
2. How should I go about submitting a bug report for something like this?

Thanks!

I get similar behavior on my T510.  Question - is your always-on USB port functional after resume?

---

### Post by jlgoolsbee on 2010-03-13
I can confirm this behavior on my T510, but I can also reproduce it on Karmic, so this isn't limited to Lucid.

---

### Post by KB1JWQ on 2010-03-15
My t510 is on the way, and I'll be sure to test this out.  Following this thread so I remember to circle back around. :-)

---

### Post by peepingtom on 2010-03-15
Not a regression, this is a known issue with T510s.
Bug report here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/532374](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/532374)

---

### Post by tekstr1der on 2010-03-26
> **pferraro said:**
> I get similar behavior on my T510.  Question - is your always-on USB port functional after resume?

I also have very similar behavior on my ThinkPad X201s. My USB ports power-off on resume. Only a reboot corrects the issue. As for multiple suspend-resume cycles, the first time works other than the USB issue. However, while suspending again works, resuming fails triggering reboot.

I filed:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/542035](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/542035)

but it seems there are many diverse issues affecting suspend/resume ATM.

EDIT: Just saw peepingtom's link. Will dupe mine!

---

### Post by tylerwylie on 2010-04-12
Happens on my T410 as well.

---

