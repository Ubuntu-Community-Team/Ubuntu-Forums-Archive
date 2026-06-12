---
title: "Ubuntu 11.04 Firefox problem"
date: 2011-04-28
forum: Installation &amp; Upgrades
---

### Post by rashby3 on 2011-04-28
Just upgraded to 11.04.

Started Firefox. Noticed it took up the whole screen. Could not get to the ubuntu launch "tray" or sidebar--whatever it is called (on the left edge of the desktop). Could not figure out a way to reduce or resize or even quit Firefox. Then my touch pad mouse pointer froze up and could not get it moving again. Had to restart.

Same things happened second time I tried it, after restart.

I DO NOT have this problem with Google Chrome browser, at least not so far.

Is there some way I can get Firefox to work with 11.04?

Thanks.

---

### Post by ssherwood on 2011-04-28
> [COLOR=Red]Just upgraded to 11.04.

Started Firefox. Noticed it took up the whole screen. Could not get to  the ubuntu launch "tray" or sidebar--whatever it is called (on the left  edge of the desktop). Could not figure out a way to reduce or resize or  even quit Firefox. Then my touch pad mouse pointer froze up and could  not get it moving again. Had to restart.

Same things happened second time I tried it, after restart.

I DO NOT have this problem with Google Chrome browser, at least not so far.

Is there some way I can get Firefox to work with 11.04?

Thanks. [/COLOR]    
Hiya rashby3,

I had a similar issue on the beta 2 version, and to resolve the Firefox issue I had to press F11 until I could see the restore icon in the window control frame, then I closed the browser and started Firefox again and the problem was resolved.

The unity bar issue was same as well, I scrolled my mouse to the left side of the screen until it appeared but once my mouse move it disappeared. This is a feature which is built into unity to free up the desktop for window sessions.

Heres a link for the Unity Bar [http://ubuntuforums.org/showthread.php?t=1741293](http://ubuntuforums.org/showthread.php?t=1741293)


Stephen ->ssherwood

---

### Post by rashby3 on 2011-04-28
Thanks very much, ssherwood. Your suggestions fixed my problems.

---

### Post by ssherwood on 2011-04-28
No problem, glad to help :)

ssherwood

---

### Post by joeweaver on 2011-05-01
This may be a slightly different problem, and I don't know if anyone else is experiencing it, but after upgrading from 10.10 to 11.04, I cannot resize the Firefox window and I don't have any menus.  Is that the same problem that rashby had?
Chromium works fine, but Firefox is my browser of choice.  

I have a large high-resolution monitor and I like to see multiple windows at the same time.  I'm not really believing that the full-screen effect of Firefox is a new feature that was meant to be implemented.  Resizing windows is important to me!  I'm curious to know whether anyone else has experienced this problem.  I have tried re-installing compiz, re-installing the ubuntu desktop, and re-installing firefox.  If I can't figure it out, then I guess Chromium is my new favorite browser on Ubuntu.  No big deal, but it will continue to bother me.

---

### Post by ssherwood on 2011-05-01
hi joeweaver,

how did you upgrade to 11.04, as an upgrade or clean install as this could be the issue

Stephen, SSHERWOOD

---

### Post by ssherwood on 2011-05-01
Heres a quick guide, I will include images and more detail if needed or requested.

1/. If the browser is in full screen mode, press f11.
2/. Press and hold ctrl, alt and del to bring up the shutdown menu. and exit this.
3/. Whilst the task-bar for the desktop is shown hover over the view menu which will be for Firefox and check that the F11 Full screen mode is disabled.
4/. Then hover over the file menu and click exit and click all prompts, e.g. two or more tabs, etc.
5/. Right click on the Firefox icon in unity and the click either Firefox or new window.

This should now open Firefox normally with out full-screen and includes the menu integrated into the task-bar. 

> [COLOR=Red]***_**NOTE** THIS METHOD ONLY WORKS WHILST USING THE DEFAULT UBUNTU SESSION - UNITY!!_***[/COLOR]!

Thanks Stephen, (SSHERWOOD)

---

### Post by joeweaver on 2011-05-01
Stephen--

Thanks for your help.  I wasn't in full-screen mode at all, but your tip to look for the view menu did help.  The problem was that the menu appeared in the top bar, but was barely visible because it was black text on a charcoal gray bar.  I swear it is nearly invisible.  I was able to then see the icons to minimize and re-size the window in the top bar also.  I'm not a fan of that interface change, as I would prefer if the window sizing features were kept on either the left side or the right, not on both.  Non-maximized windows have it on the right, but once you're maximized, it appears on that top menu bar on the left, right next to the Ubuntu logo.

Anyhow, thank you very much for the prompt help!  This is the first time I ever posted something on the forums, despite using Ubuntu for about two years.

Joe

---

### Post by ssherwood on 2011-05-01
Joe,

Its no problem, just glad to help you.

Stephen

---

### Post by ssherwood on 2011-05-02
[CENTER]**_*[SIZE=3]Ubuntu 11.04 Unity Session Firefox Guide[/SIZE]*_**
[LEFT][SIZE=1]
Below I have created a quick guide to help anyone with this issue, to overcome it.

1/.  [COLOR=DimGray][I](This is dependent on if the browser is in full screen or partial full screen and if you close the browser whilst in full screen)[COLOR=Red]
If the browser is in full screen[COLOR=Navy] (FX-Browser_fscrn.png)[/COLOR], you will need to press **F11 **to bring this in to a partial screen mode [/COLOR][/I][/COLOR][/SIZE][SIZE=1][COLOR=DimGray]*[COLOR=Red][COLOR=Navy](FX-Browser_fscrndis.png)[/COLOR][/COLOR]*[/COLOR][/SIZE][SIZE=1][COLOR=DimGray][I][COLOR=Red].

[COLOR=Black]2/.[/COLOR] Next press and hold **Ctrl, Alt, Del **until the shutdown menu shows [COLOR=Navy](FX-Ctrl-Alt-Del.png)[/COLOR]. Do not shutdown your system just cancel the window, which will provide the menus for Firefox in the task-bar [COLOR=Navy](FX-menu.png)[/COLOR].

[COLOR=Black]3/.[/COLOR] Now open the **File** menu and click **Exit**. once Firefox has closed go to the Firefox icon and RIGHT click on the icon and click either **Open a new Window **or **Firefox Web Browser**, and the browser should open in its normal fashion [COLOR=Navy](FX-New.png)[/COLOR].


[COLOR=Black]Stephen[/COLOR]
[/COLOR][/I][/COLOR][/SIZE][/LEFT]
[/CENTER]

---

### Post by th3_survivor on 2011-05-03
Hi, I've got another problem with firefox. With Ubuntu 10.04 there was no problem, but I installed Ubuntu 11.04 and now have problem with gfx.color_management.  When the value is 2 (by default) some of the images are darker, by value 0 images are better, but not good enough like in chromium or opera. Any idea how to fix it?

---

### Post by ssherwood on 2011-05-03
Sorry, I can help with that, I have only posted what I know from my experiences so far, but with me I haven't had an issue with the colour on images etc.

Again, sorry I can't be much help with this.

Stephen

---

### Post by th3_survivor on 2011-05-03
No problem :) It's strange that this happens only with some photos in facebook and when I press F5 and the photoviewer is disabled, the picture looks fine.

---

