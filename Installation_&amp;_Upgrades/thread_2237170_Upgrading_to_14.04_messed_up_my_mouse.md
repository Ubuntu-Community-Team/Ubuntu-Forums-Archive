---
title: "Upgrading to 14.04 messed up my mouse"
date: 2014-07-31
forum: Installation &amp; Upgrades
---

### Post by Sunsawe on 2014-07-31
Hi everyone,

I was using uBuntu 12.10 for a while and decided to upgrade. The system upgraded first to 13.10 without any issue for the mouse. Then, one upgrade session more and I was up to date with 14.04 running.
The problem is now that my mouse is pretty messed up. I use a mouse which has 4 buttons plus a wheel, so a total of 7 virtual buttons. Basically, now, the right click is detected as being a wheelclick. xev returns that they have the same identifier : 2. So my right click has been moved to my backward  navigation button (id 3) which has been it self move to the forward button (id 8).
So the situation is like this:

[table="width: 500, class: full_border"]
[tr]
	[td]Button Name[/td]
	[td]Button Usual Function[/td]
	[td]Button ID with xev[/td]
	[td]Button current function[/td]
[/tr]
[tr]
	[td]Button 1[/td]
	[td]left/main click[/td]
	[td]1[/td]
	[td]left/main click[/td]
[/tr]
[tr]
	[td]Wheel click (2)[/td]
	[td]In browser: active scrolling function to just move the mouse to scroll.[/td]
	[td]2[/td]
	[td]In file explorer: open directories in new tab and open files directly like a double click. In browser: open links in new tab if on link otherwise, nothing.[/td]
[/tr]
[tr]
	[td]Button 3[/td]
	[td]Right click[/td]
	[td]2[/td]
	[td]same as wheel click[/td]
[/tr]
[tr]
	[td]Button 4[/td]
	[td]Previous/Backward navigation[/td]
	[td]3[/td]
	[td]Right click[/td]
[/tr]
[tr]
	[td]Button 5 (scroll up)[/td]
	[td]scroll up[/td]
	[td]4[/td]
	[td]scroll up[/td]
[/tr]
[tr]
	[td]Button 6 (scroll down)[/td]
	[td]scroll down[/td]
	[td]5[/td]
	[td]scroll down[/td]
[/tr]
[tr]
	[td]Button 7[/td]
	[td]forward navigation[/td]
	[td]8[/td]
	[td]backward navigation[/td]
[/tr]
[/table]

Is there any way to fix this? I have search a bit a found some xorg.conf tricks, but this doesn't seem to work in my case. Would it be related to the fact that 2 buttons are now detected with the same ID and one of the button has an ID out of range?

Thank you all

---

