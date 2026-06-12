---
title: "Thinkpad i1200"
date: 2006-04-08
forum: Installation &amp; Upgrades
---

### Post by byrdmeln on 2006-04-08
Not sure where this goes.

I've never used Linux before unless you count the qnx I used for a number of years in highschool back in the 80's on old Icon and Lexicon school servers, but that was 20 years ago.

3 weeks ago I installed 5.10 on my laptop, an i1200-1161-250 ...a celeron 500 with 192 megs (max allowed) and a 6 gig hard-drive.  It had been running win98 and I decided it needed an upgrade, and while I don't mind spending money on an operating system the thought of spending money to upgrade an OS I already bought in the firstplace seemed a little much ....hense the Linux. 

Everything loaded up fine, except the Belkin 7010 wireless of course.  I suppose the i1200 can be added to the supported ibm thinkpad list!

After 3 weeks of 6 to 8 hours a day messing around (and having to re-install ubuntu 5 times from my mess ups) I finally got the wireless working though I think my marriage is now in danger.  I googled my eyeballs off, searched these forums to no use, nothing worked, until i came across someones personal blog where they mentioned that the /etc/lib/ndiswrapper/bcmwl5 .conf files had to be edited to turn radiostate on ...and viola, i have wireless with security turned on!  Would have helped me 3 weeks ago if this was public knowledge on this forum /cough cough.

Everything is running well ...but a little slow.  I used the sysv-rc-conf found on this forum and turned off a lot of unneeded startup routines, which did speed up the boot process, but many of the programs within ubuntu still run a little slow.  I downloaded abiword which boots up a hell of a lot faster then openoffice ...but I'm wondering if there are any other tweaks i can do, or things i can remove from my system that I don't really need to speed things up.   I understand that I have an old system, and there is really only so much that can be done ...but any help would be great.  I've googled and searched these forums all morning but I can't seem to find very much about it.  

SO if you skipped all that ...how do i speed up my system? :-D 

Thanks for any help offered.

RT

---

### Post by John.Michael.Kane on 2006-04-08
You can try prelinking [http://www.ubuntuforums.org/showthread.php?t=74197](http://www.ubuntuforums.org/showthread.php?t=74197). also you can just search through synaptic, and remove what you programs and drivers you don't need. i can list some, and you can choose if you want them or not.

bluetooth
printer drivers tools if you don't have or need to print thing's
gimp gthumb eog
gcalc
gnome games
xsane
evolution
tsc=terminal server client
rsync 
rdesk
telnet
irssi
vnc
bittorrent

Hope this helps just take your time searching.

---

### Post by byrdmeln on 2006-04-09
Thanks for the help SD-Plissken.

The first time I tried to remove the items you cited I somehow removed the entire graphical desktop and could only log in under command line.  Oops.  But after a clean re-install, getting my wireless back up in 10 minutes now I know what to do with it, everything is back and running.  The second time I tried to remove everything you listed I was much more careful and things went smoothly.  A lot of freed up diskspace and boot up does seem to go a little faster.

I also Prelinked, which seemed to go well.  Now it only takes 65 or so seconds for Openoffice to open instead of 2 or 3 minutes ...but Abiword still blows open in less then 10 seconds ...wierd.  Firefox is a hell of a lot faster though so well worth doing.

Any other little tweaks for a linux noob? :)

RT

---

