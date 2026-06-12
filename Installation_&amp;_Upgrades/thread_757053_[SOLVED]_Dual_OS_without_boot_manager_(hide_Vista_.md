---
title: "[SOLVED] Dual OS without boot manager (hide Vista unless REALLY needed)"
date: 2008-04-16
forum: Installation &amp; Upgrades
---

### Post by Palu on 2008-04-16
Upon Hardy Heron's launch in 8 days I'm going to make the change to Ubuntu... my roommates also use my computers. The main computer runs Vista and I'd like to skin it to look like Vista (I'm new, but the tutorials are good) and see how long it takes them to notice it isn't Windows. Setting up dual boot sounds easy enough, but I would rather it always go to Ubuntu without showing a menu and just have a special way to go to Vista. It doesn't matter how clunky the method is.

[This post]("http://ubuntuforums.org/showthread.php?t=267674") was helpful because it mentioned that I could set the boot menu to 0 seconds... but I wouldn't know how to boot to Vista at all. I need to compile under Windows now and then, so I can't delete Vista, sadly.

Thank you so much. :popcorn:

---

### Post by LeoSolaris on 2008-04-16
You sould be able to set up a blank screen that says, "Push ESC for boot options" and a count down till it automatically boots to Ubuntu.

All ya do is when you're editing your menu.lst ```
 sudo gedit /boot/grub/menu.lst
``` is take the # (and the spaces after it) out from in front of hiddenmenu

It will look like this to start

```
## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
# hiddenmenu
```Change it to this

```
## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu
```Then just set it to boot Ubuntu automatically after like 5 seconds. 

Setting it to 0 sec. will not allow you to actually access Vista unless you change it every time you want in. Using the hidden menu will hide it, but if you hit ESC, you can get to it with no issues, without having to change it in Ubuntu just to access Vista.

Don't forget to change the bootsplash to something htat looks like Vista's booting otherwise the jig is up before they even get to the desktop.

Leo

---

### Post by Palu on 2008-04-16
Perfect! Thank you.

Good call on the splash screen! :) I'll have to make sure I find a tutorial for than and login

---

### Post by LeoSolaris on 2008-04-16
No prob!  I'll see if I can find anything, too.

Leo

I went hunting, but did not find anything supper helpful. I did discover a way to change that splash screen, but not a Vista theme. You may have to make your own.

I found this [site]("http://tuxenclave.wordpress.com/2007/11/23/ubuntu-customization-guide-v2/"). Down a little ways is where he talks about editing the three different splash screens. The second one is the one we were talking about, the "loading screen." I am not sure yet how to make a theme for it, but now I have something to tinker with in my free time. Thanks!

---

