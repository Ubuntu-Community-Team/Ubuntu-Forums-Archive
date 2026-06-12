---
title: "dovecot imapd assertion failure (Ubuntu 6.10 (Edgy) amd64)"
date: 2006-11-26
forum: Installation &amp; Upgrades
---

### Post by zhaytee on 2006-11-26
Hullo.

I recently obtained a new server with an amd64 processor. I am using the amd64 distribution of Edgy (Ubuntu 6.10) on the server.

Unfortunately, I am having a problem with dovecot. With my local client, I am able to log into my dovecot server using TLS. However, when I go to read any of my mail folders, an error is written to /var/log/mail.log and I get no mail sent to my client.

The exact error is as follows.

dovecot: IMAP(zhay): file index-mail.c: line 105 (index_mail_get_fixed_field): assertion failed: (buffer_get_used_size(buf) == data_size)
dovecot: child 29900 (imap) killed with signal 6

Can anyone lend me a hand with this problem? I'd appreciate it.

Thanks,

--JT
[http://zhay.name/music/](http://zhay.name/music/)

---

### Post by MJN on 2006-11-27
I'm not at my machine right now so can't check the exact filenames however would I be right in thinking your existing Dovecot installation was on a 32bit machine? If so, I believe certain aspects (time/date fields?) of the index files may differ.
 
To fix, firstly backup your mail folders (just in case!) and try removing all your dovecot.index files (I believe that's what they're called - you may also have dovecot.index.cache which should be removed too) and when Dovecot is restarted it'll rebuild a new index file for each folder (as you go into them).
 
Specifically, try **find <path of your mail dir>/ -name 'dovecot.index*' -exec rm {} \;**
 
Mathew
 
P.S. In case you missed it first time, **BACKUP first!**

---

### Post by zhaytee on 2006-11-27
Holy crap, that was totally it. Thanks a bunch; it's working fine now.

--JT
[http://zhay.name/music/](http://zhay.name/music/)

---

### Post by MJN on 2006-11-27
Good to hear it! (and nicely put by the way!)

Incidentally, well done for mentioning the otherwise potentially-insignficant bit about moving to a 64-bit CPU as without that clue we could've been here quite some time! There's nothing more frustrating than going round in circles diagnosing somebody's problem when they suddenly drop in a clanger late on like '*oh by the way, the machine was struck by lightning the night before I had booting problems - could this be why the machine won't turn on?*' ;)

Mathew

---

