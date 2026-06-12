---
title: "install cvs server"
date: 2005-08-25
forum: Installation &amp; Upgrades
---

### Post by Blues- on 2005-08-25
does anyone have a HOWTO or good guide that can help me to
install cvs server on my ubuntu box ?

---

### Post by DJ_Max on 2005-08-25
I would imagine 
```
sudo apt-get install cvs
```

Look in synaptic.

---

### Post by Blues- on 2005-08-26
Well .. trough trial and error i managed to setup CVS server,
with Viewcvs read access with C# and php colorization with the help of enscript.

I wrote my own HOW-to for later reference,
If anyone is intested in it .. lemme know and I'll post it.

Cherrs,
Konni.

---

### Post by LarryD on 2005-08-29
I'm an absolute noob to Linux and only have experience as a user of CVS.  Despite that, I've just wiped my laptop and installed Ubuntu.  Pretty good experience so far...

My goal is to get a CVS server going on this laptop so that all of my other computers (all Windows based currently, but subject to change) can access the repository.

If you have your guide available, I'd love to take a look at it.  I've managed to get CVS installed, but I don't yet have a clue how to configure it.

Thanks for any help that can be offered...

LarryD

---

### Post by sn33kyP3t3 on 2005-09-07
[QUOTE=Blues-]Well .. trough trial and error i managed to setup CVS server,
with Viewcvs read access with C# and php colorization with the help of enscript.

I wrote my own HOW-to for later reference,
If anyone is intested in it .. lemme know and I'll post it.

Cherrs,
Konni.[/QUOTE]


Can you please post your howto

---

### Post by CiberAmigo on 2005-09-08
I would also be very pleased with a HOWTO on cvs.

Cencerly
CiberAmigo

---

### Post by robert114 on 2005-11-14
I'm interested in the how to aswell, ive installed viewcvs with apt-get but don't know what to do next.

---

### Post by mihaic on 2005-12-06
I can see this howto about CVS is in high demand :), I also would like to have a look at it...

Thanks,
Mihai

---

### Post by zi99y on 2006-04-06
whats the point of writing a howto and not posting it ffs!

duh

---

### Post by overfused on 2006-04-11
still no cvs how-to ? :(

---

### Post by MrEricSir on 2006-04-27
If anyone's still trying to setup CVS, I found this guide earlier today.  Seems to be accurate, because I just got a CVS server running on my machine :D

[http://sanatio.blogspot.com/2005/12/cvs-server-on-ubuntu.html](http://sanatio.blogspot.com/2005/12/cvs-server-on-ubuntu.html)

---

### Post by TitusDalwards on 2006-04-27
ok it will be more useful for me thanks lot again

---

### Post by robert114 on 2006-04-27
thanx

---

### Post by souren on 2006-05-10
Thanks...that's a helpful guide! Cheers mate.

---

### Post by emachine on 2007-06-09
> **MrEricSir said:**
> If anyone's still trying to setup CVS, I found this guide earlier today.  Seems to be accurate, because I just got a CVS server running on my machine :D

[http://sanatio.blogspot.com/2005/12/cvs-server-on-ubuntu.html](http://sanatio.blogspot.com/2005/12/cvs-server-on-ubuntu.html)


This walk through was going great for me until the very last checkout.

I got this error.


```
? bin
? cvsrepo
? dev
? etc
? lib
? tmp
? usr
cvs checkout: failed to create lock directory for `/cvsrepo/CVSROOT' (/cvsrepo/CVSROOT/#cvs.history.lock): Permission denied
cvs checkout: failed to obtain history lock in repository `/cvsrepo'
cvs checkout: Updating .
cvs checkout: Updating CVSROOT
cvs checkout: failed to create lock directory for `/cvsrepo/CVSROOT' (/cvsrepo/CVSROOT/#cvs.lock): Permission denied
cvs checkout: failed to obtain dir lock in repository `/cvsrepo/CVSROOT'
cvs [checkout aborted]: read lock failed - giving up

```

ANyone have any ideas?  I tried running this as sudo and still got the same error.

---

### Post by cyrano24100 on 2007-06-28
Well I tried it and I didn't even get the login portion to work!

sppuser@spp3:/$ cvs -d : pserver:Charles@localhost:/stprosrc login
Logging in to : pserver: Charles@localhost:2401/stprosrc
CVS password: 
cvs [login aborted]: unrecognized auth response from localhost: cvs [pserver aborted]: /stprosrc: no such repository

Man, and I tried the Demo repository too;neither work!blast! Back to square one!

---

### Post by bibby on 2007-10-05
I got as far as emachine above, with the failed checkout, following the steps at
[http://www.yehuang.net/archives/44](http://www.yehuang.net/archives/44) 
but with much help as well from 
[http://ale.freeshell.org/articles/cvs-getting-started/index.html](http://ale.freeshell.org/articles/cvs-getting-started/index.html)

**cvs checkout project_name** barfed with the same errors, but
**sudo cvs checkout project_name** worked ok. 
!! edit by bibby: don't do this, see next post. !!

Now that the lock directories exist, I hope not to have to sudo commit my modifications or use sudo at all, but we'll see.

---

### Post by bibby on 2007-10-07
Figured I'd follow up my own post by retracting some bad information.
As the user, you should not need to sudo do-anything to check out or in. If you're getting "permission denied" , then the group permissions on the repository aren't right.

That said, you'll (likely) need sudo to create the repo, but after that, your user's group permission should be able to handle the rest.
```

sudo mkdir /var/lib/cvsd/cvsroot/project_name
sudo chown cvsd:cvsd /var/lib/cvsd/cvsroot/project_name
sudo chmod 775  /var/lib/cvsd/cvsroot/project_name

```

/var/lib/cvsd/  was the default location in my instance, so this could differ for you.
 Also be certain that your user is part of the specified group (in my case cvsd).

---

