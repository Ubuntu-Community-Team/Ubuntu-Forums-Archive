---
title: "Lubuntu boots into terminal, no GUI"
date: 2013-09-26
forum: Installation &amp; Upgrades
---

### Post by Information_Missing on 2013-09-26
I installed Lubuntu with an alternate installation [as recommended here]("http://ubuntuforums.org/showthread.php?t=2175895"). However, there were some issues during the install, and application installation failed. I could not get it to work. The Grub was installed, and when it boots it goes directly to a terminal screen. There is no GUI, I read somewhere that I should try to run startx, but I get an error that Startx is not recognized. How do I proceed from here? My internet connection doesn't seem to be recognized either. 

The computer is an old Compaq that I got for free.
Compaq Presario sr1215cl
AMD sempron, unknown speed.
512Mb SDRAM
Geoforce FX 5200

---

### Post by Bashing-om on 2013-09-26
Information_Missing; Hi !

This might be a tough issue to trouble shoot.
Log onto your system through the text console and ->
Let's see where we stand on the GUI installation:
Terminal code:
```

dpkg -l xorg

```
If it returns something like this:
> 
sysop@1304mini:~$ dpkg -l xorg
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name            Version      Architecture Description
+++-===============-============-============-====================================
ii  xorg            1:7.7+1ubunt amd64        X.Org X Window System
sysop@1304mini:~$ 

then that is a good thing. let's see what results in trying to start the desk top:
```

sudo service lightdm start

```instead of "startx".
If the desk top does not start we need to know what errors the system reported. Maybe take a look at some log files and see what the system recorded.

[INDENT][INDENT]as good of a place to start as most
[/INDENT][/INDENT]

---

### Post by Information_Missing on 2013-09-27
Bashing-om! I've seen your name all over these forums, thanks for offering your help. 

Before I saw your reply, I reinserted the CD and chose "rescue a broken system". I was able to use the CD to successfully configure my network settings, but application installation failed again. I guess I now can access the package repository? Haven't tried yet though. 

The dpkg command returned this:
dpkg-query: no packages found matching xorg

The lightdm command returned:
lightdm: unrecognized service

---

### Post by Information_Missing on 2013-09-27
In an attempt to get xorg on the system I executed:

sudo apt-get install xorg

It created a list of dependencies and other packages that would need to come with which seemed good, but then requested that I put the CD 'Lubuntu 13.04 _Raring Ringtail_ - Release i386 (20130424)' into the drive and press enter, but when I put my installation CD in, it does not recognize it. Is that because I used an Alternate ISO?

---

### Post by Bashing-om on 2013-09-27
Information_Missing;
This forum do keep my attention and I am kept occupied !

OK, I have no experience with the "alternate installation", not doing the background research I am going to "assume !" that xorg is not installed by default and that you want a full desk top.
Do you have internet connection ?
do:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install xorg

```
desk top ? None I bet; do:
```

echo $DESKTOP_SESSION

```
I also expect that there is no desk top installed so ->
Now what do you want for a desk top .. I really like xfce4 .

[INDENT][INDENT]getting there is half the fun
[/INDENT][/INDENT]

---

### Post by Information_Missing on 2013-09-27
apt-get isn't working. I looked at my repository sources.list earlier and it was referencing the CDROM instead of a URL. Can I modify the sources.list file? I don't know if I have a text editor. kwrite did not work when I tried. what other editors might I have?

edit: Also, I know that lubutunu *is* supposed to have a desktop environment as standard.

---

### Post by Bashing-om on 2013-09-27
Information_Missing;
Presently you do not have an Xserver installed hence no GUI applications.
text based editors ... humm should have "nano" or "vim" installed.
looksee:
```

dpkg -l nano
dpkg -l vim
man nano
nano --help

```
safety first .. make a backup of the sources.list file !
Ya know all ya need to do is a "#" at the start of the reference line. At this point you should most certainly have access to apt-get !
The file you are working with: "/etc/apt/sources.list"

We are working to get ya a GUI.

edit: desktops.
alternate install edition .. I have my doubts on that .. standard desk top install YES .

[INDENT][INDENT]ain't no step for a stepper
[/INDENT][/INDENT]

---

### Post by Information_Missing on 2013-09-27
OK, now we're getting somewhere. I got the /etc/apt/sources.list to stop trying to use a cdrom. updated, upgraded, and then installed xorg. that all looks good.

When I tried 'sudo service lightdm start', I get the error 'lightdm: unrecognized service'.

I installed xfce4 by your suggestion. a reboot gives a slight difference, but I'm still at a terminal. It says "login: *Starting"  and then an [OK] on the far right. pressing enter gets me to the same textbased login I've been using til now.

edit: OK! startxfce4 is what I needed. I'm in the desktop now. Can ubuntu automatically run this for me?

---

### Post by Bashing-om on 2013-09-27
Information_Missing;
```

startxfce4

```
and now you are on the path of learning !

[INDENT][INDENT]it's a fun ride 
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2013-09-27
Information_Missing; I trust things are going well for you now.

It is past the witching hour for me and it is getting difficult for me to focus my thinking so;
I will leave you with this,
still to be done is to install a web browser.

I will check on your progress in my morrow
[INDENT][INDENT][INDENT]ubuntu, all things are possible
[/INDENT][/INDENT][/INDENT]

---

### Post by Information_Missing on 2013-09-27
sleep well, friend. 

I have already installed firefox and am now trying to get flash to work. I have also installed synaptic so that I don't have to keep opening a terminal window. I think I'm good from here and I truly appreciate your help.

---

