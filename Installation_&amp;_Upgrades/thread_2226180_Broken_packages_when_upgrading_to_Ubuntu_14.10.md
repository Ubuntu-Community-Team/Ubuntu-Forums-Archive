---
title: "Broken packages when upgrading to Ubuntu 14.10"
date: 2014-05-25
forum: Installation &amp; Upgrades
---

### Post by superpurple11 on 2014-05-25
Hello,

Recently I tried to upgrade to Ubuntu 14.10 (Trusty Tahr). It must have somehow went wrong, because when I logged into my computer again, it was still on 13.10. Now, when I try to open my software updater or anything related, they a) don't open or b) ask to repair broken packages, then the repair isn't supported or fails.

I'd like to upgrade to receive support again. What do I do?

---

### Post by ian-weisser on 2014-05-26
First, open a terminal and try:
```
do-release-upgrade
```

If it doesn't work, then please show us the output, and then also show us the contents of /etc/apt/sources.list and all the files (yes, *all* of them) in /etc/apt/sources.list.d

---

### Post by superpurple11 on 2014-05-27
I tried that, the result was:

No new release found

I tried to open the sources.list, but my entire update application doesn't open, so I can't view the file.
The contents of the /etc/apt/sources.list.d folder are: steam.list.distUpgrade, google-chrome.list, steam.list, and google-chrome.list.distUpgrade.

Do those mean anything?

---

### Post by ian-weisser on 2014-05-27
Not much.
We need the complete text content of all those files, not the mere file names.

They will all open in any *text editor* like gedit or mousepad or bluefish or nano.
Do _not_ use a *word processor* to open them.
Do not double-click on the files to open them. That will open them in something else. Seems like that's what you tried to do.

---

### Post by superpurple11 on 2014-05-31
Here is one of the Google Chrome files:

### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main

The rest are very similar, with weblinks. See also:

# deb [http://repo.steampowered.com/steam/](http://repo.steampowered.com/steam/) precise steam # disabled on upgrade to saucy
# deb-src [http://repo.steampowered.com/steam/](http://repo.steampowered.com/steam/) precise steam # disabled on upgrade to saucy

---

### Post by Bashing-om on 2014-05-31
superpurple11; Hi !  My Welcome to the forum.

In order for us to assist you you must follow the directives given - entirely and exactly.
To that end is the instructions to do so;
Post all requested outputs between code tags:
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
And show us the outputs of terminal ( ctl + alt + t ) commands:
```

sudo do-release-upgrade
cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*

```
So we can see where you are at, and where you are going. Anything you do not understand or have questions regarding, we are more than glad to expound and explain.

[INDENT][INDENT]it is all a process
[INDENT][INDENT][INDENT]even in the learning
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

