---
title: "Upgrading from 6.10(edgy)  to 7.04(feisty)"
date: 2007-09-14
forum: Installation &amp; Upgrades
---

### Post by jamesr on 2007-09-14
Hi,

I am upgrading from edgy to feisty but I have a separate home directory and a an additional vfat partition for my mozilla files (firefox). Can I assume that the upgrade will correctly handle thiese  modifactions. I believe it should but there have been several comments about modified systems giving errors.

---

### Post by reckless2k2 on 2007-09-14
i'm just throwing this out there but no. regular upgrades have shown issues under normal circumstances. now your adding in a complication that "may" be fine "if" the general upgrade goes well. 

there is an upgrade path but clean install is best. back up your stuff and make the magic happen.

---

### Post by jamesr on 2007-09-14
Hi,

This part of the reason that I upgrading, and  is to test out MondoRescue on 7.04. Since my /home is separate partition, it requires only backing the changes in the /etc directory or am I missing something. Is the fstab, since it uses UIUD transferable, or does it setup it independantly each. Perhaps I need to update my knowledge as well on the new style of fstab.

---

### Post by rsambuca on 2007-09-14
Unlike Windows, one of the benefits of linux is that you shouldn't be required to do constant re-installations.  Guess I am on the other side of the fence from reckless2k2.  I would do the standard upgrade.  Just make sure you use the recommended method of upgrading

[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

---

### Post by jamesr on 2007-09-15
Hi,

Unfortunately the Upgrade using the update manager needs a  relatively large amount of free space on the root drive. After a lot of playing about I had almost had generated enough free space. So I thought that I would use gparted to increase the partition. This was a bad thought on my part. The net result was the system is not recognising all of the drive.  Hopefully my backups of the other directories will work.

So I thought, since it looks as if I will have to start from Scratch. I downloaded the install disk. It boots ok but does not see the mouse so it is next to useless. I am now downloading the alternate CD to try that.

PS I will have to change my signature NO WORKING Ubuntu 6.10

GRRR!!!

---

### Post by jamesr on 2007-09-17
Hi Folks,

Thanks for the previous replies and suggestions. As I mentioned previously , I ended up having to try a complete new install. But the saga continues

The new installation using a new 7.04 Clean install disk / Live CD did not work.
Did not not work  for the alternative CD. Both asked for a additional CD, same name, and the name name of the install CD, I believe. Again unsuccessful.

Back to the beginning.
Re-install 6.10 needed the alternate CD because the mouse not recognised with the live CD, therefore could not use the live CD. Once installed from the Alternative CD, I needed to edit the xorg.conf file after boot to recognise the mouse
Re create the separate /home. Check that it basically worked again.
Select the update manager
Check that all update had been done, check the update manager version
and select the upgrade button and leave for a time.
Note at this point I had network/internet access.
Finish upgrade no problems noted.

Reboot  and went to main page after login. But now no internet access, network not seen. Using a terminal window find that NIC is seen
```
dmesg |grep eth0
sudo ifconfig -a
``` but no active address. After several attempts using the GUI, goto the CLI and a terminal window```
sudo dhclient
``` solved the problem i.e. a manual restart of DHCP. The file /etc/network/interfaces seems to be OK, but no auto restart of the network. Another problem to solve. Currently I need to do this every time I boot up.

A general comment, why on do upgrades on working systems, seem to cause problems i.e. the system   no longer works. I know that it quite impressive that I am able to keep old hardware still working but even Microsoft does not remove operating setups. Of course, with the exception of the Vista upgrades, where a lot of older drivers no longer work but I would not even try Vista on this PC.  I am not talking about hardware related problems but  software issues ie network no longer auto starting.
RANT over

I suppose I have to change my signature. Once I have done the other updates/testing  that required the upgrade to 7.04.

---

### Post by jamesr on 2007-09-17
Hi ,

Now I have file permission problems, sorry directory permission problems, I cannot write to additional directories that I created in separate partitions

and 

I know that I will have problems, getting a printer to print  which is directly attached to my router. 

I am sure that I can solve these problems. The printer is a case of finding my old notes.

 It never ends. Still not Feisty user yet.

---

