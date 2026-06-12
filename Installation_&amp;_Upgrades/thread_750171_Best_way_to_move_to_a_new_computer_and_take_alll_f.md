---
title: "Best way to move to a new computer and take alll files/settings?"
date: 2008-04-09
forum: Installation &amp; Upgrades
---

### Post by thikrat on 2008-04-09
Hello,

I have searched far and wide but have not found an answer to my problem.

I have been using Linux, Ubuntu specifically for about 3 years now and its time to move to a new laptop.  I have every app imaginable installed on my old laptop which is running Hardy.  I installed Ubuntu 64-bit on my new laptop (hardy as well) and was looking at options on how to move all my data over.  

I saw a program called conduit which seems like it will sync some stuff but what about Evolution/thunderbird e-mails PGP keys and all that?

So this is my "idea" someone please shoot it down if it deserves it.  If I have the same version of an app on both laptops can I just copy the .thunderbird or .evolution or .exaile or whatever over to my new home directory on the new laptop?  I even kept the username the same as to cut down on potential issues.

Any ideas please let me know!

Thanks

---

### Post by pytheas22 on 2008-04-09
If you replace the entire home directory on your new computer with the one from your old computer, everything should be transferred.  I've never done that, but I have kept the same /home directory through half a dozen installs of Ubuntu (I keep /home on its own partition to make things easier, but I don't see why it wouldn't just work to also copy the directory), and my personal settings get preserved with no problems.  The only issue is that you might get some errors about improper ownership or permissions; if these come up, do a Google search and the solution should be obvious.

---

### Post by Belak on 2008-04-09
In theory that copying idea should work.

---

### Post by thikrat on 2008-04-09
I have done a lot of upgrades as well, but I have never copied my home directory to an entirely different system.  Thats what I'm worried about.  It seems odd that there is no tool to do this kind of thing as there is a tool to import settings in from Windows.  I understand there is more need for that, but the thought of such a utility is not bad.

Thanks for the help to all

---

### Post by atomkarinca on 2008-04-09
Check out [remastersys]("http://www.remastersys.klikit.org/").

---

### Post by thikrat on 2008-04-30
hey guys,

I kind of got this to work, on everything except evolution, I just did an rsync of certain dirs from my home on my old laptop to my new laptop.  So for example, 

.tomboy 
.purple
.thunderbird

all moved over no problem, ssh keys i had to move manually as well as PGP keys.  Evolution has been a nightmare, see my other post for details.

[http://ubuntuforums.org/showthread.php?t=775636](http://ubuntuforums.org/showthread.php?t=775636)

---

