---
title: "it only finds the main hard drive"
date: 2006-06-21
forum: Installation &amp; Upgrades
---

### Post by yadalda on 2006-06-21
I just got ubuntu 6.06 on my pc I have a 12 GB hard drive I have everything installed on. I also have 2 10 GB hard drives but when I try to mount them it gives me an error.

error: device /dev/hdb1 is not removable 
error: could not execute pmount

I don't really under stand what format I need to go with when formatting my hard drives and I don't under stand how to access my hard drives if they ever become accessible.

I am windows person so if someone can please explain how I can fix this problem with basic steps I would really appreciate it.

In windows there is to formatting types nfts and fat32 so I am new to these other formatting options 
I would take screen shots but I haven't found out how to do that just yet.

---

### Post by gerbman on 2006-06-21
[QUOTE=yadalda]error: device /dev/hdb1 is not removable 
error: could not execute pmount[/QUOTE]What does your /etc/fstab file look like?

> I don't really under stand what format I need to go with when formatting my hard drivesFAT32 and EXT3 are probably the most common filesystem formats for additional drives. NTFS isn't fully supported in Linux at the moment, so stay away from it.

> I am windows person so if someone can please explain how I can fix this problem with basic steps I would really appreciate it.What filesystem are you currently using on the drives?

[This]("http://www.psychocats.net/ubuntu/mountlinux.html") page might clear things up a little.

---

### Post by Ptero-4 on 2006-06-21
type this in a terminal window:
```

sudo mkdir /media/HD2
sudo mkdir /media/HD3

```
When asked for a password use yours.
This commands create two new folders in the /media folder, this folders will be used to mount your two 10GB HD's and the contents of those two HD's will be accesible from the folders you just created.
After that type this:
```

sudo nano /etc/fstab

```
This opens the /etc/fstab file for editing, again use your password when asked.
Then finally add the drives to your /etc/fstab file.

---

### Post by yadalda on 2006-06-22
[QUOTE=Ptero-4]type this in a terminal window:
```

sudo mkdir /media/HD2
sudo mkdir /media/HD3

```
When asked for a password use yours.
This commands create two new folders in the /media folder, this folders will be used to mount your two 10GB HD's and the contents of those two HD's will be accesible from the folders you just created.
After that type this:
```

sudo nano /etc/fstab

```
This opens the /etc/fstab file for editing, again use your password when asked.
Then finally add the drives to your /etc/fstab file.[/QUOTE]
Can I see a screen shot of what you mean?
I still need to get used to the ubuntu environment.

---

### Post by gerbman on 2006-06-22
[This]("http://www.psychocats.net/ubuntu/mountlinux.html") page didn't help? Also, read [this]("http://www.tuxfiles.org/linuxhelp/fstab.html") if you're not clear on how to add partitions to your fstab file.

---

### Post by Daniel Ibrahim on 2006-06-22
you can do this:
press ALT+CTRL+F1 (all together)
you will get a black screen and you have to log in, log in with your username and password

then type:
sudo mkdir /media/hd2
sudo mkdir /media/hd3

you will not be able to use the mouse but you can always come back to your normal screen by clicking: CTRL+ALT+F5 (or CTRL+ALT+F7) 
Alternately you find the Terminal in your Menu.
and type the commands in the window that appears.

Terminal is a text terminal. You will get used to it soon. It is very powerful.

the above command:
sudo mkdir /media/hd2
sudo mkdir /media/hd3

will make two new folders in the folder /media/

you have to provide your password because this is an administrative task, you must be sure what you are doing after typing sudo because you can destroy your whole system with the wrong command (never type sudo rm -rf / for example, you will loose all your data and the complete system. don't even try it... but if you don't sudo, you can savely type rm -rf / (unless you managed to be a root user, what I don't think)

This is a start. are you still here?

---

