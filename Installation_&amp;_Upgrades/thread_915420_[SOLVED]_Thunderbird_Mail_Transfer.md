---
title: "[SOLVED] Thunderbird Mail Transfer"
date: 2008-09-09
forum: Installation &amp; Upgrades
---

### Post by 44tr on 2008-09-09
I want to transfer my Thunderbird Mail Account from my Windows XP install to my Ubuntu install on my dual boot computer.  I can't figure out what files need to be moved and to where since it obviously is not a mirror image.

Can anybody guide me through this?  I AM trying to abandon Windows as much as possible :)

Thanks in advance.

---

### Post by 44tr on 2008-09-10
Any ideas?  Anybody?

---

### Post by fballem on 2008-09-10
All the files in Local Folder and don't forget your address book, which I think is at the same level as Local Folder. That's what worked for me.

---

### Post by 73ckn797 on 2008-09-10
Sure.

In Windows go to "My Computer", "Documents and Settings", "(Your Name)", "Application Data", "Thunderbird", "Profiles", "(code looking name).default", "Mail". Once in there you need to copy all of the directories. They contain all of your email data. Copy that over and into the following in Ubuntu:

Click on "Places" and choose "Home Folder".

Click on "View" and choose "show Hidden Files".

Go to the folder titled ".mozilla-thunderbird".

Go to the sub-folder titled "*.default". The * will be an unusual code looking name. this is where the personal data for Thunderbird resides.

The "Mail" folder is the one you want.

Paste the copied files into there.

You may have to first setup your email info in Thunderbird in Ubuntu (or any other OS). Paste what was copied from Windows and let it overwrite the same named directories.

This works great as I do it a lot.

The email address book will need to be exported from the Windows Thunderbird. Do that in a "comma separated value (csv) format, naming it whatever you wish but keep the csv extension. 

Import that file back into the Thunderbird on Ubuntu.

Presto, you are back up and running again.

---

### Post by cariboo on 2008-09-10
An other way to access your default folder, and the way I do it, is to copy and paste the whole directory into .mozilla-thunderbird then just edit profiles.ini to point to the just pasted directory.

Jim

---

### Post by 44tr on 2008-09-10
> **73ckn797 said:**
> Sure.

In Windows go to "My Computer", "Documents and Settings", "(Your Name)", "Application Data", "Thunderbird", "Profiles", "(code looking name).default", "Mail". Once in there you need to copy all of the directories. They contain all of your email data. Copy that over and into the following in Ubuntu:

Click on "Places" and choose "Home Folder".

Click on "View" and choose "show Hidden Files".

Go to the folder titled ".mozilla-thunderbird".

Go to the sub-folder titled "*.default". The * will be an unusual code looking name. this is where the personal data for Thunderbird resides.

The "Mail" folder is the one you want.

Paste the copied files into there.

You may have to first setup your email info in Thunderbird in Ubuntu (or any other OS). Paste what was copied from Windows and let it overwrite the same named directories.

This works great as I do it a lot.

The email address book will need to be exported from the Windows Thunderbird. Do that in a "comma separated value (csv) format, naming it whatever you wish but keep the csv extension. 

Import that file back into the Thunderbird on Ubuntu.

Presto, you are back up and running again.

I used this idea.  Thanks.  Unfortunately, I can't get Thunderbird to connect to my ISP's email server; it keeps asking for a password but entering the correct one doesn't help.  From Windows it works fine and as far as I can tell, the settings are identical in both. :confused:

I'll keep at it; thanks for help though.

---

### Post by 44tr on 2008-09-10
Ah, I understand now.  My ISP requires the entire email address as the 'username' where Thunderbird defaults to just the prefix before the @ sign.  It works now.  Thanks again everybody.

---

