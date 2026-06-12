---
title: "after Oneiric update, flash stopped working"
date: 2012-06-01
forum: Installation &amp; Upgrades
---

### Post by Frustrated2218 on 2012-06-01
This has been baffling me for days now, as soon as I allowed the update manager to finish about four days ago, flash stopped working in all browsers.  Just to be sure, I have already tried:  Uninstalling Flash  Uninstalling Firefox  Reinstalling Both  and Using Flash-Aid.  Nothing I've read in any forum works so far, and I have been searching this problem for a while now.  I have only started to have this problem once the update manager ran, so it's clearly something to do with one of the many regular updates that Ubuntu gets on a semi-daily basis. Is there any way I can pinpoint what it is, and get rid of it so I can finally use multimedia in my browser again?

---

### Post by darkod on 2012-06-01
You can try this:
[http://ubuntuforums.org/showpost.php?p=11951782&postcount=3](http://ubuntuforums.org/showpost.php?p=11951782&postcount=3)

Note: It's better to remove all flash related packages you installed while trying to make flash work, not to create any possible conflict.

---

### Post by Frustrated2218 on 2012-06-01
Well, I tried that, unfortunately it didn't work.

---

### Post by kirby33 on 2012-06-01
Hello Frustrated2218!

Do you have a old computer with a 32bits processor (example: AMD Atlhon/Barthon/Sempron)? 

Since the flash player version 11.2.202.228, libflashplayer.so is compiled without SSE2 instruction support... Therefore, the last flash player version does not work with the old processor... :(

You can try to install the release 11.1.102.63 (this one is the last release with SSE2)
[http://helpx.adobe.com/flash-player/kb/archived-flash-player-versions.html](http://helpx.adobe.com/flash-player/kb/archived-flash-player-versions.html)

---

### Post by kirby33 on 2012-06-01
Sorry for the mistake (but the conclusion is the same )
The last flash player is compiled with SSE2 instructions support... And this does not exist on the old AMD 32 bits processor...

---

### Post by darkod on 2012-06-01
That procedure works 100% for firefox. I have been doing it like that since ubuntu 9.10 when 64bit flash support was still very buggy. As I said, other packages you might have installed trying to make it work can interfere unless removed completely (purged).

If you suspect flash 11 can't work on your computer, Adobe still offers flash 10 for download for linux on the same web page.

---

### Post by Frustrated2218 on 2012-06-01
but that's just it, I haven't installed anything aside from flash itself, and flash-aid.  As I said, everything was working fine, untill the update manager did a few routine updates to different libraries in the usr/dev directory or whatever it does, and broke flash.

---

### Post by darkod on 2012-06-02
OK. So, did you remove/purge the flash itself and flash aid?

sudo apt-get remove --purge <package_name>

You don't need any of that if you manually copy the library file to the mentioned folder. You don't install anything. You just copy the file.

Otherwise, I can't be sure which flash it's trying to use.

---

### Post by Frustrated2218 on 2012-06-02
Okay, so I saw you mentioning previous versions of flash, and since the updater may have updated my flash to another version, I tried taking out the current one and running a lower revision, many functions have been restored now using the method you told me. Not all of them, but I can live with that, at least untill I find the correct version of flash for my system.  Thanks one and all for all your help.

---

### Post by darkod on 2012-06-02
No problem. I find this method very easy to use.

Also, you can keep that .so file on a usb stick and simply copy it back after a clean reinstall, etc. Not to mention, that if you install flash from the repositories, it will try to update when there is an update, which sometimes can make issues for some people.

With this method of copying the .so file, you can use an "old" version as long as you want, and use a newer one when you decide to do so. Plus, if the new one doesn't work good, simply copy the older .so file and that's it. Very easy to "downgrade", which is almost impossible with a repository package.

---

