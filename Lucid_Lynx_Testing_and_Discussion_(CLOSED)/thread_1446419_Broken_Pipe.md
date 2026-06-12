---
title: "Broken Pipe"
date: 2010-04-04
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by beegary on 2010-04-04
I installed 10.04 yesterday, everything works fine except.....

When booting before the splash screen I get a terminal type output, it comes and goes so quickly I am unable to see the full output (is there a way of outputting this to a text file) what I do catch is a Broken Pipe message relating to Firefox?

Is this caused by me keeping my .mozilla config folder from my Karmic install?

---

### Post by praveenthivari on 2010-04-04
> **beegary said:**
> I installed 10.04 yesterday, everything works fine except.....

When booting before the splash screen I get a terminal type output, it comes and goes so quickly I am unable to see the full output (is there a way of outputting this to a text file) what I do catch is a Broken Pipe message relating to Firefox?

Is this caused by me keeping my .mozilla config folder from my Karmic install?

Same here. Some broken pipes msg and could not write bytes.

---

### Post by djchandler on 2010-04-04
> **beegary said:**
> I installed 10.04 yesterday, everything works fine except.....

When booting before the splash screen I get a terminal type output, it comes and goes so quickly I am unable to see the full output (is there a way of outputting this to a text file) what I do catch is a Broken Pipe message relating to Firefox?

Is this caused by me keeping my .mozilla config folder from my Karmic install?

I assume you mean that this appears between the log-in screen and Gnome desktop appearing.

Perhaps "Path=" in profiles.ini does not point to your data folder, which is in the same directory, /home/yourname/.mozilla/firefox.

For instance, where x stands for any alpha-numeric character, if that line reads:

Path=xxxxxxxx.default

then your data folder, residing in that same directory, would be named:

xxxxxxx.default

Only some things from that folder should be kept from 9.10. There may be other changes in .mozilla configuration data structures between 3.5.x and 3.6.x causing your problems. Your only personal data that you really need is in .mozilla/firefox and consists of your cookies.sqlite, cookies.sqlite-journal and bookmarks.html files in the xxxxxxxx.default folder. You may want to keep blocklist.xml if you use the NoScript add-on. Some extensions from 3.5.x in your xxxxxxxx.default folder may not work with 3.6.x.

A re-install of firefox may fix the problem by overwriting the troublesome configuration files and culling the incompatible extensions. I suggest only copying cookies.sqlite, cookies.sqlite-journal and bookmarks.html to xxxxxxxx.default after you open firefox one time with the default config following the re-install.

---

### Post by zenarcher on 2010-04-04
> **praveenthivari said:**
> Same here. Some broken pipes msg and could not write bytes.

I'm seeing the same thing here with Kubuntu.  Some broken pipes messages and could not write bytes.

Cheers,
zenarcher

---

### Post by beegary on 2010-04-04
> **djchandler said:**
> I assume you mean that this appears between the log-in screen and Gnome desktop appearing.


Thank you for your help. It appears immediately before the login screen, I tried to pause it but the login screen appears over the top of it before I can take a close look.
Is there a way of storing the complete output of these errors somewhere, or is it just worth me forgetting about it (boot time is still ok) and waiting until the full release?

I did a complete firefox re-install. I wasnt that bothered about keeping my settings so I just purged and started again.
Im still getting some pipes broken and other messages. One of which says something about user/bin/firefox I think??

---

### Post by 98cwitr on 2010-04-05
just happened to me...I just upgraded from grub to grub2 and have been messing around with plymouth themes. It seems to happen when I try to download updates :popcorn:

---

### Post by gare on 2010-04-05
I have same problem with the fun addition that am caught in login loop and can not get to gdm at all - the login prompt just reappears after some broken pipe message flashes.

---

### Post by mrowth on 2010-04-05
Here's a screenshot of my boot messages, including the "broken pipe" in its possible context, as they appear on the 7th virtual terminal (KDM starts on #8 now). 
[http://img28.imageshack.us/img28/1352/p1010033r.jpg](http://img28.imageshack.us/img28/1352/p1010033r.jpg)

---

### Post by 98cwitr on 2010-04-05
^^^i had no where near that much info...now Chrome is crashing ever so often. :(

and now just get "Caught segmentation fault, core dumped" Ubuntu's BSOD huh? <snip>.

---

### Post by beegary on 2010-04-07
> **beegary said:**
> 
Is there a way of storing the complete output of these errors somewhere, or is it just worth me forgetting about it (boot time is still ok) and waiting until the full release?


I did manage to read some of the info, seems to be having a problem with the following file:
/etc/apparmor/functions

and this entry in it....
```

PROFILES="/etc/apparmor.d"
```

This file doesnt exist?????:confused:

---

### Post by mhpathfinder on 2010-04-08
Get same message, "Broken pipe: cannot write bytes" on my ASUS EEE PC 1000HEB, although from the previous reports this seems to have nothing to do with hardware and everything to do with profile locations, at least Firefox profiles.

I echo that this did not occur until I ran my most recent updates, i.e.,
sudo apt-get update
sudo aptitude safe-upgrade

Whatever the bug is, it seems to be in one of the most recent LUCID builds.

After the broken pipe message, which flashes quickly on boot-up, everything opens ups and works fine, excepting some of my hotkeys for sound and screen settings, which haven't worked in any of the alpha versions, nor this beta version.  Optimistic that fixes will be in by end of April.
Amen

---

### Post by nerdy_kid on 2010-04-08
have this issue too (kubuntu) i dont have firefox installed.
doesnt seems to effect anything though.  just complains.

---

### Post by manoynmonic on 2010-04-08
I get this whenever I run anything that requires video - totem, skype video, etc.  The whole system crashes/BSOD's and requires a hard restart. :confused:

---

### Post by beegary on 2010-04-09
> **beegary said:**
> I did manage to read some of the info, seems to be having a problem with the following file:
/etc/apparmor/functions

and this entry in it....
```

PROFILES="/etc/apparmor.d"
```This file doesnt exist?????:confused:


**Please can anyone help me with capturing the boot sequence information??? Is it stored in a log file somewhere so I can better trouble shoot?**

I have found out a little more: 

~/apparmor.d is a folder

The error mentions that it is skipping a profile that it cant find in: usr.bin.firefox which is in /etc/appmor.d

However I cannot find any mention of a profile in that file or any that it references. This must be something to do with the way I originally tried to copy all my firefox settings......
I still have broken pipes but I think this error is unrelated.

---

### Post by mrowth on 2010-04-09
> **beegary said:**
> **Please can anyone help me with capturing the boot sequence information??? Is it stored in a log file somewhere so I can better trouble shoot?**
There's /var/log/boot.log but mine doesn't contain the "Broken pipe" business and stops at "* Starting AppArmor profiles".

However, the messages stay put on the otherwise unused VT #7 in my case so I can examine them with a Ctrl-Alt-F7. 

> I have found out a little more: 

~/apparmor.d is a folder

The error mentions that it is skipping a profile that it cant find in: usr.bin.firefox which is in /etc/appmor.d
In my case at least it seems to be skipping 
usr.bin.firefox
usr.bin.firefox-3.5
usr.bin.firefox-3.7
because those are linked to in the directory /etc/apparmor.d/disable, not because they're missing.

> However I cannot find any mention of a profile in that file or any that it references.
The file usr.bin.firefox itself **is** an AppArmor profile.

> I still have broken pipes but I think this error is unrelated.
Me too. I suspect it's to do with ureadahead. But iIt doesn't seem to be causing any problems so I don't much care at this point. Boots fast, too.

---

### Post by xir_ on 2010-04-09
> **beegary said:**
> **Please can anyone help me with capturing the boot sequence information??? Is it stored in a log file somewhere so I can better trouble shoot?**

I have found out a little more: 

~/apparmor.d is a folder

The error mentions that it is skipping a profile that it cant find in: usr.bin.firefox which is in /etc/appmor.d

However I cannot find any mention of a profile in that file or any that it references. This must be something to do with the way I originally tried to copy all my firefox settings......
I still have broken pipes but I think this error is unrelated.

dmesg is a good one

---

### Post by -humanaut- on 2010-04-09
When I first downloaded and installed 'Beta2' I had this exact problem however I downloaded a fresh ISO image and put it on usb stick and did a clean install seemed to work so far.

---

### Post by mrfelker on 2010-04-12
The broke error only appers for me extremely bariefly on reboot only.  It did appear during the last large update to the update which I did today.  I expect it will be fixed in the GA.

Marty Felekr

> **mhpathfinder said:**
> Get same message, "Broken pipe: cannot write bytes" on my ASUS EEE PC 1000HEB, although from the previous reports this seems to have nothing to do with hardware and everything to do with profile locations, at least Firefox profiles.

I echo that this did not occur until I ran my most recent updates, i.e.,
sudo apt-get update
sudo aptitude safe-upgrade

Whatever the bug is, it seems to be in one of the most recent LUCID builds.

After the broken pipe message, which flashes quickly on boot-up, everything opens ups and works fine, excepting some of my hotkeys for sound and screen settings, which haven't worked in any of the alpha versions, nor this beta version.  Optimistic that fixes will be in by end of April.
Amen

---

### Post by InF3XioN on 2010-04-13
> **gare said:**
> I have same problem with the fun addition that am caught in login loop and can not get to gdm at all - the login prompt just reappears after some broken pipe message flashes.
I have a similar problem in Kubuntu beta2. The "proken pipes" message appears on splash screen and when I try to login, the screen turns black and the login screen reappears again. This happens every time a try to login. I can only access my files in failsafe graphics mode, but with no desktop manager.

---

### Post by forcecore on 2010-04-13
i see those too, some 5 messages about that broken pipe but it wont do anything, everything works fine :confused: . Fresh daily 11 installed on laptop.

---

### Post by ronparent on 2010-04-13
I may be probing into an area whare I am out of my depth. But my impression is that the "broken pipes" message can occur on any machine with an AMD processor or any Intel core that predates piping. For he most part Ubuntu seems to be designed to cope with it. So the messages themselves may be of no consequences. I have found, however, that I invite a kernel freeze if I don't use the noapic nolapic opyions on my older AMD systems!

---

### Post by null_pointer_us on 2010-04-13
My Core 2 Duo machine has this "broken pipes" message, too.

I think "pipes" refers to the | in a shell command, not a processor feature.

---

### Post by InF3XioN on 2010-04-13
> **InF3XioN said:**
> I have a similar problem in Kubuntu beta2. The "proken pipes" message appears on splash screen and when I try to login, the screen turns black and the login screen reappears again. This happens every time a try to login. I can only access my files in failsafe graphics mode, but with no desktop manager.
Actually, I managed to solve the problem with the login screen. The 195.36.15 version of NVidia driver that is downloaded from the repositories has a corruption that caused kmserver to stop. So I had to download the driver manually, from the site of NVidia. Although, the "broken pipes" issue remains...

---

