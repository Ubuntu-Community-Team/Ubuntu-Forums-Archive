---
title: "Ubuntu 10.04 and flash player"
date: 2012-05-10
forum: Installation &amp; Upgrades
---

### Post by joemcummings on 2012-05-10
A few weeks ago the upgrade Ubuntu requested me to allow broke my flash player.

This is a long term support version of the product. Why do they do upgrades that are going to break things? I have heard many complain about this same problem.

Just today they did another upgrade on flash and it still doesn't work. Speedtest.net is a good test for me.

Is there going to be a solution to this immediate problem and is am I going to be able to trust the updates in the future?

Thanks,

Joe

---

### Post by darkod on 2012-05-10
Just go to adobe.com and download the .tar.gz of flash player for your system (32bit, 64bit). Extract the archive anywhere.

Copy just the libflashplayer.so in /yourHome/.mozilla/plugins

In case the plugins folder doesn't exist simply create it. Case closed. In my opinion, fault proof install method.

PS. It might be needed to remove all flash versions you tried to install and didn't work.

---

### Post by joemcummings on 2012-05-11
Thank you for your response. Does that mean the next time Ubuntu updates it will break again, and I will have to run this repair again? Why doesn't the update Ubuntu does accomplish what you suggest? On long term support, doesn't the Ubuntu community check to see they are not breaking things when they do an update?

I don't want to cause problems, I just need to understand. I perceive a computer as a tool, and if I have a typewriter that keeps quiting, I quickly need to ascertain whether it is practical to maintain. Is Ubuntu reliable in it's update process, or do I need to find an old version that works and stop updating, or maybe find another flavor of Linux? 

I know they have some type of supported version for pay. Do these problems exist with that product as well, or is that what people are paying for, to be rid of these problems?

These don't seem like questions there should be problems getting answers to.

Please advise. Thanks,

Joe

---

### Post by Enigmapond on 2012-05-11
It's not the fault of Ubuntu but of the Adobe people. Want a fool-proof method and use FireFox? Install the Flash-Aid plugin. It was  created by one of our members and hasn't failed me yet. Install, run the script it will install the latest and uninstall anything conflicting. Th plugin will notify you of any updates.

---

### Post by darkod on 2012-05-11
> **joemcummings said:**
> Thank you for your response. Does that mean the next time Ubuntu updates it will break again, and I will have to run this repair again? Why doesn't the update Ubuntu does accomplish what you suggest? On long term support, doesn't the Ubuntu community check to see they are not breaking things when they do an update?

I don't want to cause problems, I just need to understand. I perceive a computer as a tool, and if I have a typewriter that keeps quiting, I quickly need to ascertain whether it is practical to maintain. Is Ubuntu reliable in it's update process, or do I need to find an old version that works and stop updating, or maybe find another flavor of Linux? 

I know they have some type of supported version for pay. Do these problems exist with that product as well, or is that what people are paying for, to be rid of these problems?

These don't seem like questions there should be problems getting answers to.

Please advise. Thanks,

Joe

It depends. Since I have separate /home partition that I don't format and I do clean installs instead of upgrades, the flash plugin is there because it's part of my home folder. So, I was running the same flash 10 plugin since 9.10 until recently when I changed it with flash 11 (I think when I installed my 11.10 few months back).

So, for a couple of years I never needed to touch the flash plugin. But in my separate /home partition.

Anyway, it's as simply as keeping it on a usb stick or external hdd, and copy that folder/file back to your home folder after the new install, even if you don't use separate /home partition.

There are other options, like suggested, flash-aid plugin, etc.

---

### Post by akeberte on 2012-05-11
> **Enigmapond said:**
> It's not the fault of Ubuntu but of the Adobe people. Want a fool-proof method and use FireFox? Install the Flash-Aid plugin. It was  created by one of our members and hasn't failed me yet. Install, run the script it will install the latest and uninstall anything conflicting. Th plugin will notify you of any updates.

Flash-Aid unfortunately does not seem to work with the most recent version of the Adobe Flash plugin (11.2.202.235). When installing the regular distro of this this it just results in a "dead" plugin, i.e. when clicking on a video in YouTube in Firefox (12.0) you first see the length of the video then the plugin freezes and shows "0:00" as the length of any video.

In Chromium the plugin looks like it tries to connect to the video without ever accessing it and in Opera the YouTube web page freezes.

Using Flash-Aid to tweak the flash plugin only gives the same end result as just described.

Flash-Aid worked for me with the previous version of the Flash plugin (11.2.202.228 ) where it rectified the "smurf" effect (i.e. the erroneous colour rendering).

Don't know if this is a general bug or related to my specific configuration - I have a NVIDIA GeForce 9300M graphics card.

Unticking "enable hardware acceleration" in the Flash plugin does not help either.

I have also tried downgrading the Flash plugin to 11.1.102.63 using the method presented by lovinglinux [http://ubuntuforums.org/showthread.php?t=1953796](http://ubuntuforums.org/showthread.php?t=1953796) (#1). There seem, however, to be some error in the script provided as all it does for me is to remove the current version of the plugin without installing the old version.

I have not tried the manual method darkod suggested. Is it possible to do that without access to the root account?

---

### Post by ammofreak on 2012-05-11
Hi ):P
Have to concur with Darkod on this one. Had the same problems with Flash & Java. Finally manually installed both & now its' a no-brainer! Had to use Adobe & Oracle because I have a development environment. Regardless, this is the best way to go...:)

---

### Post by darkod on 2012-05-12
> **akeberte said:**
> 
I have not tried the manual method darkod suggested. Is it possible to do that without access to the root account?

Yes it is. You are simply downloading a compressed archive (tar.gz), extract it, and copy a single file in your Home folder exactly in /Home/.mozilla/plugins

Your user should have right to do that because it's your own home folder.

Also upgrades/downgrades are very easy because you simply put there the file (version) you want. You wanna keep running flash 10 for what ever reason, nothing is stopping you.

It might be even better than installing it from any repository because it will never try to update by itself. You update it by copying a new file when ever you want and when you are sure the new is working fine.

PS. Attached below is a test I did in virtual box for someone who didn't believe installing flash works like that. First the new system didn't have any flash at all, trying to open speedtest.net shows that. Then you download the file from the adobe website, extract, copy just the libflashplayer.so in /Home/.mozilla/plugins and voila flash working.

---

### Post by lovinglinux on 2012-05-12
> **akeberte said:**
> I have also tried downgrading the Flash plugin to 11.1.102.63 using the method presented by lovinglinux [http://ubuntuforums.org/showthread.php?t=1953796](http://ubuntuforums.org/showthread.php?t=1953796) (#1). There seem, however, to be some error in the script provided as all it does for me is to remove the current version of the plugin without installing the old version.

I have not tried the manual method darkod suggested. Is it possible to do that without access to the root account?

Do it again, input the old version path,  but before actually running the script, copy it from the Script preview and post it here, so I can take a look.

---

### Post by akeberte on 2012-05-12
> **darkod said:**
> Yes it is. You are simply downloading a compressed archive (tar.gz), extract it, and copy a single file in your Home folder exactly in /Home/.mozilla/plugins

Your user should have right to do that because it's your own home folder.

Also upgrades/downgrades are very easy because you simply put there the file (version) you want. You wanna keep running flash 10 for what ever reason, nothing is stopping you.



Thanks for your reply! I discovered, however, through another thread the existence of the gksudo command so I used that to start Nautilus with root rights.

Manually copying the Flash plugin file didn't prove as simply as copying it into the /Home/.mozilla/plugins folder. There is no such folder in my configuration. It *should* have been stored in my /usr/lib/mozilla/plugins folder (that folder certainly demands root privileges to fiddle with), but for some reason its location was relinked in two stages to the /usr/lib/adobe-flashplugin folder. After having replaced the 202.233 version by the 102.63 one FF, Chromium and Opera **still** behaved the same as described above when trying to view YouTube content, and I felt at a loss, especially as both the 233 and the 63 one proved to work in Konqueror! Eventually I got the idea to test disabling the HTML5 viewing method in FF and Chromium and then suddenly the Flash plugin started to work again, and still works after having enabled HTML5 viewing. So, apparently my problem was caused by some sort of conflict between HTML5 and the Adobe Flash plugin that had appeared after the latest update of the Flash plugin. I had noted that the Flash plugin seemed to work in other web pages than YouTube.

I have still to test whether the problem re-appears if I go back to the 233 version of the plugin.

I should perhaps add that I'm using Ubuntu 10.04 as I'm not yet able to edit my presentation info.

---

### Post by darkod on 2012-05-12
I said in my first post on this subject, if the plugins folder doesn't exist, simply create it. Trust me, it works.

That way you avoid symlinks, system folders, etc. You can create any folder you like in your Home folder.

PS. I am not sure how it can be affected by any flash installed during previous attempts. That's why it's recommended to remove anything you installed that didn't work.

---

### Post by akeberte on 2012-05-12
> **lovinglinux said:**
> Do it again, input the old version path,  but before actually running the script, copy it from the Script preview and post it here, so I can take a look.

Thanks for your reply, lovinglinux!

Here is the script I get after having entered the address to the 32-bit version of your repository ([https://github.com/downloads/webgapps/flashaid/flashplayer11_1r102_63_linux.i386.tar.gz](https://github.com/downloads/webgapps/flashaid/flashplayer11_1r102_63_linux.i386.tar.gz)) in the "Select a local file..." box.

```
#!/bin/bash

sudo apt-get --yes purge adobe-flashplugin
TWEAK=$(cat /etc/adobe/mms.cfg | grep 'OverrideGPUValidation')
if test -z "${TWEAK}";then
echo 'OverrideGPUValidation=true' | sudo tee -a /etc/adobe/mms.cfg
fi
cat /etc/adobe/mms.cfg | sed '/EnableLinuxHWVideoDecode=1/d' | sudo tee /etc/adobe/mms.cfg
NPVIEWER=/usr/lib/nspluginwrapper/i386/linux/npviewer
if test -f "${NPVIEWER}";then
cat /usr/lib/nspluginwrapper/i386/linux/npviewer | sed '/export GDK_NATIVE_WINDOWS=1/d' | sudo tee /usr/lib/nspluginwrapper/i386/linux/npviewer
fi
```

I tried to run this at least two times without any success. However, as stated in my reply to darkod above I eventually gave up on this method and installed the adobe-flashplugin manually instead.

Perhaps my non-typical(?) configuration is causing your script not to work as it should? (See folder addresses in my reply to darkod above.)

---

### Post by akeberte on 2012-05-12
> **darkod said:**
> I said in my first post on this subject, if the plugins folder doesn't exist, simply create it. Trust me, it works.

That way you avoid symlinks, system folders, etc. You can create any folder you like in your Home folder.

PS. I am not sure how it can be affected by any flash installed during previous attempts. That's why it's recommended to remove anything you installed that didn't work.

Aha, now I understand! However, re: your PS. I wonder if I just create the folder you suggest it might actually be overridden by the existing folders. The /usr/lib/mozilla/plugins contains a link file called flashplugin-alternate.so that contains the first relink I mentioned above and I'm not sure if that really goes away if I uninstall the flashplugin with Synaptic; I might have to remove the files manually. I don't want to start going into that process at the moment though, it's too late over here in Sweden, and I'm too tired and need to go to bed...

What would happen if I install the flash-plugin manually in the way you suggest and then forget about it and by mistake install the latest version of the plugin with Synaptic or by a sudo command? Will the two versions be in conflict with another or will sudo/Synaptic discover the manually installed version even if (I'm pretty sure) it won't show up in Synaptic? (What I actually did was that I copied the 63 version of the libflashplayer.so file into the /usr/lib/adobe-flashplugin folder without first deleting the 233 version; I simply renamed that file. Now FF etc correctly reports it as the 63 version but in Synaptic it still looks as if I have the 233 version installed, which technically I have. I suppose I need to do something about this potential problem before the Update Manager wants to install a newer version of the plugin...)

---

### Post by darkod on 2012-05-13
Unfortunately, I'm not such a good expert with these details.

What you could try is this: Right now it still doesn't work 100% right?
Forget for a moment about these installs of flash that didn't work, do the manual procedure and create the plugins folder in your /home/.mozilla.

See if that makes it work. If it does, it means the library in your Home is overriding the previously installed attempts, which sounds good.

I can't promise it won't interfere when doing updates in future, if there is an update for the flash installed in Synaptic.

That's why I would do a remove --purge of all attempts that were made with Synaptic or apt-get, that should clean it all. After that do it manually and that's it.

---

### Post by lovinglinux on 2012-05-14
> **akeberte said:**
> Thanks for your reply, lovinglinux!

Here is the script I get after having entered the address to the 32-bit version of your repository ([https://github.com/downloads/webgapps/flashaid/flashplayer11_1r102_63_linux.i386.tar.gz](https://github.com/downloads/webgapps/flashaid/flashplayer11_1r102_63_linux.i386.tar.gz)) in the "Select a local file..." box.

```
#!/bin/bash

sudo apt-get --yes purge adobe-flashplugin
TWEAK=$(cat /etc/adobe/mms.cfg | grep 'OverrideGPUValidation')
if test -z "${TWEAK}";then
echo 'OverrideGPUValidation=true' | sudo tee -a /etc/adobe/mms.cfg
fi
cat /etc/adobe/mms.cfg | sed '/EnableLinuxHWVideoDecode=1/d' | sudo tee /etc/adobe/mms.cfg
NPVIEWER=/usr/lib/nspluginwrapper/i386/linux/npviewer
if test -f "${NPVIEWER}";then
cat /usr/lib/nspluginwrapper/i386/linux/npviewer | sed '/export GDK_NATIVE_WINDOWS=1/d' | sudo tee /usr/lib/nspluginwrapper/i386/linux/npviewer
fi
```

I tried to run this at least two times without any success. However, as stated in my reply to darkod above I eventually gave up on this method and installed the adobe-flashplugin manually instead.

Perhaps my non-typical(?) configuration is causing your script not to work as it should? (See folder addresses in my reply to darkod above.)

Thanks for the information. It is a bug and I can reproduce it here. It only works with http and not https. The workaround is to download the tar.gz file and use the local path, as it also works.

I will fix this in the next version.

---

### Post by joemcummings on 2012-05-21
From the response, it would seem prudent for Ubuntu users to consider stopping the automatic updates.

I have found over the years they don't worry about breaking something that had previously been working when they do updates. If you can get a version of Ubuntu to run on your computer, and most everything seems to be working, it would seem wise to stop the upgrade process. You never know if they are going to break something, and they don't even provide an easy way to get back where you were. Does anyone know of another flavor of Linux that seems more concerned with keeping their users up to date, but only when things work?

Everyone should warn people about this problem. They want to blame it on flash player of course, but Ubuntu decides what gets updated. If they don't have an update that works, they shouldn't do it. That ain't rocket science.

Thanks for the attempts to help from everyone.

Best,

Joe

---

### Post by darkod on 2012-05-21
I already suggested how to make it work, and it will keep working even if you upgrade the version.

Are you here for a solution or to keep repeating your complaints? Besides, if you really want to report this as a bug, this is not the place.

Report it on launchpad.

I can understand your frustration but I can't understand ignoring the obvious solution and continuing blabbing about the problem. Plus, just because few people reported it on this thread, doesn't mean it doesn't work for anyone. Otherwise there would have been much more than two pages written here.

---

### Post by joemcummings on 2012-05-23
To Darkrod, or what ever it is. (I'm not looking at the name on the last post as I write this, and I can't really remember.) Wow! What a sweet heart reply. Yes, I do want a solution, but as I said, I am looking for a tool that will work, not something I have to learn how to build myself.

I thought someone might have a solution that would seem reasonable and practical to me. As to your solution, there seems some disagreement as to whether that is really the perfect solution you seem to imagine it is. 

I have tried lots of hot rod solutions to problems over the years, and have suffered a lot of terrible consequences of doing so. I am looking for a solution that seems reasonable to me. Any suggestions are still welcome. As to my complaining about something that is a very obvious and serious problem, you might wish to bark at those (or blab at those as you say) who caused this problem; rather than getting upset with me for not choosing to apply your magic fix. Not just me, everyone should complain about developers who routinely break systems for many users through their updates, and just seem not to worry about it. They should complain about it everywhere they can. They should let as many people know as possible. This isn't a bug, it's poor management of the update process. 

For those who tried to help without getting all full of themselves, I thank you. Again let me say, any suggestions are welcome.

Best, 

Joe

---

### Post by darkod on 2012-05-24
Reasonable and practical solution? If copying a single file is not that, I don't know what more to offer.
As for a "solution that you need to build yourself", you are exaggerating it way too much. If we tell that to someone he would think we are making you write software development for flash. You call extracting a compressed archive building it yourself? You never extract ZIP files in windows or what ever... ?

Anyway, I never saw any major (if any) disagreement about this approach. Further more, I posted it in another thread too and you can see how unhappy they are:
[http://ubuntuforums.org/showthread.php?t=1983218](http://ubuntuforums.org/showthread.php?t=1983218)

Go with what ever is best for you man.

---

