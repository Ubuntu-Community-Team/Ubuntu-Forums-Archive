---
title: "Gnucash on Gutsy"
date: 2007-10-28
forum: Installation &amp; Upgrades
---

### Post by emink on 2007-10-28
Hello all,

After upgrading to Gutsy, my GnuCash doens't work properly.
From Help - About in GnuCash, I am using GnuCash 2.2.1, r16462 build on 2007-10-03.

1. When GnuCash is activated, part of the screen is black.
2. When trying to enter a split transaction, tab won't show where the cursor is.
3. The drop-down box in accounts column doesn't show up either. I have to use entering and edition transactions from what is displayed in the status bar.
4. Calendar won't show up, but that part of the screen is shady/not visible.

Did anyone notice similar problems? All help is appreciated.

---

### Post by rbmorse on 2007-10-28
Do you have Desktop effects/Compiz active?  I see all sorts of screen redraw problems in Gnucash with the effects enabled.  Gnucash behaves normally if I turn effects off.

---

### Post by emink on 2007-10-28
Yes, I have Compiz Fusion with Avant-Window-Navigator.
GnuCash is one my most important applications that I use. If these desktop effects are causing the screen redraw problem in GnuCash, then it is a bug either in the desktop cosmetics or in GnuCash.

I had Beryl in Fiesty and there were no problems at all, including GnuCash. 
Anyone using Beryl on Gusty and GnuCash don't have the redraw problems?

---

### Post by emink on 2007-11-02
I solved this problem, and no more redraw problems with GnuCash.

I found that the problem is due to the incorrect theme settings. In my case I have Emerald theme, applied thru Emerald Theme Manager and then I tweaked some other settings thru 'Change desktop background' option (right-click on desktop and choose 'Change desktop background').
This caused conflicts and hence the redraw problem.

So, I removed Emerald Theme Manager and related themes. Then, I chose icons and window themes available at gnome-look.org, this solved the redraw problem. Installing a certain Emerald theme in a correct way also solves the problem, and I tried this one too. In both the cases, the redraw problem went away.

Hope this helps anyone with similar problem. Cheers :popcorn:

---

### Post by gregwilkins on 2007-12-26
I have the redraw problem with gnucash, but I don't have the emerald theme installed.  I'm just using the normal human theme.

Anyway, while changing theme might be a work around, I don't think it should be called a fix.  gnucash should be able to work with any theme.

---

### Post by paxmark1 on 2007-12-27
Hey,  no problems with redraws - way too slow for beryl, etc.

However I cannot get splits set up.  I see one mention of a bug, but info that there is does not do it for me.  

Really works well for currency transactions - conversions.  Any help appreciated on getting splits right.  peace mark

---

### Post by emink on 2007-12-28
I agree with gregwilkins that GnuCash should work with any theme.

---

### Post by wpshooter on 2007-12-28
> **emink said:**
> I agree with gregwilkins that GnuCash should work with any theme.

I agree that it should work under all circumstances BUT IMO GNUCASH is not much of a choice as far as accounting type programs go when you have been used to using M/S windows based programs like Quickbooks, Peachtree & others !!!

---

