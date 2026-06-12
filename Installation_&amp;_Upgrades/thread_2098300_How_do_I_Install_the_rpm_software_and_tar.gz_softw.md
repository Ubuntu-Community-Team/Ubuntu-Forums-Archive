---
title: "How do I Install the rpm software and tar.gz software"
date: 2012-12-26
forum: Installation &amp; Upgrades
---

### Post by frhs on 2012-12-26
I was heard some softwares, and I have got they from Internet. their name is ***.tar.gz or ***.rpm   .    And I try google, but I do not know it yet...

so, ask you if you know...

---

### Post by frhs on 2012-12-26
And thank you very much if the answers are helpfully and usefully.

---

### Post by dino99 on 2012-12-26
ubuntu like debian use .deb packages, not .rpm

tar.gz are compressed files and you should not use them untill you know and understand what you are doing

[http://manpages.ubuntu.com/manpages/intrepid/man1/tar.1.html](http://manpages.ubuntu.com/manpages/intrepid/man1/tar.1.html)

---

### Post by CeltaWeb on 2012-12-26
For a bit of an explanation of rpm files.

> RPM was originally written in 1997 by Erik Troan and Marc Ewing for use in Red Hat Linux, RPM is now used in many GNU/Linux distributions. It has also been ported to some other operating systems, such as Novell NetWare (as of version 6.5 SP3) and IBM's AIX as of version 4..

Depending on what you are attempting to install you can normally find a .deb alternative which can be installed two ways.

[LIST]
[*]               To install a *.deb* file, simply double click on it, and then select **Install Package**
[*]               Alternatively, you can also install a *.deb* file by opening a terminal and typing: 						
[/LIST]
```
sudo dpkg -i package_file.deb
```

---

### Post by Cheesemill on 2012-12-26
You should stay clear off .rpm and .tar.gz files until you know what you are doing.

For more information on installing software:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by frhs on 2012-12-26
> **dino99 said:**
> ubuntu like debian use .deb packages, not .rpm

tar.gz are compressed files and you should not use them untill you know and understand what you are doing

[http://manpages.ubuntu.com/manpages/intrepid/man1/tar.1.html](http://manpages.ubuntu.com/manpages/intrepid/man1/tar.1.html)


But Why Ubuntu do not support they?

---

### Post by mörgæs on 2012-12-26
In Buntu the preferred way of installing is through a repository which is known to be of good quality. 

Downloading stuff from some place and installing is a bad habit from Windows.

Which kind of application are you looking for?

---

### Post by fdrake on 2012-12-26
> **frhs said:**
> But Why Ubuntu do not support they?

ubuntu supports them but you need to have some knowledge too while you build from source, o you compile your kernel. Can be dangerous and a security risk

---

### Post by agillator on 2012-12-26
rpm is a system used by Red Hat and Red Hat based distributions. deb is the system used by Debian and Debian based distributions such as Ubuntu. the tar.gz files you see are simply simply compressed archive files and can be/contain anything. 

In ubuntu one normally installs software from the various repositories using one of aptitude off spring such as apt-get. Most software you want can be installed this way, most but not all. If you will mention the specific software you are looking for someone will try to help. Otherwise, try searching (google, yahoo, whatever) for the software's home page and follow their instructions for installation, if you trust them of course.

---

