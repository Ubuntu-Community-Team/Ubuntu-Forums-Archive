---
title: "Installation of Scheme"
date: 2008-01-30
forum: Installation &amp; Upgrades
---

### Post by kenny2010ken on 2008-01-30
hello everyone 

my name is Kenny

I'm a student at UC Berkeley

right now I'm taking CS3 which requires software Scheme

I read the online installation steps from our school website

and follow the steps key in 

# wget [http://inst.eecs.berkeley.edu/~scheme/precompiled/Linux/STk-4.0.1-ucb1.3.6.i386.rpm](http://inst.eecs.berkeley.edu/~scheme/precompiled/Linux/STk-4.0.1-ucb1.3.6.i386.rpm)
	# apt-get install alien
	# alien -i STk-4.0.1-ucb1.3.6.i386.rpm

but the last step # alien -i STk-4.0.1-ucb1.3.6.i386.rpm says can't create file; file exists

what should I do ?

my Ubuntu is 7.10 x64

here's the website that address the steps 

[http://inst.eecs.berkeley.edu/~scheme/precompiled/Linux/](http://inst.eecs.berkeley.edu/~scheme/precompiled/Linux/)

thanks in advance for those who read this and try to help me  :)

---

### Post by PaulFr on 2008-01-30
Two possibilities to check:

1. You have Sound Synthesis Toolkit (stk) already installed. To verify ```
aptitude show stk
``` and verify that the state is "Not installed". If it is installed, **apt-get remove stk** as your Web page indicates.

2. You are not running as root (typically using sudo). Prefix the apt-get and alien commands with sudo.

Good luck.

---

### Post by kenny2010ken on 2008-01-31
I used the aptitude show stk

is shows uninstalled

and then I use the sudo for both apt- and aline line

but it shows can't write in the file, file exists...

> kenny@kenny-laptop:~$ aptitude show stk
Package: stk
State: not installed
Version: 4.2.0-9build1
Priority: optional
Section: universe/sound
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Uncompressed Size: 1360k
Depends: libstk0c2a, tk8.4, libasound2 (> 1.0.11), libc6 (>= 2.5-0ubuntu1),
         libgcc1 (>= 1:4.1.1-17ubuntu1), libjack0.100.0-0 (>= 0.101.1),
         libstdc++6 (>= 4.1.1-17ubuntu1)
Description: Sound Synthesis Toolkit example applications
 The example applications and synthesisers that come with the sound synthesis
 toolkit. 
 
 Homepage: [http://ccrma.stanford.edu/software/stk/](http://ccrma.stanford.edu/software/stk/)

kenny@kenny-laptop:~$ sudo alien -i STk-4.0.1-ucb1.3.6.i386.rpm
mkdir: cannot create directory `STk-4.0.1': File exists
unable to mkdir STk-4.0.1:  at /usr/share/perl5/Alien/Package.pm line 257.
kenny@kenny-laptop:~$ 



can anyone help me?

---

### Post by jfinkels on 2008-01-31
> **kenny2010ken said:**
> 
# wget [http://inst.eecs.berkeley.edu/~scheme/precompiled/Linux/STk-4.0.1-ucb1.3.6.i386.rpm](http://inst.eecs.berkeley.edu/~scheme/precompiled/Linux/STk-4.0.1-ucb1.3.6.i386.rpm)
	# apt-get install alien
	# alien -i STk-4.0.1-ucb1.3.6.i386.rpm

but the last step # alien -i STk-4.0.1-ucb1.3.6.i386.rpm says can't create file; file exists


Have you tried installing using the package manager?```
sudo aptitude install mit-scheme
```

If that is not an option for you, then to fix the last command, you will need to convert the .rpm package to a .deb package by typing the following:```
alien -d STk-4.0.1-ucb1.3.6.i386.rpm
```Note the -d option which signals alien to convert to .deb. After it is converted, use 'dpkg' to install the newly created .deb:```
dpkg -i STk-4.0.1-ucb1.3.6.i386.deb
```Note that the filename may be slightly different.

---

### Post by kenny2010ken on 2008-01-31
ok

I tired it again

and it can't change the .rpm to .pm

```
kenny@kenny-laptop:~$ sudo alien -d STk-4.0.1-ucb1.3.6.i386.rpm
[sudo] password for kenny:
mkdir: cannot create directory `STk-4.0.1': File exists
unable to mkdir STk-4.0.1:  at /usr/share/perl5/Alien/Package.pm line 257.

```

---

### Post by kenny2010ken on 2008-01-31
another thing I noticed was

that my Ubuntu is 64bit

and from my school websites

it says this

```
	Use a 32-bit computer to 'alien STk-4.0.1-ucb1.3.6.i386.rpm'
	On the 64-bit computer, run 'apt-get install ia32-libs'
	copy the $STK.deb file from the 32-bit computer to the local amd64, ie:
	'scp user@32bHost:~/$STK.deb root@local64bHost:~/.'
	On the 64-bit computer, run 'dpkg --force-architecture $STK.deb'
```

can someone explain to me what it means?

and yes, I need this specific scheme because that way I can have the same buildin as the lab computer does.

---

### Post by jfinkels on 2008-01-31
> **kenny2010ken said:**
> another thing I noticed was

that my Ubuntu is 64bit

and from my school websites

it says this

```
	Use a 32-bit computer to 'alien STk-4.0.1-ucb1.3.6.i386.rpm'
	On the 64-bit computer, run 'apt-get install ia32-libs'
	copy the $STK.deb file from the 32-bit computer to the local amd64, ie:
	'scp user@32bHost:~/$STK.deb root@local64bHost:~/.'
	On the 64-bit computer, run 'dpkg --force-architecture $STK.deb'
```

can someone explain to me what it means?

and yes, I need this specific scheme because that way I can have the same buildin as the lab computer does.

Alrighty, this is what you're going to have to do.

First, I recommend removing any .rpm or .deb packages, or any directories you have left over from previous (failed) attempts to install this.

Following the directions on the website:
> Installing:

      You need to have Korn Shell(ksh) installed on your system for this to install.

To install korn shell, type the following:```
sudo aptitude install ksh
```
> 
      For Debian GNU/Linux, you can use a program called 'alien' to convert the RPM package to a *.deb file.   'alien' is in the main debian archive (see [http://packages.debian.org/unstable/admin/alien](http://packages.debian.org/unstable/admin/alien)).   IE, as root:

      	# wget [http://inst.eecs.berkeley.edu/~scheme/precompiled/Linux/STk-4.0.1-ucb1.3.6.i386.rpm](http://inst.eecs.berkeley.edu/~scheme/precompiled/Linux/STk-4.0.1-ucb1.3.6.i386.rpm)

So to get the file, type the following in the terminal:```
wget http://inst.eecs.berkeley.edu/~scheme/precompiled/Linux/STk-4.0.1-ucb1.3.6.i386.rpm
```

> 
      	# apt-get install alien

To install alien, type:```
sudo aptitude install alien
```
> 
      	# alien -i STk-4.0.1-ucb1.3.6.i386.rpm	(uses dpkg)

Don't do this step yet. See below.
> 
      Note:   There is a package name conflict between the UCB Scheme ("stk") and a current package available through the Debian mirror system ( [http://packages.debian.org/unstable/sound/stk](http://packages.debian.org/unstable/sound/stk)), so if you run one of these:

      	# apt-get upgrade
      	# apt-get dist-upgrade 			(upgrade all packages)

      you should re-install UCB Scheme like this:

      	# apt-get remove stk			(the sound synth toolkit)
      	# dpkg -i stk_4.0.1-1_i386.deb

In essence, this means you should make sure that you have removed the package that is named "stk" in the Ubuntu/Debian repository, in case you have installed in the past. Type the following:```
sudo aptitude remove stk
```
> 
      For Debian GNU/Linux on a pure64 (amd64) system:

      	Use a 32-bit computer to 'alien STk-4.0.1-ucb1.3.6.i386.rpm'
      	On the 64-bit computer, run 'apt-get install ia32-libs'
      	copy the $STK.deb file from the 32-bit computer to the local amd64, ie:
      	'scp [email]user@32bHost:~/$STK.deb[/email] root@local64bHost:~/.'
      	On the 64-bit computer, run 'dpkg --force-architecture $STK.deb'

Ok, apparently you have to use alien to convert the .rpm to a .deb package ONLY on an x86 (i.e. 32-bit) computer system. You're going to have to copy the .rpm to a 32-bit computer, then run:```
alien -d STk-4.0.1-ucb1.3.6.i386.rpm
``` Then you're going to have to copy the .deb package back over to your 64-bit system.

Back on your personal 64-bit computer, install the following package:```
sudo aptitude install ia32-libs
```

Now to install the .deb package on your computer, type the following:```
sudo dpkg -i STk-4.0.1-ucb1.3.6.i386.deb
```Note that the name of the .deb may be slightly different from what I have written here.

Let me know if you have any other questions.

As a postscript, please post the full command and complete error output of any command that you want to show to the forum.

---

### Post by PaulFr on 2008-02-01
The exact error message shown as per your later post is: > mkdir: cannot create directory `STk-4.0.1': File existsi.e., there is already a directory called STk-4.0.1 in  your home directory and so the mkdir is failing (the "file" in "file exists" refers to this "directory"). This is confirmed by looking at /usr/share/perl5/Alien/Package.pm line 257 ```
my $workdir = $this->name."-".$this->version;
$this->do("mkdir $workdir") or
     die "unable to mkdir $workdir: $!";
```Either remove this directory, or make a temporary directory and then cd to that directory before using the alien -d command to convert to a .deb file.

For your 64-bit / 32-bit issues, you should follow the excellent advice given above.

---

### Post by kenny2010ken on 2008-02-01
no guys

it says 

dpkg: error processing STK_4.0.1-1_i386.deb ( - - install):
package architecture (i386) does not match system (amd64)
Error were encountered while processing:
 stk_4.0.1-1_i386.deb

I tried to remove the STK file

but it said I don't have permission...

I did used alien on another 32-bit computer and successfully transform it into .deb file

what should I do now?

---

### Post by PaulFr on 2008-02-02
You may have already solved it, but if not, here goes:

1. Copy the .deb file (which I presume you created on a 32-bit system) to your 64-bit system.

2. I presume you followed the instructions and have already run **sudo apt-get install ia32-libs**. If not, please do so now.

2. **sudo dpkg --force-architecture -i stk_4.0.1-1_i386.deb**

Hope this helps.

---

### Post by kenny2010ken on 2008-02-02
thanks guys 

I finally have the stk now

thank for all your helps

-Kenny

---

### Post by jfinkels on 2008-02-04
> **kenny2010ken said:**
> thanks guys 

I finally have the stk now

thank for all your helps

-Kenny

Great! I hope it works out for you! If you need any other help let us know. Enjoy the beauty that is functional programming.

---

