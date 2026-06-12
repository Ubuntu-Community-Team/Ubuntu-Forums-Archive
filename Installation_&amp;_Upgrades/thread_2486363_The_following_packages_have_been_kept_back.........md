---
title: "The following packages have been kept back........why?"
date: 2023-04-27
forum: Installation &amp; Upgrades
---

### Post by DigiAngel on 2023-04-27
I just updated an ubuntu 20.04 AND an 22.04.  20.04 updated everything with apt, no issues.  22.04, kept back tzdata....same package that was updated on 20.04.  Why?  Why does 22 almost always keep back packages on updates?

---

### Post by ian-weisser on 2023-04-27
See [https://askubuntu.com/questions/1431940/what-are-phased-updates-and-why-does-ubuntu-use-them](https://askubuntu.com/questions/1431940/what-are-phased-updates-and-why-does-ubuntu-use-them)

---

### Post by ubfan1 on 2023-04-27
Usually you can just ignore the phased packages held back, and in a few days, they will show up.  Sometimes thought, it may take weeks!  Still, if an upgrade phases some video driver dependencies, you may suddenly be left without your proprietary video drivers when the module rebuild fails. You can force the upgrades, without tagging them "manual" with:
sudo apt -o APT::Get::Always-Include-Phased-Updates=true upgrade

(add --dry-run if you just want to check)

---

### Post by DigiAngel on 2023-04-27
Appreciate the answers all thank you.

---

### Post by mIk3_08 on 2023-04-27
> **DigiAngel said:**
> Appreciate the answers all thank you.
if your query has been answered. You can mark this thread as solve.
On how to mark this thread as solve,
Please Click the "Solve thread" link below. Regards and cheers.

---

### Post by BBQdave on 2023-04-28
> **ian-weisser said:**
> See [https://askubuntu.com/questions/1431940/what-are-phased-updates-and-why-does-ubuntu-use-them](https://askubuntu.com/questions/1431940/what-are-phased-updates-and-why-does-ubuntu-use-them)

Thank you for this information. Good to understand the update process and "packages held back" message :)

---

