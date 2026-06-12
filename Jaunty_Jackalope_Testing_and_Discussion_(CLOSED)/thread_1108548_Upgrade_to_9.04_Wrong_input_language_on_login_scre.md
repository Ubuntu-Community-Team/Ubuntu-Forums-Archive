---
title: "Upgrade to 9.04: Wrong input language on login screen"
date: 2009-03-27
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by roland_j on 2009-03-27
Hi,

after the upgrade to 9.04, I have the wrong input language on my login screen. It seems to be Arabic (from right to left). Login is not possible. It rebooted from a live CD and checked /etc/default/locale (US-English) and /etc/X11/xorg.conf (No lang. is specified). Maybe I made the mistake during the upgrade procedure. How can I switch to English as the login screen input language?

Thanks & regards
Roland

---

### Post by newschapmj1 on 2009-03-28
I got the same problem.

I downloaded the standard desktop PC image for Intel machines yesterday.
I did a fresh install today and installed for UK options.
The 1st thing I did was check for updates then I started having problems.

When I looked at the systems, admin,language support it said  English UK but 'arabic' text appeared right to left in a text editor and the browser.

I have just formatted and installed and everything is fine.
I have skipped the updates for the moment.

---

### Post by grokdesigns on 2009-03-28
Having the same problem after updating. Hope someone figures out how to fix it.

---

### Post by xtoudi on 2009-03-28
The same here. I don't know any workaround so... I did a fresh install a whole Jaunty 9.04 Beta and after update (again) everything is ok.

---

### Post by morfeibg on 2009-03-28
Same problem here.
I just made new installation of the 32 bit desktop version.
After the installation I installed all updates and restarted my laptop. After the restart on the logon screen the input language was changed to Arabic and I couldn't not log in anymore.
Anyone know how we could fix that?

---

### Post by morfeibg on 2009-03-28
Hello Guys,
I figured it is more than the input language at the login screen.
When I restart in recover mode the input language was still wrong.
I'm not able to type anything with this language in the root console. What file defines what is the input language when the recovery shell starts?

---

### Post by Nullack on 2009-03-28
Bug report?

---

### Post by Nelson-Ray on 2009-03-28
I was able to get past the login screen (rebooted into ubuntu 8.10 and mounted the 9.04 partition) then edited /etc/gdm/gdm.conf-custom and added under [daemon]

AutomaticLoginEnable=true
AutomaticLogin=username
TimedLoginEnable=true
TimedLogin=username
TimedLoginDelay=5

but once in ubuntu 9.04 .... the gnome panels are locked & doesn't work at all. Furthermore I managed to open konqueror and when typing in the input box the language was coming out arabic and left to right. Hope there is a fix for this (not sure how the hell I am going to download the update).

---

### Post by mcnate on 2009-03-28
I was able to fix this on my laptop.
- Looked in /etc/default/console-setup and saw that XKBLAYOUT was set to "af".
- Changed XKBLAYOUT to "us".

---

### Post by xtoudi on 2009-03-29
This is a bug! I made another new instalation of 9.04 beta, new full upgrade and there is this problem! After upgrade XKBLAYOUT is changed to "af" / **XKBLAYOUT="af" (/etc/default/console-setup)** / - thanks mcnate.

---

### Post by williane on 2009-03-29
So how are you guys able to edit [B]/etc/default/console-setup?

[/B]I'm trying to boot to terminal to fix this but I'm not sure how.

---

### Post by morfeibg on 2009-03-30
You have to boot from CD, mount the partition where ubuntu is installed and then edit the file.

---

### Post by Sarai the Geek on 2009-03-31
There was another more recent post about this, and I ended up writing a blog post with a fairly detailed explanation of how to fix this. It is here: [http://saraithegeek.wordpress.com/2009/03/30/jaunty-default-keyboard-bug/](http://saraithegeek.wordpress.com/2009/03/30/jaunty-default-keyboard-bug/)

Not to toot my own horn or anything. I just don't want to retype it. ;)

---

### Post by paxmark1 on 2009-04-08
Jaunty worked well for over a week.  I dist upgraded into the late alpha time with no problems whatsoever. 
 
I have rectangles for fonts after an update on Jaunty.  And when I go to root terminal to repair, I can't even cd as my forward slash / comes up as something else and I cannot seem to find where it (/) went.

I suppose I could file a bug report, but it just seems so hard to describe the wild permutations I had with the various tries at logging in via Ubuntu or XFCE and the two kernel flavours.  Very little replication possible, every try had a slightly different flavour.  Every once in a blue moon I could get it up and the only app that had correct language (not rectangles for letters) was opera.  Previous to the glitch I also added the "free" windows fonts via aptitude install prior to restarting.  And then enabled.  That might be part of it and it might not even be the updates of April 4-5.  

I suppose I could use this as a learning experience with knoppix or the live cd to get it up, but I am just going to do a new install.

So I downloaded the daily and will just do a total reinstall.

peace mark

---

### Post by tubegeek on 2009-04-11
Thanks to sarai the geek!

is there anything clever that can be done to prevent re-ocurrence? Can the /etc/default/console-layout be locked or the af option made unavailable?

---

### Post by jtniehof on 2009-04-11
> **tubegeek said:**
> is there anything clever that can be done to prevent re-ocurrence? Can the /etc/default/console-layout be locked or the af option made unavailable?

I would suggest dpkg-reconfigure console-setup to make sure everything is set properly across the board. (Directly editing XKBLAYOUT didn't fix my console.)

I see you've already found the bug report, but just so everybody sees all the discussion: [the other forum thread](http://ubuntuforums.org/showthread.php?t=1111564); [the bug report](https://bugs.launchpad.net/ubuntu/+source/console-setup/+bug/357971).

---

### Post by Sarai the Geek on 2009-04-11
> **jtniehof said:**
> I would suggest dpkg-reconfigure console-setup to make sure everything is set properly across the board. (Directly editing XKBLAYOUT didn't fix my console.)

I see you've already found the bug report, but just so everybody sees all the discussion: [the other forum thread]("http://ubuntuforums.org/showthread.php?t=1111564"); [the bug report]("https://bugs.launchpad.net/ubuntu/+source/console-setup/+bug/357971").

I've added this to my blog post as well. It's getting quite a bit of traffic, hopefully that will redirect some people over to the bug report.

---

