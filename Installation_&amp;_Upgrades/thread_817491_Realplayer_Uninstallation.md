---
title: "Realplayer Uninstallation"
date: 2008-06-03
forum: Installation &amp; Upgrades
---

### Post by Cody Jordan on 2008-06-03
I just recently installed a packet for Realplayer and I cannot find the packet to uninstall it.
Does anyone know what to search for???

---

### Post by unicorn_2003_1 on 2008-06-03
[http://ubuntuforums.org/showthread.php?t=681778]("http://ubuntuforums.org/showthread.php?t=681778")

Read into the post, the steps there seem promising. I haven't installed RealPlayer on my machine, using Mplayer with rm/rmvb codecs instead.

---

### Post by Riverside on 2008-06-04
> **Cody Jordan said:**
> I just recently installed a packet for Realplayer and I cannot find the packet to uninstall it.
Does anyone know what to search for???The RealPlayer executable is called realplay.

If you have installed a packaged version of RealPlayer but can't remember the package name, do:

user@localhost:~$ which realplay
/usr/bin/realplay

Next, you can find out which package /usr/bin/realplay (or whatever the result of your own "which realplay" command locates) was installed by, by doing:

user@localhost:~$ dpkg -S /usr/bin/realplay

That will show you the name of the package.

You can next fully uninstall that package, by doing:

user@localhost:~$ sudo apt-get purge packagename

(replacing "packagename" with your own previously identified RealPlayer package, obviously)

If you next want to install the latest RealPlayer version from the real.com web site, go to:

Go to:

[http://www.real.com/linux](http://www.real.com/linux)

Click the download link and save the file to a suitable location.

Next, make the file executable:

user@localhost:~$ chmod 744 RealPlayer11GOLD.bin

Next, run the file:

user@localhost:~$ sudo ./RealPlayer11GOLD.bin

Follow the defaults and it will be installed.  

You will need to keep a close eye on the real.com web site though and download and install new versions if new releases take place for security reasons, as applications installed manually from third party sources in this way are not automatically updated as Ubuntu packages installed using Ubuntu package management tools are.

---

