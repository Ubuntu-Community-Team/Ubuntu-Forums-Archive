---
title: ":: installing compressed .tar files::"
date: 2005-08-06
forum: Installation &amp; Upgrades
---

### Post by mohsin on 2005-08-06
hello guyz i m newbie to forum and ubuntu world ..well could any one plz tell me how to install the compressed files in ubuntu .. i downloaded some .tar extension files these are compressed now installe ubuntu i m having XP also .. 


 so .. plz provide help .. any tutorial link if in this forum give me link 

 plz rpely thnx in advance  O:)

---

### Post by hypnos on 2005-08-06
Type in terminal
```
tar -x name_of_the_package.tar.gz
```

---

### Post by Sam on 2005-08-06
*.tar:
```
$ tar xvf <filename>
```

*.tar.gz, *.tgz:
```
$ tar xzvf <filename>
```

*.tar.bzip, *.tar.bz:
```
$ tar xjvf <filename>
```


More info:
```
$ man tar
```

---

### Post by mohsin on 2005-08-06
[QUOTE=][/QUOTE]
 thnnx a lot guyz .. really thankfull ..

---

### Post by Omnios on 2005-08-06
Some Linux command help files --tar

[http://www.linuxdevcenter.com/linux/cmd/cmd.csp?path=t/tar](http://www.linuxdevcenter.com/linux/cmd/cmd.csp?path=t/tar)

[http://www.ss64.com/bash/tar.html](http://www.ss64.com/bash/tar.html)

---

### Post by mohsin on 2005-08-10
helpful

---

### Post by varunus on 2005-08-10
You should just be able to double click a tar file and it will open in file-roller, a program very similar to winzip classic and included with GNOME.  It can handle zip, tar, gz, bz2, and rar, I think...maybe more.

However, if you have a tar file because you are trying to install a program, this is not the Linux way.  Ubuntu Linux uses something called a "repository" to install programs.  There is a program found in System->Administration called "Synaptic Package Manager", this program will allow you to install up to 16,000 programs.  You simply add repositories to your computer, and Synaptic will show you every program you could possibly install.  Its a nice method; no reboots, and everything (install, uninstall) can be done from one place.

Make sure to enable some basic extra repositories you'll need first, though:
[http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories)

The guide itself has some good info, like how to enable codecs for file formats, and how to install some software you might need.

---

### Post by Levo75 on 2007-11-11
Thanx, you guys win many internets.

---

