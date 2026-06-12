---
title: "Anyone EVER go from ARCH to (K)ubuntu? 64bit? read this.."
date: 2010-06-18
forum: Installation &amp; Upgrades
---

### Post by binskipy2u on 2010-06-18
I am currently using ARCH 64bit, it's a rolling release..  works well.. but there is no wine for 64bit.. and it takes alot of work to get it working.. took months of reading, and trial and error.. but what I was wondering is..
if i were to do a Minimal install of ubuntu.. then using this information/website.. install what I want.. (I'm sure synaptic will take care of all dependencies) 
************************
```
1 – Expand the Software Repository List
First of all, lets make Ubuntu “see” more packages. Go to the terminal and edit your sources.list with :
sudo gedit /etc/apt/sources.list
Here is the content of my sources.list which I think is quite complete to have all the necessary applications you could ever need. So delete the whole content of your sources list and replace it with the content of mine
Save it. Now import the necessary repositories keys to avoid “aptitude” crying about some missing keys, go to the terminal and type:
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com DCF9F87B6DFBCBAE F9A2F76A9D1A0061 A040830F7FAC5991 2EBC26B60C5A2783
Get your system up to date with :
sudo aptitude update && sudo aptitude full-upgrade
Now all your programs will run on the last version.
2 – Anti-Virus
Windows equivalent : AVG AntiVirus, NAV, TrendMicro, F-Prot, Kaspersky, …
Ubuntu equivalent : ClamAV, Avast
ClamAV
sudo aptitude install clamav clamtk
Access it through System Tools &#8594; Virus Scanner .
Avast
wget [http://files.avast.com/files/linux/avast4workstation_1.3.0-2_i386.deb](http://files.avast.com/files/linux/avast4workstation_1.3.0-2_i386.deb) && sudo dpkg -i avast4workstation_1.3.0-2_i386.deb
Access it through Accessories &#8594; avast! Antivirus .
3 – Essential tools for compiling from sources
sudo aptitude install build-essential checkinstall cdbs devscripts dh-make fakeroot libxml-parser-perl check avahi-daemon
4 – Java runtime environment
Java is a very important thing to install, now that many programs like Azureus need it to run. So type:
sudo aptitude install sun-java6-jre sun-java6-plugin equivs
6 – Multimedia
Windows equivalent : windows media player, real player, vlc, mplayer
Ubuntu equivalent : vlc, mplayer, helix player
To have Ubuntu playing all kinds of stuff, you need to install many codecs. So on the Terminal, type:
* Installing vlc and mplayer (plays almost everything):
sudo aptitude install vlc mplayer
* Common packs
sudo aptitude install non-free-codecs libxine1-ffmpeg gxine mencoder mpeg2dec vorbis-tools id3v2 mpg321 mpg123 libflac++6 ffmpeg libmp4v2-0 totem-mozilla icedax tagtool easytag id3tool lame nautilus-script-audio-convert libmad0 libjpeg-progs libmpcdec3 libquicktime1 flac faac faad sox ffmpeg2theora libmpeg2-4 uudeview flac libmpeg3-1 mpeg3-utils mpegdemux liba52-dev
* Gstreammer 0.10
sudo aptitude install gstreamer0.10-ffmpeg gstreamer0.10-fluendo-mp3 gstreamer0.10-gnonlin gstreamer0.10-pitfdll gstreamer0.10-sdl gstreamer0.10-plugins-bad-multiverse gstreamer0.10-schroedinger gstreamer0.10-plugins-ugly-multiverse totem-gstreamer
* More programs
sudo aptitude install gstreamer-dbus-media-service gstreamer-tools ubuntu-restricted-extras
* Enable dvd support
sudo aptitude install libdvdcss2 && sudo /usr/share/doc/libdvdread4/./install-css.sh
* Flash
sudo aptitude install gsfonts gsfonts-x11 flashplugin-nonfree
7. Tweak your eyecandy
Ubuntu 10.04 comes with compiz fusion effects OOTB but doesn’t offer a way to customize them.
In a terminal copy/paste this:
sudo aptitude install simple-ccsm
Now navigate to System &#8594; Preferences &#8594; Simple CompizConfig Settings Manager .
8 – Missing Windows software?? Run Windows softwares in Linux!!!
Run Windows Applications such as 7zip, Google Sketchup, AutoCAD, Dreamwaver, Flash MX, Fireworks MX, IE6, IE7, Safari, Itunes, Windows Media Player and many more…
Play Windows Games in Linux like Age Of Empires, Call Of Duty, Diablo, Fear, Fallout, Far Cry, Grand Theft Auto, Half Life, Halo, Hitman, Max Payne, Need For Speed, Prince Of Persia, Sim City Star Wars, The Simsworld of warcraft , Tomb Raider, Warcraft, World Of Warcraft, Counterstrike and many other can be played.
Install Playonlinux. It’s based on wine. Wine is a compatibility layer for running Windows programs in Linux.
sudo aptitude install wine playonlinux
9 – Clipboard Management
By Default in ubuntu when u copy something from an application and closes the application u will not be able to access it from the clipboard. And also when u copy severals text in serial u only have the last on available to you in the clipboard. To solve that install either of the following but Glipper is better because it supports plugins.
Glipper
sudo aptitude install glipper
Then right click ur panel &#8594; Add to Panel then drag Clipboard Manager to ur panel
Parcellite
sudo aptitude install parcellite
10 – Archiver/ Packing software
Windows equivalent : winrar, zip, 7zip
Ubuntu equivalent : tar, unrar, p7zip, arj, unace
It’s bad when you don’t have Internet on your computer/notebook, but you have to pack/unpack something but the file format isn’t recognized by the system. To prevent from this bad situation, you can install a bunch of packing software by typing this on the terminal:
sudo aptitude install unace rar unrar zip unzip p7zip-full p7zip-rar sharutils uudeview mpack lha arj cabextract file-roller
11 – Graphical web browser
Windows equivalent : Internet explorer, firefox, opera
Ubuntu equivalent : Firefox, opera, chromium
Opera
sudo aptitude install opera
Firefox (installed by default intrepid)
sudo aptitude install firefox
Chromium (open source equivalent of Google Chrome)
sudo aptitude install chromium-browser chromium-browser-l10n
12 – Download Manager
Windows equivalent : Free download manager
Ubuntu equivalent : Multiget
MultiGet is a http/ftp downloader with a nice GUI for linux desktop users. It can run on almost all desktops without any configuration. It has many powerful functions comparing to others.
sudo aptitude install multiget
Access it through Applications &#8594; Internet &#8594; MultiGet .
13 – Graphical Email client
Windows equivalent : Outlook
Ubuntu equivalent : Evolution, Thunderbird
Evolution (installed by default in lucid)
sudo aptitude install evolution
Access it through Applications &#8594; Internet &#8594; Evolution Mail .
Thunderbird
sudo aptitude install thunderbird
Access it through Applications &#8594; Internet &#8594; Mozilla Thunderbird Mail/News .
14 – Instant Messanging protocal clients
Windows equivalent : MSN messenger, Yahoo messenger, QQ, AIM, Gtalk, ICQ,IRC
Ubuntu equivalent : Empathy, Pidgin, emesene
Empathy IM Client (installed by default)
Add the related launchpad repository :
sudo add-apt-repository ppa:telepathy/ppa && sudo aptitude update
Then install it by running the following :
sudo aptitude install empathy telepathy-mission-control-5 telepathy-gabble telepathy-butterfly telepathy-haze telepathy-idle telepathy-salut telepathy-sofiasip libtelepathy-farsight0 python-tpfarsight galago-eds-feed python-galago python-galago-gtk msn-pecan
Access it through Applications &#8594; Internet &#8594; Empathy IM Client .
Pidgin
Pidgin is an easy to use and free chat client used by millions. Connect to AIM, MSN, Yahoo, and more chat networks all at once. Supported chat networks: AIM, Bonjour, Gadu-Gadu, Google Talk, Groupwise, ICQ, IRC, MSN, MySpaceIM, QQ, SILC, SIMPLE, Sametime, XMPP, Yahoo!, Zephyr
Add the launchpad repository :
sudo add-apt-repository ppa:pidgin-developers/ppa && sudo aptitude update
Then install it :
sudo aptitude install pidgin pidgin-data pidgin-lastfm pidgin-guifications msn-pecan pidgin-musictracker pidgin-plugin-pack pidgin-themes
Access it through Applications &#8594; Internet &#8594; Pidgin Internet Messenger .
Emesene only for MSN Messenger.
Add the launchpad repository :
sudo add-apt-repository ppa:bjfs/ppa && sudo aptitude update
Then install it :
sudo aptitude install emesene
Access it through Applications &#8594; Internet &#8594; Emesene .
15 – VOIP
Windows equivalent : skype
Ubuntu equivalent : skype
Skype
sudo aptitude install skype
Access it through Applications &#8594; Internet &#8594; Skype.
16 – Viewing PDF files
Windows equivalent : Adobe Reader
Ubuntu equivalent : Adobe Reader
Adobe Reader
sudo aptitude install acroread acroread-fonts
Access it through Applications &#8594; Office &#8594; Adobe Reader.
17– Adobe Air
wget [http://airdownload.adobe.com/air/lin/download/latest/AdobeAIRInstaller.bin](http://airdownload.adobe.com/air/lin/download/latest/AdobeAIRInstaller.bin)
chmod +x ./AdobeAIRInstaller.bin
sudo ./AdobeAIRInstaller.bin
Access it through Applications &#8594; Accessories &#8594; Adobe Air Application Installer.
18 – Music / MP3 / OGG Players
Windows equivalent : iTunes, Winamp
Ubuntu equivalent : Rhythmbox, Banshee, Amarok
Rhythmbox
sudo aptitude install rhythmbox
Access it through Applications &#8594; Sound & Video &#8594; Rhythmbox Music Player.
Banshee
sudo aptitude install banshee banshee-extension-ubuntuonemusicstore libappindicator0-cil banshee-extension-appindicator banshee-extension-lyrics banshee-extension-mirage
Access it through Applications &#8594; Sound & Video &#8594; Banshee Media Player.
Amarok
sudo aptitude install amarok amarok-common
Access it through Applications &#8594; Sound & Video &#8594; Amarok.
19– Hard Disk Partitions Manager
Windows equivalent : Symanted Partition Magic
Ubuntu equivalent : GParted
GParted
sudo aptitude install gparted ntfsprogs menu ntfs-config
Access it through System &#8594; Administration &#8594; Partition Editor.
20 – Vector Graphics Editor
Windows equivalent : Adobe Illustrator
Ubuntu equivalent : Inkscape
Inkscape
sudo aptitude install inkscape
Access it through Applications &#8594; Graphics &#8594; Inkscape Vector Graphics Editor.
21 – Image Editor
Windows equivalent : Adobe Photoshop, Paint.Net
Ubuntu equivalent : GIMP
GIMP
Add the launchpad repository :
sudo add-apt-repository ppa:matthaeus123/mrw-gimp-svn && sudo aptitude update
Then install it with the following command :
sudo aptitude install gimp gimp-data gimp-plugin-registry gimp-data-extras
Access it through Applications &#8594; Graphics &#8594; GIMP Image Editor.
PINTA
Add the launchpad repository :
sudo add-apt-repository ppa:moonlight-team/pinta && sudo aptitude update
Then install it with the following command :
sudo aptitude install pinta
Access it through Applications &#8594; Graphics &#8594; Pinta Image Editor.
22 – 3D Graphics Applications
Windows equivalent : 3D Studio MAX
Ubuntu equivalent : Blender
Blender
sudo aptitude install blender
Access it through Applications &#8594; Graphics &#8594; Blender (windowed).
23 – Simple Yet Advanced Text Editor
Windows equivalent : Notepad ++
Ubuntu equivalent : GEdit
GEdit
sudo aptitude install gedit gedit-plugins
Access it through Applications &#8594; Accessories &#8594; Text Editor.
24 – Office Applications
Windows equivalent : Microsoft Office
Ubuntu equivalent : OpenOffice
OpenOffice
sudo aptitude install openoffice.org
Access it through Applications &#8594; Office
25 – Microsoft Visio
Windows equivalent : Microsoft Visio
Ubuntu equivalent : Dia
Dia
sudo aptitude install dia
Access it through Applications &#8594; Graphics &#8594; Dia Diagram Editor
26 – Microsoft Project
Windows equivalent : Microsoft Project
Ubuntu equivalent : OpenProj
OpenProj
wget [http://nchc.dl.sourceforge.net/sourceforge/openproj/openproj_1.4-2.deb](http://nchc.dl.sourceforge.net/sourceforge/openproj/openproj_1.4-2.deb) && sudo dpkg -i openproj_1.4-2.deb
Access it through Applications &#8594; Office &#8594; OpenProj
27 – Development IDE
Windows equivalent : Dreamweaver
Ubuntu equivalent : Quanta, Kompozer, NetBeans
Quanta
sudo aptitude install quanta
Access it through Applications &#8594; Programming &#8594; Quanta Plus
Komposer
sudo aptitude install kompozer nvu
Access it through Applications &#8594; Internet &#8594; Kompozer
NetBeans
sudo aptitude install netbeans
Access it through Applications &#8594; Programming &#8594; NetBeans IDE
28 – Source Control Management
Windows equivalent : TortoiseSVN
Ubuntu equivalent : RabbitVCS
RabbitVCS
Add the launchpad repository :
sudo add-apt-repository ppa:rabbitvcs/ppa && sudo aptitude update
Then install it :
sudo aptitude install rabbitvcs-nautilus
killall nautilus
Right Click on any folder or file and access the RabbitVCS submenu
29 – Graphical FTP clients
Windows equivalent : CuteFTP, SmartFTP
Ubuntu equivalent : FileZilla
FileZilla
This is great FTP program, very complete, in my opinion, the best one for linux.
On the terminal type:
sudo aptitude install filezilla filezilla-common
Access it through Applications &#8594; Internet &#8594; FileZilla FTP Client.
30 – P2P Clients / Servers, File Sharing
Windows equivalent : utorrent, azureus, emule
Ubuntu equivalent : Deluge, azureus, amule
Bittorent clients
Deluge (written in python)
Add the launchpad repository :
sudo add-apt-repository ppa:deluge-team/ppa && sudo aptitude update
Then install it :
sudo aptitude install deluge-torrent
Access it through Applications &#8594; Internet &#8594; Deluge Torrent.
Azureus: Uses Java to run, very complete but a bit heavy
sudo aptitude install azureus
Access it through Applications &#8594; Internet &#8594; Azureus.
Emule Donkey Clients
Amule
Add the launchpad repository :
sudo add-apt-repository ppa:happyaron/amule-dlp && sudo aptitude update
Then install it with the following command :
sudo aptitude install amule-dlp amule-dlp-gnome-support amule-dlp-utils-gui amule-dlp-daemon
Access it through Applications &#8594; Internet &#8594; aMule.
31 – Programs for CD burning with GUI
Windows equivalent : Nero, Roxio Easy CD Creator
Ubuntu equivalent : K3b, Brasero
K3b
Nero is available for linux,but its not free.A trial is available for 1 month usage and later it asks or activation code.But K3B is as good as Nero.Have a good feature set as Nero.
sudo aptitude install k3b k3b-data libk3b6
Access it through Applications &#8594; Sound & Video &#8594; K3B.
Brasero (installed by default in Lucid)
sudo aptitude install brasero
Access it through Applications &#8594; Sound & Video &#8594; Brasero Disc Burning .
32 – Mountings ISO files
Windows equivalent : Alcohol
Ubuntu equivalent : acetoneiso
Acetoneiso
The best one for linux ACETONEISO, which is similar to ALCOHOL in windows
its supports almost all formats. AcetoneISO is CD/DVD image manipulator for Linux.Using this tool it is very easy to Mount and Unmount ISO,MDF,NRG Images . I dont think its available in ubuntu repository.
sudo aptitude install libksba8 libenca0 libtwolame0 fuseiso kommander p7zip-full gnupg-agent gnupg2 pinentry-qt mencoder cdrdao && wget [http://darkstar.ist.utl.pt/getdeb/ubuntu/jaunty/ac/acetoneiso_2.1.1-1~getdeb1_i386.deb](http://darkstar.ist.utl.pt/getdeb/ubuntu/jaunty/ac/acetoneiso_2.1.1-1~getdeb1_i386.deb) && sudo dpkg -i acetoneiso_2.1.1-1~getdeb1_i386.deb
33 – Install Vista like gadgets.
Windows equivalent : Vista Sidebar
Ubuntu equivalent : google-gadgets
Google gadgets
sudo aptitude install google-gadgets-gtk
This will complete the installation.
Now press Alt+F2, and type “ggl-gtk” to start them. You should see a small icon show up in your system tray, and a sidebar. Right click on any of them and select ‘Add Gadgets’ to show a menu. If you’d like to have Google Gadgets start automatically, go to System – Preferences – Session, click ‘Add’, paste ‘Google Gadgets’ for the name and ‘ggl-gtk’ for the command. Click OK and Close, and you’re good to go.
34 – Google Desktop
Google Desktop allows one to full text search of a user’s e-mail, computer files, music, photos, chat, and Web pages viewed,OpenOffice documents , PDF files and more .
Now similar tools already existed on Linux like beagle (supported by novell ) , meta tracker etc . However Google Desktop search is not based on any of these tools and uses its proprietary algorithms to search for files on the computer ,also being 1.0 release and more stable then these products it could be preferred over tools like beagle .
To install Google Desktop Search type the following command in the terminal window : -
sudo aptitude install google-desktop-linux
Access it through Applications &#8594; Google Desktop &#8594; Google Desktop
Now after choosing appropriate option through Applications &#8594; Google Desktop &#8594; Google Desktop Preferences, you would find Google Desktop icon in the bar at the top of the screen , now it would automatically scan and index files on computer and store it in local database which could be searched using web browser .
35 – Photo Management
Google Picasa
Google Picasa is an extremely professional good looking photo management application available on Windows ,Linux and Mac OS. Now Google Picasa has a number of features that many photo management software on Linux dont have further Google Picasa looks very user friendly as compared to similar open source application available on linux . Now Google Picasa for Linux is not a native linux application but runs on Linux thru application layer called wine which allows many windows application to run flawlessly on Linux.
Now to install Google – Picasa type the following command in the terminal window
wget [http://dl.google.com/linux/deb/pool/non-free/p/picasa/picasa_3.0-current_i386.deb](http://dl.google.com/linux/deb/pool/non-free/p/picasa/picasa_3.0-current_i386.deb) && sudo dpkg -i picasa_3.0-current_i386.deb
Access it through Applications &#8594; Graphics &#8594; Picasa &#8594; Picasa
36 – Map Viewing and Management
Google Earth
To install Google Earth type the following command in the Terminal Window.
sudo aptitude install googleearth
After downloading is over you will get a screen like this press ¨Yes¨ to accept the license agreement and complete software installation.
Now you can launch Google Earth from Application &#8594; Internet &#8594; Google Earth
37 – Gmail Notification
Checkgmail
If you would like to get notified when you have a new mail in your google mail account, checkgmail is for you. To install Checkgmail type the following command in the Terminal Window.
sudo aptitude install checkgmail
Now you can launch it from Application &#8594; Internet &#8594; CheckGmail
38 – Configure Firewall
If you are concern about your security, then it is pertinent that you activate the firewall and prevent any unauthorized access to your computer.
UFW is installed by default, but if you need a graphical interface, install GUFW.
sudo aptitude install gufw
39– Gnome Do
Gnome Do is a small application that allows you to search and do things faster and more efficiently in your Ubuntu machine. It is similar to QuickSilver in Mac and Launchy in Windows. For those who have not tried Gnome Do before, it might take some time for you to get used to it. But once you’re hooked to it, there will be no turning back for you.Gnome Do also comes with a dock interface that you can use it like any other docks.
sudo aptitude install gnome-do
Now you can launch it from Application &#8594; Accessories &#8594; Gnome Do
40 – Ubuntu Tweak
Ubuntu Tweak allows you to tweak your system settings, all in one place. You can install new applications, customize your desktop settings, configure your startup applications, changing the system filetype association and many more tweaks in this single application.
Add the launchpad repository :
sudo add-apt-repository ppa:ubuntu-tweak-testing/ppa && sudo aptitude update
Then install it with the following command :
sudo aptitude install ubuntu-tweak
Then access it through Applications &#8594; System Tools &#8594; Ubuntu Tweak
App Runner
App Runner is a small open source utility that makes it very easy to run any type of program/executable/script on any distro/OS that uses the nautilus file manager: Debian/Ubuntu/Super OS/Fedora/etc
wget [http://hacktolive.org/files/app_runner/App_Runner_0.2.deb](http://hacktolive.org/files/app_runner/App_Runner_0.2.deb) && sudo dpkg -i App_Runner_0.2.deb
Then right-click the file -> Scripts -> Run This App or Run This App (root)
```
******************************
if i were to add what i wanted from the above mentioned list.. then added crossover office 9, to run the windows apps I like (which i cant do on arch 64 , unless i want to use arch 32 and lose over a gig of ram
I think it would be fast, small foot print.. then since I do like Kde. just add kde-base and a bare bones kde desktop (since I'll already have everything I want from the above mentioned install..) 

this along with a few speed tweaks, swapiness, internet tweaks, OS tweaks, etc..  and with this being a 3 year desktop LTS, (almost the same as rolling release) wouldnt this seem like a nice fast system??
any opinions..  just fishing for opinions.. 
thanks for the long read and your time..

---

### Post by humbug01 on 2010-06-18
I have been tempted from time to time to try Arch because I really like a lean, fast system and don't use many (most?) of the apps installed in the canned distros. I have found the minimal install to be an ideal alternative for me and the reason I stick to Ubuntu (though this great forum is another important reason).

I have just completed installing Lucid 64bit on my desktop (for home) and Lenovo T-61 laptop (for work); with only a few minor tweaks everything is up and running great. I had Jaunty on both machines before and dual booted. On the laptop I no longer dual-boot but run Wine and VirtualBox for one each app that I need for work that have no Linux equivalent. No problems at all.

I just bought a Samsung netbook and installed the 32bit version with alternate install and gnome as well. Regular Ubuntu is supposed to be too "heavy" for a netbook but not when you leave out unneeded stuff like samba etc. that it doesn't really need.

A little over a year ago, I also did a minimal install on an older HP laptop for my dad (with XFCE as the desktop). Almost all he really uses it for is email and a little web browsing. It was easy to set up as a dedicated email/Firefox machine. Works great for him.

All of this is for the gnome version, but you start out the same with the CLI. And apt/synaptic is the common heart of all *buntus and really makes setup and use of this system a snap.

If still in doubt, try it out on a virtual machine. And check out a couple threads on this forum for "minimal" or "alternate" install that have some helpful tips. Go for it!

---

### Post by dabl on 2010-06-18
I tried Arch a couple years ago.  It reminded me of an Erector Set (a toy for boys in the 1950s).  A box full of all the mechanical parts you might need to build whatever you fancy, including some of the tools required for assembly.  Nothing there that actually works on its own, mind you, but all the potential to make something very interesting and useful.

Anyway, I've long since settled upon sidux as my preferred rolling release, and Kubuntu as my second OS, because it sometimes provides even newer software than Debian Sid.

As for supporting Windows apps, I'm long since sold on VMware Player. I have a Win XP VM and recently built a 40GB Win 7 VM which is working great.  I need to run a proprietary database written for Windows in MS Visual FoxPro -- a true resource hog.  I spent a weekend proving that it won't work on Wine, and haven't bothered with Wine ever since.  So I have a pretty beefy desktop rig to run that on, but the Windows stuff only lives on the VM, not on a real hard drive.  Works good -- no need for a real Windows installation at all.

---

### Post by ssri on 2010-06-18
> **binskipy2u said:**
> I am currently using ARCH 64bit, it's a rolling release..  works well.. but there is no wine for 64bit.. and it takes alot of work to get it working.. took months of reading, and trial and error.. but what I was wondering is..

Huh?  It is fairly easy getting 32bit wine to install on arch64.  The trick is to install wine from the Arch User Repository (AUR) using a tool that can grab pkgbuilds from aur.  Yaourt is a pretty popular tool for it.  After installing yaourt simply type in:

```
yaourt -S bin32-wine
```

Then it will automagically download the source and wine's 32bit dependencies and compile 32bit wine on your arch64 install.  I can run exact audio copy and mp3tag under wine perfectly.

---

### Post by binskipy2u on 2010-06-18
SSRE.. i did do that.. but ended up with upgrade issues and some dependency hell..  but I will try it again, maybe it was because i installed wine-doors..and that added to the headache, so i'll just install wine, see what happens..
thanks

---

### Post by ssri on 2010-06-18
All I did was install wine and winetricks, so far so good.  Sure there was quite a number of dependencies that had to be installed (see bin32-wine's PKGBUILD), but so long as they install correctly, then you should not have problems compiling wine.  That said, after my wine compile finished and worked perfectly with the software I needed to run on it, I simply held the package from being upgraded.  I always viewed wine as a bit capricious with some of my windows software version to version.

---

