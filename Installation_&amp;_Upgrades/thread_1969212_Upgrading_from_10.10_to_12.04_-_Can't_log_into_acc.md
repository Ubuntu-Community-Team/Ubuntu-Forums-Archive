---
title: "Upgrading from 10.10 to 12.04 - Can't log into account"
date: 2012-04-29
forum: Installation &amp; Upgrades
---

### Post by lazermanx2 on 2012-04-29
Hello, I upgraded one of my Ubuntu installs from 10.10 to 12.04 by upgrading from the CD to hopefully bypass a step by step upgrade. The upgrade maintained all of my data, home folder and installed apps, however my account didn't roll over and a new account was created.

I logged into the new account and did an add user with the same username and password as my old account and made it an admin. I can log into said account via the terminal and my home directory's content linked correctly, however when I try to log into the account from the login screen, it takes my password, the screen goes black and then kicks back to the login screen.

Any ideas? Are there some . files I need to nuke for gnome 3, etc?

---

### Post by oldfred on 2012-04-30
You probably are correct. 

The update installed your user files into your new user's hidden . files and the user you have reinstated does not have the new settings. Not sure best to salvage, but besure to have good backups.

I would try to just rsync new user's hidden files & folders to the old, but am not sure what that overwrites. So again a good backup.

---

