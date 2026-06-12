---
title: "boot splash logo glitched out! (disappeared after using startupmanager))"
date: 2010-05-19
forum: Installation &amp; Upgrades
---

### Post by gnomeout on 2010-05-19
Ok people. Here is a relatively small issue compared to my usual life ending bugs. 

After a clean install of Lucid, I found my boot splash logo(the ubuntu logo surrounded by purple) was at a terrible resolution and appeared all pixelated. I gathered this was a normal issue for anyone using proprietary drivers thanks to the new splash screen manager that Lucid uses. 

However I still wanted to fix this because it was irritating me immensely. So I found a thread where someone said they used the program "startupmanager" to fix this issue. However this must have been an out of date post. Because when I installed and went to use startupmanager, I lost my boot splash for good. 

After running startup manager and trying to change the boot splash resolution and restarting, my boot splash is now ruined. Heres the weird part though, its still there! The screen is still purple, and I can see what just looks like a bar of static on the top, but judging by the way it gently flickers, I am assuming it is the loading image(with the gently flickering loading dots). So the image is there, it is just ruined beyond belief thanks to startupmanager trying to fix the resolution. This would also just be mildly inconvenient, but unfortunately its even worse, because my text output screen is also ruined like that too, so i cant see critical output if there is any.

NOTE!!!! This is most likely not an issue with the image itself or its existence, but an issue with rendering it in the correct resolution during boot. 

HELP?!!

---

### Post by gnomeout on 2010-05-26
bump :(

---

### Post by BoogeyOfTheMan on 2010-05-29
Bump

Same problem here too.

---

### Post by Dynaflow on 2010-06-01
Exactly the same problem.  It seems to have been startupmanager that scotched it.

---

### Post by marciomj on 2010-06-01
Same problem here.

The funny part of history: when I boot via a Live-USB, the splash works fine.

I'm using 10.04 (64 bits).

---

### Post by BoogeyOfTheMan on 2010-06-02
I get it on shutdown as well. 

I dont know why, but that was always one of my favorite things about trying a new OS, the boot-up and shutdown screens.

---

### Post by michaelqangeles on 2010-06-03
Polite bump lol. Same problem this sucks :/

---

### Post by Jonathan Moerman on 2010-06-03
I got the same thing after using  startup-manager but i restored it by 3 steps:

1 I fully deinstalled startup-manager.

2 I fully deinstalled GRUB. (Must be a FULL (no configs left))

3 I reinstalled GRUB. And rebooted.

It worked by me :smile:, I hope this helps....

(Sorry for my bad English I'm not a native speaker.)

---

### Post by gnomeout on 2010-06-05
Hey everyone! thanks for all pitching in.

I have ultimately just reinstalled(since I had to anyway) and now I am living with the less ideal image resolution rather than trying to fix it. 

A few things I have noticed:
1: startupmanager is just definitely not compatible with the new boot splash logo manager, its a new program that handles boot splashes on Lucid, and startupmanager hasnt been updated for it. So that's that. 

2: the reason why the usb works is because it is not using at all the same data to boot, everything is coming from the usb rather than the hard drive. Unless you have installed and used startupmanager on your usb OS. 

3: about the image resolution issue(before startupmanager issues) I read on other threads that the new splash manager does not like to support proprietary graphics drivers, which is why booting from CD gives a pretty resolution. Then once it is installed it will only keep the good resolution until you enable the restricted graphics drivers(does not matter which brand of card you have, as long as its proprietary)


Hope this helps inform some of you, sorry I could never find a solution for the startupmanager completely ruining the boot logo..... thats just a bummer.

EDIT: Just saw your post Jonathan, wish I saw it 2 weeks ago :( I hope it works for others.

---

### Post by Jonathan Moerman on 2011-03-30
If you want to fix the resolution this might help (worked for me :)): [http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/](http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/)

---

