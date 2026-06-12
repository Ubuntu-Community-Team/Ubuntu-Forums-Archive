---
title: "Cannot use installed apps."
date: 2007-09-06
forum: Installation &amp; Upgrades
---

### Post by donnie616 on 2007-09-06
":(You will not be able to change your system settings in any way (install, remove or upgrade software), because this application needs special administrator (root) privileges. Please run it as root or through kdesu or sudo programs to be able to perform these actions"   

IEven with tha previoust error I got adept on th computer and tried ton run it and got the above.  I have no idea what is going on and most certainly do not know what to do next.  I do not know diference between root and me too well.  I need to be guided as to whatto do next CREATE a root acct?  HOW?

Thanks

---

### Post by o3rat on 2007-09-06
Hi, i am also new, but i will try to explain from my understanding.

When you installed ubuntu all the system files "Filesystem" was create by root. i think this is for security purposes. Only root can edit core system files. So in that sense root is already created. To run apps as root open terminal and type ```
su - root 
``` 

For most apps that require root privileges its easier to just do ```
sudo "command"
``` then enter in your user password.


Hope this helps.

---

