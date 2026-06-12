---
title: "Ubuntu never asked me for a root password!"
date: 2005-05-27
forum: Installation &amp; Upgrades
---

### Post by magomago on 2005-05-27
Hi guys.  I'm currently trying out ubuntu and i LOVE how it looks.  Very nice and very clean, this is my first debian based distro.  Now i've p[layed/messed around with many RPM based distros, bu i'm far from a knowledge linux guru.    More like an acolyte if anything

Now when I installed Ubuntu, it never asked me for a root password.  It created me another username to work on and I was fine with that...

but now I want to install drivers, add pakcages, download updates, etc. etc...but i can't!  I need to know my root password.

I've tried inputting nothing, root, Ubuntu, KDE, current password...the list goes on

Does anyone know what it is (if there is a default) and where I can change it...or if I have or don't have one..

lol I just want to SU ;)

---

### Post by misterben on 2005-05-27
I'm new to this, but after my readings before install I believe you want to use sudo, not su. Something along the lines of "everyone in the admin group can run sudo, which is basically su only better"  -  not certain though, correct me if I'm wrong

---

### Post by magomago on 2005-05-27
[QUOTE=misterben]I'm new to this, but after my readings before install I believe you want to use sudo, not su. Something along the lines of "everyone in the admin group can run sudo, which is basically su only better"  -  not certain though, correct me if I'm wrong[/QUOTE]

What do you mean by SUDO?  I'm slightly confused by that...I tried inputting SUDO as a passowrd and it didn't work.  

I tired inputting sudo by istelf and it return some information....

amarry@cv077078:~$ sudo -h
usage: sudo -K | -L | -V | -h | -k | -l | -v
usage: sudo [-HPSb] [-p prompt] [-u username|#uid]
            { -e file [...] | -i | -s | <command> }

---

### Post by the_clown on 2005-05-27
[QUOTE=magomago]What do you mean by SUDO?  I'm slightly confused by that...I tried inputting SUDO as a passowrd and it didn't work.  

I tired inputting sudo by istelf and it return some information....

amarry@cv077078:~$ sudo -h
usage: sudo -K | -L | -V | -h | -k | -l | -v
usage: sudo [-HPSb] [-p prompt] [-u username|#uid]
            { -e file [...] | -i | -s | <command> }[/QUOTE]
 [http://www.ubuntulinux.org/wiki/RootSudo](http://www.ubuntulinux.org/wiki/RootSudo)

type sudo
   
then use the password for the account you set up during the install

---

### Post by huh? on 2005-05-27
try "sudo apt-get update"...it will then ask you for the password that you assigned earlier...hit "enter" and it should run update..I had trouble with "sudo" when I first ran into it...there's a way to assign a regular root password, but I found "sudo" works just fine...just play a bit and read a bit, and you should be fine...:)

---

### Post by ymtoh on 2005-05-28
i also did not get the promp to enter root password. 

so i went to the "system" -> "users and groups" -> check "show all users and groups" -> then go to "root" -> "properties" -> then change the password there.

---

