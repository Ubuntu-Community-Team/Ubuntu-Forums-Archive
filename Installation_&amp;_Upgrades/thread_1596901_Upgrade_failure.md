---
title: "Upgrade failure"
date: 2010-10-14
forum: Installation &amp; Upgrades
---

### Post by joel@parke.ods.org on 2010-10-14
Hi - I upgraded today from 10.04 -> 10.10 and afterboot, the Ubuntu Screen marches through the 5 lit dots and then freezes.  Boot into recovery gets to prompt and can login.  Safe X leads to a list of the users, but can't login, after password, it immediately returns to list of users screen.  Has anyone else seen this and is there a fix?  

Thanks for any help, suggestions!  Desperate!

---

### Post by garvinrick4 on 2010-10-14
After login and password do you get your terminal prompt if so:

```
sudo apt-get -f install
```

```
startx
```Tell us what happens.
You are fixing dependency problems and starting your GUI (desktop) which is also know as x

---

### Post by benbelly on 2010-10-14
I have the same problem. I tried the above and when I run startx, i get:

exec: 3: /usr/bin/X: not found

Which is pretty bad, I'm thinking

---

### Post by garvinrick4 on 2010-10-14
[QUOTE=benbelly;9974038]I have the same problem. I tried the above and when I run startx, i get:

exec: 3: /usr/bin/X: not found

Which is pretty bad, I'm thinking[/QUOTE

```
aptitude show gdm
```
Does it say installed
If not installed:
```
sudo apt-get install gdm
```

---

### Post by joel@parke.ods.org on 2010-10-14
Sorry that it took me so long to reply.  
I was able eventually to boot into recovery and rebuilt broken packages.
Rebooted and then did try apt-get -f install, startx above and it doesn't seem that my problem is directly related to x.  When I boot into recovery and select netroot, I CAN startx and X comes up.  

The problem seems to be related to the display manager.  
When I boot, it now comes to the point that I would normally login.

Now it says:

Not starting X display manager (xdm)
it is not the default display manger

Which brings me to the login prompt.
When I log as my standard user:joel, I get a blank screen.
So I suspect that I have a problem with the gdm and xdm display mangers.  How can I sort that out?

Thanks for your Help!!

---

### Post by joel@parke.ods.org on 2010-10-15
Given that I suspected that the display manger was at issue, I did
apt-get remove xdm
And rebooted.
Now I have a login screen with expected users.
PROBLEM - whenever I attempt to longin, I get bounced back to the login screen.  - How can I debug the startx of a normal user, given that startx from root works?

---

### Post by garvinrick4 on 2010-10-15
[http://www.tuxfiles.org/linuxhelp/changeman.html](http://www.tuxfiles.org/linuxhelp/changeman.html)

---

### Post by joel@parke.ods.org on 2010-10-15
If I boot into recovery and into normal login.
After I have logged into by normal user, I can startx and all is correct.
I still have the problem that the normal login screen is useless.  What gives? How can I correct this?  I suspect that is login screen is attempting to access the xdm display manager which no longer exists.  
How can I set the login screen to use gdm?

Thanks for you help!

---

### Post by garvinrick4 on 2010-10-15
What happens with System/admin/ login screen   when you set it to
log in automatically?
 I do not understand the term "normal user" you mean yourself.

---

### Post by benbelly on 2010-10-15
> **garvinrick4 said:**
> [QUOTE=benbelly;9974038]I have the same problem. 
If not installed:
```
sudo apt-get install gdm
```

After posting last night I checked to see if xorg was installed.  And it wasn't! So I 
```
sudo apt-get install xorg
```
and everything started working.  I had been using xorg edgers ppa in Lucid - I suspect I had problems because of that. I probably should have thought of that right away.

Thanks for the tip!

---

### Post by joel@parke.ods.org on 2010-10-15
I tried the suggestion to look at .xinitrc or .xsession - neither is in existence anywhere on my system.  So I suspect the issue is somewhere deeper - unless I don't understand.  

I checked that both gdm and xorg are already installed.

Before the upgrade I was set to automatically login.  Now the screen with setting for LoginScreen is all grayed out.  How can I get to the settings for LoginScreen which is where I believe the problem is.  OR How do I enable automatic login now?

THANKS for all the help and suggestions - it is getting closer to working, and if I boot into recovery and then normal boot - I can login and startx - I just can't do that through the normal startup.

---

