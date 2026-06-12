---
title: "Custom install CD now is too big for one CD!`"
date: 2007-11-05
forum: Installation &amp; Upgrades
---

### Post by ebel_ on 2007-11-05
I'm preseeding Edubuntu 6.10 Dapper to include some extra customer packages. I'm following [https://help.ubuntu.com/community/InstallCDCustomization](https://help.ubuntu.com/community/InstallCDCustomization) and it's all going great. However now my CD ISO is more than 700MB and hence won't fit on a CD. I've burned it to a DVD and it seems to be working. However I can only rely on CDs. This is going to be installed on hundreds of second hand computers, virtually none of which have DVD drives. I'm guessing it's possible to put all my custom stuff on another CD (leaving all the edubuntu stuff on cd #1). How do I make the installer promt the user to insert cd #2? I'd want all the software installed in one go, not just a stock edubuntu and then rely on the user to insert CD #2 and then start 'add/remove applications'.

Could I make CD #2 suitable for use with apt-cdrom, add then add that as an apt source in the preseed? How do I ad extra apt sources via the preseed?

---

### Post by phrostbyte on 2007-11-05
Yes I would recommend you check out apt-on-cd. Also if these machines have Internet access you can run a script on them like this:

script.sh:

#! /bin/bash
apt-get install package1 package2 package3


To run:

chmod +x scropt.sh; sudo bash script.sh


Also I would recommend using 7.10 Gutsy, since 6.10 is going out of date in less then six months.

---

### Post by ebel_ on 2007-11-06
Thanks phrostbyte.

No these macines would not have internet access. I'd like to use a LTS version of ubuntu and dapper is the latest one. I'll be switching to hardy when it comes out.

---

### Post by smwny on 2007-11-06
I have been working on this too. What you need to do is delete some of the language packs. You can find most of them in:

$CDROOT/pool/main/l/local*

DO NOT delete them all. You might want to keep any file with "common" or "en" in them.

Also you can delete some of the fonts in:

$CDROOT/pool/main/t/ttf-*

Many of those fonts are for other languages like Chinese and Japanese.

To find out about these fonts I went into the ubuntu IRC then had a pm with the bot and used the command "!info $PACKAGE" in order to determine what language they were for.

I hope this helps!

P.S. This should get rid of about 90-100 MB

---

### Post by ebel_ on 2007-11-06
Thanks for the suggestion smwny, however I'm going to want to include *a lot* of extra packages in my distrobution. I have a subset of wikipedia (about 300MB's worth) that I want to include. Deleteing extra stuff to fit onto one CD isn't really an option.

---

### Post by maybeway36 on 2007-11-06
Wow. You might want to look at how Debian works with CD prompting. Maybe even use Debian. They have an educational setup you can use, I think.

---

### Post by ebel_ on 2007-11-07
> **maybeway36 said:**
> Wow. You might want to look at how Debian works with CD prompting. Maybe even use Debian. They have an educational setup you can use, I think.

'debian-cd' seems to be how debian cds are made. It's something that's been at the back of my mind as an alternative. However all the documentation refers to debian and I'm not sure how easy it would be to use for me. I'm concerned that I might have to go back to the start. I hoped there was some easy way to do it. :)

---

### Post by desertboy on 2007-11-07
Overburn?

---

### Post by ebel_ on 2007-11-07
> **desertboy said:**
> Overburn?
I wanna put a few hundred megabytes of extra stuff on there... There's only so much one can overburn by.

---

