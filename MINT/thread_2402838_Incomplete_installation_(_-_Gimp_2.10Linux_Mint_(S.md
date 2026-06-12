---
title: "Incomplete installation :( - Gimp 2.10/Linux Mint (Sylvia)"
date: 2018-10-04
forum: MINT
---

### Post by drpeppercan on 2018-10-04
Hi all,


I followed the commands given at the Gimp web site (flatpak install [https://flathub.org/repo/appstream/org.gimp.GIMP.flatpakref](https://flathub.org/repo/appstream/org.gimp.GIMP.flatpakref), and flatpak run org.gimp.GIMP//stable)
Then the only one item I have been able to find is its shortcut in the main menu.


I did a search in the Terminal to no avail:


```
/home $ find /home GIMP
find: ‘GIMP’: No such file or directory

```

I also did a seach with the File Browser. I did find the .config dir, but there's no GIMP dir inside.



After using this new installation of Gimp some more, I found out that the filters do not do a thing!

I guess this might suggest that the installation did not include a plug ins folder. After all, I can't find the GIMP 2.10 dir anywhere. I wonder how's running this version.

I opened the properties window of the shortcut from the main menu. It shows this path:

/usr/bin/flatpak run --branch=stable --arch=x86_64 --command=gimp-2.10 --file-forwarding org.gimp.GIMP @[@U]("https://github.com/U") %U @@


Any ideas?


Thanks!
[COLOR=#24292e]
[/COLOR]

---

### Post by Frogs Hair on 2018-10-04
If Mint's repositories are still Ubuntu based you can remove the flatpak and install the .deb from the package manager. I use Deepin on one computer which is slowly moving  its default applications to the flatpak format , but I've stayed away from Flathub so far. Ubuntu is offering[ snap]("https://snapcraft.io/store") applications instead of flatpak though flatpacks are available.

---

### Post by drpeppercan on 2018-10-04
Oh, this is great to know!
Thank you for the link :)

Now I have to find out how to remove the installation with Flatpak.

---

### Post by Frogs Hair on 2018-10-05
[http://docs.flatpak.org/en/latest/using-flatpak.html](http://docs.flatpak.org/en/latest/using-flatpak.html)

---

### Post by drpeppercan on 2018-10-05
Hi Yavie,

So, I first installed Snaps with this
```
sudo apt install snapd
```

```
Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  snapd
0 upgraded, 1 newly installed, 0 to remove and 167 not upgraded.
Need to get 12.4 MB of archives.
After this operation, 57.8 MB of additional disk space will be used.
Get:1 http://archive.ubuntu.com/ubuntu bionic-updates/main amd64 snapd amd64 2.34.2+18.04 [12.4 MB]
Fetched 12.4 MB in 4s (2,772 kB/s)
Selecting previously unselected package snapd.
(Reading database ... 284136 files and directories currently installed.)
Preparing to unpack .../snapd_2.34.2+18.04_amd64.deb ...
Unpacking snapd (2.34.2+18.04) ...
Setting up snapd (2.34.2+18.04) ...
Created symlink /etc/systemd/system/multi-user.target.wants/snapd.autoimport.service &#8594; /lib/systemd/system/snapd.autoimport.service.
Created symlink /etc/systemd/system/multi-user.target.wants/snapd.core-fixup.service &#8594; /lib/systemd/system/snapd.core-fixup.service.
Created symlink /etc/systemd/system/multi-user.target.wants/snapd.seeded.service &#8594; /lib/systemd/system/snapd.seeded.service.
Created symlink /etc/systemd/system/cloud-final.service.wants/snapd.seeded.service &#8594; /lib/systemd/system/snapd.seeded.service.
Created symlink /etc/systemd/system/multi-user.target.wants/snapd.service &#8594; /lib/systemd/system/snapd.service.
Created symlink /etc/systemd/system/timers.target.wants/snapd.snap-repair.timer &#8594; /lib/systemd/system/snapd.snap-repair.timer.
Created symlink /etc/systemd/system/sockets.target.wants/snapd.socket &#8594; /lib/systemd/system/snapd.socket.
Created symlink /etc/systemd/system/final.target.wants/snapd.system-shutdown.service &#8594; /lib/systemd/system/snapd.system-shutdown.service.
**snapd.snap-repair.service is a disabled or a static unit, not starting it**.
Processing triggers for man-db (2.8.3-2) ...
drpeppercan@drpeppercan-Predator-G3-710:~$ sudo snap install gimp
gimp 2.10.6 from 'snapcrafters' installed
drpeppercan@drpeppercan-Predator-G3-710:~$ find gimp
find: ‘gimp’: **No such file or directory**



```

This doesn't look good, does it? :(

Should I give up on Snaps?

---

### Post by Frogs Hair on 2018-10-05
No need to use snap or flatpak. Remove the snap and install gimp from the repository.

```
sudo snap remove gimp
```

 ```
sudo apt install gimp
```

---

### Post by drpeppercan on 2018-10-05
Unfortunately that method only installs 2.8 :(

Given the previous attempts, I guess I have no choice.

---

### Post by drpeppercan on 2018-10-05
I tried it again with the Flatpak link at the Gimp web site, this time it worked! :)

---

### Post by ajgreeny on 2018-10-05
There is a ppa for gimp-2.10 which I am using in Xubuntu 18.04 so it will possibly/probably work fine in Mint 19, which I think is your version.

Try command ```
sudo add-apt-repository ppa:otto-kesselgulasch/gimp
``` the update the repos and upgrade with ```
sudo apt update
sudo apt upgrade
``` If you have the standard gimp-2.8 version it should upgrade to 2.10 which for me has been working without any problems.

---

### Post by Frogs Hair on 2018-10-05
> **drpeppercan said:**
> Unfortunately that method only installs 2.8 :(

Given the previous attempts, I guess I have no choice.

I'm running a newer version under the hood and didn't think of that . Glad it worked out for you and if there any problems try the PPA above with the repository version.

---

### Post by drpeppercan on 2018-10-05
Thanks for sharing ajgreeny :)

---

