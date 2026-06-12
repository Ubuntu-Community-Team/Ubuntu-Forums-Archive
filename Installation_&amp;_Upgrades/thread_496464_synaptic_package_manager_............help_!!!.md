---
title: "synaptic package manager ............help !!!"
date: 2007-07-09
forum: Installation &amp; Upgrades
---

### Post by 12hello on 2007-07-09
hey when ever i start the synaptic package manager i get this error ...........................


E: Malformed line 40 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

i was trying to download vlc payer and added repository after which i got this error ...
Please help

and if any one could help me with the steps to download vlc player could be of great help

---

### Post by Pumalite on 2007-07-09
The repository you added might have misspellings, orthography faults, punctuation faults, etc. Go and fix it or remove it altogether. VLC in 7.04 can be gotten without adding any repository( that I know of).

---

### Post by mikewhatever on 2007-07-09
Can you post the output of the following command here
> cat /etc/apt/sources.list

---

### Post by Algoodman on 2007-07-09
We have the MIT open course were USB drive which we wish to share in our network using our web-server which is running Ubuntu 6.10, but we want to mount it in /home/sites/MITocw
At last we are able to mount the drive using the following command written in fstab:
/dev/sdb1 /home/sites/MITocw ntfs rw,suid,auto,nouser,sync o o

this mount the drive even after restart but come the problem which is the first two or three pages will open after which the rest will not but if we use the following command which has to be done manually any time the server is restarted:

sudo mount –t ntfs /dev/sdb1 /home/sites –o umask=0222 –o uid=1028,gid=100

Now every page will open and we can access it over the intranet. Now my question is most I keep on doing this manually? What is the defaults configuration in the auto run all about?

---

### Post by Pumalite on 2007-07-09
> **Algoodman said:**
> We have the MIT open course were USB drive which we wish to share in our network using our web-server which is running Ubuntu 6.10, but we want to mount it in /home/sites/MITocw
At last we are able to mount the drive using the following command written in fstab:
/dev/sdb1 /home/sites/MITocw ntfs rw,suid,auto,nouser,sync o o

this mount the drive even after restart but come the problem which is the first two or three pages will open after which the rest will not but if we use the following command which has to be done manually any time the server is restarted:

sudo mount –t ntfs /dev/sdb1 /home/sites –o umask=0222 –o uid=1028,gid=100

Now every page will open and we can access it over the intranet. Now my question is most I keep on doing this manually? What is the defaults configuration in the auto run all about?

You have to open a new thread.

---

### Post by bigken on 2007-07-09
sudo gedit /etc/apt/sources.list 

and remove line 40

---

