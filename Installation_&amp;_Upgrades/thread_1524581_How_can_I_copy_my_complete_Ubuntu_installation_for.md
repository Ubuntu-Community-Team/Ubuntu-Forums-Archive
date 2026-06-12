---
title: "How can I copy my complete Ubuntu installation for a friend?"
date: 2010-07-05
forum: Installation &amp; Upgrades
---

### Post by MountainX on 2010-07-05
I need some advice about cloning a HDD.

I'm planning to clone my system to a friend's computer. We have identical hardware (including the same HDD's). I have prepared a clone of my fresh install to use as the source. Before doing the clone, I need to do a few more tweaks to the configuration. Then I want to delete all the unneccessary stuff.

I know I can delete .bash_history. What other files can I remove without losing any actual configuration info?

I can remove the history in firefox via the GUI, but is there a file I can just delete (while keeping the profile, the bookmarks, etc.).

I want to keep all config info (including anything I set such as bookmarks). I do not want to keep the history or cache.

Which files can I delete? Thanks.

(In case you are wondering why I don't use remastersys or something similar, I have looked at several options and so far my opinion is that cloning [or maybe copying] the disk fits our needs the best.)

---

### Post by anieruddha on 2010-07-05
check for remastersys backup. Following link might help u
[http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html](http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html)

---

### Post by MountainX on 2010-07-05
> **anieruddha said:**
> check for remastersys backup. Following link might help u
[http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html](http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html)

Did you read my post? remastersys is cool, and I'm sure others will appreciate the link, but you didn't even reply to my question.

---

### Post by ajgreeny on 2010-07-05
Clonezilla is also good for the cloning part of the job, but as to what you can remove, there will be a lot of personal data and information in your home folder or partition which you may wish to keep away from your friend, and he will of course, need to make a user for himself.  That will be much easier to do if you keep your user until that is done, as otherwise there will be no admin user and everything will have to be done as root in recovery mode; possible but more difficult if you don't know much about the cli.

So I suggest you clone your system with one or other of the two apps suggested, then you, personally, transfer the clone to your friend's computer, make a new user, with admin rights for him, then with his new admin user, delete everything from your old user home folder, and remove the old user, ie, you.  I would not feel too happy passing over all the files and folders from my user to another person, but of course, that's your choice.   As for firefox, you can choose what is removed from the personal data when you choose Tools->Clear Recent History.  I think it might be safer and more sensible to set up the new user, and then just allow him to use the .json file of your bookmarks backup from your old profile.

That should be fine as far as I can see, but wait for other responses before you do this, as I may have forgotten something of great importance, knowing me and my memory.

I hope that answers some of your questions, and that even if you don't do exactly what I've said, it may have given you some food for thought.

---

### Post by CharlesA on 2010-07-05
Creating a new user and deleting your user and home directory would be the best way to go about it.

As for cloning drives, I use clonezilla. :)

---

### Post by MountainX on 2010-07-05
Note: We are keeping the same user. We want to keep all the configurations for that user. 

But I want to delete the history and cache and MRU (most recently used). Those will all contain stuff from setting up the system, so I just want to get rid of it. Anyone know what I can get rid of that does not delete any settings or configuration info?

Why are we doing it this way? The user account is a generic user and it will be reused by the new person. There is a bunch of customization for this user account such as bookmarks, mouse cursor settings, theme, startup applications, etc. That is exactly what I do not want to have to recreate. Therefore, I cannot just delete the home folder.

---

### Post by MountainX on 2010-07-09
One of the things I need to do is this:

```
rm ~/.recently-used.xbel
```

(from [http://www.watchingthenet.com/ubuntu-tip-clear-disable-recent-documents.html](http://www.watchingthenet.com/ubuntu-tip-clear-disable-recent-documents.html))

Where else is history stored?

And what about logs? Which log files can I delete without causing any harm?

---

