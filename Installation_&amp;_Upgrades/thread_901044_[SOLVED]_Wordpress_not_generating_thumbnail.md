---
title: "[SOLVED] Wordpress not generating thumbnail"
date: 2008-08-26
forum: Installation &amp; Upgrades
---

### Post by eLPhi on 2008-08-26
Hello all,

I wish I'm posting on the right category. This is my 1st post so please do forgive me.:confused:

Here's the problem. I have a wordpress installation on XAMPP running at windows xp. All features are working well, I have a newly installed wordpress on LAMP running on Ubuntu server. Features are working (eg. photo upload, video upload, plugins) but the thumbnail of photos uploaded are not generated. Been trying to find a solution on google but can't find any and I suspect that the problem is on my Ubuntu installation (since the other wordpress installation is working fine on XAMMP)

What settings do i need to change to make it work?:confused:

Thank you all.

---

### Post by manishtech on 2008-08-26
Are they getting uploaded? Are you sure.. I guess some problems of the file permissions. Gimme the output of the command

```
ls -lr /var/www | grep -i wp-uploads
```

---

### Post by eLPhi on 2008-08-26
Yes they are being uploaded. when i enter the code: 

> ls -lr /var/www | grep -i wp-uploads

nothing happens.

---

### Post by manishtech on 2008-08-26
> **eLPhi said:**
> Yes they are being uploaded. when i enter the code: 



nothing happens.
Can you tell us the path to your wordpress installation in local file system path like **/var/www/....**

There is a folder called wp-uploads where all uploads are stored AFAIK, not sure about the thumbnails part.
BTW you are telling about the thumbnails for the user profile? Gravatrs like display pic?

---

### Post by eLPhi on 2008-08-26
The full path for my local wp installation is:

```
/var/www/unitel/dir
```

the uploaded pictures are located on:

```
/var/www/unitel/dir/wp-content/wp-uploads
```

From there, uploaded pictures are suppose to have a thumbnail generated automatically if I wish to insert a photo as thumbnail on a post. In my local installation of wp at XAMPP on xp, it's ok but on LAMMP at ubuntu, thumbnails are not generated although the files are uploaded..

---

### Post by manishtech on 2008-08-26
Quite unusual, I have Linux hosting and it works fine. I can upload and resize and create thumbnails. I think there is some problems with file permissions.

---

### Post by eLPhi on 2008-08-26
File/folder permission on the whole "wp-content" directory are set to 777.

The rest of the directories are 755 (eg wp-admin, wp-includes) files are set to 644.

Does it have something to do with the user who owns the directory? I have created a User under "user" group. This user uploads files via vsftpd and his home directory is set to /var/www/unitel/

PS
My prob is well explained here: [http://wordpress.org/support/topic/199390?replies=1](http://wordpress.org/support/topic/199390?replies=1)

---

### Post by manishtech on 2008-08-26
> **eLPhi said:**
> File/folder permission on the whole "wp-content" directory are set to 777.

The rest of the directories are 755 (eg wp-admin, wp-includes) files are set to 644.

Does it have something to do with the user who owns the directory? I have created a User under "user" group. This user uploads files via vsftpd and his home directory is set to /var/www/unitel/

PS
My prob is well explained here: [http://wordpress.org/support/topic/199390?replies=1](http://wordpress.org/support/topic/199390?replies=1)
Am a bit confused! You say that images are being uploaed by thumbnails are not being generated. This means the problem is something ahead permissions.

Now since its clear about the file/folder permissions are set correctly, problem lies in something else.

In XAMPP when you uploaded anything, it got stored in wp-uploads. After that did it store any other small resized image of this uploaded picture?

---

### Post by eLPhi on 2008-08-26
> In XAMPP when you uploaded anything, it got stored in wp-uploads. After that did it store any other small resized image of this uploaded picture?

Yes. Photo uploaded would have 2 other smaller image (medium and thumbnail).

---

### Post by manishtech on 2008-08-26
> **eLPhi said:**
> Yes. Photo uploaded would have 2 other smaller image (medium and thumbnail).
I guess there is the problem creating additional images. I would have to check the source of WP in this case how it takes place!

---

### Post by eLPhi on 2008-08-26
You're so kind! Thank you so much for the help! Greatly appreciated.

I think the file responsible for smaller image creation is 
/var/www/unitel/dir/wp-admin/includes/media.php it has a permission of 644. 

But again i don't know if it's really have something to do with my problem (since I too was helping myself to solve this problem)

---

### Post by manishtech on 2008-08-26
> **eLPhi said:**
> You're so kind! Thank you so much for the help! Greatly appreciated.

I think the file responsible for smaller image creation is 
/var/www/unitel/dir/wp-admin/includes/media.php it has a permission of 644. 

But again i don't know if it's really have something to do with my problem (since I too was helping myself to solve this problem)
The permissions on media.php doesnt not affect in any way! I don't think so. That permission is just to say that file can be accessed by this,this users.
It has nothing to do with the ability to write file to a folder.


Am still unable to understand the cause of problem... :-k

---

### Post by eLPhi on 2008-08-27
Problem is solve. Guy from wordpress.org helped me with this. I just need to install php5-gd as instructed below:

[http://wordpress.org/support/topic/199390?replies=3](http://wordpress.org/support/topic/199390?replies=3)

thank you again manishtech for your replies. :)

---

### Post by manishtech on 2008-08-27
Oh! Why didnt this strike my mind. Am so foolish ](*,)

Hope you know what is GD? Its a imaging library which can manipulate images right from the php script.

If you think its done, please mark this thread as solved. Hope you know to mark a thread as solved?

---

