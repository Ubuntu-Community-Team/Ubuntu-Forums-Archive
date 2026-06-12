---
title: "Ubuntu for noobs – Video issues @ installation"
date: 2010-05-18
forum: Installation &amp; Upgrades
---

### Post by gmhead on 2010-05-18
After wrestling with Ubuntu for a few days, I finally gleaned enough information from this forum to install the 10.04 LTS OS

What I discovered in browsing through these was a lot of shorthand – as a greenbean, I like to have things spelled out for me.  Hopefully, what I figured out will help someone else.

Steps:

1.  Change the computer BIOS such that you can boot from a CD (USB might work, but I didn’t go there).
2.  When you see the “[COLOR="Red"]**boot from CD**[/COLOR]:” prompt, hold down the Shift key.  [Award BIOS; might be different for a different BIOS.]
3.  You get 2 prompts – answer Yes to both:
[INDENT][LIST]
[*][COLOR="Red"]**Load boot graphics?**[/COLOR]  (aside: can also input N for a text-based install)
[*]	[COLOR="red"]**Detect display size?**[/COLOR]
[/LIST][/INDENT]

4.  “Press any key” a couple of times, at the screen prompts
5.  You get the keyboard = little stick figure sign – press any key
6.  Select your language then
7.  Press F6 “[COLOR="red"]**Other Options**[/COLOR]”.  
8.  Use the arrow keys to move to the line with [COLOR="red"]**nomodeset**[/COLOR] on it
9.  Press the spacebar to select that option
10. Press ESC
11. From the menu, choose “[COLOR="red"]**Install Ubuntu**[/COLOR]” – you’ll see the Ubuntu splash screen with the 5 dots that go from white – red – white (etc.)
11. At this point, you’re waiting for the Install screens – 7 of them:
[INDENT][LIST]
[*]     Set language
[*]	Set timezone
[*]	Set keyboard layout (AKA map)
[*]	Prepare disk space
[*]	Enter user information, computer name
[*]	Ready to install
[*]	Install
[/LIST][/INDENT]
12. Reboot your PC – I had to take the disk out and shut it off, then turn on.
13. Press and hold the SHIFT key as your hard drive is booting – this starts up GRUB
14. Press ‘[COLOR="Red"]**e**[/COLOR]’ for edit
15. Look for the line that says “[COLOR="red"]**quiet splash**[/COLOR]” in it, and add “[COLOR="red"]**nomodeset**[/COLOR]” to that line.
16. Press CTRL-x and reboot
17. If you see the mouse pointer as you are booting up, you are home free!
:biggrin:

---

