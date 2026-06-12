---
title: "Funny thing happened on the way to upgrading to 2.6.20.16"
date: 2007-09-30
forum: Installation &amp; Upgrades
---

### Post by dryder on 2007-09-30
Hi,

I am not so quick to install updates to Feisty after the disastrous update earlier in the life of Feisty. So the last nine were installed a week or so after I was notified.

I checked out the forums and did not see any posts complaining about them and proceeded to upgrade from 2.6.20.15 to 2.6.20.16.

The install process warned me of "serious bug in ... leading to freezing of update manager - Proceed (y/n)? .... or something similar. Methought that as I had not seen any posts then it was probably OK to proceed - and to be honest I did not understand why the message implied an update was put out knowing it had a 'serious bug' in it.

What do those warning messages mean anyway, given the implication above?

Well, during the reboot the boot process failed, ("what did you expect after ignoring the warning", do I hear some say? :) ), went to text mode and I was told a few things were not installed; one was apt-get and the message said 'you can install this by typing the command aptitude apt-get, or something very similar. Sorry I did not diligently write all this down.

Anyway, after typing in 'reboot' the process continued to my log in screen. Funny how it thought reboot meant 'continue'.

After logging in  .... all my hard drive icons were missing and the drivers inaccessible via /media/... 

Definitely this update had not gone as planned. Went to bed, got up this morning and rebooted my system, intending to revert to .15 if it failed again, but nope, the new kernel etc booted perfectly this time and my drive icons have reappeared. I can even still access the ntfs ones.

Has anybody any idea why the initial boot would fail but subsequent boots succeed? And why those 'Do you want to continue (y/n)?' messages appear when doing updates?

Many thanks,
David

---

### Post by Pumalite on 2007-09-30
Count yourself lucky.

---

### Post by dryder on 2007-09-30
That teaches me (and others) absolutely nothing.

Do you intend to keep knowledge to yourself or do you just like to increase your bean count?

---

### Post by Pumalite on 2007-09-30
I wish I had the answer.

---

