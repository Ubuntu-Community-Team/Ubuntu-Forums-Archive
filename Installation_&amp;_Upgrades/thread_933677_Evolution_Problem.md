---
title: "Evolution Problem"
date: 2008-09-29
forum: Installation &amp; Upgrades
---

### Post by deakmann on 2008-09-29
Hi,

After updating from 7.10 to 8.04 I have a problem with Evolution.

Every time I start it I get the following message:-

Enter Password for default keyring to unlock

The application `evolution` (usr/bin/evolution) wants access to the default keyring, but it is locked.

My user password dosen`t work.

Any ideas whats going on?

---

### Post by fballem on 2008-10-01
> **deakmann said:**
> Hi,

After updating from 7.10 to 8.04 I have a problem with Evolution.

Every time I start it I get the following message:-

Enter Password for default keyring to unlock

The application `evolution` (usr/bin/evolution) wants access to the default keyring, but it is locked.

My user password dosen`t work.

Any ideas whats going on?

If you have changed your system password, the password for your keyring does not get updated. The password for your keyring is your old password.

To change this, select Applications > Accessories > Passwords and Encryption Keys from the menu. This will open the Passwords and Encryption Keys panel.

On the Passwords and Encryption Keys panel, select Edit > Preferences. This will open the Passwords and Encryption Settings panel.

On the Password and Encryption Settings panel, select the Login option (shown on the attached screenshot). At that point, you can then select the Change Unlock Password button. This will allow you to change the password. Set the new password to be the same as the password that you use to login to your workstation, then select OK (or Close) on each panel until you are done.

Reboot your system. When you login, try Evolution and your keyring should be already unlocked.

Hope this helps

---

### Post by deakmann on 2008-10-01
Thank you this worked

---

### Post by jurgen32 on 2008-10-21
This solution worked for me to.
But, after a few weeks the problem is back.
It started with mail-notification and now evolution has the same problem again.
I'm working with Kubuntu and followed this topic. 
First I had to install the *Passwords and Encryption Keys panel* because I could'nt find such a option in KDE. 
I've tried to change the login password in *Passwords and Encryption Keys settings* again (the first time I did'nt change the password, I just had to make a login keyring because there was only a default keyring) but off course this does'nt work because my login password never chanced.

To be short: I'm stuck with the "Enter Password for default keyring to unlock" message again.

I hope somebody can help me with this one.

Jurgen

---

