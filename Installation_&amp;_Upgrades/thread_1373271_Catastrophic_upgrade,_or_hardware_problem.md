---
title: "Catastrophic upgrade, or hardware problem?"
date: 2010-01-05
forum: Installation &amp; Upgrades
---

### Post by GregIthaca on 2010-01-05
Running Xubuntu 8.04..3 LTS on fairly new server-class hardware with industrial CF card for boot/root and RAID-1 drives for /var, /home, and data.  It has been running fine (although the GUI takes some getting used to...) for about 2 months.

It all started yesterday when I noticed my clock was off, and realized I'd never installed NTP.  I tried to use the 'Applications: System: Time and Date' function but ran into the problem so many others have reported, for which I found no answer -- that although I would change 'Manual' to say 'Keep synchronized with internet servers', and it would pop up telling me I needed to install ntp, and would offer to do it, and I would accept, at the end, it would come back to saying 'Manual' again.

I decided maybe I should go ahead an install the pending updates that it was telling me about.  Partway through this process, I noticed (from another room) that my ssh to the server had died.  When I came back, I found that I couldn't ssh, I couldn't sudo, and I couldn't even 'do' -- something had trashed the libraries.

I thought, well, what the heck, maybe I need to reboot like it is telling me, and then everything will be fine.  So I tried this, and it hung shortly after the graphic came on the screen.  So I tried the grub recovery mode boot, and that told me the kernel was panicing because it couldn't load /sbin/init.

Yikes.  Not only was I down, but I also no longer had any internet connection to be able to research the problem.  I got my dad to look around online, and he came across this cryptic thread, not obviously related:

[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1347696;wq](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1347696;wq)

In short, it convinced me I wasn't the only one who was having problems with my /lib directory getting wiped out.  I spent the evening at a friend's house downloading the Live CD, and this morning was able to boot from that.

When I got there, I could see that most of the /lib directory (**all** the lib*.so files, and many others) was gone.  I did the best I could by copying from the live CD, and after about 6 rounds of copying, rebooting, recopying, fscking away over 200MB of bad inodes (based on what I found in /lost+found later), rebooting, looking for more missing files, rebooting, trying dpkg updates, etc. I got back to the point where I could actually get into the system and into a functional user interface.

I had 48 packages that were missing files; 11 where files had bad checksums, 43 with no checksums on record, and 3 other library files I had to reinstall to correct error messages.

What I can't tell is whether the problem started with hard errors on the CF card (seems unlikely, remember it's only 2 months old and industrial grade), or whether it started with some package run amok which prevented all the running applications from properly closing their files when the system crashed.

In any case, it took me about 4 hours to get back to a working system, and taught me a lot of things I wish I never had to know... like the fact that there is no single tool (that I could find) which will verify the installed packages and only re-download and reinstall those that have problems.

I there anyone else having this kind of problem after a recent upgrade, or should I suspect my hardware?

Greg Nelson      
White Hawk Ecovillage
Ithaca, NY 14850
[www.whitehawk.org]("http://www.whitehawk.org")

---

