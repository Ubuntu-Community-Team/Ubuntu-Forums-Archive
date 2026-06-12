---
title: "VIM cannot install"
date: 2012-01-09
forum: Installation &amp; Upgrades
---

### Post by its_bigB on 2012-01-09
Hi all,

Tried the command **sudo apt-get install vim **and allow all the permissions. But at some point I got the following error.

> 
After this operation, 26.8MB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  vim-runtime vim
Install these packages without verification [y/N]? y
Err [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) jaunty/main vim-runtime 2:7.2.079-1ubuntu5
  404 Not Found [IP: 91.189.92.176 80]
Err [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) jaunty/main vim 2:7.2.079-1ubuntu5
  404 Not Found [IP: 91.189.92.176 80]
Failed to fetch [http://lk.archive.ubuntu.com/ubuntu/pool/main/v/vim/vim-runtime_7.2.079-1ubuntu5_all.deb](http://lk.archive.ubuntu.com/ubuntu/pool/main/v/vim/vim-runtime_7.2.079-1ubuntu5_all.deb)  404 Not Found [IP: 91.189.92.176 80]
Failed to fetch [http://lk.archive.ubuntu.com/ubuntu/pool/main/v/vim/vim_7.2.079-1ubuntu5_i386.deb](http://lk.archive.ubuntu.com/ubuntu/pool/main/v/vim/vim_7.2.079-1ubuntu5_i386.deb)  404 Not Found [IP: 91.189.92.176 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?



So the installation is not completed. Can anyone of you help me to solve this.


Thanks

---

### Post by raja.genupula on 2012-01-09
Hi 
do **sudo apt-get update**  & post the result here if you got any errors.

:):)

---

### Post by its_bigB on 2012-01-09
Thanks a lot for the reply.

I tried what you said and get the following.

> 
W: Failed to fetch [http://lk.archive.ubuntu.com/ubuntu/dists/jaunty/main/binary-i386/Packages](http://lk.archive.ubuntu.com/ubuntu/dists/jaunty/main/binary-i386/Packages)  404 Not Found [IP: 91.189.92.181 80]

W: Failed to fetch [http://lk.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/binary-i386/Packages](http://lk.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/binary-i386/Packages)  404 Not Found [IP: 91.189.92.181 80]

W: Failed to fetch [http://lk.archive.ubuntu.com/ubuntu/dists/jaunty/main/source/Sources](http://lk.archive.ubuntu.com/ubuntu/dists/jaunty/main/source/Sources)  404 Not Found [IP: 91.189.92.181 80]

W: Failed to fetch [http://lk.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/source/Sources](http://lk.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/source/Sources)  404 Not Found [IP: 91.189.92.181 80]

W: Failed to fetch [http://lk.archive.ubuntu.com/ubuntu/dists/jaunty/universe/binary-i386/Packages](http://lk.archive.ubuntu.com/ubuntu/dists/jaunty/universe/binary-i386/Packages)  404 Not Found [IP: 91.189.92.181 80]

W: Failed to fetch [http://lk.archive.ubuntu.com/ubuntu/dists/jaunty/universe/source/Sources](http://lk.archive.ubuntu.com/ubuntu/dists/jaunty/universe/source/Sources)  404 Not Found [IP: 91.189.92.181 80]

W: Failed to fetch [http://lk.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/binary-i386/Packages](http://lk.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/binary-i386/Packages)  404 Not Found [IP: 91.189.92.181 80]

W: Failed to fetch [http://lk.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/source/Sources](http://lk.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/source/Sources)  404 Not Found [IP: 91.189.92.181 80]

W: Failed to fetch [http://lk.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/binary-i386/Packages](http://lk.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/binary-i386/Packages)  404 Not Found [IP: 91.189.92.181 80]

W: Failed to fetch [http://lk.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/binary-i386/Packages](http://lk.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/binary-i386/Packages)  404 Not Found [IP: 91.189.92.181 80]

W: Failed to fetch [http://lk.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/source/Sources](http://lk.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/source/Sources)  404 Not Found [IP: 91.189.92.181 80]

W: Failed to fetch [http://lk.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/source/Sources](http://lk.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/source/Sources)  404 Not Found [IP: 91.189.92.181 80]

W: Failed to fetch [http://lk.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/binary-i386/Packages](http://lk.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/binary-i386/Packages)  404 Not Found [IP: 91.189.92.181 80]

W: Failed to fetch [http://lk.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/source/Sources](http://lk.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/source/Sources)  404 Not Found [IP: 91.189.92.181 80]

W: Failed to fetch [http://lk.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/binary-i386/Packages](http://lk.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/binary-i386/Packages)  404 Not Found [IP: 91.189.92.181 80]

W: Failed to fetch [http://lk.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/source/Sources](http://lk.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/source/Sources)  404 Not Found [IP: 91.189.92.181 80]

E: Some index files failed to download, they have been ignored, or old ones used instead.


Actually there is a huge list like that.

BTW, I am working on Ubuntu 9.04

---

### Post by raja.genupula on 2012-01-09
HI actually you're using Ubuntu 9.04 , actually its life time ends by October 23 2010. so Ubuntu not going to provide updates for it officially . So what the choice you have with you is Upgrade your OS .

open your update manager -> settings -> at the 1st tab you will have the option for upgrades there select normal and go again updating . The update manager head is with a message as upgrade new version available . SO say yes for that and go on and make it up to 10.04 and stop because this a LTS and gonna support up to 2013 . 

else download latest Ubuntu and install it again gonna solve your problem.

for more clear info look at this

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

all the best.

---

### Post by its_bigB on 2012-01-09
Ok, it is clear with me now.

However, can I do something like this. While I keep the OS as it is I can change the repository link to the latest (if I could find the URL) and then update. Am I able to do that.

Honestly speaking I am new to Ubuntu and I have lots of stuff to learn. So I need your guys help a lot. :)

---

### Post by its_bigB on 2012-01-09
> **raja.genupula said:**
> HI actually you're using Ubuntu 9.04 , actually its life time ends by October 23 2010. so Ubuntu not going to provide updates for it officially . So what the choice you have with you is Upgrade your OS .

open your update manager -> settings -> at the 1st tab you will have the option for upgrades there select normal and go again updating . The update manager head is with a message as upgrade new version available . SO say yes for that and go on and make it up to 10.04 and stop because this a LTS and gonna support up to 2013 . 

else download latest Ubuntu and install it again gonna solve your problem.

for more clear info look at this

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

all the best.

I check with the Update Manager and it says Ubuntu 9.10 is available. Not 10.04 or latest.

---

### Post by its_bigB on 2012-01-09
Please have a look at the screen-shot (attached).

---

### Post by raja.genupula on 2012-01-09
> **its_bigB said:**
> I check with the Update Manager and it says Ubuntu 9.10 is available. Not 10.04 or latest.

Hi man , yes its right . first you have to give ok for 9.10 and then only you are able to go for 10.04 . do same process repeat after getting to 9.10. 

all the best .

---

### Post by its_bigB on 2012-01-10
Thanks again.

However, since I am using multiple OSs it is better not to do so. I'll update with the latest once I reformat my PC in few weeks times. Feel it is much better. 

Anyway, is there a way that I can install VIM off-line without connecting to any such repository?

---

### Post by raja.genupula on 2012-01-11
try this 

[https://launchpad.net/ubuntu/+source/vim/2:7.2.079-1ubuntu5/+build/911770](https://launchpad.net/ubuntu/+source/vim/2:7.2.079-1ubuntu5/+build/911770)

[https://launchpad.net/ubuntu/+source/vim/2:7.2.079-1ubuntu5](https://launchpad.net/ubuntu/+source/vim/2:7.2.079-1ubuntu5)

---

### Post by anuphys on 2012-05-24
hi all, 
i have recently installed the Ubuntu 12.04 LTS in my system. but when i went to install synaptic package manager or anything else it shows the no network connection even though i am connected to INTERNET. then i came to know that VI editor is necessary to config the internet settings . to install VI editor i use the following command
   " sudo apt-get install vim-nox" when i am running this following thing appears in terminal.

> anup@anup-Vostro-260s:~$ sudo apt-get install vim-nox
[sudo] password for anup: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 vim-nox : Depends: vim-common (= 2:7.3.429-2ubuntu2.1) but 2:7.3.429-2ubuntu2 is to be installed
           Depends: vim-runtime (= 2:7.3.429-2ubuntu2.1) but it is not installable
           Depends: libruby1.8 (>= 1.8.7.352) but it is not installable
           Depends: tcl8.5 (>= 8.5.0) but it is not installable
E: Unable to correct problems, you have held broken packages.
anup@anup-Vostro-260s:~$

if anyone can please help me out of this problem... this is urgent.

Thanks

---

### Post by andurill on 2012-06-19
Try clearing vim and and starting over - worked for me


sudo apt-get remove vim-common
sudo apt-get clean && sudo apt-get purge
sudo apt-get update && sudo apt-get install vim

---

