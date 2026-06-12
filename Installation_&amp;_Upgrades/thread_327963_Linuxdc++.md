---
title: "Linuxdc++"
date: 2006-12-30
forum: Installation &amp; Upgrades
---

### Post by durus on 2006-12-30
I follows the wiki at 
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_File_share_utility_.28LinuxDC.2B.2B.29]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_File_share_utility_.28LinuxDC.2B.2B.29")

>  How to install File share utility (LinuxDC++)

    * Read #General Notes 

wget -c [http://easylinux.info/uploads/linuxdcpp.tar.gz](http://easylinux.info/uploads/linuxdcpp.tar.gz)
sudo tar zxvf linuxdcpp.tar.gz -C /opt
gksudo gedit /usr/share/applications/linuxdcpp.desktop

    * Insert the following lines into the new file 

[Desktop Entry]
Encoding=UTF-8
Name=LinuxDC++
Exec=linuxdcpp
Terminal=false
Type=Application
StartupNotify=true
Icon=/opt/linuxdcpp/pixmaps/linuxdcpp.png
Categories=Application;Network;

    * Save the edited file 

    * Applications -> Internet -> LinuxDC++ 

I can start dc with the console if i do it like this:
cd /opt/linuxdcpp/
./linuxdcpp 
but not by writing linuxdcpp, how shuld i modify  /usr/share/applications/linuxdcpp.desktop to get dc to start ?

And how can i uninstall this application, if i don't like it ?

---

### Post by KenSentMe on 2006-12-30
You can edit the menu options with System - Preferences - Menu something (i'm not on english ubuntu) to open the right binary from the menu. For removing the program just delete it from the menu and delete the folder with the following command:

sudo rm -Rf /opt/linuxdcpp

You need to fill in your own password when asked for.

---

### Post by WakkiTabakki on 2006-12-30
The Exec-line in the desktop file assumes you have /opt/linuxdcpp in your PATH-variable...
So do this:
```
gksudo gedit /usr/share/applications/linuxdcpp.desktop
```

And edit the Exec-line to
```
Exec=/opt/linuxdcpp/linuxdcpp
```


That should do it.

/N

---

### Post by durus on 2006-12-30
I have already tested that, the GUI tries to start but then disappears.

---

### Post by blackmh on 2006-12-30
I have linuxdc++ installed by automatix and works better than windows version :)

---

### Post by WakkiTabakki on 2007-01-09
> **durus said:**
> I have already tested that, the GUI tries to start but then disappears.

Apparently it assumes default install directory to be /use/share (or something) so it can't find the resources.

1. Create a shell script in the linuxdcpp folder and name it start_dcpp.sh (as root):
```

#!/bin/sh
cd /opt/linuxdcpp
./linuxdcpp &

```
Replace /opt/ with the path to wherever the app is installed

2. Give the script execute privileges
```
sudo chmod 755 start_dcpp.sh
```

3. Change the app link (as root):
Open the file ```
/usr/share/applications/linuxdcpp.desktop
```
and change the Exec line to
```
Exec=/opt/linuxdcpp/start_dcpp.sh
```

Good luck
/N

---

