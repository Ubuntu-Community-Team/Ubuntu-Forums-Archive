---
title: "change url when downloading packages in feisty fawn"
date: 2007-12-24
forum: Installation &amp; Upgrades
---

### Post by hydraconsole on 2007-12-24
hi, i'm using feisty fawn on wubi7.04. i need help changing the url when i use the update manager. packages are currently downloading through [http://us.archiv.ubuntu.com](http://us.archiv.ubuntu.com) feisty-updates/main. I am not in the US. I'm in the Philippines. How do I change it to download from the servers here in the Philippines?

thanks

---

### Post by seshomaru samma on 2007-12-25
You need to edit your sources list
back up your sources list with this command:
```
sudo cp -i /etc/apt/sources.list /etc/apt/sources.list_backup
```
then edit it with this command:
```
gksudo gedit /etc/apt/sources.list
```
change the us to ph so it will look something like this:

```
deb http://ph.archive.ubuntu.com/ubuntu feisty main restricted 
deb http://ph.archive.ubuntu.com/ubuntu feisty-updates main restricted
deb http://security.ubuntu.com/ubuntu feisty-security main restricted


deb http://ph.archive.ubuntu.com/ubuntu feisty universe multiverse 
deb http://ph.archive.ubuntu.com/ubuntu feisty-updates universe multiverse
deb http://security.ubuntu.com/ubuntu feisty-security universe multiverse
```

save the new file and run the command :
> sudo apt-get update

you can also go to this website which will generate a sources list for you:
[http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)

---

### Post by hydraconsole on 2007-12-25
thank you!

---

