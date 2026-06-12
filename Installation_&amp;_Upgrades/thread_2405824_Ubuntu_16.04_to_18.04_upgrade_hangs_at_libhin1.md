---
title: "Ubuntu 16.04 to 18.04 upgrade hangs at libhin1"
date: 2018-11-11
forum: Installation &amp; Upgrades
---

### Post by waltwhitman on 2018-11-11
I am on a binge upgrade of servers from Ubuntu 16.04 to 18.04. Some of the upgrades are going fine and some of the servers the upgrade hangs [at this point][1]:


    Preparing to unpack .../libnih1_1.0.3-6ubuntu2_amd64.deb ...
    Unpacking libnih1:amd64 (1.0.3-6ubuntu2) over (1.0.3-4.3ubuntu1) ...
    Processing triggers for libc-bin (2.27-3ubuntu1) ...
    Setting up libnih1:amd64 (1.0.3-6ubuntu2) ...


This is a known pitfall and the work around is [found here][2].


I am interested in knowing is why is this happening?


PS: These are all systems which are just been upgraded to 16.04 from 14.04 and are almost close to bare Ubuntu.


  [1]: [https://i.stack.imgur.com/xN8RZ.png](https://i.stack.imgur.com/xN8RZ.png)
  [2]: [https://wildwolf.name/pitfalls-when-upgrading-ubuntu-xenial-to-bionic/](https://wildwolf.name/pitfalls-when-upgrading-ubuntu-xenial-to-bionic/)

---

