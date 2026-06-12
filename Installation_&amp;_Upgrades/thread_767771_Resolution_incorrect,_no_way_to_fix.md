---
title: "Resolution incorrect, no way to fix"
date: 2008-04-25
forum: Installation &amp; Upgrades
---

### Post by mixmastamyk on 2008-04-25
I've got display/monitor issues :(  ... New clean install with Hardy Heron.

My monitor is 1920x1200. Screen resolution control panel only allows up to 1280x800 !!

Half my screen going to waste. Gutsy/Rhel worked fine.

Opened up the xorg.conf ... nothing much in there ... WTF??

No way to fix this and no way to set it manually ... what do I do to fix it? There is an ATI video card in this box.

---

### Post by overdrank on 2008-04-25
> **mixmastamyk said:**
> I've got display/monitor issues :(  ... New clean install with Hardy Heron.

My monitor is 1920x1200. Screen resolution control panel only allows up to 1280x800 !!

Half my screen going to waste. Gutsy/Rhel worked fine.

Opened up the xorg.conf ... nothing much in there ... WTF??

No way to fix this and no way to set it manually ... what do I do to fix it? There is an ATI video card in this box.

Hi and welcome, you can try and use screens and graphics to adjust your resolution. It is located under applications, other. If not there then you will need to edit your menus. Also have you installed your drivers for the ATI card and what is the model?

---

### Post by Shadowfire on 2008-04-25
As Overdrank has pointed out you could go under SYSTEM> Preferences>Screen Resolution and try to fix it through the GUI wizard called Monitor Resolution Settings.  If that doesn't work for some strange reason - like I have proven sometimes it doesn't, then you would have to look in your xorg.conf and fix it manually there.

If you find that will not change it in the GUI wizard, then to be fair to others trying to help you, could you please paste your xorg.conf in a post, so we can look at it and try to help you.  It's kinda hard to fix thing sometimes if you can not see them first.  So a post of your current xorg.conf would be quite helpful indeed!  You can find it under /etc/X11.  

In terminal type one of the following:

gedit /etc/X11/xorg.conf        <---to look

sudo gedit /etc/X11/xorg.conf   <---to edit

copy and paste the results in a post.

Thanks,

Shadowfire

---

