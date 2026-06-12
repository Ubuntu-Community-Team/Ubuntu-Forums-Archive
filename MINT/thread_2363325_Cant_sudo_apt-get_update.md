---
title: "Cant sudo apt-get update"
date: 2017-06-08
forum: MINT
---

### Post by devdlp on 2017-06-08
When i try to update from the terminal it gives me this error. Malformed entry 3 in list file /etc/apt/sources.list.d/additional-repositories.list (Suite)
E: The list of sources could not be read.
What can i do to solve this?

---

### Post by howefield on 2017-06-08
Can you post the output of the following two terminal commands

```
egrep -v '^#|^ *$' /etc/apt/sources.list /etc/apt/sources.list.d/*
```
and
```
cat /etc/apt/sources.list.d/additional-repositories.list*
```

---

### Post by devdlp on 2017-06-09
```
deven@deven-X501A1 ~ $ egrep -v '^#|^ *$' /etc/apt/sources.list /etc/apt/sources.list.d/*
/etc/apt/sources.list:deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) trusty contrib
/etc/apt/sources.list.d/additional-repositories.list:deb [https://dl.winehq.org/wine-builds/ubuntu/](https://dl.winehq.org/wine-builds/ubuntu/) xenial main
/etc/apt/sources.list.d/additional-repositories.list:deb [https://dl.winehq.org/wine-builds/ubuntu/](https://dl.winehq.org/wine-builds/ubuntu/) xenial main
/etc/apt/sources.list.d/additional-repositories.list:deb [https://dl.winehq.org/wine-builds/ubuntu/](https://dl.winehq.org/wine-builds/ubuntu/)
/etc/apt/sources.list.d/additional-repositories.list:sudo apt-add-repository deb
/etc/apt/sources.list.d/danielrichter2007-grub-customizer-xenial.list:deb [http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu](http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu) xenial main
/etc/apt/sources.list.d/danielrichter2007-grub-customizer-xenial.list:deb-src [http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu](http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu) xenial main
/etc/apt/sources.list.d/google-chrome.list:deb [arch=amd64] [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main
/etc/apt/sources.list.d/kxstudio-debian.gcc5.list:deb [http://ppa.launchpad.net/kxstudio-debian/gcc5/ubuntu](http://ppa.launchpad.net/kxstudio-debian/gcc5/ubuntu) wily main
/etc/apt/sources.list.d/kxstudio-debian.gcc5.list:deb [http://ppa.launchpad.net/kxstudio-debian/gcc5/ubuntu](http://ppa.launchpad.net/kxstudio-debian/gcc5/ubuntu) xenial main
/etc/apt/sources.list.d/kxstudio-debian.gcc5.list:deb [http://ppa.launchpad.net/kxstudio-debian/gcc5-deps/ubuntu](http://ppa.launchpad.net/kxstudio-debian/gcc5-deps/ubuntu) xenial main
/etc/apt/sources.list.d/kxstudio-debian.list:deb [arch=amd64,i386] [http://ppa.launchpad.net/kxstudio-debian/libs/ubuntu](http://ppa.launchpad.net/kxstudio-debian/libs/ubuntu) lucid main
/etc/apt/sources.list.d/kxstudio-debian.list:deb [arch=amd64,i386] [http://ppa.launchpad.net/kxstudio-debian/music/ubuntu](http://ppa.launchpad.net/kxstudio-debian/music/ubuntu) lucid main
/etc/apt/sources.list.d/kxstudio-debian.list:deb [arch=amd64,i386] [http://ppa.launchpad.net/kxstudio-debian/plugins/ubuntu](http://ppa.launchpad.net/kxstudio-debian/plugins/ubuntu) lucid main
/etc/apt/sources.list.d/kxstudio-debian.list:deb [arch=amd64,i386] [http://ppa.launchpad.net/kxstudio-debian/apps/ubuntu](http://ppa.launchpad.net/kxstudio-debian/apps/ubuntu) lucid main
/etc/apt/sources.list.d/kxstudio-debian.list:deb [arch=amd64,i386] [http://ppa.launchpad.net/kxstudio-debian/kxstudio/ubuntu](http://ppa.launchpad.net/kxstudio-debian/kxstudio/ubuntu) lucid main
/etc/apt/sources.list.d/kxstudio-debian.new.list:deb [http://ppa.launchpad.net/kxstudio-debian/libs/ubuntu](http://ppa.launchpad.net/kxstudio-debian/libs/ubuntu) trusty main
/etc/apt/sources.list.d/kxstudio-debian.new.list:deb [http://ppa.launchpad.net/kxstudio-debian/music/ubuntu](http://ppa.launchpad.net/kxstudio-debian/music/ubuntu) trusty main
/etc/apt/sources.list.d/kxstudio-debian.new.list:deb [http://ppa.launchpad.net/kxstudio-debian/plugins/ubuntu](http://ppa.launchpad.net/kxstudio-debian/plugins/ubuntu) trusty main
/etc/apt/sources.list.d/kxstudio-debian.new.list:deb [http://ppa.launchpad.net/kxstudio-debian/apps/ubuntu](http://ppa.launchpad.net/kxstudio-debian/apps/ubuntu) trusty main
/etc/apt/sources.list.d/kxstudio-debian.new.list:deb [http://ppa.launchpad.net/kxstudio-debian/kxstudio/ubuntu](http://ppa.launchpad.net/kxstudio-debian/kxstudio/ubuntu) trusty main
/etc/apt/sources.list.d/kxstudio-free.gcc5.list:deb [arch=amd64,i386] [http://kxstudio.linuxaudio.org/repo/](http://kxstudio.linuxaudio.org/repo/) gcc5 free
/etc/apt/sources.list.d/kxstudio-free.list:deb [arch=amd64,i386] [http://kxstudio.linuxaudio.org/repo/](http://kxstudio.linuxaudio.org/repo/) stable free
/etc/apt/sources.list.d/kxstudio-non-free.gcc5.list:deb [arch=amd64,i386] [http://kxstudio.linuxaudio.org/repo/](http://kxstudio.linuxaudio.org/repo/) gcc5 non-free
/etc/apt/sources.list.d/kxstudio-non-free.list:deb [arch=amd64,i386] [http://kxstudio.linuxaudio.org/repo/](http://kxstudio.linuxaudio.org/repo/) stable non-free
/etc/apt/sources.list.d/official-package-repositories.list:deb [http://packages.linuxmint.com](http://packages.linuxmint.com) serena main upstream import backport #id:linuxmint_main
/etc/apt/sources.list.d/official-package-repositories.list:deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial main restricted universe multiverse
/etc/apt/sources.list.d/official-package-repositories.list:deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates main restricted universe multiverse
/etc/apt/sources.list.d/official-package-repositories.list:deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-backports main restricted universe multiverse
/etc/apt/sources.list.d/official-package-repositories.list:deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) xenial-security main restricted universe multiverse
/etc/apt/sources.list.d/official-package-repositories.list:deb [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) xenial partner
/etc/apt/sources.list.d/skype-stable.list:deb [arch=amd64] [https://repo.skype.com/deb](https://repo.skype.com/deb) stable main
/etc/apt/sources.list.d/spotify.list:deb [http://repository.spotify.com](http://repository.spotify.com) stable non-free
deven@deven-X501A1 ~ $ cat /etc/apt/sources.list.d/additional-repositories.list*deb [https://dl.winehq.org/wine-builds/ubuntu/](https://dl.winehq.org/wine-builds/ubuntu/) xenial main
deb [https://dl.winehq.org/wine-builds/ubuntu/](https://dl.winehq.org/wine-builds/ubuntu/) xenial main
deb [https://dl.winehq.org/wine-builds/ubuntu/](https://dl.winehq.org/wine-builds/ubuntu/)


sudo apt-add-repository deb
deven@deven-X501A1 ~ $
```

---

### Post by RobGoss on 2017-06-09
Please use the code tags when posting output results, it's much easier for members to read without scrolling

---

### Post by devdlp on 2017-06-09
tags??

---

### Post by RobGoss on 2017-06-09
> **devdlp said:**
> tags??


Here you go,
[https://ubuntuforums.org/misc.php?do=bbcode](https://ubuntuforums.org/misc.php?do=bbcode)

---

### Post by devdlp on 2017-06-09
i cant add wine to my pc because of this issue and i really need it

and i dont get howto use the tags ill figure that out later

im sorry for posting so much but i cant open the software manager aswell

i wont have good internet in the next hour so could someone help me plz

---

### Post by #&amp;thj^% on 2017-06-09
> **devdlp said:**
> ```
deven@deven-X501A1 ~ $ egrep -v '^#|^ *$' /etc/apt/sources.list /etc/apt/sources.list.d/*
/etc/apt/sources.list:deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) trusty contrib
/etc/apt/sources.list.d/additional-repositories.list:deb [https://dl.winehq.org/wine-builds/ubuntu/](https://dl.winehq.org/wine-builds/ubuntu/) xenial main
/etc/apt/sources.list.d/additional-repositories.list:deb [https://dl.winehq.org/wine-builds/ubuntu/](https://dl.winehq.org/wine-builds/ubuntu/) xenial main
/etc/apt/sources.list.d/additional-repositories.list:deb [https://dl.winehq.org/wine-builds/ubuntu/](https://dl.winehq.org/wine-builds/ubuntu/)
/etc/apt/sources.list.d/additional-repositories.list:sudo apt-add-repository deb
/etc/apt/sources.list.d/danielrichter2007-grub-customizer-xenial.list:deb [http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu](http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu) xenial main
/etc/apt/sources.list.d/danielrichter2007-grub-customizer-xenial.list:deb-src [http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu](http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu) xenial main
/etc/apt/sources.list.d/google-chrome.list:deb [arch=amd64] [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main
/etc/apt/sources.list.d/kxstudio-debian.gcc5.list:deb [http://ppa.launchpad.net/kxstudio-debian/gcc5/ubuntu](http://ppa.launchpad.net/kxstudio-debian/gcc5/ubuntu) wily main
/etc/apt/sources.list.d/kxstudio-debian.gcc5.list:deb [http://ppa.launchpad.net/kxstudio-debian/gcc5/ubuntu](http://ppa.launchpad.net/kxstudio-debian/gcc5/ubuntu) xenial main
/etc/apt/sources.list.d/kxstudio-debian.gcc5.list:deb [http://ppa.launchpad.net/kxstudio-debian/gcc5-deps/ubuntu](http://ppa.launchpad.net/kxstudio-debian/gcc5-deps/ubuntu) xenial main
/etc/apt/sources.list.d/kxstudio-debian.list:deb [arch=amd64,i386] [http://ppa.launchpad.net/kxstudio-debian/libs/ubuntu](http://ppa.launchpad.net/kxstudio-debian/libs/ubuntu) lucid main
/etc/apt/sources.list.d/kxstudio-debian.list:deb [arch=amd64,i386] [http://ppa.launchpad.net/kxstudio-debian/music/ubuntu](http://ppa.launchpad.net/kxstudio-debian/music/ubuntu) lucid main
/etc/apt/sources.list.d/kxstudio-debian.list:deb [arch=amd64,i386] [http://ppa.launchpad.net/kxstudio-debian/plugins/ubuntu](http://ppa.launchpad.net/kxstudio-debian/plugins/ubuntu) lucid main
/etc/apt/sources.list.d/kxstudio-debian.list:deb [arch=amd64,i386] [http://ppa.launchpad.net/kxstudio-debian/apps/ubuntu](http://ppa.launchpad.net/kxstudio-debian/apps/ubuntu) lucid main
/etc/apt/sources.list.d/kxstudio-debian.list:deb [arch=amd64,i386] [http://ppa.launchpad.net/kxstudio-debian/kxstudio/ubuntu](http://ppa.launchpad.net/kxstudio-debian/kxstudio/ubuntu) lucid main
/etc/apt/sources.list.d/kxstudio-debian.new.list:deb [http://ppa.launchpad.net/kxstudio-debian/libs/ubuntu](http://ppa.launchpad.net/kxstudio-debian/libs/ubuntu) trusty main
/etc/apt/sources.list.d/kxstudio-debian.new.list:deb [http://ppa.launchpad.net/kxstudio-debian/music/ubuntu](http://ppa.launchpad.net/kxstudio-debian/music/ubuntu) trusty main
/etc/apt/sources.list.d/kxstudio-debian.new.list:deb [http://ppa.launchpad.net/kxstudio-debian/plugins/ubuntu](http://ppa.launchpad.net/kxstudio-debian/plugins/ubuntu) trusty main
/etc/apt/sources.list.d/kxstudio-debian.new.list:deb [http://ppa.launchpad.net/kxstudio-debian/apps/ubuntu](http://ppa.launchpad.net/kxstudio-debian/apps/ubuntu) trusty main
/etc/apt/sources.list.d/kxstudio-debian.new.list:deb [http://ppa.launchpad.net/kxstudio-debian/kxstudio/ubuntu](http://ppa.launchpad.net/kxstudio-debian/kxstudio/ubuntu) trusty main
/etc/apt/sources.list.d/kxstudio-free.gcc5.list:deb [arch=amd64,i386] [http://kxstudio.linuxaudio.org/repo/](http://kxstudio.linuxaudio.org/repo/) gcc5 free
/etc/apt/sources.list.d/kxstudio-free.list:deb [arch=amd64,i386] [http://kxstudio.linuxaudio.org/repo/](http://kxstudio.linuxaudio.org/repo/) stable free
/etc/apt/sources.list.d/kxstudio-non-free.gcc5.list:deb [arch=amd64,i386] [http://kxstudio.linuxaudio.org/repo/](http://kxstudio.linuxaudio.org/repo/) gcc5 non-free
/etc/apt/sources.list.d/kxstudio-non-free.list:deb [arch=amd64,i386] [http://kxstudio.linuxaudio.org/repo/](http://kxstudio.linuxaudio.org/repo/) stable non-free
/etc/apt/sources.list.d/official-package-repositories.list:deb [http://packages.linuxmint.com](http://packages.linuxmint.com) serena main upstream import backport #id:linuxmint_main
/etc/apt/sources.list.d/official-package-repositories.list:deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial main restricted universe multiverse
/etc/apt/sources.list.d/official-package-repositories.list:deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates main restricted universe multiverse
/etc/apt/sources.list.d/official-package-repositories.list:deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-backports main restricted universe multiverse
/etc/apt/sources.list.d/official-package-repositories.list:deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) xenial-security main restricted universe multiverse
/etc/apt/sources.list.d/official-package-repositories.list:deb [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) xenial partner
/etc/apt/sources.list.d/skype-stable.list:deb [arch=amd64] [https://repo.skype.com/deb](https://repo.skype.com/deb) stable main
/etc/apt/sources.list.d/spotify.list:deb [http://repository.spotify.com](http://repository.spotify.com) stable non-free
deven@deven-X501A1 ~ $ cat /etc/apt/sources.list.d/additional-repositories.list*deb [https://dl.winehq.org/wine-builds/ubuntu/](https://dl.winehq.org/wine-builds/ubuntu/) xenial main
deb [https://dl.winehq.org/wine-builds/ubuntu/](https://dl.winehq.org/wine-builds/ubuntu/) xenial main
deb [https://dl.winehq.org/wine-builds/ubuntu/](https://dl.winehq.org/wine-builds/ubuntu/)


sudo apt-add-repository deb
deven@deven-X501A1 ~ $
```

You have some PPA's that have not been corrected to the proper versions IE:
```
deb http://ppa.launchpad.net/kxstudio-debian/gcc5/ubuntu wily main
```
Where it should read:
```
deb http://ppa.launchpad.net/kxstudio-debian/gcc5/ubuntu xenial main 
```
And All of these should be removed:
```
deb [arch=amd64,i386] http://ppa.launchpad.net/kxstudio-debian/libs/ubuntu lucid main
deb [arch=amd64,i386] http://ppa.launchpad.net/kxstudio-debian/music/ubuntu lucid main
deb [arch=amd64,i386] http://ppa.launchpad.net/kxstudio-debian/plugins/ubuntu lucid main
deb [arch=amd64,i386] http://ppa.launchpad.net/kxstudio-debian/apps/ubuntu lucid main
deb [arch=amd64,i386] http://ppa.launchpad.net/kxstudio-debian/apps/ubuntu lucid main
deb [arch=amd64,i386] http://ppa.launchpad.net/kxstudio-de...xstudio/ubuntu lucid main
deb http://ppa.launchpad.net/kxstudio-debian/libs/ubuntu trusty main
deb http://ppa.launchpad.net/kxstudio-debian/music/ubuntu trusty main
deb http://ppa.launchpad.net/kxstudio-debian/plugins/ubuntu trusty main
deb http://ppa.launchpad.net/kxstudio-debian/apps/ubuntu trusty main
deb http://ppa.launchpad.net/kxstudio-de...xstudio/ubuntu trusty main
deb [arch=amd64,i386] http://kxstudio.linuxaudio.org/repo/ gcc5 free
deb [arch=amd64,i386] http://kxstudio.linuxaudio.org/repo/ stable free
```

And this is from a completely different OS
```
deb http://packages.linuxmint.com serena main upstream import backport #id:linuxmint_main
```
This is a big mess you have going on here _**I'm very surprised you have a working system at all.**_
And what is this from your last post??
```
sudo apt-add-repository deb 

```

---

### Post by devdlp on 2017-06-09
sudo apt-add-repository deb thatsprobably from me trying to install wine back on

is there a code i can enter to make go back to normal?

---

### Post by RobGoss on 2017-06-09
> **devdlp said:**
> is there a code i can enter to make go back to normal?

I doubt that, if this is a new installation?

---

### Post by #&amp;thj^% on 2017-06-09
> **devdlp said:**
> is there a code i can enter to make go back to normal?

Just remove those PPA's I  showed then run:
```
sudo apt update
```
Do you have synaptic package manager installed?

---

### Post by devdlp on 2017-06-09
can you post the command to remove them plz

i hao ushe commands cuz i cant use the package manager right now its stopping me from using half my applications.

---

### Post by #&amp;thj^% on 2017-06-09
Be very careful here:

```
sudo -i software-properties-gtk

```
A window will now open, you need to look at the top for **"Other Software"**
now you can remove those PPA's I have already pointed out.
And close that window after editing it.
And try to run:
```
sudo apt update
```

---

### Post by RobGoss on 2017-06-09
Please follow the instructions giving by 1fallen, you much remove the PPA's listed. Go to Software & update click on Other software, them remove the PPA'so as advised

---

### Post by devdlp on 2017-06-09
when i click remove nothing happens should i just disable it

---

### Post by #&amp;thj^% on 2017-06-09
Just make sure they do** not **have a check ticked in the box.
See Screen-shot
Mine show Ticked...you do not want yours with a check in the box.

---

### Post by devdlp on 2017-06-09
i was able to remove them besides the one in the different os. but when i do apt-get update it shows:deven@deven-X501A1 ~ $ sudo apt-get update
[sudo] password for deven: 
E: Malformed entry 3 in list file /etc/apt/sources.list.d/additional-repositories.list (Suite)
E: The list of sources could not be read.
deven@deven-X501A1 ~ $

---

### Post by #&amp;thj^% on 2017-06-09
I was afraid of that...due to a Mint entry you had. 
Well lets see what we have now:
Run in the terminal:
```
gedit /etc/apt/sources.list
```
Paste back here so we can see....Using Code tags Please!!! ;) **[How to use [/Code Tags]]("https://ubuntuforums.org/showthread.php?p=12776168#post12776168")**

---

### Post by devdlp on 2017-06-09
deven@deven-X501A1 ~ $ gedit /etc/apt/sources.list
The program 'gedit' is currently not installed. You can install it by typing:
sudo apt install gedit
deven@deven-X501A1 ~ $ sudo apt-get install gedit
[sudo] password for deven: 
E: Malformed entry 3 in list file /etc/apt/sources.list.d/additional-repositories.list (Suite)
E: The list of sources could not be read.
E: Malformed entry 3 in list file /etc/apt/sources.list.d/additional-repositories.list (Suite)
E: The list of sources could not be read.
deven@deven-X501A1 ~ $

---

### Post by #&amp;thj^% on 2017-06-09
What Desktop are you using? XFCE, Mate KDE LXDE Openbox
I'm going to have to leave you here real soon, I have some Appointments to tend to.

---

### Post by devdlp on 2017-06-09
mate

---

### Post by #&amp;thj^% on 2017-06-09
Ok then:
```
pluma /etc/apt/sources.list
```

---

### Post by devdlp on 2017-06-09
mate

pluma /etc/apt/sources.list
The program 'pluma' is currently not installed. You can install it by typing:
```
sudo apt install pluma
deven@deven-X501A1 ~ $ sudo apt-get install pluma
[sudo] password for deven: 
E: Malformed entry 3 in list file /etc/apt/sources.list.d/additional-repositories.list (Suite)
E: The list of sources could not be read.
E: Malformed entry 3 in list file /etc/apt/sources.list.d/additional-repositories.list (Suite)
E: The list of sources could not be read.
```

---

### Post by deadflowr on 2017-06-09
It seems to be getting out there here.
Plese post only the output response from the cat command again:
```
cat /etc/apt/sources.list.d/additional-repositories.list 
```
The original posting of it is mucked looking so it's hard to tell, but from a quick look it seems the last line is malformed as it does not have the proper form.
(It only shows the url and not the distro nor the component.)

It seems to be like this:
```
deb https://dl.winehq.org/wine-builds/ubuntu/ xenial main <= proper line
deb https://dl.winehq.org/wine-builds/ubuntu/ xenial main <= proper line
deb https://dl.winehq.org/wine-builds/ubuntu/ <= not proper line
```

---

### Post by #&amp;thj^% on 2017-06-09
Ubuntu Mate comes with Pluma as the default text editor.
You have me on the ropes here.:confused:
What do you use for a text editor then?
Also show me the output from this:
```
echo $DESKTOP_SESSION
```

---

### Post by devdlp on 2017-06-09
deven@deven-X501A1 ~ $ cat /etc/apt/sources.list.d/additional-repositories.list deb [https://dl.winehq.org/wine-builds/ubuntu/](https://dl.winehq.org/wine-builds/ubuntu/) xenial main deb [https://dl.winehq.org/wine-builds/ubuntu/](https://dl.winehq.org/wine-builds/ubuntu/) xenial main deb [https://dl.winehq.org/wine-builds/ubuntu/](https://dl.winehq.org/wine-builds/ubuntu/)

deven@deven-X501A1 ~ $ echo $DESKTOP_SESSION
mate

---

### Post by deadflowr on 2017-06-09
> **devdlp said:**
> deven@deven-X501A1 ~ $ cat /etc/apt/sources.list.d/additional-repositories.list deb [https://dl.winehq.org/wine-builds/ubuntu/](https://dl.winehq.org/wine-builds/ubuntu/) xenial main deb [https://dl.winehq.org/wine-builds/ubuntu/](https://dl.winehq.org/wine-builds/ubuntu/) xenial main deb [https://dl.winehq.org/wine-builds/ubuntu/](https://dl.winehq.org/wine-builds/ubuntu/)

Run 
```
sudo nano /etc/apt/sources.list.d/additional-repositories.list 
```
and delete or comment out the last two lines, so it either reads as one line only, or reads like so:

```
deb https://dl.winehq.org/wine-builds/ubuntu/ xenial main 
#deb https://dl.winehq.org/wine-builds/ubuntu/ xenial main 
#deb https://dl.winehq.org/wine-builds/ubuntu/
```
(adding the # symbol will comment out the line, making it unreadable by the system)
when done press ctrl + x to save and exit; 

then re-run
```
sudo apt-get update
```

---

### Post by devdlp on 2017-06-09
deven@deven-X501A1 ~ $ echo $DESKTOP_SESSION mate

i did ctrl x but it wont exit

---

### Post by deadflowr on 2017-06-09
> **devdlp said:**
> i did ctrl x but it wont exit

Hit Y for yes and then hit enter.
The Y confirms the changes and the enter confirms where to put the new file.

---

### Post by devdlp on 2017-06-09
/home/deven/Desktop/Screenshot at 2017-06-09 16-46-40.png

[IMG]/home/deven/Desktop/Screenshot at 2017-06-09 16-46-40.png[/IMG]

i saved it but i cant exit it im sorry for being a noob guys

so we got somewhere theres a different problem now.
deven@deven-X501A1 ~ $ sudo apt-get update
N: Ignoring file 'additional-repositories.list.save.1' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
E: Type 'sudo' is not known on line 6 in source list /etc/apt/sources.list.d/additional-repositories.list
E: The list of sources could not be read.
deven@deven-X501A1 ~ $

---

### Post by deadflowr on 2017-06-09
Click on Go Advanced (or Reply to Thread) on then click on the paperclip icon to access the attachment function to post images, please.

---

### Post by devdlp on 2017-06-09
ok thank you

any idea how to fix this last problem?

is it in windows maybe because i mounted windows on linux,im wondering if that could be it cuz i had to go into windows to do it

also  my friend said i should get rid of my .wine folder should i?

---

### Post by mc4man on 2017-06-09
Post the results of this - 
```
cat /etc/apt/sources.list
```

---

### Post by mc4man on 2017-06-09
Well would like to see sources.list as prior post (to check for proper location of the wine repo entry)
Rather than beat around this bush any longer copy, paste & run  these commands (strongly suggest you do copy & paste

```
sudo rm /etc/apt/sources.list.d/additional-repositories.list
```
```
sudo rm /etc/apt/sources.list.d/additional-repositories.list.save
```
```
sudo rm /etc/apt/sources.list.d/additional-repositories.list.save.1
```

Then try to update yet again..

---

### Post by devdlp on 2017-06-10
deven@deven-X501A1 ~ $ cat /etc/apt/sources.list
#deb cdrom:[Linux Mint 18.1 _Serena_ - Release amd64 20161213]/ xenial contrib main non-free
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) trusty contrib

---

### Post by howefield on 2017-06-10
Moved to the "*Mint*" forum.

---

### Post by devdlp on 2017-06-10
it worked for once but i still get this at the end:
```
Reading package lists... Done
W: [http://download.virtualbox.org/virtualbox/debian/dists/trusty/InRelease:](http://download.virtualbox.org/virtualbox/debian/dists/trusty/InRelease:) Signature by key 7B0FAB3A13B907435925D9C954422A4B98AB5139 uses weak digest algorithm (SHA1)
W: GPG error: [https://repo.skype.com/deb](https://repo.skype.com/deb) stable InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 1F3045A5DF7587C3
W: The repository 'https://repo.skype.com/deb stable InRelease' is not signed.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
deven@deven-X501A1 ~ $
```

and can i install wine now and if yes how do i go about doing it so i wont break it again?

---

