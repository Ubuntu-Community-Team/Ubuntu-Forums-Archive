---
title: "Installation &amp; Performance when Only Main Repostory Enabled"
date: 2017-06-01
forum: Installation &amp; Upgrades
---

### Post by richolad-k on 2017-06-01
I'm currently using Debian Testing (stretch) with only the Main repository enabled, and it works well for me.  I prefer a couple of the Ubuntu Flavors (Xubuntu, MATE) because of even newer apps than in stretch, and am wondering how to install from a DVD and enable only the Main repository.  Then, I am wondering if the functionality will be similar to what I am experiencing now.  Any help would be appreciated.  Thanks, in advance.

---

### Post by QIII on 2017-06-01
Hello!

Do you mean you want to install one of the Ubuntu flavors with only the main Debian repo active?  Debian with only the main Ubuntu repo active?  An Ubuntu flavor with only the main Ubuntu repo active?

---

### Post by richolad-k on 2017-06-01
> **QIII said:**
> Hello!

Do you mean you want to install one of the Ubuntu flavors with only the main Debian repo active?  Debian with only the main Ubuntu repo active?  An Ubuntu flavor with only the main Ubuntu repo active?

If I could install directly with only Main enabled, and have a reasonable reason to believe my functionality would be similar to what I have now with stretch, I would install Xubuntu, I think.  I already have the disk burned.  I could always just try it, but I prefer not to waste half the day trying and then having to reinstall if someone already has some insight.

---

### Post by ajgreeny on 2017-06-01
But install what with only the main repos enabled?  
You have still not told us what exactly you are trying to do, and I am totally confused about the "what" and the "why".

You do not get any options about which repos are enabled when you install any of the *ubuntu family apart from the third party packages that you are offered.  If you refuse those and also do not accept the offer to update packages while installing, you can then edit your software sources after installation so that only the repos you want are enabled.

I do, however, find it difficult to figure out why you would want to do that and not use the normal default list of repos.

---

### Post by richolad-k on 2017-06-01
> **ajgreeny said:**
> But install what with only the main repos enabled?  
You have still not told us what exactly you are trying to do, and I am totally confused about the "what" and the "why".

You do not get any options about which repos are enabled when you install any of the *ubuntu family apart from the third party packages that you are offered.  If you refuse those and also do not accept the offer to update packages while installing, you can then edit your software sources after installation so that only the repos you want are enabled.

I do, however, find it difficult to figure out why you would want to do that and not use the normal default list of repos.

I think I was clear that I wanted to install with the main repo only, as I have with debian stretch.  My reasons include a desire to use only truly free and non-proprietary software, and to have that software secured by the internal mechanisms of the distro itself, which rules the universe repo out.  This is not an uncommon goal in the linux world.  Despite your inability to understand my question, you have answered it, for which I thank you.  I now know what I need to do.  I consider this question answered.

---

### Post by QIII on 2017-06-01
Unlike Debian, I don't think you can absolutely guarantee that what is in Ubuntu's main main repo is truly free and non-proprietary.  Probably?  Sure.

Many FLOSS purists attack Ubuntu because there can be packages that are not strictly FLOSS, even if they include source code you may modify and redistribute.

Here is what Canonical says about MAIN:

> All application software included in the Ubuntu main component:

    **Must include source code**. The main component has a strict and non-negotiable requirement that application software included in it must come with full source code.

    **Must allow modification and distribution of modified copies under the same licence**. Just having the source code does not convey the same freedom as having the right to change it. Without the ability to modify software, the Ubuntu community cannot support software, fix bugs, translate it, or improve it.


The bold is mine.  Strictly speaking, I don't think those two are sufficient to guarantee FLOSS.  The Ubuntu kernel, in fact, may contain firmware BLOBs.

That said ...  Your user experience may be significantly limited by staying strictly with main.  I don't know what your definition of "performance" is, but mine includes being able to do what I want to do with whatever tool strikes my fancy.

---

### Post by richolad-k on 2017-06-01
> **QIII said:**
> Unlike Debian, there is no guarantee that what is in Ubuntu's main main repo is truly free and non-proprietary.

Many FLOSS purists attack Ubuntu because there ARE such packages.

So, I can't take this page at face value: [https://help.ubuntu.com/community/Repositories](https://help.ubuntu.com/community/Repositories) ?  This would be important for me to know before I leave Debian...

---

### Post by QIII on 2017-06-01
You can take it exactly at face value:  > The main component contains applications that are free software, can be freely redistributed and are fully supported by the Ubuntu team.

As I said above, some FLOSS purists would not find those conditions sufficient.  If you are not a strict purist, that might be fine.

Also, as I said, there can be firmware BLOBs in the kernel depending on the hardware configuration detected at install time.

I'm not trying to discourage you or disparage FLOSS adherents.  I'm just telling you that your dinner may have been prepared on machinery used to prepare peanuts -- in case you are allergic.

---

### Post by richolad-k on 2017-06-01
Very well, QIII.  I understand.

---

