---
title: "hang on shutdown"
date: 2009-02-19
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by linuxaz on 2009-02-19
Hello,
I just installed the daily x86-64 version of Jaunty from the alternate CD.
The laptop suspends and resumes perfectly, but will not shut down.  It just hangs at a terminal screen.

I can alt-f1 into other screens, but do not have other functioning keys on the keyboard.  There are different messages on these screens.  some look normal, others not.

Where should I look in the logs for a hint as to what is not allowing the machine to shut down properly?

thanks,

bertman

---

### Post by adasilva on 2009-02-23
I am having the same problem, and do not have a solution... 

For starters, check the system log: System-> Administration -> System Log.
This might give you an idea about whats going on.

Also see these posts:
[http://ubuntuforums.org/showthread.php?t=1001648](http://ubuntuforums.org/showthread.php?t=1001648)
[http://ubuntuforums.org/showthread.php?t=966436](http://ubuntuforums.org/showthread.php?t=966436)

The first thread is solved, but the fix there did not work for me. 
The second has a list of known bugs and work-arounds. One is a bug related to alsa (see second thread) which causes the system to hang when it shuts down/restarts.

I hope this helps. Good luck

---

### Post by linuxaz on 2009-02-26
adasilva,
Thanks for the post.
I don't think it's a Pulse or Alsa bug.

I noticed this problem when I upgraded from 8.04 to 8.10.
Then, I did a fresh install of 9.04 Alpha 4 ( I think) and still had the bug.

So far, I have resolved it by removing "quiet splash" from the line in Grub, and adding vga=791.  I found these hints in another post that was fairly short, and goes back to version 8.10.

I have opened a bug report for Jaunty, but not had any response so far.  While now I can boot and shut down just fine, the bug causes the machine to NOT shut down.  I'm concerned that this would confuse a new user.
linuxaz

---

### Post by meborc on 2009-02-28
have the same problem with kubuntu jaunty with latest upgrades... hanks on shutdown & reboot... :(

---

### Post by kde4-core-user on 2009-02-28
I have the same issue since the last updates on Kubuntu Jaunty, but Ctrl + Alt + Backspace and logout/reboot from KDM is still working.

I hope this will get fixed quickly!

---

### Post by meborc on 2009-02-28
yeah, just converted my friend to use/try out linux

i was surprised that everything worked on his laptop, webcam, skype WITH working sounds without needing to configure it like i do

the ONLY thing wrong is the shutdown/reboot hang

i should have given him a cd of ibex instead, but ibex has many problems with pulseaudio which are now fixed in jaunty ;) and he still has his windows partition, so no harm there

---

### Post by jerrylamos on 2009-02-28
On /boot/grub/menu.lst on the kernel line add acpid=noirq after quiet splash.  Helps on a couple of my pc's.

Jerry

---

### Post by linuxaz on 2009-03-11
jerrylamos,
I have not had to add that line since VERY early in the 2.6 kernel.
I would consider this a regression, because everything had been working just fine on this laptop until then.

As of the latest kernel update last night, and the revision to the menu.lst, the problem still exists.

linuxaz

---

### Post by linuxaz on 2009-03-13
Ok,
This thread does not seem too active, so are those affected so few in numbers?
I have opened a bug report #332772 in Launchpad, but have not had a response yet.

Anyone, Anyone?????

linuxaz

---

### Post by Name change on 2009-03-13
I had this problem since Windows time. It stoped when I changed to Linux, but it soon came back.
I found that removing ATA disks "reapired" it. It also made it better.
But that could just be a coincidence I'll hvae to see if it comes back.
(Just to clear things my ATA disk were not original disks but were "salvaged" from an older computer to suit my experimentation needs :D)

---

### Post by linuxaz on 2009-03-13
Primoz,
I don't think it's related to that at all.  As listed above, it appears to be a problem with the implementation of U-splash...I think.

linuxaz

---

### Post by ussndmac on 2009-03-18
Just to add to the frey.

I just installed 8.10 and my system now hangs on shutdown.

the screen shows acpid:

Worked fine under 8.04

---

