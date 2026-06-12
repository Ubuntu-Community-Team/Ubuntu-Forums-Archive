---
title: "question on upgrade?"
date: 2013-10-07
forum: Installation &amp; Upgrades
---

### Post by gregz41 on 2013-10-07
I have ubuntu 12.04 lts  love it BUT 2 problems and I was wondering if the upgrades addressed them......  Flash dont work tried everything on google and forums no luck...... playdeb keeps asking for app to download games but gives me no app options...   Flash has always been a problem  for me on linux not sure why but it is.....

Flash is what concerns me the most.

---

### Post by heir4c on 2013-10-07
Have you installed the "ubuntu-restricted-extras"?
You can install the packages via SoftwareCenter or via terminal:
```
sudo apt-get install ubuntu-restricted-extras
```
Normally you don't have to do that this days, here on a new install of 13.10 it works out of the box. I have no problems with flash (never in the 5 years I use Ubuntu).



For the Playdeb: have you following the instructions on the site? (by clicking on: "Click here to learn how to install games from PlayDeb" )


> Install the repository in one of the following ways:

    Install the playdeb package.

    Or configure the repository manually:

    Go to System-Administration-Software Sources, Third-Party Software tab, Add:
    deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) raring-getdeb games

    Add the repository GPG key, open a terminal window and type:
    wget -q -O- [http://archive.getdeb.net/getdeb-archive.key](http://archive.getdeb.net/getdeb-archive.key) | sudo apt-key add -

 

---

### Post by gregz41 on 2013-10-08
The apt-get ive done a few times no luck....says its up to date (always does)..... Like i said tried everything on google and forums. i dont get it  its the only issue I have with ubuntu.  i'm really sick of booting back an forth.....I quit using it for awhile cause of this... trying to get some family members to change but this makes it hard as they are heavy facebook users and the flash games are out.

Its wierd cause it will load all the way up to games -video whatever starting and just quit hang it does something......but not what its supposed too.......

And yes tried chrome same result and flash aid is gone now

---

### Post by ibjsb4 on 2013-10-08
What are the exact 'flash' errors and are you running firefox?

---

### Post by gregz41 on 2013-10-08
It gives no errors, just dont load it will load everything around it but not the game/video.  and yes firefox or chromium neither will work...but in chromiun it will tell you "flash wont load"

---

### Post by ibjsb4 on 2013-10-08
Don't know/use chromium, so do you see flash in FF in Edit>Preferences>Applications?

---

### Post by gregz41 on 2013-10-08
Shockwave flash file and SPL file

---

### Post by ibjsb4 on 2013-10-08
Ok, thats right.

Are you familiar with terminal?  Have a crash course :)
[URL="https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal"]
Open a terminal[/URL] and enter:

```
sudo apt-get install --reinstall ubuntu-restricted-extras
```

Watch for errors.

---

### Post by gregz41 on 2013-10-08
james@james-A7N8X-E:~$ sudo apt-get install --reinstall ubuntu-restricted-extras[sudo] password for james: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  thunderbird-globalmenu libglee0d1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 3 not upgraded.
Need to get 0 B/2,840 B of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 205698 files and directories currently installed.)
Preparing to replace ubuntu-restricted-extras 57 (using .../ubuntu-restricted-extras_57_i386.deb) ...
Unpacking replacement ubuntu-restricted-extras ...
Setting up ubuntu-restricted-extras (57) ...

no errors

---

### Post by ibjsb4 on 2013-10-08
Its hard to fix when you can't find anything wrong :(

I have never used this package, but wonder if it would be of any help to you.

EDIT: my bad, went to download it, but no longer available.  Link removed.

---

### Post by gregz41 on 2013-10-08
One thing I have noticed is in firefox, if you go to say  facebook or any flash game/video it will connect reconnect and just sit there little firefox spinning like crazy says connecting...........  but internet works can open another tab and surf away  lol

---

### Post by gregz41 on 2013-10-08
now u see why I'm ](*,)

---

### Post by ibjsb4 on 2013-10-08
Is this a new install?

---

### Post by gregz41 on 2013-10-08
I remember open suse and you had to install all nvidia and such drivers in manualy...which was fun :)   but this I just dont get

---

### Post by gregz41 on 2013-10-08
yes, on new install

---

### Post by gregz41 on 2013-10-08
question is there anyone I could shoot an email to about this. I know its a known problem google and forums are full of it.

---

### Post by ibjsb4 on 2013-10-08
> **gregz41 said:**
> I remember open suse and you had to install all nvidia and such drivers in manualy...which was fun :)   but this I just dont get

Its possible a driver upgrade exists, you have a program installed.  Its called 'hardware drivers' or maybe 'jockey' on your system.

This is a fresh install.  Did you burn at low speed?  Check CD after the burn?

[http://packages.ubuntu.com/lucid/jockey-gtk](http://packages.ubuntu.com/lucid/jockey-gtk)

---

### Post by ibjsb4 on 2013-10-08
> **gregz41 said:**
> question is there anyone I could shoot an email to about this. I know its a known problem google and forums are full of it.

[http://askubuntu.com/questions/ask](http://askubuntu.com/questions/ask)

---

### Post by gregz41 on 2013-10-08
slow speed and always check disks :)

---

### Post by gregz41 on 2013-10-08
**NOTE**: Adobe Flash Player 11.2 will be the last version  to target Linux as a supported platform. Adobe will continue to provide  security backports to Flash Player 11.2 for Linux. 

Hmmmmmmm  not good

---

### Post by ibjsb4 on 2013-10-08
> **gregz41 said:**
> **NOTE**: Adobe Flash Player 11.2 will be the last version  to target Linux as a supported platform. Adobe will continue to provide  security backports to Flash Player 11.2 for Linux. 

Hmmmmmmm  not good

I don't know, works for me, but I understand this can be a problem for gamers where latest flash is required.

---

### Post by gregz41 on 2013-10-08
> **ibjsb4 said:**
> I don't know, works for me, but I understand this can be a problem for gamers where latest flash is required.

its not just games its any flash thats the problem new old don't matter wont play

---

### Post by ibjsb4 on 2013-10-08
```
sudo dpkg --configure adobe-flashplugin
```

Try it.  If its ok, it will say already configured.

Got to go now, good luck :)

---

### Post by gregz41 on 2013-10-08
ahhh This is what i got

 sudo dpkg --configure adobe-flashplugin
[sudo] password for james: 
dpkg: warning: there's no installed package matching adobe-flashplugin

---

### Post by gregz41 on 2013-10-08
how do I install it it says its there in restricted extras

---

### Post by ibjsb4 on 2013-10-08
You can swap them around if you want, but I think your fine.  You have the flashplugin-installer package, thats all.

You can try either by just installing one.  Only one can be installed at a time so the other one is auto-deleted at time of install.

```
sudo apt-get install adobe-flashplugin

or

sudo apt-get install flashplugin-installer
```

[http://askubuntu.com/questions/15408/flashplugin-installer-vs-flashplugin-nonfree-vs-adobe-flashplugin](http://askubuntu.com/questions/15408/flashplugin-installer-vs-flashplugin-nonfree-vs-adobe-flashplugin)

[URL="http://askubuntu.com/questions/49298/whats-the-difference-between-flashplugin-installer-and-adobe-flashplugin"]http://askubuntu.com/questions/49298/whats-the-difference-between-flashplugin-installer-and-adobe-flashplugin


[/URL]

---

### Post by gregz41 on 2013-10-09
I can try either and neither solve the problem.... no flash will play.. Its there but wont play

---

### Post by gregz41 on 2013-10-09
I have tried firefox,google chrome, chromium and all the same result no flash.....will not load flash.........whats up....Guess I will keep checking and go back to windows til this can be addressed..........

[http://askubuntu.com/questions/186779/why-did-adobe-stop-flash-player-for-linux?lq=1](http://askubuntu.com/questions/186779/why-did-adobe-stop-flash-player-for-linux?lq=1)  


maybe part of it.......    this sucks

---

### Post by gregz41 on 2013-10-10
found this interesting

[http://www.infoworld.com/t/adobe-flash/javascript-killed-the-flash-player-plug-in-star-228539](http://www.infoworld.com/t/adobe-flash/javascript-killed-the-flash-player-plug-in-star-228539)

---

### Post by gregz41 on 2013-10-10
ok found that in usr/lib/firefox addons/plugins  was missing the .so file. So I downloaded put it there it now starts to play (further than I've been in mths)....but still don't work :confused:

---

### Post by heir4c on 2013-10-10
Can you try it out with a Live-cd/usb? When it works on the Live-cd/usb and also in windows (if you have a dualboot) than it is something in the installed Ubuntu on the PC/Laptop.
So we can check all the possibilities where it goes well and where not.

---

### Post by gregz41 on 2013-10-15
ok Think its the nvidia drivers......ok I took and old computer I had in closet loaded ubuntu 12.04 on it updated it will play flash on it,  but its like a 60's flash back....lol  colors are green and purple and man the only way to describe it is an old 60's poster................................

---

### Post by mörgæs on 2013-10-16
Now the thread spans four pages and still noone has asked you to run

```
sudo lshw -sanitize > lshw.txt
```

and post lshw.txt in CODE tags.

Please do this for all computers in question.

---

### Post by apollothethird on 2013-11-18
> **mörgæs said:**
> Now the thread spans four pages and still noone has asked you to run

```
sudo lshw -sanitize > lshw.txt
```

and post lshw.txt in CODE tags.

Please do this for all computers in question.

Hi, Gregz41.  I was looking to see the output of the command above suggested by Morgaes.  It appears that you have a lot of support from very knowledgeable people on your issue.  It should be a matter of a few messages that they get to the bottom of the issue.

I read the four pages.  Maybe I missed it, but I didn't see two important commands issued:

```

$ sudo apt-get update
$ sudo apt-get upgrade

```

Will you run those two commands and tell me if you get any errors.  Does the flash work after those two commands.

Also, please include the output from the lshw command.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

