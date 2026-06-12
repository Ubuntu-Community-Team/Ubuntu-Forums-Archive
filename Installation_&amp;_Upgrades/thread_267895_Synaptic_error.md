---
title: "Synaptic error"
date: 2006-09-29
forum: Installation &amp; Upgrades
---

### Post by Gargamella on 2006-09-29
Hi guys, i installed ubuntu and i customized and installed a lot of software,but i don't know why i wanted to add a new custom repository to synaptic and now every time synaptic tries to refresh it makes an error caused by my repository,i deleted from the list, but it still does this error,and i can't use it.
If you know what to do to reinstall it i will do it.

an other problem i have is amarok: it works well but when i was on mandriva musicbrainz tag service worked well, now it doesn't do anything,have you got any idea?

thanks 


Andrea

---

### Post by Gargamella on 2006-09-29
i tried to insert the ubuntu live cd to get its package,but it does always that damned error,so what to do?

reinstall?

---

### Post by ajgreeny on 2006-09-29
What is happening that means you can't use *synaptic* and what was the custom repo?  What about using *apt-get* or *aptitude* instead?  If you have an apt error none of those will work either, so let us know what error you see.

The same thing with amarok, more info needed.

---

### Post by Gargamella on 2006-09-29
the error appears even using apt-get commands in terminal

example:

root@andrea-laptop:/home/andrea# apt-get update

E: Il tipo 'http://users.musicbrainz.org/~luks/ubuntu' non è riconosciuto alla linea 23 nella lista sorgenti /etc/apt/sources.list
root@andrea-laptop:/home/andrea#
root@andrea-laptop:/home/andrea#



i am an italian user... it tells that "http..." isn't known in line 23 of the source list

:-k

---

### Post by ajgreeny on 2006-09-29
Make sure that line is deleted from your sources.list file and save the file.
Now in a terminal run *sudo apt-get update* which will update the repos that apt is trying to use.  If you don't do that, apt will still use the older version of the file with the error line still being looked for.

---

### Post by Kateikyoushi on 2006-09-29
I can't speak italian but seems your repos are messed up.
Could you give me the output of this command ?

```
cat /etc/apt/sources.list
```

---

### Post by Gargamella on 2006-09-29
root@andrea-laptop:/home/andrea# cat /etc/apt/sources.list


## Major bug fix updates produced after the final release of the
## distribution.

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

deb cdrom:[Ubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060806.1)]/ dapper main restricted
[http://users.musicbrainz.org/~luks/ubuntu](http://users.musicbrainz.org/~luks/ubuntu) dapper main
# deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted universe multiverse
# deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse
# deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) dapper-security main restricted universe multiverse
# deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse


root@andrea-laptop:/home/andrea#



here it is

---

### Post by Gargamella on 2006-09-29
ok guys i forgot #deb ;D

i made now gedit /etc/apt/sources.list

and now works thank you guys

;D see you next time

---

### Post by Sariel Amraphel on 2007-02-22
remove the #

# means comment.

---

