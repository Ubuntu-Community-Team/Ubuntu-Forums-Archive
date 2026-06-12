---
title: "Example case of the Sticky: Graphics Resolution- Upgrade /Blank Screen after reboot"
date: 2011-06-11
forum: Installation &amp; Upgrades
---

### Post by CaronMargarete on 2011-06-11
I have tried the tips, and to the best of my ability understand the later posts from the sticky post "Graphics Resolution" however I seem to keep reverting back to the blank screen.

I did this:
> 
ATI TIPS:
Note that some ATI cards need flgrlx and some do not... If not then this workaround sometimes works:
(Found this in another thread / credit to
Quote:
Originally Posted by surgus View Post
Steps for ATI users:
1. When the boot hangs, press ctrl+alt+f1.
2. Login as user with root privileges.
3. Type "cd /usr/share/ati" and press enter.
4. Type "sudo sh ./fglrx-uninstall.sh" and press enter.
5. Type "sudo reboot".
The above only works for some but not all, depending on what card you have and whether it actually is supported by additional drivers (proprietary). All at the moment, mostl seem to need "nomodeset radeon mode=X", where x= 0 or 1... Some ATI cards are not working with the current natty kernel, but are working with the older 2.6.37 kernel or the proposed 2.6,38.9 kerne (please see post 2)l

Sometimes (rarely) it'll work but more often it won't, and in the two times it's worked I haven't known how to get it to *remember* the setting permanently- keep in mind I have no idea what that last paragraph about x= 0 or 1 means.

Can someone walk me through simple steps in lay-lady terms to get a permanent resolution please?

---

### Post by CaronMargarete on 2011-06-19
I've also asked this same question on Ubuntu Launchpad with immediate response:
[https://answers.launchpad.net/ubuntu/+question/161961](https://answers.launchpad.net/ubuntu/+question/161961)

---

