---
title: "Problems with Update Manager"
date: 2011-11-08
forum: Installation &amp; Upgrades
---

### Post by TheMTtakeover on 2011-11-08
When I try to install updates it says "Failed to download package files
Check your Internet connection."

then under details it gives me this
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/b/binutils/binutils_2.21.53.20110810-0ubuntu4_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/b/binutils/binutils_2.21.53.20110810-0ubuntu4_amd64.deb) 404  Not Found [IP: 91.189.92.184 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/n/nautilus/libnautilus-extension1_3.2.1-0ubuntu1_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/n/nautilus/libnautilus-extension1_3.2.1-0ubuntu1_amd64.deb) 404  Not Found [IP: 91.189.92.184 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/n/nautilus/nautilus-data_3.2.1-0ubuntu1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/n/nautilus/nautilus-data_3.2.1-0ubuntu1_all.deb) 404  Not Found [IP: 91.189.92.184 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/n/nautilus/nautilus_3.2.1-0ubuntu1_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/n/nautilus/nautilus_3.2.1-0ubuntu1_amd64.deb) 404  Not Found [IP: 91.189.92.184 80]

Please Help Me!!!!

---

### Post by subehsharma on 2011-11-10
est method to getaway from this problem is to install fix404. You can read about it more here:

Under Ubuntu, the APT package index is a database containing all packages of repositories (PPAs) defined in the /etc/apt/sources.list file. To update this database after adding some repositories, we need to use this command from the Terminal:

sudo apt-get update

Sometimes, when running the command given above, we get error messages (404 Not Found) that are the result of wrong PPAs, which may slow down the update process via the Terminal. In fact, this 404 Not Found error messages are not harmful at all, but you can use Fix404 to detect and remove these PPAs.

To install Fix404 on Ubuntu 11.04, launch the Terminal and run these commands:

sudo apt-add-repository ppa:lkjoel/fix404
sudo apt-get update
sudo apt-get install fix404

To install on Ubuntu 10.10/10.04, download this deb package here.

To start using Fix404, run this command (root privileges required):

sudo fix404

Then follow displayed instructions to disable PPAs causing the 404 Not Found Error.

---

### Post by anafshalom on 2012-04-17
I'm having the same problem. here is what I get when i tried your suggestion:

root@Reuen-Ubuntu:/etc# apt-add-repository ppa:lkjoel/fix404
bash: apt-add-repository: command not found
root@Reuen-Ubuntu:/etc# 

help please!

---

### Post by subehsharma on 2012-04-17
> **anafshalom said:**
> I'm having the same problem. here is what I get when i tried your suggestion:

root@Reuen-Ubuntu:/etc# apt-add-repository ppa:lkjoel/fix404
bash: apt-add-repository: command not found
root@Reuen-Ubuntu:/etc# 

help please!

follow the steps i mentioned in my note above yours.

---

### Post by sammiev on 2012-04-17
> **anafshalom said:**
> I'm having the same problem. here is what I get when i tried your suggestion:

root@Reuen-Ubuntu:/etc# apt-add-repository ppa:lkjoel/fix404
bash: apt-add-repository: command not found
root@Reuen-Ubuntu:/etc# 

help please!

It looks like your problem is a little different. I would suggest starting a new thread to get the help that you need.

---

### Post by raja.genupula on 2012-04-18
could you post what you got after doing as```
 
sudo apt-get update
``` in your terminal

---

### Post by catchup on 2012-04-22
Hi

I think I have found my self in the same boat as I am getting the same 404 errors that have been mentioned with a difference of having an older installation of Ubuntu (I have just installed this old version from 9.04). 

I'm wondering if I need to just uninstall and get a new version as I get the same results as anafshalom as I though I might and I can not see the references to links for installing fix404

> **subehsharma said:**
> est method to getaway from this problem is to install fix404. You can read about it more here:


Please forgive me if I have missed how this forum might post links

---

### Post by Phosphoric on 2012-04-23
Don't know if it's the same problem but I had the same error message this morning for a standard update.  Press the "Check" button first and then update.  Worked like a charm for me. :D

---

