---
title: "Backup / restore, Like windows home server"
date: 2010-01-07
forum: Installation &amp; Upgrades
---

### Post by DFortier on 2010-01-07
Hello all,
I'm new to Ubuntu (very minimal linux use as well). I rathe like what i have seen so far with ubuntu (tried Wubi, VM's and even installed via dual boot). I'm currently looking for a backup option that works like window home server. Where it will run on the OS and give me the option to recover a few files or more importantly restore the whole partition to how it was (I find the best way for me to learn something is to "play" and that can = fubar).
 
I tried Deja Dup (choose / as backup point) and while this did seem to backup/restore personal data, I got alot of permision errors and it didnt restore programs. I googled looking for a way to make a "recovery disk" hoping it would allow me to bypass the permission errors and overwrite everything.
 
I have also download clonezilla but this seems to require that i reboot the machine and manually kick off a backup (havent actually tried it yet)
 
Is there a better solution that i am missing? I have a network share, dvd burner and external hard disk that i can use as backup media. 
 
Any advice would be most helpfull
thank you

---

### Post by maybeway36 on 2010-01-07
I haven't heard of anything like this, but I don't see why it wouldn't be possible for someone to make.
In the meantime, you might consider making either a partition image or a tarball of all the files on the drive. There's a good, although slightly outdated, tutorial [here.](http://ubuntuforums.org/showthread.php?t=35087)
I'd add the options
```
--exclude=/dev --exclude=/media
```
to tar when you back it up. That way you don't have to worry about unmounting stuff in /media.

---

### Post by DFortier on 2010-01-07
Thanks for the input i'll give it a try.

---

### Post by DFortier on 2010-01-28
I've done some more research and it is looking like what i really want is refered to "live backup and bare metal restore". That way if i delete some files i can do a basic restore and if i really screw things up i can just go back to yesterday from a live cd. The biggest issue i'm have is i cant seem to find something that will backup the machine while in the os (as apposed to boot a rescue cd) and allow me to use it as an image to restore the partitions. A'm I missing something or is there not a "all in one solution" like windows home sever or macrium reflect?
 
thanks again for you time.

---

### Post by Mark Phelps on 2010-01-28
The primary limitation that you present is the "while in the OS" criterion.  Linux utilities, in general, perform filesystem operations (like partition backup/restore) with the partition unmounted.  That's how they work.  This means that, by definition, you can not be "in the OS" while you're backing up the partition that houses it.

Howevever, that said, I strongly suggest you read up on Clonezilla.  It is supplied as an ISO or Zip file, can be burned to a CD, and can be used (in a manner similar to Macrium Reflect and Acronis True Image) to save an image of a partition (or complete disk) and restore the same later.

Also, if you read the Clonezilla info, you'll find it has the ability to be copied to a partition on your drive, and then, while you still have to exit the OS to do a backup/restore, you can run Clonezilla from your hard drive -- which prevents you having to keep a boot CD around.

---

### Post by llawwehttam on 2010-01-28
Why not just have a seperate backup NAS and then use the command

```
rsync -avz --update / user@IP.OF.NAS:/backup
```or similar. You could also easily add this to crontab.

Rsync is very useful.

---

### Post by DFortier on 2010-01-28
Thanks for the suggestions i will look at both of them. I have found by trial and error, that i can use tar to backup and restore "while in OS". It seem that if i backup, do a fresh install, then restore. I'm able to preserve my data and setup (tested this in Virtualbox and it seems to work, not sure about the true effects as im far from a linux guru, but all the programs and drivers were restored and seemed to work w/o issue).
 
thanks again for the help.

---

