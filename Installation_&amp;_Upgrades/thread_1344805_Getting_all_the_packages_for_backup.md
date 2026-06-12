---
title: "Getting all the packages for backup"
date: 2009-12-03
forum: Installation &amp; Upgrades
---

### Post by ubuntpetbe on 2009-12-03
Hello, 
I'm new to trying Linux and am searching for a solution to a specific problem. 

(Have read a lot about Linux. )

Here is my situation: 
Me and my family share an internet connection with a pretty low download limit per month. 
Due to problems, Karmic Koala (Ubuntu 9.10) was reinstalled at least two times now. And every time it needs to be prepared. 
(Searching packages and installing.) 

But since the download limit is pretty low and disk space (intern and extern HDD) is plenty. 
Keeping the packages for backup would be handy. 

Synaptic Package Manager is very On-line leaning. 
Give some love for the off-liners too. 

Didn't fount anything to put the downloaded packages somewhere and don't delete them after I've downloaded them. 
(Note: My problem is about having the packages, not about synaptic)

_A way to keep and access those packages would be really handy. _

Moving them is not a problem. 
Know how to do that. 

Can anybody tell how to keep packages while installing and accessing them? 
Also, since it would be a good thing. 
Can anybody tell how to also keep dependencies or put them also in the packages that require them. And keep a copy of the ubuntu updates, all of them, for backup and fast reinstal. 

Would be very helpful, thanks.

---

### Post by halj32 on 2009-12-03
there is a program call aptoncd
[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)
hope this helps very easy to use, backs up all the apps you downloaded to cd/dvd

---

### Post by ubuntpetbe on 2009-12-03
Thanks, that's a handy resource. 

Can I also include updates on the cd? 
That would be really helpful. 

And I want the .deb packages. 
Or can I grab .debs with it too? 
(I wanna place them on an external HDD, no cd.) 
I need to get the .debs, packaging them is no problem. 
As I mentioned in my post. 
Still, thanks for the answer.

---

### Post by atoztoa on 2009-12-08
> **ubuntpetbe said:**
> Thanks, that's a handy resource. 

Can I also include updates on the cd? 
That would be really helpful. 

And I want the .deb packages. 
Or can I grab .debs with it too? 
(I wanna place them on an external HDD, no cd.) 
I need to get the .debs, packaging them is no problem. 
As I mentioned in my post. 
Still, thanks for the answer.

What it does is, it will copy and index all the .deb files already installed using apt-get.

You can keep it as a ISO image in HDD and mount it when needed.

When you try to restore using APTonCD, it will copy all the deb packages to your local cache. So, the next time you try to install, it won't go online for that package...

You can also add the CD as an installation source, synaptic will search that first before going online...

---

### Post by Ishachaitanya on 2009-12-11
Re: Howto: Backup and restore your system! 
Backing up by AptonCD and restoring packages offline.
 
 First one have to install aptoncd in the offline computer or the computer which has no internet connection.
 
 The AptonCd can be downloaded with all dependecies in a folder of a internet computer and then can be installed in that internet computer and in any other computer which have no internet connection. To do this one has to be a superuser or administrator with password for the internet computer.
 
 the command is as follows
 
 root@ubuntu:/# apt-rdepends aptoncd 2>&1 | grep "^[a-zA-Z0-9_].*$" > /tmp/x1
 
 apt-rdepends to be installed first in the internet computer if not already installed.
 The above command is for creating a list for all dependencies for aptoncd with the main aptoncd package.
 
 Next commands are
 
 root@ubuntu:/# for f in `cat /tmp/x1` ; do apt-cache show $f | grep Filename | cut -f 2 -d ' ' ; done >/tmp/x2
 
 mkdir mycache 
 [to keep the downloaded aptoncd package with all dependencies in the mycach folder under root]
 
 root@ubuntu:/# cd mycache
 
 root@ubuntu:/mycache# wget -B [http://np.archive.ubuntu.com/ubuntu/](http://np.archive.ubuntu.com/ubuntu/) -i /tmp/x2
 
 [if wget is not already installed then it is to be installed first before executing the above command]
 this command will start downloading packages & all dependencies of aptoncd application.
 
 Now copy the mycache folder to the home directory of the computers which have no internet connection and install it in those computers.
 
 In the internet computer also install the aptoncd and make backup of all packages with upgrades and dependencies and make a CD/DVD/ISO image. Carry them to the computers having no internet connection and by using aptoncd application restore the packages and upgrades with all dependencies.
 
 So by using only one computer with internet one can install applications in other computers having no internet connection at all.

---

### Post by Ishachaitanya on 2009-12-11
Re: Howto: Backup and restore your system! 
Backing up by AptonCD and restoring packages offline.
 
 First one have to install aptoncd in the offline computer or the computer which has no internet connection.
 
 The AptonCd can be downloaded with all dependecies in a folder of a internet computer and then can be installed in that internet computer and in any other computer which have no internet connection. To do this one has to be a superuser or administrator with password for the internet computer.
 
 the command is as follows
 
 root@ubuntu:/# apt-rdepends aptoncd 2>&1 | grep "^[a-zA-Z0-9_].*$" > /tmp/x1
 
 apt-rdepends to be installed first in the internet computer if not already installed.
 The above command is for creating a list for all dependencies for aptoncd with the main aptoncd package.
 
 Next commands are
 
 root@ubuntu:/# for f in `cat /tmp/x1` ; do apt-cache show $f | grep Filename | cut -f 2 -d ' ' ; done >/tmp/x2
 
 mkdir mycache 
 [to keep the downloaded aptoncd package with all dependencies in the mycach folder under root]
 
 root@ubuntu:/# cd mycache
 
 root@ubuntu:/mycache# wget -B [http://np.archive.ubuntu.com/ubuntu/](http://np.archive.ubuntu.com/ubuntu/) -i /tmp/x2
 
 [if wget is not already installed then it is to be installed first before executing the above command]
 this command will start downloading packages & all dependencies of aptoncd application.
 
 Now copy the mycache folder to the home directory of the computers which have no internet connection and install it in those computers.
 
 In the internet computer also install the aptoncd and make backup of all packages with upgrades and dependencies and make a CD/DVD/ISO image. Carry them to the computers having no internet connection and by using aptoncd application restore the packages and upgrades with all dependencies.
 
 So by using only one computer with Internet one can install applications in other computers having no internet connection at all.

---

