---
title: "Partitioning Problems.."
date: 2007-02-13
forum: Installation &amp; Upgrades
---

### Post by mancel on 2007-02-13
I'm a complete noob to any Linux based OS..
I hope you guys can help me.

I have 2 harddrives in my computer, a 74gb and a 160gb.
The 74 has winblowsxp and the 160 is clean fresh.
Here's my problem:
I want to put Edgy on the 160 and leave the 74 completely untouched.  But, I also want to keep most of the 160 in ntfs for winblows file storage.  I do graphic design so I originally bought the 160 for that storing that stuff.  But I don't think I'll be filling the whole drive up any time soon so I want to try Ubuntu.
So I tried to partition it to how I thought would work and I've looked all over the place on how to do this but I'm starting to get frustrated.

This is how i have it partitioned:
(i realized i had the 10gb root partion as ntfs after i took the screenshot.. i changed it to ext3 but it does the same thing as shown in the second screen.)
[http://i20.photobucket.com/albums/b209/mancel/ss2.png]("http://i20.photobucket.com/albums/b209/mancel/ss2.png")

and this is how i'm trying to mount things:
[http://i20.photobucket.com/albums/b209/mancel/ss.png]("http://i20.photobucket.com/albums/b209/mancel/ss.png")

I appreciate any help you can give.

---

### Post by Kateikyoushi on 2007-02-13
Did you try to click the forward button ? Isn't that warning always there ?
I would try to erase the partitions and start it over if still no go because the second screenshot seems okay.

---

### Post by Fahuadai on 2007-02-13
You're on the right path. The way I have my laptop partitioned is that I have Windows on one partition, ubuntu on another, then the third partition formatted in ext3 which i use as my /home and My Documents for linux and windows to share. 

This is done using this program:  [www.fs-driver.org]("http://www.fs-driver.org")

Hope this helps. 

Have fun.

---

### Post by mikewhatever on 2007-02-13
It is probably asking you to mount the fourth partition. The mount point can be something like /media/sdb4.

---

### Post by mancel on 2007-02-13
> **Kateikyoushi said:**
> Did you try to click the forward button ? Isn't that warning always there ?
I would try to erase the partitions and start it over if still no go because the second screenshot seems okay.
Yeah, that's actually the result of clicking Forward.  And I've tried starting over and over again but it's not working for me. :/


> **Fahuadai said:**
> You're on the right path. The way I have my laptop partitioned is that I have Windows on one partition, ubuntu on another, then the third partition formatted in ext3 which i use as my /home and My Documents for linux and windows to share. 

This is done using this program:  [www.fs-driver.org]("http://www.fs-driver.org")

Hope this helps. 

Have fun.
I really want to keep all Windows and Ubuntu files separate though.  Maybe I'm just being picky..


> **mikewhatever said:**
> It is probably asking you to mount the fourth partition. The mount point can be something like /media/sdb4.
I tried that too but it brought up yet another field like it wants me to include my 74gb..


---

Thanks for the replies so far guys.

---

### Post by mancel on 2007-02-13
I think, for some reason, the 10gb ext3 root partition is being seen as an ntfs.  Whenever I click the back button from the mount window it shows all the partitions and the 10gb partition is showing up as being ntfs..  This is really bugging me. :mad:

---

### Post by Methodize on 2007-02-13
hey, i hope you don't mind but this thread seems to be a good place to post about my problem as well.

I have a 80GB hard drive and run windows on it.
I also have a 320 GB external hard drive for storage. and I'm only using about 30 gigs of it. I recently tried to install Ubuntu on it and when i was asked how i wanted to partition it i mistakenly made a 100GB partition for Windows. and a 220 GB for Ubuntu. what i wanted was the opposite. 100 for Ubuntu and 220 for Windows.
To top it all off it didn't finish correctly, so i was left with no Ubuntu and an incorrectly partitioned hard drive. so i have 2 questions.

How do i fix the partitions so that i have 220GB for windows and 100 for Ubuntu?
How do in install Ubuntu on an external hard drive.

thanks ahead of time!

---

### Post by Kateikyoushi on 2007-02-13
> **mancel said:**
> I think, for some reason, the 10gb ext3 root partition is being seen as an ntfs.  Whenever I click the back button from the mount window it shows all the partitions and the 10gb partition is showing up as being ntfs..  This is really bugging me. :mad:

I thought so that's why I said erase the partitions and start it from scratch again.

---

### Post by Kateikyoushi on 2007-02-13
> **Methodize said:**
> hey, i hope you don't mind but this thread seems to be a good place to post about my problem as well.

I have a 80GB hard drive and run windows on it.
I also have a 320 GB external hard drive for storage. and I'm only using about 30 gigs of it. I recently tried to install Ubuntu on it and when i was asked how i wanted to partition it i mistakenly made a 100GB partition for Windows. and a 220 GB for Ubuntu. what i wanted was the opposite. 100 for Ubuntu and 220 for Windows.
To top it all off it didn't finish correctly, so i was left with no Ubuntu and an incorrectly partitioned hard drive. so i have 2 questions.

How do i fix the partitions so that i have 220GB for windows and 100 for Ubuntu?
How do in install Ubuntu on an external hard drive.

thanks ahead of time!

I would say erase the ubuntu partition and resize the windows partition then start the install again.
You can use gparted to resize the partitions from the live disc.

Remember it is always recommended to do backup of important data before playing with partitions.

---

### Post by mancel on 2007-02-13
> **Kateikyoushi said:**
> I thought so that's why I said erase the partitions and start it from scratch again.
That still wasn't the problem though.  No matter how many times I re-partitioned it it'd always go back to ntfs.  I tried reiser and that worked.
So now it's all installed but I didn't create a partition for /boot so now it boots from my 74gb HD and I can't get into Windows..  Is there any way to move the /boot to my other HD?
I hope i haven't screwed Windows up.
 [-o<

---

### Post by mancel on 2007-02-14
Disregard that last comment.  It's all working fine now.
I'm already in love with Ubuntu..

---

### Post by Methodize on 2007-02-14
> **Kateikyoushi said:**
> I would say erase the ubuntu partition and resize the windows partition then start the install again.
You can use gparted to resize the partitions from the live disc.

Remember it is always recommended to do backup of important data before playing with partitions.
how do i erase the Ubuntu partition?

---

### Post by Kateikyoushi on 2007-02-14
You can use gparted from the ubuntu live disc or can even use the windows system tool to erase it but that can not resize partition so would rather go with the first one.

---

