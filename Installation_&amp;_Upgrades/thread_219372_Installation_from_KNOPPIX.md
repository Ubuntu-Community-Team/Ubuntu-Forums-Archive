---
title: "Installation from KNOPPIX"
date: 2006-07-19
forum: Installation &amp; Upgrades
---

### Post by Aranel on 2006-07-19
Hey... I've been trying to install Ubuntu Dapper for several days now because it is, to my knowledge, currently the only Linux distribution that provides my wireless card's driver natively. (To make a long story short, the BCM43xx driver seems to dislike me in all three of its other attainable forms.)

I first tried the install LiveCD, which took forever to do anything and froze on the second step. My computer runs other Linux LiveCDs just fine, and this one worked on another computer beautifully; obviously, that wasn't supposed to happen.So I tried the alternate install CD, which got a little further but gave me an equivalent of the Blue Screen of Death (which I have dubbed the Black Screen of Death with Two Little Gray Rectangular Thingies in It) at about 60% through the "select & install software packages" step. I gave up again after trying that approach three times to no avail. Then I tried booting from Windows using the GRUB4DOS method, but that ended with the same result as the alternate install. So now I'm on my last option: installing from Knoppix, as per [these directions](https://help.ubuntu.com/community/Installation/FromKnoppix).

I've successfully untarred the debootstrap tarball and run make. The directions now tell me to enter:

```
# DEBOOTSTRAP_DIR=`pwd` ./debootstrap --arch i386 breezy /mnt/ubuntu http://archive.ubuntu.com/ubuntu breezy
```

Now, since I've only been using Linux for a couple months, I'm not too hot with commands just yet... but... Something's definitely not right. I've changed the instances of *breezy* in the command to *dapper*, of course, but I don't think I get the first part of the command. Since I've extracted the tarball to /usr/local, I tried entering /usr/local/debootstrap-0.3.3.0ubuntu3=`pwd` for that part, but it gave me an error saying that /usr/local/debootstrap-0.3.3.0ubuntu3=/home/knoppix does not exist. If I enter the command literally, it tells me, "bash: ./debootstrap: Permission denied." It also does the same thing when I just omit the first part.

Could someone please help me with this? Am I supposed to have some sort of password for the "`pwd`" part? Ubuntu seems to have something against my computer (or vice-versa) so far, and this is basically my last leg here... I really would appreciate any help you could offer. Otherwise, I'll have to wait until other distributions start basing themselves on version 2.6.17+ of the Linux kernel.

---

### Post by catlett on 2006-07-19
First you need to be at a root terminal. In knoppix that means opening a terminal and entering ```
su 
```then press enter. I do not know if you need a password with the knoppix live cd or not.
Once it changes to the root terminal (it will say root@knoppix instead of knoppix@knopix)
Enter the command. With linux instructions you enter everything after #. # id telliong you the command needs to be given as root. If it was a $ then the command is to be given as user,
Enter this in the terminal
```
DEBOOTSTRAP_DIR=`pwd` ./debootstrap --arch i386 breezy /mnt/ubuntu http://archive.ubuntu.com/ubuntu breezy
``` I do not know anything about debootstrap but according to the instructions, that is the command string you are to enter as root.

---

### Post by Aranel on 2006-07-19
> **catlett said:**
> First you need to be at a root terminal. In knoppix that means opening a terminal and entering ```
su 
```then press enter. I do not know if you need a password with the knoppix live cd or not.
Once it changes to the root terminal (it will say root@knoppix instead of knoppix@knopix)
Enter the command. With linux instructions you enter everything after #. # id telliong you the command needs to be given as root. If it was a $ then the command is to be given as user,
Enter this in the terminal
```
DEBOOTSTRAP_DIR=`pwd` ./debootstrap --arch i386 breezy /mnt/ubuntu http://archive.ubuntu.com/ubuntu breezy
``` I do not know anything about debootstrap but according to the instructions, that is the command string you are to enter as root.

Yes, I'm aware of that, and I was root when I ran the command (or else I wouldn't have been able to extract the tarball to /usr/local :) ). That's why I find this odd; there should be *no* permissions denied as root. This is exactly what it did when I opened a new terminal:

knoppix@0[knoppix]$ su
root@0[knoppix]# cd /usr/local/debootstrap-0.3.3.0ubuntu3/
root@0[debootstrap-0.3.3.0ubuntu3]# DEBOOTSTRAP_DIR=`pwd` ./debootstrap --arch i386 dapper /mnt/ubuntu [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper
bash: ./debootstrap: Permission denied
root@0[debootstrap-0.3.3.0ubuntu3]#

I'm... confused.:confused:

---

### Post by Aranel on 2006-07-20
Well, I finally did get that part to work. I tried running make install and taking the "./" before debootstrap out of the command, and it worked like a charm.

But now, I'm having another problem... I'm trying to install GRUB, and the instructions say to install a dependency ("linux-image-386") first. But apt-get install can't seem to find it, and it refuses to install GRUB without that package. So I Googled its name and downloaded a .deb file, then I looked up how to install .deb files. This is what came up when I entered "dpkg -i linux-image-2.6.15-26-386_2.6.15-26.45_i386.deb" (which is the package's name):

> root@Knoppix:/# dpkg -i /home/linux-image-2.6.15-26-386_2.6.15-26.45_i386.deb
Selecting previously deselected package linux-image-2.6.15-26-386.
(Reading database ... 9287 files and directories currently installed.)
Unpacking linux-image-2.6.15-26-386 (from .../linux-image-2.6.15-26-386_2.6.15-26.45_i386.deb) ...

You are attempting to install an initrd kernel image (version 2.6.15-26-386)
This will not work unless you have configured your boot loader to use
initrd. (An initrd image is a kernel image that expects to use an INITial
Ram Disk to mount a minimal root file system into RAM and use that for
booting).

   As a reminder, in order to configure LILO, you need
   to add an 'initrd=/initrd.img' to the image=/vmlinuz
   stanza of your /etc/lilo.conf

I repeat, You need to configure your boot loader -- please read your
bootloader documentation for details on how to add initrd images.

If you have already done so, and you wish to get rid of this message,
please put
  "do_initrd = Yes"
in /etc/kernel-img.conf. Note that this is optional, but if you do not,
you will continue to see this message whenever you install a kernel
image using initrd.
Do you want to stop now? [Y/n]n
Setting up linux-image-2.6.15-26-386 (2.6.15-26.45) ...
/initrd.img does not exist. Installing from scratch, eh?
Or maybe you don't want a symbolic link here. Hmm? Lets See.
I notice that you do not have initrd.img symbolic
link. I can create one for you, and it shall be
updated by newer kernel image packages. This is
useful if you use a boot loader like lilo.
Do you want me to create a link from initrd.img to /boot/initrd.img-2.6.15-26-386?[Yn] y
/vmlinuz does not exist. Installing from scratch, eh?
Or maybe you don't want a symbolic link here. Hmm? Lets See.

So I need to configure my bootloader, which refuses to be installed until this is...? Could someone please explain this to me?

Anyway, this is still the message I get when I try to install GRUB:

> root@Knoppix:/# apt-get install grub
Reading package lists... Done
Building dependency tree... Done
Package grub is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package grub has no installation candidate

Please help!

---

### Post by catlett on 2006-07-20
Grub isn't in your repository list for some reason. That is the response when a package isn't available to synaptic.
The whole configuration of initrd thing isn't needed with grub. That warning pertains to lilo but you aren't going to be using lilo.(lilo is the original linux bootloader but grub has overtaken it because you don't have to do this very thing. FYI...lilo = [COLOR="Red"]li[/COLOR]nux [COLOR="Red"]lo[/COLOR]ader
An initrd goes with the kernel. You need to have vmlinuz and initrd in boot. . I am attaching a picture of my boot folder so you can see what I mean. You will need to install the linux image to your boot folder and then install grub.
You may want to add an ubuntu repository to your source list so you can get grub and the kernel image.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse


I would think that once the linux image is installed, grub will install without an issue. This may be of help [http://www.linuxjournal.com/article/4622](http://www.linuxjournal.com/article/4622)

---

### Post by Aranel on 2006-07-21
Well, I've got GRUB installed and running now. It didn't work at first because I apparently made a mistake in the creation of menu.lst (and it refused to be overwritten or deleted, even as root :-| ), so I reformatted hda3 and started the installation from scratch.

GRUB is working beautifully now, but... When I select Ubuntu from the list it now gives, I get a bunch of scrolling text that the kernel is coming up; but after awhile, a little flashing line appears at the bottom. When I press enter, I'm prompted for a localhost login. I enter root, a little paragraph about Ubuntu (disclaimers and stuff) comes up, and I'm landed with a command prompt. This is further than I've yet reached, but... I'm still not sure what to do.:-?

In my very insignificant knowledge of Linux and Ubuntu, I'm hypothesizing there may be something wrong with the whole... software system. I had to find DEBs of GRUB and the Linux kernel online, since apt-get install wouldn't work; I get a "command not found" error when I type nano at one point in the installation (that's a text editor, right? I had to open a second session and use Knoppix's KWrite to edit grub.conf). It said "base system installed successfully" towards the beginning of the installation, but... I dunno. Any ideas?

(Also, why is it that only one ext3 partition and one swap partition are created during the text installation? Is it supposed to happen that way? Mandriva and SuSE, the distros I've previously used, had three in total - one swap, one mounted at /, and the last mounted at /home. I'm just curious...)

Again, I'm stumped. I really would appreciate any help...

---

### Post by catlett on 2006-07-21
2 things can be happening right now. 
1. You are at a text login and need to enter ```
startx
``` to start the x window system. So log in and enter startx.
2. You have a server install of ubuntu and it doesn't have a gui or x window system because it is intended for a server not a desktop. This can be fixed by installing the ubuntu desktop meta-package. Log in and enter 
```
sudo apt-get install ubuntu-desktop
``` That will install gnome and everything else that comes with the base ubuntu desktop install.
Your experienxe is puzzling. I never seen someone have so many problems with ubuntu. The partitioning is correct. A home is good to have and many distros create it by default but ubuntu doesn't. Ubuntu just creates a swap and root.
I think the ubuntu-desktop install will finally get you there. After you get in, you might want to browse this [http://doc.gwos.org/index.php/DapperGuide](http://doc.gwos.org/index.php/DapperGuide) It is what I use when I do a new install. It gives you the commands and packages for dvd playback, mp3's, video card drivers etc.
Good luck. I think your almost there.

---

### Post by Aranel on 2006-07-22
Thanks once again, but... now I have yet another problem. apt-get install ubuntu-desktop returns an error saying that there's no such package in the repositories... I looked at that link you gave me, and I created a /etc/apt/sources.list file from what that document provided (there wasn't a sources.list file there to begin with, or even a sources.list_backup :-s ).

Then I tried booting up in Ubuntu again, and I entered "apt-get update" as root. What output greeted me? "Temporary failure" for *every single one of the repositories*. I entered ifconfig eth0 up to make sure the Internet connection was active and tried apt-get update again with the same results.

At this point, I'd almost be content with booting into a GUI, even with an uncooperative package manager, but I seem to be denied even that. I can't find a "ubuntu-desktop" DEB anywhere so I could at least get away from that command-line interface, and I'm really starting to get irritated (if it's not evident already).

Any guesses...?

Edit: Also, in the instructions, it might be important to note that I only got a "no such file or directory" error when I tried running /usr/sbin/base-config new. I just let that go, since it said I could configure it once I'd had the system installed, so...

Edit again: Going off on that tangent, I found a base-config DEB, saved it to a FAT32 storage partition, and booted up in Ubuntu again. I typed apt-get install base-config first of all, and that returned an error saying that two packages - belocs-locales-bin and locales - "replaced" it; so I couldn't install it that way. I then mounted the aforementioned FAT32 partition and typed dpkg -i [filename]. I was given an error message that belocs-locales-bin conflicted with it, so it couldn't be installed either. apt-get remove belocs-locales-bin and apt-get remove locales both returned an error message that they couldn't be installed (that's not what I told it to in the first place, dangit!) and that there was probably a bug somewhere. Something is definitely up here... is base-config obsolete? Is there another way I should be carrying its functions out? (I'm willing to try about anything at this point.)

...Do you think maybe even installing Breezy then updating to Dapper might work? This is so frustrating...

---

### Post by catlett on 2006-07-22
You are the Job of Ubuntu installs.
Here are 2 links that may be helpfull.
[http://packages.ubuntu.com/dapper/](http://packages.ubuntu.com/dapper/) Here is the Dapper packages link. You can download and install dappers packages as debs. It will also list the packages the package you want depends on.
The /etc/apt/sources.list from the dapper guide is the one I use. I don't know why you are having issues with it. You can go here for a list as well. It is an /etc/apt/sources.list generator [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)

Now that I am thinking about it, there is one more method you may be able to use. Ubuntu is based on Debian. Debian Sarge the current stable version of debian is the base for ubuntu. You may want to install debian and then change your source list to the dapper guides list. Then run 
```
sudo aptitude update
sudo aptitude dist-upgrade
```This should change your debian install into a dapper install. If for some change it didn't do it with the dist-upgrade you could still be able to manually change the packages with Synaptic Package manager or apt-get, as long as the list installed and updated.
This is the link to the debian sarge minimal installer. It is a small download because it uses the internet to download the packages. The cd image is just to get a basic setup installed and then it gets the rest online.[http://www.debian.org/CD/netinst/](http://www.debian.org/CD/netinst/)

---

### Post by Aranel on 2006-07-23
Thank you once again! I tried that Debian install, and... I think Debian and anything related to it hates me. It began like the Ubuntu alternate installer, detecting the network and all, but unlike Ubuntu's installer, it couldn't configure mine with DHCP. I tried entering all the information manually, but that didn't work either; I went ahead and installed the base system, it rebooted from the hard disk, and it just gave me timeout failures once it tried getting the rest from the Internet. I could burn more CD images, but would that do any good? I mean, do you think it would be able to connect once everything's installed?

At this rate, I may indeed end up covered in sores...:-x

---

### Post by Aranel on 2006-07-24
Aha, got that one solved by booting into the 2.6 kernel instead.

Now the same thing that I ended up with in Ubuntu (a command-line interface) is happening now, except this time around I'm getting a proper error message and the package manager seems to work. It goes through all the steps of booting, then blinks like it's going to load the GUI. It goes back to the booting screen after a moment, then tries it again. And again. Then I get a message saying that X couldn't start, it will stop trying until I have the problem resolved, and would I like to see the output.

I suppose that would explain a few of the problems I've had... If Debian's graphical interfaces have issues with my computer, that would explain it taking forever and freezing in the LiveCD. It would also explain why GNOME didn't want to come up when I tried prodding it in Ubuntu... but yeah. I think this is probably the source of the problem, but is it fixable somehow? I mean, the Ubuntu LiveCD worked fine on other computers, and other distributions run perfectly on this one... I dunno. At this point, I think I'll finally have to succumb to the inevitable. :-k

---

### Post by catlett on 2006-07-24
It would stink to have hardware stop you. Do you have an unusual setup? Are you using a sun monitor or something?
The last thing I can think of is to run ```
dpkg-reconfigure xserver-xorg
``` In ubuntu you would put sudo before the command. In Debian you would have to be at a root terminal. (after you log in, type su and then your administrator password)
That command in ubuntu takes you through the configuration of x. It will ask about and then configure you monitor, video card and keyboard/mouse.
To give yourself the best chance possible, make sure you have your hardware specs handy (even if you have to go to the support page and get the manual for your monitor)
The more info you give the configurer the better. Meaning the horizontal and vertical refresh rates of your monitor, The amount of ram your video card has and the model number, etc.
If you can't boot into x then....I don't know what else to do.
You may want to try another distro that isn't debian based. Actually you are definitely more capable than most linux users. You may be interested in Gentoo. In Gentoo, you configure everything from scratch. You compile the kernel and add the modules you want to boot with the kernel. You compile and configure the sound server etc. From what you have already done, you sound like a gentoo person already.Plus there wiki is the best out there. Full length step by step how tos on everything.
Just in case debian craps out on you again here are a couple of gentoo links.
[http://forums.gentoo.org/index.php](http://forums.gentoo.org/index.php)
[http://gentoo-wiki.com/Main_Page](http://gentoo-wiki.com/Main_Page)
Good luck

---

### Post by Aranel on 2006-07-24
I've got Debian working! I entered dpkg-reconfigure xserver-xfree86 and just played around with it until GNOME came up. Turns out it seemed to have the wrong type of video card driver... I'll try doing what you suggested right now. Thank you!

But I don't think I'm ready for Gentoo at the moment... I've only been using Linux for a couple months. I think I'll try to get comfortable with it a little more before doing anything like that. Thanks, though.:D

---

### Post by catlett on 2006-07-24
Great! Perserverance paid off. If you have debian, keep with it. Gentoo I haven't gotten to but it is my next install and challenge. 
I used there sound server wiki to get my new sound card working and I got intrigued. Well good luck.

---

### Post by Aranel on 2006-07-25
Well, I tried using those commands you gave to "turn it into" Ubuntu, and it seemed to be going fine... then the whole thing abruptly committed suicide (like the alternate install), and suddenly the repositories stopped working (like the Knoppix install). I guess Ubuntu just hates my computer, and I believe it's high time I gave up on it.

But I think I'll stick with Debian, if I can get the kernel upgraded (since from what I've seen, it seems much easier in Debian than it is in SuSE, which doesn't seem to like kernel upgrades in the least). The point of trying to switch to Ubuntu in the first place was for support of my wireless card, which 2.6.17+ kernels provide.

Anyway, thank you *SO* much for all the help you've given me. I really appreciate it.:D

---

### Post by catlett on 2006-07-25
Well you didn't get ubuntu but Debian is great. As you know Ubuntu is based on debian (as well as knoppix, mempis, puppy, xandros, linspire and on and on). I only mention them to show that your configuration options with Debian are almost limitless. It is rock solid and has a huge repository.
This is one you are going to want to add [http://hpisi.nerim.net/](http://hpisi.nerim.net/) Scroll down the page and you will see the lines to add to your repository list. It is the debian multimedia repo, in case you are wondering. That is where you will get mplayer and such.
Here are a couple of more Debian links
[http://d-i.alioth.debian.org/manual/en.i386/index.html](http://d-i.alioth.debian.org/manual/en.i386/index.html)
[http://www.debian.org/](http://www.debian.org/)
[http://forums.debian.net/](http://forums.debian.net/)

Good luck. And about the thank you, as the saying goes - Don't pay me back. Pay it forward. :-D

---

