---
title: "Questions about ubuntu"
date: 2007-11-15
forum: Installation &amp; Upgrades
---

### Post by bourne- on 2007-11-15
Hey guys whats up. 

I am not really new to linux, although my knowledge is not very extensive. I recently decided to give ubuntu a whirl. I have been using fedora 7 on my laptop and I am really enjoying, So i thought I would give another distro a go.

I am liking it so far however I do have a few questions.
First of all I am noticing that while navigating through different windows there is A LOT of lag. The desktop environment appears to be very shifting and not smooth like I would have expected. I am assuming that this is because of my video card drivers maybe not being configured properly so I thought I would ask and see if anyone can suggest something for me to try to attempt to smooth things out a little.

Another question I have is about 'apt-get', which i understand to be similar to 'yum' that is used in fedora. So far I don't like 'apt-get' all that much as there doesn't seem to be very many programs available through it and I have been unsuccessful in my attempts to track down whether or not I can add more respositories, or if 'apt-get' even uses them. So I was wonder if someone might suggest what I can do to broaden 'apt-get's program options. In particular right away I am looking for: aMSN, amarok-extras-nonfree..

I think that is all I am really curious for the time being, I am sure that as I us it more and more I will have more, but for right now those are the ones that I would like to know the most.

Here is a break down of my system and the distro of unbuntu I am using:

AMD Athlon 64-bit 3200+
Asus K8V deluxe mainboard
1024 generic RAM
ATi Radeon 9800 Pro All-In-Wonder 128MB

And as for the distro I am using I am pretty sure that it is edgy with a kernel version of: 2.6.15-28-386

any help or suggestions would greatly be appreciated, thanks in advance.
todd

---

### Post by bourne- on 2007-11-15
Hello again, sorry to post again so soon. I have noticed another issue that seems kind of strange. I have been watching the CPU load indicator through the system monitor and the CPU usage spikes to 100% while doing just about anything. If I have a terminal window open and I shirt it on the desktop the CPU usage goes to 100% and stays there until I stop moving. I don't think that should really be and I am wondering if that is what is contributing to the system being so laggy?

thanks again in advance.

todd

---

### Post by torgrot on 2007-11-15
I only have the default plus restricted repositories enabled in Synaptic and a quick search found aMSN and there were a few referencing amarok.  I don't know if those will meet your needs, but I am sure if you were to be more agressive with the repositories in Synaptic you will find all that you need.

torgrot

---

### Post by torgrot on 2007-11-15
Click on System Administration Restricted drivers and make sure you have the ATI restricted driver enabled.  I have an ATI 9700 and use it with no problem.  There is another part to the x-server that I don't remember off hand that speeds it up a little more and allows you to enable the eye candy.

torgrot

---

### Post by seachnasaigh on 2007-11-15
Your video card is probably the culprit on lag, if not the AMD64 processor. I think Ubuntu offers a couple of flavours on the processor, and I've encountered several threads on problems with the 64 bit version. An upgrade to Gutsy 7.10 or Feisty 7.04 might help there. I'll let wiser heads play with that one but that's a direction to start looking. Ditto for the video card; Gnome in general really likes your video card to be right, I've found, regardless of the distro. Fedora (which I also use) has some better built-in support for video drivers for some reason. On all of the versions of Ubuntu I've used, I've had to do some video tweaking for spiffy video cards.

As far as apt-get goes, I'll give you what I've gotten. Having been a RedHat user since v6 and Fedora since RedHat went corporate, I've been a fan of yum and its inherent simplicity. However, with yum you do need to tell it what sort of things you're looking for. apt-get (or the synaptic package manager if you like the gui stuff) is no different. apt-get has a conf file that specifies what sort of things to go out and look for; the out-of-the-box version only specifies basic packages and security updates, which means it'll look for updates to things that were pre-installed with Ubuntu. To get edgier stuff, you need to add to the apt conf file the "universe" (supported packages that may or may not be foss and aren't automatically installed) and "multiverse" (packages that are/are not foss and are not directly supported by the Ubuntu community, but which may be supported by the underlying Debian community). Once those are added to the conf file, you can command line apt-get install (packageX) and reasonably expect to find it, or use the gui tool in synaptics package manager to tick off things you want and have them auto-installed.

I've found apt-get to be easier to use overall than rpm and yum when working with things a little off-centre, and just as easy when working with things that in Fedora I'd have to do the four-step trick with (tar -xvf <filename>; nav to the dir and then .config; then make; then make-install). Give it a little time ... it's a different paradigm, but so far I've been impressed with it and found it to be far more user-friendly. Let me know if you need specific code.

ckr

---

### Post by bourne- on 2007-11-15
yeah I didn't find either one of those two things you just described through 'apt-get' or synaptics

---

### Post by gcrussell1 on 2007-11-15
Widen your repository base by enabling universe and multiverse repos - easiest way is to go to system-administration-Software Sources and check the boxes and make sure to update the lists or the universe and multiverse repos won't be recognized. Incidentally, you might find the Synaptic Package Manager's GUI a little easier to use than the terminal interface (though you might be fine without it).

Incidentally, it's probably better if you upgrade to Feisty or Gutsy - Edgy's a bit dated - everything I've read says that Feisty's just as stable as Edgy, and while Gutsy's still got a few bugs (though I've run into none of them), it's definitely a viable option. Since they're newer, they should improve your hardware functionality without sacrificing any of Edgy's benefits.

The CPU spike issue has been noted many times on these forums, and you can probably do a quick search and find some threads to help you out with that.

---

### Post by bourne- on 2007-11-15
> **seachnasaigh said:**
> Your video card is probably the culprit on lag, if not the AMD64 processor. I think Ubuntu offers a couple of flavours on the processor, and I've encountered several threads on problems with the 64 bit version. An upgrade to Gutsy 7.10 or Feisty 7.04 might help there. I'll let wiser heads play with that one but that's a direction to start looking. Ditto for the video card; Gnome in general really likes your video card to be right, I've found, regardless of the distro. Fedora (which I also use) has some better built-in support for video drivers for some reason. On all of the versions of Ubuntu I've used, I've had to do some video tweaking for spiffy video cards.

As far as apt-get goes, I'll give you what I've gotten. Having been a RedHat user since v6 and Fedora since RedHat went corporate, I've been a fan of yum and its inherent simplicity. However, with yum you do need to tell it what sort of things you're looking for. apt-get (or the synaptic package manager if you like the gui stuff) is no different. apt-get has a conf file that specifies what sort of things to go out and look for; the out-of-the-box version only specifies basic packages and security updates, which means it'll look for updates to things that were pre-installed with Ubuntu. To get edgier stuff, you need to add to the apt conf file the "universe" (supported packages that may or may not be foss and aren't automatically installed) and "multiverse" (packages that are/are not foss and are not directly supported by the Ubuntu community, but which may be supported by the underlying Debian community). Once those are added to the conf file, you can command line apt-get install (packageX) and reasonably expect to find it, or use the gui tool in synaptics package manager to tick off things you want and have them auto-installed.

I've found apt-get to be easier to use overall than rpm and yum when working with things a little off-centre, and just as easy when working with things that in Fedora I'd have to do the four-step trick with (tar -xvf <filename>; nav to the dir and then .config; then make; then make-install). Give it a little time ... it's a different paradigm, but so far I've been impressed with it and found it to be far more user-friendly. Let me know if you need specific code.

ckr

Oh wow man thanks for the repsonse. Its good to get input from another fedora user. I have become quite accustomed to working in fedora and the switch to ubuntu I am noticing little things that are different (i miss the 'll' automcatically being setup). I am curious as to how exactly you add the two conf files you describe to apt? Is it similar to how you would if you were adding say, livna to the repository list for yum?

thanks for the help

todd

---

### Post by seachnasaigh on 2007-11-15
Yes, similar but easier. On a command line you have to sudo vim (or, er, ah sudo gedit if you like that editor) the /etc/apt/apt.conf file and in there you'll find a name (much like in /etc/yum/yum.conf) that specifies the url to go to and lists the various package repositories that are available. yum handles this in four separate conf files; apt does it in one. The line essentially identifies your version of Ubuntu and then the available repositories including basic, restricted, security, universe and multiverse.

This is the definitive guide locally for apt:
[https://help.ubuntu.com/community/AptGetHowto](https://help.ubuntu.com/community/AptGetHowto)
It has some great info and specific command-line code for getting various packages.

ckr

---

### Post by seachnasaigh on 2007-11-15
Just to be correct, 'cause that's important, let me code this for you. I grabbed my terminal and dug into the files I modded a couple of months back and it's not the direct /etc/apt.conf file, it's a little deeper (the guide above still applies!) Looks like this:

sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup
### backup the native install file just in case ;)

sudo vim /etc/apt/sources.list

### THIS is the source file found in fedora under yum.conf
### looks kinda like this ::
###sources.list
### General comments about the sources.list file
 deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) <VERSION> main restricted
 deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) <VERSION> main restricted
 
### Comment about the 'Update' repositories
### Comments about the role of the updates
 deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) <VERSION>-updates main restricted
 deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) <VERSION>-updates main restricted
### Obviously, replace <VERSION> with whatever version of Ubuntu you're running ...
### It'll be "dapper" or "edgy" or "feisty" or "gutsy" or whatever, lowercase
### now uncomment the lines below that so they look like this:
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) <VERSION> universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) <VERSION> universe multiverse
### and now to avoid version mismatches during upgrades ADD the following lines
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) <VERSION>-security universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) <VERSION>-security universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) <VERSION>-updates universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) <VERSION>-updates universe multiverse
### and then save the file.
### now run the following to update your packages:
sudo apt-get update

There ya go. Now you can get packages from anything available <caveat>including things that may or may not be legal where you live </caveat> to Ubuntu or Debian.

Good luck!

ckr

---

### Post by bourne- on 2007-11-15
> **seachnasaigh said:**
> Just to be correct, 'cause that's important, let me code this for you. I grabbed my terminal and dug into the files I modded a couple of months back and it's not the direct /etc/apt.conf file, it's a little deeper (the guide above still applies!) Looks like this:

sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup
### backup the native install file just in case ;)

sudo vim /etc/apt/sources.list

### THIS is the source file found in fedora under yum.conf
### looks kinda like this ::
###sources.list
### General comments about the sources.list file
 deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) <VERSION> main restricted
 deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) <VERSION> main restricted
 
### Comment about the 'Update' repositories
### Comments about the role of the updates
 deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) <VERSION>-updates main restricted
 deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) <VERSION>-updates main restricted
### Obviously, replace <VERSION> with whatever version of Ubuntu you're running ...
### It'll be "dapper" or "edgy" or "feisty" or "gutsy" or whatever, lowercase
### now uncomment the lines below that so they look like this:
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) <VERSION> universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) <VERSION> universe multiverse
### and now to avoid version mismatches during upgrades ADD the following lines
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) <VERSION>-security universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) <VERSION>-security universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) <VERSION>-updates universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) <VERSION>-updates universe multiverse
### and then save the file.
### now run the following to update your packages:
sudo apt-get update

There ya go. Now you can get packages from anything available <caveat>including things that may or may not be legal where you live </caveat> to Ubuntu or Debian.

Good luck!

ckr

aw man that is awesome. Thanks so much you have been sooo much help. I really appreciate you doing that for me. I will put it into play and hopefully I can get things running the way they should!


[quote="gcrussell1"]
Widen your repository base by enabling universe and multiverse repos - easiest way is to go to system-administration-Software Sources and check the boxes and make sure to update the lists or the universe and multiverse repos won't be recognized. Incidentally, you might find the Synaptic Package Manager's GUI a little easier to use than the terminal interface (though you might be fine without it).

Incidentally, it's probably better if you upgrade to Feisty or Gutsy - Edgy's a bit dated - everything I've read says that Feisty's just as stable as Edgy, and while Gutsy's still got a few bugs (though I've run into none of them), it's definitely a viable option. Since they're newer, they should improve your hardware functionality without sacrificing any of Edgy's benefits.

The CPU spike issue has been noted many times on these forums, and you can probably do a quick search and find some threads to help you out with that.
[/quote]

Thanks for the advice man. I will search for the CPU spike issue. I will also be looking into edgy, I didn't realize it was already so dated. I installed it some time ago on another hard drive i have in my system but I just have not had time to play with it. Thank you very much for taking the time to response though I will be looking into everything you suggested


Thanks again for all the responses guys. Hopefully I can get into ubuntu and enjoy it as much as i have fedora

---

### Post by bourne- on 2007-11-16
ust an update. I decided to upgrade to fiesty 7.04 and since doing that it seems to be running A LOT better on my system. The cpu spikes are gone as well everything is moving nicely on the desktop environment for the most part. There is still a little issue when windows are minimized but I think that I can live with that till I get a little more experienced and can maybe attempt to fix that.

thanks again for all the help guys I really appreciate it
todd

---

