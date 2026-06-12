---
title: "Installing AIM"
date: 2006-12-23
forum: Installation &amp; Upgrades
---

### Post by wannaBeHacker on 2006-12-23
Hey guys i want to install aim on my new utuntu :)

here is the sets i took

i went to aim.com downloaded   the newest version of aim for linux the deb 2.1 ver

it was installed on my desktop

/home/errorprone/desktop

so i went to follow the commands the sit told me to take

> errorprone@errorprone-laptop:~/Desktop/usr/bin$ cd ../..
errorprone@errorprone-laptop:~/Desktop$ ls
aim_1.5.286-1_i386.deb  aim-1.5.286.tgz  usr
errorprone@errorprone-laptop:~/Desktop$ dpkg -i aim_1.5.286-1_i386.deb 
dpkg: requested operation requires superuser privilege
errorprone@errorprone-laptop:~/Desktop$ cd /
errorprone@errorprone-laptop:/$ ls
bin   cdrom  etc   initrd      lib    mnt  proc  sbin  sys  usr  vmlinuz
boot  dev    home  initrd.img  media  opt  root  srv   tmp  var
errorprone@errorprone-laptop:/$ cd home
errorprone@errorprone-laptop:/home$ ls
errorprone
errorprone@errorprone-laptop:/home$ cd errorprone
errorprone@errorprone-laptop:~$ ls
Desktop  Examples
errorprone@errorprone-laptop:~$ /l
bash: /l: No such file or directory
errorprone@errorprone-laptop:~$ /
bash: /: is a directory
errorprone@errorprone-laptop:~$ cd /
errorprone@errorprone-laptop:/$ dpkg -i /home/errorprone/Desktop/aim_1.5.286-1_i386.deb 
dpkg: requested operation requires superuser privilege
errorprone@errorprone-laptop:/$ 


As you can see it tells me that i dont have superuser privilege??:-k 

i dont know why it would be saying that... can someone help me

and what i need to do

thanks!

btw im a super noob user

thanks

---

### Post by Sef on 2006-12-23
> errorprone@errorprone-laptop:/$ dpkg -i /home/errorprone/Desktop/aim_1.5.286-1_i386.deb 

try switching to /Desktop first

rrorprone@errorprone-laptop:/$ cd ~/Desktop

rrorprone@errorprone-laptop/Desktop:/$ dpkg -i aim_1.5.286-1_i386.deb

---

### Post by wannaBeHacker on 2006-12-23
same problem, asking me to be a superuser](*,)

---

### Post by Smokeymcpawt on 2006-12-24
put sudo before the command, so try


```
sudo dpkg -i /home/errorprone/Desktop/aim_1.5.286-1_i386.deb
```

---

