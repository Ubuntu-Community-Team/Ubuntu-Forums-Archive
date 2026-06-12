---
title: "Reinstall: What is my default user group?"
date: 2012-10-01
forum: Installation &amp; Upgrades
---

### Post by MrsUser on 2012-10-01
Hello Ubuntu community,

I want to re-install my system according to this way:

[http://askubuntu.com/questions/56051/reinstalling-ubuntu-without-formating-home-as-well-as-without-any-old-config-f](http://askubuntu.com/questions/56051/reinstalling-ubuntu-without-formating-home-as-well-as-without-any-old-config-f)

So first, I rename my home folder:

```
sudo mv /home/myUserName /home/myUserName.bak
```And after re-installing, I move needed files from my backuped home folder to my new home folder and modify the owner to gain access to the files of the old home folder:

```
sudo chown -R newUser.newUsersGroup /home/myUserName.bak
```Problem is that I don't know what the name of the user group is that I belong to. I'd like to check, but strangely I cannot find the user/group administration in Ubuntu. Is my system wrecked? It used to be in the system settings.

Is there any command line to find out my default user group?

Using Ubuntu 12.04 64-bit.

---

### Post by deadflowr on 2012-10-01
In a terminal simply:

```
id username
```

will list the user named's groups. 
Typically, a user will belong to his own group, and maybe others.

---

### Post by MrsUser on 2012-10-01
> **deadflowr said:**
> In a terminal simply:

```
id username
```will list the user named's groups. 
Typically, a user will belong to his own group, and maybe others.


Thank you very much for your help! This is exactly what I was looking for!

---

