---
title: "server, post login System information"
date: 2010-04-04
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by boondocks on 2010-04-04
Every time I log into this new **ubuntu-10.04-beta1-[COLOR="Red"]server[/COLOR]-amd64** it shows:
```
Linux server1 2.6.32-19-server #28-Ubuntu SMP Thu Apr 1 11:46:36 UTC 2010 x86_64 GNU/Linux
Ubuntu 10.04 (lucid)

Welcome to the Ubuntu Server!
 * Documentation:  http://www.ubuntu.com/server/doc

  System information as of Sun Apr  4 17:20:46 PDT 2010

  System load:  0.0                Swap usage:  0%     Users logged in: 0
  Usage of /:   0.8% of 144.26GB   Temperature: 62 C
  Memory usage: 13%                Processes:   92

  Graph this data and manage this system at https://landscape.canonical.com/

Checking for a new ubuntu release
No new release found

For documentation and useful resources, please visit:
 * http://ubuntu.com/server/doc

  System information as of Sat Apr  3 15:36:52 PDT 2010

  System load:  0.05               Swap usage:  0%     Users logged in: 1
  Usage of /:   0.7% of 144.26GB   Temperature: 63 C
  Memory usage: 6%                 Processes:   109

  Graph this data and manage this system at https://landscape.canonical.com/

132 packages can be updated.
0 updates are security updates.

Checking for a new ubuntu release
No new release found
```

Why does it display this System information twice?

---

### Post by boondocks on 2010-04-05
Also, it showed:
132 packages can be updated.  (now 133)
0 updates are security updates.

So I did:
sudo aptitude -q clean 
sudo aptitude -q update 
sudo aptitude -q safe-upgrade 

I log out and log back in and still get the same message:
133 packages can be updated.
0 updates are security updates.

---

