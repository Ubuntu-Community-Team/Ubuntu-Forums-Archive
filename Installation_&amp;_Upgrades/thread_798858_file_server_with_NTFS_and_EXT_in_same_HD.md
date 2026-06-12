---
title: "file server with NTFS and EXT in same HD"
date: 2008-05-18
forum: Installation &amp; Upgrades
---

### Post by aluxgt on 2008-05-18
NTFS partition?
hi, i am traying to configure a file server.

I have read this post: [http://howtoforge.com/ubuntu-home-fileserver](http://howtoforge.com/ubuntu-home-fileserver)
that is some kind of tutorial to get the same results, but the article point to the use of 2 HD, one for linux system and the 2nd. in NTFS formar to store the shared folders and files, that in order to read the HD with the NTFS partition in any windows based machine in case of any crash.

I have two question.
1) what do you think about the mix: linux - NTFS that the article describes?

2) I have a 1TB WD green disk, may i have 2 partitions one wiht linux system an the other with NTFS partition and configure the samba to write the shared files and folders to that partition?

Please be kind i am very... very... very... newby too and i am trying to learn.
Thanks a lot for your help.
Best regards.

---

### Post by tamoneya on 2008-05-18
I agree with how the article did most of the configurations.  Mixing NTFS in with linux is much better than it used to be.  I read the partitions from my dual boot all the time and have no problems.  Also you definately need to have both the NTFS and ext3 as you dont want to be installing ubuntu into an NTFS partition.  As for how to partition your 1TB drive I would go with 30 GB ext3 (ubuntu) and give the rest to NTFS.  30 GB is a gives you plenty of extra space should you want to install other stuff into the partition.  It is annoying to have to make partitions larger.

---

### Post by aluxgt on 2008-05-18
Thanks a lot tamoneya for your post.

I have another question if you have some time:

1) In the tutorial the steps show are for configuring samba with 2 HD, any idea how to configure it with one HD and two partitions?

2) if any crash occure can i read the ntfs partition in any windows machine, am i right?


Thanks a lot for your help.

---

### Post by tamoneya on 2008-05-18
basically you make two partitions: /dev/hda1 and /dev/hda2 instead of /dev/hda1 and /dev/hdb1.  That is the only real main difference between doing it with one harddrive versus two.

---

### Post by aluxgt on 2008-05-18
Thanks a lot tamoneya.

One last quetion.

All my machines in my network are windows vista ultimate.  Do i need Samba to share the ntfs partition of my file server?

I ask that because my undestanting of sambas is that you need it to share files between linux and windows machines (EXT and NTFS partitions), but in my case i only have windows machines and linux file server with one shared ntfs partition.

Hope i had express well my idea.
Thanks a lot for your help.

---

### Post by pas_paa on 2008-05-18
Hi,

I read the very same howto the other day and I have just installed my old computer with ubuntu and samba. However, I can't get it to work. In the last sentence in chapter 9, he says: "now you can access your fileserver from internet explorer". What I want to do is access the shared directory by mapping a drive letter to it from Windows explorer on my XP box. That should be possible, right?

When I try that I get a log in screen for the server (which I don't think I should) and when trying to log in with linux userID/password (same as Samba userID/password) I get an error message that the network path could not be found. What I want is for the directory on the linux box to be accessible for everyone in the workgroup without having to log in.

I'll appreciate any comments to this.

Thanks

---

### Post by tamoneya on 2008-05-18
samba will allow you to see the linux machine and specified directories through network neighborhood(i think thats what ist called its been a while).

---

### Post by pas_paa on 2008-05-18
Yes, I see the name of my Ubuntu machine when I try to map, so I'm pretty sure the networking part is ok. 

My smb.conf looks like this (the part that I added, rest is default)
-o-o-o-o-o-o-o-o-o-o-o-o-o-o-o-o-o-o-o-
[hdb public hard disk]
comment = Public Folder
path = media/store
public = yes
writable = yes
create mask = 0777
directory mask = 0777
force user = nobody
force group = nogroup
guest ok = yes
-o-o-o-o-o-o-o-o-o-o-o-o-o-o-o-o-o-o-o-

In the log file (/var/log/samba/log.xxx) I get the following messages:
-o-o-o-o-o-o-o-o-o-o-o-o-o-o-o-o-o-o-
[2008/05/17 22:14:56, 0] lib/util_sock.c:write_data(562)
write_data: write failure in writing to client 192.168.15.10. Error Connection
reset by peer
[2008/05/17 22:14:56, 0] lib/util_sock.c:send_smb(769)
Error writing 4 bytes to client. -1. (Connection reset by peer)
[2008/05/17 22:15:52, 0] smbd/service.c:make_connection(1191)
colt (192.168.15.10) couldn't find service media
-o-o-o-o-o-o-o-o-o-o-o-o-o-o-o-o-o-o-o-o-o-

192.168.15.10 is my XP box. I'm not sure how to interpret this.

---

### Post by aluxgt on 2008-05-18
I read the very same howto the other day and I have just installed my old computer with ubuntu and samba. However, I can't get it to work. In the last sentence in chapter 9, he says: "now you can access your fileserver from internet explorer". What I want to do is access the shared directory by mapping a drive letter to it from Windows explorer on my XP box. That should be possible, right?

When I try that I get a log in screen for the server (which I don't think I should) and when trying to log in with linux userID/password (same as Samba userID/password) I get an error message that the network path could not be found. What I want is for the directory on the linux box to be accessible for everyone in the workgroup without having to log in.

I'll appreciate any comments to this.

Thanks[/QUOTE]

[QUOTE=pas_paa;4991046]Hi,
I have the same question, because i had seen tutorial where you actualy map the drive, but i realy do not how with samba.  And i realy do not know if i should install samba to share a ntfs partition.

Look at this tutorial: 

[http://www.linuxjournal.com/article/8590](http://www.linuxjournal.com/article/8590)

[http://www.linux-watch.com/news/NS9015653445.html](http://www.linux-watch.com/news/NS9015653445.html)

[http://www.howtoforge.com/samba_setup_ubuntu_5.10_p3](http://www.howtoforge.com/samba_setup_ubuntu_5.10_p3)


:(

---

### Post by aluxgt on 2008-05-19
Look at this tutorial:
[https://wiki.ubuntu.com/EasyFileSharing](https://wiki.ubuntu.com/EasyFileSharing)

---

### Post by pas_paa on 2008-05-19
That last tutorial "EasyFileSharing" looks like some project that's  not completed yet. But the samba setup on 5.10 I'm going to try out. I _WILL_ get this to work :-)
Will keep you posted.

---

### Post by pas_paa on 2008-05-27
I got it to work!!! Thinking that there was some firewall/antivirus problem, I added my wife as a samba user (and didn't assign her a password, just hit enter when prompted)

smbpasswd -a your_username
smbpasswd -e your_username

I went to her computer and there it was. I could map a network drive to the shared directory on my ubuntu box, using windows explorer. 
After that I deleted

smbpasswd -x your_username

and created myself again, this time also without password. Voila!

So something with authentication that WinXP does not like, I'm guessing.

I also found this tutorial 
[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)
which has alot more tweaking possibilities. Using this one also works for me as long as I don't assign passwords to the samba users

---

