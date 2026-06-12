---
title: "dolphin crashes on any file copy - new install 11.04"
date: 2011-08-16
forum: Installation &amp; Upgrades
---

### Post by vayu on 2011-08-16
I don't know where to begin figuring this out.  On a total fresh install of kubuntu 11.04, everything went fine.  When I do any copying in dolphin it crashes.  Konqueror does the same thing.  I installed samba and I can copy files when using samba from a remote computer, locally it crashes dolphin and konqueror.  I turned off desktop searching, still crashes. I tried copying from konquorer to dolphin and vice versa, crashes everytime. The system notification acts like it started the copy and keeps whirring until I close it.  What can I try?

---

### Post by ofnuts on 2011-08-16
> **vayu said:**
> I don't know where to begin figuring this out.  On a total fresh install of kubuntu 11.04, everything went fine.  When I do any copying in dolphin it crashes.  Konqueror does the same thing.  I installed samba and I can copy files when using samba from a remote computer, locally it crashes dolphin and konqueror.  I turned off desktop searching, still crashes. I tried copying from konquorer to dolphin and vice versa, crashes everytime. The system notification acts like it started the copy and keeps whirring until I close it.  What can I try?What happens when you try to do the same copy operation from a command line?

What happens if you try a sizable download with Konqueror (this also starts progress indicators in the system notification tray)

---

### Post by vayu on 2011-08-16
> **ofnuts said:**
> What happens when you try to do the same copy operation from a command line?

What happens if you try a sizable download with Konqueror (this also starts progress indicators in the system notification tray)


I can copy from the command line.  I can download and save a large file (and it shows up in the notification with it's progress displaying and updating.   Turns out I can delete from dolphin but I cannot rename.

Everything else seems to work fine on this install.  Though it's pretty unusable if I can't copy and rename from dolphin or konqueror.

---

### Post by ofnuts on 2011-08-16
> **vayu said:**
> I can copy from the command line.  I can download and save a large file (and it shows up in the notification with it's progress displaying and updating.   Turns out I can delete from dolphin but I cannot rename.

Everything else seems to work fine on this install.  Though it's pretty unusable if I can't copy and rename from dolphin or konqueror.Are the files you copy (source and target) in local directories? What has Samba got to do with this?

---

### Post by vayu on 2011-08-16
> **ofnuts said:**
> Are the files you copy (source and target) in local directories? What has Samba got to do with this?

Nothing other than that it shows copying works.  From another computer I was able to copy files onto and within this computer.

---

### Post by ofnuts on 2011-08-16
> **vayu said:**
> Nothing other than that it shows copying works.  From another computer I was able to copy files onto and within this computer.The same files in the same directories? And can you copy them using shell commands?

---

### Post by vayu on 2011-08-17
> **ofnuts said:**
> The same files in the same directories? And can you copy them using shell commands?

Yes, I could.   I ended up reinstalling and it seems to be working fine now.  I'm afraid to install the same things I did before.  I want to install konqueror but I'm worried that the problem might have come from that and I don't want to install all over again.  Thanks for your interest.

---

