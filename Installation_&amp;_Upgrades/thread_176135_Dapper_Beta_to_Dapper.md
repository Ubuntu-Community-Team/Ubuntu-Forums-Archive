---
title: "Dapper Beta to Dapper"
date: 2006-05-14
forum: Installation &amp; Upgrades
---

### Post by Nonno Bassotto on 2006-05-14
I'm currently using Ubuntu Breezy, but I'd really like to try out Dapper. Currently Dapper is in his beta stage. Suppose I dist-upgrade now and get this beta. What will I have to do on 6/1?
A) Dist-upgrade another time
B) Nothing, just regular updates
C) Someething else

Moreover, is Dapper working well for the basic things? I mean, repositories are working (also plf ones or something similar), crashes are rare, or you have to trick something to have a working system?
Thank you

EDIT: I hope the question is a little more clear now.

---

### Post by Sef on 2006-05-14
To upgrade to Dapper, you will have to dist-upgrade.

It is due to be stable 1 June 2006.

Overall Dapper is very stable.

---

### Post by dabear on 2006-05-14
> **Nonno Bassotto]I'm currently using Ubuntu Breezy, but I'd really like to try out Dapper. Currently Dapper is in his beta stage. When the definitive edition comes out, will I have to dist-upgrade? 
[/QUOTE]
You would have two options:
 1) replace all occurences of "breezy" to "dapper" in you /etc/apt/souces.list and do a sudo apt-get dist-upgrade

2) Use update-manager. A new version of update-manager should have hit the breezy repos. This version will notify you when a new release is available. It will also update your system.
You can make the update-manager check for beta-releases by starting t with the "-d" switch: "sudo update-manager -d"

> 
Or maybe there will be a seamless transition, just some package updates? Or something intermediate? It would be annoying to dist-upgrade now and again a month later.

There a more than just a few packages to update said:**
> Moreover, is Dapper working well for the basic things? I mean, repositories are working (also plf ones or something similar), crashes are rare, or you have to trick something to have a working system?
Thank you
Work pretty well, if you ask me. Repos are working and I am currently using the breezy PLF repos to get extra stuff. Dapper haven't crashed on me since flight 2 or something (we are on Flight 7 now)

---

### Post by Nonno Bassotto on 2006-05-14
Thank you for your answers, but I realize now that my question was not clear at all. The point is: if I dist-upgrade now to Dapper beta, will I have to dist-upgrade again from Dapper beta to Dapper definitive?
Sorry for not being clear.

---

### Post by dabear on 2006-05-14
[QUOTE=Nonno Bassotto]Thank you for your answers, but I realize now that my question was not clear at all. The point is: if I dist-upgrade now to Dapper beta, will I have to dist-upgrade again from Dapper beta to Dapper definitive?
Sorry for not being clear.[/QUOTE]
Well, I always dist-upgrade, as dist-upgrade is better to sort out dependencies than 'update'. If what you really are asking; is if you will have to update your system to get the newest version, then the answer would be a clear 'yes'.

---

