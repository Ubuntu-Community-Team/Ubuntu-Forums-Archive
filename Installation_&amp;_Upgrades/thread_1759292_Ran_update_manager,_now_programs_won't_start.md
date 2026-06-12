---
title: "Ran update manager, now programs won't start"
date: 2011-05-15
forum: Installation &amp; Upgrades
---

### Post by zepolmot on 2011-05-15
So I just ran update manager in 10.04 and rebooted.  Now random programs won't run (so far I've found I can't use Firefox and Tetris).  I tried rebooting again and when it came to the login screen I didn't have a mouse cursor, when I try to upgrade to 10.10 via update manager it fails and I get this message:

An unresolvable problem occurred while calculating the upgrade:
E:Unable to correct problems, you have held broken packages.

 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu

If none of this applies, then please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bug report

Has anybody come across this problem or know how I can repair the broken packages that this error is alluding to?  Thanks.

---

### Post by mörgæs on 2011-05-15
[http://ubuntu4beginners.blogspot.com/2011/03/unresolvable-problem-occurred-while.html](http://ubuntu4beginners.blogspot.com/2011/03/unresolvable-problem-occurred-while.html)

---

### Post by zepolmot on 2011-05-15
Odd, this lets me get to the upgrade now, but Firefox still crashes at startup and again I don't have a mouse at the login screen.  Will report back after the update completes, maybe it'll fix the issue.

---

### Post by zepolmot on 2011-05-15
Well, upgrading to 10.10 did not fix the issue, and I have a whole new problem now.  After the purple 'ubuntu' screen, the signal to my monitor cuts out and the screen goes black.  I have no way to boot to anything besides the BIOS.  Is there a way I can save this?

---

### Post by mörgæs on 2011-05-16
How does a 10.10 live boot work?

---

### Post by zepolmot on 2011-05-16
Good idea, I'll test that after work and give updates.  Thanks for the help.

---

### Post by zepolmot on 2011-05-16
Well the Live USB worked once, and I was able to get into recovery mode.  I tried the 'repair packages' option, and it seemed to work fine.  I rebooted my system hoping to go into the normal boot option, again I got the 'no video' message.  Tried to reboot again and go back into recovery mode however it wouldn't display the GRUB screen.  I shut down the computer and re-made the Live USB, checked to make sure my boot priorities were correct in my BIOS and tried again to get back into recovery mode.  Still getting 'no video'.

---

### Post by zepolmot on 2011-05-16
Ok, so I was able to use my install CD for 10.04 to at least use the 'Try Ubunutu' option to get access to the computer.  Is there a way that I can fix the issue or at least back up my files and install programs from here?  I've read on a few places that trying to update with ATI Catalyst active that some funky issues can come up, I'm wondering if that's whats happened to me.

---

### Post by zepolmot on 2011-05-17
Forget it, reformatting.

---

### Post by scottstensland on 2011-05-17
I@ve had similar issues when attempting an upgrade - tho had to drop kick N reformat as well - only to later see this bit of advice :


    downgrade all ppa prior to upgrade to next release

        sudo ppa-purge ppa : name

this might have allowed the  ~~calculating ....
to successfully negotiate the upgrade 

take care - Scott Stensland

---

### Post by mörgæs on 2011-05-17
Reinstalling is not a bad solution. Get into the habit of reinstalling rather than upgrading, and after doing it a few times it will take you one hour or less.

---

### Post by zepolmot on 2011-05-17
I'm sure its not a bad solution.  Its just that when people are new and switching over to Linux for the first time, losing all of your files and programs  is a pretty **** way of learning that the 'upgrade' button is a lie.  Thank you for trying to walk me through, I'll mark this "solved"

---

### Post by mörgæs on 2011-05-17
Yes, it is very unfortunate that the system does not warn the user that the process is risky. This leads to statements like 'Linux is not ready for prime time, I switch back to Windows'.

---

