---
title: "Still have upgrade problems"
date: 2006-11-09
forum: Installation &amp; Upgrades
---

### Post by Somenoob on 2006-11-09
I know it's easy to backup personal data but if i would delete my current Dapper partition i would have to install a high number of programs.

In the middle of the upgrade i recieve this error message

```
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/source/Sources.gz Sub-process gzip returned an error code (1)
```

How do i solve this? I really want Edgy, please help.

---

### Post by Jussi Kukkonen on 2006-11-09
This might not be related to your problem, but are you upgrading to Edgy? If you are, there's probably a line still referencing Dapper in your *sources.list*... Better check that.

The actual problem is probably just a repository or a network connection  problem. Try again in a couple of hours.

---

### Post by Somenoob on 2006-11-09
I just replaced "dapper" with "edgy" in /etc/apt/sources.list and saved. And then i ran ```
gksu "update-manager -c"

``` it stated "fail to fetch" on 2 adresses. And the dist-upgrade command is just as useless right now.

---

