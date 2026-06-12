---
title: "Cannot get Ubuntu to share with Windows"
date: 2011-02-08
forum: Installation &amp; Upgrades
---

### Post by xtomtomx on 2011-02-08
Hello Team,
Installed Ubuntu server 10. 
Using it for file server only.
Need a directory under "home" to be accessible via a windows network share such as \\10.10.10.1\home\myfiles

Here's what I have done:
1. Installed Samba
2. Installed Nautilus
3. created the directory to be shared
4. Chmod my target directory under "home" to be 755
5. chowned my target directory to my user account 
5. used the Gnome gui tool, right clicked target file, set sharing options --> "share this folder" --> allow others to create and delete files, and guest account. all checked.

Then I get this error:
The folder "Target" needs the following extra permissions for sharing to work:
  - write permission by others
Do you want Nautilus to add these permissions to the folder automatically?
I say yes,
then I get this error:
"failed to execute child process "net" permission denied.

what am I doing wrong?

---

### Post by Morbius1 on 2011-02-08
If your starting from the server edition it's possible that your user isn't a member of the right groups:
```
sudo gpasswd -a your_user_name sambashare
``````
sudo gpasswd -a your-user-name fuse
```
Then logoff and login again.

---

### Post by xtomtomx on 2011-02-08
Hi,

Thank your for that information.
I tried what you recommended, but I still receive the error ""failed to execute child process "net" permission denied."
when trying to share the folder.

---

### Post by Bert987 on 2011-02-08
[http://www.youtube.com/watch?v=deb2jRm3c7g](http://www.youtube.com/watch?v=deb2jRm3c7g)
she walk you thru samba setup all my windows machine see Ubuntu

---

### Post by Morbius1 on 2011-02-09
I have been able to reproduce your error by disabling execute on "net".

To fix it:
```
sudo chmod +x /usr/bin/net
```

---

### Post by xtomtomx on 2011-02-09
Hello Morbius,
Did that, same error, and no joy.
I have even given 755 -r to everything on that directory.
Nothing.

Perhaps it might help to describe what I want to do?

I want to make a folder available to anyone on the windows network,
and also to backup devices.

who should I be logged in to do this?
It seems I cannot log into the desktop as root, but my admin account has root access.

what directory is best for sharing?
normally I use /usr/home/(username)/folder
but right now, I cannot even access my own admin home directory, as it tells me the permissions do not allow it, even though it's set to 755.

---

### Post by xtomtomx on 2011-02-09
> **Bert987 said:**
> [http://www.youtube.com/watch?v=deb2jRm3c7g](http://www.youtube.com/watch?v=deb2jRm3c7g)
she walk you thru samba setup all my windows machine see Ubuntu

Hello Bert,
This worked perfectly!
Except when I ran sudo /etc/init.d/samba restart it told me there's no command for that, but it looks like it does not matter, as I can now connect to the share with windows.
Yay!

Thanks everyone!
( ^ ^)

---

