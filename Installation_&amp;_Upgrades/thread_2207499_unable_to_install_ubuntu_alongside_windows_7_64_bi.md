---
title: "unable to install ubuntu alongside windows 7 64 bit"
date: 2014-02-23
forum: Installation &amp; Upgrades
---

### Post by mehraks9 on 2014-02-23
I have been trying to install Ubuntu 13.10 on Lenovo machine running Windows 7 Ultimate 64 bit.After install alongside windows 7 option is selected it reboots and same process gets repeated. Earlier I have successfully install  Ubuntu 12.04 on two machines running Windows 7 Ultimate 32 bit edition.I am installing it with USB drive.
Kindly help.I have already posted this issue but couldn't find it on forum..


regards

---

### Post by fantab on 2014-02-24
> After install alongside windows 7 option is selected it reboots and same process gets repeated

Please post more details of the problem you are having. How are we supposed to guess what the issue is?

Post 'error messages' if any. Post details about your Lenovo hardware, is it a UEFI or BIOS system etc....

---

### Post by Bucky Ball on 2014-02-24
Yes, you did post another thread about this [HERE]("http://ubuntuforums.org/showthread.php?t=2203340") which I replied to and you never replied to, probably because you couldn't find it. If you click 'Settings' at the top right of the screen you will see all threads of yours which have been replied to. 

Please use this option in future rather than posting duplicate threads. Go and have a look at my reply there as your post was unclear. That duplicate thread has been closed.

---

### Post by mehraks9 on 2014-02-24
I am very thankful for your reply. This is true that I could not locate or find the solution posted by you.I found it today and I will try to install 12.04 AMD 64 bit and will get back in case of any problem.

Thanks a lot..

regards

---

### Post by mehraks9 on 2014-02-24
I am very thankful for your reply. Actually there is no error message during the installation but when I select the "[SIZE=4]**_install alongside windows 7"_**[/SIZE] option and hit Continue button system reboots and again same process repeats.Installation does not proceed further..It is BIOS system ***"Intel dual core"***

Thanks a lot..

regards

---

### Post by mastablasta on 2014-02-25
how many disk parititions do you have? what happens if oyu select try it and then start installer from running desktop?

---

### Post by oldfred on 2014-02-25
Almost all Windows 7 systems use all 4 primary partitions. Post this from terminal in liveCD to see existing partitions.

sudo parted -l

       My laptop already has 4 primary partitions: how can I install Ubuntu?
[http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu](http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu)
Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor utility partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
For a complete blow-by-blow on dealing with HP's four partitions, see Full Circle Magazine, issue 41, page 36. - gordintoronto
[http://fullcirclemagazine.org/](http://fullcirclemagazine.org/)

---

