---
title: "Google Earth http://kh.google.com:80/"
date: 2009-12-29
forum: Installation &amp; Upgrades
---

### Post by Vadimus on 2009-12-29
Hello,
I found a bunch of complaints about the Google Earth installation. I tried to install/reinstall GE from the Ubuntu Software Center and from the Terminal - all the same. When I try to open GE it does so but when it tries to go to the server it ends up giving the following message: "Google Earth could not contact [http://kh.google.com:80/](http://kh.google.com:80/) . Please check your network connection..." and another one: "Google Earth could not establish a new session with EarthServer...." 

I tried to go to [http://kh.google.com:80/](http://kh.google.com:80/) using my Firefox but it says:"Google Error. Not Found. The requested URL / was not found on this server." Also I tried Google Earth help website, Ubuntu Wiki GE troubleshooting and a bunch of other suggestions but none of them addressed my problem precisely and therefore did not help.

 I have Ubuntu 9.10, it is the only OS installed on this laptop. There are no firewalls or anything that would interfere with the connection. 

Any help would be appreciated. :confused:

---

### Post by pepsifx357 on 2010-05-11
I've got Ubuntu 10.04 and I have the same problem.  I can ping it all day but Google Earth can't get to it for some reason.

---

### Post by Mickser_52 on 2010-05-15
I am having exactly the same problem. The Google Earth that came with 10.4 was giving me blurred images so I downloaded the version from medibuntu. Then I got the message about not connecting to server.

By the way does it make a difference which forum you post a question to?

---

### Post by gvernold on 2010-05-19
Yep same problem here in Lucid 32bit. I need Google Earth for some research quite soon so I hope they get this sorted out.

I have nothing that would interfere with my connection either and like-wise I can ping the server without a problem but Google Earth just doesn't want to speak to it.

---

### Post by n1ght5t4lk3r on 2010-05-29
exactly the same issue "Google Earth could not contact [http://kh.google.com:80/]("http://kh.google.com/") . Please check your network  connection..."
Never had the problem in Jaunty, but did a fresh install of Lucid earlier and re-installing a lot of programs, google earth being one (which I installed from the software center within Ubuntu after adding medibuntu repo).

google's own help page that this message points to was not helpful as the above posters have also said.

The are also so many unresolved posts from other users on google's support forums on exactly the same issue, all saying google's help link from the error message was useless, and as far as I can see on ubuntuforums there's no answer for this either. 

Any help would be greatly appreciated

---

### Post by n1ght5t4lk3r on 2010-05-31
I have tried uninstalling googlearth, plus removing the folders for it in the home folder and then re-installing via different methods (originally was via software center), then tried directly from google with no luck so repeated the uninstall/re-install via googleearth-packege, and this issue persists.

2 errors
"Google Earth could not contact [http://kh.google.com:80/]("http://kh.google.com/") . Please check your network  connection..." and another one: "Google Earth could not establish a new  session with EarthServer...." 

I should add that the exact same version of google earth worked for me perfectly a few days ago when i was running ubuntu 9.04 (on the same machine, on the same connection), I did a clean install of 10.04 and Im getting this connection problem. I have searched all over the ubuntu forums, google support forums and elsewhere around the net, lots have this issue and none seem to have it resolved. 

Has anyone else found a solution for this?

---

### Post by Pablo Alonso on 2010-06-03
Hi Everybody !!! I&#7743; having this same issue !!! I'm totally frustrated !!!!!!!!!!!!!!!!!!!!!!!! ](*,)

It seems there is no solution available yet at any place !!!!
I'm posting in this topic also FYI [http://art.ubuntuforums.org/showthread.php?p=9405164&posted=1#post9405164](http://art.ubuntuforums.org/showthread.php?p=9405164&posted=1#post9405164)

If someone has google account to post in their forums please save me from another registration process!

thank to all!
keep searching, eventually someone who has the knowledge will arise!

Regards,

---

### Post by darkod on 2010-06-03
Not sure if it's anything in particular with your systems, but I simply downloaded from the GE website (never tried in software center) the .bin file, run it in terminal and worked straight away.

I know it's not much help. I'm running Lucid 64bit, a clean install, not upgrade from earlier version.

---

### Post by wizodd0 on 2010-06-03
:PI too was able to fix the problem by reinstalling from Google instead of synaptic.
10.4  64bit.

When I reinstalled from synaptic there was no difference from my previous install.:(

---

### Post by Mickser_52 on 2010-06-07
I have sorted google earth problem I reported earlier. I disable ipv6 to sort out a connection problem with thunderbird email and now google earth is working as well

---

### Post by pepsifx357 on 2010-06-07
Looks like nothing has changed.  I've uninstalled my GE from the medibuntu repository and downloaded the .bin from google and I still get the same thing.  I started out with the .bin package when I got Ubuntu 10.04 32bit, so I've gone through this a few times now.

This problem needs to be resolved!:mad:

---

### Post by Pablo Alonso on 2010-06-10
Yep......
still do not work here......

I installed .bin freshly downloaded from google and nothing changed.

how can I disable ipv6 in order to make that test?

thanks.
regards,

---

### Post by darkod on 2010-06-10
> **Pablo Alonso said:**
> Yep......
still do not work here......

I installed .bin freshly downloaded from google and nothing changed.

how can I disable ipv6 in order to make that test?

thanks.
regards,

Isn't that in network manager, right click, Edit Connections... Then select your wired or wireless connection, click Edit button, and there are ipv4 and ipv6 tabs. I guess you can disable it there.

---

### Post by Mickser_52 on 2010-06-11
I disabled ipv6 using this link.
[http://www.webupd8.org/2010/05/how-to-disable-ipv6-in-ubuntu-1004.html]("http://www.webupd8.org/2010/05/how-to-disable-ipv6-in-ubuntu-1004.html")

---

### Post by pepsifx357 on 2010-06-14
Any news?

---

### Post by kuvanito on 2010-06-15
i am having problems too,I don't get any error message it jus opens up and dissapear,no meesages,no google earth either.  :mad::mad::mad:

---

### Post by gychang on 2010-06-15
> **kuvanito said:**
> i am having problems too,I don't get any error message it jus opens up and dissapear,no meesages,no google earth either.  :mad::mad::mad:

same problem here, is there anyone who successfully got the googleearth running?

gychang

---

### Post by Frogster on 2010-06-26
Same problem here and disabling IPv6 made no difference at all

---

### Post by eltonw on 2010-06-26
**[COLOR="Sienna"]HOWTO install Google Earth[/COLOR]** (CURRENTLY version 5) easily:

1) Download the .bin file from here: 
[http://earth.google.com/download-earth.html]("http://earth.google.com/download-earth.html")

2) you need to change permissions to make it an executable (from the GUI right click on the file, select Properties and change permissions to "Allow executing file as a program"

[FONT="Comic Sans MS"][COLOR="DarkRed"]FULL and *easy instructions* HERE:[/COLOR][/FONT]
[http://www.econowics.com/linux/312/install-google-earth-50-in-ubuntu-linux/]("http://www.econowics.com/linux/312/install-google-earth-50-in-ubuntu-linux/")

cheers, ):P

---

### Post by Frogster on 2010-06-27
Does this sort the error?

---

### Post by 6invivo on 2010-12-02
Hi,
I was able to resolve the error with this scenario (combined from different replies on different forums)
 
sudo apt-get autoremove
sudo apt-get install lsb-core
./GoogleEarthLinux.bin --target /tmp/ge
cd /tmp/ge/setup.data/bin/Linux/x86/
sudo mv setup.gtk2 setup.gtk2.bkup
sudo mv setup.gtk setup.gtk2
cd /tmp/ge
./setup.sh
 
and I am ignore ipv6
 
I tried different things, the crucial was installation of lsb-core

---

