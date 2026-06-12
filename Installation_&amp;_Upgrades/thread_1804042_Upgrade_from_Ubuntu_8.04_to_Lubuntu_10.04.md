---
title: "Upgrade from Ubuntu 8.04 to Lubuntu 10.04 ?"
date: 2011-07-14
forum: Installation &amp; Upgrades
---

### Post by hvn on 2011-07-14
Hi,

I want to upgrade an old machine with 350 MB RAM running Ubuntu 8.04. My first attempt was to upgrade to Ubuntu 10.04 LTS. Initially it seemed fine, but then it hang at the splash screen. 
Then I reinstalled 8.04, and tried to upgrade using "sudo add-apt-repository" but 8.04 doesn't know that yet.
Next attempt was to boot into the LiveCD of Lubuntu 10.04 and it hangs at a message about unknown UID.
Can somebody please tell me what I may be doing wrong?

Thanks

---

### Post by dino99 on 2011-07-14
update your sources.list (and deactivate all non genuine repo if any)

as you have a limited amount of ram you might choose lxde instead of gnome (Lubuntu-desktop instead of ubuntu-desktop, do it before upgrading)

---

### Post by hvn on 2011-07-14
> **dino99 said:**
> update your sources.list (and deactivate all non genuine repo if any)

as you have a limited amount of ram you might choose lxde instead of gnome (Lubuntu-desktop instead of ubuntu-desktop, do it before upgrading)

Hi, thank you for your answer.
First, I notice a typo I made. I didn't install Ubuntu but Xubuntu. But I think that doesn't matter much.
With what should I update my sources.list? Lxde ? If so, then I figure after the update I should find Lxde in synaptic to install ?

Thank you.

---

