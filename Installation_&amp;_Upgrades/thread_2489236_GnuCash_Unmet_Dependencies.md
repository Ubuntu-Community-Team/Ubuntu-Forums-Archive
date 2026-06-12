---
title: "GnuCash Unmet Dependencies"
date: 2023-07-23
forum: Installation &amp; Upgrades
---

### Post by unfirthman on 2023-07-23
I am following these steps from the GnuCash website:

```
sudo dpkg -i gnucash_4.4-1_amd64.deb gnucash-common_4.4-1_all.deb
```

from my Downloads folder, where the .deb files are located.

I start with this error:

```
Selecting previously unselected package gnucash.
(Reading database ... 280353 files and directories currently installed.)
Preparing to unpack gnucash_4.4-1_amd64.deb ...
Unpacking gnucash (1:4.4-1) ...
Preparing to unpack gnucash-common_4.4-1_all.deb ...
Unpacking gnucash-common (1:4.4-1) over (1:4.4-1) ...
dpkg: dependency problems prevent configuration of gnucash:
 gnucash depends on guile-3.0-libs; however:
  Package guile-3.0-libs is not installed.
 gnucash depends on libaqbanking44 (>= 5.99.43); however:
  Package libaqbanking44 is not installed.
 gnucash depends on libboost-filesystem1.74.0 (>= 1.74.0); however:
  Package libboost-filesystem1.74.0 is not installed.
 gnucash depends on libboost-locale1.74.0 (>= 1.74.0); however:
  Package libboost-locale1.74.0 is not installed.
 gnucash depends on libboost-program-options1.74.0 (>= 1.74.0); however:
  Package libboost-program-options1.74.0 is not installed.
 gnucash depends on libboost-regex1.74.0-icu67; however:
  Package libboost-regex1.74.0-icu67 is not installed.
 gnucash depends on libdbi1 (>= 0.9.0); however:
  Package libdbi1 is not installed.
 gnucash depends on libgwengui-gtk3-79 (>= 5.4.0~); however:
  Package libgwengui-gtk3-79 is not installed.
 gnucash depends on libgwenhywfar79 (>= 4.1.0); however:
  Package libgwenhywfar79 is not installed.
 gnucash depends on libicu67 (>= 67.1-1~); however:
  Package libicu67 is not installed.
 gnucash depends on libofx7 (>= 0.9.14); however:
  Package libofx7 is not installed.
 gnucash depends on libpython3.9 (>= 3.9.0~b4); however:
  Package libpython3.9 is not installed.
 gnucash depends on guile-3.0 | guile-2.2 | guile-2.0; however:
  Package guile-3.0 is not installed.
  Package guile-2.2 is not installed.
  Package guile-2.0 is not installed.
 gnucash depends on libfinance-quote-perl; however:
  Package libfinance-quote-perl is not installed.
 gnucash depends on libhtml-tableextract-perl; however:
  Package libhtml-tableextract-perl is not installed.
 gnucash depends on libcrypt-ssleay-perl; however:
  Package libcrypt-ssleay-perl is not installed.
 gnucash depends on libdate-manip-perl; however:
  Package libdate-manip-perl is not installed.

dpkg: error processing package gnucash (--install):
 dependency problems - leaving unconfigured
Setting up gnucash-common (1:4.4-1) ...
Processing triggers for mailcap (3.70+nmu1ubuntu1) ...
Processing triggers for gnome-menus (3.36.0-1ubuntu3) ...
Processing triggers for desktop-file-utils (0.26-1ubuntu3) ...
Processing triggers for man-db (2.10.2-1) ...
Processing triggers for libglib2.0-0:amd64 (2.72.4-0ubuntu2.2) ...
Processing triggers for libglib2.0-0:i386 (2.72.4-0ubuntu2.2) ...
Processing triggers for hicolor-icon-theme (0.17-2) ...
Processing triggers for install-info (6.8-4build1) ...
Errors were encountered while processing:
 gnucash
```

After running ```
apt update && apt upgrade -y
``` I get this error:

```
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 gnucash : Depends: guile-3.0-libs but it is not installable
           Depends: libaqbanking44 (>= 5.99.43) but it is not installable
           Depends: libboost-filesystem1.74.0 (>= 1.74.0) but it is not installable
           Depends: libboost-locale1.74.0 (>= 1.74.0) but it is not installable
           Depends: libboost-program-options1.74.0 (>= 1.74.0) but it is not installable
           Depends: libboost-regex1.74.0-icu67 but it is not installable
           Depends: libdbi1 (>= 0.9.0) but it is not installable
           Depends: libgwengui-gtk3-79 (>= 5.4.0~) but it is not installable
           Depends: libgwenhywfar79 (>= 4.1.0) but it is not installable
           Depends: libicu67 (>= 67.1-1~) but it is not installable
           Depends: libofx7 (>= 0.9.14) but it is not installable
           Depends: libpython3.9 (>= 3.9.0~b4) but it is not installable
           Depends: guile-3.0 but it is not installable or
                    guile-2.2 but it is not installable or
                    guile-2.0 but it is not installable
           Depends: libfinance-quote-perl but it is not installable
           Depends: libhtml-tableextract-perl but it is not installable
           Depends: libcrypt-ssleay-perl but it is not installable
           Depends: libdate-manip-perl but it is not installable
           Recommends: gnucash-docs but it is not installable
           Recommends: python3-gnucash but it is not installable
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).
```

After that, ```
apt --fix-broken install
``` seems to want to delete gnucash altogether. Trying to install the packages individual generates a ```
package xxxx is not available but is referred to by another package...
``` error.

I have done this before, so I don't know what I am doing incorrectly this time! Any help would be appreciated.

Thanks

---

### Post by ajgreeny on 2023-07-23
What version of Ubuntu are you running and why download gnucash from its website when it is available from the repositories?

Have you tried installing gnucash from the normal repos with command ```
sudo apt install gnucash
```
Ubuntu 22.04 currently has gnucash version 4.8-1 in the repos a more recent version than the one you downloaded.

---

### Post by #&amp;thj^% on 2023-07-23
It's available via flatpak as well
```
flatpak search GnuCash
Name  Description             Application ID   Version            Branch Remotes
GnuC&#8230; Manage your finances, &#8230; &#8230;gnucash.GnuCash 5.3+ (Flathub 5.3) stable flathub

```
Your version seems old to me.
And in the repos as well:
```
apt policy gnucash
gnucash:
  Installed: (none)
  Candidate: 1:4.13-1
  Version table:
     1:4.13-1 500
        500 http://archive.ubuntu.com/ubuntu lunar/universe amd64 Packages

```
Even if I just install it from the repos I'll add this before:
```
sudo apt install build-essential cmake libncurses5-dev libncursesw5-dev git
```
Then just a simple command to install:
```
sudo apt install gnucash
```

```
gnucash --version
GnuCash 4.13
Build ID: 4.13+(2022-12-17)

```

---

### Post by Frogs Hair on 2023-07-23
This application in the repository on 20.04 +.  Does the website offer a newer version ? 
 [https://packages.ubuntu.com/search?keywords=gnucash](https://packages.ubuntu.com/search?keywords=gnucash)

---

### Post by unfirthman on 2023-07-23
Thanks!

I am running 22.04 jammy. 

I purged all gnucash from my system with

```
sudo apt purge gnucash && sudo apt purge gnucash-common
```

Then

```
sudo apt update && sudo apt upgrade -y
```

Now when I enter:

```
sudo apt install gnucash
```

I get:

```
E: Unable to locate package gnucash
```

---

### Post by #&amp;thj^% on 2023-07-23
It should be in "universe"
```
gnucash | 1:4.8-1build2   | jammy/universe         | source, amd64, arm64, ppc64el, riscv64, s390x
 gnucash | 1:4.11-1        | kinetic/universe       | source, amd64, arm64, armhf, ppc64el, riscv64, s390x
 gnucash | 1:4.13-1        | lunar/universe         | source, amd64, arm64, armhf, ppc64el, riscv64, s390x
 gnucash | 1:5.1-1         | mantic/universe        | source, amd64, arm64, armhf, ppc64el, riscv64, s390x

```

---

### Post by unfirthman on 2023-07-23
Also, the return from 

```
sudo apt install build-essential cmake libncurses5-dev libncursesw5-dev git
```

is this:

```
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Note, selecting 'libncurses-dev' instead of 'libncurses5-dev'
Note, selecting 'libncurses-dev' instead of 'libncursesw5-dev'

No apt package "cmake", but there is a snap with that name.
Try "snap install cmake"

E: Unable to locate package cmake
```

I thought I have used cmake before, but I'll double check to make sure

---

### Post by unfirthman on 2023-07-23
> **1fallen said:**
> It should be in "universe"
```
gnucash | 1:4.8-1build2   | jammy/universe         | source, amd64, arm64, ppc64el, riscv64, s390x
 gnucash | 1:4.11-1        | kinetic/universe       | source, amd64, arm64, armhf, ppc64el, riscv64, s390x
 gnucash | 1:4.13-1        | lunar/universe         | source, amd64, arm64, armhf, ppc64el, riscv64, s390x
 gnucash | 1:5.1-1         | mantic/universe        | source, amd64, arm64, armhf, ppc64el, riscv64, s390x

```

Do I access this repo by ?

```
sudo add-apt-repository universe
```

I have done this and I get the same return when I try to install gnucash via apt repo

---

### Post by #&amp;thj^% on 2023-07-23
your repos are wacky then please try this first then the install again
```
sudo add-apt-repository universe
```
update:
```
sudo apt update
```
install:
```
sudo apt install gnucash 
```

---

### Post by unfirthman on 2023-07-23
For more context:

```
&#10140;  ~ sudo add-apt-repository universe 
Adding component(s) 'universe' to all repositories.
Press [ENTER] to continue or Ctrl-c to cancel.
Hit:1 [http://packages.microsoft.com/repos/code](http://packages.microsoft.com/repos/code) stable InRelease
Hit:2 [https://dl.winehq.org/wine-builds/ubuntu](https://dl.winehq.org/wine-builds/ubuntu) lunar InRelease                                                                                               
Get:3 [https://cli.github.com/packages](https://cli.github.com/packages) stable InRelease [3,917 B]                                                                                             
Hit:4 [https://download.docker.com/linux/ubuntu](https://download.docker.com/linux/ubuntu) jammy InRelease                                                                                               
Hit:5 [https://dl.google.com/linux/chrome/deb](https://dl.google.com/linux/chrome/deb) stable InRelease                                                                                            
Hit:7 [https://ppa.launchpadcontent.net/helkaluin/webp-pixbuf-loader/ubuntu](https://ppa.launchpadcontent.net/helkaluin/webp-pixbuf-loader/ubuntu) jammy InRelease                  
Hit:6 [https://debian.sur5r.net/i3](https://debian.sur5r.net/i3) jammy InRelease                                 
Hit:8 [https://ppa.launchpadcontent.net/neovim-ppa/stable/ubuntu](https://ppa.launchpadcontent.net/neovim-ppa/stable/ubuntu) jammy InRelease   
Hit:9 [https://ppa.launchpadcontent.net/wireshark-dev/stable/ubuntu](https://ppa.launchpadcontent.net/wireshark-dev/stable/ubuntu) jammy InRelease
Fetched 3,917 B in 1s (3,066 B/s)                          
Reading package lists... Done
&#10140;  ~ sudo apt update
Hit:1 [http://packages.microsoft.com/repos/code](http://packages.microsoft.com/repos/code) stable InRelease
Hit:2 [https://download.docker.com/linux/ubuntu](https://download.docker.com/linux/ubuntu) jammy InRelease                                                                                               
Hit:3 [https://dl.winehq.org/wine-builds/ubuntu](https://dl.winehq.org/wine-builds/ubuntu) lunar InRelease                                                                                               
Get:4 [https://cli.github.com/packages](https://cli.github.com/packages) stable InRelease [3,917 B]                                                                                             
Hit:5 [https://dl.google.com/linux/chrome/deb](https://dl.google.com/linux/chrome/deb) stable InRelease                                                                                                
Hit:7 [https://ppa.launchpadcontent.net/helkaluin/webp-pixbuf-loader/ubuntu](https://ppa.launchpadcontent.net/helkaluin/webp-pixbuf-loader/ubuntu) jammy InRelease                  
Hit:8 [https://ppa.launchpadcontent.net/neovim-ppa/stable/ubuntu](https://ppa.launchpadcontent.net/neovim-ppa/stable/ubuntu) jammy InRelease                             
Hit:6 [https://debian.sur5r.net/i3](https://debian.sur5r.net/i3) jammy InRelease                                                          
Hit:9 [https://ppa.launchpadcontent.net/wireshark-dev/stable/ubuntu](https://ppa.launchpadcontent.net/wireshark-dev/stable/ubuntu) jammy InRelease
Fetched 3,917 B in 1s (3,238 B/s)                          
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
All packages are up to date.
&#10140;  ~ sudo apt install gnucash
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
E: Unable to locate package gnucash
```

---

### Post by Holger_Gehrke on 2023-07-23
'gnucash' is in the 'universe' part of the repositories - software that's packaged by Canonical but maintained and supported by the community. I do faintly remember that while most flavours activate that part of the repositories by default, mainline Ubuntu doesn't. You should find a checkbox to activate it in the "Software & Updates" settings program aka software-properties-gtk.

Holger

---

### Post by #&amp;thj^% on 2023-07-23
We need to see this please:
```
inxi -r
```

---

### Post by unfirthman on 2023-07-23
Here ya go:

```
&#10140;  ~ inxi -r
zsh: command not found: inxi
&#10140;  ~ sudo inxi -r
sudo: inxi: command not found
&#10140;  ~ sudo apt install inxi
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
E: Unable to locate package inxi
```

---

### Post by #&amp;thj^% on 2023-07-23
Can you get out of a zsh shell and run a regular bash shell?
```
 echo "$0"
bash

```
for a bash shell:
```
bash
```
You have some apparent problems here my friend

---

### Post by unfirthman on 2023-07-23
> **1fallen said:**
> 
You have some apparent problems here my friend

Hahaha I'm going to take a dinner break before going deeper.

Thank you everyone for your help so far!

---

### Post by MAFoElffen on 2023-07-24
Please run the [UbuntuForums 'system-info' script]("https://github.com/UbuntuForums/system-info"). 

Or just post the output from
```

grep -v '#' /etc/apt/sources.list

```
Note: inxi is also in the Universe Repo...

---

### Post by #&amp;thj^% on 2023-07-24
MAFoElffen This is all I have been able to gleem out of thread for the OP's sources:
```
Hit:1 http://packages.microsoft.com/repos/code stable InRelease
Hit:2 https://dl.winehq.org/wine-builds/ubuntu lunar InRelease                                                                                               
Get:3 https://cli.github.com/packages stable InRelease [3,917 B]                                                                                             
Hit:4 https://download.docker.com/linux/ubuntu jammy InRelease                                                                                               
Hit:5 https://dl.google.com/linux/chrome/deb stable InRelease                                                                                            
Hit:7 https://ppa.launchpadcontent.net/hel...-loader/ubuntu jammy InRelease                  
Hit:6 https://debian.sur5r.net/i3 jammy InRelease                                 
Hit:8 https://ppa.launchpadcontent.net/neo.../stable/ubuntu jammy InRelease   
Hit:9 https://ppa.launchpadcontent.net/wir.../stable/ubuntu jammy InRelease
Fetched 3,917 B in 1s (3,066 B/s)                          
Reading package lists... Done
&#10140;  ~ sudo apt update
Hit:1 http://packages.microsoft.com/repos/code stable InRelease
Hit:2 https://download.docker.com/linux/ubuntu jammy InRelease                                                                                               
Hit:3 https://dl.winehq.org/wine-builds/ubuntu lunar InRelease                                                                                               
Get:4 https://cli.github.com/packages stable InRelease [3,917 B]                                                                                             
Hit:5 https://dl.google.com/linux/chrome/deb stable InRelease                                                                                                
Hit:7 https://ppa.launchpadcontent.net/hel...-loader/ubuntu jammy InRelease                  
Hit:8 https://ppa.launchpadcontent.net/neo.../stable/ubuntu jammy InRelease                             
Hit:6 https://debian.sur5r.net/i3 jammy InRelease                                                          
Hit:9 https://ppa.launchpadcontent.net/wir.../stable/ubuntu jammy InRelease
```

---

### Post by Tadaen_Sylvermane on 2023-07-24
One thing Debian is very structured on is don't add random repositories unless you know exactly what you are doing. You may have created a Frankenbuntu. Try getting a default Jammy sources.list and see what happens. Add the others carefully one at a time. Better yet use Snap and Flatpaks liberally. This is what they are very good for. Prevents this kind of disaster movie mess.

I've learned through bitter experience and many package manager explosions to follow this priority.

Default repositories for specific release (jammy in this case) -> Flatpacks / Snaps (if you aren't offended by them) -> Ppa's -> random website repositories.

I haven't had to add a ppa or random repo in a long time and haven't heard so much as a peep from my systems. Debian or Ubuntu.


*EDIT* and if you absolutely must have something from a future version of ubuntu in your current version then try backporting it properly if possible. Then it's built against the current and you don't have to risk pulling upgraded the rest of hte system may not be happy with.

---

### Post by ian-weisser on 2023-07-24
I don't see any Ubuntu repositories among that list.
ONLY non-Ubuntu sources.

So of course adding -universe to nothing won't work.

---

### Post by ajgreeny on 2023-07-25
> **ian-weisser said:**
> I don't see any Ubuntu repositories among that list.
ONLY non-Ubuntu sources.

So of course adding -universe to nothing won't work.
Same here!

So now please show us the full output of command
**cat /etc/apt/sources.list**

As someone has already said, it seems you need to add the default Ubuntu repos to your sources as they all appear to be missing.

---

### Post by unfirthman on 2023-07-25
> **MAFoElffen said:**
> Please run the [UbuntuForums 'system-info' script]("https://github.com/UbuntuForums/system-info"). 

Or just post the output from
```

grep -v '#' /etc/apt/sources.list

```
Note: inxi is also in the Universe Repo...

Nothing came from the grep command. I've run the system-info script, just need to figure out how to post it

> **Tadaen_Sylvermane said:**
> One thing Debian is very structured on is don't add random repositories unless you know exactly what you are doing. You may have created a Frankenbuntu. Try getting a default Jammy sources.list and see what happens. Add the others carefully one at a time. Better yet use Snap and Flatpaks liberally. This is what they are very good for. Prevents this kind of disaster movie mess.

I've learned through bitter experience and many package manager explosions to follow this priority.

Default repositories for specific release (jammy in this case) -> Flatpacks / Snaps (if you aren't offended by them) -> Ppa's -> random website repositories.

I haven't had to add a ppa or random repo in a long time and haven't heard so much as a peep from my systems. Debian or Ubuntu.


*EDIT* and if you absolutely must have something from a future version of ubuntu in your current version then try backporting it properly if possible. Then it's built against the current and you don't have to risk pulling upgraded the rest of hte system may not be happy with.

This is great advice! I try to keep an up to date version of NeoVim, and that led me away from snap packages, since the NeoVim one is always one or two dev cycled behind. I can see now that this is not a hard and fast rule...

> **ajgreeny said:**
> Same here!

So now please show us the full output of command
**cat /etc/apt/sources.list**

As someone has already said, it seems you need to add the default Ubuntu repos to your sources as they all appear to be missing.

Here is what I get from that command:

```
## See sources.list(5) for more information, especialy
# Remember that you can only use http, ftp or file URIs
# CDROMs are managed through the apt-cdrom tool.

```

I have a system-info.txt generated from the [UbuntuForums 'system-info' script]("https://github.com/UbuntuForums/system-info") provided by MAFoElffen. Shall I attach it?

Thanks again for the help, all!

---

### Post by ian-weisser on 2023-07-25
Now you have confirmed it: You have no Ubuntu repositories among your sources.

Add them. There are many ways to do so.

My favorite method is [https://askubuntu.com/a/192388/19626](https://askubuntu.com/a/192388/19626)

---

### Post by unfirthman on 2023-08-02
Hello all, and thanks again for your help and patience.

This appears to have worked! I have been able to download gnucash and run it, so definitely a good sign.

Thanks!

---

