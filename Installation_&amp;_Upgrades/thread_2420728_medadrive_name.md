---
title: "/meda/drive_name???"
date: 2019-06-10
forum: Installation &amp; Upgrades
---

### Post by DarkDancer on 2019-06-10
When setting up mount points for drives in Ubuntu as of 10.04 do we still use /media or do we use /dev or something else?

---

### Post by yetimon_64 on 2019-06-10
This [[COLOR=#0000ff]--link--[/COLOR]]("https://askubuntu.com/questions/336518/why-has-ubuntu-moved-the-default-mount-points") from [noparse]askubuntu.com[/noparse] should answer your question and includes links to further information as to why the change to /media/$USER/ from /media/ was made. Apparently the changes were made in Quantal 12.10 when udisks2 was introduced.

Basically the normal usage in Ubuntu is now /media/$USER/<drive-name>.
> ...Ubuntu as of 10.04... Is that a typo? Do you mean 18.04 or 19.04 there? Lucid 10.04 is a very long dead, end-of-life, release. 

Regards, yeti.

---

### Post by DarkDancer on 2019-06-10
It was a typo, 19.04... ;)

So when installing and setting up a Storage drive instead of mounting it as /media/Storage it would be /media/$USER/Storage... Maybe, (hopefully) that's why I can't get it to boot when the instal is done.

---

### Post by yetimon_64 on 2019-06-11
> **DarkDancer said:**
> ...So when installing and setting up a Storage drive instead of mounting it as /media/Storage it would be /media/$USER/Storage... Maybe, (hopefully) that's why I can't get it to boot when the instal is done.

I usually manually mount to /media/$USER/Storage just to maintain consistency with what is automatically mounted by the system, I think it is still possible to use /media/Storage for manual mounts, though have never really tried it myself. I can't see offhand why doing such a mount would stop the boot process though .

---

