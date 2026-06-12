---
title: "KDE desktop startup"
date: 2007-09-10
forum: Installation &amp; Upgrades
---

### Post by Challengerquay on 2007-09-10
Hi all,

Installed KDE desktop on my Ubuntu distro, can't get it to open from the options screen at startup.
Message from system is: could not start ksmserver, check your installation!

Have un-installed KDE and re-installed it with no difference observed.

Also a number of packages do not run, but as I can only operate in GNOME, this could be an effect. At the same time I keep getting the following message when opening a KDE package:
 check if decopserver is running.

Any help would be appreciated, as I am on the verge of going to another distro.

:confused:

---

### Post by Pumalite on 2007-09-10
Go to terminal and: sudo dcopserver
Post output

---

### Post by Challengerquay on 2007-09-10
Hi Pumlite,

Tried that here are the results, does this mean there is a part of a package missing from the build?

mike@Mikes Desktop:~$ sudo dcopserver
Password:
/usr/bin/iceauth: /tmp/dcopPfMg8b:1:  bad "add" command line
/usr/bin/iceauth: /tmp/dcopPfMg8b:2:  bad "add" command line
DCOPClient::attachInternal. Attach failed Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
ICE Connection rejected!

DCOPClient::attachInternal. Attach failed Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
DCOPServer self-test failed.
ICE Connection rejected!

Or just a command line needing changing?

:confused:

mike@Mikes Desktop:~$

---

### Post by Pumalite on 2007-09-10
Go to Places>Home>View>Show Hidden Files. Locate .DCOPserver_username-desktop__0 and erase what's in there, save exit and reboot and lets see what happens.
If it doesn't work, then throw the file to the trash, reboot and let the system regenerate the file.

---

### Post by Challengerquay on 2007-09-10
Hi Pumalite,

File does not seem to exist on the system.

](*,)

---

### Post by Pumalite on 2007-09-10
It has to be in your /home/<username> . Can be seen after you go to 'VIEW>Show Hidden Files' and go to the end because it's not a folder, it's a text file ( they are at the end )

---

### Post by Challengerquay on 2007-09-10
Hi Pumalite

List of files in that directory

/home/mike/Desktop
/home/mike/Examples
/home/mike/firestarter-1.0.3
/home/mike/.beagle
/home/mike/.config
/home/mike/.cups
/home/mike/.debtags
/home/mike/.evolution
/home/mike/.fontconfig
/home/mike/.gconf
/home/mike/.gconfd
/home/mike/.gimp-2.2
/home/mike/.gnome
/home/mike/.gnome2
/home/mike/.gnome2_private
/home/mike/.gstreamer-0.10
/home/mike/.icons
/home/mike/.kde
/home/mike/.kpackage
/home/mike/.local
/home/mike/.macromedia
/home/mike/.mcop
/home/mike/.metacity
/home/mike/.mozilla
/home/mike/.nautilus
/home/mike/.openoffice.org2
/home/mike/.qt
/home/mike/.scim
/home/mike/.themes
/home/mike/.thumbnails
/home/mike/.tomboy
/home/mike/.Trash
/home/mike/.tsclient
/home/mike/.update-manager-core
/home/mike/.update-notifier
/home/mike/.wapi
/home/mike/find
/home/mike/Giant-Squid-Astern-Sir-BIG.jpg
/home/mike/output.pdf
/home/mike/wallpaper2.zip
/home/mike/.aeeinfo
/home/mike/.bash_history
/home/mike/.bash_logout
/home/mike/.bashrc
/home/mike/.dmrc
/home/mike/.esd_auth
/home/mike/.gksu.lock
/home/mike/.gtk-bookmarks
/home/mike/.gtkrc-1.2-gnome2
/home/mike/.gtkrc-2.0-kde
/home/mike/.ICEauthority
/home/mike/.kderc
/home/mike/.profile
/home/mike/.recently-used
/home/mike/.recently-used.xbel
/home/mike/.sudo_as_admin_successful
/home/mike/.tomboy.log
/home/mike/.viminfo
/home/mike/.Xauthority
/home/mike/.xsession-errors

---

### Post by Pumalite on 2007-09-10
Did you do a 'Find File' search?. Everybody has that file in his system. If you don't have it something very wrong is happening.

---

### Post by strabes on 2007-09-10
Pumalite, I'm not experiencing this problem but I don't have that mystery file in my home directory either.

---

### Post by merlinus on 2007-09-10
FWIW, I have two, the difference being that one of them has an _:0 and the other simply an _0 at the end of the filename.

---

### Post by Pumalite on 2007-09-10
Hey Merlin, me too. The thing is that file rules the use of sockets and such and is at the root of many problems with programs based on KDE. It might be that one has to have KDE installed. I do.

---

### Post by merlinus on 2007-09-10
I only have k3b installed from that reality, but the app needed some kde libraries.

---

### Post by Pumalite on 2007-09-10
I have Konqueror installed and sometimes fails because of dcopserver. I erase DCOPserver file, reboot, regenerates itself and voilá, Konqueror is back. Same thing happened to me with k3b one time. Same fix.

---

### Post by Challengerquay on 2007-09-11
Hi All,

I have searched for the file Pumlite suggested I should try to find, there is no such file on my system, this would probably account for KDE desktop not working.

I have downloaded KDE desktop from the website, as re-installing from Synaptic does not work either, can someone talk me through how I re-install Kubuntu from a CD.

I have got both downloads -desktop and alternate.

Thanks again

](*,)

---

### Post by Tautoa on 2007-09-11
If you want to install KDE on top of an existing Ubuntu installation, follow the instructions at [this address]("http://www.psychocats.net/ubuntu/kde")

If you wanted to  install Kubuntu and get rid of the Gnome interface, there are instructions at the same site, just look for 'Pure KDE' in the sidebar at the left :)

---

### Post by Challengerquay on 2007-09-11
My Thanks to Tautoa and Pumalite for their contributions, I have completely cleared the hard drive and started again. Re-installed Ubuntu and used the sudo apt-get install command for kubuntu desktop and everything seems to be working now, as far as I can see.
My original quest was to set up SAMBA with SWAT, but that still does not work from the browser. However having got KDE up and running I hope to be able to do it from the consul, will let you all know the result, or more likely the trouble I get into.

Thanks to all again.

):P

---

### Post by Pumalite on 2007-09-11
You are welcome. The other fix for the problem ( for future reference)( I found out too late it seems), is to delete the file .ICEauthority.

---

### Post by Bobrm2 on 2007-11-14
I am have both problems, files failing to oper and complaining about DECOPserver and was unable to locate the file (DECOPserver) until I dropped the first ë and typed:
sudo dcopserver, now I am getting out of my depth, so I wish to step in and inquire if I go to /usr/bin/iceauth and delete the file or???? Thank you.

Oh, I am typing configure wireless network and wonder if the DECOPserver has anything to do with that??

Bob

bob@Bob&#347;:~$ sudo decopserver
[sudo] password for bob:
sudo: decopserver: command not found
bob@Bob&#347;:~$ dcopserver
/usr/bin/iceauth: /tmp/dcopPfMg8b:1:  bad "add" command line
/usr/bin/iceauth: /tmp/dcopPfMg8b:2:  bad "add" command line
DCOPClient::attachInternal. Attach failed Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
ICE Connection rejected!

DCOPClient::attachInternal. Attach failed Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
DCOPServer self-test failed.
ICE Connection rejected!

bob@Bob&#347;:~$

---

### Post by Bobrm2 on 2007-11-14
Sorry, I missed the last two posts. After trashing the /.ice/
   file, I returned to attempting to run the Hal Device Manager, receiving the same error message with regards to the DECOPserver; however upon Xing out of the error message the HAL-Device Manager window appeared and ran normally.???    Also, having problems, DECOPserver again, with the music program Amarok. 

Bob

---

