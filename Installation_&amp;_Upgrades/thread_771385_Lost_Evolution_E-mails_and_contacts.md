---
title: "Lost Evolution E-mails and contacts"
date: 2008-04-27
forum: Installation &amp; Upgrades
---

### Post by juniorsonny on 2008-04-27
I upgraded from Gutsy to Hardy using a live cd because the update manager locked up and didn't finish the upgrade.  I chose the option during upgrade to import all documents from Gutsy(evolution e-mail and setting and such).  It set up the account but did not import the e-mails or contacts.  My Question is, Where are they and how do I get them back? Or, are they lost forever?

---

### Post by pytheas22 on 2008-04-27
Is there a directory named '.evolution' in your /home folder?  In other words, what is the output of the command:
```

ls -a | grep evolution
```

Also, did you create any new user accounts or modify partitions for any reason?  And is /home on its own partition or under / ?

---

### Post by juniorsonny on 2008-04-28
I found the folder in another partition that was made from the import.  I was able to retrieve my mail and contacts.  Thanks for the help!!!

---

