---
title: "Help with new installation"
date: 2005-07-02
forum: Installation &amp; Upgrades
---

### Post by Hyperion on 2005-07-02
Hi,i m a Linux newbie and this is also the first time i installed Ubuntu.I wonder if you could help with these problems:

1)I have 2 hard disks,one SATA with WinXP and one PATA for Linux.GRUB  can't load the WinXP (i can still do it by changing a BIOS setting everytime switching the hard disks but is a bit annoying).Is there a solution?

2)The PATA disk was partitioned in a big partition (about 35GB) with reiserFS for Ubuntu,a 260 MB for swap and a 1,87 GB as FAT 32.Ubuntu  doesn't seem to list the FAT 32 partition in the storage media.

3)The Desktop is slightly moved to the right of the screen.I have to move it to the left using the monitor's settings each time.using 1024x768 @ 85 Hz with Radeon 9600 and LG F700P.Is this normal?

4)and most important.I can't install the drivers for my USB ADSL modem.I have the eciadsl drivers (the modem uses Globespan chipset and works with other distros i tried) ,but when i try to install them with dpkg -i,the installation is aborted because of lacking dependencies problem.Says pppoE is not installed.What should i do???

Thank you in advance

---

### Post by Omnios on 2005-07-02
The grub problem is addressed in the forum you might want to try a search for it. You may get away with editing the grub part in linux.

 check out the Unofficial starters guide for instructions on how to mount a Fet32 disk.
  
   [http://ubuntuguide.org/](http://ubuntuguide.org/) 

  I have a similar screen problem as far as I know its a live with it issue for now.

 As far as the modem is concerened go into Synaptic updgrader the advanced part and type in search (name and description) "pppoE" and you will probably find the dependacy (Last resort keep downloading ppp till you find the one you need (not recomednded) ). I did this a few times and its a real pain. Basicly look for pppoE dependacy in the description.

 I have used Linux for about 3 months and im still a newb but ive come a long way! Stick with it. 

 Does Linux suck! Who cares its fun.
 Even If I got Longhorn for free I still couldn't afford it! (software and $3 smileys)
 I learn't more in 3 months of playing with Linux than I learn't with XP in 2 years!
 Joining the Ubunti community is like joining the boyscouts!
 Did I mention Fun!

---

### Post by Hyperion on 2005-07-02
Thanks Omnios.I ll give it a try but i think that ubuntu isn't for me...I can't keep playing with the monitor position settings back and forth when i load Windows and Linux and i have my doubts i can make the pppoE work.I also can't download anything since my modem is dead without the eci drivers...I ve tried 2 other distros that i managed to connect to internet with firestarter up and running in 15 minutes.I think i ll chose one of them...Pitty,because i liked much the Gnome menus.

---

### Post by Stemp on 2005-07-02
Don't worry Hyperion, try other distros (Gnoppix or Fedora if you like gnome), trying Ubuntu didn't cost you much  ;-) 
And I'm sure after a fews tries, you will come back (maybe be Breezy will be for you)

---

### Post by Omnios on 2005-07-02
K last thing edit you synaptic so your Installation CD is on it

Go to add/remove programs then advanced to get synaptic. In synaptic choose settings repositories. In the repository window choose settings. Check show disabled software souces. then then close and the cd will be there. Now uncheck everything except the cd as you dont have net yet. The CD has huge amounts of software etc aperently over 1,000 pieces and will probably have the dependacy that you need. 

 Cheers! And Ubuntu has a #1 Linux newbie friendly rating.

---

### Post by Hyperion on 2005-07-02
Thanks again for the effort Omnios,but it didn't work...I verified that in Synaptic the only repository was the CD Wary 5.0.4 and that all other repositories were unticked.i searched for ppp,pppoe, the result was that ppp is installed and also is installed pppoeconf.Now,the eciadsl drivers in their properties had 2 dependencies: ppp and pppoe.A package "pppoe" didn't come up when searching in synaptic.So i went to root terminal and launched "pppoeconf".I got a screen saying me that there is no ethernet card detected and asked if i wanted to run a utility i don't recall the name  to add manually the drivers.I clicked Yes (pressing enter highliting the yes) but nothing happened.I tried to launch that utility from the root window,but said there was no such util.I also tred man utility name,no manual available.I also tried to "fix" the broken eciadsl package ,but Synaptic simply marked it for removal.

I agree that Ubuntu seems newbie friendly,i liked the menus,much easier than KDE,i liked the Synaptic already installed (i started with apt-get in Kanotix),the add/remove programs,but the best newbie system imho is a hybrid of Kanotix and Ubuntu.For ex. Kanotix automatically sees all hard disks,even has Captive.Also has all codecs ready.I tried to see an avi with ubuntu and i got message that the codec is missing.Now this phantomatic pppoE.On the other hand,Kanotix has more complicated KDE interface with many mainly network tools that an average home user will never use and just clutter the interface.Also installing ATI drivers ruin my refresh rate there.I think both should learn from each other.I also tried Blag,but i prefer debian.The installation of my modem is both kanotix and Blag is  matter of minutes only.

su
you go to the directory of the deb or rpm driver package
you give dpkg -i
then eciadsl-config-text and you put your ISP's name,password,modem model etc from a cosy list
eciadsl-start and you connect

Why all this hassle with ubuntu ,i don't know.Anyway,i ll try again the next release.For now i m downloading Mepis,since i ve heard good things about it for newbies and it's debian based too.

Thanks for the help anyway.A really nice forum with quick replies and helpful members.

---

### Post by Omnios on 2005-07-02
Um can you get the dependancy with WinXP you can mount and read a ntfs hard drive which means you can copy it to linux! As to finding the dependancy? Another funny thing with Ubuntu things just seem to work with no warnings after installing something. I have 32k cable and it set up right out of the box "even before it got to Xserver. 
 
 If you nail the right driver tool or dependancy it may just work but then again maybe not. Thing I learn't about linux is just keep trying and it useualy works out. I spent over a week doing my first install trying to get the monitor working "dam those funky monitors lol"
 
 Did you try doing a forum search for ppp etc? Lots of reading but you may find the answer there.

---

### Post by Hyperion on 2005-07-03
Thanks agan Omnios.Yes,i had searched yeasterday in the forum too before posting this,but to no avail.

these are 2 examples:

[http://www.ubuntuforums.org/showthread.php?t=45195&highlight=pppoE+installed](http://www.ubuntuforums.org/showthread.php?t=45195&highlight=pppoE+installed)

[http://www.ubuntuforums.org/showthread.php?t=45923&highlight=pppoE+installed](http://www.ubuntuforums.org/showthread.php?t=45923&highlight=pppoE+installed)

Nobody seems to know how to install these modems.They have exactly my problem.USB ADSL modems are picky and in all distros you need to have the driver ready downloaded yourself,but apart this,it installs OK.It's a pitty,because the eciadsl drivers support a big range of different USB brand modems (i think over 40) that use Globespan chipsets and all these people can't use Ubuntu if they are newbies.Ethernet modems are always a breeze to install,but USB like mine also work just fine.But something must be done in Ubuntu about tthem,to make the life of the user easier.Anyway,i can't lose another day playing around with Ubuntu.Hopefully the next release will be more USB friendly.

Thank you very much for all the help :smile:

---

### Post by Omnios on 2005-07-03
Got the ubuntu driver demons and stuff for the modem now I just have to find the archive file lol this could take a bit its 192k.

Edit: Found the lib to
Edit2: Found The files want them emialed or messengered  :smile:  ?

---

### Post by Hyperion on 2005-07-03
Thanks Omnios.You have  a private message with my mail.

---

### Post by Hyperion on 2005-07-05
Just for eventual other newbies that will encounter the same problem and will use the search function,the solution came to me after reinstalling Kanotix where i saw that it had a pppoe package (while Ubuntu didn't and it's not in the CD either).

I haven't tried it,since i didn't reinstall Ubuntu,but should work.first you need to install pppoe taking it from here:

[http://packages.debian.org/testing/net/pppoe](http://packages.debian.org/testing/net/pppoe)

Then use the eciadsl drivers and should work.

Ubuntu is nice,but it's not exactly "for human beings"  :) 

Regards

---

