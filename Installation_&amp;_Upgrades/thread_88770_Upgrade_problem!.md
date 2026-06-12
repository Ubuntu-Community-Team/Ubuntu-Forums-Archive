---
title: "Upgrade problem!"
date: 2005-11-11
forum: Installation &amp; Upgrades
---

### Post by aum11 on 2005-11-11
Today I began the upgrade path from Hoary to Breezy, using the synaptic method.  It was about a 750 mB download which was successful.  The problem has come with the installation phase.  

At about 80% of the way through the installation, everything stopped.  Not even the cursor could move.  I have no idea why.  No messages, no nothing!  So, I held my breath and rebooted.

It reboots as Breezy.  The boot goes fine, except that there there is only terminal mode.  There is no GUI.  It asks for my logon and password, and then puts me in terminal mode.

How can I complete the upgrade?

I am very much a newbie and really need some wisdom here.

PS this message coming from the XP partition.

---

### Post by darth_vector on 2005-11-11
sudo apt-get dist-upgrade

will finish the installation, i think. good luck :)

---

### Post by aum11 on 2005-11-11
Well done Darth-Vector...may the force be with You!!!!!!!!

I am up and running now.  This message is coming from Breezy.

However, there are a series of error messages for mailx, mutt, isb-core, lsb-graphics, lsb-cxx, lsb ......stating that they all have a problem and are being left unconfigured.

What is this all about?

---

### Post by aum11 on 2005-11-11
I found that others are having this same problem and that it was overcome by uninstalling postfix.
It also worked for me.

---

### Post by darth_vector on 2005-11-12
[QUOTE=aum11]Well done Darth-Vector...may the force be with You!!!!!!!!

I am up and running now.  This message is coming from Breezy.[/QUOTE]

no worries, and good work :)

[QUOTE=aum11]However, there are a series of error messages for mailx, mutt, isb-core, lsb-graphics, lsb-cxx, lsb ......stating that they all have a problem and are being left unconfigured.

What is this all about?[/QUOTE]

sorry mate, cant help with this one...

---

### Post by Zerocool10482 on 2005-11-12
Hi, I tried that and it didn't work. I"m sorry to ask but can you help me too. I did that command but it didn't work so is there another way to start my gnome manager.

---

