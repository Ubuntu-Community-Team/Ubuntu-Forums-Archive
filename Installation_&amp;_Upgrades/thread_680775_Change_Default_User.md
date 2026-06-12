---
title: "Change Default User"
date: 2008-01-28
forum: Installation &amp; Upgrades
---

### Post by smadon on 2008-01-28
Hello,

I m doing a PXE install of Ubuntu, and I'm going to use the connection to AD .
So, the user will be store in the AD.

I would like to change the default user and select only some application for every user which will connect on the PC?

So, where are store the default data concerning new User? 
And can I add a script which will start for all new User,
And One which will start only for the first connection
and another one which will start each time the user connect?

ummh, not sure, if my question is not really clear, let me know if you want precision :( ?

Thanks for your reply :-)

---

### Post by CheShA on 2008-01-28
> So, where are store the default data concerning new User? 

in /etc/skel

set up a user as you want, then copy over to /etc/skel
> And can I add a script which will start for all new User,> and another one which will start each time the user connect?
Sure, as i said, set up a user as youwant your default user, then copy the contents of that user's home directory to /etc/skel.  This includes setting up 
scripts in  System > Preferences > Sessions


Not sure how you'd get a script to only run on first login, but, perhaps you could make a script ~/firstrun.sh   have it run (from  System > Preferences > Sessions)  then have the last line be 
```
rm ~/firstrun.sh 
```

 so that next login the script isn't there.  There are almost certainly better ways though!

---

### Post by smadon on 2008-01-28
Hi, 

Thanks for your reply.
It give me a good start for the login script.
I will copy my script to /etc/skel.


But still it's not exactly what I need for the User.
/etc/skel can have only default document for the user. What I want is to redefine the Desktop for all user, before there account has been created on the pc.
 Exemple : Application will just have accessories and Internet and not Games and Graphic,
and so if the new user is a member of a group Admin he can have access to all, 
Plus for all user change the default setting of Desktop Remote to exemple autorize remote access, and define the same default ScreenSaver.
Basicly I would like to define default rules and security like you can do with Active Directory on Windows XP desktop.

so which file or folder define all default Desktop configuration for default user?

Thanks for you reply.
:popcorn:

---

### Post by smadon on 2008-01-28
Ok,

Sorry I've got my reply.

[http://ubuntuforums.org/showthread.php?t=399202](http://ubuntuforums.org/showthread.php?t=399202)
the file was hidden :-)

---

### Post by smadon on 2008-01-30
Hello,

Ok, I look at etc/skel and I can add default file for my new user.

**But I still don't know how I can run a script as root when the user log on the PC?**

I want to mount disk form my script, basically i want to mount drive for the user who connect.

so a personal Folder : 
```
mount -t cifs //SERVERWIN2003/$LOGNAME  /media/perso  -o username=$logonUser,password=$passwordUser,iocharset=utf8,file_mode=0777,dir_mode=0777

and network folder 
mount -t cifs //SERVERWIN2003/$group1   /media/share -o username=$logonUser,password=$passwordUser,iocharset=utf8,file_mode=0777,dir_mode=0777
```

for now, I don't know how I can have the data for group1, probably a research in the AC with LDAP should do, but not yet  implemented, if you have an idea as well :-)

---

