---
title: "Unable to upgrade from 8.10 to 9.04 PPC"
date: 2009-04-13
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by karimone on 2009-04-13
Hi all, I have a macmini PPC with Ubuntu on it. I use only with terminal, not gui. When I do this:
```
do-release-upgrade -d

```

The system give me this error:

```
...
Hit http://ports.ubuntu.com jaunty-security/multiverse Sources
Done downloading            

Error during update 

A problem occurred during the update. This is usually some sort of 
network problem, please check your network connection and retry. 

W:Failed to fetch 
http://ports.ubuntu.com/ubuntu-ports/dists/jaunty/Release Unable to 
find expected entry partner/binary-powerpc/Packages in Meta-index 
file (malformed Release file?) 
, E:Some index files failed to download, they have been ignored, or 
old ones used instead. 


Restoring original system state

Aborting
Reading package lists: Done
Reading state information: Done
Reading state information: Done
Reading state information: Done

```

Any idea? I found nothing on google...

---

### Post by avtolle on 2009-04-13
> **karimone said:**
> Hi all, I have a macmini PPC with Ubuntu on it. I use only with terminal, not gui. When I do this:
```
do-release-upgrade -d

```The system give me this error:

```
...
Hit http://ports.ubuntu.com jaunty-security/multiverse Sources
Done downloading            

Error during update 

A problem occurred during the update. This is usually some sort of 
network problem, please check your network connection and retry. 

W:Failed to fetch 
http://ports.ubuntu.com/ubuntu-ports/dists/jaunty/Release Unable to 
find expected entry partner/binary-powerpc/Packages in Meta-index 
file (malformed Release file?) 
, E:Some index files failed to download, they have been ignored, or 
old ones used instead. 


Restoring original system state

Aborting
Reading package lists: Done
Reading state information: Done
Reading state information: Done
Reading state information: Done

```Any idea? I found nothing on google...
What I did was to disable and delete the partner repository from my software sources, reload the same, and then try again (which worked).I then added the same back, with (to date) no ill effects.
Good luck.

---

### Post by mkvnmtr on 2009-04-13
I think the Medibuntu repository has to be deleted also. I do know a standard upgrade disables it.

---

### Post by karimone on 2009-04-14
I removed the partner repository and now the upgrade works. Wish me good luck.
Thanks!

---

