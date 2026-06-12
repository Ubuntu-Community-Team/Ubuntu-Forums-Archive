---
title: "graphics not functioning after upgrade to Ubuntu 16.04.2 LTS"
date: 2017-04-02
forum: Installation &amp; Upgrades
---

### Post by tevang2 on 2017-04-02
Greetings,

I had before Ubuntu 14.10 on my laptop but after the upgrade I did, I see a black screen after the boot loading finishes. However I can switch to text mode with ctrl+alt+F1. Can someone troubleshoot me please to repair the graphics? I have the feeling that must be something simple.

thank you in advance!

---

### Post by ajgreeny on 2017-04-02
What hardware, particularly the graphics card do you have?

---

### Post by tevang2 on 2017-04-02
I have a Lenovo laptop with the onboard VGA (Haswell-ULT Integrated Graphics Controller) plus GeForce 840M.

---

### Post by ajgreeny on 2017-04-03
Try booting with the nomodeset option as a start to see if that gets you a low resolution GUI from which you can install the recommended nvidia proprietary driver for that Geforce card by using Additional Drivers.

You can set the nomodeset option from the grub menu, if you see it, for this single boot, and following that, the addition of the driver may get you a full GUI.

---

### Post by tevang2 on 2017-04-04
I added "nomodeset" as shown in this photo:

[https://www.dropbox.com/s/6nyp2vm3zj0pzz0/IMG_20170405_001059.jpg?dl=0](https://www.dropbox.com/s/6nyp2vm3zj0pzz0/IMG_20170405_001059.jpg?dl=0)

but whenever I enter my password to login the screen turns black for a second and brings me back to the login menu as show in this photo:

[https://www.dropbox.com/s/13s7cuc02oioxga/IMG_20170405_000716.jpg?dl=0](https://www.dropbox.com/s/13s7cuc02oioxga/IMG_20170405_000716.jpg?dl=0)

The same happens if I add "nomodeset *quiet splash*".

---

### Post by ajgreeny on 2017-04-05
Can you still login as user to the command line from Ctrl+Alt+F1?

If so, please do so and run command ```
ls -la | less
``` which will allow you to scroll up and own the output with up/down cursor keys to see if any files or folders do not belong to you as user.

There should be only one that shows "root root" in the output, near the top, probably the second entry, and it ends with .. which is the /home folder, not /home/user but the main /home, so don't get confused by the naming here.

---

### Post by tevang2 on 2017-04-05
In which directory should I do ls -la?

---

### Post by ajgreeny on 2017-04-05
Your own home directory which is where you will be when you login to the command line of Ctrl+Alt+F1.
Don't change directory, just run that command ```
ls -la | less
```
I am looking for any folders or files that belong to a user other than you, particularly to root.

---

### Post by tevang2 on 2017-04-05
Only the following files in my home folder do not belong to me (and belong to the root):
.dbus
.gvfs
.pip

---

### Post by ajgreeny on 2017-04-06
I have no idea what .pip might be ; have you installed some package or application called pip or similar for which this might be a configuration folder or file?
However, the ownership of the other two folders is incorrect and they should be owned by you as user like almost everything else, and should be completely invisible to others with permissions from that command shown similar to
```
drwx------   3 tevang2  tevang2  4096 Mar 29  2013 .dbus
drwx------   2 tevang2  tevang2  4096 Mar 29  2013 .gvfs
```
Try running command ```
sudo chown -R tevang2:tevang2 /home/tevang2
```I am calling your username in Ubuntu **tevang2** but if it is something else change that chown command to the correct name in the three places where I used **tevang2**.
This will make everything in your home owned by you, as it must be, and may solve your login to GUI problem.
We may then need to consider why those folders were not owned by you in the first place.

---

### Post by tevang2 on 2017-04-06
the change of ownership doesn't resolve the problem. Btw, pip is the python installer of Anaconda.

---

