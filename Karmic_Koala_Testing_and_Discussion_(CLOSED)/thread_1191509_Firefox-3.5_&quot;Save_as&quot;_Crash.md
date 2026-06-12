---
title: "Firefox-3.5 &quot;Save as&quot; Crash"
date: 2009-06-19
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by taavikko on 2009-06-19
Anyone else experiencing this?

Visit: [www.socwall.com](www.socwall.com)
Click on any picture->
Right click on picture -> "Save image as"
click few times on different folders in "Select destination folder"

this happens on new profile as well with the obvious default one.
new profile: sun-java6-plugin, adobe 64-bit flashplugin(manually installed libflashplayer.so)

default: same as above but also, firegpg, adblock+

So addons aren't ones to blame. Unless somebody made filedialogs to use java/flash :D 

Will do a search for existing bugs in LP before reporting.

Note: [https://wiki.ubuntu.com/MozillaTeam/Bugs](https://wiki.ubuntu.com/MozillaTeam/Bugs)
Could use a bit loving, to accomodate easier debugging...
example, what are the dbg packages I really need to install...

Edit: 
Bug report: [https://bugs.edge.launchpad.net/ubuntu/+source/firefox-3.5/+bug/389340](https://bugs.edge.launchpad.net/ubuntu/+source/firefox-3.5/+bug/389340)

---

### Post by mattduckman on 2009-06-19
I don't experience this crash.

Also your bug report is private.

I have everything you have except on 32-bit and without firegpg.

Is there a pattern to which folders you're looking in when it crashes?

---

### Post by taavikko on 2009-06-19
> **mattduckman said:**
> I don't experience this crash.
Also your bug report is private.
I have everything you have except on 32-bit and without firegpg.
Is there a pattern to which folders you're looking in when it crashes?

I have 2 machines, both with 64-bit systems
Happens with/without extensions.

So it seems that only 64-bit is affected.

Crash happens an all versions available, including fta:s PPA
```
:~$ ls /var/crash/
_usr_lib_firefox-3.5b4_firefox-3.5.999.crash
_usr_lib_firefox-3.5pre_firefox-3.5.999.crash
_usr_lib_firefox-3.6a1pre_firefox-3.6.999.crash
```

Crash is triggered on any images I try to "save image as" and trying to select folder.

About the bugreport, I marked it as "Public" but it keeps getting reverted to "Private".

---

### Post by xebian on 2009-06-19
> **taavikko said:**
> I have 2 machines, both with 64-bit systems
Happens with/without extensions.

So it seems that only 64-bit is affected.

Crash happens an all versions available, including fta:s PPA
```
:~$ ls /var/crash/
_usr_lib_firefox-3.5b4_firefox-3.5.999.crash
_usr_lib_firefox-3.5pre_firefox-3.5.999.crash
_usr_lib_firefox-3.6a1pre_firefox-3.6.999.crash
```

Crash is triggered on any images I try to "save image as" and trying to select folder.

About the bugreport, I marked it as "Public" but it keeps getting reverted to "Private".


No problem here.  64-bit KDE4

---

### Post by taavikko on 2009-06-19
> **xebian said:**
> No problem here.  64-bit KDE4

Just tried saving your avatar, whups, there went Firefox.
64-bit Karmic KDE

Cleaned my ~/ today, left nothing but .ssh/ and .gnupg/
didn't help :(

---

### Post by Hairy_Palms on 2009-06-19
cant replicate it here with the latest nightly from mozilla or the 3.5 PPA tried saving a gif,png,jpeg,bmp, even a .ico

---

