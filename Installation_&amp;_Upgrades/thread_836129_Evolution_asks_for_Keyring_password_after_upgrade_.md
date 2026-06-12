---
title: "Evolution asks for Keyring password after upgrade to Hardy"
date: 2008-06-21
forum: Installation &amp; Upgrades
---

### Post by Asmilwho on 2008-06-21
Hallo,

I upgraded to Hardy from Gutsy last week and now Evolution asks for a keyring password when I start it up.

The problem is, I never set up any keyring passwords so I haven't the faintest idea what to type in.

I tried the admin password, and the password for the mailservice itself, but no success.Clicking on the "skip" button makes no difference ( I assume it's "skip", I'm translating from German)

The only way to get rid of the dialog box is to kill it via terminal. 

But I can't read any mail now ...

Thanks in advance for any tips

---

### Post by rkosby on 2008-06-24
I have the same problem.  I have yet to find a solution

---

### Post by iaculallad on 2008-06-24
Try this if it could work your case:

Press Alt+F2 and input "gksudo nautilus" (w/o double quote): This will open your nautilus window with you as root. Try to browse the ~/.gnome2/keyrings directory and make a backup copy of it (keyrings folder). (While in YOUR home directory, press Ctrl+H so you can see the hidden .gnome2 folder).

Navigate to System->Preferences->Encryption and Keyrings, on the "Password Keyrings" tab, select login and click "Remove Keyring". Close the windows and logout on your account. Login back and retry your Evolution.

---

### Post by screenn on 2008-12-05
> **iaculallad said:**
> Try this if it could work your case:

Press Alt+F2 and input "gksudo nautilus" (w/o double quote): This will open your nautilus window with you as root. Try to browse the ~/.gnome2/keyrings directory and make a backup copy of it (keyrings folder). (While in YOUR home directory, press Ctrl+H so you can see the hidden .gnome2 folder).

Navigate to System->Preferences->Encryption and Keyrings, on the "Password Keyrings" tab, select login and click "Remove Keyring". Close the windows and logout on your account. Login back and retry your Evolution.

 I had same problem. You just need to install libpam-gnome-keyring, and after next evolution password request allow auto password.

---

### Post by DJ_Peng on 2008-12-12
> **iaculallad said:**
> Try this if it could work your case:

Press Alt+F2 and input "gksudo nautilus" (w/o double quote): This will open your nautilus window with you as root. Try to browse the ~/.gnome2/keyrings directory and make a backup copy of it (keyrings folder). (While in YOUR home directory, press Ctrl+H so you can see the hidden .gnome2 folder).

Navigate to System->Preferences->Encryption and Keyrings, on the "Password Keyrings" tab, select login and click "Remove Keyring". Close the windows and logout on your account. Login back and retry your Evolution.
I tried that but my E&K window (in Ubuntu Intrepid) doesn't have that tab (see keyring). Do you have any suggestions?

> **screenn said:**
> I had same problem. You just need to install libpam-gnome-keyring, and after next evolution password request allow auto password.
I already have that installed, and I still get asked to log in every time I fire up Evo (after restarting/logging in, additional launches of Evo in that session don't prompt me for my pwd). Any other ideas?

I'm running Ubuntu 8.10 (32 bit) with all of the latest updates from intrepid-proposed.

---

### Post by pjalegria on 2009-01-22
Hi

I have the same problem, after enable autologin everytime i open Evolution it ask me for a key (password)...:(

I think is beter to disable again autologin

---

