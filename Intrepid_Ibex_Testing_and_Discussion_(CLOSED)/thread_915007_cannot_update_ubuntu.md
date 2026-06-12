---
title: "cannot update ubuntu"
date: 2008-09-09
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by donjo on 2008-09-09
i got this error mesej when i tried to updates my ubuntu
```

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://archive.ubuntu.com intrepid Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/intrepid/Release  

W: Some index files failed to download, they have been ignored, or old ones used instead.

```
can anyone help me please??
how to solve this?

---

### Post by Rocket2DMn on 2008-09-09
Are you using Intrepid Ibex?  That version is still in development and is subject to above normal amounts of breakage.  Can you please post the outputs of
```
lsb_release -a
cat /etc/apt/sources.list
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by donjo on 2008-09-09
> **Rocket2DMn said:**
> Are you using Intrepid Ibex?  That version is still in development and is subject to above normal amounts of breakage.  Can you please post the outputs of
```
lsb_release -a
cat /etc/apt/sources.list
sudo apt-get update && sudo apt-get upgrade
```

scorps@scorps-laptop:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu intrepid (development branch)
Release:	8.10
Codename:	intrepid
scorps@scorps-laptop:~$ 


scorps@scorps-laptop:~$ cat /etc/apt/sources.list

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid main restricted universe multiverse

scorps@scorps-laptop:~$ sudo apt-get update
[sudo] password for scorps: 
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid Release.gpg [189B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/multiverse Translation-en_US
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid Release [65.9kB]                      
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid Release
  
Fetched 190B in 15s (13B/s)
Reading package lists... Done
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid/Release](http://archive.ubuntu.com/ubuntu/dists/intrepid/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems
scorps@scorps-laptop:~$ 

scorps@scorps-laptop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
scorps@scorps-laptop:~$

---

### Post by cariboo on 2008-09-09
Have a look here for info on renewing your keys:

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

Any further questions and problems with intrepid should be asked here:

[http://ubuntuforums.org/forumdisplay.php?f=346](http://ubuntuforums.org/forumdisplay.php?f=346)

Jim

---

### Post by Rocket2DMn on 2008-09-09
Moved to Intrepid Ibex Testing and Discussion

+1 for renewing keys.

---

