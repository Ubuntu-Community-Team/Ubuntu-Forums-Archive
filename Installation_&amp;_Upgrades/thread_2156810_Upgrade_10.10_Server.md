---
title: "Upgrade 10.10 Server"
date: 2013-06-23
forum: Installation &amp; Upgrades
---

### Post by cipe53 on 2013-06-23
I need to up upgrade an Ubuntu *server* 10.10. Of course this version is no longer supported EOL (apt-get update fails with 404s). 

Following Google, I have tried do-release-upgrade but that too fails also with 404s.

Google suggests changing the urls in sources.list to old-release ... if I wish to update, but says I cannot then upgrade to new versions.

Is there any path forward to upgrading 10.10?

Thank you.

---

### Post by dino99 on 2013-06-23
if you really does not want to use a "maintained" (aka newer) release, then you cant get any update except using some untrusted oldish ppas, with the risk of non compatible package(s).
10.10 is dead, thats it; choose something actual (raring for stability) instead of staying in the past.

---

### Post by cipe53 on 2013-06-23
Sorry, perhaps I did not make myself clear.

I **do** want to upgrade to the newest LTS release (I was expecting to upgrade to natty and then again to the latest LTS).

But do-release-upgrade gives 404 errors, just as apt-get update gives 404s, so does do-release-upgrade. (Certain repositories have been moved to old-release).


[LIST]
[*]Is it still possible to migrate/upgrade to the newer releases?
[*]How do I make do-release-upgrade find the sources it needs?
[/LIST]

---

### Post by gordintoronto on 2013-06-23
10.10 reached end of life more than two years ago. (I used it for the full 18 months.) I could be wrong, but I think you are looking at a fresh install.

Doing two release upgrades often causes problems, so a fresh install is a good option. But first, you need to make sure you have copious backup. Here's an extreme option: buy a new hard drive, and put the old one into a USB adapter. (I have done this, it worked great, didn't cost much.)

---

