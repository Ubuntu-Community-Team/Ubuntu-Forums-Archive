---
title: "Can Not Partition Drive During Install From LiveCD"
date: 2009-02-08
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Therion on 2009-02-08
Running into an issue with installing Jaunty.  

I have a good burn of the LiveCD, everything checks out clean with it.  I boot to it just fine, start the install process and select the option to use the entire drive (which is correctly identified in the installer).  I get the partitioning menu (Guided, Manual, Use Entire Disk, just like usual) and I select "Use Entire Disc", click forward a couple times or whatever to start the intstall then after about two seconds the installer menu jumps right back to the prompt asking me how I want to install. Guided, Manual, Use Entire Disk, etc.  There's no error message.

What's the problem?

---

### Post by Therion on 2009-02-09
I can't be the only person on the planet having this problem, can I?

---

### Post by Slug71 on 2009-02-09
> **Therion said:**
> I can't be the only person on the planet having this problem, can I?

Have you tried todays Daily Build?

---

### Post by Therion on 2009-02-10
> **Slug71 said:**
> Have you tried todays Daily Build?
No, but I have to wonder how much changes from day to day in the installer itself.  I have also discovered that the exact same problem occurs if I try to install Intrepid.  Except with Intrepid I get a generic error that the partition can not be created.  

It seems something changed between Hardy and Intrepid, that's carried forth into Jaunty, that's preventing me from being able to install from the LiveCD.  

I thought it might be the fact that the LiveCD is using my hard drive to mount a swap file, so I used "sudo swapoff -a" before starting the installer but that didn't help.

---

