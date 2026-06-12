---
title: "My Upgrade Went Wrong"
date: 2006-12-17
forum: Installation &amp; Upgrades
---

### Post by zweiundzwei on 2006-12-17
I just tried to upgrade from Dapper to Edgy and ran into a few problems.
While it was installing, I was asked whether I wanted to overwrite some settings or keep mine and not install the new version. (It was something with ntp?) I wanted Ubuntu to install the new version, but then suddenly the upgrade manager (is that the real name? I don't know) shut down. 

So, that's the first problem.


The second problem is that when I click the orange update symbol I'm prompted for my password and it doesn't work. I've checked multiple times whether I'd typed it correctly, but I did, and I really don't know what to do now.

](*,) 

Help?

---

### Post by Iarwain ben-adar on 2006-12-17
Hiya,

Maybe you could try via the command line

```
sudo aptitude update && sudo aptitude upgrade
```
This will update aptitude (the CLI version of the Upgrade manager) and upgrade any packages you may have skipped (because the update manager shut down).

```
sudo dpkg-reconfigure -a
```
This will reconfigure the packages you downloaded, and probabely will fix the problem


Iarwain

---

### Post by zweiundzwei on 2006-12-17
thanks for the fast reply :)

it seems to work quite well, but there is a problem with samba - i keep getting this error:
E: /var/cache/apt/archives/samba_3.0.22-1ubuntu4_i386.deb: subprocess new pre-removal script returned error exit status 102

I can't get around that for some reason. Any ideas how to fix that?

---

### Post by Iarwain ben-adar on 2006-12-17
Don't know about that one,
but try to remove the .deb (located somewhere in /var/cache/apt if i recall correct)

And then try to install in via aptitude, it will then say that an newer version is available, and will download and install that version.

Should that fail to work, just ```
sudo aptitude remove samba
```
and then install it. (Don't purge, as it will delete your .conf files)

btw, no problem :wink:


Iarwain

---

### Post by zweiundzwei on 2006-12-17
Ok. I tried that several times now and it doesn't help. I can delete the file, but trying to install it always returns this error message: 
dpkg: warning - old pre-removal script returned error exit status 102
dpkg - trying script from the new package instead ...
invoke-rc.d: dangling symlink: /etc/rc2.d/K09samba
dpkg: error processing /var/cache/apt/archives/samba_3.0.22-1ubuntu4_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 102
Errors were encountered while processing:
 /var/cache/apt/archives/samba_3.0.22-1ubuntu4_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:


and when  i then start the update program, it tells me to do "sudo apt-get install -f", but that only leads to those errors...

---

### Post by zweiundzwei on 2006-12-17
All solved. Seems like I was not the only one with that problem.

Thanks for the help, Iarwain!

---

### Post by Iarwain ben-adar on 2006-12-18
Just awake again :D

Great!

Could you post how you solved it (or future reference :wink: )


Iarwain

---

### Post by zweiundzwei on 2006-12-20
I'm sorry I'm only replying now, school got in the way of everything ;)

I think [this]("http://ubuntuforums.org/showthread.php?t=240699") is what did the trick. It didn't help at first, but suddenly everything worked again.



...But once I had it, my newly found computer-destroying tendencies came through and I promptly screwed up my monitor settings. That works now, but I can't log in (instead of getting my desktop I get the log in page again (without errors). I guess it is somehow linked to me editing the xorg.conf file... though that makes no sense whatsoever since I only changed monitor settings. It's a mystery.

---

