---
title: "Updates are installing Ubuntu Updates (Not Xubuntu)"
date: 2014-02-24
forum: Installation &amp; Upgrades
---

### Post by austinrandy0209 on 2014-02-24
Hello,

I recently switched from Ubuntu to Xubuntu using this method: [https://sites.google.com/site/easylinuxtipsproject/alternative](https://sites.google.com/site/easylinuxtipsproject/alternative)
I have been using LTS releases and I want to start using the latest releases. When I try to update I notice it installs Ubuntu packages such as Unity.
[IMG]http://i.imgur.com/kmHQ1eP.png[/IMG]

[IMG]http://i.imgur.com/LZyISe5.png[/IMG]

How can I make it so it doesn't install these packages and installs the new Xubuntu packages?

**SOLVED:**
Just gonna do a fresh install with a non-LTS Xubuntu CD.

---

### Post by ian-weisser on 2014-02-24
1437 packages to upgrade indicates that you have a serious problem unrelated to your plans to switch Desktop Environments or to Upgrade from 12.04 to 13.10.

Do not proceed with either change until you understand why you have so many packages that need to be upgraded.

Normal weekly updates at this point in a release cycle are around 10-20 packages/week.

---

### Post by austinrandy0209 on 2014-02-24
> **ian-weisser said:**
> 1437 packages to upgrade indicates that you have a serious problem unrelated to your plans to switch Desktop Environments or to Upgrade from 12.04 to 13.10.

Do not proceed with either change until you understand why you have so many packages that need to be upgraded.

Normal weekly updates at this point in a release cycle are around 10-20 packages/week.
Oh I see. Should I try a fresh install but instead use a non LTS Xubuntu CD? I could do this cause I got all my important files on another computer and I don't have anything important on this computer. The only reason why I'm avoiding a fresh install is because I don't want to redownload my steam games again, but that's not a big problem.

---

### Post by ian-weisser on 2014-02-25
No. You should not reinstall until you understand why you have a huge number of packages to be upgraded.
Else you may simply duplicate the problem on your new system.

---

### Post by ibjsb4 on 2014-02-25
Could you have the meta package ubuntu-desktop installed?

---

