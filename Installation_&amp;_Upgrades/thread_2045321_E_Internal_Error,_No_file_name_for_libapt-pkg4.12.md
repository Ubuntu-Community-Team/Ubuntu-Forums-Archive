---
title: "E: Internal Error, No file name for libapt-pkg4.12"
date: 2012-08-21
forum: Installation &amp; Upgrades
---

### Post by manvvip on 2012-08-21
Upgraded as normal and then:

-------------------------------------------------------------------
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libapt-pkg4.12 : Breaks: libapt-pkg4.12:i386 (!= 0.8.16~exp12ubuntu10.3) but 0.8.16~exp12ubuntu10.2 is installed
 libapt-pkg4.12:i386 : Breaks: libapt-pkg4.12 (!= 0.8.16~exp12ubuntu10.2) but 0.8.16~exp12ubuntu10.3 is installed
E: Unmet dependencies. Try using -f.
--------------------------------------------------------------
also:

----------------------------------------------------------------
dpkg: error processing libapt-pkg4.12 (--configure):
 libapt-pkg4.12:amd64 0.8.16~exp12ubuntu10.3 cannot be configured because libapt-pkg4.12:i386 is in a different version (0.8.16~exp12ubuntu10.2)
Errors were encountered while processing:
 libapt-pkg4.12
anonymou5@anonymou5-kdeBook:~/Documents$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libapt-pkg4.12:i386
The following packages will be upgraded:
  libapt-pkg4.12:i386
1 upgraded, 0 newly installed, 0 to remove and 24 not upgraded.
1 not fully installed or removed.
Need to get 0 B/941 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? Y
E: Internal Error, No file name for libapt-pkg4.12
----------------------------------------------------------------


How to solve this? Can no longer upgrade.

---

### Post by e8hffff on 2012-08-21
Same problem.  I think this is the result of using 'proposed' packages in say Synaptic Package Manager and faulty apt release.

I hope someone posts the solution or if there is a update to correct the missing information.

---

### Post by bluedalek on 2012-08-21
I am having the same problem..

```
XXX@XXX-desktop:~/Documents$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libapt-pkg4.12 : Breaks: libapt-pkg4.12:i386 (!= 0.8.16~exp12ubuntu10.3) but 0.8.16~exp12ubuntu10.2 is installed
 libapt-pkg4.12:i386 : Breaks: libapt-pkg4.12 (!= 0.8.16~exp12ubuntu10.2) but 0.8.16~exp12ubuntu10.3 is installed
E: Unmet dependencies. Try using -f.
XXX@XXX-desktop:~/Documents$ sudo apt-get -f install 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libsmbclient:i386 libopenctl0.8 libtalloc2:i386 libgtlfragment0.8 libgmp10:i386 libqtshiva0.1 gstreamer0.10-alsa:i386 phonon:i386
  libpolkit-gobject-1-0:i386 libwbclient0:i386 libapt-inst1.4:i386 libxmuu1:i386 libboost-test1.46.1 libboost-graph1.46.1 wine-gecko1.6
  wine-gecko1.6:i386 libgtlcore0.8 libapt-pkg4.12:i386 libphonon4:i386 libopenshiva0.8 libhunspell-1.3-0:i386 phonon-backend-gstreamer:i386
  libpolkit-agent-1-0:i386 libboost-serialization1.46.1 libcurl3-gnutls:i386 libssh-4:i386 libusb-1.0-0:i386
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libapt-pkg4.12:i386
The following packages will be upgraded:
  libapt-pkg4.12:i386
1 upgraded, 0 newly installed, 0 to remove and 28 not upgraded.
1 not fully installed or removed.
Need to get 0 B/941 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
E: Internal Error, No file name for libapt-pkg4.12
XXX@XXX-desktop:~/Documents$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libapt-pkg4.12 : Breaks: libapt-pkg4.12:i386 (!= 0.8.16~exp12ubuntu10.3) but 0.8.16~exp12ubuntu10.2 is installed
 libapt-pkg4.12:i386 : Breaks: libapt-pkg4.12 (!= 0.8.16~exp12ubuntu10.2) but 0.8.16~exp12ubuntu10.3 is installed
E: Unmet dependencies. Try using -f.
```

Anyone have any thoughts?

---

### Post by latebeat on 2012-08-21
+1 here..
This just happened today, dunno why.


```
$ sudo apt-get upgrade 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libapt-pkg4.12 : Breaks: libapt-pkg4.12:i386 (!= 0.8.16~exp12ubuntu10.3) but 0.8.16~exp12ubuntu10.2 is installed
 libapt-pkg4.12:i386 : Breaks: libapt-pkg4.12 (!= 0.8.16~exp12ubuntu10.2) but 0.8.16~exp12ubuntu10.3 is installed
E: Unmet dependencies. Try using -f.

```

so I did..

```
$ sudo apt-get -f install 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libapt-pkg4.12:i386
The following packages will be upgraded:
  libapt-pkg4.12:i386
1 upgraded, 0 newly installed, 0 to remove and 25 not upgraded.
2 not fully installed or removed.
Need to get 0 B/941 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
E: Internal Error, No file name for libapt-pkg4.12
```


I also tried to download it manually and install:

```
$ sudo dkpg -i libapt-pkg4.12_0.8.16~exp12ubuntu10.2_i386.deb 
sudo: dkpg: command not found
latebeat@zod:~/Downloads$ sudo dpkg -i libapt-pkg4.12_0.8.16~exp12ubuntu10.2_i386.deb 
(Reading database ... 216412 files and directories currently installed.)
Preparing to replace libapt-pkg4.12:i386 0.8.16~exp12ubuntu10.2 (using libapt-pkg4.12_0.8.16~exp12ubuntu10.2_i386.deb) ...
Unpacking replacement libapt-pkg4.12:i386 ...
dpkg: error processing libapt-pkg4.12:i386 (--install):
 libapt-pkg4.12:i386 0.8.16~exp12ubuntu10.2 cannot be configured because libapt-pkg4.12:amd64 is in a different version (0.8.16~exp12ubuntu10.3)
Errors were encountered while processing:
 libapt-pkg4.12:i386

```

I'm running out of ideas, any suggestions please?



> **bluedalek said:**
> I am having the same problem..

---

### Post by e8hffff on 2012-08-21
You guys and maybe girls maybe interested in this;

[http://translate.google.com/translate?sl=auto&tl=en&js=n&prev=_t&hl=en&ie=UTF-8&layout=2&eotf=1&u=http%3A%2F%2Fforum.ubuntuusers.de%2Ftopic%2Faktualisierungsproblem-wine-1-5%2F%23post-4722237&act=url]("http://translate.google.com/translate?sl=auto&tl=en&js=n&prev=_t&hl=en&ie=UTF-8&layout=2&eotf=1&u=http%3A%2F%2Fforum.ubuntuusers.de%2Ftopic%2Faktualisierungsproblem-wine-1-5%2F%23post-4722237&act=url")

I was able to eliminate the broken-packages, and upgrade new updates, but I still get some errors over the libapt files.   Note I'm on 'proposed' mode hoping to get newer versions that fix the whole problem!

If you ever get the question to remove a heap of installs, then don't do it.  Tinker till you get what you want.

---

### Post by manvvip on 2012-08-21
Thanks for the find e8hffff

Turning off proposed worked, hmmm seems we have to wait for a solution.

---

### Post by manvvip on 2012-08-22
I turned off proposed

upgraded and autoremove'd

then proposed on

used Muon (for the first time ever) chose "Full-Ugrade" after update. Muon allowed me to "unmark" libapt-pkg4.12:386 and it auto-unmarked its dependencies.

Then I was able to install all the new packages and the new kernel.

---

### Post by bluedalek on 2012-08-22
> **manvvip said:**
> I turned off proposed

upgraded and autoremove'd

then proposed on

used Muon (for the first time ever) chose "Full-Ugrade" after update. Muon allowed me to "unmark" libapt-pkg4.12:386 and it auto-unmarked its dependencies.

Then I was able to install all the new packages and the new kernel.

This worked for me too...thanks!

---

### Post by funicorn on 2012-08-22
> **manvvip said:**
> Thanks for the find e8hffff

Turning off proposed worked, hmmm seems we have to wait for a solution.

I don't understand how. Turning off proposed I stills meet the same mistake. Because apt always show the same message when "apt-get update"

---

### Post by manvvip on 2012-08-22
> **funicorn said:**
> I don't understand how. Turning off proposed I stills meet the same mistake. Because apt always show the same message when "apt-get update"
Not sure.

Used a mixture of two packet managers and apt-get (but I reckon aptitude could have presented better answers quicker, and finding out only now that aptitude is missing, and can only use apt-get. :( )

Try one of these:

1st,   disable proposed inside of synaptic (or similar)

2nd,   apt-get download libapt-pkg4.12/precise-security
3rd,   sudo dpkg -i libapt-pkg4.12_0.8.16~exp12ubuntu10.2_amd64.deb 

Then after try, still bad, then

4th,   sudo dpkg --force-depends -r libapt-pkg4.12
5th,   sudo dpkg -i libapt-pkg4.12_0.8.16~exp12ubuntu10.2_amd64.deb 
6th,   wget [http://security.ubuntu.com/ubuntu/pool/main/a/apt/libapt-pkg4.12_0.8.16~exp12ubuntu10.2_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/a/apt/libapt-pkg4.12_0.8.16~exp12ubuntu10.2_amd64.deb) 

try
Then still maybe bad, then

7th,   sudo dpkg --force-depends -r libapt-pkg4.12:i386
8th,   sudo dpkg -i libapt-pkg4.12_0.8.16~exp12ubuntu10.2_amd64.deb 
9th,   sudo apt-get -f install 
try
(Tried all this random stuff and can't remember exactly, i checked after doing stuff, looking at libapt-pkg4.12:386's status each time in synaptic, to see what it was doing, (without clicking fix broken packages, as this wants the libapt-pkg4.12:386 marked as an upgrade, and we DONT want that. This is why I went to Muon package manager, that allowed me to unmark it)

Then, this is what I did, and this worked for me,

10th,   Back into synaptic and enable proposed.

11th,    Update within Muon Package manager (because I couldn't unmark libapt-pkg4.12:386 with apt-get or synaptic)

12th,    click "Full-Update"
13th,    select libapt-pkg4.12:386i and click "unmark" (this also unmarks the other apt stuff)
14th,    Press Apply

Hmmm, that's how I solved my problem and installed the latest kernel, etc. , and will wait for libapt*.*:386*blah2.blah and apt.blah etc. to get their problems sorted.

---

### Post by latebeat on 2012-08-22
Thanks for the help guys! It's all good now...
This fixed it for me...


> **manvvip said:**
> 

1st,   disable proposed inside of synaptic (or similar)

2nd,   apt-get download libapt-pkg4.12/precise-security
3rd,   sudo dpkg -i libapt-pkg4.12_0.8.16~exp12ubuntu10.2_amd64.deb 



---

### Post by manvvip on 2012-08-27
This is now the longest time Iv'e waited for a fix.

We need this problem resolved.

---

### Post by manvvip on 2012-08-31
I hope I havn't done anything wrong here, but by also removing 
libapt-inst1.4:386
It seems to have solved the problem?

Anyone else can confirm this?

This seems to be the solution after doing the above.

sudo dpkg --force-depends -r libapt-inst1.4:i386

---

### Post by manvvip on 2012-08-31
As far as I can gather, all is fine.

Am now changing the status to solved as of this date.

Thank you everyone.

---

### Post by latebeat on 2012-08-31
> **manvvip said:**
> As far as I can gather, all is fine.

Am now changing the status to solved as of this date.

Thank you everyone.

For me it's solved but only if I keep the pre-released updates disabled. If enable them I still get the libapt error

---

### Post by manvvip on 2012-09-01
Hmmm, changed status back to unsolved, grrrrrrrr, aaaaaagh.

Have you tried

Put pre-released back on then,
sudo dpkg --configure -a
sudo dpkg --force-depends -r libapt-pkg4.12:i386
sudo dpkg --force-depends -r libapt-inst1.4:i386
sudo dpkg -i libapt-pkg4.12_0.8.16~exp12ubuntu10.2_amd64.deb

Still same?
(maybe I just randomly typed the right thing, unfortunately not sure what, and fluked it!!! hehe)

---

### Post by latebeat on 2012-09-01
> **manvvip said:**
> Hmmm, changed status back to unsolved, grrrrrrrr, aaaaaagh.

Have you tried

Put pre-released back on then,
sudo dpkg --configure -a
sudo dpkg --force-depends -r libapt-pkg4.12:i386
sudo dpkg --force-depends -r libapt-inst1.4:i386
sudo dpkg -i libapt-pkg4.12_0.8.16~exp12ubuntu10.2_amd64.deb

Still same?
(maybe I just randomly typed the right thing, unfortunately not sure what, and fluked it!!! hehe)

that did the trick and now pre-released is back on and also upgraded to latest kernel! 

Thank you!

The whole thing was a pain but for me it's solved all the way now!

---

### Post by manvvip on 2012-09-01
Woooooooooooooot!

Can mark as solved, cool...

---

### Post by bobjohnbowles on 2012-09-27
Thanks Manvvip this thread helped me out of a hole.

---

### Post by Calimo on 2012-09-28
Just got this error now. Solved, thanks!

---

### Post by sforces on 2012-09-29
Thanks, this just solved it for me too!

> **manvvip said:**
> Hmmm, changed status back to unsolved, grrrrrrrr, aaaaaagh.

Have you tried

Put pre-released back on then,
sudo dpkg --configure -a
sudo dpkg --force-depends -r libapt-pkg4.12:i386
sudo dpkg --force-depends -r libapt-inst1.4:i386
sudo dpkg -i libapt-pkg4.12_0.8.16~exp12ubuntu10.2_amd64.deb

Still same?
(maybe I just randomly typed the right thing, unfortunately not sure what, and fluked it!!! hehe)

---

