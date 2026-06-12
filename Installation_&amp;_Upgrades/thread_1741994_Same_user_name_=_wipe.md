---
title: "Same user name = wipe"
date: 2011-04-28
forum: Installation &amp; Upgrades
---

### Post by pszpak on 2011-04-28
This is a hard way to learn.

If you have a separate /home partition and do the "other" install in 11.04 and then chose to create a user name that already exists it will wipe out the older user and their data with the same name. 

I guess that makes sense (now), but don't you think a warning like user name detected or you are about to delete an entire directory structure would be kind to the neophyte? I mean, it asks about windows users for imports...would it not be possible to check for existing users on /home?

Of course now I know to just proceed without a new user since the old user is present. But I learned that at the cost of /home and a lot of data and settings. Perhaps a simple check to see if you've entered the exact same name as already exists would be useful.

---

### Post by zvacet on 2011-04-28
If it is not only you it´s good to know and you are right there should be some kind of message for that.But I didn´t notice that,because I use admin user just for install/upgrades,so I don´t have files/settings there.I made second account for everyday work and there is place where I save what I need.Other way is to have just root and backup partition and then sync them.

---

### Post by Derek Karpinski on 2011-04-29
Going to install 11.04 this weekend.  I'm not going to upgrade.  I'm going to install 11.04 over 10.10, but not format my /home dir.
 
Can someone confirm that if I set up with the same user name, I'll lose my home?:o

---

### Post by ottosykora on 2011-04-29
how should any system know the user1 is not the same as user1?

But it also kind of depends on how all ins installed.

I do partition all by hand, set the partition by hand to /home and just enter exactly same user and same pw etc. The user is kind of not created again in this case. And also select hat the partition has NOT to be formated!!!
If you do all install automatic, well it wants format all , and then many thing may be lost for ever.

This will probably work only if you have one system using the home partition, some people tried to use same home partition, with same user by two different root prts, this must lead to confusion sooner or later.

---

### Post by Derek Karpinski on 2011-04-29
Just a suggestion:
 
-If you're not formatting /home, and you set up the same user name as what's already installed, have a warning dialog pop up and say you will lose all data in /home.
 
-Better yet, if you enter the same user name and you're not formatting /home, ask if you'd like to merge your old home with the new home.
 
Given the problems with updating, doing a clean install seems the best way to go.  I suppose backing up /home to an external drive or USB stick and dumping everything back into the clean home is the way to go.  Although this seems counter-intuitive given the OP consciously made a choice NOT to format /home thinking he was protecting his data.  Besides, who wants to change user names every install? And then you'd have to move everything from your old username /home to the new username /home.:confused:

---

### Post by Derek Karpinski on 2011-04-29
> **ottosykora said:**
> how should any system know the user1 is not the same as user1?
 
But it also kind of depends on how all ins installed.
 
I do partition all by hand, set the partition by hand to /home and just enter exactly same user and same pw etc. The user is kind of not created again in this case. And also select hat the partition has NOT to be formated!!!
If you do all install automatic, well it wants format all , and then many thing may be lost for ever.
 
This will probably work only if you have one system using the home partition, some people tried to use same home partition, with same user by two different root prts, this must lead to confusion sooner or later.
 
Are you suggesting the OP had checked the 'format' box of his  /home dir?  He did have a separate /home partition.

---

### Post by pszpak on 2011-04-30
Just for clarity.

If you have /home on a separate partition I believe you do not  have to create a new user (since it is already there and will be detected). This is not clear though on the installation dialogue. 

Or you can just create another user like admin, and all your settings will still be there when you log in with your old user name and password.

---

### Post by Hedgehog1 on 2011-04-30
> **Derek Karpinski said:**
> Going to install 11.04 this weekend.  I'm not going to upgrade.  I'm going to install 11.04 over 10.10, but not format my /home dir.
 
Can someone confirm that if I set up with the same user name, I'll lose my home?:o

This is what I did on my main PC, and it went very smoothly.  it also gave me the 'spring cleaning' in the '/' directory I have been meaning to do...

You will not lose your '/home' directory or data by using the same user name - UNLESS you format the '/home' partition.  Worst case you might have to do a 'chown' if the internal ID of the new user is different from the old one.

However - backing up your data before any install or large upgrade is **ALWAYS** a very good idea.

**The Hedge**

:KS

---

### Post by zvacet on 2011-04-30
> You will not lose your '/home' directory or data by using the same user name - UNLESS you format the '/home' partition.

Exactly.That way I install,reinstall,upgrading,.... for years and never had a problem.

---

### Post by ottosykora on 2011-04-30
>Are you suggesting the OP had checked the 'format' box of his /home dir? He did have a separate /home partition.<

well have no idea what he did exactly, but last time I did a reinstall, I noticed that the installation wanted to format the partition and I had to confirm again, no, I do not want format,
So if he just went on, click ok, ok, ok.. then probably the partition was formated by that.
I would think in that case, the installer is kind of too strange and thinks formating is best. Well yes, might be if there nothing on the drive, but I prefer to create and format volumes to my taste and as the installer wants it. 

I have files, settings for gnome and lot of other things remaining in the /home partition when reinstalling and using exactly same name as used before. Do that often.

---

### Post by Nesaskewatch on 2011-05-01
So just to clarify all this...  If one follows the instructions listed at Hedge's comment #4 [here]("http://ubuntuforums.org/showthread.php?p=10750566#post10750566") everything *should* go just fine, correct?

Will the installer still ask for a user name and password if "Format Partition" is _un_checked on the /home drive screen?  If it does, and one simply re-enters their user name and password, it will retain all the settings, data etc in the previous /home partition, yes?

Like I said.  I just want to add these details should anyone else stumble in here like I did, looking for instructions on how to do a clean re-install over an existing Ubuntu OS with a separate /home partition.  Hedge's mini pictorial "how to" at the above link is nice, short, simple and informative.  It only lacks the issues raised in this thread.

Thanks very much!

---

### Post by zvacet on 2011-05-01
Instructions are correct,but picture is confusing.Above picture you see big warning letters how not format /home partition and on picture it is checked.If you don´t want format /home uncheck **format the partition**.

> Will the installer still ask for a user name and password if "Format Partition" is unchecked on the /home drive screen? If it does, and one simply re-enters their user name and password, it will retain all the settings, data etc in the previous /home partition, yes?

That is right.It will ask for username and password and just re-enter your user name and password,and you will have your settings saved on separate home partition.

---

### Post by Nesaskewatch on 2011-05-26
I just thought I would add that this procedure worked perfectly!  The installer does ask for a user name and password, and I simply entered the same one again and voila.  Thanks for the great advice.

---

