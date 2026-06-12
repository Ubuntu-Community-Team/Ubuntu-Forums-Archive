---
title: "No checking for integrity of CD on Lucid ???"
date: 2010-03-13
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by wpshooter on 2010-03-13
Am I correct from what I am seeing on the 03-16-2010 daily build on Lucid desktop 32 bit version, that there is not going to be any function for checking the integrity of the Ubuntu/Lucid CD ?  If this is correct, I am not to sure that I care for this very much !!!

When I insert the CD into the computer and boot to it there is no longer any initial menu which gives you the choice to check the integrity of the CD or to run a memtest and several other functions that used to be included on the initial Ubuntu boot menu in older versions.  Instead the system boots straight-way up to Ubuntu desktop from the Lucid live CD, where you can then choose to run a live session from the CD or to install the Lucid O/S to your hard drive.

Thanks.

---

### Post by VMC on 2010-03-13
> **wpshooter said:**
> Am I correct from what I am seeing on the 03-16-2010 daily build on Lucid desktop 32 bit version, that there is not going to be any function for checking the integrity of the Ubuntu/Lucid CD ?  If this is correct, I am not to sure that I care for this very much !!!

When I insert the CD into the computer and boot to it there is no longer any initial menu which gives you the choice to check the integrity of the CD or to run a memtest and several other functions that used to be included on the initial Ubuntu boot menu in older versions.  Instead the system boots straight-way up to Ubuntu desktop from the Lucid live CD, where you can then choose to run a live session from the CD or to install the Lucid O/S to your hard drive.

Thanks.
One thing you can do is use md5sum to check it as follows:
(Make sure your at root or you need to tell it where to look)

```
md5sum -c md5sum.txt
```

---

### Post by kansasnoob on 2010-03-13
> **wpshooter said:**
> Am I correct from what I am seeing on the 03-16-2010 daily build on Lucid desktop 32 bit version, that there is not going to be any function for checking the integrity of the Ubuntu/Lucid CD ?  If this is correct, I am not to sure that I care for this very much !!!

When I insert the CD into the computer and boot to it there is no longer any initial menu which gives you the choice to check the integrity of the CD or to run a memtest and several other functions that used to be included on the initial Ubuntu boot menu in older versions.  Instead the system boots straight-way up to Ubuntu desktop from the Lucid live CD, where you can then choose to run a live session from the CD or to install the Lucid O/S to your hard drive.

Thanks.

I just did a fresh install after running the Live CD and checking a few things. And yes if you take no action whatsoever no menu shows up it just goes to the Live Desktop.

However I found that if I pressed Esc right when the initial screen shows up I get the usual menu. And the CD integrity test did work for the first time. (I'd just tried yesterdays and it did not).

There was however a glitch. When the test was complete and it displayed the results, then says press Enter to reboot -------- well it didn't reboot :( I had to press either Ctrl + Alt + Del or Alt + SysReq + B (sorry can't remember which for sure).

Then I chose Try without changes and it all went well however there was a pesky Apport crash icon that said Ubiquity crashed (tried to report but couldn't), but nothing was apparent so after fiddling a bit I installed with no problems.

One more glitch though, after choosing to restart when the CD ejected and it said "remove CD and press enter to reboot" it once again failed to reboot. That time I'm sure I used Alt + SysReq + B to reboot.

And it looks like the installation went fairly well other than os-prober not finding everything, that kind of surprised me.

BTW I hope you meant the 03-13-10 CD.

---

