---
title: "Postfix/Dovecot mail server migration +"
date: 2018-10-24
forum: Installation &amp; Upgrades
---

### Post by Leechpool on 2018-10-24
Hi,
I've had a postfix/Dovecot/Fetchmail mail server running on ubuntu 12.04 for many years.  I've finally got around to updating things. The system is on one partition and the maildir directories are on another.  Worried about my ability to do things smoothly, I installed another 18.04 system on another partition such that I could boot the old 12.04 or new 18.04.  In 18.04 I followed the same postfix/dovecot install directions as I had for 12.04 before, creating user/group vmail id 5000 etc on 18.04 so it would mirror those used for mail on 12.04.  I copied the etc/postfix and etc/dovecot config files over from 12.04 to 18.04 (effectively using the same maildir directories on the third partition for the 12.04 and 18.04 installations).  It seemed to work, when I booted 18.04 on the server, I created a new profile in thunderbird on a client machine and when I added the account settings all the mail already there appeared and new mail was fetched correctly etc.  When I booted back into 12.04 I found some mail folders worked ok e.g. sent items, but over time I noticed some didn't e.g. inbox would be empty and no new mail appeared.  But when I boot back into 18.04 new mail appears and everything works. The 12.04 installation is set up for squirrelmail and I noticed that squirrelmail appeared to be working (inbox correctly populated with mail and new mail appearing). I checked the user and permissions of the maildir directories/files and it all seems as it should be. 

I appreciate it's perhaps a strange thing to try but I have other things I need to get working on the 18.04 install before we go over to it permanently.  This is why I wanted parallel systems to give me time to get 18.04 fully configured and tested.  Could someone help point me in a direction in terms of what could be going wrong, even if it is to explain why this will never work.  

Thanks
:D

---

### Post by Leechpool on 2018-10-26
I found the problem so I thought I'd post in case it helps someone....
It appears that running different versions of Dovecot can cause the index files placed in the maildirs to become corrupt.  I noticed I kept getting server disconnections whenever I tried to do anything in a folder like delete etc... I looked in the /var/log/dovecot logfile on the server and found lots of errors which started like this:

> Jul  4 10:44:22 claudia dovecot: imap(someuser@core-admin.com): Panic: file mail-index-sync-keywords.c: line 227 (keywords_update_records): assertion failed: (data_offset >= sizeof(struct mail_index_record))
Jul  4 10:44:31 claudia dovecot: imap(someuser@core-admin.com): Panic: file mail-index-sync-keywords.c: line 227 (keywords_update_records): assertion failed: (data_offset >= sizeof(struct mail_index_record))

I googled "assertion failed: (data_offset >= sizeof(struct mail_index_record)" which led me to this:

[http://https://www.core-admin.com/portal/fixing-dovecot-panic-mail-index-sync-keywords-c-broken-dovecot-indexes]("https://www.core-admin.com/portal/fixing-dovecot-panic-mail-index-sync-keywords-c-broken-dovecot-indexes")

Although I think it's written for a windows based system (doesn't seem to be Ubuntu/Linux), it implied that differing programme versions corrupted the indexing and the fix was as simple as deleting the index files. You don't even have to restart Dovecot. Dovecot automatically regenerates the index files. I suspect just deleting them is a bit brutal and the proper fix is to use doveadm to force reindexing etc but I am not familiar with doveadm. I just know the minimum I need to get things working. Hence, my difficulty in even working out how to go about diagnosing the issue...

After doing some backups, I navigated to the root of the mailbox affected and ran:

```
find . -name "dovecot*" -type f
```
to list matching files to check nothing unintended was going to happen. Then added -delete to the end of the command to actually delete all the index files.

```
find . -name "dovecot*" -type f -delete
```

After that everything was fine.  It's worth nothing that each mail folder within a mailbox has such files in it, hence the recursive command. Initally, I just fixed the INBOX. However, I then had issues deleting files etc. and I believe it was because the indexing in the trash folder was still corrupt. I did the recursive command and everything seems to be fixed.

Hope this helps someone.

:p

---

