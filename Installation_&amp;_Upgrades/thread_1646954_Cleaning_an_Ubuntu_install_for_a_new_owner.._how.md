---
title: "Cleaning an Ubuntu install for a new owner.. how?"
date: 2010-12-16
forum: Installation &amp; Upgrades
---

### Post by QwUo173Hy on 2010-12-16
I'm giving my Ubuntu laptop to someone. I don't want a trace of my data or activities on the laptop, but it did take some work to get the wireless working, so a fresh install is not an option.

Besides deleting all the user accounts and their home folders, what else do I need to do?

---

### Post by cogier on 2010-12-16
Why not create a new user at **System>Administration>Users and Groups**. Make sure you copy all that you do want to keep to the new user Home folders and then delete the old user and all the files.

All your data will then be deleted.

---

### Post by QwUo173Hy on 2010-12-16
> **cogier said:**
> Why not create a new user at **System>Administration>Users and Groups**. Make sure you copy all that you do want to keep to the new user Home folders and then delete the old user and all the files.

All your data will then be deleted.

Thanks cogier. Will that really get rid of everything? No logs or history left lying arount the root filesystem for web-browsers or anything?

---

### Post by cogier on 2010-12-16
Well I would not like to promise that there would be nothing there but most, if not all, your data is stored in folders that start with a "." in the Home folder. You can see these hidden folders (and files) by opening the Home folder in Nautilus and then pressing **[Ctrl] + H**.

If browser history is your worry then this will get rid of it. If you are using Firefox the folder is **.Mozilla** in you Home folder.

---

### Post by QwUo173Hy on 2010-12-16
Thank you cogier! I've come across a book called Linux and Unix Security (Hack Notes), and it seems that the log files in /var only contain information about the activities of applications and other users. I'm not that concerned though, and as you say, the browser history will be gone when I delete my ~ directory.

Thanks again,
Jarlath

---

### Post by wojox on 2010-12-16
Check your /tmp directory. Also have a look at [secure-delete]("http://techthrob.com/2009/03/02/howto-delete-files-permanently-and-securely-in-linux/") paying attention to sfill and sswap.

---

### Post by oldfred on 2010-12-16
Just do some normal housekeeping.

# empty trash
# remove log files if no issues
cd /var/log
sudo rm -f messages.*
sudo rm -v /var/log/*.gz

 How To: Disk Full? - Check Your Trash 
[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)

Not sure you need to do any of this:
HOWTO: Cleaning up all those unnecessary junk files...
[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)
    Caution deborphan will delete anything you manually installed. See comment:
Better to use Synaptic to select the ones you no longer want. Also you get notified about dependencies to be removed and can reconsider, if need be.

---

### Post by matt_symes on 2010-12-16
Hi

You could also install Bleachbit and use that to remove history, cache etc.

Kind regards

---

### Post by amauk on 2010-12-16
If you're intending to delete the main user account (the account with sudo access), then add any new user you create to the "admin" & "sudo" groups before you do

Else the new user will not have sudo access

---

### Post by QwUo173Hy on 2010-12-17
Thanks guys, that takes care of it.

---

