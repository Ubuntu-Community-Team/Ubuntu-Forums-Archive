---
title: "The specified Domain either does not exist or could not be contacted."
date: 2013-01-19
forum: Installation &amp; Upgrades
---

### Post by zchristianl on 2013-01-19
**[SIZE="4"]Seriously Need Help!!![/SIZE]**

I'm trying to setup a Samba server to act as a Primary Domain Controller for other Ubuntu and Windows machines to logon to. When my Windows 7 Pro machine tries to join this server, it shows a logon screen. When I try to logon, I see this message

The specified Domain either does not exist or could not be contacted.

I'm not sure what I'm doing wrong. I followed this guy's tutorial, yet he won't offer any help.

[http://www.youtube.com/watch?v=8MWBhlaLIxQ&list=WL5B5CE282B38B802B](http://www.youtube.com/watch?v=8MWBhlaLIxQ&list=WL5B5CE282B38B802B)

Here is part of my config file

```
=================== Global Settings =============

[global]
workgroup = ZACCARIA

server string = %h server (Samba, Ubuntu)


dns proxy = no

security = user
username map = etc/samba/smbusers

encrypt passwords = true




############## Domains ##########333
[global]
domain logons = yes
domain master = yes
local master = yes
preferred master = yes
os level = 255

logon script = logon.cmd

add machine script = /user/sbin/useradd -g machines -c "%u machine account " -d /var/lib/samba/-s /bin/false %u

```

I've tried many times just switching stuff around and completely reinstalling everything, but nothing will work. I'm thinking it may be a DNS error, but I don't know what to do on that.

Any thoughts???

---

### Post by dino99 on 2013-01-20
maybe you will find your way with that wiki:

[https://help.ubuntu.com/community/Samba](https://help.ubuntu.com/community/Samba)

---

### Post by zchristianl on 2013-01-20
> **dino99 said:**
> maybe you will find your way with that wiki:

[https://help.ubuntu.com/community/Samba](https://help.ubuntu.com/community/Samba)

Oh... Didn't even know there was a wiki. I guess I'll try it when I have time rather than following an outdated video!!!

Thanks :popcorn:

---

### Post by zchristianl on 2013-01-20
No. I'm still getting errors. I've tried a bunch of tutorials and guides but it's getting worse than before. Does anyone have some sort of example or really detailed tutorial?

---

### Post by breadfan1979 on 2013-03-05
hi,
didn't notice any solution to this problem althouth the thread is marked as SOLVED.

that's my first post on this forum, so hello everyone!

I am setting up Ubuntu server (Ubuntu Server 12.10) with two laptops (Windows 7 pro) connected to it. Generally my aim is to use Samba/WinSCP to store movies/data on this server. - Samba 3.6.6 installed on the server.

After two weeks of running various tutorials on YT, reading manuals, book (I have a Ubunto Server 12.10 Administration and Reference book) i understood that it is not the problem with my smb.conf configuration (I edited it many times, various ways), but the problem was the settings related to the shared folder in Windows.
BTW: I was receiving exactly the same message from Windows when trying to connect to my domain/shared folder. I could access it but couldnt create any new folder or copy any files into it. So,....

1. I edited my file according to the same tutorial (YT - ReicheltAcademy) as you, my friend
2. and today I just double-clicked on 'Computer', saw my shared folder as 'H:' drive (as it should be according to the tutorial, so I mapped it this way), then right-click on it to get to 'Properties'.
3. Go to 'Security' tab
4. Now you should see the users who can access your shared folder
5. Click on 'Edit' (To change permissions) and give yourself FULL ACCESS and change the access to writeable to the other users you want to have the access to it.

Without rebooting windows you can have instant access to the shared folder with possibility to copy files etc. I checked also if my WinSCP can do the same - no problems whatsoever!:)

I am glad I found that solution myself, as I read about editing registy in Windows (in various posts) and we know what problems it could bring.
Just follow editing your smb.conf file by the AcademyReichelt tutorial on YT and then map it in your Windows 7 Pro as H: drive. Ping your server before to be sure that you can access it. Anyway, once you are in the folder, you know you have access to it. now you just need to follow my points 2-5 in order to give yourself full access to it.
Enjoy!

---

