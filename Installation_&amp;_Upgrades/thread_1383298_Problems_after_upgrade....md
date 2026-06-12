---
title: "Problems after upgrade..."
date: 2010-01-17
forum: Installation &amp; Upgrades
---

### Post by keylog on 2010-01-17
Hi everyone,
i updated my machine to 36-10 kernel with alpha2, from 36-7 kernel with alpha1. Then some problems appears. One of them isi can't mount any disk, machine says me you are not authorized. :) i look users-admin all the boxes are unticked, and i can't thick them. It gives me an error like this. ```
keylog@keylog-laptop:~$ sudo users-admin
[sudo] password for keylog: 

(users-admin:5747): Liboobs-CRITICAL **: oobs_group_add_user: assertion `OOBS_IS_GROUP (group)' failed


```

And another important problem is boot time. Machine booting too late, over 5 minutes. I edited grup and closed quiet splash, but when it's waiting there no text. My messages log is here. [http://pastebin.com/pastebin.php?dl=m7fe7648a](http://pastebin.com/pastebin.php?dl=m7fe7648a)

What can i do? :(

---

### Post by Braytonio on 2010-01-22
I also have this problem after upgrade to Lucid. I was very confused as user settings I entered through the GNOME Users & Groups managers did not seem to take, so I ran it from the command line and received the same error while trying to give a user administrative privileges.

```
(users-admin:2267): Liboobs-CRITICAL **: oobs_group_add_user: assertion `OOBS_IS_GROUP (group)' failed
```

It would be nice if the GUI would be candid with me and pop up saying, "I failed in the assignment you gave me."

The command line options for user management I find utterly confusing. This does not seem to accomplish what I intended, which was to give user obicho administrative rights:

```
sudo usermod -g admin obicho
```

typing id obicho yields:
```

uid=1000(obicho) gid=115(admin) groups=115(admin),4(adm),20(dialout),21(fax),24(cdrom),25(floppy),26(tape),29(audio),30(dip),44(video),46(plugdev),106(fuse),107(lpadmin),120(sambashare)
```

That is, obicho is a card-carrying member of admin. But is he? I will try to log in as him and see if he can really sudo.

---

### Post by Braytonio on 2010-01-22
Additional note: The user and session control icons on the right-hand side of the top panel, when clicked, display no options, such as Log Out or Restart or the status of the user.

---

### Post by keylog on 2010-01-22
When i update my ubuntu again, privileges are solved but still new kernels boots up too late :(

---

