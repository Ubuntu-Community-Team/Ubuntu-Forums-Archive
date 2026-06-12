---
title: "Location of Sylpheed config file, to allow 'security.tls.version.min' to use TLS 1.0"
date: 2022-12-02
forum: Installation &amp; Upgrades
---

### Post by robert-reg1 on 2022-12-02
Hi, I am moving from Ubuntu 18.04 to 22.04 and could not get my emails to work in Sylpheed 3.7.0 on Ubuntu 22.04, although I just transferred everything over from my old installation and the setup was identical. After a week of serious digging, I managed to get the accounts working on Thunderbird.
It turned out that my hosting company is still using TLS 1.0 and following instructions I had found online, I changed the setting in the Thunderbird config file for ‘security.tls.version.min’ from 3 to 1. Bingo. All working now. I am convinced that I have exactly the same issue in Sylpheed.
 
QUESTION: Can anybody tell me where to find the config file for Sylpheed, where I can set ‘security.tls.version.min’ to allow TLS 1.0?

Thank in advance.

---

