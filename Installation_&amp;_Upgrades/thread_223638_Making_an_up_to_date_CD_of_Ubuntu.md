---
title: "Making an up to date CD of Ubuntu"
date: 2006-07-26
forum: Installation &amp; Upgrades
---

### Post by mhw on 2006-07-26
Dear All,
I'm going to try and install Ubuntu on a group of computers in a country in Africa. There will be an internet connection, but it's not that fast.

I'd like to make a copy of the up to date Ubuntu packages; I can obviously download and burn the standard Dapper iso, but is there anyway I can grab all the updates - this way, I could burn all the updates a few days before going out, and then there wouldn't be much to download.

Any ideas?

Thanks,
Matt

---

### Post by prash@linuxitarian on 2006-07-26
I am no expert but was wondering if you could do something rsync the dapper-updates to a local folder on the hard drive? Not an expert sorry....

---

### Post by John.Michael.Kane on 2006-07-26
You may want to have a look over these [**[COLOR="Red"]AptMoveHowto[/COLOR]**]("https://help.ubuntu.com/community/AptMoveHowto") [**[COLOR="Blue"]AptMoveHowto/simple[/COLOR]**]("https://help.ubuntu.com/community/AptMoveHowto/simple")

---

### Post by mhw on 2006-09-20
Thanks a lot for these.

I followed the Simple guide, as I didn't need GPG signing. The only problem I had was with the  

dpkg-scanpackages pool /dev/null | gzip -9 > dists/stable/main/binary-i386/Packages.gz

command. I kept getting an error, which I solved by manually making the directories stable/main/binary-i386/ in dists.

Apart from that, seemed to work a treat.

I'll hopefully test the end result sometime this week, and if it works I'll try and amend the wiki.

Matt

---

