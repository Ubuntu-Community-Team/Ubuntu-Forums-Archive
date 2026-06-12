---
title: "Is there any way to Lock Ubuntu Filesystem"
date: 2008-11-06
forum: Installation &amp; Upgrades
---

### Post by ivikas on 2008-11-06
Hello all,

         Is there any way to lock directories on Ubuntu,such as application that will securely lock personal folders on hard disk(not like password protected zip or rar archives).Now a days there are windows application that can read linux filesystem directly and it does not respect file permission and so all the personal data's can be compromised.I have heard of drive encryption.So it it possible to encrypt just the ubuntu partition on my hard disk.Will these can lead to any problems?

with regards,
Vikas

---

### Post by Partyboi2 on 2008-11-07
You could try encrypting your /home 
> **Encrypted private directory**

  The ecryptfs-utils package was recently promoted to Ubuntu main, with support for a [secret encrypted folder]("https://help.ubuntu.com/community/EncryptedPrivateDirectory") in your Home Folder (by Michael Halcrow, Dustin Kirkland, and Daniel Baumann).  
  You can help test this new feature by going to Applications &#8594; Accessories &#8594; Terminal and typing:  
 
[LIST]
[*]          sudo aptitude install ecryptfs-utils
[*]          ecryptfs-setup-private
[/LIST]
 or maybe try something like
[http://ubuntu-tutorials.com/2007/08/17/7-steps-to-an-encrypted-partition-local-or-removable-disk/](http://ubuntu-tutorials.com/2007/08/17/7-steps-to-an-encrypted-partition-local-or-removable-disk/)

---

### Post by zvacet on 2008-11-07
Maybe [this]("https://help.ubuntu.com/community/EncryptedFilesystemHowto7") will help you.

---

