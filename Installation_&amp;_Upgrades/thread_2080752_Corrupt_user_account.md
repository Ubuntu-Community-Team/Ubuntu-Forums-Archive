---
title: "Corrupt user account"
date: 2012-11-04
forum: Installation &amp; Upgrades
---

### Post by moshuptrail on 2012-11-04
When I attempted to upgrade my 10.04 system, I ran into a space constraint and was unable to upgrade.  So I simply installed 12.04 as a new install in a different partition where there was more space.  When I created my only user account I referenced the same directory in /home where my account for the 10.04 system resided.

When I attempt to log into that account the screen goes blank momentarily and then reverts to the login screen.  I can log into the guest account but of course that has no privileges.  I'm guessing there's something in my account profile left over from 10.04 that is confusing the heck out of 12.04.  Any ideas?  Guidance?

I can't create a new account because I can't log in except in text mode and I don't know how to create a new user account in text mode.  Is there a way?

---

### Post by moshuptrail on 2012-11-05
Okay.  Here's what I did to resolve this:

1. get to login screen
2. press ctrl/alt/F2 to get prompt
3. login as self (admin account)
4. cd /home
5. rename home dir for self to self.bak
6. create empty home dir for self
7. change ownership to self:self
8. log out
9. press ctrl/alt/F7 to return to login screen
10. login and then move non-system files from the old dir (/home/self.bak) to the new, empty dir /home/self

seems to work.

---

