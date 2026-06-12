---
title: "Quick pre-install question"
date: 2011-03-30
forum: Installation &amp; Upgrades
---

### Post by sideburns on 2011-03-30
I'm going to be installing Ubuntu on a laptop with an empty hard drive for a friend of mine.  Normally, he uses Windows, but wants to learn something about Linux, and Ubuntu's probably the best for somebody like him.  (Not what I use myself, but I'm a Linux geek.)  AIUI, only the first account created is set up for sudo by default on Ubuntu, and if you want to let any other account have it, you have to set it up through that first account.  This would be fine for my friend, as he wants one account for himself, one for his wife and one for administration (Admin; sigh!) and only have that account have sudo access.  (Naturally, the administration account is set up first.)  If that's not the case, let me know, because I'd have no trouble editing /etc/sudors to comment out any lines giving any regular account sudo access if needed.

---

### Post by Dutch70 on 2011-03-30
I believe that all accounts have the ability to use sudo commands, it's a matter of who has the password. 
Don't hold me to that though.
If I'm wrong, see your sig! :D


Anyone have anything to add to that???
.

---

### Post by Frogs Hair on 2011-03-30
Under , System > Administration > Users and Groups there are account type settings that can be control privileges such as installing software among other things .

---

### Post by sideburns on 2011-03-30
Does that mean that when you set up a new account you can either give the new user sudo access or deny it?  If so, that's exactly what I need.

---

### Post by Frogs Hair on 2011-03-30
Yes , things like installing software and updates can be prohibited by the administrator for the user accounts.

---

### Post by sideburns on 2011-03-30
Excellent!  That's much easier than editing /etc/sudors by hand.  Thanx!

---

