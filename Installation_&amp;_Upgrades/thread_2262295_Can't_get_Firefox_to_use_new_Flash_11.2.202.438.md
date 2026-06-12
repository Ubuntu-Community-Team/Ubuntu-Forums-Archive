---
title: "Can't get Firefox to use new Flash 11.2.202.438"
date: 2015-01-24
forum: Installation &amp; Upgrades
---

### Post by Ralph L on 2015-01-24
I just updated my xubuntu 12.04 system using all the latest updates including:  Firefox 35.0 and (I think) Flash 11.2.202.438 for Ubuntu 12.04.  However, I can't get Firefox to use the new Flash.  I installed flashplugin-installer by downloading it, double-clicking the file, and letting Ubuntu Software Center install it.  Is this all that needs to be done to install it or do I need to somehow execute flashplugin-installer.  If so how?

---

### Post by Impavidus on 2015-01-24
That is already more than needs to be done to get Firefox to use the latest flash. I get a pop-up telling me there are updates available (flash player and others), I click install and the new flash player is installed. How did you install flash in the first place? You can go to the software centre (or any other front end to the package manager), search for **flashplugin-installer** and install it. It will be updated along with all other software on your computer. There is no double click or manual download involved.

---

### Post by Ralph L on 2015-01-24
Impavidus:  Thank you very much for responding.  I really appreciate it.  I guess I must have something wrong with my firefox add-ons/extensions.  I have flashplugin-installer (11.2.202.438) installed.  It shows up as installed in Synaptic. I installed it with ubuntu software center. However, when I go to Firefox>Tools>Add-ons>Plugins, it shows the old Flash 11.1 r102.  Moreover, there is no box to remove it.  The only box says "Ask to Activate".  It does have a link that says "Update Now".  If I click that it goes to [https://blocklist.addons.mozilla.org/en-US/firefox/blocked/p332](https://blocklist.addons.mozilla.org/en-US/firefox/blocked/p332) .  Here I can search for addons, but when I search for flash, I get a bunch of addons like FlashBlocker, FlashKiller, etc, but no just plain Flash.  Maybe I don't know what to look for.  Have you been down this route?  Maybe you could tell me what to install here to get the new Flash.

Also, I have looked at my Firefox profile files thinking that there might be a Flash file that I could delete.  However, I couldn't find one.  Do you know if there is a file I could delete to get rid of the old Flash?  My thinking is that if I could delete the old Flash, maybe I could then install the new Flash.

Any other suggestions are appreciated.

---

### Post by Dennis N on 2015-01-24
You can install the flash plugin manually by copying it to the same location of the old one. To find that location, type about:plugins in the Firefox address bar. Here is what I get from that:

```
Shockwave Flash

    File: libflashplayer.so
    Path: /usr/lib/flashplugin-installer/libflashplayer.so
    Version: 11.2.202.438
    State: Enabled
    Shockwave Flash 11.2 r202

```

You can get a new plugin from [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)
Download the .tar.gz file, and extract the libflashplayer.so file from the archive. Move it to the location of the old plugin. Restart Firefox.

---

### Post by Ralph L on 2015-01-24
Dennis N

Thanks for the response.  I appreciate it.  I tried what you suggested and got the new flash installed, but it didn't work.  Also, in the tar folder was a Read.Me that said to copy several other items into my system.  I did that as well as copy the .so file in.  When I do Firefox>Tools>Addons>Plugins, I see the new flash installed.  However, the old flash is also there.  I don't know how to get rid of it.  I have it set to "Never Use", but I don't really know if that is enough.  Maybe having it there is causing the new flash not to work.  I have thought about completely uninstalling Firefox and then reinstalling it with Synaptic, but I am concerned about losing all my profile, bookmarks, etc.  Do you know if I uninstalled it if I would lose all this profile stuff or would the files containing it just remain?

Thank you and if you have any other ideas I would appreciate it.

---

### Post by Dennis N on 2015-01-24
Hi - to check the process, I just did this myself on an old system that needed the new version:
Here is the before install situation:
```
Shockwave Flash

    File: libflashplayer.so
    Path: /usr/lib/flashplugin-installer/libflashplayer.so
    Version: 11.2.202.350
    State: Enabled (STATE_VULNERABLE_UPDATE_AVAILABLE)
    Shockwave Flash 11.2 r202
    
```
Here is what I downloaded:
```
 install_flash_player_11_linux.i386.tar.gz
```
Inside are:
```
usr (a directory)
libflashplayer.so
readme.txt
```
I extracted only the libflashplayer.so file to my desktop. 
Then from the desktop with the terminal:
```
dmn@Roxanne:~$ cd Desktop
dmn@Roxanne:~/Desktop$ sudo cp libflashplayer.so /usr/lib/flashplugin-installer/
```
Restarted Firefox, and doing about:plugins again, here is the new situation
```
Shockwave Flash

    File: libflashplayer.so
    Path: /usr/lib/flashplugin-installer/libflashplayer.so
    Version: 11.2.202.438
    State: Enabled
    Shockwave Flash 11.2 r202
```
So I see that it is updated.
Testing to see that it is recognized by other sites, go to [http://www.adobe.com/software/flash/about/](http://www.adobe.com/software/flash/about/)
Here it tells me: **"You have version 11,2,202,438 installed"**

Your new file will replace the old one since they have the same name, so you should see only one libflashplayer.so file in the location. The other file on my system is **install_plugin** which you can ignore. Just leave it there. Here is the contents of /usr/lib/flashplugin-installer:

```
dmn@Roxanne:/usr/lib/flashplugin-installer$ ls
install_plugin  libflashplayer.so

```

Just to be clear, flash plugin normally would be updated by the Software Updater on a supported OS. But this particular system is not able to do that.

---

### Post by Ralph L on 2015-01-25
Dennis N
Thanks again for responding.  I tried exactly what you did and still no joy.  When I bring up a website with flash in it, a space is cleared for flash to run, but it just remains blank--no error message.  If I disable flash, then I get a message saying a later version of flash is needed.  So firefox is looking for flash and knows that flash is installed. But flash doesn't execute.  Here is the output of about:plugins:```
Shockwave Flash

    File: libflashplayer.so
    Path: /usr/lib/flashplugin-installer/libflashplayer.so
    Version: 11.2.202.438
    State: Enabled
    Shockwave Flash 11.2 r202
```

I did solve the problem of not being able to get rid of the old flash.  The old flash was in a different folder:  /usr/lib/mozilla/plugins.  When I removed libflashplayer.so from there, it disappeared from the Firefox>Tool>Addons>Plugins window.
Any other ideas you might have would be appreciated.

---

### Post by Dennis N on 2015-01-25
> **Ralph L said:**
> Dennis N
Thanks again for responding.  I tried exactly what you did and still no joy.  When I bring up a website with flash in it, a space is cleared for flash to run, but it just remains blank--no error message.  If I disable flash, then I get a message saying a later version of flash is needed.  So firefox is looking for flash and knows that flash is installed. But flash doesn't execute.  Here is the output of about:plugins:```
Shockwave Flash

    File: libflashplayer.so
    Path: /usr/lib/flashplugin-installer/libflashplayer.so
    Version: 11.2.202.438
    State: Enabled
    Shockwave Flash 11.2 r202
```

I did solve the problem of not being able to get rid of the old flash.  The old flash was in a different folder:  /usr/lib/mozilla/plugins.  When I removed libflashplayer.so from there, it disappeared from the Firefox>Tool>Addons>Plugins window.
Any other ideas you might have would be appreciated.

What happens when you visit the adobe test page?

[http://www.adobe.com/software/flash/about/](http://www.adobe.com/software/flash/about/)

Does it give the version you downloaded (11.2.202.438)? If so, I would think installed and detected. 

What you describe (a blank space) sounds to me like flash has been disabled - normally you enable/disable in the Plugins window you refer to - also accessable from about:addons. If its gone, some fixing needs to be done.

Also, the Software updater today (Jan 25) has just upgraded to a still newer version: 11.2.202.440. Is flashplugin-installer installed on your system? If so, it should produce this update soon.

---

### Post by Ralph L on 2015-01-26
> 
What happens when you visit the adobe test page?The space on the screen where flash is supposed to put an image is just blank, and everything just sits there.
> 
Does it give the version you downloaded (11.2.202.438)? If so, I would think installed and detected.  What you describe (a blank space) sounds to me like flash has been disabled - normally you enable/disable in the Plugins window you refer to - also accessable from about:addons. If its gone, some fixing needs to be done.  As you can see from the output from about:plugins, 438 is loaded and enabled.
I am going to give up on this for now.  I have another computer on which the new flash does work.  I will use that when I need flash.  When I get time I will probably do a fresh install of xubuntu 14.04.
Again thank you very much for your help.  I learned a lot from this.

---

### Post by Dennis N on 2015-01-26
> The old flash was in a different folder: /usr/lib/mozilla/plugins. When I removed libflashplayer.so from there, it disappeared from the Firefox>Tool>Addons>Plugins window.

There probably were not two flash plugins - unless someone put one in /usr/lib/mozilla/plugins at some time in the past. That location actually contains a symbolic link which can be mistaken for the plugin since you cannot tell from the name alone. This is from my computer, using the -l option to get the details, and showing it is a symbolic link:

```
dmn@Daphne:/usr/lib/mozilla/plugins$ ls -l
total 0
lrwxrwxrwx 1 root root 37 Jan 25 14:06 flashplugin-alternative.so -> /etc/alternatives/mozilla-flashplugin

```
It should not have been deleted. That is probably what caused the disappearance from the Plugins window you describe. The system needs this to find the plugin location so it can get information from the plugin itself.

---

### Post by RogerDavis on 2015-01-29
I'm using SeaMonkey, and I can't get the new flash to install.  When I attempt to install it from the Add-Ons Manager everything seems to be going well, until I get a small window that says:  "This link needs to be opened with an application" .  What application would that be?  SeaMonkey?  Something else?  Which exact app name do I need to specify in that window?

---

