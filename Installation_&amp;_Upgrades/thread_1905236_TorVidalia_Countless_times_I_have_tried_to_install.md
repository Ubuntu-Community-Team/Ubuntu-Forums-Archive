---
title: "Tor/Vidalia Countless times I have tried to install Tor in Ubuntu after  installation"
date: 2012-01-06
forum: Installation &amp; Upgrades
---

### Post by stormshadow21 on 2012-01-06
Countless times I have tried to install Tor in Ubuntu after downloading  "Tor Browser Bundle for Linux with Firefox" and ran in the command line ```
 tar -xvzf tor-browser-gnu-linux-i686-2.2.35-3-dev-en-US.tar.gz or tor-browser-gnu-linux-x86_64-2.2.35-3-dev-en-US.tar.gz
```
 and got what is in the screen shot below...can someone help me or tell me another way to install this? 		__[[COLOR=blue][COLOR=blue !important][FONT=inherit !important][COLOR=blue ! important][FONT=inherit ! important][/FONT][/COLOR][COLOR=blue ! important][FONT=inherit ! important][/FONT][/COLOR][/FONT][/COLOR][/COLOR]]("http://www.v7n.com/forums/#")

---

### Post by Basher101 on 2012-01-06
tor and vidalia are in the software center, just look up "vidalia" in the search box and install..


regards

---

### Post by ottosykora on 2012-01-06
> **stormshadow21 said:**
> Countless times I have tried to install Tor in Ubuntu after downloading  "Tor Browser Bundle for Linux with Firefox" and ran in the command line ```
 tar -xvzf tor-browser-gnu-linux-i686-2.2.35-3-dev-en-US.tar.gz or tor-browser-gnu-linux-x86_64-2.2.35-3-dev-en-US.tar.gz
```
 and got what is in the screen shot below...can someone help me or tell me another way to install this? 		__[[COLOR=blue][COLOR=blue !important][FONT=inherit !important][COLOR=blue ! important][FONT=inherit ! important][/FONT][/COLOR][COLOR=blue ! important][FONT=inherit ! important][/FONT][/COLOR][/FONT][/COLOR][/COLOR]]("http://www.v7n.com/forums/#")

something seems to be wrong with the file or the way you are downloading it.
1.download the file from: [https://www.torproject.org/projects/torbrowser.html.en](https://www.torproject.org/projects/torbrowser.html.en)

2.unpack the file contents in suitable place in your home folder (e.g. torbrowser or so)

3. run the torbrowser file, it will start all the rest.


This is the best and safest solution apart from the bootable image Tail.

Otherwise you can install Tor by using the instruction on the Tor website, which will also tell you that the version in the repository of ubuntu is very old and should not be used.

If you install the torprojects ppa all can be installed directly from there in the latest version.

Vidalia is in fact not needed for full install, tor is loaded at boot. You need only Torbutton for firefox and should not use any other browsers currently.

Also no need for polipo or privoxy any more.
I downloaded the file, extracted it with default extractor to my home

---

### Post by stormshadow21 on 2012-01-06
Thanks [ottosykora]("http://ubuntuforums.org/member.php?u=758846") it works now but I keep getting the following error messages that are in the screenshot below...how do i solve this now?

---

### Post by ottosykora on 2012-01-06
yes, because you seem to have installed tor and trying to run other tor...

Either you have to use the tor browser bundle and have otherwise no tor installed, or you have a tor installed and then do not run the tor bundle browser.
You can do one of following:

1. uninstall tor completly, but for that you have to stop it first
and use the tor browser bundle alone
This is prefered for just browsing, no install needed.

2. you keep using installed tor and only use torbutton addon for firefox and do not use anything else like vidalia etc.

3. you use vidalia, because you want a gui for configuring a relay or bridge operation etc, then you have to make sure tor is not running when vidalia starts and tries to start tor.

go to terminal:
sudo apt-get install sysv-rc-conf
sudo sysv-rc-conf

scroll down with arrow keys to the line with tor and remove all x by the use of space bar

reboot

now you can start tor with vidalia

also in vidalia there is a tickbox saying start tor, remove this tick and start tor with the big start button in the vidalia gui. Or if you have the automatic start with vidalia ticked, then do not operate the big start button later. Tor runs then and the browser will tell you that it works when you go to the test site.

you may still get some error and warnings, then choose in vidalia the http port operation and not the socks operation, as the conf file is missing and proper rights have to be set in the place where it needs to be written to.

But if you are after secure surfing, remove any tor installs and use the tor browser bundle only.

---

