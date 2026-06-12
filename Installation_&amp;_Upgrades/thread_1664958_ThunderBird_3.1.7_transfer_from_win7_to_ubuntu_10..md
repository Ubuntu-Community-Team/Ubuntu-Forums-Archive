---
title: "ThunderBird 3.1.7 transfer from win7 to ubuntu 10.04"
date: 2011-01-11
forum: Installation &amp; Upgrades
---

### Post by jao_madn on 2011-01-11
Hi i would like share what i did when i migrate my ThunderBird 3.1.7 including (extensions, calendar, settings, addressbook) windows 7 to ubuntu 10.04. 1. Archive(7zip) the mail database or the thunderbird folder in the windows 7 which is in the location (C:\Users\(Ur Username)\AppData\Roaming\)  2. Install the TB on your linux and open it to create the ****.default folder and the profile.ini in the home/.thunderbird/* Note: althought your windows thunderbird archive backup has the ****.default and profile.ini it doesn't work in my case when i replace or put it the the home/.thunderbird/* directory 3. When you open the TB in the first time it will create *****.default and profile.ini, dont replace or delete it as i said above, what you must do is copy all the files or content in the directory of ****.default in the windows 7 backup archive which is in location (/Thunderbird/Profiles/.default/*) to the home/.thunderbird/ all of it but first remove the content of your ******.dafault and now its almost finish 4. Start ur TB and its ok Note: In my case the lightning calendar doesn't sync to google i reinstall my lightning and provider of google extension before it work.  I think this is the 5th time i migrate my TB mail from windows xp to 7 to linux..

---

### Post by oldfred on 2011-01-11
You can copy & paste the entire profile ***.default, but then have to edit profile.ini to use the new default.

I share my Thunderbird & Firefox profiles between XP & Ubuntu and have for about 4 years. I also copy entire profile from Desktop to portable. Once I reset profile.ini on portable I just have to copy entire default. Then when done traveling with portable, I just copy profiles back to desktop.

[http://support.mozillamessaging.com/en-US/kb/Profiles](http://support.mozillamessaging.com/en-US/kb/Profiles)
[http://www.mozilla.org/support/thunderbird/profile](http://www.mozilla.org/support/thunderbird/profile)

---

### Post by jao_madn on 2011-01-13
@oldfred: Thanks for additional info..

---

### Post by wkulecz on 2011-01-13
Wouldn't this make a lot of sense to keep your master profile on the cloud (Ubuntu One perhaps?) and then sync the local machines to it as needed.  Kind of an Email analog of how Xmarks lets me get my bookmarks anywhere I need them.

I've moved Thunderbird from Windows to Ubuntu for my wife several years ago using the method oldfred described.  I seem to recall encountering a nasty bug once her mailbox exceeded 2 (or 4 can't recall offhand) GB and had to split things up into sub-folders.

---

### Post by jao_madn on 2011-01-13
I also realize that very importants of the security of my system because if your machine is compromise and bad guys download all your mail database and then use the procedure mention above then its game over for all your emails..since when i did this procedure there no need to configure again the  password of my in/out email transactions.

---

