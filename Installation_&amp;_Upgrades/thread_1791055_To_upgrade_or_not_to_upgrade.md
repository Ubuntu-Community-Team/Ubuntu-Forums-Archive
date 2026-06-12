---
title: "To upgrade or not to upgrade?"
date: 2011-06-26
forum: Installation &amp; Upgrades
---

### Post by kroq-gar78 on 2011-06-26
Hello Ubuntu Forums Community,

I have a Dell desktop which had 10.04 on it, then upgraded to 10.10 RC (back then when there was RC), and finally to the actual 10.10. It was all 32-bit, since I really didn't know what the difference was back then. It has 3GB RAM, so I was thinking recently that I should upgrade to 11.04 Natty 64-bit. Should I or should I not? Do most 32-bit programs now work on 64-bit? Also, I'm thinking of a complete re-install through liveCD/flashdrive b/c I heard that you should do that after some amount of upgrades. Also, which is more stable: Maverick or Natty? It runs Maverick right now, so if I do a re-install off LiveCD it would only benefit (or serve as a detriment to) me. It has a bunch of apps (lots of which I don't even use), and it has a dual boot with Windoz XP. Ubuntu is installed on and run off of a 320GB external HDD that's connected to the computer with a USB cable. GRUB is installed on the main HDD (inside of the computer; 80GB) so that I didn't have to boot off of USB as default (security issue, in my opinion).

My other desktop, an alienware, has a WUBI install w/ 10.04. *Can* I even upgrade it to Maverick? Some places, I heard that Maverick is more stable than Lucid; please tell me if that's not necessarily the case. I have dual NVidia's on the Alienware using proprietary drivers. 

[B]So, the four main questions:
[/B] 
[LIST=1]
[*]**Should I upgrade my Dell from 32-bit to 64-bit?**
[*]**Should I upgrade my Dell from 10.10 Maverick to 11.04 Natty?**
[*]**Which is more stable: Maverick or Natty?**
[LIST=1]
[*]**Would it affect my performance on either of my systems (both proprietary NVidia graphics cards)**
[/LIST]
 
[*]**Should/can I upgrade my Alienware WUBI from 10.04 Lucid to 10.10 Maverick?**
[/LIST]
Thanks in advance.

Sincerely,
kroq-gar78

P.S. I'm not really worried about Unity. I'm using it right now on one of my other computers and am completely fine with it.

---

### Post by josephmills on 2011-06-26
Hi there with any form of ubuntu you can add a repository and then add unity,fluxbox,gnome3,kde or whatever 

**How to install unity on ubuntu 10.10** 

open your terminal (ctrl+alt+t)
then type in 
```
sudo add-apt-repository ppa:canonical-dx-team/une
```
then 
```
sudo apt-get update && sudo apt-get install unity
``` 
then log out 
now when logging in select ubuntu netbook edition enter your password and there you go you have unity 


**How to install Xfce on ubuntu 10.10 **
open you terminal and type in 
```
sudo add-apt-repository ppa:koshi/xfce-4.8
```
then 
```
sudo apt-get update && sudo apt-get install xfce4
```
then log out of you session and when you go to log back in select xface session and that is all there is to it .


[b]How to install gnome 3 on ubuntu 10.10 
[/b]
The first thing that we are going to do is open a terminal(ctrl+alt+t) 
Ok now that the terminal is open lets make sure that gcc is installed to do type in
```
gcc --version
```
Did you get an error if so please install it
```
sudo apt-get install gcc
```

then time for the dep 
```
sudo apt-get install curl libtiff4-dev libgstreamer0.10-dev libcroco3-dev xulrunner-dev mesa-utils mesa-common-dev libreadline5-dev libgl1-mesa-dev libwnck-dev librsvg2-dev libgnome-desktop-dev libgnome-menu-dev libffi-dev libgtk2.0-dev libgconf2-dev libdbus-glib-1-dev gtk-doc-tools gnome-common git-core flex bison automake build-essential icon-naming-utils autopoint libvorbis-dev libpam-dev libgcrypt-dev libtasn1-dev libtasn1-3-bin libgnome-keyring-dev libupower-glib-dev libxklavier16 libxklavier-dev xserver-xephyr python-dev libpulse-dev libjasper-dev jhbuild libgtop2-dev libsqlite3-dev libproxy-dev libdb-dev libproxy-dev libcups2-dev libusb-1.0-0-dev gperf
```
then 
```
sudo apt-get install curl jhbuild libjasper-dev libdconf0 libtiff4-dev libgstreamer0.10-dev libcroco3-dev xserver-xephyr xulrunner-dev python-dev mesa-utils mesa-common-dev libreadline5-dev libgl1-mesa-dev libwnck-dev librsvg2-dev libgnome-desktop-dev libgnome-menu-dev libffi-dev libgtk2.0-dev libgconf2-dev libdbus-glib-1-dev gtk-doc-tools gnome-common git-core flex bison automake build-essential icon-naming-utils autopoint libcanberra-dev libpulse-dev libvorbis-dev gnome-settings-daemon-dev libxklavier-dev libpam0g-dev libtasn1-3-bin libupower-glib-dev libgnome-keyring-dev libgtop2-dev libvala-0.12-dev valac libcups2-dev evolution-data-server-dev libecal1.2-dev libedataserver1.2-dev libedataserverui1.2-dev iso-codes sqlite3 libsqlite3-dev libproxy0 libproxy-dev libdb-dev libdb4.8 gperf libsoup2.4-dev libsoup-gnome2.4-dev python-argparse libsane-dev libgudev-1.0-dev libpolkit-gobject-1-dev liblcms2-dev libxcb-aux0-dev libxcb-event1-dev libx11-xcb-dev libgconf2.0-cil-dev libxtst-dev liboauth-deb
```
then must and I mean absolutely must – remove the .la files from /usr/lib and /usr/lib64. It seems that these files contain hard-coded paths, which cause issues with the compilation of your new sandbox installation of GNOME 3. So, let’s get rid of them. The easiest way to do this is
```
sudo find /usr/lib*/ -name "*.la" -delete
```
Next we need to download and execute the setup script, but first add the following to the path
```
export PATH=$PATH:/home/YOUR USERNAME/bin
```
Obviously, replace “YOUR USERNAME” with…your username. the bit before the @ sign in your command prompt,
next it is time to start the fun 
```
cd
```
then 
```
wget http://git.gnome.org/browse/gnome-shell/plain/tools/build/gnome-shell-build-setup.sh
```
then 
```
chmod +x ./gnome-shell-build-setup.sh
```
then 
```
./gnome-shell-build-setup.sh
```
then build time 
```
jhbuild build
```
this will take some time (two to three hours )and you will have to watch for errors 
then
```
cd ~/gnome-shell/source/gnome-shell/src
```
then 
```
./gnome-shell --replace
```
now you should have gnome 3 installed 
This will give you a happy sandbox to play in. It won’t affect your current GNOME installation, and you can test out GNOME 3 to your heart’s content. To get back to your previous window manager, simply switch back to the terminal and hit CTRL-C.

If you have been utterly blown away by the GNOME 3 experience or – like me – you just decide to doggedly persevere until you get it working exactly as you want, then type the following lines to replace GNOME 2 with GNOME 3:
```
ln -s ~/gnome-shell/install/share/applications/gnome-shell.desktop ~/.local/share/applications/gnome-shell.desktop

gconftool-2 -s /desktop/gnome/session/required_components/windowmanager "gnome-shell" -t strin
```

have fun with gnome 3 


**How to install kde on ubuntu 10.10 **

first thin open up a terminal (ctrl+alt+t)
then type in 
```
sudo add-apt-repository ppa:kubuntu-ppa/backports
```
then 
```
sudo apt-get update 
```
then 
```
sudo apt-get install kubuntu-desktop
```
then log out and when logging back in select kde and go have fun 

If anyone would like to know anymore fluxbox ect post hope that this helps with making a choice

---

### Post by kroq-gar78 on 2011-06-26
Ah, sorry, it seems that my original post is misleading. I meant that I'm not "scared" of unity. I already know how to install all of these other awesome desktop environments, but I was really asking if I should upgrade my computers and how it would affect me (look at the original post, then main questions).

P.S. Thanks for the info on Gnome3. I didn't know how to install it :) thanks.

---

### Post by josephmills on 2011-06-26
I would have to say that 10.10 is more stable at the moment then 11.04 that is just my option. it also depend if you are a power usr or a everyday usr I like the classic gnome with all its options. as far as nivida they will use the same drivers under additional drivers I sure that a couple people will not like what I have to say but that is how I feel about it. oh and dont install all those desktop enviroments at once could mess stuff up as far as 64 or 32 you would be pushing it with 3 gigs if you ever wanted to run vbox

---

### Post by nzjethro on 2011-06-26
Depending on your system specs, you may find 10.10 smoother than 11.04 (my oldish laptop runs 10.10 perfectly, but 11.04 a bit laggy). Of course you should try the Live CD to see how your system will handle it, because there will probably be a certain degree of performance change.

The way I see it, 10.10 is supported until April 2012, so if you're enjoying 10.10, why bother with an upgrade? I've given Natty a shot twice, and then tried 10.04 LTS as well (thinking I could get an extra year of support), but I've come back to 10.10. If you like how you have 10.10 set up and it runs well on your system, I wouldn't recommend updating.

I hear that 64 bit OSes have improved a lot, so if you do decide to go 11.04, I would go for a clean 64 bit install, rather than upgrading Maverick through the Update Manager. It'll give you a cleaner start, plus you don't have to deal with some of the upgrade errors I've read about on here.

---

