---
title: "Installing BIN?"
date: 2005-02-05
forum: Installation &amp; Upgrades
---

### Post by Uncle_Buck on 2005-02-05
Hi, 

Just installed Ubuntu, pretty new to the whole linux experience so sorry if this is a increidbly silly question :D

However I downloaded AMSN and I'm not allowed to run it. Ubuntu is saying it could be a security risk and so on. I get the following message 

> 
The filename "amsn-1.94-linux-installer.bin" indicates that this file is of type "unknown". The contents of the file indicate that the file is of type "executable". If you open this file, the file might present a security risk to your system.

Do not open the file unless you created the file yourself, or received the file from a trusted source. To open the file, rename the file to the correct extension for "executable", then open the file normally. Alternatively, use the Open With menu to choose a specific application for the file. 

Can anyone tell me what I'm meant to do. Also where can I change security settings so that I don't have this sort of hassle in future? 

Thanks :)

---

### Post by sunscape on 2005-02-05
sh ./program... blah .. blah . blah.bin


Why not use gaim?

---

### Post by DJ_Max on 2005-02-05
Hello,
If you downloaded the file from amsn.sourceforge.net, you have nothing to worry about.
Be sure to make the file excutable,```
chmod a+x amsn-1.94-linux-installer.bin
```

BUT, to save the trouble, download the latest version of their .deb file.
[http://packages.debian.org/unstable/x11/amsn](http://packages.debian.org/unstable/x11/amsn)

And issue this command to the appropiate file directory.
```
sudo dpkg -i PACKAGE.deb
``` 

Of course PACKAGE is the filename.

---

