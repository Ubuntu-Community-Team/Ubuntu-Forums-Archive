---
title: "Freeze during text based install, clue about reason"
date: 2007-12-30
forum: Installation &amp; Upgrades
---

### Post by tim_c on 2007-12-30
I've been going through "difficulty" trying to get anything new onto an old laptop but severe install problems happen every time... Windows 98 or XP have no problem whatsoever though. :-)

Having tried most BSD and quite a few Linux I decided to try hard with Xubuntu text based install, alt CD. (only thing that worked immediately out of the box was plain DSL, Puppy wouldn't, strange stuff)

I won't bother with the machine details, what follows is general.

The machine consistently stalls with the Debian text install (seen it with a similar other Linux) at

"Select and install software
Configuring xserver-org"

Symptoms are the disk activity stops, I thought no keyboard.

If you look at this December 2006 thread 
[http://ubuntuforums.org/archive/index.php/t-315632.html](http://ubuntuforums.org/archive/index.php/t-315632.html)
it mentions the same thing, found the same elsewhere too.

Today whilst waiting for something else I carried on web trawling, read the following, bingo, a clue

[https://help.ubuntu.com/community/Installation/I386](https://help.ubuntu.com/community/Installation/I386)
Yeah the standard installation instructions!

The text there says this
"During this process, you will be asked about Configuring xserver-xorg. It should be safe to just press Return to continue with the installation. However, if you like, you can use this opportunity to select which display resolutions you may want to use in the future. Several should already be selected."

Penny dropped, so I hit enter. Instant hard disk activity followed by CD activity.

What I think is happening is a terminal message is being put up in a hidden terminal, the screen actually showing
"Select and install software
Configuring xserver-org"
And a text based progress bar.

This is a bug methinks. What I have silently agreed to I hate to think, still installing to much whirring :-)

---

### Post by foolsh on 2007-12-31
A log is output to termainal 4 I think ctrl+alt+F4 
much luck to you

---

