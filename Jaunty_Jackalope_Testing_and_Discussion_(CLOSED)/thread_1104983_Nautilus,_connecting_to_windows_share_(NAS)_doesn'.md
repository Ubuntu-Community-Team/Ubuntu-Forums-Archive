---
title: "Nautilus, connecting to windows share (NAS) doesn't work"
date: 2009-03-24
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by jalmargyyk on 2009-03-24
I'm having problems connecting to Windows (samba) shares via nautilus. Nautilus is able to see all the shares and the username/domain/password dialog fires up when trying to connect.

After inserting all the necessary information, I get an error "Unable to mount location" "Failed to mount Windows share".

If I mount the samba shares via fstab or smbmount command everything is working just fine. Is anyone else experiencing this?

```
jallu@jallu-desktop:~$ uname -a
Linux jallu-desktop 2.6.28-11-generic #37-Ubuntu SMP Mon Mar 23 16:40:00 UTC 2009 x86_64 GNU/Linux
```

with the latest updates applied.

Okay, this seems to be a problem of the NAS drive itself, since I'm able to connect my other ubuntu box via samba. Still a bit strange since with Intrepid all worked out of the box.

Here's some info about the NAS drive:
D-Link DNS-323
Current Firmware Version :  	 1.05
Firmware Date : 	 05/05/2008 

I'll make a firmware upgrade and see if that helps.

---

### Post by jalmargyyk on 2009-03-24
Firmware update didn't help. I'm still getting the same response as in the previous post.

Okay, I found out where the problem was. According to [->this post<-]("http://ubuntuforums.org/showpost.php?p=6238553&postcount=5"), D-Link has a bit old samba server and it supports only lanman authentication. 

So I just added the following line to /etc/samba/smb.conf and everything worked again just fine. :)

```
client lanman auth = yes
```

Thanks goes to cebesius for finding this out.

---

