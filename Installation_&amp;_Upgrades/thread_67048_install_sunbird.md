---
title: "install sunbird"
date: 2005-09-19
forum: Installation &amp; Upgrades
---

### Post by christian on 2005-09-19
how do you install Sunbird from the tar.gz that the mozilla website gives to download? 
I've been rummaging around google, mozilla website, etc for easy step-by-step instructions but turned up very little...

I have some rough + random knowledge as to how to how some linux installations works but failed in all attempts with sunbird... I don't particularly want to run it as an extension from thunderbird/firefox...

... please, if there's anyone that could write up a brief step-by-step version (other posts on the subject here haven't recieved many replies). And I get the impression that once I can install this then my understanding of how to install other programs will be dramatically improved!

Many thanks!

---

### Post by wesdeboer on 2005-09-27
i did this and it seemed to work just fine for me:
download gtk2-xft from here... [http://www.mozilla.org/projects/calendar/sunbird_download.html]("http://www.mozilla.org/projects/calendar/sunbird_download.html")

```
tar -zxvf sunbird-0.2-i686-linux-gtk2+xft.tar.gz -C /opt/
/opt/sunbird/sunbird -calendar
```

---

### Post by oliwally on 2005-11-02
[QUOTE=wesdeboer]i did this and it seemed to work just fine for me:
download gtk2-xft from here... [http://www.mozilla.org/projects/calendar/sunbird_download.html]("http://www.mozilla.org/projects/calendar/sunbird_download.html")

```
tar -zxvf sunbird-0.2-i686-linux-gtk2+xft.tar.gz -C /opt/
/opt/sunbird/sunbird -calendar
```[/QUOTE]
This just isn't working for me. Sunbird does not open up. I would love some help with this please.

---

### Post by editrix on 2005-11-09
[QUOTE=oliwally]This just isn't working for me. Sunbird does not open up. I would love some help with this please.[/QUOTE]

I really hope someone answers you, or you figured it out by now so you can help me. I'm in Hoary (I doubt it makes a difference), and I can run Sunbird by clicking on the shell script in Konqueror, but not from the command line!

Tried:
sunbird
mozilla -sunbird
sunbird -calendar

Is there a special directory it should be located in? I've got mine in /.mozilla/sunbird, since firefox is in /.mozilla

---

### Post by ubuntu_demon on 2005-11-13
this worked for me :

(fill the correct name on the dots using the TAB key)

$ bunzip2 *sunbird....tar.bz2*
$ tar xvf *sunbird...tar*
$ sudo cp sunbird /opt

to start it :

$ /opt/sunbird/sunbird

---

### Post by mr_crimp on 2005-11-22
[QUOTE=ubuntu_demon]this worked for me :

(fill the correct name on the dots using the TAB key)

$ bunzip2 *sunbird....tar.bz2*
$ tar xvf *sunbird...tar*
$ sudo cp sunbird /opt

to start it :

$ /opt/sunbird/sunbird[/QUOTE]

Hi ubuntu_demon, I just followed your steps above, but instead of typing: $ sudo cp sunbird /opt. I typed: $ sudo cp -R sunbird /opt. I hope that is the right thing to do.

But when I want to start sunbird it is "freezing" at the "observer added" part and nothing is happening afterwards. Here is the terminal output:

```
$ /opt/sunbird/sunbird
Starting calendar alarm service
error creating table cal_calendars -- probably already exists
error creating table cal_calendars_prefs -- probably already exists
observer added
```

I hope someone can help me I don't know what to do with the errors.

---

### Post by ubuntu_demon on 2005-11-22
It worked for me :)

 I googled for the error and nothing came up to solve it. If there's isn't anyone who knows it's probably best to either :

-try a new version of sunbird
-rename the hidden sunbird files/dirs in your /home (if any) and try again to start it

---

### Post by wingedlizard on 2005-11-23
I'm running 5.10 on amd64, and I get the following:

>./sunbird-bin: error while loading shared libraries: libstdc++.so.5: cannot open >shared object file: No such file or directory

it looks like I'm running 6.0.5 of stdc++

Can I recompile it?

b\375

---

### Post by daynah on 2005-12-27
First I tried what Wes said except there is no tar.gz on that website so... that didn't work.

Then I tried what Ubuntu_Demon said and all was well until this...

daynah@ubuntuwhitc:~$ sudo cp sunbird /opt
Password:
cp: omitting directory `sunbird'
daynah@ubuntuwhitc:~$ /opt/sunbird/sunbird
bash: /opt/sunbird/sunbird: No such file or directory
daynah@ubuntuwhitc:~$ sudo cp sunbird /opt
cp: omitting directory `sunbird'
daynah@ubuntuwhitc:~$ /opt/sunbird/sunbird
bash: /opt/sunbird/sunbird: No such file or directory

So then I tried what mr_crimp said and I also got the exact same results as him. So... no one do what mr_crimp said unless you wanna get stuck at observer added. Come to think of it, my sunbird 0.2 on my lappy with Windows hates the alarms, also.

...I just want my calendars :(

---

### Post by ounas on 2005-12-27
[QUOTE=wesdeboer]i did this and it seemed to work just fine for me:
download gtk2-xft from here... [http://www.mozilla.org/projects/calendar/sunbird_download.html]("http://www.mozilla.org/projects/calendar/sunbird_download.html")

```
tar -zxvf sunbird-0.2-i686-linux-gtk2+xft.tar.gz -C /opt/
/opt/sunbird/sunbird -calendar
```[/QUOTE]


Thanks this worked for me...

-Ounas from Finland :p

---

### Post by daynah on 2005-12-27
The .tar.gz isn't on that website right now, though I did find a link to it eventually. That was the sole reason it "wouldn't work" I think the newer problems are the difference between the 0.2 (what you installed) and the 0.3 (what's on the site right now). Am trying and will keep you updated! :)

---

### Post by skion on 2006-01-06
Try running sunbird as root once, and then start it normally... Does that help?

---

### Post by daynah on 2006-01-06
This isn't Sunbird. [http://www.mozilla.org/projects/calendar/download.html](http://www.mozilla.org/projects/calendar/download.html) But the Thunderbird extension from that url worked. Not from any other URL. In fact, just to make sure you download the same xpi as I do, it's [http://ftp.mozilla.org/pub/mozilla.org/calendar/xpi/linux/calendar_linux_20050111.xpi](http://ftp.mozilla.org/pub/mozilla.org/calendar/xpi/linux/calendar_linux_20050111.xpi)

It's not Sunbird, but it took me two months to finally be able to be able to use my calendars! What a concept! A calendar to post on the internet! ~gasp~ iCal rocks. Anyway, so maybe that will hold you over until you can get sunbird. :) I like them seperate better, too. But at least you can USE the gosh darn things!

---

### Post by elwood_j_blues on 2006-01-06
The current alpha release does not seem to work. However, I tried it with the nightly build and it worked flawlessly.

Sunbird works better for me than the thunderbird extension when using it with a remote iCal file. :cool: 

Note, the file is now a bz2 compressed tar rather than gzip so instead of "tar xv**z**f" use "tar xv**j**f" to extract it.

---

### Post by crichell on 2006-01-07
This how to may help.  The how to installs Sunbird into your /opt directory, appropriately sets the permissions and places the sunbird icon into your Application > Office menu.  Installs Sunbird 0.3 alpha1 (the latest release as of January_06)

[http://system76.com/knowledge/index.php/Sunbird_Installation_on_Ubuntu_Breezy](http://system76.com/knowledge/index.php/Sunbird_Installation_on_Ubuntu_Breezy)

---

### Post by Buenaventura Durruti on 2006-01-11
The problem lies surely in the AMD64, if you have a system compiled for 64 bits its a bit complicated to have 32 bits compiled things working. I tried this afternoon to install the fuc*d calendar as:

1. firefox extension:

Can't do, even when I've a firefox compiled in 32 bits due java and flash extensions does not work with 64 bits one, the version (1.5) is not (at least yet) supported for the binaries of mozilla calendar for LiNUX+firefox that're downloadable in mozilla calendar's website.

2. thunderbird extension:

Simply impossible. It refuses to install, no mather if you use root. I think this is because my thunderbird is 64 bits but the calendar extension is 32 bits. Perhaps I can install a 32 bits version of thunderbird, but there's still another chance...

3. sunbird (standalone):

I've do a lot of things trying to install this but it refuses to work. I've removed some library missing errors by linking them from /usr/lib32 and running ldconfig, but I continue getting errors from "pango" or something similar about a component's name or... I'm tired and I do not remember exactly...

4. apt-get install mozilla-calendar:

Dependencies error. It claims that need version 2:1.7.12-0ubuntu2 of mozilla-browser but I've one *higher*: 2:1.7.12-1ubuntu1

I've expend three hours playing with this but I think its enough for today. Twomorrow I'll try it again... :-|

---

### Post by crichell on 2006-01-13
Running 32bit apps on 64bit Ubuntu is a bit of a pain.  My limited understanding is that you have to chroot all the 32bit apps and manage them separately.  Hardly worth it in my opinion - but it can be done.

---

### Post by foxy123 on 2006-01-28
[QUOTE=crichell]This how to may help.  The how to installs Sunbird into your /opt directory, appropriately sets the permissions and places the sunbird icon into your Application > Office menu.  Installs Sunbird 0.3 alpha1 (the latest release as of January_06)

[http://system76.com/knowledge/index.php/Sunbird_Installation_on_Ubuntu_Breezy](http://system76.com/knowledge/index.php/Sunbird_Installation_on_Ubuntu_Breezy)[/QUOTE]
it is a nice howto, but it does not work for me. When I run sunbird.sh script nothing happens. Neither happens when I cd to /opt and run ./sunbird... And there is no output in the console.

---

### Post by crichell on 2006-01-28
[QUOTE=foxy123]it is a nice howto, but it does not work for me. When I run sunbird.sh script nothing happens. Neither happens when I cd to /opt and run ./sunbird... And there is no output in the console.[/QUOTE]

Lets make sure sunbird is in there and executable

ls /opt/sunbird

you should see one entry that says *sunbird* and it should be green

cd /opt/sunbird
./sunbird

Does this bring up Sunbird for you?

---

### Post by saubz on 2006-01-29
The same is happening for me after I installed sunbird this way.  

Nothing happens.  And using ls /opt/sunbird, sunbird appears green.

---

### Post by crichell on 2006-01-29
[QUOTE=saubz]The same is happening for me after I installed sunbird this way.  

Nothing happens.  And using ls /opt/sunbird, sunbird appears green.[/QUOTE]

Even when you run the executable directly? ie - cd into sunbird directory and run ./sunbird

---

### Post by foxy123 on 2006-01-30
[QUOTE=crichell]Lets make sure sunbird is in there and executable

ls /opt/sunbird

you should see one entry that says *sunbird* and it should be green

cd /opt/sunbird
./sunbird

Does this bring up Sunbird for you?[/QUOTE]
the problem was with permissions. As soon I changed it to user it started to work. Thanks a lot.

---

### Post by saubz on 2006-01-30
thanks foxy.  i think i had the same permission problem.  first, i did 

```
sudo ./sunbird
```

and it opened fine. so i did

```
sudo chown *user* sunbird
```

and it worked fine from the application -> office menu.  sweet

---

### Post by crichell on 2006-01-30
I'll get that added to the How To - Thanks

---

### Post by lyly on 2006-02-13
I have done as explained in [http://system76.com/knowledge/index.php/Sunbird_Installation_on_Ubuntu_Breezy]("http://system76.com/knowledge/index.php/Sunbird_Installation_on_Ubuntu_Breezy")

But I have the error:

```
./run-mozilla.sh: line 131: 25271 Segmentation fault      "$prog" ${1+"$@"}
```

with sunbird-bin I have:
```
$ /opt/sunbird/sunbird-bin
/opt/sunbird/sunbird-bin: error while loading shared libraries: libxpcom.so: cannot open shared object file: No such file or directory

```

This lib exists in /opt/sunbird if I make a link of it to /usr/lib it gave me the same error but with the next lib.... I dont think making link for each lib is the right solution...

Can someone help?
Thx

Lynda

---

### Post by xmastree on 2006-02-13
Hell, I can't even get it to work under Windows... :confused:

---

### Post by Boberg on 2006-05-19
Maybe this package could be helpful for amd64 users:
[http://debian.csail.mit.edu/debian-amd64/debian-amd64/pool/main/s/sunbird/sunbird_0.2.99+0.3alpha1-3_amd64.deb](http://debian.csail.mit.edu/debian-amd64/debian-amd64/pool/main/s/sunbird/sunbird_0.2.99+0.3alpha1-3_amd64.deb)

Not the newest version, but easily installed and works on my 64bit architecture.

---

### Post by MarkSheely on 2006-06-20
I succesfully installed Sunbird on Dapper using this manual referenced earlier:

[http://knowledge76.com/index.php/Sunbird_Installation_on_Ubuntu_Breezy](http://knowledge76.com/index.php/Sunbird_Installation_on_Ubuntu_Breezy)

The only thing is, you have to change the version number from 0.3a1 to 0.3a2 to get the new version of Sunbird from Mozilla.  

Many thanks to whomever it was that pointed out the link above originally -

-Mark

---

### Post by crichell on 2006-06-20
The only thing is, you have to change the version number from 0.3a1 to 0.3a2 to get the new version of Sunbird from Mozilla.
-Mark[/QUOTE]

Thanks for the alpha2 update - The How To has been updated accordingly

---

### Post by nu2this on 2006-06-28
I too had great success with [http://knowledge76.com/index.php/Sunbird_Installation_on_Ubuntu_Breezy](http://knowledge76.com/index.php/Sunbird_Installation_on_Ubuntu_Breezy)
I now have all of my favorite Mozilla animals :D !

---

### Post by winvado on 2006-08-12
The system76 is a fine site re instructions for installing Sunbird and coming to grips with direct installations outside apt-get, checkinstall etc. ( I'm wading my way through the command line)

But... now - how to remove??

Help appreciated.

---

### Post by crichell on 2006-08-12
That's a good point.  We'll get a how to put together.  Removing the entry in your panel is pretty easy.

sudo rm /usr/share/applications/sunbird.desktop

---

### Post by Jesdisciple on 2008-05-28
I installed to .mozilla/sunbird and get the same results as wingedlizard:```
chris@Jesdisciple-laptop:~$ .mozilla/sunbird -safe-mode
bash: .mozilla/sunbird: is a directory
chris@Jesdisciple-laptop:~$ .mozilla/sunbird/sunbird -safe-mode
.mozilla/sunbird/sunbird-bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
chris@Jesdisciple-laptop:~$ .mozilla/sunbird/sunbird -calendar
.mozilla/sunbird/sunbird-bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
```

EDIT:```
chris@Jesdisciple-laptop:~/.mozilla/sunbird$ ls
chrome              extensions  libfreebl3.chk  libnss3.so     libsmime3.so     libxpcom_compat.so  LICENSE                 res             updater
components          greprefs    libfreebl3.so   libnssckbi.so  libsoftokn3.chk  libxpcom_core.so    mozilla-xremote-client  run-mozilla.sh  updater.ini
defaults            icons       libmozjs.so     libplc4.so     libsoftokn3.so   libxpcom.so         README.txt              sunbird         xpicleanup
dependentlibs.list  js          libnspr4.so     libplds4.so    libssl3.so       libxpistub.so       removed-files           sunbird-bin

chris@Jesdisciple-laptop:~/.mozilla/sunbird$ sudo ./sunbird
[sudo] password for chris:
./sunbird-bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

chris@Jesdisciple-laptop:~/.mozilla/sunbird$ sudo chown chris sunbird
[nothing]
```

... Help, please?

---

### Post by Tigerix on 2008-06-12
HiJesdisciple,

I had the same issue like you. 
You need to install the missing libaries!
Now its working for me :)

```
sudo apt-get install libstdc++5
```

---

### Post by Jesdisciple on 2008-06-12
That was it; thanks!

---

