---
title: "Thinkpad X301 intermittently freezes upon waking from hibernation"
date: 2009-10-12
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by JuddGarratt on 2009-10-12
Disclaimer: You may have to bear with me - I'm new to Linux and Ubuntu.

I installed Karmic on one of my laptops a few weeks ago out of curiosity to see what Ubuntu and Linux were all about.

I became addicted.

I've noticed a problem recently and I'd like to help by reporting it, but I'm not sure what aspect of Ubuntu is causing the issue.

My Thinkpad X301 intermittently freezes upon waking from hibernation. This always occurs after the login screen appears and requires a hard reset to escape.

I cannot replicate the freeze consistently. However, the freeze only occurs when I hibernate the laptop while connected to mains power and wake the laptop while on battery power.

I have searched Launchpad but can find no bug that matches this description.

Searching the Bugs/FindRightPackage wiki pages suggests the issue is in the linux kernel if it's a hibernate issue, or GDM if it's a login screen issue.

However, when I rebooted after one such freeze, apport wanted to report a crash that related to wireless (I wasn't able to understand what, specifically, crashed).

Since the login screen fully loads (and sometimes the mouse works for a second until everything freezes), gut feeling says something related to GDM (but not GDM itself) caused the problem.

Can anyone help me understand what I should investigate to consistently reproduce the issue or identify the problem area so I can report the issue?

(I've only been using Ubuntu/Linux for a few weeks, so any suggestions might need instructions.)

---

### Post by JuddGarratt on 2009-10-13
Anyone have any ideas?

Froze twice again today. No apport alert after reboot.

What can I test to figure out what package I should report a bug in?

---

### Post by Longinus00 on 2009-10-13
I have a hp nc6400 and my hibernation has been very touch and go in karmic. Interestingly, suspend has worked well. Everything was working great in jaunty so I assume it's probably the new kernel.

---

### Post by Martey on 2009-10-14
> **JuddGarratt said:**
> I cannot replicate the freeze consistently. However, the freeze only occurs when I hibernate the laptop while connected to mains power and wake the laptop while on battery power.

I have searched Launchpad but can find no bug that matches this description.


Your issue sounds sort of like [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/412363](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/412363), specifically the fact the failure only happens when you try to resume on battery power.

---

### Post by JuddGarratt on 2009-10-20
Thanks for the replies.

I've been digging around and it does seem to be a kernel issue.

I did an update and the system now boots and then switches off automatically when waking from hibernation on battery (after hibernating on mains power).

I will keep trying to learn about this so I can post an intelligible bug report.

---

