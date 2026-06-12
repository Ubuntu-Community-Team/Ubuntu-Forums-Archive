---
title: "How to install Flash 10 64bits (native) in Jaunty 64 bits"
date: 2009-04-04
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Kosimo on 2009-04-04
Hello folks, I'm about to install my fist 64bits OS ever!

I just have one question: 

Is the Flash-nonfree plugin in Jaunty 64  the official adobe 64bits native version?

---

### Post by lonniehenry on 2009-04-04
The answer is no.  The 64 bit is still beta - however it works great and causes fewer problems than the flash with wrapper.  (at least in my system).  Follow the steps in this thread. [http://ubuntuforums.org/showthread.php?t=772490](http://ubuntuforums.org/showthread.php?t=772490) (java from here also works very well in Jaunty.   Welcome aboard the 64 bit experience.

---

### Post by Kosimo on 2009-04-04
> **lonniehenry said:**
> The answer is no.  The 64 bit is still beta - however it works great and causes fewer problems than the flash with wrapper.  (at least in my system).  Follow the steps in this thread. [http://ubuntuforums.org/showthread.php?t=772490](http://ubuntuforums.org/showthread.php?t=772490) (java from here also works very well in Jaunty.

Good, then I won't install it using synaptic. I want to use the 64bit native version (even in beta) which seems to work flawlessly

---

### Post by davidself1001 on 2009-04-04
Followed the install instructions but when done I don't have any sound when playing flash videos in youtube, dailymotion, etc.  Now what?

---

### Post by biji on 2009-04-04
you have to download it from adobe (64 bit version) yourself.. extract.. and move libflashplayer.so to 
~/.mozilla/plugins/

---

### Post by Yashiro on 2009-04-04
[http://labs.adobe.com/technologies/flashplayer10/releasenotes_64bit.html#install](http://labs.adobe.com/technologies/flashplayer10/releasenotes_64bit.html#install)

---

### Post by davidself1001 on 2009-04-04
Ok.  I tried to load the libflashplayer.so to ~.mozilla and now when I try to play a video it says I don't have the plugin installed.  I tried to re-apply the 64bit installer but still no dice.  Help!

---

### Post by rplantz on 2009-04-04
> **davidself1001 said:**
> Ok.  I tried to load the libflashplayer.so to ~.mozilla and now when I try to play a video it says I don't have the plugin installed.  I tried to re-apply the 64bit installer but still no dice.  Help!

I think it has to be in ~/.mozilla/plugins/

I'm still running 8.10, and I did a system-wide install: /usr/lib/mozilla/plugins/

It works for me at most websites, but a few cause my Firefox to crash. And Opera simply does not show the content.

---

### Post by ktp on 2009-04-04
> **davidself1001 said:**
> Ok.  I tried to load the libflashplayer.so to ~.mozilla and now when I try to play a video it says I don't have the plugin installed.  I tried to re-apply the 64bit installer but still no dice.  Help!

Did you put it in ~/.mozilla/**plugins**/?

---

### Post by davidself1001 on 2009-04-04
Yes.

---

### Post by ktp on 2009-04-04
Do you still have the nonfree install?  I would try purging it.  I have mine in there and everything works:

```
ls -l ~/.mozilla/plugins/
-rwxr-xr-x 1 9543400 2009-02-02 23:03 libflashplayer.so
```

---

### Post by davidself1001 on 2009-04-04
I did a complete removal on the non-free version with synaptic and still no gass.  When I do the ls in my ~/.mozilla/plugins/ I get exactly the same as you show here.  I am confused.  I even went into firefox, preferences, apps and made sure that flash videos are played with the specific libflashplayer.so that is in the above mentioned dir.  Man, this is frustrating.

---

### Post by taavikko on 2009-04-05
```
devil@elite:~$ locate libflashplayer
/usr/lib/mozilla/plugins/libflashplayer.so
devil@elite:~$ locate libflashplayer |xargs file
/usr/lib/mozilla/plugins/libflashplayer.so: ELF 64-bit LSB shared object, x86-64, version 1 (SYSV), dynamically linked, stripped
```

Downloaded from adobe, then moved to that folder.
(For system wide. If multiuser)

---

### Post by phenest on 2009-04-05
I put the flash player in /usr/lib/firefox-addons/plugins

Of course, don't forget to uninstall flashplugin-nonfree

---

### Post by davidself1001 on 2009-04-05
> **taavikko said:**
> ```
devil@elite:~$ locate libflashplayer
/usr/lib/mozilla/plugins/libflashplayer.so
devil@elite:~$ locate libflashplayer |xargs file
/usr/lib/mozilla/plugins/libflashplayer.so: ELF 64-bit LSB shared object, x86-64, version 1 (SYSV), dynamically linked, stripped
```

Downloaded from adobe, then moved to that folder.
(For system wide. If multiuser)
I get this when I do the locate libflashplayer.so

~$ locate libflashplayer/home/david/.mozilla/plugins/libflashplayer.so
/usr/lib/firefox/plugins/npwrapper.libflashplayer.so
/usr/lib/iceweasel/plugins/npwrapper.libflashplayer.so
/usr/lib/mozilla/plugins/libflashplayer.so
/usr/lib/mozilla/plugins/npwrapper.libflashplayer.so

$ locate libflashplayer | xargs file
/home/david/.mozilla/plugins/libflashplayer.so:         ELF 64-bit LSB shared object, x86-64, version 1 (SYSV), dynamically linked, stripped
/usr/lib/firefox/plugins/npwrapper.libflashplayer.so:   broken symbolic link to `/var/lib/flashplugin-nonfree//npwrapper.libflashplayer.so'
/usr/lib/iceweasel/plugins/npwrapper.libflashplayer.so: broken symbolic link to `/var/lib/flashplugin-nonfree//npwrapper.libflashplayer.so'
/usr/lib/mozilla/plugins/libflashplayer.so:             ELF 64-bit LSB shared object, x86-64, version 1 (SYSV), dynamically linked, stripped
/usr/lib/mozilla/plugins/npwrapper.libflashplayer.so:   ERROR: cannot open `/usr/lib/mozilla/plugins/npwrapper.libflashplayer.so' (No such file or directory)


Where are those npwrappers coming from?  How do I fix the broken links?

---

### Post by taavikko on 2009-04-05
Either you have flashplugin installed from repos, or you have forgotten to remove those dependencies (64bit installs ia32-libs and nspluginwrapper)

---

### Post by Kareeser on 2009-04-05
The broken symbolic links should be removed at your earliest convenience.

You also seem to have the flash player installed in both plugins directories. Choose one.

---

### Post by biji on 2009-04-05
> **davidself1001 said:**
> Ok.  I tried to load the libflashplayer.so to ~.mozilla and now when I try to play a video it says I don't have the plugin installed.  I tried to re-apply the 64bit installer but still no dice.  Help!

We are talking about flash right? what video? try opening youtube.com does it worked?
:guitar:

---

### Post by davidself1001 on 2009-04-05
Yes I am talking about flash.  I have tried youtube and dailymotion. Both ask for me to install the latest flash player.  I have also removed the links via sudo rm -f xxx  but they still show up when I do the locate libflashplayer.  I should mention that I am using swiftfox which is a compiled version of FF for my particular processor.

---

### Post by taavikko on 2009-04-05
Using swiftfox shouldn't be the source of problems.

Remove all flashplugins and it's dependencies.
```
sudo apt-get --purge remove flashplugin-nonfree && sudo apt-get --purge autoremove
```

Remember to restart the browser;)

Now you should only have the manually installed libflashplayer.so from adobe, right?

---

### Post by davidself1001 on 2009-04-05
Ok did that.  Still no flash plugin.  Locate still show this after the above recommended purge/remove.

~/.mozilla/plugins$ locate libflashplayer.so
/home/david/.mozilla/plugins/libflashplayer.so
/usr/lib/firefox/plugins/npwrapper.libflashplayer.so
/usr/lib/iceweasel/plugins/npwrapper.libflashplayer.so
/usr/lib/mozilla/plugins/libflashplayer.so
/usr/lib/mozilla/plugins/npwrapper.libflashplayer.so

As mentioned earlier even though I removed all of the npwrappers they still show up when I do locate.  If you ls in those dirs they are not there.

---

### Post by taavikko on 2009-04-05
locate database needs to be updated "sudo updatedb"
Then it should not show any irrelevant results.

But your saying that flash still doesn't work?

---

### Post by davidself1001 on 2009-04-05
Ok, did the updatedb and now this shows in locate

~$ locate libflashplayer.so
/home/david/.mozilla/plugins/libflashplayer.so
/usr/lib/xulrunner-addons/plugins/libflashplayer.so

And correct I still have no flash when trying youtube videos.

---

### Post by phenest on 2009-04-05
And what if you put it in the location I suggested earlier?

/usr/lib/firefox-addons/plugins

Or with Iceweasel it might be:

/usr/lib/iceweasel-addons/plugins

I've never used Iceweasel.

---

### Post by ubersolid on 2009-04-05
[http://rubbad.wordpress.com/2008/11/25/flash-10-64bit-linux-alpha/](http://rubbad.wordpress.com/2008/11/25/flash-10-64bit-linux-alpha/)

That's how I do it. Title says alpha, but it's still the same. Sorry for the blogspam.

---

### Post by davidself1001 on 2009-04-05
No luck.  I tried copying the libflashplayer.so file to all /lib64/..plugins folders that might matter.  /firefox /mozilla /firefox-3.0.8 /swiftfox and still no plugin in swiftfox.

Man this is tough.

---

### Post by davidself1001 on 2009-04-06
Ok. Still no flash.  I've been off chasing another problem and am just getting back to this.  Any new ideas out there?  I have tried placing the libflashplayer.so file in all of the places below and still no flash in swiftfox.

~$ locate libflashplayer
/home/david/.mozilla/plugins/libflashplayer.so
/usr/lib/firefox/plugins/libflashplayer.so
/usr/lib/firefox-addons/plugins/libflashplayer.so
/usr/lib/mozilla/plugins/libflashplayer.so
/usr/lib/xulrunner-addons/plugins/libflashplayer.so
~$

---

### Post by ktp on 2009-04-06
What does firefox way you have installed for flash?  Type following in the address bar of firefox:

```
about:plugins
```

```
Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 10.0 r22

MIME Type 			Description 		Suffixes	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 		Yes
application/futuresplash 	FutureSplash Player 	spl 		Yes
```

---

### Post by davidself1001 on 2009-04-06
Doesn't show anything for flash.  How do I get it there?

Adobe Reader 8.0

    File name: nppdf.so
    The Adobe Reader plugin is used to enable viewing of PDF and FDF files from within the browser.

MIME Type 	Description 	Suffixes 	Enabled
application/pdf 	Portable Document Format 	pdf 	Yes
application/vnd.fdf 	Acrobat Forms Data Format 	fdf 	Yes
application/vnd.adobe.xfdf 	XML Version of Acrobat Forms Data Format 	xfdf 	Yes
application/vnd.adobe.xdp+xml 	Acrobat XML Data Package 	xdp 	Yes
application/vnd.adobe.xfd+xml 	Adobe FormFlow99 Data File 	xfd 	Yes
Helix DNA Plugin: RealPlayer G2 Plug-In Compatible

    File name: nphelix.so
    Helix DNA Plugin: RealPlayer G2 Plug-In Compatible version 0.4.0.4005 built with gcc 3.4.3 on Feb 25 2008

MIME Type 	Description 	Suffixes 	Enabled
audio/x-pn-realaudio-plugin 	RealPlayer Plugin Metafile 	rpm 	Yes

---

### Post by dBuster on 2009-04-06
Okay this is what I did and I did it from a clean install, however it is designed to remove any nspluginwrapper type setup there may be and it works correctly.

I have a script file I got from the following post:  [Adobe Flash 64 bit install script thanks to Kilz]("http://ubuntuforums.org/showthread.php?t=772490")

This is the script that I saved as Get64bitFlash2, after saving, right click on it and go to properties, then PERMISSIONS and make sure you put a check mark in "Allow executing file as program".  When you have done that double click on it and choose to Run it in a terminal.

```
## First we uninstall and remove all the existing flash packages

sudo apt-get -y purge nspluginwrapper
sudo apt-get -y purge mozilla-plugin-gnash
sudo apt-get -y purge swfdec-mozilla
sudo apt-get -y purge flashplugin-nonfree
sudo rm -rfd /usr/lib/nspluginwrapper
sudo rm -f /usr/lib/firefox-addons/plugins/libflashplayer.so
sudo rm -f /usr/lib/mozilla/plugins/flashplugin-alternative.so

## Then we make a temp folder and download the new plugin
cd /tmp/pluginstall
sudo wget  http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz

## Next we extract and place the plugin
sudo tar xvf libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz
sudo mv libflashplayer.so /usr/lib/mozilla/plugins/


elif [ "$refstr" = "no" ]
then
 echo "I am sorry but you have to agree. "

else
 echo  " I am sorry but you have to agree. "
 echo
fi
```

---

### Post by davidself1001 on 2009-04-06
Thanks for the file.  However, I have already done this process manually based on an earlier recommendation in this thread.  I did all the purge then rm steps and then downloaded the new v10 .so file and placed it everwhere in both lib and lib64 (ie firefox/plugins, mozillia/plugins/ firefox-3.0.8/plugins, swiftfox/plugins) and swiftfox still does not see it.  Could there be a config file somewhere that tells swiftfox where to find the plugins?

---

### Post by davidself1001 on 2009-04-06
Another question regarding plugins.  I thought that the sw that runs on a flash video was defined in the preferences/applications instead of the plugins.  Which one is it.  I have preferences/apps set to libflashplayer.so for flash video.

---

### Post by dBuster on 2009-04-06
I did not see the mention of Swiftfox until your most recent posts...  Sorry about that.

Does flash function properly in Firefox?  If so then the plugin is installed correctly.  And the script I posted will fix anything that may have been borked with the different attempts.  Believe me I did it myself on my 8.04 machine.

Also I just came across this... [http://ditoinfo.wordpress.com/2007/05/21/moving-and-using-firefox-plugins-on-swiftfox/]("http://ditoinfo.wordpress.com/2007/05/21/moving-and-using-firefox-plugins-on-swiftfox/")

>  There&#8217;s an platform independent installer on the website, but if it does not import the plugins for you, or, for some reason, you have installed it using another method (like Automatix, or tarball), you can create soft links from your existing plugins to use them on swift fox.

1. Go to /usr/lib/firefox/plugins

2. Do a &#8216;ls -l&#8217; so that you can see where the link points to

3. Now, create links on /opt/swiftfox/plugins to the original files

Tip: ln receives the target and then the name for the link (I always misplace them)

Example:

Giving ls -l you find out that the java plugin (firefox-javaplugin.so) is in /etc/alternatives/firefox-javaplugin.so. So you do a

ln -s /etc/alternatives/firefox-javaplugin.so /opt/swiftfox/plugins/

Swiftfox will automatically use the new plugins.

You could also check out:  [https://help.ubuntu.com/community/RestrictedFormats/Flash]("https://help.ubuntu.com/community/RestrictedFormats/Flash")  Looking particularly the part where it talks about patching swiftfox...   might work.

---

### Post by ktp on 2009-04-06
mine says use shockwave flash (in firefox).

---

### Post by davidself1001 on 2009-04-06
Did confirm that FF works with the plugin (but it's slower than SF by a mile it seems).  I did the link approach and now it doesn't give me the "need to install plugin" but instead I just get a white screen where the video should be playing and status shows done in the status bar.  I'm getting closer.  I also notice that I have sound when using FF which was my next problem that I have been trying to solve on SF.  When I had flash working I didn't have sound.  I am getting close to giving up and using FF but I still have a little more fight in me.  Any ideas on the white player screen?

---

### Post by Tamiyadd on 2009-04-17
white screen me too! any help? i have done the same thing of david!

---

