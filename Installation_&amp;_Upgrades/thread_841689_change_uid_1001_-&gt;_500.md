---
title: "change uid 1001 -&gt; 500"
date: 2008-06-26
forum: Installation &amp; Upgrades
---

### Post by Kropotkin on 2008-06-26
Hi all,

I have just installed 8.04 on a new laptop, and I need to change my uid fron 1001 to 500 so as to be able access files on some Fedora and BSD NFS shares.

In the past I have logged out, logged in as root via failsafe terminal, and run 

usermod -u 500 <my login>

But now it doesn't work; when I try to re-log in, Gnome can't read any of the config files. The only way I can access my home dir again is to reset the uid to 1001.

I have done this often enough before, but either I have forgotten a step, or something has broken or been changed.

Thanks.

---

### Post by Vivaldi Gloria on 2008-06-27
If I remember correctly Red-Hat reserves uids upto 499 for system use but debian reserves uids upto 999 for system use.

So I don't think its possible lower your ubuntu user id to 500. Why don't you try making the fedore uid something over 1000 first?

---

