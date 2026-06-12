---
title: "Broken packages"
date: 2010-10-11
forum: Installation &amp; Upgrades
---

### Post by bogedy on 2010-10-11
Yesterday, I upgraded to Ubuntu 10.10. Before then, Ubuntu 10.04 had issues installing/removing package and programs. Whenever I would do that, it would give me an error saying that it failed, but really it worked and I actually had Removed/Installed the program. Now I'm on Ubuntu 10.10 netbook and I actually cant Upgrade, Install, or remove anything. I have an error message in the top right corner that says: An error occured, please run package manager from the right click menu or apt-get in a terminal to see what is wrong. The error message was: 'Error: BrokenCount >0'This usually means that your installed packages have unmet dependencies. whenever I run the update manager and click install updates it says: The package system is broken

Check if you are using third party repositories. If so disable them, since they are a common source of problems.
Furthermore run the following command in a Terminal: apt-get install -f.

I run sudo apt-get install -f (apt-get install -f asks for root permissions) and the terminal says:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libavutil49 libdvbpsi5 libx264-85 libmodplug0c2 libebml0 libmpcdec3 libmatroska0
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libqt4-assistant
The following packages will be upgraded:
  libqt4-assistant
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/46.4kB of archives.
After this operation, 8,192B disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 200289 files and directories currently installed.)
Preparing to replace libqt4-assistant 4:4.6.2-0ubuntu5 (using .../libqt4-assistant_4%3a4.7.0-0ubuntu4_i386.deb) ...
Unpacking replacement libqt4-assistant ...
dpkg (subprocess): unable to execute old post-removal script (/var/lib/dpkg/info/libqt4-assistant.postrm): Exec format error
dpkg: warning: subprocess old post-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
dpkg: error processing /var/cache/apt/archives/libqt4-assistant_4%3a4.7.0-0ubuntu4_i386.deb (--unpack):
 there is no script in the new version of the package - giving up
Errors were encountered while processing:
 /var/cache/apt/archives/libqt4-assistant_4%3a4.7.0-0ubuntu4_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by bogedy on 2010-10-11
When I run synaptic package manager it says: You have 2 broken packages on your system!

Use the "Broken" filter to locate them.

I go under edit and hit fix broken packages, and then after a second at the bottom it says succesfully fixed dependency problems. This repeats every time i start synaptic

---

