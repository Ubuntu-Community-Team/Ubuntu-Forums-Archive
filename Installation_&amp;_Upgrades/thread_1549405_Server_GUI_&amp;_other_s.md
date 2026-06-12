---
title: "Server GUI &amp; other ?s"
date: 2010-08-09
forum: Installation &amp; Upgrades
---

### Post by ask21900 on 2010-08-09
Hello All,

I am looking for a little advice from the experts here (as always ;-) !)

I have set up several Ubuntu servers in the past but always end up wishing I did things a little different later down the line.  Unfortunately, I never remember all the little things that I wanted to change next time, so I was hoping for suggestions on the "perfect setup"!

My first question is whether to setup a gui or not.  I am converting a Windows SBS 2003 over to Ubuntu.  Nobody that works for this company will be able to use bash (or they don't as of now), but since this is a (for the most part) file server, nobody should really be logging into the terminal anyway.  Should I waste resources on a gui in the event that a n00b wants to login for whatever reason some day, or just stick with the cli?

I also have been debating the directory structure and permissions a little bit.  I will be setting up samba and fuse so that those who need to access things can (mainly samba).  I have had problems in the past where a samba user is denied access to a folder (using samba's user-level permissions) and I couldn't figure out why.  I tried chmod, chgrp, etc to no avail.  I would like to avoid these types of issues (I am by no means a permissions expert) while still maintaining a certain level of security.

A thoughts or suggestions to the above, or server installation in general, would be greatly appreciated!

Thanks

---

### Post by mörgæs on 2010-08-10
> **ask21900 said:**
> 
Should I waste resources on a gui in the event that a n00b wants to login for whatever reason some day, or just stick with the cli?


The X11 environment does not take significant resources, unless you have a very old server. Do what is most convenient for you and your users. 

I have no experience with setting um Samba, sorry.

---

