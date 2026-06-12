---
title: "ubuntu will not install on my HP 7935"
date: 2006-10-19
forum: Installation &amp; Upgrades
---

### Post by dsimpson on 2006-10-19
I have tried to install Ubuntu on my wife's HP 7935 desktop and have so far had no luck. It has a AMD Athlon cpu, 1.3 Gh. When installing it doesn't even get to the desktop on the live version, although one time it did load and I tried to install from there but it hung up and didn't complete the install. Now when I try it will get to "loading hardware", then stop and finally some text errors will pop up and it says, "The GDM user 'gdm' does not exist. Please correct GDM configuration and restart GDM". Is this a hardware problem that can be resolved or is it a bios conflict etc. I am new to Ubuntu and need any help that can be offered. The Ubuntu disc 6.06, is fine as far as I can tell, I installed it onto my personal computer and there were no problems, I too, have an AMD cpu 1.0 Gh but it is not a HP and didn't have any of the problems with the install. The HDD's on my computer and my wife's are both Western Digital, and her's is brand new, so no apparent difference there. I have formatted the HD and retried and it again stopped and upon reboot again went to the error message and stopped.

---

### Post by Sef on 2006-10-19
Have you tried the alternate cd?  It is text based, but very easy to follow.  Sometimes the alternate works when the Desktop cd doesn't.  

[Alternate CD]("http://www.ubuntu.com/download") pick where you want to download from and scroll down to alternate CD.

Also what graphics card does your wife have on her computer?

---

### Post by dsimpson on 2006-10-19
I only have the live cd, I have ordered the alternate cd, and will try it when it comes. I have a DVD but no player on my wife's computer with which to open the alternate cd and install it. Thank you for the ideas.

---

### Post by gn2 on 2006-10-19
Have you tried the boot options on the Live CD?

There's a few to try, I think you press F6 to get to them, it's on the Live CD splash screen.

"noapic nolapic" was the one that worked for me.

---

### Post by dsimpson on 2006-10-19
Tried to go the F6 route, only one option for booting, is there a way to see the full options by pressing other keys after pressing F6 key? As to an earlier question concerning type of graphics card, it seems to be part of the motherboard, not a separate card, can another graphics card be added without conflicts with the original graphics? Still trying so keep sending the suggestions. Thanks

---

### Post by h4rdwire on 2006-10-19
did you download the alternate CD, might just be a bad disc you got...download another one and burn it..

---

### Post by gn2 on 2006-10-19
> **dsimpson said:**
> Tried to go the F6 route, only one option for booting, is there a way to see the full options by pressing other keys after pressing F6 key? As to an earlier question concerning type of graphics card, it seems to be part of the motherboard, not a separate card, can another graphics card be added without conflicts with the original graphics? Still trying so keep sending the suggestions. Thanks

After you press the F6 a list of keys for other options should be displayed?

I fiddled about for a while with them till it worked.

Does it have ATI graphics? They can be troublesome...

---

### Post by lfloyd on 2006-10-21
try boot option live acpi=acpi

---

### Post by lfloyd on 2006-10-21
sorry try live acpi=off in boot options

---

