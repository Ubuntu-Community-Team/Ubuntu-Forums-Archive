---
title: "Apt-Get Update Error: Faile to fetch CDROM"
date: 2016-01-08
forum: Installation &amp; Upgrades
---

### Post by intrepdmind on 2016-01-08
Running server 15.10 fresh install from ISO to VM, after my first log in I'm running the traditional sudo apt-get update, and am seeing tailing errors in regards to cdrom update issues (nothing is mounted - I'm assuming this is a cdrom repo listing or something):

```
[SIZE=1][SIZE=2]
W: Failed to fetch cdrom://Ubuntu-Server 15.10 _Wiley Werewolf_ - Release  amd64 (10151021)/dists/wily/restricted/binary-amd64/Packages Please us apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu-Server 15.10 _Wiley Werewolf_ -  Release  amd64 (10151021)/dists/wily/main/binary-i386/Packages Please  us apt-cdrom to make this CD-ROM recognized by APT. apt-get update  cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu-Server 15.10 _Wiley Werewolf_ -  Release  amd64 (10151021)/dists/wily/restricted/binary-i386/Packages Please  us apt-cdrom to make this CD-ROM recognized by APT. apt-get update  cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu-Server 15.10 _Wiley Werewolf_ -  Release  amd64 (10151021)/dists/wily/main/binary-amd64/Packages Please  us apt-cdrom to make this CD-ROM recognized by APT. apt-get update  cannot be used to add new CD-ROMs

E: Some index files failed to download. They have been ignored, or old ones used instead.[/SIZE][/SIZE][B][SIZE=1]
[/SIZE][/B]
```

May not be a big deal, but I figured I'd ask, for education if anything. Thank you for any guidance you might offer.

---

### Post by intrepdmind on 2016-01-08
Found this with a bit more google-foo. At the top of this person's post, they explain how to comment this section out of /etc/apt/sources.list. Just curious to see if anyone could enlighten me as to why it would fail, or whether or not it's a big deal to leave this source out of the sources.list file.

[https://www.howtoforge.com/tutorial/ubuntu-perfect-server-with-apache-php-myqsl-pureftpd-bind-postfix-doveot-and-ispconfig/](https://www.howtoforge.com/tutorial/ubuntu-perfect-server-with-apache-php-myqsl-pureftpd-bind-postfix-doveot-and-ispconfig/)

Thank you again!

---

### Post by QIII on 2016-01-08
Your update should not fail.  Fetching those particular resources failed because those entries are still in your sources.list.

Could you please post back the results of 

```
cat /etc/apt/sources.list | grep cdrom
```

---

### Post by intrepdmind on 2016-01-08
Sure! I may have misspoken - the update as a whole did not fail, just  these entries. I went through and commented them out and re-ran the  updates successfully. Here's the requested grep output:

```

foo@ubuntu:~$ cat /etc/apt/sources.list | grep cdrom
# deb cdrom:[Ubuntu-Server 15.10 _Wiley Werewolf_ - Release amd64 (20151021)]/ wily main restricted
# deb cdrom:[Ubuntu-Server 15.10 _Wiley Werewolf_ - Release amd64 (20151021)]/ wily main restricted
foo@ubuntu:~$

```

I figured it probably wasn't a huge deal to just comment the cdrom update source out, just wanted to make sure I wasn't doing something that might complicate updates down the line.

---

### Post by QIII on 2016-01-08
Won't cause any problems at all.  You should be good!

Cheers!

---

