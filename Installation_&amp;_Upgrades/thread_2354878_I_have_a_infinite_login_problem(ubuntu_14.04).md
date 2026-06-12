---
title: "I have a infinite login problem(ubuntu 14.04)"
date: 2017-03-07
forum: Installation &amp; Upgrades
---

### Post by hanana on 2017-03-07
Im trying to install tensorflow to my lab's server computer, but it failed.(prints various errors.)

and rebooted computer.

next, it falls into INFINITE login loop.

I cannot even log in with guest account.

my server computer has

CPU : i7-5930K
Mainboard : ASUS X99-E WS
GPU : two Geforce TITAN X s, with CUDA 7.0

I have to fix it. plz help me guyz :)

[IMG]https://ubuntuforums.org/images/icons/icon12.png[/IMG]

---

### Post by adedamoo-ab on 2017-03-07
Press Ctrl+Alt+F3 to log in to shell


enter ls -lA. If you see the line
do chown username:username
you might need to do sudo chmod a+wt /tmp 
try to log in again at this point.


You can also try to uninstall and install lightdm 
restart.

I hope this help

---

### Post by hanana on 2017-03-07
i tried 
chown name:name ./Xauthority
sudo chmod a+wt /tmp

and relogined, but it still in infinite loop.

next, i tried uninstall lightdm

sudo apt-get purge lightdm

but it doesnt work.
it prints

some packages could not be installed. this may mean that you have requested an impossible situation or if you are using the unstable distribution that some required packages have not yet been created or been moved out of incoming.

....

the following packages have unmet dependencies:
libcheese-gtk23 : Depends: libclutter-gtk-1.0-0 but it is not going to be installed
                         Depends: libcogl15, same upper
libcheese7 : Depends:libclutter-gst-2.0-0 same upper
                  Depends: gstreamer1.0-clutter same upper
libclutter-1.0-0 : Depends: libcogl-pango15
                        Depends: libcogl15  are also not going to be installed.

E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

so i can't remove it
autoremove also doesn't work with same errors, and i tried apt-get -f install, but also has same problem.

I think graphic drivers can cause these problems.
because it outputs LOWER resolution(i think 640x480).

now, what should i do? please help me friends. :(

---

### Post by Bashing-om on 2017-03-07
hanana; Hello; Welcome to the forum.

Let's look and see where the package manager reports the failure;
Post back - Between Code Tags - the outputs of terminal commands:
```

sudo apt update
sudo apt upgrade
sudo apt -f install

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

[INDENT]it is all in the process
[/INDENT]

---

### Post by hanana on 2017-03-29
i just re-installed ubuntu.

nothing could fix it. ToT

please becareful when you guys try to install tensorflow or other toolkits with NVIDIA drivers.

i think it is very critical to computer ToT..

---

