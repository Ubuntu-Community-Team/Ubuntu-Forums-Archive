---
title: "craming a desktop into 500mb of space. I could use a little help"
date: 2007-02-14
forum: Installation &amp; Upgrades
---

### Post by 900donuts on 2007-02-14
heres the situation 

I recently acquired from a neighbor a pc old enough to say "Gateway 2000" on the front
(stats: 500mhz pentium 3 slot 1, 384 MBs of sdram, and an 8MB graphics card)
there is no hard drive (the person had sensitive info on the hard drive so i told him to take a sledge hammer to it) :lolflag: 
there are cd and floppy drives

the largest spare hard drive i have is 500MBs is there a ubuntu install option that will function as a desktop and fit in this space?

thanks in advance

---

### Post by 900donuts on 2007-02-14
note the lagest spare i have is 500MBs ive got smaller ones to store my goodies in later
(this machine is for one my family they only need net and word processing)

---

### Post by kerry_s on 2007-02-14
You can do a custom install, but it will be far easier to just install a full distro that is built to work with in those constraints-> [http://damnsmalllinux.org/](http://damnsmalllinux.org/)
If you learn to use the frugal install you will still have 450mb to play with.

---

### Post by meng on 2007-02-14
500 MB just isn't going to be enough to install Ubuntu (requirement 3 GB). Even the server edition requires 500 MB of space. Damn Small Linux is a good choice, otherwise perhaps Puppy Linux.

---

### Post by 900donuts on 2007-02-15
ive tried DSL (couldn't get to disk partitioner to work)](*,) 

and puppy (i couldn't burn the cd right it just wouldn't work)](*,) 

what about xubuntu?

could that be made to fit?

---

### Post by meng on 2007-02-15
No. Perhaps you could elaborate on the problems you had with the other distros.

---

### Post by 900donuts on 2007-02-15
then can you point me in the derection of a good live cd burning soft ware (my linux does not have a burner drive so the soft ware has to run on windows)

---

### Post by bandie on 2007-02-15
unless you wish to persue your challange you could get a 10Gb drive from Ebay for less than £10.00

---

### Post by meng on 2007-02-15
[www.psychocats.net/ubuntu/iso](www.psychocats.net/ubuntu/iso)
has a suggestion for Windows software to burn ISO

---

### Post by K.Mandla on 2007-02-15
I was under the impression that a server install fit into 300Mb; that being said, you probably won't be able to prune a GUI of any sort (even Openbox or the like) down to less than ~500Mb. You could probably add links2 to a server install and at least have some rudimentary graphical Web surfing, then rely on text-based applications for playing music, chatting, etc.

Other distros are probably better options. DSL, Puppy and Deli Linux are all extremely small. 

Are you sure you can't get your hands on a 4Gb or even a 1Gb hard drive somewhere? People are practically giving those away on eBay.

---

### Post by 900donuts on 2007-02-15
ive never used ebay before and im not that willing to wait 4 to 6 weeks for delivery just to find out the post offices new bomb sniffer fried it

but there is a surplus store in town (2GB for 12 Bucks!):shock: (6GB for $16)

I was just trying to solve problem the cheapest (and hardest) way possible

---

### Post by kerry_s on 2007-02-15
You can try with the server install, but your going to have to do alot of trimming.( [http://archive.ubuntu.com/ubuntu/dists/edgy/main/installer-i386/current/images/netboot/mini.iso](http://archive.ubuntu.com/ubuntu/dists/edgy/main/installer-i386/current/images/netboot/mini.iso) )
From my other thread, for a full base system, you can get pretty close, but your going to have to sacrifice a little, after the fluxbox install, spend alot of time on trimming, uninstall as much as you can. If you think outside the box you can make it fit, it's all a mater of compromise and a lot of linking and replacing. For example: xvt is way smaller then xterm(uninstall xterm install xvt> ln -s xvt xterm), do you really need all those fonts? Why keep drivers for other cards?  Spend alot of time looking for smaller options, see what the small distro's use->

command-line install
login
sudo su
nano /etc/apt/sources.list
comment(#) out the cdrom and uncomment all the repos
ctrl and x and y and enter to save
apt-get update
apt-get dist-upgrade
apt-get install x-window-system-core gdm fluxbox synaptic
type> reboot
select fluxbox from session menu and login
open synaptic and start trimming it down further, you want to get rid of what you don't need,fonts,extra xserver-drivers for cards you don't have,all the raid stuff,etc...
After you do that install a filemanager,editor,eterm->
sudo apt-get install emelfm leafpad eterm

These are very small, once those install, launch> sudo emelfm /usr/share
go into the /doc and /man folders and delete everything, that will give you even more space then start building the rest->
apt-get install firefox dillo xmms mplayer mozilla-mplayer flashplugin-nonfree

That will give you 2 web browsers 1 regular and 1 built to be fast, players for your music and movies,you will still need to install the w32codecs->
wget -c [http://www.debian-multimedia.org/poo...2-0.0_i386.deb](http://www.debian-multimedia.org/poo...2-0.0_i386.deb)
sudo dpkg -i w32codecs_20061022-0.0_i386.deb

You might also need libdvdcss2->
wget -c [http://www.dtek.chalmers.se/groups/d...2.5-1_i386.deb](http://www.dtek.chalmers.se/groups/d...2.5-1_i386.deb)
sudo dpkg -i libdvdcss2_1.2.5-1_i386.deb

That will be a very basic system and if you clean up the /doc and /man again you should still have just under a gig of space to play with.

---

### Post by kerry_s on 2007-02-15
I'll do a small build later today and try an get an easy to follow set up that fits in 500mb. I'll try and write down everything so you can have the exact commands to follow. :)

---

### Post by JensenDied on 2007-02-15
smallest ive used was about 700 mb, but that was a minimal system with gui as fluxbox... 500 is possible, go with commandline install and build from there. just watch the freespace and i guess forgo the swap.

staying away from kde and gnome will be necessary due to large dependencies. 

im not sure if OOo will fit and work well in that space for processing but its worth a shot, clear the cache if something isnt going to work to save that space

---

### Post by kerry_s on 2007-02-15
Okay my friend, it's do able but tight. I just did enough to get it installed and ended with 488mb of space, after removing some apps 426mb. I just used the standard server(mini.iso) install and built up from there and removed what ever caught my eye on the first pass that i know i don't need/want. I hope you got  good internet connection, cause mine was kinda slow today, might be the repos were slow.

Give me a little while to sort through my chicken scratch i call notes and type it up. :)  I'll post the instructions shortly.


Grab the mini.iso, that way after you install your already fully up to date->[http://archive.ubuntu.com/ubuntu/dists/edgy/main/installer-i386/current/images/netboot/mini.iso](http://archive.ubuntu.com/ubuntu/dists/edgy/main/installer-i386/current/images/netboot/mini.iso)
type> server <and enter
You want to use> reiserfs <file system so you don't have to sacrifice space right off the back, i used 1 partion and no swap.
Now just wait for it to install (You can press ctrl+alt+F4 if you want to see the installation,ctrl+alt+F1 to get back to the installer)
At software selection, just press tab and enter, were going to pick are own.
If grub fails to install, click on "go back" and then just hit enter till it completes the install. I get that from time to time, don't know if it happens to others.
It should now say it's finished click continue, make sure when it reboots you grab the cd out.
Now your at command line type in your user name and password
type> sudo su
enter your password
type> nano /etc/apt/sources.list
comment(#) out the lines starting with deb-src and uncomment all the lines starting with deb, saves some space
Press ctrl and x and y and enter to save the file
type> apt-get update
type> apt-get install x-window-system-core gdm fluxbox synaptic
use the space bar to select your screen size and tab to get to okay when your finished.
type> apt-get clean
type> reboot
Don't worry about that error, it just means you don't have that theme, just click ok. You can change the theme in gdm setup and also setup the auto login if you want that.
Click on options> select session> fluxbox> change session and then login
select> make default
Now open synaptic and click on> settings> preferences> in general tab, check th box under apperance, we want to see that info. Under the file tab, select delete download and go ahead and press the clear cache button. the click apply and okay to close.

Take a quick break, were about to remove applications, just in case your wondering your around 400+mb, so you really need some space.

click on> status> installed
now work your way down the list and mark what you don't want/need for complete removal.
Here's what i took out/removed on the first pass->
aptitude
installation-report
libparted
memtest86+
openssh-client
pcmciautils
popularity-contest
ppp
rsync
telnet
vim-common
w3m
wirelesstools
wpasupplicant
xfonts-75dpi
xserver-xorg
xserver-xorg-input-all
xserver-xorg-input-elographics
xserver-xorg-input-synaptics
xserver-xorg-input-wacom
xserver-xorg-video-all
I removed all the xserver-xorg-video-? drivers except for nv and vesa(you must keep vesa), because my card is nvidia and that is what i'm was using.

I then installed emelfm and gtkedit and in terminal typed> gksu emelfm < and went to /usr/share/doc and deleted everything in there, then i went to /man and deleted everything in there.
So i ended up at 426mb which i know can be trimmed even lower, i just got bored.
Get to this point and then come back and will see what else we can do :)

continuing->
Removed->
inputattach
laptop-detect
man-db
manpages
xfonts-100dpi

Installed->
ttf-bitstream-vera

Removed->
ttf-dejavu
xterm

Installed->
xvt

In terminal> sudo ln -s /usr/bin/xvt /usr/bin/xterm

installed->
dillo

Added repo-> deb [http://getswiftfox.com/builds/debian](http://getswiftfox.com/builds/debian) unstable non-free 
installed->
swiftfox

I installed swiftfox because i couldn't log into ubuntu forums with dillo. Size so far 447mb.

Alternative to swiftfox->
You can use dillo to download seamonkey which will give you a slew of features, but it will take the size to 460mb.
-> [http://www.mozilla.org/projects/seamonkey/](http://www.mozilla.org/projects/seamonkey/)

---

### Post by kerry_s on 2007-02-16
I added scrot and took some pics->

---

### Post by kerry_s on 2007-02-16
Well, dude that's pretty much the smallest i can get it with out the system becoming unstable or crashing. I'm all out of ideas.

---

### Post by meng on 2007-02-16
kerry_s: impressive!

---

### Post by confused57 on 2007-02-16
> **meng said:**
> kerry_s: impressive!

I agree...it's amazing the number of highly knowledgable people we have in the forum, haven't seen anything like it in any of the other Linux forums, especially people willing to go to such great lengths to help others...

---

### Post by kerry_s on 2007-02-16
Thank you, all of you! I just hope it works for the OP and any one else who tries. I tried to write down everything, which was the hard part, I'm helping my grandma with renovations and was doing plumbing and "DAMN!" my hands are so sore. But what can i say, i love to help, pain or not.  :)

---

### Post by K.Mandla on 2007-02-17
Nicely done! =D>

---

### Post by allforcarrie on 2007-04-19
spend $10. on a crap drive.... or install on a USB drive. spend the sma amount on a cd drive.

---

