---
title: "Flash in Official PPA in 64bits"
date: 2009-09-25
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Kosimo on 2009-09-25
When installing flash-nonfree from apt-get using Ubuntu 64 bits, does install the 32 bits version or the beta version available in adobe labs, which is 64 bit native?

Thank you

---

### Post by steeleyuk on 2009-09-25
Last time I checked, and from what I've read, it still installs the 32-bit version.

---

### Post by philinux on 2009-09-25
Flashplugin-nonfree depends on flashplugin-installer.

Which in turn depends on nspluginwrapper and ia32-libs etc.

I hope this changes soon as the 64bit plugin although alpha refresh has been rock solid.

Get the 64bit plugin from adobe labs.

---

### Post by Kosimo on 2009-09-25
> **philinux said:**
> Flashplugin-nonfree depends on flashplugin-installer.

Which in turn depends on nspluginwrapper and ia32-libs etc.

I hope this changes soon as the 64bit plugin although alpha refresh has been rock solid.

Get the 64bit plugin from adobe labs.

I've tried the native version and it does works great when it does... But I get some serious crashes, like when opening gMail, for some reason the flash plugin just crash my firefox session.

---

### Post by philinux on 2009-09-25
> **Kosimo said:**
> I've tried the native version and it does works great when it does... But I get some serious crashes, like when opening gMail, for some reason the flash plugin just crash my firefox session.

With the 64 bit plugin from adobe I've not had any npviewer.bin crashes that I used to get.

---

### Post by Kosimo on 2009-09-25
> **philinux said:**
> With the 64 bit plugin from adobe I've not had any npviewer.bin crashes that I used to get.

Can you open firefox and gmail without any issues?

How did you install it?

---

### Post by steeleyuk on 2009-09-25
I can open gmail just fine. I usually create a directory called /usr/lib/flash, copy the plugin to their and symlink to the firefox/chromium directories.

---

### Post by philinux on 2009-09-25
FF works great but I dont use gmail.

Get the plugin here. [http://labs.adobe.com/technologies/flashplayer10/](http://labs.adobe.com/technologies/flashplayer10/)

Uninstall all other flash. Extract the file libflashplayer.so

Move or copy it to here.
/home/username/.mozilla/plugins/libflashplayer.so

You will need to create the folder plugins first. Restart FF

Thats it.

---

### Post by Longinus00 on 2009-09-25
> **Kosimo said:**
> I've tried the native version and it does works great when it does... But I get some serious crashes, like when opening gMail, for some reason the flash plugin just crash my firefox session.

Gmail doesn't have any flash on the page. What error do you get when firefox crashes?

---

### Post by ljrmorgan on 2009-09-25
Yeh, gmail doesn't use flash, so it's an odd error.

I use the 64-bit version, and use gmail extensively, I don't have any problems at all. The 64-bit version I don't think has crashed once for me, the old version crashed all the time, and buttons in videos never worked.

---

### Post by jpeddicord on 2009-09-25
> **ljrmorgan said:**
> Yeh, gmail doesn't use flash, so it's an odd error.

I use the 64-bit version, and use gmail extensively, I don't have any problems at all. The 64-bit version I don't think has crashed once for me, the old version crashed all the time, and buttons in videos never worked.

Gmail does hide flash. It's loaded for chat sounds and the advanced file attachment uploader. You can disable both of these in Settings.

---

### Post by motang on 2009-09-25
I hope they would go with 64bit soon.

---

### Post by Kosimo on 2009-09-25
> **jacobmp92 said:**
> Gmail does hide flash. It's loaded for chat sounds and the advanced file attachment uploader. You can disable both of these in Settings.

Yeps, I knew it has something to do with that. 
I'll try disable those and give it a try again


Thanks for the advice

---

### Post by keenish27 on 2009-09-25
> **steeleyuk said:**
> I can open gmail just fine. I usually create a directory called /usr/lib/flash, copy the plugin to their and symlink to the firefox/chromium directories.

I know where the FF directory is, but where is the google chrome directory?

---

### Post by jpeddicord on 2009-09-25
> **keenish27 said:**
> I know where the FF directory is, but where is the google chrome directory?

~/.config/chromium

cache is in ~/.cache/chromium

---

### Post by keenish27 on 2009-09-25
Thanks.

Thanks, I still can't use the buttons in flash thought.  FF is okay now.

---

### Post by Kosimo on 2009-09-26
After some updates I am now using the native 64 bits flash available in adobe labs webpage. The performance is very good and now all buttons are working perfectly. 

It is sad to know that Ubuntu still offers the buggy 32 version in Ubuntu 64bits as in my opinion does not works. They should add the alpha native version as is much better and lets you use all controls integrated in flash objects.

---

### Post by dinxter on 2009-09-26
> **Kosimo said:**
> After some updates I am now using the native 64 bits flash available in adobe labs webpage. The performance is very good and now all buttons are working perfectly. 

It is sad to know that Ubuntu still offers the buggy 32 version in Ubuntu 64bits as in my opinion does not works. They should add the alpha native version as is much better and lets you use all controls integrated in flash objects.
experience seems to be divided between flash64 being a big improvement for some people and crashing firefox  constantly for others. theres a tweaked version of the repository 32 bit version for 64 bit in the ppa [here]("https://launchpad.net/%7Esevenmachines/+archive/flash") if your lucky enough to be in the former category

---

### Post by nhasian on 2009-09-26
actually i think they use flash for the audio when the chat window pops up in the gmail page.

---

### Post by Kosimo on 2009-09-26
> **dinxter said:**
> experience seems to be divided between flash64 being a big improvement for some people and crashing firefox  constantly for others. theres a tweaked version of the repository 32 bit version for 64 bit in the ppa [here]("https://launchpad.net/%7Esevenmachines/+archive/flash") if your lucky enough to be in the former category

Thanks, but at the moment I'm not going to use it as I already have the native version installed. 

Whave I've said was for the vast majority of users,  which will use the typical installation process having that buggy flash without being able to doing something that basic like viewing videos in full screen...

---

### Post by lithorus on 2009-09-26
> **Kosimo said:**
> Thanks, but at the moment I'm not going to use it as I already have the native version installed. 

Whave I've said was for the vast majority of users,  which will use the typical installation process having that buggy flash without being able to doing something that basic like viewing videos in full screen...
That is actually one of the drawbacks of Flash 64-bit, it's not hardware accelerated, which the 32-bit one is. However opengl acceleration is disabled when composite is enabled.

---

### Post by dinxter on 2009-09-26
maybe if we send the gnash people a christmas hamper we'll be pain free by next aprils release :)

---

### Post by Kosimo on 2009-09-26
> **lithorus said:**
> That is actually one of the drawbacks of Flash 64-bit, it's not hardware accelerated, which the 32-bit one is. However opengl acceleration is disabled when composite is enabled.

I don't feel any difference between flash 32 bits in a 32 bits system and flash native 64bits in a 64 bits system.

---

### Post by Jim March on 2009-09-27
You have to nuke every trace of 32bit flash and support (including the horror that is NSPLuginwrapper) and then install Adobe's Flash64.  This thread has more details:

[http://ubuntuforums.org/showthread.php?t=1241313](http://ubuntuforums.org/showthread.php?t=1241313)

As best we can tell Adobe doesn't want to publicly admit they've done Flash64 for Linux before doing the same for Windows and Mac, so they've labeled what appears to be solid code "alpha".  This in turn scares all the major distros away from it.

Flash64 has been BY FAR the best Linux flash player ever, for me.  And I only jumped to 64bit with Karmic (at alpha4).  It runs Hulu fullscreen without a glitch.

---

### Post by lithorus on 2009-09-27
> **Kosimo said:**
> I don't feel any difference between flash 32 bits in a 32 bits system and flash native 64bits in a 64 bits system.
Did you try without composite enabled in X? 32-bit flash explicity checks for the composite extension.

---

### Post by Amaranth on 2009-09-27
I believe it actually checks for a running compositor with gdk_screen_is_composited() since they do use GTK+ and it would be silly to disable flash acceleration for having an X extension enabled that has been on by default for about 4 years.

---

### Post by nanog on 2009-09-27
Its ironic that, for me, the 64 bit flash "alpha" is far more stable than 32 bit. 

> As best we can tell Adobe doesn't want to publicly admit they've done Flash64 for Linux before doing the same for Windows and Mac, so they've labeled what appears to be solid code "alpha". This in turn scares all the major distros away from it.


Adobe stated that they chose to develop native 64 bit for *nix because linuxites were more vocal (and actually knew what a bit was).

---

### Post by Kosimo on 2009-09-27
> **Amaranth said:**
> I believe it actually checks for a running compositor with gdk_screen_is_composited() since they do use GTK+ and it would be silly to disable flash acceleration for having an X extension enabled that has been on by default for about 4 years.

So, you're saying that 64bit flash still have hardware acceleration even enabling compiz?

---

### Post by Amaranth on 2009-09-27
No I'm saying their check for composite is smarter than lithorus suggested. That is completely different from them just not compiling the GPU acceleration code into their 64-bit version.

---

### Post by lithorus on 2009-09-27
> **Amaranth said:**
> No I'm saying their check for composite is smarter than lithorus suggested. That is completely different from them just not compiling the GPU acceleration code into their 64-bit version.
Still, I would like to know under which conditions did the poster test the 32-bit version of flash.

---

### Post by kaotiko on 2009-09-29
In /etc/apt/sources.list:

deb [http://ppa.launchpad.net/sevenmachines/flash/ubuntu](http://ppa.launchpad.net/sevenmachines/flash/ubuntu) karmic main 
deb-src [http://ppa.launchpad.net/sevenmachines/flash/ubuntu](http://ppa.launchpad.net/sevenmachines/flash/ubuntu) karmic main 

In Terminal:

gpg --keyserver keyserver.ubuntu.com --recv 35DA01C261E46227
gpg --export --armor 35DA01C261E46227 | sudo apt-key add -
sudo apt-get update
sudo apt-get install flashplugin64-installer

\\:D/

---

### Post by Arlanthir on 2009-09-29
Can't use gmail with flash enabled, for the life of me :S 
Already disabled the two flash features and nothing...

Edit: Fixed it by installing Flashblock :)

---

### Post by kaotiko on 2009-09-30
> **kaotiko said:**
> In /etc/apt/sources.list:

deb [http://ppa.launchpad.net/sevenmachines/flash/ubuntu](http://ppa.launchpad.net/sevenmachines/flash/ubuntu) karmic main 
deb-src [http://ppa.launchpad.net/sevenmachines/flash/ubuntu](http://ppa.launchpad.net/sevenmachines/flash/ubuntu) karmic main 

In Terminal:

gpg --keyserver keyserver.ubuntu.com --recv 35DA01C261E46227
gpg --export --armor 35DA01C261E46227 | sudo apt-key add -
sudo apt-get update
sudo apt-get install flashplugin64-installer

\\:D/

Is recommended to remove previous flash plugins:

sudo apt-get purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash swfdec-mozilla

:p

---

