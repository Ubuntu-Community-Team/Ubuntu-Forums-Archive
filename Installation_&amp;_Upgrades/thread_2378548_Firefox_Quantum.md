---
title: "Firefox Quantum"
date: 2017-11-24
forum: Installation &amp; Upgrades
---

### Post by riseringseeker on 2017-11-24
Firefox updated without input from me, and yes I did have, or thought I had unattended upgrades shut off.  I've seen other posts complaining of the same behavior.  That is another issue, and too late to worry about it now.

The issue I am having with are mostly trivial (though the bass guitar music that unexpectedly plays, and the delays between clicking on a link or tab and it occurring are quite annoying, and a few other items) I do have one real issue.

For years I have been using a user-agent switcher to access a vital page for my work.  Firefox never worked out of the box with that site, saying "As the specific application has yet to be tested on your platform some issues/problems may be encountered."  Firefox was not the only browser with this issue, Opera, Konqueror and others did the same.  IOW, it does not like Linux.

The user agent switcher was able to lie to the server making it "see" I was running windows, then would allow me to log on and it worked just fine.  The user-agent switcher extension doesn't work anymore - no longer supported - making the site unavailable to me on my laptop or desktop.  I need some way to access that site, and was hoping someone had an answer.

I have tried another user-agent switcher (there seem to be at least 3 available), but none of them give me what I need.  Is there an extension that will work, or another browser that has that functionality?

Open to suggestions here.

---

### Post by vasa1 on 2017-11-24
Please mention the UA switchers you've tried unsuccessfully _with Fx57_ so people don't suggest the same ones!

---

### Post by mc4man on 2017-11-24
It seems some are seeing upgrades after supposedly disabling unattended. Maybe the switch doesn't work right or they're not doing right. 
Here I just remove the unattended-upgrades package (and update-manager) so it can't possibly work..

---

### Post by riseringseeker on 2017-11-24
> **vasa1 said:**
> Please mention the UA switchers you've tried unsuccessfully _with Fx57_ so people don't suggest the same ones!

User-Agent Switcher 0.7.3.1 (the one I had been using without issue) by Chris Pederick (last updates April 2016) was disabled by the upgrade and is no longer supported.

User-Agent Switcher 0.2.0 by Linder does not have the functionality that I need.  It came up when looking for replacements for the one I had been using.  

I don't want to have to install and remove several agents before I find one that works (if it can be found), that is why I asked here.

---

### Post by riseringseeker on 2017-11-24
> **mc4man said:**
> It seems some are seeing upgrades after supposedly disabling unattended. Maybe the switch doesn't work right or they're not doing right. 
Here I just remove the unattended-upgrades package (and update-manager) so it can't possibly work..

I thought I had it shut off, but really, at this point I just need to find a replacement that works for me.  It did bother me that the upgrade seemed to also effect Firefox ESR, making it unusable as well.  I am going to try to delete and reinstall that, and see if I can get it to work.

---

### Post by riseringseeker on 2017-11-24
> **riseringseeker said:**
> I thought I had it shut off, but really, at this point I just need to find a replacement that works for me.  It did bother me that the upgrade seemed to also effect Firefox ESR, making it unusable as well.  I am going to try to delete and reinstall that, and see if I can get it to work.

Well, uninstalling ESR and reinstalling, then adding the original user-agent switcher worked, until I fired up the default mozilla.  It apparently changed the settings in ESR, disabling the UAS I wanted to use.  There is likely a way to get it to use a separate config file, just have to research it.  It's a PITA to have to change browsers for just one or two websites, but the IT department for our company is largely useless, and I am afraid if I ask for a change, it will just make it worse.  (It's happened before).

---

