---
title: "i can't play any mp3"
date: 2007-08-19
forum: Installation &amp; Upgrades
---

### Post by FaReSALandloS on 2007-08-19
hey all

i need some help i can't play any music or mp3 files

i don't know why
i'm a new user of ubuntu

i have 3 OS right now
XP ' Vista and ubuntu

the boot loader is working 
and i can see my windows files and drives

the only problem is that
(((
Totem could not play 'file:///home/fwhat ever'.

You do not have a decoder installed to handle this file. You might need to install the necessary plugins.

)))))
this is the message

i need help

---

### Post by yogo on 2007-08-19
[http://www4.mplayerhq.hu/homepage/design7/dload.html](http://www4.mplayerhq.hu/homepage/design7/dload.html)


You just need the proper codecs

---

### Post by PmDematagoda on 2007-08-19
Is your Ubuntu version directly from the Ubuntu website(Meaning not one like Ubuntu Ultimate which has the   necessary stuff preinstalled), if so, you may need to install the commonly used multimedia codecs through Automatix.

---

### Post by bapoumba on 2007-08-19
[https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")
Which version of ubuntu are you using?
With feisty, just install **ubuntu-restricted-extras**, you'll get nearly everything set up. For libdvdcss2, check the medibuntu repos as mentioned on the wiki page.

---

### Post by PmDematagoda on 2007-08-19
Aren't the restricted extras not recommended to be installed? In fact even i would like to know how to solve this except that my problem is that i can't play DVD movies in totem player properly since it directly goes to the movie instead of going through the menu.

---

### Post by bapoumba on 2007-08-19
ubuntu-restricted-extras is a metapackage (do not pay attention to the version number, I'm on my gutsy box ;)) meaning it's only there to provide all the extra codecs as dependencies. The only thing to be careful with is the laws from the country you live in that might prevent you from using them.
```
:~ $ aptitude show ubuntu-restricted-extras
Package: ubuntu-restricted-extras
New: yes
State: installed
Automatically installed: yes
Version: 10
Priority: optional
Section: multiverse/metapackages
Maintainer: Michael Vogt <michael.vogt@ubuntu.com>
Uncompressed Size: 32.8k
Recommends: gstreamer0.10-plugins-ugly, gstreamer0.10-plugins-ugly-multiverse,
            msttcorefonts, flashplugin-nonfree, sun-java6-plugin, unrar,
            gstreamer0.10-plugins-bad, gstreamer0.10-plugins-bad-multiverse,
            gstreamer0.10-ffmpeg, liblame0, libdvdread3
Description: Commonly used restricted packages
 This package depends on some commonly used packages in the Ubuntu multiverse
 repository. 
 
 Installing this package will pull in support for MP3 playback and decoding,
 support for various other audio formats (gstreamer plugins), Microsoft fonts,
 Java runtime environment, Flash plugin, LAME (to create compressed audio
 files), and DVD playback. 
 
 Please note that packages from multiverse are restricted by copyright or legal
 issues in some countries. See http://www.ubuntu.com/ubuntu/licensing for more
 information.

```

For the dvd, the issue might be with libdcss2, provided by the medibuntu repositories. Same thing, it can be illegal to use in some countries. So read the legal note and get informed about the laws from your country.

---

### Post by PmDematagoda on 2007-08-19
I tried installing the non-free codecs through automatix2  but as the attachment shows it doesn't install completely. What can i do about this?

---

### Post by bapoumba on 2007-08-19
I guess your attachment did not go through.

Do you mind the command line?
If not, open a terminal (Accessories > Terminal) and paste the output to:
```
cat /etc/apt/sources.list
```

---

### Post by PmDematagoda on 2007-08-19
Could you please elaborate?

---

### Post by bapoumba on 2007-08-19
Well, without an error message, it's quite hard to guess, as there is no attachment to your post ;)

So I just assumed you were missing some repositories, preventing you from installing all the codecs. The repos are stored in the sources.list file. Without having a look at it, no one can help you.

---

### Post by PmDematagoda on 2007-08-19
I'm sorry it's just that im very new to linux, im so used to windows and it's softening ways, anyway here is the output i got:-

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-updates universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-security main restricted universe multiverse
#AUTOMATIX REPOS END

This is what you wanted right?

---

### Post by bapoumba on 2007-08-19
> **PmDematagoda said:**
> I'm sorry it's just that im very new to linux, im so used to windows and it's softening ways, anyway here is the output i got:-This is what you wanted right?
No problem, and yes, that's what we needed.

> **PmDematagoda said:**
> 
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-updates universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-security main restricted universe multiverse
#AUTOMATIX REPOS END


You are missing a line for all the basic repositories. You will need to edit the file. I'm used to using nano, a small text editor that works from the command line.

Save it first:
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_bak
```
(enter your password when prompted to, it will not appear on the screen when you type it)

Edit the file:
```
sudo nano /etc/apt/sources.list
```
after the first line, add this one:
```
deb http://archive.ubuntu.com/ubuntu/ feisty main restricted universe multiverse
```
Save the file with CTRL-O (same name, hit enter)
Exit nano with CTRL-X
reload the repo list:
```
sudo apt-get update
```

You should now be able to install the codecs. I'm not sure how it works with automatix, because I've never used it. Just do again what you did previously to get the codecs.

Alternatively, you can install the meta package:
```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by PmDematagoda on 2007-08-19
When i say this it's going to be weird and stupid but here goes. When i tried again with automatix it gave the same problem(Am unable to copy the displayed text as option is not available), but when it tried it the other way using the terminal it says that it's already installed, the fact being that i installed it following your last reply. The thing is it was installed before i made the changes to the souces list file. So has the problem been solved?(Once again i admit that this problem is really weird.)

---

### Post by bapoumba on 2007-08-19
Can you play mp3 files ?

---

### Post by PmDematagoda on 2007-08-19
Yup.

---

### Post by bapoumba on 2007-08-19
All good then ;)

---

### Post by PmDematagoda on 2007-08-19
Thanks a lot for your help, really appreciate it, and please forgive me if caused you a problem with my petty questions.

---

### Post by PmDematagoda on 2007-08-19
By the way (Really sorry about this) how is xubuntu when compared to ubuntu and kubuntu?

---

### Post by bapoumba on 2007-08-19
> **PmDematagoda said:**
> Thanks a lot for your help, really appreciate it, and please forgive me if caused you a problem with my petty questions.
No problem at all, glad to see you got it to work!

> **PmDematagoda said:**
> By the way (Really sorry about this) how is xubuntu when compared to ubuntu and kubuntu?
xubuntu uses the Xfce desktop, when ubuntu used GNOME and kubuntu KDE. I have low specs computers (older ones). Xfce is lighter than GNOME and KDE, thus works better on older hardware.
It's all a matter of choices, really, if hardware is not an issue for you.

[http://psychocats.net/ubuntu/kdegnome]("http://psychocats.net/ubuntu/kdegnome")
here is a comparison side by side between GNOME and KDE (I'm giving you this link, there are other interesting pages to read ;))
[http://www.xubuntu.org/]("http://www.xubuntu.org/")
and there the xubuntu site where there are screenshots.

Basically, you install xubuntu-desktop, and next login, you will be able to start your session with Xfce (under the session option). So you can try it for yourself!

---

### Post by PmDematagoda on 2007-08-19
Thanks a lot, i owe you one!! Anything you want from me?:popcorn:

---

### Post by bapoumba on 2007-08-19
No problem! Just be happy!
Come back and ask anything, if you need help again. One day, you'll pass along to others what you know. That's how a community works best.

---

### Post by PmDematagoda on 2007-08-19
Got it thanks for the advice. Hop 2 meet again.:)

---

