---
title: "file zilla upgrade"
date: 2008-10-21
forum: Installation &amp; Upgrades
---

### Post by namaster on 2008-10-21
3.1.4.1 New client and i am running old one. I am Newbie to linux and i saw somewhere it's always good to install using  synoptic manager. 

Any idea how to install new client? Or should i go ahead with sudo make and sudo make install and then install it? 

Running 3.0 and i am having time out after sometime while upload big files.

Thanks for help.

---

### Post by zeronothing on 2008-10-21
what you can do is install the newest client from the [[COLOR="Blue"]getdeb[/COLOR]]("http://www.getdeb.net") website. the getdeb website builds ubuntu packages (deb packages) which are easy to install. when you install them synaptic package manager will actually manage those packages as well. so if for instants you fell like uninstall filezilla you can do so with synaptic. also those packages from the website are just double click installs. but if you install the original filezilla from synaptic, you will have to uninstall it first. then install the ones from the getdeb website. I know this because I also like filezilla and use it quite frequently. the getdeb website also has many other programs to download as well. check it out, and let me know if you need anymore help.

---

### Post by namaster on 2008-10-21
So, do i need to uninstall old version first and then install new version?

Thanks for the quick help.

Edit: 3 downloads. Which one to download?

 Download:   filezilla  (1.1 MB)  ,  filezilla-common  (567.8 kB)  ,  filezilla-locales  (1.6 MB)

---

### Post by sethvath on 2008-10-21
You need all 3 download, the last 2 are dependencies of the first one. Install the common, locales and filezilla in that order. 

And yes remove the last one via synaptic or you might end up having multiple desktop menu for filezilla. If you have existing data on filezilla do a backup of the config files before you upgrade from getdeb.

---

### Post by namaster on 2008-10-21
> **sethvath said:**
> You need all 3 download, the last 2 are dependencies of the first one. Install the common, locales and filezilla in that order. 

And yes remove the last one via synaptic or you might end up having multiple desktop menu for filezilla. If you have existing data on filezilla do a backup of the config files before you upgrade from getdeb.

1. How do u take backup of configs?
2. Why in the same order? Just for my knowledge. So i don't always remain newbie.

Edit. I get error while installing locale. It says:

Error: Dependancy is not satisfiable: filezilla.

I did installed common properly. Also, how do i install filezilla package bec its tar.bz2 package. Do i need to use make install thing? 

Thanks for the help.

---

### Post by sethvath on 2008-10-21
If you have any config or preconfigured server addresses to save its in /usr/bin/filezilla or /home/yourusername/.filezilla

You could trial and error which one to install first since it will prompt you for the dependency. Normally you have to install the core dependencies like program-data, program-core first before you install the program. That is all to it, no exact science involved.

---

### Post by namaster on 2008-10-21
> **sethvath said:**
> If you have any config or preconfigured server addresses to save its in /usr/bin/filezilla or /home/yourusername/.filezilla

You could trial and error which one to install first since it will prompt you for the dependency. Normally you have to install the core dependencies like program-data, program-core first before you install the program. That is all to it, no exact science involved.

but how do i install tar.bz2 package? Because u cant install that thing using packet manager.

---

### Post by sethvath on 2008-10-22
Is this the link you downloaded from? [http://www.getdeb.net/app/FileZilla](http://www.getdeb.net/app/FileZilla)

Its a deb file not tar.gz2. To be sure i clicked both 32bit and 64bit and the download link shows a deb.

---

### Post by namaster on 2008-10-23
> **sethvath said:**
> Is this the link you downloaded from? [http://www.getdeb.net/app/FileZilla](http://www.getdeb.net/app/FileZilla)

Its a deb file not tar.gz2. To be sure i clicked both 32bit and 64bit and the download link shows a deb.

anh thanks. Somehow i got .tar one. All works good now. Thanks

---

