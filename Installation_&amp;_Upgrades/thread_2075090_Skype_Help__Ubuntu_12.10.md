---
title: "Skype Help | Ubuntu 12.10"
date: 2012-10-23
forum: Installation &amp; Upgrades
---

### Post by AleksOne on 2012-10-23
Like a noob, i tried installing skype numerous ways, non of them worked. Today i notice there is skype on Ubuntu software centre, when i try install i get this error message:

The following packages have unmet dependencies:

skype: Depends: skype-bin but it is not going to be installed

How can i install skype ? what do i need to do? 

Im a noob. sorry. D:

---

### Post by moribashi on 2012-10-23
Got to skype.com and download Ubuntu 10.04 32 or 64-bit version of deb file. Double click it and it is done. :)

---

### Post by AleksOne on 2012-10-23
> **moribashi said:**
> Got to skype.com and download Ubuntu 10.04 32 or 64-bit version of deb file. Double click it and it is done. :)

I get this :

Selecting previously unselected package skype. 
(Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 151224 files and directories currently installed.) 
Unpacking skype (from .../skype-ubuntu_4.0.0.8-1_amd64.deb) ... 
dpkg: dependency problems prevent configuration of skype: 
 skype depends on ia32-libs; however: 
  Package ia32-libs is not installed. 
 
dpkg: error processing skype (--install): 
 dependency problems - leaving unconfigured 
Processing triggers for desktop-file-utils ... 
Processing triggers for bamfdaemon ... 
Rebuilding /usr/share/applications/bamf.index... 
Processing triggers for gnome-menus ...

---

### Post by mikewhatever on 2012-10-23
Let us see the output of **dpkg -l | grep skype** . It looks like skype-bin conflicts with something you've installed previously. Have you undone the previous installation attempts?

---

### Post by AleksOne on 2012-10-23
> **mikewhatever said:**
> Let us see the output of **dpkg -l | grep skype** . It looks like skype-bin conflicts with something you've installed previously. Have you undone the previous installation attempts?

How would i do that ? : P and no i havn't how would i undo prev. installation attempts?

---

### Post by mikewhatever on 2012-10-23
Open a terminal window (ctrl-alt-t), copy/paste the command and hit Enter. How exactly have you tried installing skype?

---

### Post by buckyaustin on 2012-10-23
You should remove the skype installs that have failed before in the past before trying to install a new working one.

So run this in terminal, "sudo apt-get remove skype". Then download the correct skype off the skype website. This should install without any problems.

---

### Post by AleksOne on 2012-10-23
> **mikewhatever said:**
> Open a terminal window (ctrl-alt-t), copy/paste the command and hit Enter. How exactly have you tried installing skype?

> **buckyaustin said:**
> You should remove the skype installs that have failed before in the past before trying to install a new working one.

So run this in terminal, "sudo apt-get remove skype". Then download the correct skype off the skype website. This should install without any problems.

  	 	 	 	 	 	   **rc  skype                                     4.0.0.8-1                                 amd64        Skype **
 

 **I get that when I type: dpkg -l | grep skype**
 

 **And ive tried to install it off skype.com like the guy at the top suggested, and ive tried to get it from the softwere centre, both dont work**
 

 

 

 **When I type: sudo apt-get remove skype**
 

 **I get :**
 **Reading package lists... Done **
 **Building dependency tree        **
 **Reading state information... Done **
 **Package 'skype' is not installed, so not removed **
 **The following packages were automatically installed and are no longer required: **
   **lib32asound2 lib32gcc1 lib32stdc++6 libc6-i386 **
 **Use 'apt-get autoremove' to remove them. **
 **0 upgraded, 0 newly installed, 0 to remove and 9 not upgraded. **
 

 **Is that right?**

---

### Post by mikewhatever on 2012-10-23
Try something like this from a terminal window:

```
sudo apt-get purge skype

sudo apt-get --purge autoremove

sudo apt-get update

sudo apt-get install skype
```

Please post the output of the last one.

---

### Post by AleksOne on 2012-10-23
Paste them individually or in one block?

---

### Post by mikewhatever on 2012-10-23
> **AleksOne said:**
> Paste them individually or in one block?

Individually, one by one. Hit Enter after each and wait for it to finish, then go to the next one.

---

### Post by AleksOne on 2012-10-23
> **mikewhatever said:**
> Try something like this from a terminal window:

```
sudo apt-get purge skype

sudo apt-get --purge autoremove

sudo apt-get update

sudo apt-get install skype
```Please post the output of the last one.


): I got this:

sudo apt-get install skype
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 skype : Depends: skype-bin but it is not installable
E: Unable to correct problems, you have held broken packages.

---

### Post by mikewhatever on 2012-10-23
That's strange. How about:
```
sudo apt-get install skype-bin
```

Hopefuly, we'll see what it conflicts with.

---

### Post by AleksOne on 2012-10-23
> **mikewhatever said:**
> That's strange. How about:
```
sudo apt-get install skype-bin
```Hopefuly, we'll see what it conflicts with.

It says:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package skype-bin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'skype-bin' has no installation candidate

---

### Post by mikewhatever on 2012-10-23
I think the installation package you've tried from skype.com may have added its own repository to the sources. Let us see the output of
```
cat /etc/apt/sources.list
```

---

### Post by AleksOne on 2012-10-23
> **mikewhatever said:**
> I think the installation package you've tried from skype.com may have added its own repository to the sources. Let us see the output of
```
cat /etc/apt/sources.list
```

This comes up:

cat /etc/apt/sources.list
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) quantal-security main restricted universe multiverse
deb [http://archive.canonical.com/](http://archive.canonical.com/) quantal partner
deb-src [http://archive.canonical.com/](http://archive.canonical.com/) quantal partner
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal-updates main restricted universe multiverse

---

### Post by mikewhatever on 2012-10-23
Well, I am almost out of ideas. Let's see the output of
```

ls /etc/apt/sources.list.d

apt-cache show skype

apt-cache show skype-bin
```

---

### Post by AleksOne on 2012-10-23
I know, i thought there might be a simple fix, thank you for your help so far! (:

1st one:

[B]apt-cache show skype
Package: skype
Priority: extra
Section: net
Installed-Size: 64
Maintainer: Brian Thomason <brian.thomason@canonical.com>
Architecture: amd64
Version: 4.0.0.8-0oneiric1
Depends: skype-bin
Filename: pool/partner/s/skype/skype_4.0.0.8-0oneiric1_amd64.deb
Size: 15072
MD5sum: b05cb1a1bcf14fae43dce4fc6b7e02e3
SHA1: 01350172bd1b9319afc491994754df707b03ac7c
Description: client for Skype VOIP and instant messaging service
 Skype is software that enables the world's conversations.  Millions of
 individuals and businesses use Skype to make free video and voice calls,
 send instant messages and share files with other Skype users.  Every day,
 people also use Skype to make low-cost calls to landlines and mobiles.
 .
 * Make free Skype-to-Skype calls to anyone else, anywhere in the world.
 * Call to landlines and mobiles at great rates.
 * Group chat with up to 200 people or conference call with up to 25 others.
 * Free to download.
[/B] 
2nd one:

[B]apt-cache show skype-bin
N: Can't select versions from package 'skype-bin' as it is purely virtual
N: No packages found[/B]

---

### Post by mikewhatever on 2012-10-23
OK, lets try removing the skype.com version in a different way:

```
sudo dpkg -P skype*
```

also, what's the output of 

```
ls /etc/apt/sources.list.d
```

---

### Post by AleksOne on 2012-10-23
> **mikewhatever said:**
> OK, lets try removing the skype.com version in a different way:

```
sudo dpkg -P skype*
```also, what's the output of 

```
ls /etc/apt/sources.list.d
```

Okay when i do the 1st one:

**sudo dpkg -P skype***

[I]dpkg: error: --purge needs a valid package name but 'skype*' is not: illegal package name in specifier 'skype*': character `*' not allowed (only letters, digits and characters `-+._')

Type dpkg --help for help about installing and un-installing packages 
[*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;

Options marked 
[*] produce a lot of output - pipe it through `less' or `more' ![/I]

**So i tried it again with out the '*'**

[I]sudo dpkg -P skype
dpkg: warning: ignoring request to remove skype which isn't installed

**Also when i paste : **[/I][I][B]ls /etc/apt/sources.list.d

Nothing happens. ):
[/B]

[/I]

---

### Post by AleksOne on 2012-10-23
Also, i don't know if it's relevant, after going my history, i remembered that i attempted to install skype through the terminal by:

[INDENT] 
[LIST]
[*]sudo add-apt-repository "deb [http://archive.canonical.com/](http://archive.canonical.com/) $(lsb_release -sc) partner"
[*]sudo apt-get update
[*]sudo apt-get install skype
[/LIST]
*from [http://www.noobslab.com/2012/10/install-latest-skype-4-in-ubuntulinux.html](http://www.noobslab.com/2012/10/install-latest-skype-4-in-ubuntulinux.html)*


(Sorry i forgot to mention this earlier)

[/INDENT]

---

### Post by mikewhatever on 2012-10-23
> **AleksOne said:**
> Also, i don't know if it's relevant, after going my history, i remembered that i attempted to install skype through the terminal by:

[INDENT] 
[LIST]
[*]sudo add-apt-repository "deb [http://archive.canonical.com/](http://archive.canonical.com/) $(lsb_release -sc) partner"
[*]sudo apt-get update
[*]sudo apt-get install skype
[/LIST]
*from [http://www.noobslab.com/2012/10/install-latest-skype-4-in-ubuntulinux.html](http://www.noobslab.com/2012/10/install-latest-skype-4-in-ubuntulinux.html)*


(Sorry i forgot to mention this earlier)

[/INDENT]

That seems to be correct. It just adds the partner repository and installs skype. There are several similar reports on the web, notably [http://askubuntu.com/questions/192425/installing-skype-on-12-04-64-bit-causes-errors](http://askubuntu.com/questions/192425/installing-skype-on-12-04-64-bit-causes-errors), but I've not found a solution. 
I suspect there is a packaging problem with the 64bit Quantal. You should be able to work around it by downloading [skype_4.0.0.8-0oneiric1_amd64.deb]("http://archive.canonical.com/pool/partner/s/skype/skype-bin_4.0.0.8-0oneiric1_i386.deb") from the partner repository and installing it by double clicking. Then try installing the skype package from the Software Center again. 
I'll file a bug report meanwhile.

---

### Post by AleksOne on 2012-10-23
When i double click it, it opens software centre and says:

Dependency is not satisfiable: skype-bin


Would it solve it by un-installing ubuntu and just reinstalling it? I have nothing else on here installed at the minute, and should i get a different ubuntu variation?

---

### Post by mikewhatever on 2012-10-23
Of cause it does! Wrong link, sorry.
Here's the right one: [http://archive.canonical.com/pool/partner/s/skype/skype-bin_4.0.0.8-0oneiric1_i386.deb](http://archive.canonical.com/pool/partner/s/skype/skype-bin_4.0.0.8-0oneiric1_i386.deb)

Fixed above as well.

PS:I don't think reinstalling will help. Pretty sure it a packaging problem.

---

### Post by AleksOne on 2012-10-23
lol when i try use the new one i get 

Wrong architecture 'i386'

---

### Post by AleksOne on 2012-10-23
> **mikewhatever said:**
> Of cause it does! Wrong link, sorry.
Here's the right one: [http://archive.canonical.com/pool/partner/s/skype/skype-bin_4.0.0.8-0oneiric1_i386.deb](http://archive.canonical.com/pool/partner/s/skype/skype-bin_4.0.0.8-0oneiric1_i386.deb)

Fixed above as well.

PS:I don't think reinstalling will help. Pretty sure it a packaging problem.

Okay thanks (: do you think will there be a fix for this in the near future?

---

### Post by mikewhatever on 2012-10-23
Well, it's a 32bit package, and there isn't a 64bit.

I've filed a bug report, so let's see what happens.
[https://bugs.launchpad.net/ubuntu/+source/skype/+bug/1070329](https://bugs.launchpad.net/ubuntu/+source/skype/+bug/1070329)

If you have nothing better to do, try reinstalling. It's quick, and I am rather curious.

---

### Post by AleksOne on 2012-10-23
> **mikewhatever said:**
> Well, it's a 32bit package, and there isn't a 64bit.

I've filed a bug report, so let's see what happens.
[https://bugs.launchpad.net/ubuntu/+source/skype/+bug/1070329](https://bugs.launchpad.net/ubuntu/+source/skype/+bug/1070329)

If you have nothing better to do, try reinstalling. It's quick, and I am rather curious.

Okay, I'll give it a try, when i do (Wednesday afternoon-ish) I'll post the result here / Send you it via PM if the thread gets closed

---

### Post by bikejunkie on 2012-10-23
You might have to activate multiarch support

```
sudo dpgk --add-architecture i386
sudo touch > /etc/dpkg/dpkg.cfg.d/multiarch
```Then you can install skype with 

```
sudo apt-get update
sudo apt-get install skpe
```Hope that helps.

---

### Post by draucia on 2012-10-23
try

```
sudo apt-get -f install
```

---

### Post by mikewhatever on 2012-10-23
So, there you have it:
> 
> It seems to be a packaging problem

It is not. This is an i386 package; you must have multiarch enabled to install it. Multiarch is enabled by default on all 64-bit installs of Ubuntu 11.10 and later.


Any ideas why the OP wouldn't have multiarch enabled?

---

### Post by AleksOne on 2012-10-24
> **bikejunkie said:**
> You might have to activate multiarch support

```
sudo dpgk --add-architecture i386
sudo touch > /etc/dpkg/dpkg.cfg.d/multiarch
```Then you can install skype with 

```
sudo apt-get update
sudo apt-get install skpe
```Hope that helps.

1st one:

[I]sudo dpgk --add-architecture i386
sudo: dpgk: command not found[/I]

2nd one: 

[I]sudo touch > /etc/dpkg/dpkg.cfg.d/multiarch
bash: /etc/dpkg/dpkg.cfg.d/multiarch: Permission denied

[/I]Any advice?

---

### Post by AleksOne on 2012-10-24
> **draucia said:**
> try

```
sudo apt-get -f install
```

I get this:

 [I]sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 18 not upgraded.[/I]

---

### Post by AleksOne on 2012-10-24
Going to uninstall this crap in a minute, any recommendations on what version i should install? or just re install ubuntu 12.10?

---

### Post by mastablasta on 2012-10-24
12.04 is supported for 4.5 more years...

---

### Post by Nagihiko on 2012-12-01
I'm having the same problem as AleksOne regarding Skype installation. I too have tried all the suggestions in this thread, but it's still not working. If anyone does find a solution to this, please PM me!~

-Edit-

[https://answers.launchpad.net/ubuntu/+source/skype/+question/214084](https://answers.launchpad.net/ubuntu/+source/skype/+question/214084)

I *finally* found a solution that worked!~

---

### Post by Jan Greeff on 2012-12-12
Individually.

Skype would not relaunch after reboot on Ubuntu 12.10 Quantal until I updated the installation via Synaptic, then Skype bin loaded and everything was fine.

---

