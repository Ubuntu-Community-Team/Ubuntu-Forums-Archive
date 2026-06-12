---
title: "Patched Pidgin with Xtraz: compile error"
date: 2008-05-04
forum: Installation &amp; Upgrades
---

### Post by cz7asm on 2008-05-04
Hi...
Does anybody know what these errors at the end may mean? I tried to compile pidgin with Xtraz support through checkinstall but it couldn't make a package because of...I don't know why. I have Ubuntu 8.04 with Gnome... and I executed checkinstall with "-D make install"

Thanks in advance for every advice

```

make[4]: Leaving directory `/home/cz7asm/Desktop/pidgin-2.4.1/pidgin/pixmaps/emotes/none'
make[3]: Leaving directory `/home/cz7asm/Desktop/pidgin-2.4.1/pidgin/pixmaps/emotes/none'
make[3]: Entering directory `/home/cz7asm/Desktop/pidgin-2.4.1/pidgin/pixmaps'
make[4]: Entering directory `/home/cz7asm/Desktop/pidgin-2.4.1/pidgin/pixmaps'
make[4]: Nothing to be done for `install-exec-am'.
test -z "/usr/share" || /bin/mkdir -p "/usr/share"
 /bin/bash /home/cz7asm/Desktop/pidgin-2.4.1/install-sh -c -m 644 'icons/hicolor/16x16/apps/pidgin.png' '/usr/share/icons/hicolor/16x16/apps/pidgin.png'
chmod: changing permissions of `/usr/share/icons/hicolor/16x16/apps/_inst.18490_': No such file or directory
 /bin/bash /home/cz7asm/Desktop/pidgin-2.4.1/install-sh -c -m 644 'icons/hicolor/22x22/apps/pidgin.png' '/usr/share/icons/hicolor/22x22/apps/pidgin.png'
chmod: changing permissions of `/usr/share/icons/hicolor/22x22/apps/_inst.18496_': No such file or directory
 /bin/bash /home/cz7asm/Desktop/pidgin-2.4.1/install-sh -c -m 644 'icons/hicolor/24x24/apps/pidgin.png' '/usr/share/icons/hicolor/24x24/apps/pidgin.png'
chmod: changing permissions of `/usr/share/icons/hicolor/24x24/apps/_inst.18502_': No such file or directory
 /bin/bash /home/cz7asm/Desktop/pidgin-2.4.1/install-sh -c -m 644 'icons/hicolor/32x32/apps/pidgin.png' '/usr/share/icons/hicolor/32x32/apps/pidgin.png'
chmod: changing permissions of `/usr/share/icons/hicolor/32x32/apps/_inst.18508_': No such file or directory
 /bin/bash /home/cz7asm/Desktop/pidgin-2.4.1/install-sh -c -m 644 'icons/hicolor/48x48/apps/pidgin.png' '/usr/share/icons/hicolor/48x48/apps/pidgin.png'
chmod: changing permissions of `/usr/share/icons/hicolor/48x48/apps/_inst.18514_': No such file or directory
make[4]: *** [install-nobase_dist_pidginiconsDATA] Error 1
make[4]: Leaving directory `/home/cz7asm/Desktop/pidgin-2.4.1/pidgin/pixmaps'
make[3]: *** [install-am] Error 2
make[3]: Leaving directory `/home/cz7asm/Desktop/pidgin-2.4.1/pidgin/pixmaps'
make[2]: *** [install-recursive] Error 1
make[2]: Leaving directory `/home/cz7asm/Desktop/pidgin-2.4.1/pidgin/pixmaps'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/cz7asm/Desktop/pidgin-2.4.1/pidgin'
make: *** [install-recursive] Error 1

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.


```

---

