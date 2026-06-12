---
title: "Need to go back to VIsta 0xd0000017 Error"
date: 2008-06-03
forum: Installation &amp; Upgrades
---

### Post by scraghty604 on 2008-06-03
I have an Acer Aspire 5570Z, I have the Acer Recovery and System Disk. And the Newest Ubunutu

When i go to install it loads ram disk image then ask for recovery disk, put in then it starts to to the install but then gets error 0xd0000017 Please Restart.

I have looked around and it seems some ppl think that The "Cd" cant find a suitable spot to install the "c;\" Drive and thus cant install windows...

Any help guys...Wish i could stay with this but i need windows again thanxs

---

### Post by Sam Lars on 2008-06-03
[http://answers.yahoo.com/question/index?qid=20080331134656AAvmosR](http://answers.yahoo.com/question/index?qid=20080331134656AAvmosR)
This page says to reformat the drive before running the Restore CD.

---

### Post by scraghty604 on 2008-06-04
i saw that but i do not know how to format the drive!! lol

---

### Post by scraghty604 on 2008-06-04
Also i am trying to install Vitsa(unfortunately yes)  if make difference

---

### Post by scraghty604 on 2008-06-04
also it is not a dual boot just one partition and that 8.04, from what i can read look like it not gonna happen

---

### Post by VMC on 2008-06-04
Not sure what 's on your recovery disl. It's best to have a Vista install disk. So the easist way is to put in the livcd from ubuntu and launch gparted. Then right-click on each partition and select delete. Then your left with the mbr. If you can get to a dos disk do fdisk/mbr to rrestore the mbr to default.

Maybe just deleting all the partitions will let the restore disk work.

What I use is Ghost's Gdisk. It works the same as Microsofts fdisk, lise
Gdisk 1 /del /all, then gdisk/mbr (1) being the hard drive number. Gdisk by itself will reveal the number.

---

### Post by scraghty604 on 2008-06-04
Im not that smart lol..so i am a lil confused thanxs tho..ok so load into the live cd

-then lanch gparted (were is that?)
-delete the partition(there is only one)
-then do a fdisk on mbr(no idea what that is)
-Or how to get to a dos disk, Do i need that ghoast thing u were talkig about

---

### Post by scraghty604 on 2008-06-04
If its easier i would be more then happy to have Windows and ubuntu on here i have a 160gig drive so lots of room mabey if i reinstall ubuntu ther is an option to slect how much space to use? then the left over space should alow me to install windows?

---

### Post by Sam Lars on 2008-06-04
It would be better to install Windows, and then when you install Ubuntu you can size up your partitions, leaving Windows available and installing Ubuntu as well.
Gparted will be in the menu somewhere as Disk Partition Manager or something like that.
If only one partition shows up, then delete it, and make a new one.  This should reformat the disk.

---

### Post by scraghty604 on 2008-06-04
again thanxs

Now about mbr? im supposed to do something with that as well?

---

### Post by Sam Lars on 2008-06-04
Installing Windows might take care of that.

---

### Post by shultzjr on 2008-06-04
famous quote "it takes several computers to fix one broken one"

You need to get access to another computer and download and burn a gparted live cd.  With that you can partition and format to your hearts content.  Once cd is made, boot with it and delete all the partitions you find, then create two partitions on the hd about half the hd each.  If you have a 120G hd then it will have two 60G partitions.  Then if the recovery disk requires the target partition to be formatted, format the first one with NTFS.  That should allow the recovery disk to use the first partition for the Windows install.  Once completed, install the Ubuntu/Linux cd on the second/rest of the hd.  That will give you a dual boot system.  Much more usable than just Windows.

later.....

---

### Post by VMC on 2008-06-04
> **Sam Lars said:**
> Installing Windows might take care of that.

Yes, Vista is pretty aggressive.  You have a rescue disk. Just insert it and see if it does all this for you. If so then AFTER its finished, then install ubuntu. Ubuntu will even recover free Windows disk space, so you don't have to worry about re-partitions. I used it the first time that way.

Since by your won admission, I can't expaind much further, but I would suggest getting hold of either Ghost or Acronis to back up your partitions. I have Vista, XP, you name it. All backed up with one of those programs. They can be cd-rom dos bootable. The only reason I'm bringing this up is the fact that then you can restore your Windows partitions in short order. I even have ubuntu backed up with Acronis. The first time I installed it. After everything was just right. Then as a test I re-imaged ubuntu onto another hard disk, and within 5 minutes I was back up running ubuntu!

It would be helpful to invest some time and learn how to do this.

---

