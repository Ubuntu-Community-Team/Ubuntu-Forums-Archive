---
title: "Wide array of weird problems on new laptop: live installation, grub, shutdown"
date: 2016-04-20
forum: Installation &amp; Upgrades
---

### Post by plotor2 on 2016-04-20
Hello.  I have a couple of questions about a variety of issues I'm facing with my new laptop.  I know this sort of scatter shot approach to a thread isn't particularly recommended, but I'm baffled by some of them, and I thought I'd share all of them in case readers have any insight into one or more of them. First up, the laptop: It's a MSI GS60 Ghost Pro-002. with a Core i7 (6700HQ 2.60 GHz) and an Nvidia Geforce GTX 970M, 128GB SSD and 1TB HD.  Came installed with Windows 10 obviously, and for the sake of trying, I figured I would dual boot this machine instead of wiping Win10 off completely.  So I got last nights build of the amd64 install of 16.04 and got it installed to a USB drive.  Here's where the fun starts.

1) Live Installation: Separate thread created: [http://ubuntuforums.org/showthread.php?t=2321090&p=13473075#post13473075](http://ubuntuforums.org/showthread.php?t=2321090&p=13473075#post13473075)

2) GRUB: Separate thread created: [http://ubuntuforums.org/showthread.php?t=2321091&p=13473078#post13473078](http://ubuntuforums.org/showthread.php?t=2321091&p=13473078#post13473078)

3) Shutdown: Ubuntu refuses to shutdown cleanly.  Constantly see a tail of NMI watchdog reports about CPU #0 or #2 being stalled for 22/23 seconds. Kind of troubling, I Googled a bit on this one and couldn't find much.  I end up holding the power button down to force it off.  Less than ideal.

Does anyone have any thoughts about all of this? Things I should have tried, or should try if I factory reset the machine and try again?  (which I'm sorely tempted to do.) Would love to know what people think.  Thanks very much for reading this and for any help you can provide.

---

### Post by Bucky Ball on 2016-04-20
Welcome. No, it is not recommended for good reasons so please do not post multiple support requests in one thread. You severely deplete your chances of support with any one of them and it is confusing.

I suggest you edit your post above to question three only as that appears to be your actual current problem by the looks of it: you can't get a clean shutdown. If you want to ask questions or need support with something else, best to post new threads.

You managed to install and get a grub menu (well done) so you don't need support with doing that.

So, focusing on question three. When it gets stuck, can you hit control+alt+F1 and get to a CLI with a cursor? If so, you can log in and shutdown with:

> sudo shutdown -h now

Before you do that, in the CLI, type:

> dmesg

... and hit enter. This may give a clue what's going on with the bottom of that output.

---

### Post by plotor2 on 2016-04-20
> **Bucky Ball said:**
> Welcome. No, it is not recommended for good reasons so please do not post multiple support requests in one thread. You severely deplete your chances of support with any one of them and it is confusing.

You're absolutely right, that was the result of "it's 2am and I just want to type this up and go to sleep" thinking.  I broke the other two out to separate threads and linked them in.

> **Bucky Ball said:**
> 
So, focusing on question three. When it gets stuck, can you hit control+alt+F1 and get to a CLI with a cursor?

I will put a pastebin of the output when I get home tomorrow night, but from my experiments this morning, it's finicky.  The only way I got this to be somewhat useful, was to login to a CLI prior to shutting down, do a dmesg -w, over there, come back to the desktop and initiate the shutdown with a slight delay, and then go back to the CLI before the shutdown kicked in.  Once the shutdown starts, I'm unable to switch to any CLI, 1 through 6.

Interestingly, I also tried to initiate a partial upgrade to the OS, and ran into a freezing problem there too.  It wouldn't complete and it blocked shutdown.  I'm wondering how much of this has anything to do with incompatibilities with the ath10k hardware in the laptop.  I haven't begun to research how to fix that yet, I think that's my next step.  I'll paste the output of dmesg tonight.  Thanks for your help.

---

### Post by plotor2 on 2016-04-23
Third party Intel drivers + software update = happy shutdown.  Thanks for everyone's help.

---

### Post by ali60 on 2016-04-24
Hey mate,

It seems we are facing exactly the same issue. I've just purchased a new laptop with similar specs to yours, and I got the same issue (not seeing unity, seeing desktop background, and seeing a lot of the 'unity experienced a problem' flashing popups).

How did you manage to work this out? Can you share some more details please?

---

