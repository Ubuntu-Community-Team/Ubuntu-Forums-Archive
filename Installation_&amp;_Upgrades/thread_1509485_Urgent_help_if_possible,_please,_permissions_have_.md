---
title: "Urgent help if possible, please, permissions have been set wrongly?"
date: 2010-06-14
forum: Installation &amp; Upgrades
---

### Post by yc2 on 2010-06-14
I was just trying to add new ssh users for tonights session and really messed up badly.

I first installed package ibsh (iron-bars shell). I do not think this is the problem. I didn't know how to use it so I just went to a new user account and added ibsh at the end of his .profile. (I wrote```

sudo gedit /home/username/.profile

```which I suspect is the problem, I should have written```

gksu gedit /home/username/.profile

```??)

Well graphical logging  became impossible in  my own account until I did the following in my own account:
```

chmod 777 .profile
chmod 777 .ICEauthority

```

But desktop is still empty. I have restarted the system.

I can not use Firefox (it works without output for 10 sec and then dies)

Chromium says something like "Problems due to not being able to update profile" but works

(I cannot see any files on desktop. (But if i do places > desktop I can see them.)

All the mentioned files had -------- for permissions so I did
```
chmod 777 ~/Desktop/*
```

Please tell me how to get my system back to normal.
I think I got botched up permissions.

Some people expect to log on tonight and if someone can help me solve this, I would be really happy.

Thanks a lot.

EDIT: If I create new user accounts, I get several error messages in these accounts.

---

### Post by lechien73 on 2010-06-14
It sounds to me like your default shell has been also changed to ibsh!

I would suggest you boot with a LiveCD, mount your Ubuntu drive, and then examine its /etc/passwd file.

If the shell of your own account has been changed to /bin/ibsh (or whatever) then:

```
sudo vipw
```

and change it to /bin/bash (or whatever shell you prefer). Whether this will correct the permissions or not, I don't know.

Also, for adding the shell to new users, you're best just creating them with:

```
useradd xyz -s /bin/ibsh
```

So username xyz will be created with the ibsh shell.

---

### Post by yc2 on 2010-06-14
Well I have to get something running.

(Not even synaptic is working. Restoring Firefox profiles failed.)
I have Clonezilla backups that are a week old.

If no one can tell me what to do, I will try restoring from clonezilla-images (I have never done that before.)

If nothing comes up in this thread in about half an hour I will have to restore through Clonezilla (I have also saved data now).

But I would still be very happy if someone could tell me what went wrong, I may have to try the same steps once more.

Thanks guys, I know several people have looked at the issue now, but it is not always easy to find a solution.

---

### Post by yc2 on 2010-06-14
Thanks for giving an approach lechien73.

This is from the pwd file, I still think I have the right shell (bash). The iron-bar shell is really tough, it wouldn't have let me do anything.

```
yxxx:x:1000:1000:Yxxxx Lxxxx,,,:/home/yxxx:/bin/bash
```

Also thanks for telling me the correct way of giving the users the iron-bar shell.

But I am still stuck. Isn't this a case of sudo gedit (istd of gksu gedit) where root permissions have spread over my account?????  - I am just guessing.

---

