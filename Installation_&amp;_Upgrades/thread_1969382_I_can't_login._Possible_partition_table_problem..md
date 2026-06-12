---
title: "I can't login. Possible partition table problem."
date: 2012-04-30
forum: Installation &amp; Upgrades
---

### Post by grusty on 2012-04-30
I have this problem at Xubuntu 12.04

1. Trying to install Ubuntu to a friend machine, i download and copy to usb with "dd" comand, because in the last versions in ubuntu/kubuntu & xubuntu the disk creator have many probles and didn't work. I mistake the "if" and "of" in "dd" command.

2. At boot my computer, can't login. Appears the login screen, i writte the password, and go to black and back to login screen.

3. That was at xubuntu 11.10

4. I try usig testdisk from RIPlinux distro. I didn 't know what to do. I read some tutorials, but nothing.

5. I dowload (at my kubuntu netbook) new xubuntu 12.04. But do exactly the same at login screen (after installed)

6. I try with mint xfce debian. But was impossible chosse /home. So, I installed all in the same partition, andd then change at /etc/fstab. It work. But mint was very slow. I decide back to Xubuntu 12.04 an do the same with /home.

7. I installed Xubuntu 12.04 all at same partition, then, I changed in /etc/fstab the /home partition. But at boot, go to login screen and is the same that at morning, I can't login.

My questions:

1. What I did with "dd" command?
2. Perhaps i'll find the way to fix fstab, but when i wan to install the new xubuntu in 6 month, I want to have the same problem, right? (with /home)
3. What I really must do with testdisk? I follow some tutorials but nothing. I dont t know what to change at partition table.
4. Is a partition table problem?

---

### Post by darkod on 2012-04-30
I am not sure this is fixable, even with testdisk. This is why dd is a very dangerous command and should not be used for this. If the start up disk creator has issues, try to solve them, don't just go to dd.

If you tell us the exact dd command you ran, maybe someone will have some idea.

Yes, this looks like a problem with the partition table since dd starts writing immediately from the start of the disk, depending how you used it. The boot sector and the partition table are at the start.

Also, if you run the deer search in testdisk and post a screenshot, we might have some idea.

But since you installed xubuntu again after all this, testdisk might be useless and I don't understand what you want to recover now. If you plan to recover partition you should stop writing anything on the disk, and you decided to install xubuntu.

What is the current problem, you can't use the previous /home partition? Did you have it as separate partition?

---

### Post by grusty on 2012-04-30
Thanks for follow this thread.

Yes "dd" is dangerous. Many pages say how use it to do bootable USB. I did often.

I did this.

dd if=/media/sdbx of=xubuntu.iso
Was a mistake (I forgot the number of sdx)

Then this, was ok.
dd if=xubuntu.iso of=/media/sdbx

Just now, I saw, sdb is my hard disk with /home. Sda is my hard disk with /

I installed Xubuntu 12.04 and can't login. Just at screen to login, i writte my user and password but can't go in.

If i install linux mint xfce debian, is not possible chosse /home at installatian. For that I installed all in sda, and then, change at fstab /home. I know just is a trick not a solution.

I installed again Xubuntu, because I prefere it. And I think do the same, install all in sda and then change /home. Even change it in fstab, is not possible log in.

All my data is there. My information is save in original /home (sdb)

I thinked that installed a new system this will writte the MBR and partition table. It didn't.

Perhaps is time to buy a new hard disk and copy everything?

---

### Post by darkod on 2012-04-30
When you say you can't log in, do you mean as the users that existed in the /home partition, or also the user that you created during the new install?

Can you at least log in as the user you created during the new install?

---

### Post by grusty on 2012-04-30
I mean, at boot the computer, go to login screen, asking user and password. My user is there, i wrotte the password, click enter, and go to black screen like go to system, but inmediatly return to login screen again.

Recognize my user and password, because if I intentionality writte a bad password, said it.

At original /home, yes, exist my user with all my documents, photos, music, etc. All my data is there. For that was very easy change at fstab, because is the same user.

Well. Today, trying working i detect that libreoffice can't work, or open some of my docs. I think that is because a problem between my original configuration and new installed configuration.

Is like can't writte at /home, because firefox lost tabs that open today, or stuff like that.

---

