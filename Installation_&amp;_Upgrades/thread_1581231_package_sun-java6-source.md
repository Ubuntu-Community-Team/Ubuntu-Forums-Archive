---
title: "package sun-java6-source"
date: 2010-09-24
forum: Installation &amp; Upgrades
---

### Post by tinker123 on 2010-09-24
I have the Sun javac and jre installed on the latest Ubuntu.

I would like to install this package:

sun-jav6-source

Synaptic doesn't list it and I can't find a *.deb to download.  

How can I get it?

How can I tell what directory it will install into?

Thanks in advance for any info

---

### Post by howefield on 2010-09-24
Have you enabled the Partner repository ?

---

### Post by tinker123 on 2010-09-24
I did not know there was such a thing.

I went into System | Admin | Software Sources | Other Sources (tab)

and checked off the first 2 of 4 check boxes.  I then ran the reload

Ubuntu sill complains it does not know about sun-java6-source

---

### Post by howefield on 2010-09-24
By latest Ubuntu, you are referring to 10.04 Lucid ?

The package is in the partner repository.

[http://archive.canonical.com/ubuntu/dists/lucid/partner/source/Sources](http://archive.canonical.com/ubuntu/dists/lucid/partner/source/Sources)

---

### Post by tinker123 on 2010-09-24
> **howefield said:**
> By latest Ubuntu, you are referring to 10.04 Lucid ?


Yep

> 
[i]
steve@Wisdom:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 10.04.1 LTS
Release:	10.04
Codename:	lucid
steve@Wisdom:~$ 
[/i]



> 
The package is in the partner repository.

[http://archive.canonical.com/ubuntu/dists/lucid/partner/source/Sources](http://archive.canonical.com/ubuntu/dists/lucid/partner/source/Sources)

I tried adding that in the "Other Sources" tabl of System | Admin | Sources  but the add button stayed grayed out.

I found this helpful tutuorial, but the URLs in the screen shot for "partner repositiories"  don't exist in my system

---

### Post by tinker123 on 2010-09-26
I don't know what I did differently, but I got the partner URLs added to the source mangager.   I had to explicitly uninstall off of the openjdk stuff with synaptic but I got Sun's Java completely up.

---

