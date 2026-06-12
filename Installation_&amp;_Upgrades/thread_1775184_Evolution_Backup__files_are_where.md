---
title: "Evolution Backup / files are where?"
date: 2011-06-04
forum: Installation &amp; Upgrades
---

### Post by geidorei on 2011-06-04
Hi - need to backup data for Evolution - have looked on forums but says data is stored in home/username/.evolution - using 11.04, it isnt there, obviously has been moved on this release.

Any ideas folks?

Karl

---

### Post by mörgæs on 2011-06-04
Have you tried 

```
ls -a
```

while standing in home/username/?

---

### Post by 73ckn797 on 2011-06-04
If you have ever created a backup from Evolution this is the file name it creates: ```
evolution-backup.tar.gz
```
Search for this, if you have backed up manually before.

---

### Post by geidorei on 2011-06-04
yes - have looked for the hidden directory, not there - and want to backup the directory where it stores info, saves me faffing about doing a backup from evolution.

---

### Post by geidorei on 2011-06-04
Ahha found where all data is stored, as follows for those of you looking:

- User data: ~/.local/share/evolution
- Config files: ~/.config/evolution
- Data cache: ~/.cache/evolution

So main areas to back up are User data and Config.

---

### Post by 73ckn797 on 2011-06-04
> **geidorei said:**
> Ahha found where all data is stored, as follows for those of you looking:

- User data: ~/.local/share/evolution
- Config files: ~/.config/evolution
- Data cache: ~/.cache/evolution

So main areas to back up are User data and Config.

Using Evolution to back up data stores it in the file I referred earlier. You can tell it where to store it. All necessary information is assembled in the one file.

---

### Post by geidorei on 2011-06-04
> **73ckn797 said:**
> Using Evolution to back up data stores it in the file I referred earlier. You can tell it where to store it. All necessary information is assembled in the one file.

Yep, sounds good to me - however, doesnt really help what I need to do as I require the backup to be included in the automated process to the NAS and not producing the tar file manually. If you were able to schedule the tar to be produced that would do the job.

---

### Post by tomb@ibcos.co.uk on 2011-07-11
@geidorei,

Many thanks for finding the location of the data files! My OS drive had failed and I needed to extract the raw files so no backup option through Evolution was possible.

Morel of the story... always do backups!

---

### Post by fonsi2099 on 2011-07-13
I can not open Evolution, is thre any way to fix that: 

-HP-Pavilion-dv5-Notebook-PC:~$ evolution

(evolution:4971): GLib-GObject-CRITICAL **: Object class EMFolderTree doesn't implement property 'paste-target-list' from interface 'ESelectable'

(evolution:4971): GLib-GObject-CRITICAL **: Object class EMFolderTree doesn't implement property 'copy-target-list' from interface 'ESelectable'
e-data-server-ui-Message: Unable to find password(s) in keyring (Keyring reports: No matching results)
e-data-server-ui-Message: Key file does not have group 'Passwords-Mail'
e-data-server-ui-Message: Unable to find password(s) in keyring (Keyring reports: No matching results)
e-data-server-ui-Message: Key file does not have group 'Passwords-Mail'

(evolution:4971): camel-local-provider-WARNING **: Summary doesn't match the folder contents!  eek!
  expecting offset 0 got -1, state = 8

(evolution:4971): camel-local-provider-WARNING **: Summary doesn't match the folder contents!  eek!
  expecting offset 0 got -1, state = 8

(evolution:4971): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed
**
camel:ERROR:camel-mime-message.c:627:camel_mime_message_get_subject: assertion failed: (mime_message)
Aborted

Thank you

---

### Post by Johey on 2011-12-19
Did you find a solution to the assert crash? I produce exactly the same assert by trying to open an email in my inbox.

I have been messing with evolution by trying to copy the configuration directories from another installation, but that did not succees, so I have tried to remove all those files and create new email account settings. It still crashes, however.

Evolution 2.32.2

```
(evolution:4631): GLib-GObject-CRITICAL **: Object class EMFolderTree doesn't implement property 'paste-target-list' from interface 'ESelectable'

(evolution:4631): GLib-GObject-CRITICAL **: Object class EMFolderTree doesn't implement property 'copy-target-list' from interface 'ESelectable'

(evolution:4631): camel-local-provider-WARNING **: Summary doesn't match the folder contents!  eek!
  expecting offset 0 got -1, state = 8

(evolution:4631): camel-local-provider-WARNING **: Summary doesn't match the folder contents!  eek!
  expecting offset 0 got -1, state = 8

(evolution:4631): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed
**
camel:ERROR:camel-mime-message.c:627:camel_mime_message_get_subject: assertion failed: (mime_message)
```

---

### Post by fonsi2099 on 2011-12-19
now jump to Thunderbird, it works very fine
:guitar:

---

