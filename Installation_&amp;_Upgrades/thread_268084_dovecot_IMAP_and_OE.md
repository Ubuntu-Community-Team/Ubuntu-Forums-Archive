---
title: "dovecot IMAP and OE"
date: 2006-09-29
forum: Installation &amp; Upgrades
---

### Post by n3r0 on 2006-09-29
Ok so I had an inbox full of stuff and when i coppied all the folders under /home/username/mail  from my old machine, it did not get coppied. I have sense learned that it was kept in /var/spool/mail/username . I do not have this file anymore.

What I do is a backup of my OE imap .dbx file. I cannot however, copy this file over the newer one as it just re syncs and downloads the newest copy no matter what I try.

Is there some way to enable bi directional syncing of the inbox folder in dovecot? Failing that does anyone know how to restore an IMAP .dbx file in OE?

thanks

---

### Post by n3r0 on 2006-09-29
OK! I have fixed it. Just posting to let others with the same problem know how i solved it.

1) shutdown dovecot server
2) copy old dbx file from backup into OE mail store
3) verify all messages there
4) ignore OE errors about not beign able to connect and copy all the mails to another pop3 temp folder (like for some other mail account)
5) restart dovecot and syncronize
6) Inbox gets deleted again, but you can just manually copy them over out of the temp pop3 folder, which because it is not IMAP, does not syncronize
7) Learn *not* to store mails in your inbox and start archiving all mail.


There you go!

---

