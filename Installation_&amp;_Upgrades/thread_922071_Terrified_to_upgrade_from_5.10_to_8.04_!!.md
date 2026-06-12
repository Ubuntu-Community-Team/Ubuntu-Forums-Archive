---
title: "Terrified to upgrade from 5.10 to 8.04 !!"
date: 2008-09-16
forum: Installation &amp; Upgrades
---

### Post by CzarAlex on 2008-09-16
Ugh.. Yes. I'm ready to get yelled at. 

My server is running 5.10 "Breezy Badger" and has been for quite sometime. Well...since that version came out. Everything was fine. In fact, everything -is- fine.

But now some of the things I'd like to install on the box aren't playing nice with my antiquated versions of php and mysql.

I have everything on the box just the way I want it. My blog, website, everything. Is there some magic way I can upgrade and migrate all my files/settings over so the box is just how it is now.. just updated?

---

### Post by jpeddicord on 2008-09-16
> **CzarAlex said:**
> Ugh.. Yes. I'm ready to get yelled at. 

My server is running 5.10 "Breezy Badger" and has been for quite sometime. Well...since that version came out. Everything was fine. In fact, everything -is- fine.

But now some of the things I'd like to install on the box aren't playing nice with my antiquated versions of php and mysql.

I have everything on the box just the way I want it. My blog, website, everything. Is there some magic way I can upgrade and migrate all my files/settings over so the box is just how it is now.. just updated?

Yikes! I don't know the exact procedure for this, but you'll first want to upgrade to 6.06, and then to 8.04. You can't directly upgrade to the latest, with the exception of the 6.06 > 8.04 LTS bridge.

First step, backup. Then continue.

My best guess is to first edit /etc/apt/sources.list and replace all instances of 'breezy' with 'dapper'. apt-get dist-upgrade and then make sure everything is up and running on Dapper. If you are fine with everything Dapper has, stay there. It's supported for quite a long time. :)

If you want to upgrade to 8.04 from there, run `sudo do-release-upgrade` on your up-to-date Dapper box and that should take care of everything.

I can't say you won't have issues, but that should be the general way to get it done.

---

### Post by CzarAlex on 2008-09-16
I'd actually be okay with getting up to Dapper, as long as I can upgrade my web components like php and mysql.

I was a linux novice when I started back in the Breezy days. Things would break, I'd come here and learn how to fix them. Then once I got everything running the way I wanted, I never had to go in and fix anything..and lost what little skills I have. Even properly backing up will be a little difficult for me. But at least its a start. Thanks!

---

### Post by Sef on 2008-09-17
> I'd actually be okay with getting up to Dapper, as long as I can upgrade my web components like php and mysql.

Dapper server will get updates until June 2011.  Dapper Desktop will get updates until June 2009.

---

### Post by y@w on 2008-09-17
Depending upon how much time/resources you want to dedicate to this.. a great option would be to convert the machine into a virtual machine. Then you can try the upgrade and not worry if it fails. Also, you can take snapshots before making drastic changes so you don't lose a bunch of time. The VMware physical to virtual converter can be downloaded [here]("http://www.vmware.com/products/converter/").

---

### Post by CzarAlex on 2008-09-17
I have a couple users who SSH in to my box. By copying their /home folders over, does that copy their login information?

Thankfully, I have a 2nd box that I can set this upgrade up on. I think I`ll just go from a fresh install

---

### Post by y@w on 2008-09-17
> **CzarAlex said:**
> I have a couple users who SSH in to my box. By copying their /home folders over, does that copy their login information?

Thankfully, I have a 2nd box that I can set this upgrade up on. I think I`ll just go from a fresh install

Well, you have to get /etc/passwd and /etc/shadow and chown their home directories, but yes you can do that. A fresh install would definitely be the least risky, most clean, and probably the least time-consuming.

---

