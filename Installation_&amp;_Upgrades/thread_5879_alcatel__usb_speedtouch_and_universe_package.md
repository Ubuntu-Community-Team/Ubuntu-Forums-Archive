---
title: "alcatel  usb speedtouch and universe package"
date: 2004-11-22
forum: Installation &amp; Upgrades
---

### Post by simonsmith.uk@gmail.com on 2004-11-22
Hi all 

First off thanks to everyone who worked on Ubuntus 'warty' its a great product (real XP killer in my book) well done to all 

However .. i'm trying to connect to the internet with my broadband modem and a alcatel speedtouch and the first step is to include the speedtouch package from universe ....... am I right in asuming I need to connect to the internet to get this package ?  Can I download this from somewhere and burn it to a CD ? 

I know this has been said elsewhere but ubuntu's only flaw is the huge battle to connect it to the internet .... can a latter build have a internet connection package on the CD with a collection of commonly used bits and pieces ? right now I'm relying on (windows) PCs of friends to sort me out , not a great advert for Linux and ubuntu

---

### Post by thiebo on 2004-11-22
hi, 

This might help you :

[http://www.fedora-france.org/modules/wfsection/article.php?articleid=31](http://www.fedora-france.org/modules/wfsection/article.php?articleid=31)

It concerns fedora and the tutorial in in French, but who cares really ???? It gives you the packages that you need to install and which can be found also on the alcatel website. To be honest, I've tried and ended up buying a ethernet router - modem (which I have difficulties connecting under Ubuntu but which is fine under Fedora)... the two packages you need are in the link I've given above. I agree that Ubuntu is great but connecting to internet a pain ! 

Good luck

---

### Post by simonsmith.uk@gmail.com on 2004-11-23
Iv'e translated it from french (using babel fish) and still looks daunting !! can anyone recommend a hassle free (+cheap) router to use instead? 


[QUOTE=thiebo]hi, 

This might help you :

[http://www.fedora-france.org/modules/wfsection/article.php?articleid=31](http://www.fedora-france.org/modules/wfsection/article.php?articleid=31)

It concerns fedora and the tutorial in in French, but who cares really ???? It gives you the packages that you need to install and which can be found also on the alcatel website. To be honest, I've tried and ended up buying a ethernet router - modem (which I have difficulties connecting under Ubuntu but which is fine under Fedora)... the two packages you need are in the link I've given above. I agree that Ubuntu is great but connecting to internet a pain ! 

Good luck[/QUOTE]

---

### Post by Hairyharry on 2004-11-23
I use a SpeedTouch 510 modem/router - it has worked 100% with every distro I've thrown at it. Maybe not the cheapest I paid £75.00, 12 months ago, but its saved me one heck of a lot of time as all configuration is automatic using dhcp.

---

### Post by darrell on 2004-11-23
I had a bit of trouble installing my speedtouch via the "universe" package. However, taking a hint from the end of the readme.DEBIAN file in the package:

> Firmware

modem_run is used to load the modem firmware, which can be downloaded
from Thomson at [http://www.speedtouch.com/driver_upgrade_lx_3.0.1.2.htm](http://www.speedtouch.com/driver_upgrade_lx_3.0.1.2.htm)
or possibly found in a more useful form on other sites.
You should copy the files in /usr/local/lib/speedtouch/, which is where
the hotplug script will look for them.
Different firmware files may be used by editing the hotplug script.


Package web site

You may find useful information about this package and using DSL modems
with Debian at [http://people.debian.org/~md/](http://people.debian.org/~md/) .

lead me to the following method which "just worked" for me:

1. You need to download the stuff to somewhere you can access it from ubuntu - the easiest is probably onto another linux or even windows partition on your box if you have another operating system installed on the same machine. Otherwise, use a floppy or burn a cd.

2. install the libatm package from your ubuntu cd, if not already installed

3. Boot into whatever OS you need to use to download from the net.

3. Download: [http://ftp.linux.it/pub/People/md/warez/speedtouch-firmware_0.3012_all.deb](http://ftp.linux.it/pub/People/md/warez/speedtouch-firmware_0.3012_all.deb)

4. Download: [http://ftp.debian.org/debian/pool/main/s/speedtouch/speedtouch_1.3.1-1_i386.deb](http://ftp.debian.org/debian/pool/main/s/speedtouch/speedtouch_1.3.1-1_i386.deb)

4. boot back into Ubuntu

5. mount the partition/CD/floppy which contains the downloaded files

6. in a terminal, cd to the directory containing the downloaded files

7. **sudo dpkg -i speedtouch_1.3.1-1_i386.deb speedtouch-firmware_0.3012_all.deb**

8. **sudo gedit /etc/modules** - in the editor window, add **pppoatm**  at the bottom of the list of modules. save the file and close the editor. This will start this necessary module on system boot. Start it now with **sudo modprobe pppoatm**

9. **sudo gedit /etc/ppp/chap-secrets** - in the editor window, add a line:
**<your-isp-user-name> * <your-isp-password> *** 
save file and close editor

10. **sudo gedit /etc/ppp/pap-secrets** - in the editor window, add an identical line to that just added to the chap secrets file. Save and close editor. You will only use one of these two files, depending on the authentication method used by your isp, but is doesn't hurt to have both on your system.

11. **sudo cp /usr/share/doc/speedtouch/examples/peers-pppoa /etc/ppp/peers/adslscript**

12. **sudo gedit /etc/ppp/peers/adslscript** - uncomment the user line by removing the # sign at the beginning. replace the username string between the quotes with your isp user name. In the next paragraph change 8.35 to 0.38 (assuming you are in the UK) save and close.

13. **sudo gedit /etc/hotplug/usb/speedtouch** - change the PPPD_PEER line to:
**PPPD_PEER="adslscript"**
save and close

14. plug in your modem. it should load the firmware and then connect to your isp. You can check progress with **tail -f /var/log/messages** (ctrl-c will get you out of this when done) 

Hope that I haven't forgotten anything - repost if you have any problems.

darrell

---

### Post by simonsmith.uk@gmail.com on 2004-11-25
[QUOTE=darrell]I had a bit of trouble installing my speedtouch via the "universe" package. However, taking a hint from the end of the readme.DEBIAN file in the package:



lead me to the following method which "just worked" for me:

1. You need to download the stuff to somewhere you can access it from ubuntu - the easiest is probably onto another linux or even windows partition on your box if you have another operating system installed on the same machine. Otherwise, use a floppy or burn a cd.

2. install the libatm package from your ubuntu cd, if not already installed

3. Boot into whatever OS you need to use to download from the net.

3. Download: [http://ftp.linux.it/pub/People/md/warez/speedtouch-firmware_0.3012_all.deb](http://ftp.linux.it/pub/People/md/warez/speedtouch-firmware_0.3012_all.deb)

4. Download: [http://ftp.debian.org/debian/pool/main/s/speedtouch/speedtouch_1.3.1-1_i386.deb](http://ftp.debian.org/debian/pool/main/s/speedtouch/speedtouch_1.3.1-1_i386.deb)

4. boot back into Ubuntu

5. mount the partition/CD/floppy which contains the downloaded files

6. in a terminal, cd to the directory containing the downloaded files

7. **sudo dpkg -i speedtouch_1.3.1-1_i386.deb speedtouch-firmware_0.3012_all.deb**

8. **sudo gedit /etc/modules** - in the editor window, add **pppoatm**  at the bottom of the list of modules. save the file and close the editor. This will start this necessary module on system boot. Start it now with **sudo modprobe pppoatm**

9. **sudo gedit /etc/ppp/chap-secrets** - in the editor window, add a line:
**<your-isp-user-name> * <your-isp-password> *** 
save file and close editor

10. **sudo gedit /etc/ppp/pap-secrets** - in the editor window, add an identical line to that just added to the chap secrets file. Save and close editor. You will only use one of these two files, depending on the authentication method used by your isp, but is doesn't hurt to have both on your system.

11. **sudo cd /etc/ppp/peers**

12. **sudo cp /usr/share/doc/speedtouch/examples/peers-pppoa adslscript**

13. **sudo gedit adslscript** - uncomment the user line by removing the # sign at the beginning. replace the username string between the quotes with your isp user name. In the next paragraph change 8.35 to 0.38 (assuming you are in the UK) save and close.

14. **sudo gedit /etc/hotplug/usb/speedtouch** - change the PPPD_PEER line to:
**PPPD_PEER="adslscript"**
save and close

15. plug in your modem. it should load the firmware and then connect to your isp. You can check progress with **tail -f /var/log/messages** (ctrl-c will get you out of this when done) 

Hope that I haven't forgotten anything - repost if you have any problems.

darrell[/QUOTE]
 thanks I think I'm getting somewhere !!!  I went through the steps above , and step 11 (11. sudo cd /etc/ppp/peers) caused the error sudo donen't know 'cd' or somthing similar ....
I continued however and tailing the file /var/log/messages showed that the ASDL line was up. 
however starting a browser and hitting [www.google.co.uk](www.google.co.uk) didnt work  ....

PS a big thanks to EVERYONE thats helped so far

---

### Post by darrell on 2004-11-25
[QUOTE=simonsmith.uk@gmail.com]thanks I think I'm getting somewhere !!!  I went through the steps above , and step 11 (11. sudo cd /etc/ppp/peers) caused the error sudo donen't know 'cd' or somthing similar ....
I continued however and tailing the file /var/log/messages showed that the ASDL line was up. 
however starting a browser and hitting [www.google.co.uk](www.google.co.uk) didnt work  ....

PS a big thanks to EVERYONE thats helped so far[/QUOTE]

Aha  - something I didn't consider while trying to get into the ubuntu spirit of sudo, rather than using a root logon. The reason sudo won't/can't change the directory is that sudo runs as a child process, and a child process cannot affect the current working directory of its parent (i.e. your command line shell). 

Never mind. all that:

> 11. sudo cd /etc/ppp/peers

12. sudo cp /usr/share/doc/speedtouch/examples/peers-pppoa adslscript

is doing is copying the example script in the package to the correct place so that it will be invoked when your adsl line goes up. We could have achieved this as follows:

**sudo cp /usr/share/doc/speedtouch/examples/peers-pppoa /etc/ppp/peers/adslscript**

Step 13 would then become:

**sudo gedit /etc/ppp/peers/adslscript**

(i.e. just specify the absolute location of adslscript for the copy and the edit, rather than cd-ing into its directory first)

The bottom line is that you need the *adslscript* file in the correct location (/etc/ppp/peers) in order for it to work.

What has probably happened is that you have copied and amended the script in your home directory. if this is the case (you could try **ls ~/adslscript** to check - ~ is shorthand for your home directory)

if that's where it is, and as it seems, you have already edited it to include your isp user name and the correct VP.VC pair (i.e. 0.38 for the UK), do the following:

**sudo cp ~/adslscript /etc/ppp/peers/**

now, issue the tail command, and unplug your modem, then plug it in again. This time, hopefully, in addition to the stuff about the line going up, you should some messages about authentication taking place, and then the setting of ip/dns addresses. Once this has settled down, you should be connected.

darrell

---

### Post by simonsmith.uk@gmail.com on 2004-11-25
thanks (again !) will try that tonight .... will keep you posted 
Simon

---

### Post by darrell on 2004-11-25
[QUOTE=simonsmith.uk@gmail.com]thanks (again !) will try that tonight .... will keep you posted 
Simon[/QUOTE]
 just to try and help further, as the worst thing to try and set up is internet access, as without this you can't easily go on the net to ask for help...

I suggest when you start up your machine this evening, you do so without the adsl modem plugged in. This will prevent any possibility of a failed connection attempt causing any problems when you reconnect. It probably wouldn't, as the unplugging and replugging of the modem should reinitialise everything, but it can't hurt to be sure.

When booted into ubuntu, open a command line shell, and try

**lsmod |grep pppoatm**

to make sure that the pppoatm module is loaded (it should be if you added the line to your modules file as in my previous post) If by any chance it isn't, issue the modprobe command as in my previous post.

Now proceed as suggested in my last post. 

For absolute clarity, the line to be added to the chap-secrets and pap-secrets files should NOT include the < and > signs. They should look exactly like (including the *'s)

**yourispusername * yourisppassword ***

darrell

---

### Post by Mr. Brownstone on 2005-01-09
Sorry for bumping this old thread, but I just wanted to confirm something:

Will installing the Speedtouch firmware affect Windows operation?

Thanks for any help. :)

---

### Post by lesleyb on 2005-02-04
[QUOTE=darrell]I had a bit of trouble installing my speedtouch via the "universe" package. However, taking a hint from the end of the readme.DEBIAN file in the package:



lead me to the following method which "just worked" for me:

1. You need to download the stuff to somewhere you can access it from ubuntu - the easiest is probably onto another linux or even windows partition on your box if you have another operating system installed on the same machine. Otherwise, use a floppy or burn a cd.

2. install the libatm package from your ubuntu cd, if not already installed

3. Boot into whatever OS you need to use to download from the net.

3. Download: [http://ftp.linux.it/pub/People/md/warez/speedtouch-firmware_0.3012_all.deb](http://ftp.linux.it/pub/People/md/warez/speedtouch-firmware_0.3012_all.deb)

4. Download: [http://ftp.debian.org/debian/pool/main/s/speedtouch/speedtouch_1.3.1-1_i386.deb](http://ftp.debian.org/debian/pool/main/s/speedtouch/speedtouch_1.3.1-1_i386.deb)

4. boot back into Ubuntu

5. mount the partition/CD/floppy which contains the downloaded files

6. in a terminal, cd to the directory containing the downloaded files

7. **sudo dpkg -i speedtouch_1.3.1-1_i386.deb speedtouch-firmware_0.3012_all.deb**

8. **sudo gedit /etc/modules** - in the editor window, add **pppoatm**  at the bottom of the list of modules. save the file and close the editor. This will start this necessary module on system boot. Start it now with **sudo modprobe pppoatm**

9. **sudo gedit /etc/ppp/chap-secrets** - in the editor window, add a line:
**<your-isp-user-name> * <your-isp-password> *** 
save file and close editor

10. **sudo gedit /etc/ppp/pap-secrets** - in the editor window, add an identical line to that just added to the chap secrets file. Save and close editor. You will only use one of these two files, depending on the authentication method used by your isp, but is doesn't hurt to have both on your system.

11. **sudo cp /usr/share/doc/speedtouch/examples/peers-pppoa /etc/ppp/peers/adslscript**

12. **sudo gedit /etc/ppp/peers/adslscript** - uncomment the user line by removing the # sign at the beginning. replace the username string between the quotes with your isp user name. In the next paragraph change 8.35 to 0.38 (assuming you are in the UK) save and close.

13. **sudo gedit /etc/hotplug/usb/speedtouch** - change the PPPD_PEER line to:
**PPPD_PEER="adslscript"**
save and close

14. plug in your modem. it should load the firmware and then connect to your isp. You can check progress with **tail -f /var/log/messages** (ctrl-c will get you out of this when done) 

Hope that I haven't forgotten anything - repost if you have any problems.

darrell[/QUOTE]


Darrell

Thank you for posting this.

I have a speedtouch 330 silver but Rev 2.
This method has been successful in getting me onto the Internet via Ubuntu.

Is it possible to have it made into a HOWTO?

Regards

LesleyB

---

### Post by Azure_Phoenix on 2005-04-30
hey all :), just to let you know the file 
4. Download: [http://ftp.debian.org/debian/pool/m....3.1-1_i386.deb](http://ftp.debian.org/debian/pool/m....3.1-1_i386.deb)
has changed to [http://ftp.linux.it/pub/People/md/warez/speedtouch-firmware_0.3012k_all.deb](http://ftp.linux.it/pub/People/md/warez/speedtouch-firmware_0.3012k_all.deb)
as far as i can tell, 

good luck

---

### Post by Niccko on 2005-06-14
[QUOTE=darrell]
11. **sudo cp /usr/share/doc/speedtouch/examples/peers-pppoa /etc/ppp/peers/adslscript**
[/QUOTE]

I'm terribly sorry to reply lately, but I need help ! I followed the process till 11. I can't continue because i don't have any file calling "peers-pppoa" in my /usr/share/doc/speedtouch/examples directory.](*,) 

Is it normal ? And How can I do ?

Thank you for reply (and sorry for my english)

---

### Post by darrell on 2005-06-27
[QUOTE=Mr. Brownstone]Sorry for bumping this old thread, but I just wanted to confirm something:

Will installing the Speedtouch firmware affect Windows operation?

Thanks for any help. :)[/QUOTE]

no. the firmware is loaded into the modem each time it is initialised. So Windows will just load it with whatever it always did load it with.

---

### Post by darrell on 2005-06-27
version 1 of my speedtouch howto is now posted: [http://ubuntuforums.org/showthread.php?t=44763](http://ubuntuforums.org/showthread.php?t=44763)

---

### Post by bakman on 2005-07-25
Sorry to post in an old thread, but i had the same problem and now i am stuck. I followed all the instruction given here but i cant open any page in firefox!!!
I can see that the line is up and the speed is right, but i can see no page at all!!!

If anyone solved this problem please tell me how!!!

Thanx in return...

---

