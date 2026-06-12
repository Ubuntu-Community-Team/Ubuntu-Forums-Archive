---
title: "NO GUI after Install"
date: 2005-08-04
forum: Installation &amp; Upgrades
---

### Post by youngdaniel on 2005-08-04
Hi guys

i tried the Live CD, it looked like it went through all it needed to, but on the last bit where it looks like it would have launched the GUI, it just leaves a blank screen that my monitor says is "No Signal".

I went ahead with the Install CD and installed on a spare 200gb Sata drive, yet again installed fine, ran after reboot fine, and on the last bit, where it looked to load the GUI, it gave "No Signal".

My monitor is a Sony TFT SDM-HS94P, it was running through a DVI cable connected to an ATI PCI-EXPRESS X600. I tried switching it to the HD-15 VGA Cable and the monitor then said that the signal was out of range somwthing like 107.9/103 mhz????

Any Ideas how I can get some sort of GUI out of my system??

Thanking you

Dan

---

### Post by Matriz on 2005-08-04
I did have that problem too when i first time installed ubuntu and the installation borkked up in some point and when i rebooted it did go well to login screen...and i did hear that sound what comes when you go to login screen...but it gived No signal error to mee...actually it was Monitors text..not from ubuntu...so ,sry it doesnt help you but just telling that i have had that too : o

---

### Post by az on 2005-08-04
If you can get into a console by hitting CTRL-ALT-F1, try:

log in
sudo /etc/init.d/gdm stop
sudo dpkg-reconfigure xserver-xog
(try differnt settings if it does not work the first time.  try the vesa driver, for example.)

sudo /etc/init.d/gdm restart

---

### Post by youngdaniel on 2005-08-05
As I am an absolute newbie, at what point can i get in to the console? using those key combo's?

Is this a known issue/bug, because I have been searching around on google and there are quite a few articles about this happening? 

Is it best to use the DVI or the HD-15 Cable????

---

### Post by Lord Illidan on 2005-08-05
Try using the failsafe option at boot..

---

### Post by youngdaniel on 2005-08-05
and for a newbie that means doing what??

---

### Post by Lord Illidan on 2005-08-05
When you boot, there should be a menu with numerous choices.

1. Ubuntu, kernel 2.6.10-5-386
2. Ubuntu, kernel 2.6.10-5-386 (recovery mode)
3. Ubuntu, kernel memtest86+
4. Microsoft Windows XP Professional


Those are mine...

Now, on yours, the menu should be similar to this. Chose the recovery mode option to boot to a Command Line.

---

### Post by Darkscot on 2005-08-05
[QUOTE=Matriz]I did have that problem too when i first time installed ubuntu and the installation borkked up in some point and when i rebooted it did go well to login screen...and i did hear that sound what comes when you go to login screen...but it gived No signal error to mee...actually it was Monitors text..not from ubuntu...so ,sry it doesnt help you but just telling that i have had that too : o[/QUOTE]

I also had this problem when I first installed Ubuntu on a particular PC.  The defualt video setting that Ubuntu chose was out of range of my monitor.  I had to log in on recovery mode and use the command line to edit the settings manually.  I seem to remember I had to change the monitor refresh rate.

---

### Post by Lord Illidan on 2005-08-05
I had a similar problem, too...which is why I pitched in. My Nvidia card couldn't work with the nv drivers, so I had to boot to recovery mode and switch the X.org to use vesa, after which I could install the official nvidia drivers from the comfort of a gui.

---

### Post by sorry_name_taken_already2 on 2005-08-05
_**I installed unbuntu 5.04** on my Toshiba 4080XCDT laptop_ w 64/128MB ram, 10Gb hdd and onboard SIS cyber chipset. Install is complete after many attempts, I finally got all of unbuntu packages and base system files installed and setup a user (incidentally, it did not prompt me for su or root user). I dunno how to set up Xwin in unbuntu. _There is no Xxonfigurator like in Redhat_. After startup it doesn't not boot into GUI desktop or Gnome. I am stuck in a shell or prormpt with a file mbox. _Can anyone help me to set up my video and monitor?_ I am a newbie here!! 

ANd then *fingers crossed*install PHP,MYSQL and games. The screenshots look promising and easier than most linux i have played around with.


Cheers

---

### Post by sorry_name_taken_already2 on 2005-08-05
THOUGHT THIS MIGHT HELP - a walkthrough for other newbies. I didnt get the X setup or monitor for during install :((

Can someone help me manually set up my monitor and video for my older laptop.

Cheers

---

### Post by sorry_name_taken_already2 on 2005-08-05
\\:D/ THOUGHT THIS MIGHT HELP - a walkthrough for other newbies.  \\:D/ 

I didnt get the X and monitor setup during install :(

Can someone help me manually set up my monitor and video for my older laptop.

Cheers

---

### Post by sorry_name_taken_already2 on 2005-08-05
[QUOTE=sorry_name_taken_already2]_**I installed unbuntu 5.04** on my Toshiba 4080XCDT laptop_ w 64/128MB ram, 10Gb hdd and onboard SIS cyber chipset. Install is complete after many attempts, I finally got all of unbuntu packages and base system files installed and setup a user (incidentally, it did not prompt me for su or root user). I dunno how to set up Xwin in unbuntu. _There is no Xxonfigurator like in Redhat_. After startup it doesn't not boot into GUI desktop or Gnome. I am stuck in a shell or prormpt with a file mbox. _Can anyone help me to set up my video and monitor?_ I am a newbie here!! 

Can you please email [email]curious_@hotmail.com[/email] ASAP. I need a running laptop ASAP to install PHP,MYSQL and games to learn on my journey overseas. The screenshots look promising and easier than most linux i have played around with.


Cheers[/QUOTE]

This a good walkthrough with excellent screen dumps
[http://www.mrbass.org/linux/ubuntu/install/](http://www.mrbass.org/linux/ubuntu/install/)

it might help other newbies. I did not get the X or monitor setup during install :(

Can someone show me how to manually install X and video for my older laptop.

---

### Post by youngdaniel on 2005-08-05
I went in to console mode

Didnt need to log in? does that matter?

I then proceeded with

sudo /etc/init.d/gdm stop

that worked fine!

then tried 

dpkg-reconfigure xserver-xog

it came back with

Package 'xserver-xog' is not installed and no info is available.

what does this mean? I did a straightforward default installation??

Help please, because I really want to get into Ubuntu!!!

---

### Post by youngdaniel on 2005-08-05
ok, worked out that what the issue was to get in to change the setting

it was "xserver-xorg" and not "xserver-xog" as posted!!!

Played about with some settings there, mainly all the defaults and it still didnt do anything!!!

monitor said "no signal"   "out of range"    "109.7khz/103hz"

tried an old CRT and that failed as well

The xserver config located my ATI Pci-xpress x600 and my Sony TFT SDM-HS94P but then still didnt work? whats going wrong?

Also on the setups it asked me to indicate what resolutions, however i dont quite understand the setup thing, is blank, not to be used, or to be used? and when you go up and down the list, it gets messy with ** instead of just one? and you cant deselect one that is already marked!! 

Must be an easier way than this??

---

### Post by sorry_name_taken_already2 on 2005-08-06
[QUOTE=youngdaniel]I went in to console mode

Didnt need to log in? does that matter?

I then proceeded with

sudo /etc/init.d/gdm stop

Help please, because I really want to get into Ubuntu!!![/QUOTE]

I tried, sudo /etc/init.d/gdm stop
then it prompted me for a password (I assume its the root password)
I wasnt asked to enter a root password during install.

so i cant stop gdm to configure Xserver...
"dpkg-reconfigure xserver-xorg"

---

### Post by sorry_name_taken_already2 on 2005-08-06
If this is Ubuntu, then you need to use "sudo" and not "su".

For a one time root need, type:

sudo tar xvfz xampp-linux-1.4.14.tar.gz -C /opt

You will then be presented with a password prompt. Enter your user password that you used during install.

If you would like to set a root password:
sudo passwd root

And, if you'd like to remain as root (can be dangerous):

sudo -s

Hope this helps!
Be well, SD

[http://www.geekstogo.com/forum/Help_installing_something_on_Ubuntu-t46015.html](http://www.geekstogo.com/forum/Help_installing_something_on_Ubuntu-t46015.html)

**I  CREATED A NEW PASSWORD AND HAVE ROOT ACCESS NOW!!**

[COLOR=Red]root@ubuntu:/home/andy # dpkg-reconfigure xserver-xorg
Package 'xserver-xorg' is not installed and no info is available.
User dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (+dpkg-deb --content) to list thier contents.
 ](*,) **/usr/sbin/dpkg-reconfigure: xserver is not installed[/COLOR]** ](*,) 

HELP!!!

---

### Post by sorry_name_taken_already2 on 2005-08-06
Xserver was not installed during the install process..it crashed while it was installing "additional packages" after the reboot; minus the install CD!

Can anyone help me install Xserver...?
TOSHIBA Satellite 4080XCDT
PII 366Mhz
64/128MB RAM
FUJITSU 10GB
Trident Cyber 9525 video chipset with 2 Mb of video RAM
and UNBUNTU O/S

QUOTE(SoccerDad @ Aug 7 2005, 03:12 AM)
[http://www.geekstogo.com/forum/index.php?act=ST&f=7&t=51526&st=0](http://www.geekstogo.com/forum/index.php?act=ST&f=7&t=51526&st=0)

[COLOR=RoyalBlue]sudo apt-get install xserver-xorg

It will ask for a password, use yours. Xserver-xorg will have some dependancy packages, just type Y (yes) when prompted.[/COLOR]

 
After unpacking 17.9MB of additional disk space will be used.
Do you want to continue [Y/n]?Y
Preconfiguring packages...
Unpacking xserver-common (from ../xserver-common_6.8.2-10_i386.deb)
Buffer I/O error on device hdc, logical block 288212
...
dpkg-deb (subprocess):error in buffer_read(stream):failed to write to pipe in copy: Input/output error
...
Errors were encountered while processing:
/cdrom/pool/main/x/xorg/xorg-common_6.8.2-10.all.deb
...
E: Subprocess /user/bin/dpkg returned an error code (1)

** Bugga!!! not installing!!! **  


Thanks - getting closer to a beer!


Ubuntu/Debian-Sarge Mini-RAM HOWTO
[http://www.binonabiso.com/en/Ubuntu-miniRAM-HOWTO.html](http://www.binonabiso.com/en/Ubuntu-miniRAM-HOWTO.html)

Ubuntu installs by default with the Gnome Desktop and other memory-intensive applications. So if you do not have a fast and powerful machine (Pentium 4 and 512 MB of RAM) your system will be quite slow. The following document explains the steps, how to install Ubuntu and a GUI on a low memory system, so that you can use it as a Workstation for your daily work. It is aimed to the average SOHO-user (Small Office/Home Office).


STILL F***ing lost?!
[http://ubuntuguide.org/](http://ubuntuguide.org/)

[COLOR=Red]..Just wondered. Does anyone use this Forum? [/COLOR]

---

