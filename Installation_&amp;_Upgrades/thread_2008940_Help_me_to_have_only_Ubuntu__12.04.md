---
title: "Help me to have only Ubuntu  12.04"
date: 2012-06-23
forum: Installation &amp; Upgrades
---

### Post by Yellowblue on 2012-06-23
Hey guys!!! :D
I have a  laptop (HP Pavilion dv4000) since 2005... Recently i installed Linux Ubuntu  12.04
I also have in my computer  Windows 7....I would  like  to delete Windows 7 (forever) and keep Linux. My cd-player doesn't read the cd and i  don't know  how  to do it  :(
Excuse me for my English, i'm Greek. Thanks for  your time/help ;)

---

### Post by cortman on 2012-06-23
> **Yellowblue said:**
> Hey guys!!! :D
I have a  laptop (HP Pavilion dv4000) since 2005... Recently i installed Linux Ubuntu  12.04
I also have in my computer  Windows 7....I would  like  to delete Windows 7 (forever) and keep Linux. My cd-player doesn't read the cd and i  don't know  how  to do it  :(
Excuse me for my English, i'm Greek. Thanks for  your time/help ;)

Your English is excellent. :)

Open up GParted (you may have to install it, sudo apt-get install gparted) and find the Windows partitions in the list- they'll be the ones formatted to the NTFS filesystem. Make sure you don't have any external drives plugged into the laptop at the time, just to be sure you don't accidentally format them.
Right click on the partition and select "Delete". You'll wind up with a lot of unallocated space, which you can add to your existing Ubuntu partition using the same program, only you must boot from a Live CD or USB to do that.
And first and foremost: BACK UP all your data before attempting ANY kind of disk partitioning. I cannot stress that enough.

---

### Post by nipunshakya on 2012-06-24
> **Yellowblue said:**
> Hey guys!!! :D
I have a  laptop (HP Pavilion dv4000) since 2005... Recently i installed Linux Ubuntu  12.04
I also have in my computer  Windows 7....I would  like  to delete Windows 7 (forever) and keep Linux. My cd-player doesn't read the cd and i  don't know  how  to do it  :(
Excuse me for my English, i'm Greek. Thanks for  your time/help ;)

Hello. If you want to completely remove windows, you might first want to show us how your partition scheme looks like so an assist could be made on which partition is to be deleted. To do that, please run gparted software and post an image of your partition scheme.
Generally, windows is installed in NTFS format... if that's easy for you to identify, then you can boot into LiveCD and run gparted from there... and then u can just select the NTFS partition and delete it and format it to as another format.(NTFS,ext4,ext3 etc..). You may also want to update your grub while in LiveCd mode too to ensure you boot from your hard disk next time in a proper manner...

---

### Post by Yellowblue on 2012-06-24
[IMG][URL=http://imageshack.us/photo/my-images/195/gpartedonmypc.png/][/IMG]

Thanks for your help! I  still try  to delete  windows7....i uploaded the picture  you asked me.

---

### Post by nipunshakya on 2012-06-24
well, if you don't have any data to backup, its good that you boot into LiveCd, 'check the disk for errors' first,reboot the system to LiveCd again, then select 'try ubuntu', and see if your LiveCd works fine or not...
After your Live session is working fine, just at next reboot select 'Install ubuntu' and under installation type, select 'something else' then follow the following link:
[http://news.softpedia.com/news/Installing-Ubuntu-12-04-LTS-266201.shtml](http://news.softpedia.com/news/Installing-Ubuntu-12-04-LTS-266201.shtml)
(read the -_Something Else_ section nicely)

Goodluck

---

### Post by Cheesemill on 2012-06-24
OK, first of all don't try any of the suggestions above. They are all suggestions that would work if you had a normal installation of Ubuntu, but you don't.

Because you used WUBI to install Ubuntu then it's difficult to move to a Ubuntu only installation (WUBI is only really meant for testing, not for proper installations). It is possible, but not really recommended for a beginner.
[https://wiki.ubuntu.com/WubiGuide#How_do_I_migrate_to_a_real_partition.2C_and.2BAC8-or_get_rid_of_Windows_entirely.3F](https://wiki.ubuntu.com/WubiGuide#How_do_I_migrate_to_a_real_partition.2C_and.2BAC8-or_get_rid_of_Windows_entirely.3F)

Your best bet would be to back up all the data you want to keep and then do a new full installation of Ubuntu.

---

### Post by nipunshakya on 2012-06-24
Cheesemill, please read the comment #3 just above you, and say if i was wrong with my suggestion??

---

### Post by Cheesemill on 2012-06-24
> **WinuxUser said:**
> Cheesemill, please read the comment #3 just above you, and say if i was wrong with my suggestion??
Yes, you were wrong.

If the OP had followed your suggestion and deleted the NTFS partition on his drive then he would have lost everything, including Ubuntu.

---

### Post by nipunshakya on 2012-06-24
But op clearly mentions that he wants totally ubuntu, and so i suggested him quite well to backup his data first and do a fresh installation of ubuntu.... i guess thats what he wanted...
Without any debates, it would be better if we wait for the op to respond,isn't it Cheesemill? :)

---

### Post by Yellowblue on 2012-06-24
Ok i will  try your suggestions!!! I have nothing  in  my hard disc,it's totally empty!
And i am a girl  not a boy :lolflag:
Also, i don't understand what is  "op"????

---

### Post by nipunshakya on 2012-06-24
op = original poster 
Let us know how it goes... Girl.. :P

---

### Post by Yellowblue on 2012-06-25
Hey!!!!!!!!!!!!!! I made it!!! 
My husbant read  your advises ;) He  used "universal USB installer" to boot the OS and the problem was  that the  usb was  ntfs and he switched to fat32....now i  have only Ubuntu!!!! Thanks a  lot for your help!!!!!!!!!!! Come in  Greece for summeeeeeeeer!!!
):P

---

### Post by nipunshakya on 2012-06-25
hehe...thanks for your invitation...please mark the thread as solved for others to take benifits...cheers

---

