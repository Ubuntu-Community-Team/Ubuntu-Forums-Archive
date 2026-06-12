---
title: "Adobe Flash 10 rc has been released!"
date: 2008-08-12
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by olskar on 2008-08-12
* Camera input works a whole lot better (V4L1 and V4L2 cameras both work; V4L2 cameras don't peg the CPU anymore)
    * Software fullscreen performance is vastly improved
    * Faster, more stable windowless mode (but be sure to use very recent browser builds)
    * SSL now handled through NSS instead of flashsupport-OpenSSL alliance
    * White speckles are gone from video playback
    * Important stability fixes (fewer crashes)
    * Still not 64-bit native, just to get that out of the way

[Get it here!]("http://labs.adobe.com/technologies/flashplayer10/")

---

### Post by Nullack on 2008-08-12
Yeah saw that on Phoronix. Im waiting for it to hit the repos to aid in testing this alpha.

---

### Post by tommcd on 2008-08-12
I just tried Flash 10 RC in Slackware 12.1. I did not run the flashplayer-installer, I just copied the libflashplayer.so to /usr/lib/mozilla/plugins directory with the appropriate symlinks to firefox 3.0. (This method has always worked fine in Flash 7 & 9). Flash 10 seemed to work fine, except that full screen mode on youtube videos caused FF to lock up solid. Full screen works fine for me in Flash 9. So I am back with Flash 9 for now.
I had removed Flash 9 before installing Flash 10.
Anyone else have better luck?

---

### Post by mempf on 2008-08-12
It seems that using this new version of flash player 10 has made YouTube's high quality videos disappear.

When trying to view a video in the high quality setting I just get "We're sorry, this video is no longer available."

The normal quality versions work fine.

Can anyone confirm?

---

### Post by Exsecrabilus on 2008-08-12
Oh my God Flash 10 RC.

---

### Post by caish5 on 2008-08-12
Finally Full screen flas that is ... "Like Butter"!
Very Impressed Here.
Although the high quality Youtube has gone for me too.

---

### Post by phenest on 2008-08-13
Wow! Loads better. Full screen is so smooth now, but, if I press one of the media keys on my Dell laptop, full screen exits back to normal mode.

---

### Post by psyke83 on 2008-08-13
I finally set up my PPA, and flash is the first package I have uploaded ;). It will be available here for anyone interested in testing (it's currently still pending): [https://launchpad.net/~psyke83/+archive](https://launchpad.net/~psyke83/+archive)

I plan to also include a patched xulrunner-1.9 to fix [bug #239182]("https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/239182"), and thus hopefully fixing the Flash + PulseAudio mess once and for all.

---

### Post by Sealbhach on 2008-08-13
Hmmmm...

see screenshot.

---

### Post by BwackNinja on 2008-08-13
Yay! I'm about to try it out.

@Sealbhach
You'd expect that when using something that isn't meant to break backwards compatibility you'd be able to do a simple "flashversion >= 8"

---

### Post by xebian on 2008-08-13
> **psyke83 said:**
> I finally set up my PPA, and flash is the first package I have uploaded ;). It will be available here for anyone interested in testing (it's currently still pending): [https://launchpad.net/~psyke83/+archive](https://launchpad.net/~psyke83/+archive)

I plan to also include a patched xulrunner-1.9 to fix [bug #239182]("https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/239182"), and thus hopefully fixing the Flash + PulseAudio mess once and for all.

The new RC requires more than the 32bit libs now.  It looks for libcurl3 and some ssh/sss stuff.  So if you didn't factor these in it will fail.

---

### Post by psyke83 on 2008-08-13
> **xebian said:**
> The new RC requires more than the 32bit libs now.  It looks for libcurl3 and some ssh/sss stuff.  So if you didn't factor these in it will fail.

Thanks, I'll update the archive after determining the new dependencies.

---

### Post by xebian on 2008-08-13
> **psyke83 said:**
> Thanks, I'll update the archive after determining the new dependencies.

Btw, I'm talking about the 64bit install.  You need these 32bit libraries

libcurl3
libidn11
libnspr4-0d
libnss3-id
libssh2-1

It would be nice if you could add them to the ia32-libs or create another set.

---

### Post by psyke83 on 2008-08-13
> **xebian said:**
> Btw, I'm talking about the 64bit install.  You need these 32bit libraries

libcurl3
libidn11
libnspr4-0d
libnss3-id
libssh2-1

It would be nice if you could add them to the ia32-libs or create another set.

I'm not too confident to mess with the ia32-libs stuff, as I don't have a 64bit machine here to test with.

Anyway, the package has been updated to ~ppa2, with the above dependencies except for libssh2-1 - it's not necessary, which you can verify from the ldd output of libflashplayer.so.

Also, I added a quick hack that disables windowless mode in Flash, which hopefully means no more crashes! This feature can be re-enabled when Firefox 3.0.2 (and nspluginwrapper >=1.1.0 for amd64) is released.

---

### Post by xebian on 2008-08-13
> **psyke83 said:**
> I'm not too confident to mess with the ia32-libs stuff, as I don't have a 64bit machine here to test with.

Anyway, the package has been updated to ~ppa2, with the above dependencies except for libssh2-1 - it's not necessary, which you can verify from the ldd output of libflashplayer.so.



You don't believe me?  :shock:
```

       libssh2.so.1 => /usr/lib32/libssh2.so.1 (0xf6891000)
 

```
Too much or not enough Guinness ?:)

---

### Post by psyke83 on 2008-08-13
> **xebian said:**
> You don't believe me?  :shock:
```

       libssh2.so.1 => /usr/lib32/libssh2.so.1 (0xf6891000)
 

```
Too much or not enough Guinness ?:)

:p

I have installed libssh2-1, and...

```
conn@dimension:~/ppa$ ldd /usr/lib/flashplugin-nonfree/libflashplayer.so | grep ssh
conn@dimension:~/ppa$
```

Nothing. Nada. Zip. :p. Perhaps npwrapper.bin modifies the executable when wrapped, since you're on 64bit, or it's an ia32-libs dependency as you mentioned before? I'm not sure it's best to add a dependency to the flashplugin-nonfree package in this case...

---

### Post by xebian on 2008-08-15
> **psyke83 said:**
> :p

I have installed libssh2-1, and...

```
conn@dimension:~/ppa$ ldd /usr/lib/flashplugin-nonfree/libflashplayer.so | grep ssh
conn@dimension:~/ppa$
```

Nothing. Nada. Zip. :p. Perhaps npwrapper.bin modifies the executable when wrapped, since you're on 64bit, or it's an ia32-libs dependency as you mentioned before? I'm not sure it's best to add a dependency to the flashplugin-nonfree package in this case...

Do as you please.  

How can you be making 64bit deb packages without even a 64bit box to test?

```
 Originally Posted by psyke83  View Post
I'm not too confident to mess with the ia32-libs stuff, as I don't have a 64bit machine here to test with.

```

---

### Post by psyke83 on 2008-08-15
> **xebian said:**
> Do as you please.  

How can you be making 64bit deb packages without even a 64bit box to test?

```
 Originally Posted by psyke83  View Post
I'm not too confident to mess with the ia32-libs stuff, as I don't have a 64bit machine here to test with.

```

The flashplugin-nonfree source is platform-agnostic, which is why I didn't limit the build platforms. The problem, as you said, is with ia32-lib. Since it's a 450mb+ source package and some people don't think the new dependencies belong in that package, a supplemental package will need to be created. See [bug #246911]("https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/246911")

I have someone with a 64bit box helping out a bit, and I've collected some info on how to create this supplemental package (using the fetch-and-build script), but you're more than welcome to help as well. If you want to take a crack at it, go ahead.

---

### Post by psyke83 on 2008-08-15
xebian,

In fact, this post may contain the solution for the time being: [http://ubuntuforums.org/showpost.php?p=5595360&postcount=4](http://ubuntuforums.org/showpost.php?p=5595360&postcount=4) *except* that you can ignore the step to manually install flash. Use GetLibs to grab the libraries and then reinstall the flashplugin-nonfree package from my PPA.

---

### Post by silkstone on 2008-08-15
The latest Flash 10-rc doesn't play well for me on 32-bit Hardy.

At first I thought it would - the BBC iPlayer works full-screen without skipping frames, although the clock at the top right of the BBC home page doesn't show unless you click on it.

But then I tried Sky News, and the Flash videos cause FF to close. Also the CNN site gives the error message mentioned in a previous post.

So I've gone back to Flash 10 Beta 1 which works fine except that it doesn't support transparency and it skips frames with iPlayer in full screen.

P.S. I installed using the guide below - the section headed Troubleshooting - Adobe Flash Player which is near the end of the first post.

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

That involves extracting libflashplayer.so, copying it to a new folder and adding links. It's easy then to switch between different versions of the flash plugin by copying libflashplayer.so to the appropriate directory - no need to uninstall and reinstall anything.

---

### Post by psyke83 on 2008-08-15
> **silkstone said:**
> The latest Flash 10-rc doesn't play well for me on 32-bit Hardy.

Firstly, wrong forum (this is for Intrepid users).

Secondly, you're experiencing a windowless mode bug in Firefox. It's a known issue and a workaround is available; the guide you linked to isn't very helpful. See: [https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/239182](https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/239182)

Thirdly, this thread is more appropriate for you (as a Hardy user): [http://ubuntuforums.org/showthread.php?p=5587712](http://ubuntuforums.org/showthread.php?p=5587712) - my PPA includes updated packages with the necessary workaround for the wmode bug included (be sure to look at the actual guide on the first post, too). It's better for you to reply in a Hardy thread than here.

---

### Post by bpl07 on 2008-08-15
> **psyke83 said:**
> 

Secondly, you're experiencing a windowless mode bug in Firefox. It's a known issue and a workaround is available; the guide you linked to isn't very helpful. 



Have you considered building a .deb for the latest nspluginwrapper ([1.1.0]("http://gwenole.beauchesne.info/en/blog/2008/07/06/nspluginwrapper_1.1.0"))?  It has support for windowless mode with flash, as well as other nice features such as automatically restarting crashed plugins.  It's working great on my system, and other than having to adjust the flash install scripts so that they don't try to use the -n flag of nspluginwrapper (non-existent in my build) the installation was relatively pain free.

---

### Post by psyke83 on 2008-08-15
> **bpl07 said:**
> Have you considered building a .deb for the latest nspluginwrapper ([1.1.0]("http://gwenole.beauchesne.info/en/blog/2008/07/06/nspluginwrapper_1.1.0"))?  It has support for windowless mode with flash, as well as other nice features such as automatically restarting crashed plugins.  It's working great on my system, and other than having to adjust the flash install scripts so that they don't try to use the -n flag of nspluginwrapper (non-existent in my build) the installation was relatively pain free.

Funnily enough, I built a deb for i386 users (the amd64 version I built didn't seem to work correctly for other users) - it's posted somewhere on LP bug #192888. Anyway, if you use the flashplugin-nonfree package from my PPA, you don't need to use a newer nspluginwrapper release - even if you're running 64bit. The package preinstalls an /etc/adobe/mms.cfg file which disables windowless mode. It seems like the most sane option until Firefox 3.0.2 anyway.

Flash 10 RC with windowless mode disabled + the proper asoundrc configuration - libflashsupport = absolutely no crashes with Firefox, PulseAudio and Flash.

---

### Post by olskar on 2008-08-18
Firefox 3.0.2 should be here quite soon, right? 11 September or something :)

---

### Post by ScislaC on 2008-09-16
Hopefully this is the appropriate thread to post this in.

For some reason the package from Psyke83's PPA does not work for me, however the repo version works fine.

At this point I've tried all of the usual troubleshooting to no avail. What it seems to boil down to is that the flash plugin is not detected by Firefox nor Opera (even checked in Firefox via about:plugins). I can hop into Synaptic and downgrade the package to the intrepid repo version and it works fine again, and as soon as I upgrade to the ppa version it's no longer detected.

The only thing that looks like a potential culprit at this point is what I gather from the output of: ```
ldd /usr/lib/flashplugin-nonfree/libflashplayer.so
```

To which the following three things aren't found (even though they're installed and successfully detected and used by other programs).
	libnss3.so => not found
	libsmime3.so => not found
	libssl3.so => not found

Has anyone else experienced anything similar to this? Thanks in advance.

---

### Post by psyke83 on 2008-09-16
> **ScislaC said:**
> Hopefully this is the appropriate thread to post this in.

For some reason the package from Psyke83's PPA does not work for me, however the repo version works fine.

At this point I've tried all of the usual troubleshooting to no avail. What it seems to boil down to is that the flash plugin is not detected by Firefox nor Opera (even checked in Firefox via about:plugins). I can hop into Synaptic and downgrade the package to the intrepid repo version and it works fine again, and as soon as I upgrade to the ppa version it's no longer detected.

The only thing that looks like a potential culprit at this point is what I gather from the output of: ```
ldd /usr/lib/flashplugin-nonfree/libflashplayer.so
```

To which the following three things aren't found (even though they're installed and successfully detected and used by other programs).
	libnss3.so => not found
	libsmime3.so => not found
	libssl3.so => not found

Has anyone else experienced anything similar to this? Thanks in advance.

Can you try uninstalling firefox-2 and ensure you have libnss3-1d installed? Test using Firefox 3 for the time being - and if it works, we can try to get it working for the previous release if possible.

P.S. This is the best thread to discuss this issue: [http://ubuntuforums.org/showthread.php?t=866965](http://ubuntuforums.org/showthread.php?t=866965)

---

### Post by bash on 2008-09-16
Ok I got the latest flashplugin from psyke83's ppa working on my 64bit Intrepid machine. Once I figured it out it's quite simple actually:

1. Add psyke83's ppa to your sources and update. Don't install the new flashplugin just yet.:

```
deb http://ppa.launchpad.net/psyke83/ubuntu intrepid main
deb-src http://ppa.launchpad.net/psyke83/ubuntu intrepid main
```

2. Grab and install getlibs from [[http://ubuntuforums.org/showthread.php?t=474790]here](http://ubuntuforums.org/showthread.php?t=474790]here)[/here]. The run:

```
sudo getlibs -p libcurl3
sudo getlibs -p libnss3-1d
sudo getlibs -p libnspr4-0d
```

3. Now you can install/update the flashplugin package and everything should work peachy. 

psyke83's flash solved all the flickering I had with the current flash version in Ibex.

---

### Post by psyke83 on 2008-09-16
> **bash said:**
> Ok I got the latest flashplugin from psyke83's ppa working on my 64bit Intrepid machine. Once I figured it out it's quite simple actually:

Thanks for the effort to explain the process. In fact, this thread already documents the procedure: [http://ubuntuforums.org/showthread.php?t=866965](http://ubuntuforums.org/showthread.php?t=866965)

Can you confirm that getlibs needs administrator privileges? I suspected it would, but all references I saw on the forum seemed to instruct you to run it as a normal user (I don't have a 64bit install to test on).

---

### Post by pferraro on 2008-09-17
After the recent update to ia32-libs, I get the following error when viewing flash videos:
/usr/lib/nspluginwrapper/i386/linux/npviewer.bin: error while loading shared libraries: libxcb-render-util.so.0: cannot open shared object file: No such file or directory

Do others have this problem too?

---

### Post by Stepan Roucka on 2008-09-17
pferraro:

I have the same problem in Interpid, it appeared after some todays updates.

/usr/lib/nspluginwrapper/i386/linux/npviewer.bin: error while loading shared libraries: libxcb-render-util.so.0: cannot open shared object file: No such file or directory

A related bug has already been reported:
[https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/271392](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/271392)

---

### Post by LadFromWales85 on 2008-09-17
```
getlibs /usr/lib/nspluginwrapper/i386/linux/npviewer.bin
``` :)

Sadly despite solving these dependencies, I'm still only getting the grey box since I upgraded to Intrepid :(

---

### Post by justU on 2008-09-17
> **pferraro said:**
> After the recent update to ia32-libs, I get the following error when viewing flash videos:
/usr/lib/nspluginwrapper/i386/linux/npviewer.bin: error while loading shared libraries: libxcb-render-util.so.0: cannot open shared object file: No such file or directory

Do others have this problem too?

I had the same Problem (Intrepid live-daily).

But I solved it by installing the missing libs:

```
getlibs -p libxcb-render-util0 libxcb-render0 libgnutls26
```

Hope that information helps.

---

### Post by pferraro on 2008-09-17
Not here...

$ sudo getlibs -p libxcb-render-util0
The following i386 packages will be installed: libxcb-render-util0
Continue [Y/n]? Y
libxcb-render-util0 was not found in your repositories
Make sure you have all repositories enabled and updated
No packages to install

---

### Post by Stepan Roucka on 2008-09-17
> **justU said:**
> I had the same Problem (Intrepid live-daily).

But I solved it by installing the missing libs:

```
getlibs -p libxcb-render-util0 libxcb-render0 libgnutls26
```

Hope that information helps.

Thanks, it worked for me

---

### Post by psyke83 on 2008-09-17
> **Stepan Roucka said:**
> pferraro:

I have the same problem in Interpid, it appeared after some todays updates.

/usr/lib/nspluginwrapper/i386/linux/npviewer.bin: error while loading shared libraries: libxcb-render-util.so.0: cannot open shared object file: No such file or directory

A related bug has already been reported:
[https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/271392](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/271392)

Thanks for filing the bug. Stephen Hermann (the maintainer of ia32-libs) is working on this. I imagine the new package will be built and ready by tomorrow.

---

### Post by mrgnash on 2008-10-07
> **justU said:**
> I had the same Problem (Intrepid live-daily).

But I solved it by installing the missing libs:

```
getlibs -p libxcb-render-util0 libxcb-render0 libgnutls26
```

Hope that information helps.

It definitely helped me, thanks :D

---

