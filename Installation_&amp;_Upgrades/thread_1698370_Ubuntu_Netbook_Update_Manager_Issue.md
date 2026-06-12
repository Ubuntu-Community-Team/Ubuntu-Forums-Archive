---
title: "Ubuntu Netbook Update Manager Issue"
date: 2011-03-02
forum: Installation &amp; Upgrades
---

### Post by swapnilnarendra on 2011-03-02
Hi, 

I am using an Acer Aspire ONE netbook running Ubuntu Netbook Remix 10.10. I love it and dont have any problems except for this one with the upgrade manager.

Recently I have been encountering this error while the upgrade manager shows up. I am unable to get rid of this issue and its messing up with my ability to upgrade or install new programs on my netbook. I am unable to upgrade new programs or softwares.

I am posting screenshots depicting the issue. 

Here is the first error, which comes as soon as the Update Manager shows up:
[http://twitpic.com/45ab8n](http://twitpic.com/45ab8n)

I choose 'Close' and the upgrade starts. As soon as it finishes, it give me this error:
[http://twitpic.com/45apil](http://twitpic.com/45apil)

PS: You can see that the other error which is unchecked is regarding WINE. I am unable to check or remove it.

After this, when I closed this error dialogue. It came back to the step one (except this time there was only one update showing, yes it was the WINE update):
[http://twitpic.com/45aq8o](http://twitpic.com/45aq8o)

So this time, I clicked on 'Partial Upgrade, and it keeps running like it is trying to upgrade itself. After waiting patiently for more than 30 minutes, it suddenly disappeared like a bubble in the soap water. This is how it looked when it was working:
[http://twitpic.com/45ar1z](http://twitpic.com/45ar1z)

And when I try to start the update manager, it takes me back to square one. That it, the very first step of this vicious circle.

Also, here is what I get when I try to install any program in my netbook. This error message is same with both 'Ubuntu Software Center' and 'Terminal'. Here is the screenshot. You can read the error message down in the terminal window:
[http://twitpic.com/45arx4](http://twitpic.com/45arx4)


So this is my problem. Besides this, my netbook is working brilliantly. I am happy with it and would like to get this issue fixed. 

Now you may want to ask me, "If I remember about any of my recent upgrade failures?"
- "Well, to be honest, I dont think so. But still I dont know as most of the time, I upgrade it when I went to bed. I plug my netbook in power and start the upgrade. When I wake up in the morning, Tada - updated computer."


Please please please, help me with this. This is both annoying and bugging me.

Thanks in advance, waiting for replies :)

---

### Post by swapnilnarendra on 2011-03-02
I still havent got any reply on this issue :P
But something happened in the meantime. As you know there was a little red triangle icon (caution sign) in the upper panel. Showing me that there was some issue with the upgrade. I right clicked on it and is gave me an option to install all upgrades. I clicked on that.

Well it worked like a charm and it installed all the updates. Even that WINE update. It completed all the updates and told me that my netbook is up to date. I was so happy :D

But suddenly I noticed that my wireless network was disabled and no matter how much I tried to enable it, it didnt work. So I thought that it was some issue because of the update and required a restart and so I restarted my netbook.

MY SYSTEM CRASHED. It gave me the error screen and said that the low graphic mode will be running. No option for troubleshooting or recovery worked. And so I had to reinstall Ubuntu Netbook Remix 10.04 again. Thankfully, I had the my data backed up. So I reinstalled it again and now its a fresh copy of Ubuntu UNR 10.04 but when again I tried to upgrade it to 10.10, it again gave me the same error message that my previous upgrade failed.

Now I havent installed anything on this baby and so am asking, "Is this an issue with the server or the distro itself?"

Please help !!!

---

### Post by Old_Grey_Wolf on 2011-03-02
> **swapnilnarendra said:**
> And so I had to reinstall Ubuntu Netbook Remix 10.04 again. Thankfully, I had the my data backed up. So I reinstalled it again and now its a fresh copy of Ubuntu UNR 10.04 but when again I tried to upgrade it to 10.10, it again gave me the same error message that my previous upgrade failed.

If you are reinstalling your OS you may want to download the 10.10 UNR and burn it to a CD/USB rather that upgrade to it from 10.04.

---

### Post by swapnilnarendra on 2011-03-03
Well thats what I am going to do now. But seriously, what just happened in that upgrade. I would like to know if it was WINE which crashed my system or anything else ?

Because of things like this you have to be very careful while doing a few things to your ubuntu.

---

### Post by Old_Grey_Wolf on 2011-03-03
> **swapnilnarendra said:**
> Well thats what I am going to do now. But seriously, what just happened in that upgrade. I would like to know if it was WINE which crashed my system or anything else ?

Because of things like this you have to be very careful while doing a few things to your ubuntu.

There is not enough information in the posts to answer your question. You would have to get it back in the state it was in. Then people would have to ask you to enter commands and post the results in order to find out what was wrong. 

My guess is that there is something in your backup that is not compatible with 10.10. 

The problem that caused you to have to use your backup probably can't be recreated.

---

### Post by swapnilnarendra on 2011-03-03
Well it wasnt possible as the system went down after upgrade.. but till the time it was up I didnt get any reply here :P

However, next time onwards, I will make sure not to install the upgrades if this happens and also hope that I get response in time :)

Now I have installed a fresh copy of UNR 10.10 and its working fine as of now.

Thanks for your help mate :)

---

### Post by swapnilnarendra on 2011-03-04
alright.. here is another problem..
I am trying to upgrade and install a few things on my UNR 10.10 but I am getting a few errors;
1. it asks me to check my connection, thought I am PRETTY SURE that my connection is fine.
2 Gives me this error: (while installing digiKam)
[http://twitpic.com/45y7l1](http://twitpic.com/45y7l1)

The details of the code are given below:
```
akonadi-server digikam-data docbook-xsl docbook-xsl-doc-html hal hal-info icoutils kdebase-runtime kdebase-runtime-data kdegraphics-libs-data kdelibs-bin kdelibs5-data kdelibs5-plugins kdepim-runtime kdepimlibs-kio-plugins kdoctools kubuntu-debug-installer libakonadi-kabc4 libakonadi-kcal4 libakonadi-kde4 libakonadi-kmime4 libakonadiprivate1 libattica0 libboost-program-options1.42.0 libclucene0ldbl libdbusmenu-qt2 libhal-storage1 libiodbc2 libkabc4 libkatepartinterfaces4 libkcal4 libkdcraw8 libkde3support4 libkdecore5 libkdesu5 libkdeui5 libkdewebkit5 libkdnssd4 libkexiv2-8 libkfile4 libkhtml5 libkimap4 libkio5 libkipi7 libkjsapi4 libkjsembed4 libkldap4 libkmediaplayer4 libkmime4 libknewstuff3-4 libknotifyconfig4 libkntlm4 libkparts4 libkpimutils4 libkpty4 libkresources4 libkrosscore4 libkrossui4 libktexteditor4 libkutils4 liblensfun-data liblensfun0 libmailtransport4 libmarblewidget10 libmicroblog4 libnepomuk4 libnepomukquery4a libphonon4 libplasma3 libpolkit-qt-1-0 libqapt-runtime libqapt1 libqca2 libqt4-designer libqt4-network libqt4-opengl libqt4-qt3support libqt4-script libqt4-sql libqt4-sql-mysql libqt4-sql-sqlite libqt4-svg libqtwebkit4 libreadline5 libsolid4 libsoprano4 libssh-4 libstreamanalyzer0 libstreams0 libthreadweaver4 libvirtodbc0 libxcb-shape0 libxine1 libxine1-bin libxine1-console libxine1-misc-plugins libxine1-x marble-data marble-plugins odbcinst odbcinst1debian2 oxygen-icon-theme phonon phonon-backend-xine plasma-scriptengine-javascript qapt-batch shared-desktop-ontologies smartdimmer soprano-daemon ttf-dejavu virtuoso-minimal virtuoso-opensource-6.1-bin virtuoso-opensource-6.1-common
```

3. Error while updating:
[http://twitpic.com/45ycbf](http://twitpic.com/45ycbf)

Details of the error are given below:
```
alsa-utils app-install-data-partner apparmor apparmor-utils appmenu-gtk apport apport-gtk bash-completion brasero-common bsdutils computer-janitor computer-janitor-gtk dkms empathy empathy-common evolution evolution-common evolution-data-server evolution-data-server-common evolution-exchange evolution-plugins gcalctool gconf-defaults-service gconf2 gconf2-common gdb gdm-guest-session gnome-keyring gnome-settings-daemon gnome-system-tools gvfs gvfs-backends gvfs-fuse gwibber gwibber-service humanity-icon-theme ibus ibus-gtk indicator-appmenu indicator-sound initscripts jockey-common jockey-gtk language-pack-en language-pack-gnome-en libapparmor-perl libapparmor1 libasound2 libblkid1 libbrasero-media1 libc-bin libc-dev-bin libc6 libc6-dev libcairo2 libcamel1.2-14 libdrm-intel1 libdrm-nouveau1 libdrm-radeon1 libdrm2 libebackend1.2-0 libebook1.2-9 libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-7 libedataserver1.2-13 libedataserverui1.2-8 libegroupwise1.2-13 libevolution libgconf2-4 libgcr0 libgdata-google1.2-1 libgdata1.2-1 libgexiv2-0 libglib2.0-0 libglib2.0-data libgp11-0 libgpod-common libgpod4 libgudev-1.0-0 libgvfscommon0 libibus2 libldap-2.4-2 libnautilus-extension1 libpam-gnome-keyring libparted0debian1 libplymouth2 libpst4 libpulse-browse0 libpulse-mainloop-glib0 libpulse0 libpurple-bin libpurple0 libsqlite3-0 libsyncdaemon-1.0-1 libudev0 libunity0 libutouch-grail1 libuuid1 libvte-common libvte9 light-themes linux-firmware media-player-info mount nautilus nautilus-data nautilus-sendto-empathy nautilus-share nvidia-96-modaliases openssh-client parted plymouth plymouth-label plymouth-theme-ubuntu-logo plymouth-theme-ubuntu-text pulseaudio pulseaudio-esound-compat pulseaudio-module-bluetooth pulseaudio-module-gconf pulseaudio-module-x11 pulseaudio-utils python python-apport python-apt python-cupshelpers python-ibus python-minimal python-papyon python-problem-report python-ubuntuone-client python-vte rhythmbox rhythmbox-plugin-cdrecorder rhythmbox-plugins rhythmbox-ubuntuone-music-store simple-scan software-center ssh-askpass-gnome system-config-printer-common system-config-printer-gnome system-config-printer-udev sysv-rc sysvinit-utils tar telepathy-haze tomboy ttf-ubuntu-font-family ubufox ubuntu-docs ubuntu-netbook ubuntu-sso-client ubuntuone-client ubuntuone-client-gnome udev unity update-inetd update-manager update-manager-core upstart util-linux uuid-runtime xdg-utils xkb-data xserver-common xserver-xorg-core xserver-xorg-input-evdev xserver-xorg-video-intel xul-ext-ubufox
```

whats up with it and what should I do ? any idea ?

---

### Post by Old_Grey_Wolf on 2011-03-04
The error "Requires installation of untrusted packages" means that you need the GPG keys to download the packages. GPG keys are used to verify that the packages you are downloading are authentic copies.

If you enter this command and post the output, I will be able to tell you how to install the GPG keys from Ubuntu's key server.
```
sudo apt-get update
```

---

### Post by swapnilnarendra on 2011-03-05
Here is the output of the command you asked me to enter:
```
swapnil@iva-swapo-netbook:~$ sudo apt-get update
[sudo] password for swapnil: 
Get:1 http://extras.ubuntu.com maverick Release.gpg [72B]                                                            
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en                                                    
Hit http://archive.canonical.com maverick Release.gpg                                                                
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en                                             
Hit http://security.ubuntu.com maverick-security Release.gpg                                                         
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en                                         
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en_IN                                      
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_IN                                                 
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en_IN                                      
Hit http://archive.canonical.com maverick Release.gpg                                                            
Ign http://archive.canonical.com/ maverick/partner Translation-en                                                
Ign http://archive.canonical.com/ maverick/partner Translation-en_IN                                             
Hit http://extras.ubuntu.com maverick Release                                                                    
Hit http://archive.canonical.com maverick Release                                                                    
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en                                   
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_IN                                
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en                                   
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_IN                                
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en                                     
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_IN                                  
Hit http://security.ubuntu.com maverick-security Release                                                             
Hit http://archive.canonical.com maverick Release                                                                    
Hit http://extras.ubuntu.com maverick/main Sources                                                                   
Hit http://security.ubuntu.com maverick-security/main Sources                                                        
Hit http://archive.canonical.com maverick/partner Sources                                                            
Hit http://archive.canonical.com maverick/partner i386 Packages                                                      
Hit http://extras.ubuntu.com maverick/main i386 Packages                                                             
Hit http://security.ubuntu.com maverick-security/restricted Sources                                                  
Hit http://security.ubuntu.com maverick-security/universe Sources                                                    
Hit http://security.ubuntu.com maverick-security/multiverse Sources                                                  
Hit http://security.ubuntu.com maverick-security/main i386 Packages                                                  
Hit http://security.ubuntu.com maverick-security/restricted i386 Packages                                            
Hit http://security.ubuntu.com maverick-security/universe i386 Packages                                              
Hit http://security.ubuntu.com maverick-security/multiverse i386 Packages                                            
Hit http://archive.canonical.com maverick/partner i386 Packages                                                      
Get:2 http://dl.google.com stable Release.gpg [189B]                                                                 
Ign http://dl.google.com/linux/deb/ stable/main Translation-en
Get:3 http://in.archive.ubuntu.com maverick Release.gpg [198B]
Ign http://dl.google.com/linux/deb/ stable/main Translation-en_IN
Get:4 http://dl.google.com stable Release [2,544B]
Get:5 http://dl.google.com stable/main i386 Packages [1,082B]                                                        
Ign http://in.archive.ubuntu.com/ubuntu/ maverick/main Translation-en                                                
Ign http://in.archive.ubuntu.com/ubuntu/ maverick/main Translation-en_IN                                             
Ign http://in.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en
Ign http://in.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_IN
Ign http://in.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en
Ign http://in.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_IN
Ign http://in.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en
Ign http://in.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_IN
Get:6 http://in.archive.ubuntu.com maverick-updates Release.gpg [198B]
Ign http://in.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en                                        
Ign http://in.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_IN                                     
Ign http://in.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en
Ign http://in.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_IN
Ign http://in.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Ign http://in.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_IN
Ign http://in.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
Ign http://in.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_IN
Hit http://in.archive.ubuntu.com maverick Release
Get:7 http://in.archive.ubuntu.com maverick-updates Release [31.4kB]          
Hit http://in.archive.ubuntu.com maverick/main Sources                                                               
Hit http://in.archive.ubuntu.com maverick/restricted Sources
Hit http://in.archive.ubuntu.com maverick/universe Sources
Hit http://in.archive.ubuntu.com maverick/multiverse Sources
Hit http://in.archive.ubuntu.com maverick/main i386 Packages
Hit http://in.archive.ubuntu.com maverick/restricted i386 Packages
Hit http://in.archive.ubuntu.com maverick/universe i386 Packages
Hit http://in.archive.ubuntu.com maverick/multiverse i386 Packages
Get:8 http://in.archive.ubuntu.com maverick-updates/main Sources [89.7kB]
Get:9 http://in.archive.ubuntu.com maverick-updates/restricted Sources [778B]                                        
Get:10 http://in.archive.ubuntu.com maverick-updates/universe Sources [35.8kB]                                       
Get:11 http://in.archive.ubuntu.com maverick-updates/multiverse Sources [1,498B]                                     
Get:12 http://in.archive.ubuntu.com maverick-updates/main i386 Packages [242kB]                                      
Get:13 http://in.archive.ubuntu.com maverick-updates/restricted i386 Packages [1,797B]                               
Get:14 http://in.archive.ubuntu.com maverick-updates/universe i386 Packages [108kB]                                  
Get:15 http://in.archive.ubuntu.com maverick-updates/multiverse i386 Packages [2,834B]                               
Fetched 519kB in 6min 50s (1,263B/s)                                                                                 
Reading package lists... Done

```

Also, I think I shud tell u that in order to try a workaround I checked all the options in other softwares tab. It did help at that moment and I was able to upgrade. However,I am still not able to install digiKam.. getting the same error, mentioned previously.

Shud I uncheck some of them or are they fine the way they are ?

---

### Post by Old_Grey_Wolf on 2011-03-05
Enter this command and post the output if there is an error. ```
sudo apt-get install digikam
```The command will try to install digikam. If it can't install it, the error should tell us what you need to do to fix it.

---

### Post by Old_Grey_Wolf on 2011-03-05
> **swapnilnarendra said:**
> Shud I uncheck some of them or are they fine the way they are ?

If any of them have (Source Code) at the end, you can uncheck those. I doubt you need the source code.

---

### Post by swapnilnarendra on 2011-03-06
Well I tried this command way before you told me and it game an error about some package missing. It also asked me to run a '--fix-install' command and to try again. So first I resolved my updation issue by checking all the software options in the update manager's settings. 

So after the update was done, I tried again and it said that it was unable to fetch some files. Maybe it was something with the internet, I am not sure. So I again tried using the Software Center and it worked this time. So now I have my system up-t0-date and 'digiKam' installed on it. But one thing which I am not able to understand is - Why I am not able to install Picasa in my system. Whenever I open the package installer, it shows that Picasa is already installed. Even when I try to reinstall, it runs its course and says that it has been installed. Though it doesnt show in my system anywhere.

So now I have 2 questions;

1. Why Picasa is not showing in my system ?
2. Should I leave all those options checked in my software sources options (in my update manager settings) ?? 
(the ones with the source codes are unchecked) :D

Please help :)

---

### Post by Old_Grey_Wolf on 2011-03-06
For Picasa, make sure you have the key:
```
wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | apt-key add -

```
You will need to add Picasa to your sources.list:```
sudo gedit /etc/apt/sources.list

```
Look through you sources.list to make sure you do not already have Picasa in it already. If you already have one of the lines below don't add a new one.

Add one of the following lines and save the file.
For stable repo:
```
deb http://dl.google.com/linux/deb/ stable non-free
```
For testing repo:
```
deb http://dl.google.com/linux/deb/ testing non-free
```

Then install Picasa:
```
sudo apt-get update
sudo apt-get install picasa
```

If you get an error, post it back here.

---

### Post by swapnilnarendra on 2011-03-06
Here is the terminal data:

first I checked the key (I hope this is how it is supposed to be done)
```
swapnil@iva-swapo-netbook:~$ wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | apt-key add -
OK
```


then I looked for the source in the list file.. it wasnt there so I added it.

and after that I ran:
```
sudo apt-get update
```

and then I tried to install picasa:
```
sudo apt-get install picasa
```


here is what I got:
```

swapnil@iva-swapo-netbook:~$ sudo apt-get install picasa
Reading package lists... Done
Building dependency tree       
Reading state information... Done
picasa is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

```

picasa is still not showing in the menu !
please correct me if you think I didnt perform any step in the correct way.

---

### Post by Old_Grey_Wolf on 2011-03-06
Do you have WINE installed?

Start a new thread about your problems with Picasa. You have changed the topic in this one so many times that I am the only person responding to the thread.

---

### Post by swapnilnarendra on 2011-03-06
Nope, I dont have WINE installed... and I dont think that no one has even noticed the topic changed... you are the only person who has been helping me here :)


alrightos..  here is the new thread:)
[http://ubuntuforums.org/showthread.php?p=10530070#post10530070](http://ubuntuforums.org/showthread.php?p=10530070#post10530070)

Also, should I marke this thread 'RESOLVED'or what ?
As I dont know what caused that mess but I have moved on and its not there anymore :s

---

