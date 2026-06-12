---
title: "modem driver install?"
date: 2008-05-26
forum: Installation &amp; Upgrades
---

### Post by raker t on 2008-05-26
I might have found a driver for my dial up modem. It says it's a .run file. how can I install this? Comand line?
 For the sake of conversation, it's located in directory

/home/raker/opened

Do I need to be in the directory when installing a file or package?

---

### Post by iaculallad on 2008-05-26
> **raker t said:**
> I might have found a driver for my dial up modem. It says it's a .run file. how can I install this? Comand line?
 For the sake of conversation, it's located in directory

/home/raker/opened

Do I need to be in the directory when installing a file or package?

Try this:

Open the terminal, change directory to /home/raker/opened which will bring you to the directory where your .run file resides.

Code:

> cd /home/raker/opened

Make the .run file "executable"

Code:

> chmod +x your_filename_here.run

Then finally, type this in the terminal:

Code:

> ./your_filename_here.run

---

### Post by raker t on 2008-05-26
I did what you said, as close as I could, and this is what happened, further than I've gotten with other projects, thanks again. What do I do now? Should I be looking for a GUI type window to install this driver?The last sudo command is what I did, trying to get the "graphical installer" to start.
Thanks again, this is the farthest I've got on an install effort.

james@james-desktop:~$ cd /home/james/opened 
james@james-desktop:~/opened$ chmod +x cnxtinstall.run 
james@james-desktop:~/opened$ ./cnxtinstall.run 
Verifying archive integrity... All good. 
Uncompressing Linux drivers for Conexant modem chipsets Installer version 1.0.1 
Please run this installer as root. You can probably do it with the 
'sudo sh cnxtinstall.run' command. 
james@james-desktop:~/opened$ sudo sh cnxtinstall.run 
Password: 
Verifying archive integrity... All good. 
Uncompressing Linux drivers for Conexant modem chipsets Installer version 1.0.1 

If the graphical installer fails to start, you could try the terminal 
version that you can start with the following command: 

--- 
sh cnxtinstall.run -- --tty 
--- 

Alternatively, you could manually download and install the packages from the 
following pages: 

HSF: [http://www.linuxant.com/drivers/hsf/full/downloads.php](http://www.linuxant.com/drivers/hsf/full/downloads.php) 
HCF: [http://www.linuxant.com/drivers/hcf/full/downloads.php](http://www.linuxant.com/drivers/hcf/full/downloads.php) 
DGC: [http://www.linuxant.com/drivers/dgc/downloads.php](http://www.linuxant.com/drivers/dgc/downloads.php) 
RIPTIDE: [http://www.linuxant.com/drivers/riptide/downloads.php](http://www.linuxant.com/drivers/riptide/downloads.php) 
ALSA driver: [http://www.linuxant.com/alsa-driver](http://www.linuxant.com/alsa-driver) 

Trying to launch a web browser, please wait... 

The password asked by the installer is: c9b5d296254fac1dc45cd39be0159482 
sudo sh cnxtinstall.run -- --tty

---

