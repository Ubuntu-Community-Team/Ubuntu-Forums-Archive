---
title: "How to get Win98 to use samba shares - Help please?"
date: 2008-05-27
forum: Installation &amp; Upgrades
---

### Post by pksings on 2008-05-27
Hello all;

I posted yesterday in abject frustration asking how to downgrade samba so my Win98 VM will access filesystem and printer shares.
Nobody answered.

So I am asking again, can somebody please tell me what to put in smb.conf to make Win98 work again? It worked fine in Dapper, and Fiesty but Hardy is a no-go. I have chased 4 different threads and added a bunch of stuff that made W2k pro work, but Win98 still doesn't. And I'm stumped.

I use Win98 to run Quicken, it's small, light, fast and works. And I own it.
(For those of you who are wondering). I have to print reports out of it for the court so it does need to print.


The solution is to add the following to your smb.conf in the "global" section.

client lanman auth = yes
lanman auth = yes

Then re-create the password for each of your users, it's using a different hash to do it, that's why the old one doesn't work anymore. 

smbpasswd username (enter) 
or smbpasswd -a username (to add a new username)

stop and restart samba, /etc/init.d/samba restart.

Whammo, it works!

The fix was found on the samba users mailing list.

---

