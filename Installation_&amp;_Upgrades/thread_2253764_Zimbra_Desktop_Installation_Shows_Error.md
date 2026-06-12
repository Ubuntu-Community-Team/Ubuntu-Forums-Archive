---
title: "Zimbra Desktop Installation Shows Error"
date: 2014-11-22
forum: Installation &amp; Upgrades
---

### Post by Varun_C on 2014-11-22
Using the Zimbra Desktop Version 2.0.1
The following error is appearing.

The missing file **zdclient **is available in the given path. Still the error appears.
Please help.


Press "Enter" to launch Zimbra Desktop; Press "Ctrl-c" to exit: 
sh: 1: /opt/zimbra/zdesktop/linux/prism/zdclient: not found


Thanks.

---

### Post by nerdtron on 2014-11-22
What is the the permissions of the file?

```
ls -lah /opt/zimbra/zdesktop/linux/prism/zdclient 
```

---

### Post by Varun_C on 2015-02-05
Now the error is appearing like this

varun@VC-Ubuntu:~/Desktop/zdesktop_7_2_5_ga_b12038_linux_i686$ /opt/zimbra/zdesktop/linux/user-install.pl 
------------------------------
Choose the folder where you would like to install Zimbra Desktop's user data files, full path please [/home/varun/zdesktop]: 


------------------------------
Choose the folder where you would like to create desktop icon [/home/varun/Desktop]: 



Installing user data files...done
Initializing user data...done
Creating desktop icon...done
Zimbra Desktop has been installed successfully for user varun.

You can start Zimbra Desktop by double-clicking the desktop icon or by running the following command:
"/opt/zimbra/zdesktop/linux/prism/zdclient" -webapp "/home/varun/zdesktop/zdesktop.webapp" -override "/home/varun/zdesktop/zdesktop.webapp/override.ini" -profile "/home/varun/zdesktop/profile"

Press "Enter" to launch Zimbra Desktop; Press "Ctrl-c" to exit: 
varun@VC-Ubuntu:~/Desktop/zdesktop_7_2_5_ga_b12038_linux_i686$ Couldn't load XPCOM.





Thanks ..
Please help

---

### Post by MAFoElffen on 2015-02-05
Please explain how you are trying to run the install script... 

@ nerdtron-- If they are getting that error, a script has permission to execute, enough to tell them them forgot all the arguments when it was kicked off. I'm thinking if they just tried to double click on it, instead of from a terminal... If so, please help explain to them with a CLI terminal session with adding  an argument of a directory name in their personal home folder.

---

### Post by Varun_C on 2015-02-09
I was following the procedures provided by Zimbra.

Thanks..

---

