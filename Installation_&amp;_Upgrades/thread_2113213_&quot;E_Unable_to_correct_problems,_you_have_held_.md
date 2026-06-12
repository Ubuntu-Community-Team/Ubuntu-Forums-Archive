---
title: "&quot;E: Unable to correct problems, you have held broken packages.&quot;"
date: 2013-02-06
forum: Installation &amp; Upgrades
---

### Post by Harripix on 2013-02-06
Hi guys,

I'm a super noob, and I've been searching forums for the past few hours to try and find a solution to this problem, but I've had no luck and so I'm looking for some help.

I started having this error "E: Unable to correct problems, you have held broken packages." when I tried to reinstall Amarok through the terminal earlier, here's the script: ```
$ sudo apt-get install amarok
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 amarok : Depends: kde-runtime but it is not going to be installed
          Depends: libkcmutils4 (>= 4:4.7) but it is not going to be installed
          Depends: libkdeui5 (>= 4:4.7) but it is not going to be installed
          Depends: libkdewebkit5 (>= 4:4.7) but it is not going to be installed
          Depends: libkdnssd4 (>= 4:4.7) but it is not going to be installed
          Depends: libkfile4 (>= 4:4.7) but it is not going to be installed
          Depends: libkio5 (>= 4:4.7) but it is not going to be installed
          Depends: libknewstuff3-4 (>= 4:4.7) but it is not going to be installed
          Depends: libnepomukcore4abi1 (>= 4:4.9.0) but it is not going to be installed
          Depends: libplasma3 (>= 4:4.7) but it is not going to be installed
          Recommends: kdemultimedia-kio-plugins (>= 4:4.2.0) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```

I then tried to install Rhythmbox, and got a similar problem, and this seems to happen for all other programs too. I've tried to use Software Center and Synaptic PM, without any luck, Synaptic doesn't see any broken packages. Synaptic says: > The following packages have unresolved dependencies. Make sure that all required repositories are added and enabled in preferences.

I don't know what I should be looking for, everything is "checked" in the repositories options in Syaptic, but could it be something to do with my sources list?: [PHP]# deb cdrom:[Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release i386 (20120817.3)]/ precise main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://archive.ubuntu.com/ubuntu precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu precise universe
deb http://archive.ubuntu.com/ubuntu precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu precise multiverse
deb http://archive.ubuntu.com/ubuntu precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu precise-backports restricted main multiverse universe

deb http://archive.ubuntu.com/ubuntu precise-security main restricted
deb http://archive.ubuntu.com/ubuntu precise-security universe
deb http://archive.ubuntu.com/ubuntu precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
##deb http://archive.canonical.com/ubuntu precise partner
## deb-src http://archive.canonical.com/ubuntu precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise main[/PHP]

I have also tried to do this: ```
cd /var/lib/apt
sudo mv lists lists.old
sudo mkdir -p lists/partial
sudo apt-get update
``` to no avail. Does anyone have any ideas? This is really frustrating, I really like Ubuntu but when things like this happen it makes me want to switch back to Windows...

---

### Post by Hakunka-Matata on 2013-02-06
> I don't know what I should be looking for, everything is "checked" in the repositories options in Syaptic, but could it be something to do with my sources list?:
Does this mean the CD option is checked in the repositories section?  If you're using the internet to retrieve packages, uncheck the CD option.

Your signature shows 1 Bean, if you are new to this forum, Welcome,

---

### Post by Harripix on 2013-02-06
Yeah, it's my first "bean", so thanks for the welcome!

> Does this mean the CD option is checked in the repositories section? No it's unchecked, but thanks for the tip

---

### Post by ibjsb4 on 2013-02-06
I am beginning to think something is going on with our download server.  I just tried loading amarok and got the same errors.  Earlier today I failed to download ubuntu-restricted-extras on a fresh install,
 due to unmet dependencies.  I decided to give it a day, but you could try another server.

---

### Post by Harripix on 2013-02-07
I hope you're right ibjsb4, but I have already tried to change servers and that didn't help

---

### Post by Hakunka-Matata on 2013-02-07
System: Ubuntu-Desktop 
Release 12.04 (precise) 64-bit
Kernel Linux 3.2.0-37-generic
GNOME 3.4.2

I just installed Amarok via command line using server 
[http://mirror.math.ucdavis.edu/ubuntu](http://mirror.math.ucdavis.edu/ubuntu)
completed successfully with no errors.


The following information comes from a simple google search on **Unable to correct problems, you have held broken packages**

You can get a list of actual held packages with:

```
dpkg --get-selections | grep hold
```
Another method of troubleshooting may be to use aptitude rather than apt-get to try to install your package:

```
sudo aptitude install <packagename>
```

Aptitude will give up less easily, and will attempt to find solutions which may involve modifying other packages. It may give you more explanation of the problem and options for fixing it.

---

### Post by Harripix on 2013-02-07
Thanks, I had already found this article, but don't understand how I can see the output of "```
dpkg --get-selections | grep hol",
``` how do I get it?

I should emphasize, this is not only Amarok, nothing seems to want to install. 

I'm trying now to do > sudo aptitude install amarok and it looks like it's working, but it's downloading 210MB of files... and from ```
 http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu/ precise
```... is this normal? And is there any way that I can get my software center to work again?

---

### Post by Hakunka-Matata on 2013-02-08
How to get the output of Code:  I see from your first post you know how to use the Terminal, so just copy the code into a terminal and hit enter, if you get nothing back, then no packages are being held.  By the way, to Paste into a Terminal window, the command is Ctrl-Shift-V, go figure.  That can be changed of course, but stock out of the box, it includes the Shift key. Experiment with it, instead of using | grep hold, try | grep ho for instance, it should return a whole bunch of names with the letters "ho" highlighted.  | grep filters the output, use the command w/o a filter ```
dpkg --get-selections 
```
and see what you get.  You can view the output of that command page by page with the | more switch. 
```
dpkg --get-selections | more

``` 
use the space bar to move to the next page, the same as you would in a Dos Terminal.
Commands are case sensitive, as is everything else in Linux, so often it's a good idea to copy a command and drop in into the Terminal to execute it, to avoid mistakes.  Especially when the command line is long,

Synaptic is for me the best way to install applications.   Are you aware of how to invoke/select different software sources, and servers?  It can all be done through synaptic,

---

### Post by Harripix on 2013-02-09
Thanks so much Hakunka-Matata, everything is working fine now by the looks of it, but for future reference, how can I select different software sources and servers?

H

---

### Post by mörgæs on 2013-02-09
If it works then please mark the thread 'solved'.

---

### Post by Hakunka-Matata on 2013-02-09
H, The two URLs I include are examples of how one can approach fixing a problem or just learning more about how Ubuntu works.  It's a stretch for any former Windows user to consider using a "Help" site to find the answer to a specific question.  You know what happens if you try that in MSWindows, it's useless.  I implore you to try using help in Ubuntu however, help.ubuntu.com is a wonderful URL IMHO.  Rather than rattle on about how to change the server mirror your system goes to, to download software you request, I suggest you try searching it @ help.ubuntu.com.  That said, I'll list three salient topics about installing new packages, etc.

[**[COLOR="DarkSlateBlue"]Use this link to learn how to deal with all three topics[/COLOR]**]("https://help.ubuntu.com/community/Repositories/Ubuntu")
[LIST]
[*]Selecting the Best Ubuntu Mirror server for downloading software
[*]select the sources where your software center searches for packages you request
[*]learn how to manually add PPAs, which is a souce outside those offered by the standard ubuntu installation
[/LIST]

Installing Grub, the first URL, is one I used an awful lot in the beginning of my Ubuntu education, and it "Sold" me on using this site to learn.  The snapshot of selecting a different mirror to download from is made with the package/application/software (call it what you want) named "gnome-screenshot" it's a great tool, if you don't have it, but want it, install it, and learn how to use it.

The attached .png file shows how I typed the command incorrectly two times before finding the correct name of the program, 'gnome-screenshot'.
There is also a .jpg attachment showing the GUI of selecting a different Download-Server mirror.  But if you go to help.ubuntu.com, you will see much better pictures of what the GUIs look like.

[https://help.ubuntu.com/community/Grub2/Installing]("https://help.ubuntu.com/community/Grub2/Installing")

[https://help.ubuntu.com/search.html?cof=FORID%3A9&cx=004599128559784038176%3Avj_p0xo-nng&ie=UTF-8&q=software+sources&sa=Search]("https://help.ubuntu.com/search.html?cof=FORID%3A9&cx=004599128559784038176%3Avj_p0xo-nng&ie=UTF-8&q=software+sources&sa=Search")

---

