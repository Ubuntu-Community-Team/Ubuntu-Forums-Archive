---
title: "upgrade via ssh/vnc - safe?"
date: 2005-04-08
forum: Installation &amp; Upgrades
---

### Post by egg on 2005-04-08
Hi,

I have my warty unit sitting on the internet, connected only via ethernet - no KB/MOUSE/MONITOR etc. My only access to the unit is VNC.

I'd like to upgrade to Hoary and understand that I can do this via the terminal, change the update links and doing an apt-get etc as documented on the forums.

Is this safe to do in my setup? I'm scared that the update process will need some "hands-on" attention... ie, on reboot, will need a new logon or something??

Please imagine my setup (no real access to the unit except ssh/vnc)... and then doing the updates - what problems will I have?

Many Many Thanks!
 :wink:

---

### Post by jobezone on 2005-04-08
There's no reason to reboot the computer after a upgrade, unless you've installed a new kernel (and want to reboot with it).

If I were advising a friend of mine, I would say "Go for it!!":)

---

### Post by dataw0lf on 2005-04-08
Don't just 'go for it'.  Doing sensitive stuff over the internet has a significant challenge to overcome:  what are you going to do if you lose your internet connection?

My advice: install screen (sudo apt-get install screen), and learn it.  If you start up a screen, and start upgrading within it, then detach it, it'll still be there if you lose your connection.

---

### Post by sas on 2005-04-08
[QUOTE=egg]Hi,

I have my warty unit sitting on the internet, connected only via ethernet - no KB/MOUSE/MONITOR etc. My only access to the unit is VNC.

I'd like to upgrade to Hoary and understand that I can do this via the terminal, change the update links and doing an apt-get etc as documented on the forums.

Is this safe to do in my setup? I'm scared that the update process will need some "hands-on" attention... ie, on reboot, will need a new logon or something??

Please imagine my setup (no real access to the unit except ssh/vnc)... and then doing the updates - what problems will I have?

Many Many Thanks!
 :wink:[/QUOTE]
 Hoary installs a new kernel which requires a reboot to use, apart from that I *think* you should be fine. Your existing log-in information etc should work fine too.

---

### Post by egg on 2005-04-08
yeah, im a little scared of going-for-it! Even though I want to :-)

What is screen? Do you have a www link?

I can also access the unit via the LAN it's on... but again, there's NO monitor at that location so the worst case scenario is:

do upgrade,
reboot,
machine hangs on bios OR needs KB interaction etc etc.

that would make me ->  ](*,) 

 :-P

edit: updated to say that there is NO monitor.. typo before - left out the NO ;-)

---

### Post by dataw0lf on 2005-04-08
Here is a brief [tutorial](http://www.kuro5hin.org/story/2004/3/9/16838/14935)  on screen.  
I advise EVERYONE who does any sort of work from the command line to utilize this powerful tool to their full advantage.

---

