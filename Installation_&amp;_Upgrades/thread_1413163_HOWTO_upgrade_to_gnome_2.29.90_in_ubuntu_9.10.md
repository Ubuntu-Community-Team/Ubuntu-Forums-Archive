---
title: "HOWTO: upgrade to gnome 2.29.90 in ubuntu 9.10"
date: 2010-02-22
forum: Installation &amp; Upgrades
---

### Post by irus on 2010-02-22
how can i upgrade to gnome 2.29.90 when i am running ubuntu 9.10? thanks

---

### Post by irus on 2010-02-22
bump

---

### Post by KegHead on 2010-02-22
Hi!

I'm curious also.

What would be my benefits in 9.10?

KegHead

---

### Post by irus on 2010-02-22
new features and less memory leaks!!

---

### Post by KegHead on 2010-02-22
Hi!

Has anyone made this move /9.10?

And if so, what's the safest way to upgrade?

KegHead

---

### Post by Seq on 2010-02-22
Gnome, like many projects, takes a version scheme of X.Y.Z, where X is a major version (usually indicating breaking of compatibility), Y is the release, and Z is essentially point updates.

Odd releases (that's Y) like 2.**29**.90 are development releases. That means things can be less than stable, break, etc. Once they are tested and deemed to be fit for release, it will be called 2.30. So you probably don't want to install 2.29 on your stable Ubuntu 9.10 install.

Ubuntu's release schedule is actually based on Gnome's, so the development version of Ubuntu currently has 2.29 in it (though that, too, is far from stable). Once gnome releases 2.30, Lucid (to be 10.04) will get it, and shortly after that will be released for everybody to upgrade to.

---

### Post by KegHead on 2010-02-22
Seq,

Thanks for the info.

So, it would not help me much to upgrade?

KegHead

---

### Post by irus on 2010-02-23
i added lucid lynx repositories to software source list but core areas of gnome are not upgradeable specially the ones leaking memory such as gnome applets, snome volume control, gnome settings daemon. so the only way to go up is to upgrade to 10.04.

---

### Post by KegHead on 2010-02-23
copy.

---

### Post by Seq on 2010-02-23
> **irus said:**
> i added lucid lynx repositories to software source list but core areas of gnome are not upgradeable specially the ones leaking memory such as gnome applets, snome volume control, gnome settings daemon. so the only way to go up is to upgrade to 10.04.

Yes, you don't want to do that. There is more to Lucid than just a newer Gnome. They updated X, all sorts of libraries, etc. Mixing 9.10 and Lucid is going to just cause headaches.

---

### Post by KegHead on 2010-02-23
Hi!

Thanks Seq.

I'll wait for 10.04.

KegHead

---

