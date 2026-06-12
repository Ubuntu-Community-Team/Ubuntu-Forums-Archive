---
title: "Adding repositories to keep software updated"
date: 2011-12-23
forum: Installation &amp; Upgrades
---

### Post by jdix123 on 2011-12-23
So I was poking around with the "Ubuntu Tweak" utility and I noticed something that confused me.

There is a section called "Source Center" where you can "ensure your applications are always up-to-date."  But I'm confused, I thought since I installed chromium (for example) using

```
sudo apt-get install chromium-browser
```

that meant that it was ALREADY available in my current ppa list.  So does it not update automatically unless I enable the new repository?

I scroll through the list and check off the repositories I think I need to have updated (stable releases) and leave the ones I don't think I need (most of them, mainly things like beta releases and daily builds) alone.

Now before I go ahead and install these hundred and something new packages, is there a reason they aren't automatically added?

---

### Post by zvacet on 2011-12-27
If you installed Chromium through PPA then make sure that PPA is enabled and you will get all updates for that package via PPA.

---

