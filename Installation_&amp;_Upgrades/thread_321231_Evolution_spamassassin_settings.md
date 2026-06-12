---
title: "Evolution spamassassin settings"
date: 2006-12-18
forum: Installation &amp; Upgrades
---

### Post by MegaHz on 2006-12-18
hi ubuntu gurus :D

I have just upgraded to the new alpha version of feisty but it seems that the new spamassassin with new evolution do not work as before.
I am using the fmail filter.

can you please give me the settings for it again, to cross check it?

thanks

---

### Post by MegaHz on 2006-12-19
anybody?

---

### Post by ShagzModo on 2008-04-02
I am aslo wondering how to get it working...

---

### Post by brickatius on 2008-04-18
1 Check that SpamAssassin is still installed. Open a terminal (Applications>Accessories>Terminal), give yourself root privileges by typing
sudo -s
press Enter and then your password. Type the following or Copy and Paste (case sensitive)
spamassassin -V
You should see something like 3.x.x  (in Gutsy it's 3.4.2) If not, SpamAssassiin is not installed and you should type this:
apt-get install spamassassin
to reinstall SpamAssassin
2 This is the crucial bit - there is a bug, in that 'spamd', part of the spamassassin package is not enabled by default. This is why incoming junk is not being moved to the Junk folder and it appears that SA is not working. To correct this type the following
gedit /etc/default/spamassassin
Look for the line that says ENABLED=0 and change the 0 to 1 so that it reads ENABLED=1
Click Save and that should fix the problem.
Double check that your settings in Evolution are correct by looking at Edit>Prefereces>Mail Preferences>Junk and look to see that 'Check incoming mail for junk' box is checked and 'Default junk plugin is' Spamassassin. Don't forget to mark good mail as 'Not Junk' to improve the accuracy of the filtering.

---

