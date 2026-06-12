---
title: "Ubuntu Kickstart and the corrupt Packages message"
date: 2012-06-25
forum: Installation &amp; Upgrades
---

### Post by deepuvijayans on 2012-06-25
[B]During Kicsktart installation of Ubuntu 12.04 lts alternate i came across with this 
[/B]



Deboot strap Warning


Warning:

* [http://server/ubuntu12.04/dists/precise/restricted/binary-i386/Packages](http://server/ubuntu12.04/dists/precise/restricted/binary-i386/Packages) was corrupt”*




*I had tried to mount in different folder but after that it shows same warning*


*This is the only warning showing rest of all works fine*
[I]Plz help me with this 
[/I]

---

### Post by deepuvijayans on 2012-06-28
Hi,

I manually Resolved this problem
Just create a file named Packages in that particular directory

touch /var/www/ubuntu12.04/dists/precise/restricted/binary-i386/Packages

:D:D:D;)

---

### Post by thenonos on 2012-10-09
Hi,

I have the same problem...

Where did you place "touch ...." in your ks.cfg ? in the %post ?

You didn't mount an ISO file ?

Thanks a lot

---

### Post by sdpagent on 2012-12-20
> **thenonos said:**
> Hi,

I have the same problem...

Where did you place "touch ...." in your ks.cfg ? in the %post ?

You didn't mount an ISO file ?

Thanks a lot

I'm not the person who posted the resolution, but Im 99.9% sure he meant that you should use the 'touch' command to create an empty file called 'Packages'. The same effect would be done if you navigated to the correct directory, and used the command 'vi Packages' and then just saved and quit without writing anything. If you are using a GUI, then you could just right click in the directory and 'create new document' and name it Packages.

I hope that helps,
Stu

---

