---
title: "Problem with 12.04 mini.iso"
date: 2013-11-30
forum: Installation &amp; Upgrades
---

### Post by jkugler on 2013-11-30
I am trying to do an 12.04 install via the mini.iso.  I get through the first part of setup OK (network, etc), but when I get to Load Installer Components, it just hangs on a purple screenn.  The log screen (ctrl-f4) shows it downloading three GPG keys, but then after that it just hangs, nothing in the logs, nothing on the installer screen.  I've had this happen on two different systems, one VM, one physical, and with the PAE and non-PAE mini.iso.

Ideas?  I'm at a loss here.

---

### Post by sudodus on 2013-11-30
The 12.04 mini.iso works well from CD, but does not work when cloned to a USB drive. Is that your problem?

---

### Post by jkugler on 2013-11-30
> **sudodus said:**
> The 12.04 mini.iso works well from CD, but does not work when cloned to a USB drive. Is that your problem?

Yes, I used unetbootin to to transfer it to a USB drive.

It seems to be very odd place to exhibit a problem, given that:

1) the usb key boots
2) installer starts
3) language configure works
4) keyboard configure works
5) network configure works
6) hangs on the "Loading Installer Components" step.

I also had the same problem booting the mini.iso in a VM, straight from the ISO, no conversion done.

---

### Post by mörgæs on 2013-11-30
The minimal install can appear to hang for some time, especially on old hardware. 
For how long did you wait before canceling?

---

### Post by jkugler on 2013-12-01
> **mörgæs said:**
> The minimal install can appear to hang for some time, especially on old hardware. 
For how long did you wait before canceling?

Twenty to thirty minutes.  Also note: it hung running in a VM on my Core i7-2670QM machine as well.  I know a VM doesn't run as fast a native box, but... :)

Also note: on the log screen (ctrl-f4) it says it downloaded three gpg keys, and marked them as OK.  After that, there is no more log output. What would it be doing for twenty to thirty minutes that it would not produce any log output?

---

### Post by mörgæs on 2013-12-01
How does the 13.10 mini.iso work?

---

### Post by jkugler on 2013-12-01
> **mörgæs said:**
> How does the 13.10 mini.iso work?

I have not tried yet.  I wanted to install 12.04 because it is an LTS release.  I may install 13.10 as a last result, if it works.

---

### Post by jkugler on 2013-12-01
So, further investigation:

10.04 i386 mini.iso: same problem (booting in a VM)
10.04 i386 server: seems to be running OK.

Maybe I'll install this, and then upgrade to 12.04. I was trying to do the 12.04 mini so I could get a non-pae kernel.  We'll see how this goes.

---

### Post by sudodus on 2013-12-02
The mini.iso version 13.04 works from USB. I think also 13.10. See this link

[http://ubuntuforums.org/showthread.php?t=1958073&p=12698924#post12698924](http://ubuntuforums.org/showthread.php?t=1958073&p=12698924#post12698924)

---

### Post by sudodus on 2013-12-02
> **jkugler said:**
> So, further investigation:

10.04 i386 mini.iso: same problem (booting in a VM)
10.04 i386 server: seems to be running OK.

Maybe I'll install this, and then upgrade to 12.04. I was trying to do the 12.04 mini so I could get a non-pae kernel.  We'll see how this goes.

You can use fake-PAE instead of non-PAE. See this link

[https://help.ubuntu.com/community/Lubuntu-fake-PAE](https://help.ubuntu.com/community/Lubuntu-fake-PAE)

---

### Post by jkugler on 2013-12-02
Thanks for the tips.  The install 10.04, upgrade to 12.04 method worked.  I don't want to use 13.10, since I want an LTS release. I'll be alpha/beta testing the mini.iso for 14.04 for sure. :)

---

### Post by mörgæs on 2013-12-02
Good, please mark the thread 'solved'.

---

### Post by cjwatson on 2013-12-03
This is [bug 1067934]("https://bugs.launchpad.net/bugs/1067934").  Use the mini.iso from precise-updates rather than precise, which has my fix for that bug.

---

