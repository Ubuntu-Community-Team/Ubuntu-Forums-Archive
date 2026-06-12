---
title: "Upstart's status after updating from Dapper to Feisty"
date: 2007-08-02
forum: Installation &amp; Upgrades
---

### Post by hyperair on 2007-08-02
I began using Ubuntu since Dapper Drake's release. Then I upgraded to Edgy when it came out and Feisty when it came out. However, I don't think I really noticed any difference in boot up speed. Could it be that it's not utilizing the full capabilities of Upstart? A friend of mine told me to run this command: ```
dpkg --list | grep upstart
```
Here's the output:
```
ii  upstart                                    0.3.8-1                                event-based init daemon
ii  upstart-compat-sysv                        0.3.8-1                                compatibility for System-V-like init
ii  upstart-logd                               0.3.8-1                                boot logging daemon
```

Supposing my system really isn't using the full capabilities of Upstart, how can I make it do so? Is it possible without a clean install of Feisty?

By the way, my Windows XP Professional SP2 in Virtualbox boots up faster than Ubuntu. So does Vista on the same computer (dual boot)

---

