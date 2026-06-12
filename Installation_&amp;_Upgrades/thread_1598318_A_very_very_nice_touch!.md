---
title: "A very very nice touch!"
date: 2010-10-16
forum: Installation &amp; Upgrades
---

### Post by irv on 2010-10-16
This was the 6th install I did since 10.10 was released. So far I had no real problems with any of the installs. I do have a couple of questions on the last install I did. First, I did an install on my old desktop last night and it is a no name computer that I bought at a yard sale for a quarter. I had XP and Ubuntu 10.04 already installed on it. I did the install a little different this time. First I didn't really have any data on it that I needed, (I do all my main computer work on my laptop). So I did a clean install from the CD but this time I took the last option and picked the partitions I wanted to install on. For example, I used the same partition 10.04 was install on and the same swap partition 10.04 used. I did not have a separate home partition so I thought it would just create a new one. This was not the case. When I finish the install all my data and setting were still in tack in my home directory. I was really surprised. If this is the case, I plan on doing this type of install on all my computer next time.
When I booted up for the first time the thing that jumped out at me was I had the same wallpaper. 
Now for the questions: Why did this happen? Does installing this way (when you already have Ubuntu installed) just keep the old /home/user name/ if you install with the same user name?
Nice touch.

---

### Post by Rocket2DMn on 2010-10-16
Normally when you install on an existing partition, it wipes out everything that is there by formatting it. I suppose it is possible that you told it not to format the partition.
When you say home partition, you are implying that there is a separate hard drive partition that mounts to /home. Separate drive partitions like that are not created automatically during install - if you don't create the separate partition yourself, the /home directory is just created on your root partition with everything else (except swap). In your case it sounds like you have the following partitions: Windows (NTFS), Ubuntu Linux (ext3 or ext4), and a swap partition. Do you actually have a separate /home partition?

---

### Post by kutalion on 2010-10-16
Oh, lol. I made once the same installation you did and I was expecting to end up with something like the folder Windows.Old like it did back in the MS days but I was really impressed after I saw all my stuff there. The catch is that you have to leave the partition without formating it. As you install it says that it would delete many of the folders but nothing is said about /home, right? Anyway I don't see why you didn't directly updated. You could do it directly from the CD through Package Manager.

---

### Post by irv on 2010-10-16
> **Rocket2DMn said:**
> Normally when you install on an existing partition, it wipes out everything that is there by formatting it. I suppose it is possible that you told it not to format the partition.
When you say home partition, you are implying that there is a separate hard drive partition that mounts to /home. Separate drive partitions like that are not created automatically during install - if you don't create the separate partition yourself, the /home directory is just created on your root partition with everything else (except swap). In your case it sounds like you have the following partitions: Windows (NTFS), Ubuntu Linux (ext3 or ext4), and a swap partition. Do you actually have a separate /home partition?
NO that the funny part, I had my home on the main / partition. One NTFS one ext4 and a swap partition.

---

### Post by irv on 2010-10-16
> **kutalion said:**
> Oh, lol. I made once the same installation you did and I was expecting to end up with something like the folder Windows.Old like it did back in the MS days but I was really impressed after I saw all my stuff there. The catch is that you have to leave the partition without formating it. As you install it says that it would delete many of the folders but nothing is said about /home, right? Anyway I don't see why you didn't directly updated. You could do it directly from the CD through Package Manager.

That's the way I usually do it (upgrade from the package manager), but seeing I didn't really have any thing I wanted to save, I thought I would just do a clean install.
Now that it was mention, I don't remember it asking to format anything when I installed, but it did say something to the effect that that data would be lost if I continued. Seeing I have done so many installs this past week, I can't be 100% sure this last install was where I saw it.

---

### Post by zuerston on 2010-10-16
> **irv said:**
> That's the way I usually do it (upgrade from the package manager), but seeing I didn't really have any thing I wanted to save, I thought I would just do a clean install.
Now that it was mention, I don't remember it asking to format anything when I installed, but it did say something to the effect that that data would be lost if I continued. Seeing I have done so many installs this past week, I can't be 100% sure this last install was where I saw it.


Sounds like a great feature to add to Ubuntu! if it is true.

---

### Post by arpanaut on 2010-10-16
From a discussion in the Maverick Dev forum last round, a slightly different view of the install/upgrade process.

[http://ubuntuforums.org/showpost.php?p=9933073&postcount=11](http://ubuntuforums.org/showpost.php?p=9933073&postcount=11)

I think that "maybe" you did choose to NOT format the / partition...
That's the only way I can see that this happened, 
but I could see this as a possible feature to be included in the future.

---

### Post by zuerston on 2010-10-16
> **arpanaut said:**
> From a discussion in the Maverick Dev forum last round, a slightly different view of the install/upgrade process.

[http://ubuntuforums.org/showpost.php?p=9933073&postcount=11](http://ubuntuforums.org/showpost.php?p=9933073&postcount=11)

I think that "maybe" you did choose to NOT format the / partition...
That's the only way I can see that this happened, 
but I could see this as a possible feature to be included in the future.


Yes a little check box to tick in install to **keep old user** ,and it does everything,even the necessary backup to a file,completely automatic upgrade in one click!
:P

---

### Post by irv on 2010-10-16
> **arpanaut said:**
> From a discussion in the Maverick Dev forum last round, a slightly different view of the install/upgrade process.

[http://ubuntuforums.org/showpost.php?p=9933073&postcount=11](http://ubuntuforums.org/showpost.php?p=9933073&postcount=11)

I think that "maybe" you did choose to NOT format the / partition...
That's the only way I can see that this happened, 
but I could see this as a possible feature to be included in the future.
Thanks for this link, This is what I must have done, but did it without knowing I did it.
I don't believe I will ever do an upgrade again knowing what I know now. Still a very very nice touch.

---

### Post by arpanaut on 2010-10-16
The major downside to this method is having to reinstall all of the personally installed stuff.
Major upside is the preservation of /home w/out having to have a separate part. for it.
If one has a large number of additional or specialized programs installed then standard upgrade may be best.

Personally my installs do not deviate from the standard install that much and it is rather easy to restore as I like after a fresh install, preservation of /home is foremost.  Of course this is possible from other backup methods.

I was just throwing this out there as a different perspective.  Standard Upgrade should suffice for most users, other than time and bandwidth issues.  Gotta love torrents!  Alternate CD offers similar upgrade options to upgrade from CD image rather than online.

Different Strokes for Different Folks...

---

### Post by irv on 2010-10-16
> **arpanaut said:**
> The major downside to this method is having to reinstall all of the personally installed stuff.
Major upside is the preservation of /home w/out having to have a separate part. for it.
If one has a large number of additional or specialized programs installed then standard upgrade may be best.

Personally my installs do not deviate from the standard install that much and it is rather easy to restore as I like after a fresh install, preservation of /home is foremost.  Of course this is possible from other backup methods.

I was just throwing this out there as a different perspective.  Standard Upgrade should suffice for most users, other than time and bandwidth issues.  Gotta love torrents!  Alternate CD offers similar upgrade options to upgrade from CD image rather than online.

Different Strokes for Different Folks...

I agree with your last statement, but did you read the link to the other thread in post #7. I found it very good.

---

### Post by arpanaut on 2010-10-16
> **irv said:**
> I agree with your last statement, but did you read the link to the other thread in post #7. I found it very good.


Absolutely! That's why I linked it here. :)
I didn't know that was possible from the Live-CD
I have a laptop that I am going to try this method on soon.
I've just got to make some backup images before I begin... 

Getting in a few more rounds of golf before winter is more of a priority right now!
:biggrin:

---

