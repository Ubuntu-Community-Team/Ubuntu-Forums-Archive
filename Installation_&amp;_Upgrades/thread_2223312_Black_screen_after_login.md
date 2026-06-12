---
title: "Black screen after login"
date: 2014-05-10
forum: Installation &amp; Upgrades
---

### Post by p.callan on 2014-05-10
Seems like I spend most of my Ubuntu user time on the forums or other places trying to fix endless amounts of bugs and errors. 


Wanted to install Sketchup for Ubuntu. Seems simple enough, right? WRONG! Used this guide:
[http://ubuntuhandbook.org/index.php/2013/07/install-sketchup-2013-ubuntu-13-04/](http://ubuntuhandbook.org/index.php/2013/07/install-sketchup-2013-ubuntu-13-04/)

When typing *winecfg* it tells me wine isn't installed (even though I just installed it). Fine I thought, I just need to log out and then in again as the author says. On login there is a black screen with only the mouse cursor. Nothing happens. Force restart and login again. Same results. Ergo The entire OS is now unusable and I have NO CLUE what is wrong.

I recently tried to upgrade from 12.04 to 14.04 and on [UpgradeNotes]("https://help.ubuntu.com/community/UpgradeNotes") it says the following:
> An upgrade is the process of going from an earlier version of Ubuntu to a newer version of Ubuntu with an installed system. An example of this would be going from Ubuntu 11.10 to Ubuntu 12.04 LTS. **To avoid damaging your running system, upgrading should only be done from one release to the next release** (e.g. Ubuntu 12.04 to Ubuntu 12.10) or from one LTS release to the next (e.g. Ubuntu 10.04 LTS to Ubuntu 12.04 LTS).

And, of course, as a noob I play it safe and follow the advice to the letter and upgrade one release at a time. However, by the time I get to 13.10 there have been so many errors that an upgrade to 14.04 is no longer possible. Not only am I now stuck on a non-LTS distro, but it is completely unusable.

So, I though "I don't care about 14.04 any more, I just want a usable distro, and since 12.04 worked rather nicely I can just roll back to that." WRONG AGAIN! [I find out here that this MIGHT be possible]("http://askubuntu.com/questions/49869/how-to-roll-back-ubuntu-to-a-previous-version") "With enough fighting". If I can go neither up nor down, the only options I have left is to either

1. Fix the errors in 13.10 to make it stable enough to keep using it. But how? I don't even know what's wrong.
2. Somehow rescue my files and then delete this OS for good.

Either way I need to fix the black screen situation first. But where do I start?

---

### Post by kc1di on 2014-05-10
start by going to a terminal and typing this command and listing the output here. 
```
lspci | grep VGA
```

Then this one ```
lsmod
```

what your going through is why I normally do a clean install, and have a separate /home partition.  that way you can save all your files and still have a new release.

---

### Post by p.callan on 2014-05-10
> lspci | grep VGA
01:05.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RS880M
 [Mobility Radeon HD 4225/4250]


> lsmod
snd 60790 11 snd_hda_codec_realtek,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
lib80211 14040 2 wl,lib80211_crypt_tkip
sp5100_tco 13643 0 
cfg80211 401762 1 wl
soundcore 12600 1 snd
shpchp 32129 0
i2c_piix4 17682 0 
mac_hid 13037 0
hid_generic 12492 0
usbhid 47361 0
hid 87370 2 hid_generic,usbhid
radeon 1312332 0
i2c_algo_bit 13197 1 radeon
ttm 75982 1 radeon
drm_kms_helper 46867 1 radeon
sky2 52946 0
ahci 25579 1
drm 242400 3 ttm,drm_kms_helper,radeon
libahci 26619 1 ahci
video 18777 1 samsung_laptop


> what your going through is why I normally do a clean install, and have a separate /home partition. that way you can save all your files and still have a new release.
I actually have an encrypted partition where I keep all my files for storage, except the ones I am currently working on, which are on my desktop :/ This is because I had some problems with the home folder in 12.04 (It wasn't encrypting). So perhaps I should be able to to a clean install over the old one, as long as I can get the files from the desktop onto a usb stick. I have my master thesis work-in-progress copy there so... kind of important :)
But my programs and settings all get wiped then, right? They're installed on the same partition as the OS.

Thanks for taking this on.

---

### Post by kc1di on 2014-05-10
yes you will have to redo your setting and reinstall any programs that are not defaults. 

But I think you'll have much less trouble doing a fresh install of 14.04.  Move everything you want to save to a external disk or H.D.  or upload it to the cloud I use Dropbox alot also copy works well they both offer free storage.  copy I think gives you 15 GB now. 

you can get copy [here.]("https://www.copy.com/home/")

in order to get your screen back you may need to re-install your Radeon driver.  
[this thread]("http://ubuntuforums.org/showthread.php?t=2190441") may be of help in diagnosing the problem.  13.10 had problems with amd/ati/radeon cards.

---

### Post by p.callan on 2014-05-11
Thanks. 
I now have the driver on a usb stick but I don't know how to install it from there...
How do I copy my files and programs without the GUI? And also, how can I make sure I got them all if I can't see them?

I did #7 of this:
[http://ubuntuforums.org/showthread.php?t=2190441](http://ubuntuforums.org/showthread.php?t=2190441)
But it didn't help. Then again I'm not sure what it is supposed to do.

By the way, while trying different suggestions I often get the message that 
Depends: libgl1-mesa-glx or libgl1

And it gives me the chance to install this but there seems to be no uplink "Could not resolve se.archive.ubuntu.com". My internet connection works fine on other machines.

i.e while doing this:
[http://wiki.cchtml.com/index.php/Ubuntu_Raring_Installation_Guide#Removing_Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Raring_Installation_Guide#Removing_Catalyst.2Ffglrx)
it doesn't work because there seems to be "unmet dependencies"

This is waay out of my league...
Bumping for help :/

I'm testing out [this]("https://help.ubuntu.com/community/RadeonDriver") at the moment.

**Testing the driver**
> sudo apt-get install mesa-utils
W: Not using locking for read only lock file /var/lib/dpkg/lock
E: Unable to write to /var/cache/apt/
E: The package lists or status file could not be parsed or opened.

> LIBGL_DEBUG=verbose glxinfo
glxinfo: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory

What does this* mean*, though? What is "parsed" for instance?
The GPU is [Mobility Radeon HD 4225/4250] [1002:9712]

Now doing [this]("https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection#Problem:_Need_to_purge_-fglrx"), but:
> sudo apt-get remove --purge xorg-driver-fglrx fglrx*
W: Not using locking for read only lock file /var/lib/dpkg/lock
E: Unable to write to /var/cache/apt/
E: The package lists or status file could not be parsed or opened.

It won't let me do anything...
If it is not possible to fix the problem then I need to figure out how to copy some files from the desktop using root, and also an installed program or two (Litecoin client for example) Can that be done?.

[B]
[COLOR=#ff0000]If there's any more info needed, please let me know.[/COLOR][/B]

Ok, I'm tying to figure out how to copy my files from desktop to usb stick. How is this done, please?

I cd to Desktop and ls or dir, but it only lists a file called TOR.desktop. NOT the two odt-files that I know are there.
Neither does it list any other files in any other directory. If I cd to the usb stick and ls or dir it lists nothing even though it is full of files and folders.
Someone suggested I 'clean' or update the system through root, but it won't connect to ubuntu or launchpad for some reason and so there's YET ANOTHER problem I don't know how to solve.

I've decided to forego everything else since I haven't been able to do my job for almost a week due to this error in the OS. I can't have a non-functioning computer and so these files are the only ones I will attempt to save. They contain a year's work and so I cannot lose them. As long as I will be able to access the encrypted volume mentioned above, through a new OS, I'll be just dandy.

But I am going to need some help on this. I've spent days and days now trying to solve problem after problem in a root terminal with zero success.

Since nobody is replying I'll just keep telling what I am doing.

Have now figured out that I have no internet connection.
ifconfig gives
eth0, eth1, lo, wlan1  all at 0 packets sent, received or otherwise. Adress is 127.0.0.1
So, I hook up the ethernet cable to the router and run 

dhclient eth0
/etc/dhcp/dhclient-enter-hooks.d/samba: line 46: /etc/samba/dhcp.conf.new: read-only file system
mv: cannot stat '/etc/samba/dhcp.conf.new': No such file or directory
RTNETLINK answers: File exists

So that didn't work. Again, I run:
ifconfig -a
eth0 inet addr:192.168.1.159

Yay! internal IP! But no external...
I try to remount the file system as readible-writeable

sudo mount -o remount,rw
[ a LOT of text ]

I gather something to mount must be specified, and that file SYSTEMS are mounted, not drives. (?) So I specify the filesystem of the OS partition:
sudo mount -o remount,rw ext4
mount: can't find ext4 in /etc/fstab or /etc/mtab

Mhm... What does that mean??
cd /etc/fstab
bash: cd: /etc/fstab: Not a directory

WHAT!? It just told me that's the directory concerned!
cd /etc/mtab
bash: cd: /etc/mtab: Not a directory

-_-   FFS...

Ok, let's try if I get a response to a ping and find out if the internet works as per [this]("http://ubuntuforums.org/showthread.php?t=871015").
ping google.com
64 bytes from arn06s01-in-f1.1e100.net (173.194.32.1) icmp_seq=X ttl=55 time=11.0ms

and keeps ticking... Doesn't tell me about any response...
How do I stop it from pinging...? 
Esc
^[ 

WHAT!? STOP!
Ctrl + Alt + Del

Back in recovery mode, root.
Trying again to mount the OS filesystem
sudo mount -o remount,rw /dev/sda1
mount: can't find /dev/sda1 in /etc/fstab or /etc/mtab

Well, this is a well-known dead end by now...
Found [this]("http://askubuntu.com/questions/175739/how-do-i-remount-a-filesystem-as-read-write") and am trying that.
mount -v | grep "^/" | awk '{print "\nPartition identifier: " $1  "\n Mountpoint: "  $3}'
Don't understand any of this...

Trying the following after a recommendation in the comments.
sudo mountall 
Ubuntu 13.10 user-machine tty1
user-machine login: mountall: Plymouth command failed
mountall: Disconnected from Plymouth

WTF is "Plymouth"?? Thinking: Why do people post crap that doesn't work??
[ enter login ]
[ enter password ]
Still in root... Is it working?

Tried:
host google.com [ [from here]("http://ubuntuforums.org/showthread.php?t=871015") ]
[ IP adresses ans some other info ]

Seems to collect information from google.com, which means Internet works. OK, then I can get back to the mesa-stuff.

Previously I solved monitor problems by [ [this]("https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection#Problem:_Need_to_purge_-fglrx") ] and purged fglrx, so trying that again.
sudo apt-get remove --purge xorg-driver-fglrx fglrx*
[ password for user ]
[ a lot of text about different forms of fglrx ]
Package 'fglrx-glx' is not installed, so not removed
Package 'fglrx-control-qt2' is not installed, so not removed
Package 'xfree86-driver-fglrx-dev' is not installed, so not removed
Package 'xorg-driver-fglrx-dev' is not installed, so not removed
E: Unable to locate package xorg-driver-fglrx

Mhm... So it isn't there? Ok, so let's install it as [per this]("https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection#Problem:_Need_to_purge_-fglrx").
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
[ text ]
The following packages have unmet dependencies: 
libgl1-mesa-glx : depends: libglapi-mesa (= 9.2.1-1ubuntu3)
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

Mhm... So I need to install that package first I guess.
sudo apt-get install libglapi-mesa
libwebkitgtk-3.0.0  :Depends libgl-mesa-glx or libgl1
[ same for the following ]
libwxgtk2.8.0, lsb-graphics, mesa-utils, nux-tools, stellarium, unity, virtualbox-qt, vlc, x11-utils, xorg
E: Unmet dependencies. Try apt-get -f install' with no packages (or specify a solution)

Aha, so probably libgl1 is pretty important. But why doesn't it install the dependancies on its own istead of telling me about it?
sudo apt-get install libgl1
[ text ] 
The following packages have unmet dependencies: 
libgl1-mesa-glx : Depends libglapi-mesa

FFS! I already tried to install libglapi-mesa! Stuck in a catch-22. Trying the next command on [that page]("https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection#Problem:_Need_to_purge_-fglrx") for the hell of it.
sudo dpkg-reconfigure xserver-xorg

Didn't do anything. At least didn't tell me about it...

Hmm... I wonder if this is what I have: "For systems with multiarch enabled (Ubuntu 11.10/Oneiric and later has  it by default), if you have installed more than one architecture of a  package, you have to specify each to reinstall them (or you will get an  "E: Internal Error, No file name for libgl1-mesa-glx"):" After all, I have 13.10 installed at the moment. I have no idea if I have more than one architecture of a package or what that means, but let's try it, as the other recommendations just go me into a catch-22.
sudo apt-get install --reinstall libgl1-mesa-glx:i386 libgl1-mesa-dri:i386 xserver-xorg-core
[ text ] Depends: libglapimesa

Ok, so:
sudo apt-get install --reinstall **libglapi-mesa** libgl1-mesa-glx:i386 libgl1-mesa-dri:i386 xserver-xorg-core
[ text ] The following packages have unmet dependencies:
libglapi-mesalts-raring : conflicts: libglapi-mesa
E: Unmet yada-yada

So there is some sort of conflict. But that isn't possible if libglapi-mesa isn't installed. So, which is it you stupid machine? And why are you talking about raring, when I have saucy?
Next step on the guide is: "To check which architectures you have installed, you must use dpkg, as no other program has such feature yet:"
dpkg --get-selections|grep libgl1-mesa
[COLOR=#ff0000]libgl1-mesa[/COLOR]-dri:i386                   install
[COLOR=#ff0000]libgl1-mesa[/COLOR]-dri-lts-raring:i386     deinstall
[COLOR=#ff0000]libgl1-mesa[/COLOR]-glx-lts-raring:i386     deinstall

What does that mean? It's definately not the same as the example though:
libgl1-mesa-dri                                 install
libgl1-mesa-dri:i386                            install
libgl1-mesa-glx                                 install
libgl1-mesa-glx:i386                            install

And that was the end of the guide!! HAHAHA! That was useless... Now what?
All right, it looks like there are no drivers at all for the GPU/VGA-monitor-whatever-thingy. Maybe I can install AMD/ATI drivers directly through root since it doesn't recognize the usb stick that has these drivers.
This is the url for the exact package: [http://www2.ati.com/drivers/legacy/amd-driver-installer-catalyst-13.1-legacy-linux-x86.x86_64.zip](http://www2.ati.com/drivers/legacy/amd-driver-installer-catalyst-13.1-legacy-linux-x86.x86_64.zip)
[http://www2.ati.com/drivers/legacy/amd-driver-installer-catalyst-13.1-legacy-linux-x86.x86_64.zip](http://www2.ati.com/drivers/legacy/amd-driver-installer-catalyst-13.1-legacy-linux-x86.x86_64.zip)
No such file or directory

sudo apt-get install [http://www2.ati.com/drivers/legacy/amd-driver-installer-catalyst-13.1-legacy-linux-x86.x86_64.zip](http://www2.ati.com/drivers/legacy/amd-driver-installer-catalyst-13.1-legacy-linux-x86.x86_64.zip)
E: Unalbe to locate package http
E: Couldn't find any package by regex 'http://www2.ati.com/drivers/legacy'

UUUUUGggggghhh! Getting sick of this.. I need a cup of coffe. To be continued.

Made a bootable usb stick of 14.04 and upgraded 13.10 from that. Worked well enough although all my programs were deinstalled. Screen and everything else works fine now though.
Thanks for all the help. You're welcome.

---

