---
title: "Once Ubuntu + twice Windows 7 + TrueCrypt for all partitions. How to do it?"
date: 2012-06-19
forum: Installation &amp; Upgrades
---

### Post by xubulubu on 2012-06-19
Hello all!

I have a new laptop with a 500 GB harddisk and would like to achieve the following:

- on one partition: Ubuntu or Xubuntu
- on another partition: Windows 7
- on another partition: again Windows 7
- AND: ALL partitions should be encrypted, if possible using TrueCrypt.

My question is: What are all the necessary steps and especially what will be the RIGHT ORDER? Installing first Linux? First Windows 7? Encrypting at the end? In the beginning?...

Thanks a lot for your advice!

---

### Post by sudodus on 2012-06-19
Rule of thumb: Install the least intelligent system first. I suggest that you install Windows first and to a primary partition. And install linux afterwards. 

Why two Windows 7 installations?

I don't know about Truecrypt, so let us wait for someone else's advice about that.

---

### Post by xubulubu on 2012-06-19
> **sudodus said:**
> Rule of thumb: Install the least intelligent system first. I suggest that you install Windows first and to a primary partition. And install linux afterwards. 

Why two Windows 7 installations?

I don't know about Truecrypt, so let us wait for someone else's advice about that.

In the meantime I found a tutorial about installing Windows 7 and Ubuntu side by side, and in fact it's based on first installing Windows 7 and then Ubuntu. I already checked out installing Windows 7 twice, so now I will probably first install Windows 7 twice on different partitions, then Xubuntu and then see if everything works. After that there will be the issue of encrypting everything. So far I have no idea if TrueCrypt is smart enough to encrypt a whole hard disk when there are different operating systems on it.

I need Windows 7 twice because the one version on one separate partition will be used (and optimized) exclusively for music production, which means no system sounds, no Internet connection, no firewall, no running nonsense programs/services/anti virus software etc. etc.

---

### Post by sudodus on 2012-06-20
I see why 2w7 now :-)

You can encrypt the whole drive or separate partitions (including Windows partitions) according to Truecrypt's web page
[[COLOR="Red"]_http://www.truecrypt.org/_[/COLOR]]("http://www.truecrypt.org/")

An advantage with separately encrypted partitions is that it is faster to encrypt/decrypt only the partition(s) that you plan to use. And there should be no classified information in the partition table.

And don't forget that it is at least as important to make ***good and regular backups*** as to encrypt your data, and to keep a copy in another house (for example a cloned hard disk drive or a hard disk drive with a complete image of your internal HDD).

Also look at this link and apply what is appropriate.
[[COLOR="Red"]_https://wiki.ubuntu.com/BasicSecurity_[/COLOR]]("https://wiki.ubuntu.com/BasicSecurity")

---

