---
title: "No Installation Candidate... For ANYTHING!"
date: 2012-05-01
forum: Installation &amp; Upgrades
---

### Post by Celtisch on 2012-05-01
I have searched for the problem a bit myself and I can't find it.

**Everything** "has no installation candidate"! 

Doesn't matter what it is- after adding repositories successfully, apt-get upgrade/update successfully... No installation candidate from the repository I added two seconds ago, because f*** logic. :confused:

I've used Ubuntu for years and never have I seen this before.
What happened?

I am on Lucid (v10.04)

> Package <package name> is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package <package name> has no installation candidate


Any tips? Thanks in advance.

---

### Post by Celtisch on 2012-05-01
BUMP
Okay I figured out that it's not *everything* but pretty much anything that I try, even after properly adding repositories, a successful upgrade and update, it still won't install packages from the repository that I just installed.

No replies yet?

---

### Post by dino99 on 2012-05-01
if you use (have used) ppa, then run ppa-purge first

---

### Post by Celtisch on 2012-05-01
Thank you for the reply. I don't get why I am purging a repository though. :/

---

### Post by TBABill on 2012-05-01
In your software sources did you tell the system never to advise you an upgrade is available? Wondering if that setting could stop it from recognizing the new release is available.

---

### Post by Celtisch on 2012-05-01
> **TBABill said:**
> In your software sources did you tell the system never to advise you an upgrade is available? Wondering if that setting could stop it from recognizing the new release is available.

You are talking about distro version upgrades?
Actually yes, I did tell it to do that.

Strange that it would cause it to not recognize software packages. :/

Also, I enabled "Partner repositories" and that still doesn't help.

So, if it was really caused by telling my system to not notify me of new distribution version upgrades, what do I do to fix this?

---

### Post by gordintoronto on 2012-05-01
I think there is a setting to choose only LTS versions. It is probably looking for 10.10, which is no longer supported.

In any case, I would suggest you try to manage a clean install rather than an upgrade. Much more work, but a better chance of success.

---

### Post by kenyard on 2012-05-03
i have same issue...still trying to figure out how to fix it.
installed 12.04 there today after formatting my hdd. so a clean install and now all these issues getting stuff going again :/

---

