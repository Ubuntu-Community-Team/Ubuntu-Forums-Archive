---
title: "Reassigning home folders to users after reinstall"
date: 2008-11-19
forum: Installation &amp; Upgrades
---

### Post by fancyl on 2008-11-19
I have been having several problems after upgrading to Ibex, and after much deliberation, I decided to revert back to Heron. Things are running smoothly again, but I'm having a problem with other users. I have my home folder in a separate partition, and when I re-created my account during setup, it automatically recognized my previous home folder. But when I try to add other users, giving them the same User ID as their previous account, it won't allow me to add them.

How can I add my previous users to my new install?

---

### Post by taurus on 2008-11-19
The first user of the system would get a UID of 1000.  The next one should be 1001 so make sure when you create the second user, you use the same name as the original user with UID of 1001.  You can look at /home to see those UID numbers.

Maybe that is the problem or maybe it's something else entirely different.

---

### Post by fancyl on 2008-11-20
That's the problem. It won't let me assign the same user name and permissions. It tells me that the home folder already exists. How can I get my coworkers' stuff back? Is it possible to just copy it all over to their new folders? Would that screw things up? And if it's safe to do, what would be the teminal command to do it while keeping permissions. In the past, I've resorted to using nautilus to do stuff like that but all the permissions get changed to root.

Any advice?

---

### Post by taurus on 2008-11-20
Do your co-workers want to keep the same username?  How many accounts are there on your machine? 

Yes, you can copy their stuff from the old account to their new account.  Of course, you can always use the chown command to change the ownership of those files back to the appropriate owner.

---

### Post by fancyl on 2008-11-20
Yeah. They want to keep the same username and password. There are 4 accounts in total.

can you help me with the teminal command for chown? If the username is "mary", what would I type? I'm learning terminal, but it's a slow process.

Thanks.

---

