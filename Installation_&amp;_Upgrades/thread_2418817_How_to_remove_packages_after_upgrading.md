---
title: "How to remove packages after upgrading?"
date: 2019-05-11
forum: Installation &amp; Upgrades
---

### Post by rva1945 on 2019-05-11
Hi:

I upgraded from 12.04 to 14.04 (soon more upgrades).

After installing a message warned about removing the packages would take hours so I skipped it.

Now that the upgrade was successful, how can I remove the packages? Where are they?

Thanks

---

### Post by rva1945 on 2019-05-11
*sudo apt*-get autoremove

---

### Post by Impavidus on 2019-05-12
Why upgrade at all? A fresh install would be better. Going from 12.04 (which has been dead for over two years), via 14.04 (dead as well) and 16.04 (still alive, but old), to 18.04 is asking for trouble and will take a full day. A fresh install can be done in less than an hour, including the download if you have a decent internet connection – and if your connection is bad, that will hurt the upgrades more than the fresh install. And as you jump many versions ahead, you have to reconfigure pretty much every application.

So just use a fresh install. You may want to keep your /home if it's on a separate partition, or make a backup of your home directory and restore it after the install. In the latter case it may be better to backup just your documents, bookmarks, things like that, not your settings. So many things have changed that you have to reconfigure most applications anyway.

---

### Post by Topsiho on 2019-05-12
+1 for impavidus. What he says (writes, of course) is fully correct.

Topsiho

---

### Post by rva1945 on 2019-05-12
So where can I download the iso for a live CD of the latest version?

---

### Post by oldos2er on 2019-05-12
You'll need either a DVD or USB, it's been years since the ISO fit on a CD.

[https://www.ubuntu.com/download/desktop](https://www.ubuntu.com/download/desktop)

---

