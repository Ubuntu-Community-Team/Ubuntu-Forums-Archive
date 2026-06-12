---
title: "desktop from text install no net"
date: 2006-07-16
forum: Installation &amp; Upgrades
---

### Post by blackest_knight on 2006-07-16
ok 
situation is i installed from ubuntu alternative install cd 
i now have a text prompt no desktop and no network I have a ralink2500 wireles card and I know it works on my other laptop as ra0.

so basically i need to get the desktop installed and the networking working
in either order 

most info i have found assumes a network connection
i have xubuntu install cd's both desktop and alternative and dapper desktop and alternative cd's 

any idea's how to get the desktop and the wireless working

i did try puppy and DSL but I had no networking with them either 
and i would prefer a ubuntu or xubuntu setup as i am already using it on this laptop

---

### Post by lordlollo on 2006-07-16
Did you install the server edition? This would explain why you have no desktop...

---

### Post by blackest_knight on 2006-07-16
well dapper alternative basically lets you do a text based install, which is great since the systems low on ram, and forced into a 640 by 480 desktop.
(xubuntu would be so much nicer if the installer could run without putting the buttons off the screen its ok hitting enter and hoping till you get to tab tab enter to get the installer to configure](*,) )

ok so i have a basic version of ubuntu now i know i need to install the desktop package because the alternative is a server install. 

so i need to apt-get something but obviously i have no network so i need to pull it off cd.  

sudo apt-cdrom add
sudo aptitude update
sudo aptitude install xubuntu-desktop

might do it. 

i actually did apt-cdrom add with the ubuntu alternative disk 
and then apt-get install ubuntu-desktop 
which seems to be doing a lot of installing right now
probably this will be pretty much unuseable due to ram limitations but i think if i had given it the xubuntu alternative cd i would be installing a useable desktop for this system :-k :-k

---

### Post by taurus on 2006-07-16
I have to disagree with you on the alternate CD as a text only server version!  I used alternate CD to install on two machines and Gnome works just fine!  I think you are confusing yourself between alternate CD and the server CD...  And if you want to use XFce4 as your window manager, why not download and install Xubuntu directly, [http://se.archive.ubuntu.com/mirror/cdimage.ubuntu.com/xubuntu/releases/dapper/release/](http://se.archive.ubuntu.com/mirror/cdimage.ubuntu.com/xubuntu/releases/dapper/release/)...

---

### Post by blackest_knight on 2006-07-16
your probably correct, My limited experience  made me think that the alternative cd did just give a text prompt. actually it might be better just to start again since since i did apt-get install ubuntu-desktop it started installing and its still going its got to installing fonts and after everyone rebuilding the font cache. 

if it does give me a desktop after all this its probably going to be too slow.

I would benefit from some instruction on how to get the xubuntu desktop up and running. 
the initial install seems to leave me at a text prompt and I am unsure how to proceed to getting a desktop environment from there.

---

### Post by taurus on 2006-07-16
Again, download the desktop version of xubuntu and you will have XFce4 as your window manager when you're finished installing!!!

---

### Post by blackest_knight on 2006-07-16
well I know that the easy way is if you use the live desktop version of xubuntu problem is that on a 640 by 480 screen running off the cd you suffer with 1 lack of ram and 2 the bottom of the installer window is cut off and thus no idea what button has focus. 

so I am forced to use the text based installer on the xubuntu alternative CD
which does install it just leaves me without xfce4 installed. 

apt-get install will not work because of the lack of a configured network card.

so this then leads me to using the cd to try and install the desktop and after the desktop the wireless network. ubuntu has support for my card built in I am not sure about  xubuntu. 

biggest problem is I do not know how to install the desktop from the command line for sure. 

been at this for two days now and I don't want to give up and install windows.

---

