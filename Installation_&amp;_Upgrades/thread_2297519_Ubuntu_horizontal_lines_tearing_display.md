---
title: "Ubuntu horizontal lines tearing display"
date: 2015-10-04
forum: Installation &amp; Upgrades
---

### Post by ehsan10 on 2015-10-04
Hello,

Trying to install ubunto x64-14.04 (ubuntu-14.04.1-desktop-amd64) on asus x550z from USB.

1-If I boot from live usb linux comes up but when I open a program a very bad horizontal tearing screen comes up and I can't see anything on that window! 

Graphic card is ATI Radeon - CPU AMD - 8 G RAM.

2-When I try to install before booting one sound plays and the screen is totally black!

3 days googling on posts from 2006-2014 but makes no scenes or any working solution for ATI not  Nvidia.

Same thing happening if I open terminal so I can't enter any commands too.

Please advice :icon_frown:

---

### Post by ehsan10 on 2015-10-05
It seems there is many trouble with [AMD_Catalyst]("https://wiki.archlinux.org/index.php/AMD_Catalyst")

Someone said,

[B]If you go to the "Window Manager and tweaks" section, in settings: Go to  Compositor > and check "Synchronize drawing to the vertical blank".

[/B]But I have no display on any window how can I run this from terminal?

Also another guide but I cant do that
[How to switch to Compton for beautiful tear free compositing in XFCE]("http://duncanlock.net/blog/2013/06/07/how-to-switch-to-compton-for-beautiful-tear-free-compositing-in-xfce/")

Another tip:
[B]Selecting the Tear Free Desktop mode enables VSync and even Triple   Buffering, so your GPU will use more VRAM and do additional processing.   This reduces tearing in 2D and 3D applications. However, for example,   you might notice a slight mouse/keyboard input lag while playing Games.
If  you use the open source driver instead, KMS (enabled by default)  should  detect the necessary settings for your GPU and therefore  eliminate  tearing.[/B]

How to activate KDE before login?

Another tip:
[B]
To get the grub screen hold shift during boot, if you can't get to grub  then there's something seriously wrong and you might be better off with a  fresh install.
Once you're on the grub screen try a) select normal boot but press 'e'  to edit the options and add 'nomodeset' (without the quotes), that may  get you into the GUI... or b) select recovery mode and you can get a  root shell.
nomodeset is usually a temporary thing you do for troubleshooting, there  is probably a way to set it permanently but you don't really want to,  it's just a way to get you up and running with your new driver.

[/B][Or this try]("http://ubuntuforums.org/showthread.php?t=1982642&p=11959760#post11959760")

---

### Post by ehsan10 on 2015-10-05
Found a solution finally but seems no one tried to help will not put the solution

The admin can delete the whole thread and my ID and I never come back to this dead forum again... lol

---

### Post by The Cog on 2015-10-06
I'm glad you found a solution. 
please consider posting it, so that other people who have the same problem can find it.

---

