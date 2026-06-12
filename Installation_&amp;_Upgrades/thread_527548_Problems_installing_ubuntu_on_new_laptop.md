---
title: "Problems installing ubuntu on new laptop"
date: 2007-08-16
forum: Installation &amp; Upgrades
---

### Post by hammedhaaret on 2007-08-16
Hi.
Im trying to install ubuntu 7.04 from a live CD onto my sisters new laptop.
So far, without any luck.
I've already had Ubuntu running on my own laptop a couple of months and I really like it.

So... my sister buys new laptop, and wants ubuntu too.

Specs are as follows:
15.4" WXGA
Intel C2 DUO T5250 1.50GHz 800MHz
1 Gb DDR2 PC5300
80GB SATA 2.5" 5400RPM - Hitachi
Samsung combo cd/dvd
Intel Pro/Wireless 4965AGN
Intel GMA X3000  graphics
also i think it has the new intel santa rosa stuff, whatever that is.  sounds fancy

I boot from CD.  hits enter to 'start/install ubuntu'
ubuntu starts loading but shortly after stops with this error message: 
[COLOR="Red"]
"/bin/sh: can't access tty: job control turned off"[/COLOR]

I search google and these forums and find a lot about it.
Finally i decide to go with this: ([COLOR="Blue"][http://ubuntuforums.org/showthread.php?t=421588&highlight=job+control+turned+off](http://ubuntuforums.org/showthread.php?t=421588&highlight=job+control+turned+off)[/COLOR])

I lean back to enjoy what seems to be ubuntu loading up only to be met by a blue screen (allmost of death) saying that: 
[COLOR="Red"]
"failed to start the X server (your graphical interface). It is likely that it is not set up correctly.Would you like to view the X server output to diagnose the problem?"[/COLOR]

Of course I'd like to output, so i hit yes and it gives me info about X server and ubuntu version and build dates ect.
The errors in the output are:
[COLOR="Red"]
(EE) Vesa(0): no matching modes
(EE) Screen(s) found, but none have a usable configuration

Fatal server error:
no screens found[/COLOR]

After the blue X server error screen im redirected back to a black/white commandline.
Once again, I google and search these forums and finds a guy with a similar problem:
([COLOR="Blue"][http://ubuntuforums.org/showthread.php?t=521032&highlight=Failed+to+start+the+server](http://ubuntuforums.org/showthread.php?t=521032&highlight=Failed+to+start+the+server)[/COLOR])

I thought merlinus (#3) reply sounded like a solution and gave it a try.
i write 'sudo dpkg-reconfigure xserver-xorg' and go throug the configuring as told, except i choose Vesa as driver, and I give the gfx 128mb as it is the intel GMA x3000 without memory.
after the configuring i write 'startx' in the prompt, but only get another Fatal error msg:

Caught signal 11.   Server aborting.

So... im really lost here and don't know what to do.
any help is appreciated.

thx
Hammedhaaret

---

### Post by kevinlyfellow on 2007-08-16
That looks like a great laptop to run linux on!  Except that the graphics card driver was only released about a week ago.  [http://www.reghardware.co.uk/2006/08/10/intel_posts_g965_linux_driver/](http://www.reghardware.co.uk/2006/08/10/intel_posts_g965_linux_driver/)
But intel says its old drivers should work too.

As a guess try to put "vga=771" (no quotes) as a kernel option.  

In other words, /boot/grub/menu.lst should have an entry that looks something like this.
```

title           Ubuntu, kernel 2.6.20-16-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=ab5fd55d-b3a3-473e-b39
5-49fa9af2e210 ro quiet splash vga=771
initrd          /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

```

---

### Post by dougfractal on 2007-08-16
sudo apt-get install xserver-xorg-video-intel 

check xorg.conf
driver "intel"
if fail 
 driver "i810"

bad resolution
sudo apt-get install 915resolution

man 915resolution  # for info

---

### Post by hammedhaaret on 2007-08-16
thanks for the replys.

but... I haven't got ubuntu installed yet. Can't boot from the darn CD.
so there isn't a /boot/grub/menu.lst yet is there?

and I'm pretty sure that I can't get on the internet either so apt-get wouldn't work.

please correct me if I'm wrong.

---

### Post by kevinlyfellow on 2007-08-16
> **hammedhaaret said:**
> thanks for the replys.

but... I haven't got ubuntu installed yet. Can't boot from the darn CD.
so there isn't a /boot/grub/menu.lst yet is there?

and I'm pretty sure that I can't get on the internet either so apt-get wouldn't work.

please correct me if I'm wrong.

Actually, you can get the wireless to work I think...  You can't use network manager, but when you are hangin out in the terminal, issue the command
```
ifconfig -a
``` and see the interface that are  detected (I'm assuming the issue to the internet is wireless, but this more or less will work with a wired network).  If you don't have eth0 and eth1 (or possible wlan0)
```
sudo modprobe ipw4965
```

Hopefully that will load the module.  Then open up as root /etc/network/interfaces with your favorite command line editor and make sure these lines are present so you can configure both the ethernet and wireless
```
auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
```

Then if you need to connect to wireless, make sure your switch is on.  Then look for the available networks 
```
iwlist scanning
```
will give you the available wireless networks.  Find the ESSID of the network you want and
```
sudo iwconfig eth1 essid <the essid you want>
```

Finally, for both ethernet (make sure its plugged in now) and wireless, do this
```
sudo ifdown -a
sudo ifup -a
```

With any luck you will have the interent... nice and easy ;-)

---

### Post by hammedhaaret on 2007-08-17
ok, update.

thanks to the alternate install cd i finally got it installed on the laptop.
I can boot but it still fails to start the X server and I'm send to a prompt.
I'm on the internet thanks to kevinlyfellow.
So it's only the inteldriver I seem to be missing.

when i write the 'sudo apt-get install xserver-xorg-video-intel' it tells me that there is no available version, but that it is referred to by another package and that it means that the package has been made unnecessary or that it can only be downloaded from another source.... 

i also read somewhere that the Intel GMA X3000 driver were only released about a week ago or so...   so is it available to ubuntu yet?

---

### Post by kevinlyfellow on 2007-08-17
> **hammedhaaret said:**
> ok, update.

thanks to the alternate install cd i finally got it installed on the laptop.
I can boot but it still fails to start the X server and I'm send to a prompt.
I'm on the internet thanks to kevinlyfellow.
So it's only the inteldriver I seem to be missing.

when i write the 'sudo apt-get install xserver-xorg-video-intel' it tells me that there is no available version, but that it is referred to by another package and that it means that the package has been made unnecessary or that it can only be downloaded from another source.... 

i also read somewhere that the Intel GMA X3000 driver were only released about a week ago or so...   so is it available to ubuntu yet?

Make sure the universe repos are listed.  /etc/apt/source.list should have these lines in it (assuming you are in the us)
```
deb http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-backports restricted main multiverse universe
```

If it looks like that, but not quite, just modify it to look like that.

Then 
```
sudo apt-get update
```

---

### Post by climber0085 on 2007-09-15
I'm having the same problem. My question is very noob - how do you read/edit the file /etc/apt/source.list from the console. I can't open it with gedit or any other editor (obviously) the way I usually do inside the gui. I am, however, connected to the internet (thanks!)

Also, how do you export the log file to be able to host it up on the forums?

Thanks for the help.

-r.

---

### Post by dougfractal on 2007-09-15
>  how do you read/edit the file /etc/apt/source.list from the console
> 
sudo gedit /etc/apt/sources.list
or

> sudo nano /etc/apt/sources.list

or

System >> Administration >> Software sources


> cat /var/log/Xorg.0.log
can be a bit long so post > grep EE /var/log/Xorg.0.log

or attach the file** cp /var/log/Xorg.0.log ~/Xorg.0.log.txt**

I have a script that tells me a lot about your system. run it and post the xinfo.tar.gz
```
mkdir ~/Xinfo
cd ~/Xinfo
wget -O xinfo.sh  http://fractaldimension.org.uk/ubuntu/xinfo.txt
chmod a+x ./xinfo.sh
./xinfo.sh
```


please attach the ***xinfo.tar.gz**

view script
[http://fractaldimension.org.uk/ubuntu/xinfo.txt](http://fractaldimension.org.uk/ubuntu/xinfo.txt)

---

### Post by climber0085 on 2007-09-15
Wow. thanks a million. nano works great (mind you, i cannot log in to do the system -> admin.. etc..)

Aside from uploading files (I'm still a bit fuzzy on how to save them to a pen drive from the console. I think  I have to mount the drive, but if so, I still don't know how to do that...) I get the following error:

```
...refered to by another source.
E: Package xserver-xorg-video-intel has no installation candidate.
```

Where should I go from here? Upload those files? Or is there something I failed to do to the repository list?...

Again, thanks for the help.

---

### Post by dougfractal on 2007-09-15
> Package xserver-xorg-video-intel

    * feisty (x11): X.Org X server -- Intel i8xx, i9xx display driver [universe]
      2:1.9.94-1ubuntu3: amd64 i386 powerpc

> 
mind you, i cannot log in to do the system -> admin.. etc..
why can't you?  It should be your normal login passwd

What is you wireless card?  
Do you have an ethernet cable?

It would make you life easier to use a cable just to get everything setup.
> 
lspci -nn
ifconfig
iwlist


> Or is there something I failed to do to the repository list?...
enable universe

> sudo synaptic
or 
> sudo software-properties-gtk

[http://fr.archive.ubuntu.com/ubuntu/pool/universe/x/xserver-xorg-video-intel/xserver-xorg-video-intel_1.9.94-1ubuntu3_i386.deb](http://fr.archive.ubuntu.com/ubuntu/pool/universe/x/xserver-xorg-video-intel/xserver-xorg-video-intel_1.9.94-1ubuntu3_i386.deb)

> sudo dpkg -i xserver-xorg-video-intel_1.9.94-1ubuntu3_i386.deb
> 
I'm still a bit fuzzy on how to save them to a pen drive from the console. I think I have to mount the drive, but if so, I still don't know how to do that


> ls /media
do you see your pendrive?
**yes**
cp MYFILE /media/NAMEOFUSB/

**no**
> sudo fdisk -l
look for usb partition (sdXX,    ie sda1 or sdb1) repace XX with the correct bit

> sudo  mkdir /mnt/usb
sudo mount /dev/sdXX /mnt/usb
cp MYFILE /mnt/usb/


 I use quote: for code and quote.

---

### Post by dougfractal on 2007-09-15
Looking around.
Although gutsy has a month to go, I think it will solve many of your problems

so install Gutsy Tribe 6 +

[http://kuscsik.blogspot.com/2007/06/how-to-install-intel-4965-wireless.html](http://kuscsik.blogspot.com/2007/06/how-to-install-intel-4965-wireless.html)
> !!!------
This guide is not actual anymore. Just update to the latest Ubuntu
Gutsy and boot with the generic kernel.
The wireless module is not automatically loaded, so you must load it manually:

sudo modprobe iwl4965

------!!!

[http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.04_(Feisty_Fawn)_on_a_ThinkPad_T61](http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.04_(Feisty_Fawn)_on_a_ThinkPad_T61)  (similar hardware)

---

### Post by climber0085 on 2007-09-16
Okay, so here's where I'm at:

1. I can connect to the internet.
2. I've updated everything from the repositories.
3. I've done
```
sudo apt-get install 915resolution

and

sudo dpkg-reconfigure xserver-xorg
startx

and

sudo apt-get install xserver-xorg-video-intel
```

and I've updated my repository list. 

Help!

---

### Post by dougfractal on 2007-09-16
> Help!

I'm not clear to what the problem is

> sudo apt-get update   # update sources.list
sudo apt-get upgrade   # upgrade ubuntu

does  your X look like [http://shadowarts.nonlogic.org/projects/thinkpad/screen_garbage.jpg](http://shadowarts.nonlogic.org/projects/thinkpad/screen_garbage.jpg) ?

is your driver in xorg.conf "i810" or "intel"?

---

### Post by climber0085 on 2007-09-16
I went ahead and updated the sources.list and upgraded, like you said. 

Usually, when I restart x, I restart the gdm (dpkg /etc/init.d/gdm stop then start), then restart x. When I do this, the screen flashes three times and then gives me a

```
XI0: Fatal IO error 104
```

then goes back to the prompt. So no, my screen doesn't look like that. If it did, I would have more hope. 

Also, I cannot get to my xorg.conf file. I know its in /etc/x11/xorg.conf.
I've tried to cd to /etc/x11/ directory to verify it (the x11 directory does exist, but I cannot cd to it), but every time I try to open it with nano, it doesn't work. gedit gives me the error that it cannot open the graphic interface (or something like that). 

Thanks a million, all the same. Even if there's no resolution, I feel that I've learned a lot.
Thanks for everything.

---

### Post by climber0085 on 2007-09-16
I've tried everything I can think of to get the "xserver-xorg-video-intel..." .deb package off the French servers. How do I download and install it? I've tried the "dpkg -i xserver-xorg..." after adding the other .us deb and deb-src lines to my sources.list file. If I try to add the fr.archive.ubuntu.com to it, I get an error. 

Again, thanks for the help.

---

### Post by climber0085 on 2007-09-16
Finally, I got into my xorg.conf file.
The driver I used setting up the file is the "vesa" driver.

I'm going to try using "intel" or "i810".
We'll see what happens...

---

### Post by climber0085 on 2007-09-17
So I switched it over to the intel driver, but without avail.
Now I get the message:

```
Fatal sever error:
Sever is already active for display 0.
If this sever is no longer running, remove /tmp/.X0-lock and start again.
```\

Ugh. I give up for the night.
Perhaps I'll get it to work for tomorrow.

---

### Post by dougfractal on 2007-09-17
cd /etc/**X11**/ 

> Usually, when I restart x, I restart the gdm (dpkg /etc/init.d/gdm stop then start), then restart x. When I do this, the screen flashes three times and then gives me 

do you mean 
```
sudo /etc/init.d/gdm stop
sudo /etc/init.d/gdm start
sudo /etc/init.d/gdm rest
```art

reconfigure X
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

the sources.list is a config file more than a download path

```
wget [http://fr.archive.ubuntu.com/ubuntu/pool/universe/x/xserver-xorg-video-intel/xserver-xorg-video-intel_1.9.94-1ubuntu3_i386.deb](http://fr.archive.ubuntu.com/ubuntu/pool/universe/x/xserver-xorg-video-intel/xserver-xorg-video-intel_1.9.94-1ubuntu3_i386.deb)

sudo dpkg -i xserver-xorg-video-intel_1.9.94-1ubuntu3_i386.de
```b

This can be handy download a web text browser
```
sudo apt-get install lynx
```


Have you had any luck with Gutsy Tribe 6?

---

### Post by climber0085 on 2007-09-18
I tried tribe 5 recently with no avail.
It hangs at startup (doesn't even get to a prompt). I've tried the multitudes of kernal boot parameter alterations, nothing really seems to work. :(

As a side note, I cannot install Sabayon either. They've reportedly added the drivers, but they forgot to allow SATA drives to read from an ide cd-rom drive :(.
Knoppix will load, but its not really for install (there are work arounds, but still...).
and OpenSuse will install with everything but the resolution (which seems to be related to this). 

Something else I found interesting is that Ubuntu v6.1 will load just fine, minus wireless and graphics. 
ho hum...

---

### Post by dougfractal on 2007-09-18
I had a computer that I had to install with 6.06 then upgrade but thats a long path to travel.

There is an alternate install disk.  Have you still got the feisty install?

With Knoppix whats the xorg.conf.  is it using driver "vesa"

[COLOR="Silver"]You could copy the /boot/vmlinuz  and /boot/initrd.gz   add it to the [/COLOR]

---

### Post by dougfractal on 2007-09-19
I've writen a script which downloads and compiles the latest intel drivers

I don't have intel so I can't say if it works.
If it works please let me know.
also any mods you make.


```
mkdir ~/intel
cd ~/intel
wget -O intel.sh http://fractaldimension.org.uk/ubuntu/intelinstall.txt
chmod a+x ./intel.sh
./intel.sh
```


view script 
[http://fractaldimension.org.uk/ubuntu/intelinstall.txt](http://fractaldimension.org.uk/ubuntu/intelinstall.txt)


If you use it good luck!!!

---

