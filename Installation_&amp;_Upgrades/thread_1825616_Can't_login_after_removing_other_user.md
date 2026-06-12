---
title: "Can't login after removing other user"
date: 2011-08-15
forum: Installation &amp; Upgrades
---

### Post by crenvy54 on 2011-08-15
Ubuntu 10.10

I was setting up a machine for a friend using my normal username. Once the install was finished I created a new account (Admin) for the friend, logged out, logged in as the friend and deleted my own account. On the next reboot I get a message about not being able to update .ICEauthority for my own account, which I thought was deleted. Then there are messages about the configuration server failing and that Nautilus can't find the home dir for my own account, then just the desktop background, no panel, no nothing, just hangs.

Obviously, in this case deleting the account didn't clean up everything. How can I get to the login prompt for the friend's account?

TIA

---

### Post by crenvy54 on 2011-08-15
I was able to delete the user with "sudo deluser <name>" but still had some problems which I fixed by adding the user again: "sudo adduser <name>".

---

