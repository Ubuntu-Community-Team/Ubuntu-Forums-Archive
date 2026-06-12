---
title: "Firefox terribly slow after Intrepid upgrade"
date: 2008-11-03
forum: Installation &amp; Upgrades
---

### Post by BetterSense on 2008-11-03
I upgraded from hardy to Intrepid after using Hardy on this laptop only a few days. Firefox is terribly slow, and hangs/goes grey all the time. Or, I will enter text into an online form and it will freeze, so I press the key a few times, then it unfreezes and all the extra keystrokes instantly show up. Annoying stuff like this. Constantly I will be scrolling down with the arrow key, and it freezes, then unfreezez and scrolls all the way past where I wanted. Sometimes it just completely hangs and I have to kill and revive it. I have no idea why. I would use an different browser but I don't like konqueror, and kazahakase and midori crash constantly for me.

---

### Post by jonybigoude on 2008-11-04
Same here on a fresh Intrepid install. Terribly sloooooooow, barely usable. If anyone has any idea how to make it better, it would be nice. ):P

---

### Post by hunter_s on 2008-11-04
Hi, I have the similar sounding issues and they started directly after I upgraded to Intrepid ibex

In summary both Firefox versions 2.0.0.7 and 3.03 seem to have the same issues. Opera however doesn't.


I have googled and also searched the forums and found several possible solutions.


Some of these point to a problem with the nvidia driver with javascript, css or flash.

Well I've tried with 177 installed and also with just the plain old nv driver in my xorg.conf file but to no avail.

uname -a

Linux blackbox 2.6.27-7-generic #1 SMP Thu Oct 30 04:12:22 UTC 2008 x86_64 GNU/Linux

---

### Post by neried7 on 2008-11-05
Hey guys, I had this problem, and i was able to fix it in my case.

So on 64 bit ubuntu, the flash plugin has issues, mainly that it doesn't really work all the time, because there is only the x86 (32 bit) plugin, and no 64bit version. I realized this was the issue with the web browsers after upgrading to intrepid because it was flash-heavy sites (cnn.com) that would cause it to hang and go grey, but not simpler sites (digg.com). Also, running 'gksudo firefox' will give you the errors regarding not finding the flash libraries when you go to those flash-heavy sites. I had fixed flash before the upgrade thanks to a script, but the upgrade screwed things up. 

So, if this is a similar case for you, run this script below, which will download all necessary libraries and the Flash 10 plugin/player and *wrap it*, so it will work correctly with the 64bit system.  After restarting firefox, enter 'about:plugins' in Firefox to check if shockwave flash plugin is installed, it might be at the bottom. 


```

#!/bin/bash
# Script  created by
# Romeo-Adrian Cioaba romeo.cioaba@spotonearth.com
# Super minor updates by jason.melton[at]gmail[dot]com
# Other minor updates by neried7@mit.edu
# Released under GPL

#Must install Debian package 'getlibs-all' first:
#http://www.boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb
#This is a package that will grab libs, 32 and 64-bit under amd64 (and 32-bit only under i386.)

cd ~
echo "Getting and installing getlibs-all"
wget http://www.boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb
sudo gdebi getlibs-all.deb
rm -rf getlibs-all.deb


echo "Stopping any Firefox that might be running"
sudo killall -9 firefox

echo "Removing any other flash plugin previously installed:"
sudo apt-get remove -y --purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash swfdec-mozilla libflash\
support nspluginwrapper
sudo rm -f /usr/lib/mozilla/plugins/*flash*
sudo rm -f ~/.mozilla/plugins/*flash*
sudo rm -f /usr/lib/firefox/plugins/*flash*
sudo rm -f /usr/lib/firefox-addons/plugins/*flash*
sudo rm -rfd /usr/lib/nspluginwrapper

echo "Installing ia32-libs and nspluginwrapper"
sudo apt-get install ia32-libs nspluginwrapper

echo "Getting libs"
sudo getlibs -p libcurl3
sudo getlibs -p libnss3-1d
sudo getlibs -p libnspr4-0d

echo "Installing Flash Player 10"
cd ~
wget http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_install_linux_091508.tar.gz
tar zxvf flashplayer10_install_linux_091508.tar.gz
sudo cp install_flash_player_10_linux/libflashplayer.so /usr/lib/mozilla/plugins/
rm -rf ~/install_flash_player_10_linux/
sudo nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so

echo "Linking the libraries so Firefox can find it."
sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/mozilla/plugins/
sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/firefox-addons/plugins/

echo "Cleanup..."
rm -rf flashplayer10_install_linux_091508.tar

echo "Done :-)"

#Enter 'about:plugins' in Firefox to check if shockwave flash plugin is installed, it might be at the bottom.

```


Give that a try, it might solve your problem. If you are *not* running 64bit, try reinstalling flash either via firefox plugins or via ubuntu's add/remove applications, and restart firefox. Let us know how you fare.

---

### Post by hunter_s on 2008-11-05
What is this getlibs command? I'm not familiar with it and I get a "bash: getlibs: command not found" error...

---

### Post by neried7 on 2008-11-05
you may need to install the package via 'sudo apt-get install getlibs'.

getlibs: Automatically solves dependencies for 32-bit programs on 64-bit
On 64-bit systems it downloads and installs libraries needed for 32-bit programs and 64-bit programs.
On 32-bit systems it downloads and installs libraries needed for 32-bit programs.

---

### Post by kystorms on 2008-11-05
Hello

I too am having major issues even keeping Firefox runnign ( 64 bit Intrepid) this is the errors I get when running gksudo firefox _

ICEDTEAPLUGIN_DEBUG = (null)
ICEDTEAPLUGIN_DEBUG = (null)
LoadPlugin: failed to initialize shared library libXext.so [libXext.so: cannot open shared object file: No such file or directory]
LoadPlugin: failed to initialize shared library /usr/lib/mozilla/plugins/libflashplayer.so [/usr/lib/mozilla/plugins/libflashplayer.so: wrong ELF class: ELFCLASS32]

does this mean I too have to run your script you placed in this post? I checked my about: plugins and see that 10 is in fact running or rather is there with a yes beside it.

newbie here, so please excuse me if I am asking a dumb question.

thanks for any help , Opera will not work on my machine so FF is the ONLY browser option that I have as far as I know.

---

### Post by neried7 on 2008-11-05
That's the sort of message I got when i ran firefox in gksudo.

You may have flash 10 installed, but it's 32bit (there is no 64bit version for linux. adobe really does suck this way), and if you're running 64bit ubuntu, it will cause this problem. The script removes the previous flash installation, gets all the libraries and packages needed and installs flash 10 wrapped, so that it will work correctly with the 64bit environment. Try the script I included (it's never broken anything for me, promise). 

PS: Instead of running all the commands one by one, copy-paste the whole text into a file (eg flash-10-64bit-install.sh), make it executable (chmod +x <filename>), then run the script (sudo ./<filename>)

---

### Post by kystorms on 2008-11-05
Okay, saved it to desktop as a text file, with exact name you suggested, followed the steps you outline and now get error in terminal ~
flash-10-64bit-install.sh
i know it is something I am doing wrong, 

sorry for bugging you all

---

### Post by neried7 on 2008-11-05
When saving the script, make sure it is a .sh file, not a .txt file or similar. Make sure you aren't including those brackets (<>), those were just part of the 'use some filename' parameter pseudocode. At the prompt, given filename flash-10-64bit-install.sh, change to the directory where you saved it (in your case, the Desktop), make sure it's executable, and then run it as root:

```


cd /home/YourUsername/Desktop

chmod +x flash-10-64bit-install.sh

sudo ./flash-10-64bit-install.sh



```

---

### Post by josephellengar on 2008-11-05
I got this problem.  I changed to konqueror and now that works well.

---

### Post by MockY on 2008-11-06
I was forced to change to Opera. I have used Firefox for many years, and I don't think it's fun at all to be forced to migrate to another browser, just because the default browser doesn't run in this supposedly "stable" release. Browsing the Internet is THE ONE most common activity we all do, and if that does not work out of the box, then I don't see why I should use the distro at all. With all the issues that Hardy and Intrepid has given me on both desktops and laptops, I am going back to Gutsy (for the desktop) and Feisty (for the laptop).

Just try this site [http://ubuntu-bossieman.blogspot.com/](http://ubuntu-bossieman.blogspot.com/)
It runs just fine using Opera, but using Firefox, it slows down my entire system. This is really getting me pissed of and frustrated. Funny thing, I had NO issues what so ever with the release candidate. What made them take a dump on the final release is beyond me.

---

### Post by dentharg on 2008-11-06
I have Kubuntu 8.10, FF3, no slowdown on this site...

---

### Post by neried7 on 2008-11-06
As a note, it was not just Firefox 3.0.3 that was slow for me on upgrade, but all browsers, doing the hang routine. The solution I described above fixed all of that for me, as flash was the common issue. But I bet the other issues people are experiencing may be unrelated to that. I wouldn't be surprised if mozilla addressed these eventually, but unclear when.

---

### Post by mlissner on 2008-11-08
I'm not on 64 bit because I hoped to avoid just this kind of problem...I've been dealing with this for days though. Yeah, it's incredibly frustrating.

---

### Post by crate2k5 on 2008-11-09
I'm in a 32-bit install as well and it's defiantly flash. I tried the other versions of flash players and they gave me even worse problems. I'm running the same version on hardy heron with out problems. It's even on a slower system. I don't know what is it.

---

### Post by bulldog on 2008-11-09
Worked for me,thank you :KS

---

### Post by gertvs on 2008-11-09
I upgraded to 32-bit Intrepid. Same problems as mentioned on this thread.
Is there anybody who can tell if this is a bug? Is it reported? If bot should I report it?

Gert

---

### Post by ipse on 2008-11-09
> **neried7 said:**
> Hey guys, I had this problem, and i was able to fix it in my case.

Don't spend your time. Just install flashplugin-nonfree (`aptitude install flashplugin-nonfree`) - it contains latest Flash plugin and seems to solve the issue. So, no more magic to get Flash working!

---

### Post by gertvs on 2008-11-10
I solved my problem.
Just for information to others:
I had 2 version 9 Flash plug-ins installed. When I disabled them Firefox didn't lock up anymore, but I could then obviously not see any Flash content anymore. I then tried to install the latest Flash version (10), but the problems returned.

I finally completely removed Firefox and its plug-ins, and then re-installed it. This fresh version had no Flash plug-ins, but after I downloaded the latest APT package from Adobe's site, I can now see flash content without any problems.

---

### Post by BetterSense on 2008-11-10
I'll give that a try maybe. I'm on 32 bit. Could you explain  what exactly you did to completely uninstall Firefox and flash? Will > sudo apt-get remove firefox flashplugin-nonfree do it?

---

### Post by neried7 on 2008-11-10
> **ipse said:**
> Don't spend your time. Just install flashplugin-nonfree (`aptitude install flashplugin-nonfree`) - it contains latest Flash plugin and seems to solve the issue. So, no more magic to get Flash working!

So flashplugin-nonfree just gets the linux plugin from the adobe site, unpacks it, and installs it. As there is only a 32bit plugin available from Adobe for linux, this does not help those on 64bit systems.

---

### Post by eatmo on 2008-11-12
Thanks neried7, that script worked perfectly for me. Flash even seems more stable now than it was under Hardy on my laptop.

---

### Post by neried7 on 2008-11-20
Update: Adobe now has an Alpha release of Flash 10 64bit, specifically for Linux (Windows and Mac will come later). I've read good reviews so far about it, that it performs even better than 32bit, and am going to try it out myself.

[http://labs.adobe.com/technologies/flashplayer10/releasenotes_64bit.html#known]("http://labs.adobe.com/technologies/flashplayer10/releasenotes_64bit.html#known")

---

### Post by Atnevon on 2008-12-07
I'm on Intrepid 32 and having the same problem sadly.  I tried the suggested removal of firefox and re-install, but to no avail.  At this point I'm going to have to use XP until this one gets fixed, as I just don't have it in me to work with a system running that slow.

---

### Post by BetterSense on 2008-12-09
It's good to know I'm not the only 32 bit intrepid adopter stung. I personally rolled back to Hardy, and am doing just fine now, other than suffering from the time lost. My firefox works now, my Lyx and other KDE apps are working again, and I can actually use my computer. Maybe I'll try intrepid later on a different computer. Maybe.

---

### Post by gingerlizard on 2008-12-09
My FF actually became unusable today as it became frozen treacle.

(Intrepid, 1GB Thinkpad T23 1.13GHz)

Previously to Intrepid it's been reasonable provided I don't go mad with the tabs. Has got progressively worse over a matter of weeks - possibly started degrading with HH.

Tried relaoding FF, tried clearing caches & history, tried having just a single tab open, tried rebooting.

Tried opening a guest session, in the hope that a clean copy with no caches or history might improve matters - but no - same terrible performance.

I downloaded Opera with FF's last breath of life.

There seems to be something odd going on in FF. Clearing the cache & history appeared to work on previous occassions - but it seems like the history doesn't clear properly - just goes back to an earlier point with some stuff remaining.

Opera is fine. The tab and page load behaviour FF *should* have. 

(And right click seems to work reliably:p).

-------------

EDIT: Some poking about in other suggested solutions - I found deleting .mozilla/firefox/v???????.default/places.sqlite from your home directory does the trick.

---

