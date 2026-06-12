---
title: "Installed Ubuntu 10.04, but cannot login."
date: 2010-07-06
forum: Installation &amp; Upgrades
---

### Post by codecutter on 2010-07-06
Hello,
I installed Ubuntu on my desktop yesterday, using LiveCD. I am using dual boot option (with Windows Vista). During installation I selected all the default options and Ubuntu created the partition etc.

Now when I boot the computer, I see following options.

GNU GRUB Version 1.98-1ubuntu6

1. Ubuntu with Linux 2.6.32-23-generic-pae
2. Ubuntu with Linux 2.6.32-23-generic-pae (recovery mode)
3. Memory test (memtest86+)
4. Memory test (memtest 86+, serial console 115200)
5. Windows Recovery Environment (loader) (on /dev/sda3)
6. Microsoft Windows XP Home edition (on /dev/sdb1)

If I select 1st option, the screen color changes to purple so I expect the Ubuntu login screen. What happens is that it does not show me login screen. Instead I hear drum beating sound. Even if I hit escape key, login screen does not show up. Looks as if I pressed Enter key (which I did not) and Ubuntu is waiting for input or it is in a loop.

I selected 2nd option of recovery mode and reinstalled all packages, but still same problem. I cannot login to Ubuntu. 

Any help will be appreciated.

Thanks,

(newbie) codecutter

PS: Option 5 lets me log in to Windows, although the wording seems incorrect. It is not Recovery Environment, those are the real Windows.

---

### Post by WinRiddance on 2010-07-06
Go ahead and reboot, then select the very first boot option for Ubuntu. Walk away for a couple of minutes, make a cup of coffee or whatever, and let me know what you see on your screen a few minutes later.

---

### Post by codecutter on 2010-07-06
Indeed it worked after rebooting. I didn't even have to wait that long.
(and I used to think Ubuntu is different than Windozs) LOL. :p

Can you please explain what may have been wrong the first time? I had waited earlier as well.
Thanks.

---

### Post by WinRiddance on 2010-07-06
Well, it's not so much that anything went wrong, but rather that I've noticed a couple of times during past installations that sometimes not everything is 100% finished compiling yet ... during the first restart of the computer. I've noticed this primarily on older machines where it seemed as though all of the processes were just too much to complete the first time around. But then, a reboot or two later, with a little bit of patience, everything seems to be fine.

Noticed this first when I installed Ubuntu for some friends of mine last year who had an older AMD 3700+ 64bit processor and 1 GB of Ram with 128 MB ATI graphics. Don't know why but for some reason that machine takes close to 2 minutes to complete the boot cycle ... and most people don't have patience that long ... start hitting keys which then might interrupt the boot process altogether. That's why I suggested the 2 minute wait time because once the boot completes everything runs perfectly fine for them, so I figured that a little bit of "excessive" patience might work for you too ...

Live and learn, right? :D

---

### Post by codecutter on 2010-07-06
Patience is definitely needed. I agree with you 100%. Thanks for the quick replies.

Now on to my next task. Converting my wife and kids to be Linux lovers and getting rid of M$ stuff.
Thanks again for this wonderful forum and all the help.

PS: How do I change the thread status to "Solved". I found it when I created the thread, but don't see it in reply. Please close the thread if appropriate. (Found it under Thread Tools.)

---

### Post by codecutter on 2010-07-07
Well, I guess I celebrated too quickly. Today I am having same problem since rebootig computer. Yesterday I did not shut down at all, so Ubuntu was working fine. Now I am not able to log-in. The log-in screen starts playing drum sound and screen goes blank.

I have restarted the computer 4 times already, stepped away from computer 10 minutes or more each time, as suggested earlier. This is really frustrating.
Please help how to log-in.

---

### Post by WinRiddance on 2010-07-08
**#1**. Try a hard reboot i.e. power down completely, wait a minute and then power up again. Maybe we'll get lucky and that will work ...

**#2**. If you don't get a Grub menu (boot selection) because Ubuntu is the only OS on that system, start _tapping your shift key every second or two_ once you've started the system. If you see the grub menu then, try to enter the recovery options with network support (requires a network cable to be connected since WiFi is often not located in this mode).

Eventually you'll see a screen with several option. Use your arrow keys to select "repair broken packages" and when that's done reboot. If that still won't work get back into the recovery option as before and then try to use the low graphics mode which will help determine if your graphic chip may be part of the problem.

**#3**. Download the most current version of Lucid, burn yourself a _fresh & updated_ ISO boot CD and try reinstalling the system. If you've only had it installed for a day or two there's probably nothing critical that you'd be overwriting if you're installing to the same partition as before. Also make sure that that partition is formatted as a **ext4** file system which is standard for Ubuntu 10.04

**#4**. If you have a laptop with a second display, disconnect the second display before rebooting. If none of this helps bump the thread back up or start another one with more specific details if you have any. **Good luck**.

---

### Post by codecutter on 2010-08-02
Update:
I was still having problem such that drumming sound would come up. After 3-4 rebooting attempts the system used to allow me to login.

A few days ago, I made the following change.
From System => Preferences => startup applications, I unselected "Visual Assistance" .
That seems to have helped resolve the problem. I don't know why or how.
Thanks.

---

