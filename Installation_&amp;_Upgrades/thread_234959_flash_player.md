---
title: "flash player"
date: 2006-08-12
forum: Installation &amp; Upgrades
---

### Post by MacDonagh on 2006-08-12
I am in difficulty over Limewire. It won't let me download it because

---

### Post by Perfect Storm on 2006-08-12
??? :confused:
Try rephrase your question/problem.

---

### Post by MacDonagh on 2006-08-12
lol sorry, accidently pressed the click button. Anyway, flash player isn't working on Linux, and neither is Limewire. Can you help me out? I'm such a noob at this malarky.

---

### Post by Perfect Storm on 2006-08-12
Okay, first about Limewire. Did you have sun Java 1.5 installed?


Flash-player how did you try ti install it?

---

### Post by MacDonagh on 2006-08-12
By clicking on an adobe flash player thingy. It shows an error message and that.
I'm not sure if I've downloaded Sun java. Can you help me out?

---

### Post by bukwirm on 2006-08-12
What is the output of "sudo update-alternatives --list java"?

PS. Sun Java is not installed by default, but it is availible in the repositories.

---

### Post by MacDonagh on 2006-08-12
Ach, I tried that, but the terminal won't let me put in my password.

---

### Post by Perfect Storm on 2006-08-12
Aye. Just a reminder on Linux you do things way diffrently than Windows, so if you are up to learn something here we go:


Download flashplayer from here: [http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&promoid=BIOW](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&promoid=BIOW)
and save it to your Desktop. (remember that linux is case sensitive).
OPen the terminal (Applications tab ---> Accessories ---> terminal)
Type in or copy'n'paste;
```
cd Desktop
tar -zxf install_flash_player_7_linux.tar.gz
cd install_flash_player_7_linux
sudo sh flashplayer-installer

```
When it ask for path write:
```
/usr/lib/mozilla-firefox
```
Now you need to install the right fonts for it:
```
sudo apt-get install gsfonts-x11
```

To check if it works type
```
about:plugins
```
in the browser box

There's another way if you want to check it out: [http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper)

---

### Post by Perfect Storm on 2006-08-12
> **MacDonagh said:**
> Ach, I tried that, but the terminal won't let me put in my password.

You can't see while typing the password (a safty device).

---

### Post by Perfect Storm on 2006-08-12
If you wanna manually install Java (and the latest):
It requires that you have univer/multiverse enable in your sourcelist ( [http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories) ) but by enable universe/multiverse  you can find sun java there, just make a search with Synaptic package manager. Anyway if you want the newest:

Download Java Runtime Environment (JRE) 5.0 Update 7: [http://java.sun.com/javase/downloads/index.jsp](http://java.sun.com/javase/downloads/index.jsp) pick **Linux self-extracting file**. Download it to your **Desktop**.

```
cd Desktop
sudo apt-get install build-essential
sudo apt-get install fakeroot java-package java-common
fakeroot make-jpkg jre-1_5_0_07-linux-i586.bin
sudo dpkg -i sun-j2re1.5_1.5.0+update07_i386.deb
sudo update-alternatives --config java

```
When asking for which version you want to choose pick;
```
  3        /usr/lib/j2sdk1.5-sun/bin/java
```

Testing;
```
java -version
```


Making a Launcher for Java Control Center;
```
sudo gedit /usr/share/applications/java.desktop
```

fill in;

[b]
[Desktop Entry]
Name=Java Control Center
Comment=Java Options & Configuration.
Exec=sh /usr/lib/j2re1.5-sun/bin/ControlPanel
Icon=
Terminal=false
Type=Application
Categories=Application;System;
[/b]

Save and exit.
You can find it now under Applications tab ---> System Tools.

---

### Post by MacDonagh on 2006-08-12
Hey. What does this mean?

Package gsfonts-x11 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

This is for the Java script...

---

### Post by Perfect Storm on 2006-08-12
It should be there if you set up your sourcelist correctly. Can you find it in synaptic package manager?
How's your sourcelist looks like?
```
cat /etc/apt/sources.list

```

---

### Post by MacDonagh on 2006-08-12
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
admin@user-desktop:~/Desktop/install_flash_player_7_linux$

This is what the code looks like.

God, I never imagined Linux would be this complicated. I have to confess that I suck at programming. It melts my brain.

---

### Post by MacDonagh on 2006-08-12
I did find gsfonts, but not gsfonts x11

---

### Post by Perfect Storm on 2006-08-12
Okay. I can see you havn't enable thte diffrent source list in your repo.
Open up your source list;
```
sudo nano /etc/apt/sources.list
```

Now remove the # infront of every source.
eg.
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe

so it says

deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe

do it with all of them.
so it looks like:
```

deb-src http://gb.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src http://gb.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe
```

Save and exit it (<ctrl> +<o> and <ctrl> + <x>)

Back to the terminal;
```
sudo apt-get update
```

Then try again.

---

### Post by MacDonagh on 2006-08-12
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

what does this mean?

---

### Post by Perfect Storm on 2006-08-12
You have properly Synaptic package manager open. You have to close it to use apt-get in the terminal.

---

### Post by MacDonagh on 2006-08-12
Jesus Christ, you're really good at this aren't ya?

---

### Post by Perfect Storm on 2006-08-12
I have my moments ;)

---

### Post by MacDonagh on 2006-08-12
I have to apologise to you pal. It's just...I knew that Linux was a better operating system then Windows, but I never imagined it'd be so...hard to install stuff.

---

### Post by MacDonagh on 2006-08-12
Oh, this is good. Reading package lists...done
God, I hope that's good news.

---

### Post by Perfect Storm on 2006-08-12
Well the way I show you here is the hard way.

Now you have enable universe and multiverse in your source list. You can simple find Java in synaptic package manager (I also think flash is there), just use the search button. But the way I show you , you can easely install the latest version.


It's not hard when you tried it in a couple of months. It's just commands instead click, click, agree, next, next , agree gui.
With commands you get control of your computer and not the other way around. If you are willing to learn :) Have in mind I have been a newbie once :KS

---

### Post by buddhacub1120 on 2007-08-14
> **Artificial Intelligence said:**
> Aye. Just a reminder on Linux you do things way diffrently than Windows, so if you are up to learn something here we go:


Download flashplayer from here: [http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&promoid=BIOW](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&promoid=BIOW)
and save it to your Desktop. (remember that linux is case sensitive).
OPen the terminal (Applications tab ---> Accessories ---> terminal)
Type in or copy'n'paste;
```
cd Desktop
tar -zxf install_flash_player_7_linux.tar.gz
cd install_flash_player_7_linux
sudo sh flashplayer-installer

```
When it ask for path write:
```
/usr/lib/mozilla-firefox
```
Now you need to install the right fonts for it:
```
sudo apt-get install gsfonts-x11
```

To check if it works type
```
about:plugins
```
in the browser box

There's another way if you want to check it out: 
[http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper)








I tried this and this was my result.... ```
ferris@ferris-desktop:~$ ^Vcd Desktop
bash: cd: command not found
ferris@ferris-desktop:~$ tar -zxf install_flash_player_7_linux.tar.gz
tar: install_flash_player_7_linux.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
ferris@ferris-desktop:~$ cd install_flash_player_7_linux
bash: cd: install_flash_player_7_linux: No such file or directory
ferris@ferris-desktop:~$ sudo sh flashplayer-installer
sh: Can't open flashplayer-installer
ferris@ferris-desktop:~$ 
```




any help???

---

### Post by Perfect Storm on 2007-08-14
Check your spelling....

---

