---
title: "lost in linux. new to this, help"
date: 2005-05-19
forum: Installation &amp; Upgrades
---

### Post by masfenix on 2005-05-19
I juyst installed ubuntu. Right now i am Loving it :)

But i have a fwe questions:

I had win xp before? what happened to htat? How can i go to dos with this? where are my file systems?

my printer isntalled fine, but the hardware is printer and scanner combined, and it did not pick up the scanner. How can I installed the scanner. Its HP 1210.

if i try to play music videos, or music  , mp3, s or somthing i get this error saying I dont ahve the plugins. WHere can i get them? What directroy should i store them in?

Where can i find packages for linux? If i want to install extra stuff? is that possible?

How can i download shockwave? lol

I  think thats it for  now.
Thanks

---

### Post by smb2004 on 2005-05-19
ubuntuguide.org is a great website for installing all the missing plugings for mp3, dvd, wma, etc.  also shows how to install flash and acrobate plugin for mozilla, as well as how to add programs such as limewire, xine(movie player) firestarter(firewall), etc

about finding programs, do a google search for what you are looking for, its out there!  also you can use apt-get, which is great about debian based distros.  
System>Admin.>Synaptic Package Manager, will allow you to search for packages by name or what they do and install them for you.  

your file system starts at \.  simialer to C:\ .  'your' folder (i.e. my documents) is under /home/"your user name"/

hope this helps.  i was new too, but stuck with it and now linux is all i use!

---

### Post by bored2k on 2005-05-19
1. Multimedia Codecs >> [http://ubuntuguide.org/#codecs](http://ubuntuguide.org/#codecs)

2. Windows ? During the installation, did you select the default takeover harddrive option ? If you did, you erased Windows.

3. There is no DOS in Linux, we have a shell prompt. Applications > System Tools > Terminal

4. Packages, Flash > [http://ubuntuguide.org/#codecs](http://ubuntuguide.org/#codecs) ; [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

---

### Post by masfenix on 2005-05-19
> **bored2k]1. Multimedia Codecs >> [http://ubuntuguide.org/#codecs](http://ubuntuguide.org/#codecs)

2. Windows ? During the installation, did you select the default takeover harddrive option ? If you did, you erased Windows.

3. There is no DOS in Linux, we have a shell prompt. Applications > System Tools > Terminal

4. Packages, Flash > [http://ubuntuguide.org/#codecs](http://ubuntuguide.org/#codecs)  said:**
> http://ubuntuguide.org/#extrarepositories[/url]
 Thankyou..

but i dont know what i did, but with most of the things i try to install, i get this error now:
 
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  language-support-en: Depends: mozilla-firefox-locale-en-gb but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).


or somthing similar. 
How cna i fix this

---

### Post by Xian on 2005-05-19
[QUOTE=masfenix]Try 'apt-get -f install' with no packages (or specify a solution).
or somthing similar. 

How cna i fix this[/QUOTE]
Start by issuing that command in a terminal and look at the output:

```
$ sudo apt-get -f install
```

---

### Post by himuraken on 2005-05-19
Welcome to Ubuntu, I have been using Ubuntu for about a week now. I would recommend using the Synaptic Package Manger under the system -> administration menu since it is much more straight forward to use if you are new to linux.

---

### Post by bored2k on 2005-05-19
[QUOTE=himuraken]Welcome to Ubuntu, I have been using Ubuntu for about a week now. I would recommend using the Synaptic Package Manger under the system -> administration menu since it is much more straight forward to use if you are new to linux.[/QUOTE]
 Indeed. Wow I hadn't seen Shinta in a while :D thanks for the memoirs himuraken !

---

### Post by himuraken on 2005-05-19
OFF TOPIC: Yeah Rurouni Kenshin is a great series.

---

### Post by masfenix on 2005-05-19
[QUOTE=bored2k]Indeed. Wow I hadn't seen Shinta in a while :D thanks for the memoirs himuraken ![/QUOTE]
 Thankyou everyone. 

Does anyone know how to fix my scanner problem?

Other then that, I am all set to go. No more microsfot for me. I am trying to get them out of my life. lol :-P.
Sony Camera, Sony vid camrea, sony tv, sony playstation 2, hehe and now linux.

---

### Post by bored2k on 2005-05-19
[QUOTE=masfenix]Thankyou everyone. 

Does anyone know how to fix my scanner problem?

Other then that, I am all set to go. No more microsfot for me. I am trying to get them out of my life. lol :-P.
Sony Camera, Sony vid camrea, sony tv, sony playstation 2, hehe and now linux.[/QUOTE]
 I will translate a guide I found In Spanish:

1. Turn it on.
2. sudo apt-get install sane
3. sudo apt-get install libusb-0.1-4
4. sudo apt-get install hpijs hpoj

Once installed, lets configure it:
5. sudo /etc/init.d/hpoj setup

Then it will ask several questions:
> Probe for parallel-connected devices ([y]/n)? no (n)
Probe for USB-connected devices ([y]/n)? yes (y)

After a while it will say
> Press  alone to continue, or if you would like to add a
JetDirect-connected device, then enter its dotted-decimal
IP address or hostname here ---> press ENTER 

If all goes well :
> Starting the HP OfficeJet Linux driver.
mlc:usb:psc_1200_series

Let's see if the scanner got recognized:
sudo sane-find-scanner

If it did, you'll see
found USB scanner (vendor=0x03f0 [Hewlett-Packard], product=0x2f11 [psc 1200 series]) at libusb:001:005

Now we open Sane and we'll see the option.

**Hope this helps**

---

### Post by masfenix on 2005-05-19
[QUOTE=bored2k]I will translate a guide I found In Spanish:

1. Turn it on.
2. sudo apt-get install sane
3. sudo apt-get install libusb-0.1-4
4. sudo apt-get install hpijs hpoj

Once installed, lets configure it:
5. sudo /etc/init.d/hpoj setup

Then it will ask several questions:



After a while it will say


If all goes well :


Let's see if the scanner got recognized:
sudo sane-find-scanner

If it did, you'll see
found USB scanner (vendor=0x03f0 [Hewlett-Packard], product=0x2f11 [psc 1200 series]) at libusb:001:005

Now we open Sane and we'll see the option.

**Hope this helps**[/QUOTE]
 Haha Sweet dude!.
Thanks a lot.. A LOT!. lets see everything is configured now. we're good to go. 
by the way how do i open Sane llol

wait 

wait. :-P
i dont know what i did before but heres the next problem when I try to run music recorder, or music player  in the "applications menu"

"Registry is not present or it is corrupted. Please update it by running gst-register"

ANd when i open the Synaptic Package Manger, it says something is missing, and it cant be found or somthing? the program runs but it gives me that before.

---

### Post by logan2004 on 2005-05-19
[QUOTE=masfenix]ANd when i open the Synaptic Package Manger, it says something is missing, and it cant be found or somthing? the program runs but it gives me that before.[/QUOTE]

yo man! please be more specific!

---

### Post by bored2k on 2005-05-19
[QUOTE=masfenix]Haha Sweet dude!.
Thanks a lot.. A LOT!. lets see everything is configured now. we're good to go. 
by the way how do i open Sane llol

wait 

wait. :-P
i dont know what i did before but heres the next problem when I try to run music recorder, or music player  in the "applications menu"

"Registry is not present or it is corrupted. Please update it by running gst-register"

ANd when i open the Synaptic Package Manger, it says something is missing, and it cant be found or somthing? the program runs but it gives me that before.[/QUOTE]
 Applications > System Tools > Terminal
Type
gst-register
Press enter [duh]
that is it.

Inside a terminal, type sudo apt-get update and tell us the error [it would be the same as synaptc, but can copy paste it ;)].

---

### Post by masfenix on 2005-05-19
affan@ubuntu:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
affan@ubuntu:~$ sudo apt-get update
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary Release.gpg [189B]
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release.gpg [189B]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release.gpg [189B]
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release [16.9kB]
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates Release.gpg [189B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary Release
Hit [ftp://ftp.nerim.net](ftp://ftp.nerim.net) stable Release.gpg
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates Release
Get:6 [ftp://ftp.nerim.net](ftp://ftp.nerim.net) unstable Release.gpg [189B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main Sources
Get:7 [ftp://ftp.nerim.net](ftp://ftp.nerim.net) testing Release.gpg [189B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe Sources
Hit [ftp://ftp.nerim.net](ftp://ftp.nerim.net) stable Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/restricted Packages
Get:8 [ftp://ftp.nerim.net](ftp://ftp.nerim.net) testing Release [1349B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/restricted Sources
Hit [ftp://ftp.nerim.net](ftp://ftp.nerim.net) stable/main Packages
Get:9 [ftp://ftp.nerim.net](ftp://ftp.nerim.net) unstable/main Packages [18.0kB]
Get:10 [ftp://ftp.nerim.net](ftp://ftp.nerim.net) testing/main Packages [14.8kB]
Fetched 51.6kB in 18s (2845B/s)
Reading package lists... Done
affan@ubuntu:~$


I THINK I JUST DID THAT AND FIXED IT? lol ok ok .. this is very confusing :-P

---

### Post by bored2k on 2005-05-19
There was nothing to fix lol.

---

### Post by masfenix on 2005-05-19
i love the suuport, ,

how can i use my scanner tho?

---

### Post by bored2k on 2005-05-19
[QUOTE=masfenix]i love the suuport, ,

how can i use my scanner tho?[/QUOTE]
 Glad you do :D 

Applications > Graphics > XSane ?
Applications > Graphis > GIMP > Acquire > XSane ?

---

### Post by masfenix on 2005-05-19
xsane dosnt detect them. maybe i have to reinstall my scaner. cuz there was this error before :)

---

### Post by bored2k on 2005-05-19
[QUOTE=masfenix]xsane dosnt detect them. maybe i have to reinstall my scaner. cuz there was this error before :)[/QUOTE]
 My Scanning help has reached it limits. I don't do scanning :/

---

### Post by masfenix on 2005-05-19
[QUOTE=bored2k]My Scanning help has reached it limits. I don't do scanning :/[/QUOTE]
 well Thankyou.
And thanksevery one who helped.

I am all set and ready to go :)

---

