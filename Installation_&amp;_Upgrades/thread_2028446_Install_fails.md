---
title: "Install fails"
date: 2012-07-18
forum: Installation &amp; Upgrades
---

### Post by spamless on 2012-07-18
Tried four times to install Xubuntu 12.04 Alternative, 32-bit, in German, from a CRC-checked CD. It always fails at 85% of Software Selection and Installation: [http://pic.twitter.com/rr2L1qTn](http://pic.twitter.com/rr2L1qTn)

The desktop machine is seven years old with no hardware surprises and has three other Linuxes installed, including regular Ubuntu 12.04.

---

### Post by rukiaEnix on 2012-07-18
I've had this problem with Ubuntu installations and with Debian.

I don't know why sometimes happens this when the installation gets updates while installing.

Try installing Xubuntu without a network connection. I recommend to unplug your ethernet cable or if it's wireless don't use it while installing.

---

### Post by spamless on 2012-07-19
> **rukiaEnix said:**
> I've had this problem with Ubuntu installations and with Debian.

I don't know why sometimes happens this when the installation gets updates while installing.

Try installing Xubuntu without a network connection. I recommend to unplug your ethernet cable or if it's wireless don't use it while installing.

Thanks! I wonder if the same thing will happen if I try the install with the Desktop source ISO instead of Alternative.  I think I will try that first, and if the same thing happens, then I will do what you said.

(Using a German keyboard right now and can not find the apostrophe key, which is why my syntax style perhaps sounds a little like Data from *ST:TNG*. :) I know where most all the keys are, but a couple I can never remember include the apostrophe.)

---

### Post by rukiaEnix on 2012-07-19
OK! Just post here what happens!

---

### Post by spamless on 2012-07-21
> **rukiaEnix said:**
> OK! Just post here what happens!

What happens is, it won't install.  It fails in Alternative, it fails in Desktop, from the LiveCD, from a USB. It fails with no updates specified and the ethernet cable yanked. [Edit: Oy vey, but I had the wrong ethernet cable yanked. The one to **this** machine was never yanked. It was a 3-AM PEBCAK on that. But I did have the tickbox unchecked about updating packages.]

It fails in German and it fails in English.  I tried it seven ways from Sunday or seven ways from whatever.  A real seven, not just an idiom.  I tried seven different times.

Source CRC was checked and the internal check was run on the USB when I used that.

N.B.: One thing I never unchecked is to install non-free third-party stuff, though. Presumably, they are already in the sources inside the downloaded ISO.

Now I am in the LiveCD booted to the Dekstop in the self-same machine. (It loads that automatically after the GUI desktop CD installation fails, so one can troubleshoot.)  The LiveCD loads just fine.[1]

So I looked now in /var/log/installer/debug. I believe I found out what's going on:

```
xubuntu@xubuntu:/var/log/installer$ tail debug
WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

No such schema 'com.canonical.indicator.session'
No such schema 'com.canonical.indicator.session'
No such schema 'com.canonical.indicator.session'
Error opening file for reading: Permission denied

** (ubiquity:3349): CRITICAL **: unable to create '/root/.cache/dconf'; dconf will not work properly. 
```[1] For the record, one of my USB sticks won't work in this machine, though. It freezes the machine following or during "Post" on startup -- even after I tell the BIOS to ignore all errors.  The original installation that failed was done via USB, though, as were one or two of the three Linux OSes currently inhabiting other partitions of this machine. (I am trying out which one I like best on this slow, older machine with 512MB RAM. Regular 12.04 is too slow and can get into loads of 50+ sometimes. Zorin 5.02 works well (using the GNOME2 desktop), as does Mint LMDE xfce -- the winner so far.)

---

### Post by spamless on 2012-07-21
I tried it one more time ("eight is enough"!) -- this time, with the Ethernet cable pulled for real.  Same exact failure. I call this a bug in the Xubuntu installation routine.  As I stated above, the LiveCD boots and runs fine.

Ideas on how to proceed?  Or do I just keep using Mint LMDE xfce?

---

### Post by acamas on 2012-07-22
Thank you for your comments, no improvement on my side,
I will try Mint with Xfce.

---

### Post by Version Dependency on 2012-07-22
One thing you might try is downloading the Ubuntu Server 32 bit.  Skip installing all the server-related, so install should be rather quick (about 10 minutes).  When you are finished, all you will have is a command prompt.  Type: sudo apt-get install xubuntu-desktop.

---

### Post by spamless on 2012-07-22
> **Version Dependency said:**
> One thing you might try is downloading the Ubuntu Server 32 bit.  Skip installing all the server-related, so install should be rather quick (about 10 minutes).  When you are finished, all you will have is a command prompt.  Type: sudo apt-get install xubuntu-desktop.

Interesting idea. Maybe I'll try it; I don't know yet. Still, I consider this a real bug and hope the Xubuntu development team will take it up.

I also have a normal Precise installation on the machine, and I know I could take that and install xfce on it and uninstall Unity, and I would have a spiffed-up Xubuntu that way. But I read somewhere that there would still be stuff getting loaded that way that would bog down a slow, older machine such as the one I'm working with, and I wanted to see how straight Xubuntu from scratch compares.

---

### Post by spamless on 2012-07-22
> **acamas said:**
> Thank you for your comments, no improvement on my side,
I will try Mint with Xfce.

What was your situation with Xubuntu? I haven't seen the thread.

---

### Post by derekpock on 2012-07-23
I would definitely try installing server then xubuntu-desktop. The cool thing about this is you can also install different flavors, such as ubuntu-desktop and if you like, also kubuntu-desktop. This would be the most reliable way of fixing this issue. You can also install xubuntu, ubuntu, kubuntu, etcetera, inside exiting linux installations. Just during login, select the desktop type and select, xubuntu, kubuntu, or ubuntu. 


:popcorn: yum

---

