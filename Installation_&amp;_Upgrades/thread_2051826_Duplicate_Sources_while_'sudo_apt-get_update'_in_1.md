---
title: "Duplicate Sources while 'sudo apt-get update' in 12.04? Have I done right?"
date: 2012-09-02
forum: Installation &amp; Upgrades
---

### Post by satyamM on 2012-09-02
Hello everyone,

I have upgraded from 10.04 to 12.04  two days back and problems with 12.04 version continue to exist in my case.

New problem is when I update 'sudo apt-get update' command....everything goes all right till end except for last line which reads like

W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) precise/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-i386_Packages)


I started searching for this error....

As far as I could search on Google and ubuntuforums.org , I found a solution which said
/etc/apt/sources.list.d/ might be having a file which has same content as one of the lines in /etc/apt/sources.list .....I searched...and there I find following::

In sources.list.d/lucid-partner.list ...it has only one line and that line matched with one of the line of actual sources.list.....so I have commented the line in sources.list.d/lucid-partner.list ........now, when I update , I get no errors.....

So i wanted to ask have I done right to comment the line in /sources.list.d/lucid-partner.list or should I do something else....??

---

### Post by satyamM on 2012-09-02
Please reply someone...... :( :(

---

### Post by oldos2er on 2012-09-02
If you're not getting anymore errors, your problem is solved.

---

### Post by satyamM on 2012-09-02
No, your answer doesn't satisfy me...... 
Its not like if I am not getting anymore errors then its okay...

I am asking whether I have done the right thing or not by commenting same line in sources.list.d/lucid-partner.list which was there in sources.list . ?? is it right to do so?

---

### Post by oldos2er on 2012-09-02
> **satyamM said:**
> No, your answer doesn't satisfy me...... 
Its not like if I am not getting anymore errors then its okay...

Actually, it is. Most terminal programs only give negative feedback; i.e. when something has failed they tell you so. No errors = it worked.

> I am asking whether I have done the right thing or not by commenting same line in sources.list.d/lucid-partner.list which was there in sources.list . ?? is it right to do so?

Yes.

---

### Post by satyamM on 2012-09-02
Okay Mrs. **Ann**[[COLOR=#DD4814][/COLOR]]("http://ubuntuforums.org/member.php?u=338320").
Thanks for your concern.
I'll remember "No errors = it worked".

:-P

---

