---
title: "Breezy Update Error"
date: 2005-11-01
forum: Installation &amp; Upgrades
---

### Post by Skanky on 2005-11-01
When trying to update to Breezy i get this 

[B]Error
E: /var/cache/apt/archives/libofx2_1%3a0.8.0-3ubuntu8_i386.deb: trying to overwrite `/usr/share/libofx/dtd/opensp.dcl', which is also in package libofx0c102[/B]

Does anyone know how I can fix this problem.I am a noob to ubuntu and this is kind of discouraging.

---

### Post by Manny C on 2005-11-01
Try this and let me know what happens:
```
 sudo apt-get clean 
```
And then run 
```
 sudo apt-get update 
```
and then
```
 sudo apt-get upgrade
```

---

### Post by Skanky on 2005-11-01
When i tried  sudo apt-get clean I get

E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory

 sudo apt-get update

This runs with no errors


 sudo apt-get upgrade

Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  gnucash: Depends: libofx2 but it is not installed
E: Unmet dependencies. Try using -f.






Help:(

---

### Post by Manny C on 2005-11-01
[quote=Skanky]When i tried  sudo apt-get clean I get

E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory

 sudo apt-get update

This runs with no errors


 sudo apt-get upgrade

Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  gnucash: Depends: libofx2 but it is not installed
E: Unmet dependencies. Try using -f.

Help:([/quote] 
What do you get when issuing the following command:
```
 ps aux | grep apt-get 
```

---

### Post by Skanky on 2005-11-01
Thanks for the help so far.
I get this below with     ps aux | grep apt-get


**davin    17956  0.0  0.1   3060   728 pts/1    D+   20:47   0:00 grep apt-get**

---

### Post by Manny C on 2005-11-01
Ok, try
```
 sudo apt-get --force-yes clean 
```

---

### Post by Skanky on 2005-11-01
sudo apt-get --force-yes clean

Nothing appears to happen.Just goes to next line in terminal.

---

### Post by Manny C on 2005-11-01
Ok. Run update and upgrade again.

---

### Post by Skanky on 2005-11-01
sudo apt-get update

Same response as before


sudo apt-get upgrade

Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  gnucash: Depends: libofx2 but it is not installed
E: Unmet dependencies. Try using -f.

---

### Post by Manny C on 2005-11-01
Do you have all the repositories enabled? You are using breezy? See for example this /etc/apt/sources.list:
```

deb [http://us.archive.ubuntu.com/ubuntu]("http://us.archive.ubuntu.com/ubuntu") breezy main restricted universe multiverse
deb [http://us.archive.ubuntu.com/ubuntu]("http://us.archive.ubuntu.com/ubuntu") breezy-updates main restricted universe multiverse
deb [http://us.archive.ubuntu.com/ubuntu]("http://us.archive.ubuntu.com/ubuntu") breezy-security main restricted universe multiverse

``` 
In fact could you post the contents of your sources.list file here please?

---

### Post by Skanky on 2005-11-01
Contents of sources.list

deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted
deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main universe multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main universe multiverse restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

---

### Post by Manny C on 2005-11-01
Ok...add universe and multiverse to the lines with breezy-updates in it so that you have:
```

 deb [http://archive.ubuntu.com/ubuntu]("http://archive.ubuntu.com/ubuntu") breezy-updates main restricted universe multiverse
 deb-src [http://archive.ubuntu.com/ubuntu]("http://archive.ubuntu.com/ubuntu") breezy-updates main restricted universe multiverse

``` Please comment out the line which refers to the Hoary CD (the second line).

libofx is actually contained in the universe repositories. The error you are getting indicates that apt-get is trying to find the update libofx that the updated gnucash is refering to, but can't find it. This is because you aren't letting apt-get see the breezy-updates.

---

### Post by Skanky on 2005-11-01
ok my sources.list looks like

deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted
##deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted universe multiverse

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main universe multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main universe multiverse restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

Should I run update and upgrade again?

---

### Post by Manny C on 2005-11-01
[quote=Skanky]ok my sources.list looks like

deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted
##deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu]("http://archive.ubuntu.com/ubuntu") breezy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu]("http://archive.ubuntu.com/ubuntu") breezy-updates main restricted
deb [http://archive.ubuntu.com/ubuntu]("http://archive.ubuntu.com/ubuntu") breezy-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu]("http://archive.ubuntu.com/ubuntu") breezy-updates main restricted universe multiverse

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu]("http://archive.ubuntu.com/ubuntu") breezy main universe multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu]("http://archive.ubuntu.com/ubuntu") breezy main universe multiverse restricted

deb [http://security.ubuntu.com/ubuntu]("http://security.ubuntu.com/ubuntu") breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu]("http://security.ubuntu.com/ubuntu") breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu]("http://security.ubuntu.com/ubuntu") breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu]("http://security.ubuntu.com/ubuntu") breezy-security universe

Should I run update and upgrade again?[/quote] 
Remove these two lines in your sources.list (they are duplicates):
```
 deb [http://archive.ubuntu.com/ubuntu]("http://archive.ubuntu.com/ubuntu") breezy-updates main restricted
 deb-src [http://archive.ubuntu.com/ubuntu]("http://archive.ubuntu.com/ubuntu") breezy-updates main restricted
```
And then run update and upgrade.

---

### Post by Skanky on 2005-11-01
Both update and upgrade give the same outputs as they did before.

Any more suggestions?This machine crashes every 15 minutes or so and I have to ctrl-alt-Backspace to get it working again.

---

### Post by jdong on 2005-11-01
sudo dpkg -i --force-install /var/cache/apt/archives/libofx2_1%3a0.8.0-3ubuntu8_i386.deb

and then:

sudo apt-get -f install

---

### Post by Skanky on 2005-11-01
sudo dpkg -i --force-install /var/cache/apt/archives/libofx2_1%3a0.8.0-3ubuntu8_i386.deb

gives

dpkg: unknown force/refuse option `install'

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --licence for copyright licence and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !

sudo apt-get -f install

gives

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavail able)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another proc ess using it?

---

### Post by Manny C on 2005-11-01
[quote=jdong]sudo dpkg -i --force-install /var/cache/apt/archives/libofx2_1%3a0.8.0-3ubuntu8_i386.deb

and then:

sudo apt-get -f install[/quote]

I believe 
```
 sudo dpkg -i --force-yes /var/cache/apt/archives/libofx2_1%3a0.8.0-3ubuntu8_i386.deb 
```
will work better.

---

### Post by Skanky on 2005-11-01
dpkg: unknown force/refuse option `yes'

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --licence for copyright licence and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !


I get the above with 

sudo dpkg -i --force-yes /var/cache/apt/archives/libofx2_1%3a0.8.0-3ubuntu8_i386.deb

---

### Post by jdong on 2005-11-01
sorry, brain-dead.... **--force-overwrite** was what I was trying to say :)

---

### Post by Manny C on 2005-11-01
Agreed...I oops my previous post also. Sorry.

---

### Post by Skanky on 2005-11-02
Thanks guys this did the trick but..........now the installation works properly except that my machine freezes every 15 minutes or so....this is driving me crazy....it doesn't totally freeze but it slows down so much that it becomes unusable and the cpu usage goes up to 100% when this happens.Any suggestions?

---

### Post by jdong on 2005-11-02
Alright, what kind of system (laptop/desktop, etc)?

Type "top" into the terminal -- during the "freezing" periods, what process is at the top of the list?

---

### Post by Skanky on 2005-11-02
It's a laptop a Dell I9300 so if it happens again I will be sure to try what you suggested.Will let you know how that works out.Thanks.

---

### Post by jdong on 2005-11-02
also try **sudo apt-get remove powernowd** to turn off processor frequency scaling -- Dells are infamous for lockups on frequency change.

---

### Post by Skanky on 2005-11-02
Well I removed the frequency scaling but I still occassionally get lockups.I can't tell exactly what causes the problem because once it begins to happen nothing responds properly and all movement becomes 'jerky'.I tried typing top in terminal but terminal would not even open when it begins to happen.Any other suggestions?

I'm beginning to think I was better off with Hoary!:(

---

### Post by Skanky on 2005-11-03
Well the computer had another 'jerky' session but I did manage to type  top  in terminal and I found  firefox-bin at the top of the list with the most cpu usage.

Is this the cause of my problems and if it is does anyone know how I can fix it?

---

### Post by jdong on 2005-11-03
what's the CPU speed?

---

### Post by Skanky on 2005-11-03
It's a 1.6GHz but when this occurs it runs sometimes at 800Mhz and sometimes at 1.6GHz.It varies.I tried removing the frequency scaling but it still occurred.So now I have frequency scaling installed again.

---

