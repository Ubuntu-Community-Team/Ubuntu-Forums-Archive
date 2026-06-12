---
title: "Ubuntu Distro Versions"
date: 2013-06-07
forum: Installation &amp; Upgrades
---

### Post by BStrizzy on 2013-06-07
Hey all, 

I have a couple of questions about installing software on different versions of ubuntu. my first is that I am a 10.04.4 server user and have been testing out some software on a vm running 12.04.4. The instructions for apps like openfire and OCS inventory are under ubuntu 12.04 installs. I am testing it now in 10.04.4 server but would you recommend this? should I absolutely be using version specified in the instructions or guide? What big problems if I have any would I be running into?

Thanks guys.

---

### Post by 2F4U on 2013-06-07
The most likely issue when you install software for 12.04 on 10.04 will probably be dependency issues, because the newer software may require newer libraries. This can get very serious and may even render your system unusable.
If you install older software, i.e. software dedicated to be used on 10.04, you shouldn't be running into dependency issues, but the software may lack functionality only available in later versions.

---

### Post by BStrizzy on 2013-06-07
Ok I understand. Im assuming when i'm looking for particular software there will be a requirement section saying what version it will be best installed on? or would I have to do my own homework on that part?

---

### Post by grahammechanical on 2013-06-07
Each version of Ubuntu has its own software repositories. When we install software through the Ubuntu Software Centre it will bring in all the dependencies (libraries). We can also add a Personal Package Archive (PPA) for a particular application that we might want or a newer version of an application than that in the software centre. In this case it is the responsibility of the package maintainer (developer) to make sure the package contains all the necessary libraries. Further more, we can download a .deb file and if we use the software centre then there is a good chance that all the necessary libraries will be installed as well. Also apt-get (in a terminal) is smart. It will give warnings.

The issue that you will run into is when an application requires a certain version of a library and installing the application will remove the existing version of the library which will break other applications. Then apt-get will refuse to install the application. This is why it is best to install applications from the repository of the version of Ubuntu installed.

If you are running 12.04 in a virtual machine that is running on 10.04.4 then the versions of the applications are 12.04 specific. They are not actually running in 10.04.4, are they? Why should there be a problem? You are running 12.04 version applications on 12.04 and not on 10.04.

Where you will have difficulties is if you want to run those 12.04 version applications on 10.04. The server version of 10.04 is still supported but the desktop version of 10.04 has reached End Of Life. So, you will have difficulty if you want to install the Ubuntu desktop on  to that 10.04 server edition.

Regards.

---

