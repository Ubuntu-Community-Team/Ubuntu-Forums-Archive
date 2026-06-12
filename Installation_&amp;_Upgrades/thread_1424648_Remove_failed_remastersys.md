---
title: "Remove failed remastersys"
date: 2010-03-08
forum: Installation &amp; Upgrades
---

### Post by Nick Brohman on 2010-03-08
I have a block of 85 GB of a failed remastersys back-up and it is preventing me from up-dating my OS.

What do i do to remove this from my HD ?

---

### Post by zvacet on 2010-03-08
If it is folder then delete it.You can use rm command from terminal but be careful with that.Read [this]("https://help.ubuntu.com/community/Beginners/BashScripting") **twice** before use command.If you made partition for remastersys then delete that partition with Ubuntu live CD or with [Gparted live CD.]("http://gparted.sourceforge.net/")

---

### Post by Nick Brohman on 2010-03-08
Thank you, it looks like I'll have to take this slowly...

How do I determine if it is a folder ?

I'm not computer savvy, yet.

[B][I]I should have said that I read the link in the above post, twice and used the rm command only to be told that remastersys does not exist, yet I have seen it in the files in my home directory.

I did not create the remastersys partition, just followed instructions....as it stands now, I won't be up-grading to any other Ubuntu until this problem is resolved.[/I][/B]

---

### Post by Nick Brohman on 2010-03-08
G'day again, 

This thread might give you background to my problem, it is going on 5 mths now & help, which I thought I would have before Christmas, has not arrived....I'm still booting with 2.6.31.14 kernel and have stopped taking all updates....

[http://ubuntuforums.org/showthread.php?t=1319929](http://ubuntuforums.org/showthread.php?t=1319929)

---

### Post by Nick Brohman on 2010-03-09
> **zvacet said:**
> If it is folder then delete it.You can use rm command from terminal but be careful with that.Read [this]("https://help.ubuntu.com/community/Beginners/BashScripting") **twice** before use command.If you made partition for remastersys then delete that partition with Ubuntu live CD or with [Gparted live CD.]("http://gparted.sourceforge.net/")

Thank you, read the link, twice, used the rm command & was told that no such file exists.

I have found it in the file system in my home folder.

i did not create a partition, I just did as told by remastersys and ended up with a failed back-up......3 days later, i read that remaster doesn't work with the koala.....that was news to me.

I don't fully understand how to partition, yet...

---

### Post by Nick Brohman on 2010-04-20
This is the instruction I received by e-mail and it was this terminal command that removed the remastersys for me......I sent screenshots to the one person who has understood my problems.....

> From the screenshot it is evident that remastersys is a folder and not a partition. That's good news. If you can't simply right-click the folder and move it to the trash or delete it, the problem is almost certainly a 'permission denied' error. If you see any other error message take a screenshot for me. Otherwise go to a console terminal and type this EXACTLY:

**sudo rm -rf /home/remastersys**

As you can see in your last screenshot, you were attempting to delete /home/nicko/remastersys when the correct path is actually /home/remastersys.

Additionally you must use the -r option or else rm will only delete files contained in the remastersys folder but will not delete the contents of any folders contained therein.

The -r stands for recursive. We're learning now - isn't this fun? :)
The -f option stands for force and basically means to ignore errors such as bad file names or timestamps and just keep soldiering on.

---

