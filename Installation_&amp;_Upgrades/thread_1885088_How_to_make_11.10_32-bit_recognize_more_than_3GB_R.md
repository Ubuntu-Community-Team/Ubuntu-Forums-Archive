---
title: "How to make 11.10 32-bit recognize more than 3GB RAM"
date: 2011-11-22
forum: Installation &amp; Upgrades
---

### Post by Tornikee on 2011-11-22
As I discovered by doing search on this, it is a known issue that 32-bit Ubuntu doesn't recognize more than 3GB of RAM installed. I tried going around this by installing Physical Address Extension as explained [here]("http://www.cyberciti.biz/faq/ubuntu-linux-4gb-ram-limitation-solution/"), although couldn't successfuly solve the issue. Is there any other way of doing this, or is installing 64-bit version my only solution?

---

### Post by An Sanct on 2011-11-22
Well, PAE is the solution for addressing more than 3G of ram in a 32bit OS. The solution you provided is okay.

PS. Since Precise Pangolin (12.04) PAE will be set as default for the 32bit version too.

---

### Post by sudodus on 2011-11-22
> **An Sanct said:**
> Well, PAE is the solution for addressing more than 3G of ram in a 32bit OS. The solution you provided is okay.

PS. Since Precise Pangolin (12.04) PAE will be set as default for the 32bit version too.
Interesting for med too :-)

---

### Post by Tornikee on 2011-11-22
Thanks for the info, will give it another go.

---

