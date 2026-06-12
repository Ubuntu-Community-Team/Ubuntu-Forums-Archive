---
title: "Transferring Tomboy Notes to new Computer"
date: 2010-09-28
forum: Installation &amp; Upgrades
---

### Post by Tootler on 2010-09-28
I have a new computer and have successfully installed Ubuntu Lucid on it. I had all my data backed up on an external HDD together with my Firefox profile and bookmarks, so have successfully retrieved all these.

However I completely forgot about Tomboy notes. I still have my old computer so I can retrieve them. I have found that the notes are on ~/.local/shared/tomboy.

To hopefully save myself wasting too much time as I will have to reassemble the old computer, if I transfer the ~/.local/share/tomboy folder to the new computer, will that transfer the notes from the old one OK or is there another file or folder that I will need to transfer as well - a configuration file, for example?

---

### Post by Mze on 2010-09-28
copying the ~/.local/share/tomboy should do it.

contains all your previous notes. no other config option files required.

---

### Post by Tootler on 2010-09-28
Worked fine. You need to reboot but once you do the notes were all in Tomboy.

Thanks.

Geoff

---

### Post by Tootler on 2011-03-16
> **Tootler said:**
> Worked fine. You need to reboot but once you do the notes were all in Tomboy.

Thanks.

Geoff

I have now also synchronised my tomboy notes with Ubuntu One. Very useful extra backup.

---

### Post by kaspin on 2011-05-11
[FONT="Comic Sans MS"][SIZE="2"][SIZE="3"][COLOR="Blue"]There's a bug (which has been reported) in Tomboy under Ubuntu 11.04. If you select a file to delete, it actually deletes the one BEFORE it in the file list! Unfortunately, you cannot recover it as you could previously (~/Tomboy/backup...) as the directory no longer exists. If anyone knows how to recover deleted files in the new version I would be very grateful to know. In the meantime, I will try to find the answer myself. 
kaspin[/COLOR][/SIZE][/SIZE][/FONT]

---

### Post by Tootler on 2011-05-12
You can create your own tomboy backup.

Further up this thread gives the location of tomboy notes as ~/.local/share/tomboy

Copy this directory to some other location ~/Tomboy/backup will do but it is better if you copy it to an external drive so you can recover if other things go wrong.

Keep the backup up to date so you can quickly copy it back to the tomboy directory if you make a mistake. I also sync my tomboy notes with ubuntu one, though an accidently deleted note will get removed when you next sync. Syncing with ubuntu one is useful if you have tomboy notes on more than one computer so you can keep them synced on both computers.

Cheers

Geoff

---

