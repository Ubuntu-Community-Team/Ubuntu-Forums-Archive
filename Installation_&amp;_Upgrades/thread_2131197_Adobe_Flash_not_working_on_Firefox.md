---
title: "Adobe Flash not working on Firefox"
date: 2013-04-01
forum: Installation &amp; Upgrades
---

### Post by Ralph L on 2013-04-01
I installed Adobe flash (flashplugin-installer 11.2.202.275ubuntu0.12.04.1) on xubuntu 12.04 with Firefox 19.0.2, but it won't work.  I couldn't run [http://www.speakeasy.net/speedtest/](http://www.speakeasy.net/speedtest/) .  I also tried installing adobe-flashplugin_11.2.202.275-0precise1_i386.deb ,but it didn't work either.  Its strange, because on another computer I am running ubuntu 12.04.2 with the exact same version of firefox and using flashplugin-installer 11.2.202.275ubuntu0.12.04.1 (exact same version) and speakeasy runs fine.

Anybody got a suggestion???

---

### Post by dputhal on 2013-04-01
If you have net connection, then directly click on Install Missing plugins. It'll install automatically

---

### Post by claracc on 2013-04-01
> **Ralph L said:**
> I installed Adobe flash (flashplugin-installer 11.2.202.275ubuntu0.12.04.1) on xubuntu 12.04 with Firefox 19.0.2, but it won't work.  I couldn't run [http://www.speakeasy.net/speedtest/](http://www.speakeasy.net/speedtest/) .  I also tried installing adobe-flashplugin_11.2.202.275-0precise1_i386.deb ,but it didn't work either.  Its strange, because on another computer I am running ubuntu 12.04.2 with the exact same version of firefox and using flashplugin-installer 11.2.202.275ubuntu0.12.04.1 (exact same version) and speakeasy runs fine.

Anybody got a suggestion???

Have you tried to install it through synaptic?

Anycase, there is some old graphic cards which don't work with last adobe flash plugin and it is neccessary to use an older flash version (note that this can result in security risks) , please, see the discussion in [http://askubuntu.com/questions/86164/how-do-i-fix-flash-issues](http://askubuntu.com/questions/86164/how-do-i-fix-flash-issues), there are some workarounds which can help you.

---

### Post by Ralph L on 2013-04-01
Where do I find "Install missing plugins" in order to click on it?

And which version should I drop back to?

---

### Post by Ralph L on 2013-04-03
I booted an old version of lucid that I still had on my computer.  I found that [http://www.speakeasy.net/speedtest/](http://www.speakeasy.net/speedtest/), which uses flash, worked there.  In lucid I found that synaptic listed the version as 11.2.202.251ubuntu.10.04.1.  However, firefox listed the version as 11.1 r102. I don't understand the discrepancy in the two versions.  Can anybody explain?

I used synaptic to install the default flashplugin-installer 11.2.202.275ubuntu0.12.04.1 in xubuntu.  I then copied /usr/lib/flashplugin-installer/flashplugin.so from lucid to /usr/lib/flashplugin-installer in Xubuntu (deleting the original).  I also copied /usr/lib/flashplugin-installer/flashplugin.so in lucid to /usr/lib/mozilla/plugins in xubuntu (deleting the orginal), although in lucid the file was named /usr/lib/mozilla/plugins/flashplugin-alternative.so (a symbolic link that pointed back to /usr/lib/flashplugin-installer/flashplugin.so).  After doing this flash worked, but I have a question:  How could flash work on xubuntu, when I didn't have the same name for the flashplayer as I did in lucid???

While I got flash to work, it seems like a very troublesome way to have to install flash.  I did try to install flashplugin-nonfree - 11.2.202.251ubuntu0.12.04.1 from [https://launchpad.net/~ubuntu-mozilla-security/+archive/ppa/+build/3962442](https://launchpad.net/~ubuntu-mozilla-security/+archive/ppa/+build/3962442). but it didn't work.  However, I may have used the incorrect installation procedure.  Can anybody tell me how to install from a web page like [https://launchpad.net/~ubuntu-mozilla-security/+archive/ppa/+build/3962442](https://launchpad.net/~ubuntu-mozilla-security/+archive/ppa/+build/3962442) ????  Apparently I don't know how to do it.

---

### Post by pinballwizard on 2013-04-03
Install the Flash-Aid plugin from LovingLinux.

---

### Post by Ralph L on 2013-04-03
Can you give me a web page for downloading that version of flash aid?  When I try to install flash aid in firefox>Tools>Addons, it says the package has been removed by the author.

---

### Post by claracc on 2013-04-03
I have found this link: [http://www.brothersoft.com/flash-aid-download-394875.html](http://www.brothersoft.com/flash-aid-download-394875.html) to download flash-aid

---

### Post by kurt18947 on 2013-04-03
I think (not certain) that lovinglinux removed FlashAid at Adobe's request or something.  FlashAid relied on beta releases and there are no more Flash beta releases for Linux.  Mozilla is working on something they call Shumway which is a plug-in that plays flash files.  I've tried it and it worked on some sites and not on others.  I did have to disable the flash plug-in in order for Shumway to work.  Another option would be to install the Chrome browser (not chromium).  Google and Adobe have developed something they call pepper to install and manage the latest flash versions.  I installed Chrome a while ago and it didn't work well so I removed it.  It may be better now but I'm happy with the last linux flash release.

---

### Post by pinballwizard on 2013-04-03
> **kurt18947 said:**
> I think (not certain) that lovinglinux removed FlashAid at Adobe's request or something.  FlashAid relied on beta releases and there are no more Flash beta releases for Linux.  Mozilla is working on something they call Shumway which is a plug-in that plays flash files.  I've tried it and it worked on some sites and not on others.  I did have to disable the flash plug-in in order for Shumway to work.  Another option would be to install the Chrome browser (not chromium).  Google and Adobe have developed something they call pepper to install and manage the latest flash versions.  I installed Chrome a while ago and it didn't work well so I removed it.  It may be better now but I'm happy with the last linux flash release.

No, Flash-Aid has an option to install either the beta from adobe labs, or the stable version in the 32/64bit repository.

I reinstalled the machine I'm typing on less than a month ago, and used Flash-Aid, and I have zero problems with flash and use 12.04.2, with Firefox 19.0.2.

I run No Script as well, so generally I only see flash when I want to, but it works just fine. I too tried Chrome recently, and it is gawdawful on Ubuntu. Holy smoke, it was bad. Bad doesn't even come close. Yuck. 

I'll sooner use Lynx than Chrome again.

---

### Post by Ralph L on 2013-04-03
Thank you all for replying.  I appreciate it.  However, I am still not making any progress.  At claracc suggestion I went to [http://www.brothersoft.com/flash-aid-394875.html](http://www.brothersoft.com/flash-aid-394875.html), but when I clicked the "Download" button to download flash-aid, it just went back to another web site with no way to download flash-aid.  claracc, could you help me with this??

pinballwizard:  Would you give me a web address for downloading the beta of flash-aid from adobe labs, or tell me what repository it is in.  When I bring up Ubuntu Software Center in xubuntu 12.04.2, it isn't there.

Thank you again.

---

### Post by claracc on 2013-04-03
From the link provided: [http://www.brothersoft.com/flash-aid-394875.html](http://www.brothersoft.com/flash-aid-394875.html), you click on green download button and it appears a page (see image 1) where you can select two servers to download from , I selected server one and obtain a file (see image 2), which I have just noted it is an .exe one, so perhaps it doesn't work in your xubuntu firefox.

I have found another link: [https://github.com/webgapps/flashaid/downloads](https://github.com/webgapps/flashaid/downloads) which offers 2.2.3 flash aid version, you can try it too.

---

### Post by pinballwizard on 2013-04-03
> **Ralph L said:**
> 

pinballwizard:  Would you give me a web address for downloading the beta of flash-aid from adobe labs, or tell me what repository it is in.  When I bring up Ubuntu Software Center in xubuntu 12.04.2, it isn't there.

.
Try 
[http://www.adobe.com/devnet/flashplayer.html](http://www.adobe.com/devnet/flashplayer.html)
or
[http://labs.adobe.com/technologies/flashruntimes/flashplayer/](http://labs.adobe.com/technologies/flashruntimes/flashplayer/)

---

### Post by Ralph L on 2013-04-03
Claracc

Thank you very much for the explicit instructions for finding flash aid.  I found it, downloaded it and opened it with file roller (after installing the 7zip enhancement to it.  But now I am stuck.  How do I get it installed as an addon/plugin to firefox???

---

### Post by pinballwizard on 2013-04-03
> **Ralph L said:**
> Claracc

  How do I get it installed as an addon/plugin to firefox???

Go to: [https://github.com/webgapps/flashaid](https://github.com/webgapps/flashaid)

And then, from the wiki: 
To install from GitHub, go to the [downloads section]("https://github.com/webgapps/flashaid/downloads"), get the *xpi* file corresponding to the version you want and save it locally. Then drag the downloaded *xpi* file to a Firefox window to start the installation process.
  If you are cloning a GitHub repository, compress the contents of the *firefox* folder into a single *zip*, then rename the file extension to *xpi* and drag it to a Firefox window to install.

---

### Post by Ralph L on 2013-04-05
Thank you all for your replies.  I got flash-aid 2.23 installed and running.  However, all it does is intall flashplugin-installer 11.2.202.275ubuntu0.12.04.1.  This is the same version that came with xubuntu.  It doesn't work on my old compaq presario 2100.  So I am back to ground 0.  I think I need to work my way back through old versions of flash to find the most recent one that will run.  Any advice on how to do that?

---

### Post by oldos2er on 2013-04-05
I think you'd have to go back to flash v10.x, or buy a new computer.

---

### Post by claracc on 2013-04-06
Once you have flashaid installed, go to this web page: [http://helpx.adobe.com/flash-player/kb/archived-flash-player-versions.html](http://helpx.adobe.com/flash-player/kb/archived-flash-player-versions.html), where there are the old flashplayer archives and select [http://fpdownload.macromedia.com/get/flashplayer/installers/archive/fp_11.1.102.63_archive.zip](http://fpdownload.macromedia.com/get/flashplayer/installers/archive/fp_11.1.102.63_archive.zip) (this is what works in my old pIII with sis 630/730 graphics card or whatever would works for you) to download, then run flashaid in the custom mode in order to install the selected version.

In my old pIII, firefox 19.0.2 says my flashplugin is outdated ( ir can result in security risks) but I follow with my old flashplugin ( dismiss the requirements to update it) and I can see flash videos because yje old sis 630/730 graphics card doesn't work with any newer flash plugin.

Other ways to see videos (but only in certain web pages) is to install viewtube script  in firefox to see some videos with mplayer plugins.

---

### Post by Ralph L on 2013-04-11
Thanks to everybody that helped me with this.  Following claracc's instructions I installed flashaid from [https://github.com/webgapps/flashaid/downloads](https://github.com/webgapps/flashaid/downloads) (flash-aid-2.2.3-fx-linux.xpi).  I then dragged this to a firefox window and it was installed, appearing under Firefox/Tools/Addons/Extensions.  Then I went to [http://helpx.adobe.com/flash-player/kb/archived-flash-player-versions.html](http://helpx.adobe.com/flash-player/kb/archived-flash-player-versions.html) and downloaded fp_11.1.102.63_archive.zip as recommended.  I double clicked it and extracted the folder fp_11.1.102.63_archive.  I went to Firefox/Tools/Flash-Aid/Advanced Mode and set "version and source" to "custom", and selected the folder fp_11.1.102.63_archive, which I had just extracted (above).  I opened the 32 bit folder within that, opened it, and selected flashplayer11_1r102_63_linux.i386.tar.gz.  Then I opened the Script tab on the flashaid window, and selected Execute, restarted firefox, and flashplayer was installed.  I ran [http://www.speakeasy.net/speedtest/](http://www.speakeasy.net/speedtest/) (which uses flash) and it worked ok.  I then experimented with next newer version of flashplayer, but it didn't work so I guess the latest version that will work with my computer is fp_11.1.102.63_archive.zip.  Another thread I started at [http://ubuntuforums.org/showthread.php?t=2132116](http://ubuntuforums.org/showthread.php?t=2132116) explains "the why" for some of the problems I had in trying to install from a web site.  However, I stll have one question (for my own education), "How does one find the name of a missing depedency, when doing an install of a .deb file.  I couldn't find a way to do that with either Ubuntu Software Center, dpkg.  Anybody's explanation would be appreciated.

---

### Post by claracc on 2013-04-13
Glad you got fixed your problem.

I think you can know the dependencies of a software package running synaptic package manager, selecting the program, clicking on propierties and then in dependencies tab, so it will be shown all the dependencies of the program.

---

### Post by Ralph L on 2013-04-13
What I was looking for was something that listed only the missing dependencies.  On a program with many dependencies it is very time consuming  to look up each one in synaptic to see if it is installed.  Somebody must have written a program to show just missing dependencies.

---

### Post by claracc on 2013-04-14
I only know about utilities showing all the dependencies of a package: [http://www.ubuntugeek.com/how-to-check-package-dependencies-with-apt-rdepends-on-ubuntu.html](http://www.ubuntugeek.com/how-to-check-package-dependencies-with-apt-rdepends-on-ubuntu.html)

---

### Post by bsc1977 on 2013-06-10
searching in Firefox I found another solution

in the Firefox Add-ons Manager:

"Youtube to HTML5 2.0"

I works very well although one needs to wait for the error message from Firefox to clear itself and also click off the error bar at the X each time.

---

