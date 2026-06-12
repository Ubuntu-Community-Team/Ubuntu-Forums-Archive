---
title: "Kubuntu 10.04 clobbers firefox installation with gnucash log"
date: 2010-08-06
forum: Installation &amp; Upgrades
---

### Post by JimGvo on 2010-08-06
I installed a new copy of Kubuntu 10.04 on a friend's system.  I also installed gnucash from the repository.  He said he can't run firefox from either the icon on the panel nor from the applications->internet menu.  I looked at the properties for each and instead of the expeced firefox %u I saw the log file for gnucash.  Something like /home/user/gnucash.log but that wasn't the exact path, I didn't write it down.  I changed it back to firefox %u and the next day he called and said firefox wasn't working.  I asked him to look at the properties and sure enough the log entry was back.  

I've been looking on my system which is also a 10.04 install to see if I could figure out where that firefox %u is stored so I could possibly mark it as read only and maybe get gnucash to complain when it tried to rewrite that location.  I searched my entire home directory tree for that string to no avail.  

So if anyone can help either tell me why gnucash is behaving wierdly or tell me where the firefox properties is set I'd appreciate it.

Thanks,
Jim.

---

