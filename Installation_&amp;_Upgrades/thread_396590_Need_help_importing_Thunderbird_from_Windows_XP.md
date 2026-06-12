---
title: "Need help importing Thunderbird from Windows XP"
date: 2007-03-29
forum: Installation &amp; Upgrades
---

### Post by explorer716 on 2007-03-29
In Windows XP I opened Thunderbird and exported my messages to a folder I named "Tmail Ubuntu" created in "My Documents". The computer named the file with the messages, "Local Folders".

Then I went to Ubuntu and opened Thunderbird and imported the "Local Folder" file to my profile. It asked if I wanted to replace the existing folder with the one I was importing and I answered yes.

I closed out and reopened Thunderbird. On the left of the main Thunderbird screen I had a column with the mail folder I imported. However, they are empty. Also, I cannot receive email.

I am getting this error message, "Unable to write the email to the mailbox. Make sure the file system allows you write privileges and you have enough disk space to copy the mailbox."

I did something very similar to the above steps to move my contacts from Windows Xp to Ubuntu without any problems. I assumed incorrectly it would work for messages too. Woe is me.

I am very new to Ubuntu and your assistance in correcting this problem will be appreciated

---

### Post by Rui Pais on 2007-03-29
Hi.
maybe thunderbird have overwrite it's local folder (instead of copy) with the one you got from Windows, that maybe would keep the windows permissions set. 

Open the folder "Tmail Ubuntu" inside ubuntu and check if you have permission to write on it.

You can try the following, Remove the actual broken profile. Make a copy of "Tmail Ubuntu" inside linux to make sure that everything belongs to you (as user). 

Here how. 
Open a terminal and copy paste:
```

sudo rm -rf .mozilla-thunderbird
cp 'Tmail Ubuntu' Tmail2 

```
Redo the import process.

hth

---

