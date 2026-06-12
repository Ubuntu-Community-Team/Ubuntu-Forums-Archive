---
title: "dpkg warnings"
date: 2010-11-19
forum: Installation &amp; Upgrades
---

### Post by kayvee on 2010-11-19
My ubuntu installation was upgraded from Jaunty to Karmic to Lucid to Maverick. I think there was some issue at some point and now every time I run an apt-get or dpkg command, I see these "warnings":
```

warning, in file '/var/lib/dpkg/status' near line 49207 package 'virtualbox-3.0':
 error in Version string '3.0.14-58977_Ubuntu_jaunty': invalid character in revision number
warning, in file '/var/lib/dpkg/status' near line 49208 package 'virtualbox-3.0':
 error in Config-Version string '3.0.14-58977_Ubuntu_jaunty': invalid character in revision number
warning, in file '/var/lib/dpkg/available' near line 54561 package 'virtualbox-3.0':
 error in Version string '3.0.14-58977_Ubuntu_jaunty': invalid character in revision number

```

Since these are simply warnings, I never really had any problems as such. However, I would like to fix them if I can. Any help is appreciated.

---

### Post by sikander3786 on 2010-11-19
Try,

```
sudo dpkg --clear-avail
```

And the warnings might go away.

---

### Post by kayvee on 2010-11-19
> **sikander3786 said:**
> Try,

```
sudo dpkg --clear-avail
```

And the warnings might go away.

Thanks for the quick reply.
I tried that command. But how do I know it worked? I usually see those warning messages only when I install/upgrade something. Since I do not have any more packages to upgrade, is there is a quick way to check if the warnings disappeared?

---

### Post by sikander3786 on 2010-11-19
You can wait till the next time you need to install a package.

Or, install any package and later remove that e.g,

```
sudo apt-get install vlc
```

See if errors are reported or not and then remove it.

```
sudo apt-get remove vlc
```

---

### Post by kayvee on 2010-11-19
```
sudo dpkg --clear-avail
```
The above command helped to some extent. It got rid of one of the three warnings. Now I am left with these two:
```
warning, in file '/var/lib/dpkg/status' near line 49207 package 'virtualbox-3.0':
 error in Version string '3.0.14-58977_Ubuntu_jaunty': invalid character in revision number
warning, in file '/var/lib/dpkg/status' near line 49208 package 'virtualbox-3.0':
 error in Config-Version string '3.0.14-58977_Ubuntu_jaunty': invalid character in revision number

```

---

### Post by sikander3786 on 2010-11-19
You need to edit the file and remove the offensive characters manually.

Make a backup of the existing file. (However you can generate a new file whenever you want, it is a good habit to backup before editing)

```
sudo cp /var/lib/dpkg/status /var/lib/dpkg/status.bad
```

Edit,

```
gksudo gedit /var/lib/dpkg/status
```

Go to line 49207 and line 49208. Both contain an invalid character. Remove it, save and close and again try to install a package.

---

### Post by kayvee on 2010-11-19
But I did not find any invalid characters there... Here is that chunk:
```

Package: virtualbox-3.0
Status: deinstall ok config-files
Priority: optional
Section: non-free/misc
Installed-Size: 86564
Maintainer: Sun Microsystems, Inc. <info@virtualbox.org>
Architecture: i386
Version: 3.0.14-58977_Ubuntu_jaunty
Config-Version: 3.0.14-58977_Ubuntu_jaunty
Replaces: virtualbox
Provides: virtualbox
Depends: libc6 (>= 2.7), libcurl3 (>= 7.16.2-1), libgcc1 (>= 1:4.1.1), libpython2.6 (>= 2.6), libqt4-network (>= 4.5.0~+rc1), libqtcore4 (>= 4.5.0~+rc1), libqtgui4 (>= 4.5.0~+rc1), libsdl1.2debian (>= 1.2.10-1), libssl0.9.8 (>= 0.9.8f-5), libstdc++6 (>= 4.2.1), libx11-6, libxcursor1 (>> 1.1.2), libxext6, libxml2 (>= 2.6.27), libxmu6, libxslt1.1 (>= 1.1.18), libxt6, zlib1g (>= 1:1.1.4), psmisc, adduser
Pre-Depends: debconf (>= 1.1) | debconf-2.0
Recommends: libasound2, libpulse0, libsdl-ttf2.0-0, dkms, linux-headers, gcc, make, binutils, libhal1 (>= 0.5), pdf-viewer, libgl1, python-central
Conflicts: virtualbox, virtualbox-ose
Conffiles:
 /etc/init.d/vboxdrv 0d4cddf5ed0f7caa39f3c36bc2258184
Description: Sun VirtualBox
 VirtualBox is a powerful PC virtualization solution allowing you to run a
 wide range of PC operating systems on your Linux system. This includes
 Windows, Linux, FreeBSD, DOS, OpenBSD and others. VirtualBox comes with a broad
 feature set and excellent performance, making it the premier virtualization
 software solution on the market.
Python-Version: >= 2.4

```

I deleted that entire chunk. And now the warning messages disappeared!
Thank you.

---

### Post by sikander3786 on 2010-11-19
> Version: 3.0.14-58977_Ubuntu_jaunty
Config-Version: 3.0.14-58977_Ubuntu_jaunty


The issue lies somewhere in these 2 lines but I can't figure how they should look like. I am not on Ubuntu to check how it looks like on my install.

Anyways, glad to know the issue is sorted for you :-)

You can mark this thread Solved using [COLOR="Red"]**Thread Tools**[/COLOR] near the top of this page.

Happy Ubuntu-ing!

---

### Post by beernarrd on 2011-01-20
> **sikander3786 said:**
> You need to edit the file and remove the offensive characters manually.
....
You DO NOT need to edit anything manualy:

Do the following:

[LIST=1]
[*]sudo dpkg --clear-avail
[*]sudo dpkg -l > /dev/null
[*]For every package that is still listed, type: sudo apt-get purge nameOfThePackage
[/LIST]
Regards,
BB

---

### Post by beernarrd on 2011-01-20
> **sikander3786 said:**
> You need to edit the file and remove the offensive characters manually.
....
You DO NOT need to edit anything manualy:

Do the following:

[LIST=1]
[*]sudo dpkg --clear-avail
[*]sudo dpkg -l > /dev/null
[*]For every package that is still listed, type: sudo apt-get purge nameOfThePackage
[/LIST]
Regards,
BB

---

### Post by beernarrd on 2011-01-20
> **sikander3786 said:**
> You need to edit the file and remove the offensive characters manually.
....
You DO NOT need to edit anything manualy:

Do the following:

[LIST=1]
[*]sudo dpkg --clear-avail
[*]sudo dpkg -l > /dev/null
[*]For every package that is still listed, type: sudo apt-get purge nameOfThePackage
[/LIST]
Regards,
BB

---

### Post by beernarrd on 2011-01-20
> **sikander3786 said:**
> You need to edit the file and remove the offensive characters manually.
....
You DO NOT need to edit anything manualy:

Do the following:

[LIST=1]
[*]sudo dpkg --clear-avail
[*]sudo dpkg -l > /dev/null
[*]For every package that is still listed, type: sudo apt-get purge nameOfThePackage
[/LIST]
Regards,
BB

---

### Post by same.500 on 2011-11-02
):P thanks .

---

