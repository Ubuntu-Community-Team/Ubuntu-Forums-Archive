---
title: "When is the archive updated ?"
date: 2008-02-04
forum: Installation &amp; Upgrades
---

### Post by oygle on 2008-02-04
I would have expected the latest version of KMyMoney to be in the archives by now, at [http://archive.ubuntu.com/ubuntu/pool/universe/k/kmymoney2/](http://archive.ubuntu.com/ubuntu/pool/universe/k/kmymoney2/)

Apparently it has been in the debian repositories for a while now. How does it usually get into the Ubuntu archives, and how long does it usually take from the date a package is updated ?

The new version of KMyMoney was released on the 20th Dec 2007. (version 0.8.8 ).

---

### Post by luisromangz on 2008-02-04
In the repositories for a given Ubuntu version, there are no version updates for the pacakges included, only security fixes. You say about the debian repositories, but of course the unstable ones. Once a Ubuntu version gets released, its repositories are "stabilized".

---

### Post by oygle on 2008-02-04
So, are you saying that for Ubuntu 7.10, there won't be _any_ new versions of _any packages_ updated to the Ubuntu archive ?

For example, if Firefox goes to a new version and is stable, it won't be available in Ubuntu until the next release of Ubuntu ?

---

### Post by zvacet on 2008-02-04
You have deb file [here](https://sourceforge.net/project/showfiles.php?group_id=4708).

---

### Post by oygle on 2008-02-04
> **zvacet said:**
> You have deb file [here](https://sourceforge.net/project/showfiles.php?group_id=4708).

Thanks, but I wouldn't have a clue how to compile it. (or whatever has to be done ?).

---

### Post by zvacet on 2008-02-05
You don´t have to compile it.It is deb file allready.Download** kmymoney2_0.8.8-1_i386.deb file **and install it.

---

### Post by oygle on 2008-02-05
To 'install/build' it, requires the 'make' command, which automatically determines which pieces of a large program need to be _recompiled_, and issues the commands to _recompile_ them.

That, in anyones language, is compiling.    :)

---

### Post by Partyboi2 on 2008-02-05
With a deb file all you have to do is download the deb and either double click on it and select install package. (You may need to install a few other packages to satisfy dependencies)
or you can download the package and open a terminal and change directory to where the package is (prob Desktop) and install it with
```
sudo dpkg -i <package name>
```
So try downloading the deb package not the tar.bz2 package
You can get the deb from [here]("http://downloads.sourceforge.net/kmymoney2/kmymoney2_0.8.8-1_i386.deb?modtime=1198264751&big_mirror=0")

---

### Post by oygle on 2008-02-06
Thanks for the tips, but I'm not that confident to be able to do an actual install. There are no definitive docs on how to do it, and [this thread from the KMyMoney mailing lists]("http://sourceforge.net/mailarchive/message.php?msg_id=4a830c6d0712191436k6e8af097kddf8ff0455ee1ec6%40mail.gmail.com") , shows a few different methods.

Those people know what they are doing.  :)

---

### Post by zvacet on 2008-02-06
> Thanks for the tips, but I'm not that confident to be able to do an actual install. There are no definitive docs on how to do it


We are not tolking about some spacific program,but how to instal**l any** deb file.We described you how to install it and now is your move.Maybe you want to read [this](http://www.cutlersoftware.com/ubuntuinstall/).

---

