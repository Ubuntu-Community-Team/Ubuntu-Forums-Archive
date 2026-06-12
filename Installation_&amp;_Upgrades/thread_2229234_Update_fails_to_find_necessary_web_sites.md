---
title: "Update fails to find necessary web sites"
date: 2014-06-12
forum: Installation &amp; Upgrades
---

### Post by Ralph L on 2014-06-12
I am running ubuntu 12.04, Kernel Linux 3.2.0-51-generic-pae, GNOME 3.4.2.  When I try to run Update-Manager, I get a bunch of error messages of this form:
```
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/d/dpkg/dpkg_1.16.1.2ubuntu7.2_i386.deb 404  Not Found [IP: 91.189.91.15 80]
```

I tried accessing this site directly with firefox and it failed.  However, I was able to access every other web site I tried with firefox, so I think my internet connection is working fine.  Did somebody take down the update sites, or have I done something wrong?  

I attached the full set of error message in the attached file.

Thanks in advance.

---

### Post by bapoumba on 2014-06-12
[http://us.archive.ubuntu.com/ubuntu/pool/main/d/dpkg/](http://us.archive.ubuntu.com/ubuntu/pool/main/d/dpkg/)
Can you go there ? May be just a glitch because the link is working for me. Please run again :
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by rahul4557 on 2014-06-12
May be your Internet is filtered and does not allow you to access certain sites.

check if you can ping 8.8.8.8
if yes then set 8.8.8.8 as your DNS and then try updating.

---

### Post by deadflowr on 2014-06-12
That particular package doesn't seem to exist any more, from what I can tell.
Run the "Check" on the Update Manager, first to see if it updates the packages available before trying the update command listed before.
If after running the "Check" option it still has problems, then run the
```
sudo apt-get update
```
command and post the out put here in this thread
(use code tags please)

---

### Post by bapoumba on 2014-06-12
Hmm, the package does exist for precise : [http://packages.ubuntu.com/precise/dpkg](http://packages.ubuntu.com/precise/dpkg) and on the us mirrors.

---

### Post by deadflowr on 2014-06-12
Yeah, but it's <package>7.5 now, not 7.2.
I don't see
dpkg_1.16.1.2ubuntu**7.2**_i386.deb
in the listing.
Maybe I need my eyes checked.

---

### Post by bapoumba on 2014-06-12
Good catch :)

If the OP has a bunch of other such errors, a full paste of the errors would help in addition to :
```
cat -n /etc/apt/sources.list
ls /etc/apt/sources.list.d
```

There may be some problems with repositories.

---

### Post by Ralph L on 2014-06-12
Thanks again for the responses.  You really helped me.

I did:
sudo apt-get update
sudo apt-get upgrade
These ran without error.  Then I ran Update Manager again and everything now seems ok.  

Another question:  I was a little worried, when I ran "sudo apt-get upgrade" that I would upgrade to the latest version of Ubunut, which I don't want to do.  I want to stick with precise until there is some real reason (for my usage) to upgrade.  Anyway "sudo apt-get upgrade" did NOT upgrade me to the latest Ubuntu.  Would somebody explain what apt-get upgrade does, so that I can use it again and make sure I stay with precise?  I read the man page and (the way I read it) I should have been upgraded to the latest version of Ubuntu--but maybe the archives are designed so this doesn't happen.

---

### Post by bapoumba on 2014-06-12
No, an upgrade will upgrade the packages you have installed to the latest versions IN your distribution.
Upgrading to a newer release is another story.

Edit : and you are welcome. Please mark your thread as solved (under Thread Tools), thanks.

---

