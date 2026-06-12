---
title: "Problems installing on old Compaq"
date: 2007-07-30
forum: Installation &amp; Upgrades
---

### Post by C.Barr on 2007-07-30
I've been given an old Compaq desktop (probably 2-3years old) and it's got XP home one it, and I'd rather use that license on another computer and get Ubuntu on this one.

I've downloaded and tried to install it with both the normal and the alternate installs, but it produces the same error when I try it.  The disks are fine since they both load up as expected on my newer PC.  I go to the main menu where I can select to install ubuntu, do a memory test etc.  If I select to install it or check the CD for defects it gives me this: [http://www.ejectmedia.net/files/ubuntu_install_error.jpg](http://www.ejectmedia.net/files/ubuntu_install_error.jpg) - yeah, the old school way of taking a screenshot, i know.

any ideas on how to proceed?

EDIT:
XP reports the computer to have:
2.53Ghz Celeron
248MB RAM
Intel 82845G graphics card

---

### Post by gobbles414 on 2007-07-30
I had an old HP laptop (5-6 years old) that would often freeze when booting from Linux installation disks. I was able to solve the problem by disabling legacy usb support in the bios. That was awhile ago, however. Nevertheless, it may still be worth a try.

---

### Post by merlinus on 2007-07-30
Ubuntu requires 256 MB RAM.  Try Xubuntu.

-merlin

---

### Post by C.Barr on 2007-07-30
Oh, that makes sense.  I'm not sure why this has such a small ammount of RAM, I'll see if I can pull some from an older machine.  If nothing else I'll be trying out Xubuntu for the first time.  Thanks, such a simple problem.

---

### Post by C.Barr on 2007-07-30
Ok, small update here.  I was curious how it even got to a total of 248MB anyway, since thats such a strange ammount of RAM.  There's a single 256MB chip in there, but why is XP reporting it as 8MB less?

I tried switcing slots and that made no difference.  I supose just a single 8MB chip died on it, but it seems like that would make the entire thing not work.  Oh well I need more anyway, just ranting now.

---

### Post by merlinus on 2007-07-30
Maybe shared video memory?  In those days, 8 MB was a lot!

-merlin

---

### Post by C.Barr on 2007-07-31
Ok, i tried Xubuntu now, and it results in the exact same error!

I figured it must be a RAM problem, so I let the memory test on the disk run for about 3 hours and it didn't result in a single error.

The BIOS on the computer reports it as a single 256MB chip, which it is, but XP and even the memory test both say it's 248MB.

---

### Post by mewtwo064 on 2007-08-19
> **C.Barr said:**
> Ok, i tried Xubuntu now, and it results in the exact same error!

I figured it must be a RAM problem, so I let the memory test on the disk run for about 3 hours and it didn't result in a single error.

The BIOS on the computer reports it as a single 256MB chip, which it is, but XP and even the memory test both say it's 248MB.

I don't believe it's a RAM problem or lack of RAM for that matter. I have a Compaq that does the EXACT same thing and I have 768 megs in mine (came with a single 256 meg, added a 512 meg later) Your ram is probably fine, your video card is taking up 8 megs of it for its integrated video, so it's unavailable to Windows, which is why it reports less than what is "advertised". Is your compaq a model S6020WM by anychance?

---

