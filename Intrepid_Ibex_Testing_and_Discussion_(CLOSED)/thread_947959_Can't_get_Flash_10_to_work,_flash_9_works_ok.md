---
title: "Can't get Flash 10 to work, flash 9 works ok"
date: 2008-10-14
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by poit on 2008-10-14
OK, I've been banging my head against the wall for 3 days now trying to get this to work. I've been updating every day hoping that it will fix itself. I can't get Flash 10 to work in Firefox and Intreped. The best I can get is a grey screen wherever a flash element would be. When I manually install flash 9 locally it works with audio. Uninstall flash 9, and either manually install locally or use the install package in Synaptic, and I get the grey screen.  I get the feeling there is another dependency that isn't being satisfied, but I don't have a clue what. Has anyone figured this out yet?

---

### Post by psyke83 on 2008-10-14
> **poit said:**
> OK, I've been banging my head against the wall for 3 days now trying to get this to work. I've been updating every day hoping that it will fix itself. I can't get Flash 10 to work in Firefox and Intreped. The best I can get is a grey screen wherever a flash element would be. When I manually install flash 9 locally it works with audio. Uninstall flash 9, and either manually install locally or use the install package in Synaptic, and I get the grey screen.  I get the feeling there is another dependency that isn't being satisfied, but I don't have a clue what. Has anyone figured this out yet?

I assume you're using the 64-bit release? It's either a problem with nspluginwrapper or ia32-libs issue (probably the latter).

You need to see my [PulseAudio fixes]("http://ubuntuforums.org/showthread.php?t=866965") thread. A good start would be [this]("http://ubuntuforums.org/showthread.php?p=5895954#post5895954") post.

---

### Post by patrickballeux on 2008-10-15
Assuming you are running on AMD64...

For Flash 10 there are some dependencies that you need to complete using the getlib software...

You need to execute this:

getlibs -p libcurl3 
getlibs -p libnss3-1d 
getlibs -p libnspr4-0d 
getlibs -p libidn11
getlibs -p libssh2-1

This will put the 32 bits libraries needed for Flash 10.

Here is the full link : 
[http://forum.debian-fr.org/viewtopic.php?f=8&t=15890]("http://forum.debian-fr.org/viewtopic.php?f=8&t=15890")

[http://www.myscienceisbetter.info/2008/05/install-adobe-flash-player-10-on-ubuntu-using-nspluginwrapper.html]("http://www.myscienceisbetter.info/2008/05/install-adobe-flash-player-10-on-ubuntu-using-nspluginwrapper.html")

Good luck!

---

### Post by psyke83 on 2008-10-15
> **patrickballeux said:**
> Assuming you are running on AMD64...

For Flash 10 there are some dependencies that you need to complete using the getlib software...

You need to execute this:

getlibs -p libcurl3 
getlibs -p libnss3-1d 
getlibs -p libnspr4-0d 
getlibs -p libidn11
getlibs -p libssh2-1

This will put the 32 bits libraries needed for Flash 10.

Here is the full link : 
[http://forum.debian-fr.org/viewtopic.php?f=8&t=15890]("http://forum.debian-fr.org/viewtopic.php?f=8&t=15890")

[http://www.myscienceisbetter.info/2008/05/install-adobe-flash-player-10-on-ubuntu-using-nspluginwrapper.html]("http://www.myscienceisbetter.info/2008/05/install-adobe-flash-player-10-on-ubuntu-using-nspluginwrapper.html")

Good luck!

No, most of those libraries are in ia32-libs already. There's just one library missing, mentioned in the link I gave above.

---

### Post by poit on 2008-10-15
sorry. should have mentioned it's 32 bit on an old T30 laptop.  Also, looks like Adobe released flash 10 as now I can't even download flash 9 from their site.

---

### Post by jfernyhough on 2008-10-15
Try purging flashplugin-nonfree, then libflashsupport (it's not needed for Flash 10), then install flashplugin-nonfree

sudo aptitude purge flashplugin-nonfree
sudo aptitude purge libflashsupport
sudo aptitude install flashplugin-nonfree

---

### Post by psyke83 on 2008-10-15
> **poit said:**
> sorry. should have mentioned it's 32 bit on an old T30 laptop.  Also, looks like Adobe released flash 10 as now I can't even download flash 9 from their site.

Ok, then:

```
$ sudo apt-get remove --purge nspluginwrapper libflashsupport flashplugin-nonfree
$ sudo updatedb
$ locate libflashplayer.so
```

Delete any remaining instances of libflashplayer.so, and then reinstall flashplugin-nonfree. **Don't** install the deb from Adobe's site, it won't integrate well.

You can either wait for the final release of the flash 10 package to get pushed, or download it from Fabien Tassin's PPA:
```
$ wget -c http://ppa.launchpad.net/fta/ubuntu/pool/main/f/flashplugin-nonfree/flashplugin-nonfree_10.0.12.36ubuntu1~fta1_i386.deb
$ sudo dpkg -i flashplugin-nonfree_10.0.12.36ubuntu1~fta1_i386.deb
```

---

### Post by poit on 2008-10-15
> **jfernyhough said:**
> Try purging flashplugin-nonfree, then libflashsupport (it's not needed for Flash 10), then install flashplugin-nonfree

sudo aptitude purge flashplugin-nonfree
sudo aptitude purge libflashsupport
sudo aptitude install flashplugin-nonfree

I just tried that, still no flash. I've also done everything in psyke83's pulseaudio post, still no flash. Firefox isn't even seeing the flash plugin, and websites complain that I need the flash plugin. What would be keeping firefox from seeing the plugin at all now?

---

### Post by psyke83 on 2008-10-15
> **poit said:**
> I just tried that, still no flash. I've also done everything in psyke83's pulseaudio post, still no flash. Firefox isn't even seeing the flash plugin, and websites complain that I need the flash plugin. What would be keeping firefox from seeing the plugin at all now?

Make sure you've followed the steps my previous post. If it still didn't help, post the output of: ```
$ ldd /usr/lib/flashplugin-nonfree/libflashplayer.so
```

---

### Post by philinux on 2008-10-15
psyke,

As he's on 32 bit would this not be a better idea. assuming all the flash is purged first.
[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux)

---

### Post by poit on 2008-10-15
> **psyke83 said:**
> Make sure you've followed the steps my previous post. If it still didn't help, post the output of: ```
$ ldd /usr/lib/flashplugin-nonfree/libflashplayer.so
```


Here's the output:

```
dale@eckles:~$ ldd /usr/lib/flashplugin-nonfree/libflashplayer.so
	linux-gate.so.1 =>  (0xb8096000)
	libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0xb7526000)
	libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb750d000)
	libX11.so.6 => /usr/lib/libX11.so.6 (0xb741d000)
	libXext.so.6 => /usr/lib/libXext.so.6 (0xb740e000)
	libXt.so.6 => /usr/lib/libXt.so.6 (0xb73bd000)
	libfreetype.so.6 => /usr/lib/libfreetype.so.6 (0xb7347000)
	libfontconfig.so.1 => /usr/lib/libfontconfig.so.1 (0xb731a000)
	libgtk-x11-2.0.so.0 => /usr/lib/libgtk-x11-2.0.so.0 (0xb6f7c000)
	libgdk-x11-2.0.so.0 => /usr/lib/libgdk-x11-2.0.so.0 (0xb6eef000)
	libatk-1.0.so.0 => /usr/lib/libatk-1.0.so.0 (0xb6ed3000)
	libgdk_pixbuf-2.0.so.0 => /usr/lib/libgdk_pixbuf-2.0.so.0 (0xb6eb9000)
	libpangocairo-1.0.so.0 => /usr/lib/libpangocairo-1.0.so.0 (0xb6eae000)
	libpango-1.0.so.0 => /usr/lib/libpango-1.0.so.0 (0xb6e6b000)
	libcairo.so.2 => /usr/lib/libcairo.so.2 (0xb6df8000)
	libgobject-2.0.so.0 => /usr/lib/libgobject-2.0.so.0 (0xb6db9000)
	libgmodule-2.0.so.0 => /usr/lib/libgmodule-2.0.so.0 (0xb6db4000)
	libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb6db0000)
	libglib-2.0.so.0 => /usr/lib/libglib-2.0.so.0 (0xb6cf9000)
	libnss3.so => not found
	libsmime3.so => not found
	libssl3.so => not found
	libplds4.so => /usr/lib/libplds4.so (0xb6cf4000)
	libplc4.so => /usr/lib/libplc4.so (0xb6cef000)
	libnspr4.so => /usr/lib/libnspr4.so (0xb6cb9000)
	libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb6c92000)
	libgcc_s.so.1 => /lib/libgcc_s.so.1 (0xb6c83000)
	libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb6b25000)
	/lib/ld-linux.so.2 (0xb8097000)
	libxcb-xlib.so.0 => /usr/lib/libxcb-xlib.so.0 (0xb6b22000)
	libxcb.so.1 => /usr/lib/libxcb.so.1 (0xb6b09000)
	libXau.so.6 => /usr/lib/libXau.so.6 (0xb6b05000)
	libSM.so.6 => /usr/lib/libSM.so.6 (0xb6afc000)
	libICE.so.6 => /usr/lib/libICE.so.6 (0xb6ae4000)
	libz.so.1 => /usr/lib/libz.so.1 (0xb6ace000)
	libexpat.so.1 => /usr/lib/libexpat.so.1 (0xb6aa7000)
	libXcomposite.so.1 => /usr/lib/libXcomposite.so.1 (0xb6aa2000)
	libXdamage.so.1 => /usr/lib/libXdamage.so.1 (0xb6a9f000)
	libXfixes.so.3 => /usr/lib/libXfixes.so.3 (0xb6a9a000)
	libgio-2.0.so.0 => /usr/lib/libgio-2.0.so.0 (0xb6a32000)
	libpangoft2-1.0.so.0 => /usr/lib/libpangoft2-1.0.so.0 (0xb6a0a000)
	libXrender.so.1 => /usr/lib/libXrender.so.1 (0xb69ff000)
	libXinerama.so.1 => /usr/lib/libXinerama.so.1 (0xb69fc000)
	libXi.so.6 => /usr/lib/libXi.so.6 (0xb69f2000)
	libXrandr.so.2 => /usr/lib/libXrandr.so.2 (0xb69eb000)
	libXcursor.so.1 => /usr/lib/libXcursor.so.1 (0xb69e2000)
	libpixman-1.so.0 => /usr/lib/libpixman-1.so.0 (0xb699f000)
	libpng12.so.0 => /usr/lib/libpng12.so.0 (0xb6979000)
	libxcb-render-util.so.0 => /usr/lib/libxcb-render-util.so.0 (0xb6974000)
	libxcb-render.so.0 => /usr/lib/libxcb-render.so.0 (0xb696c000)
	libpcre.so.3 => /lib/libpcre.so.3 (0xb6942000)
	libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0xb693c000)
	libselinux.so.1 => /lib/libselinux.so.1 (0xb6922000)

```

Again, firefox doesn't see the flash plugin at all. It doesn't show up in the about: plugins list. 

Thanks again for all the help.

---

### Post by psyke83 on 2008-10-15
> **philinux said:**
> psyke,

As he's on 32 bit would this not be a better idea. assuming all the flash is purged first.
[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux)

No, I'm referring to post #7, which took into account that he's using the 32bit release. Installing the plugin manually is never, never, never a good idea. It will always cause problems upon official upgrades in the repositories.

The final release has been pushed to the archive by ubulette, it should be built in a little while.

---

### Post by psyke83 on 2008-10-15
> **poit said:**
> Here's the output:

```
dale@eckles:~$ ldd /usr/lib/flashplugin-nonfree/libflashplayer.so
	linux-gate.so.1 =>  (0xb8096000)
	libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0xb7526000)
	libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb750d000)
	libX11.so.6 => /usr/lib/libX11.so.6 (0xb741d000)
	libXext.so.6 => /usr/lib/libXext.so.6 (0xb740e000)
	libXt.so.6 => /usr/lib/libXt.so.6 (0xb73bd000)
	libfreetype.so.6 => /usr/lib/libfreetype.so.6 (0xb7347000)
	libfontconfig.so.1 => /usr/lib/libfontconfig.so.1 (0xb731a000)
	libgtk-x11-2.0.so.0 => /usr/lib/libgtk-x11-2.0.so.0 (0xb6f7c000)
	libgdk-x11-2.0.so.0 => /usr/lib/libgdk-x11-2.0.so.0 (0xb6eef000)
	libatk-1.0.so.0 => /usr/lib/libatk-1.0.so.0 (0xb6ed3000)
	libgdk_pixbuf-2.0.so.0 => /usr/lib/libgdk_pixbuf-2.0.so.0 (0xb6eb9000)
	libpangocairo-1.0.so.0 => /usr/lib/libpangocairo-1.0.so.0 (0xb6eae000)
	libpango-1.0.so.0 => /usr/lib/libpango-1.0.so.0 (0xb6e6b000)
	libcairo.so.2 => /usr/lib/libcairo.so.2 (0xb6df8000)
	libgobject-2.0.so.0 => /usr/lib/libgobject-2.0.so.0 (0xb6db9000)
	libgmodule-2.0.so.0 => /usr/lib/libgmodule-2.0.so.0 (0xb6db4000)
	libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb6db0000)
	libglib-2.0.so.0 => /usr/lib/libglib-2.0.so.0 (0xb6cf9000)
	libnss3.so => not found
	libsmime3.so => not found
	libssl3.so => not found
	libplds4.so => /usr/lib/libplds4.so (0xb6cf4000)
	libplc4.so => /usr/lib/libplc4.so (0xb6cef000)
	libnspr4.so => /usr/lib/libnspr4.so (0xb6cb9000)
	libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb6c92000)
	libgcc_s.so.1 => /lib/libgcc_s.so.1 (0xb6c83000)
	libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb6b25000)
	/lib/ld-linux.so.2 (0xb8097000)
	libxcb-xlib.so.0 => /usr/lib/libxcb-xlib.so.0 (0xb6b22000)
	libxcb.so.1 => /usr/lib/libxcb.so.1 (0xb6b09000)
	libXau.so.6 => /usr/lib/libXau.so.6 (0xb6b05000)
	libSM.so.6 => /usr/lib/libSM.so.6 (0xb6afc000)
	libICE.so.6 => /usr/lib/libICE.so.6 (0xb6ae4000)
	libz.so.1 => /usr/lib/libz.so.1 (0xb6ace000)
	libexpat.so.1 => /usr/lib/libexpat.so.1 (0xb6aa7000)
	libXcomposite.so.1 => /usr/lib/libXcomposite.so.1 (0xb6aa2000)
	libXdamage.so.1 => /usr/lib/libXdamage.so.1 (0xb6a9f000)
	libXfixes.so.3 => /usr/lib/libXfixes.so.3 (0xb6a9a000)
	libgio-2.0.so.0 => /usr/lib/libgio-2.0.so.0 (0xb6a32000)
	libpangoft2-1.0.so.0 => /usr/lib/libpangoft2-1.0.so.0 (0xb6a0a000)
	libXrender.so.1 => /usr/lib/libXrender.so.1 (0xb69ff000)
	libXinerama.so.1 => /usr/lib/libXinerama.so.1 (0xb69fc000)
	libXi.so.6 => /usr/lib/libXi.so.6 (0xb69f2000)
	libXrandr.so.2 => /usr/lib/libXrandr.so.2 (0xb69eb000)
	libXcursor.so.1 => /usr/lib/libXcursor.so.1 (0xb69e2000)
	libpixman-1.so.0 => /usr/lib/libpixman-1.so.0 (0xb699f000)
	libpng12.so.0 => /usr/lib/libpng12.so.0 (0xb6979000)
	libxcb-render-util.so.0 => /usr/lib/libxcb-render-util.so.0 (0xb6974000)
	libxcb-render.so.0 => /usr/lib/libxcb-render.so.0 (0xb696c000)
	libpcre.so.3 => /lib/libpcre.so.3 (0xb6942000)
	libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0xb693c000)
	libselinux.so.1 => /lib/libselinux.so.1 (0xb6922000)

```

Again, firefox doesn't see the flash plugin at all. It doesn't show up in the about: plugins list. 

Thanks again for all the help.

You're missing some libraries.

Try:
```
$ sudo apt-get install --reinstall libnss3-1d
```

The libraries may be on your system, but not symlinked correctly.

Please post the output of:
```
$ sudo updatedb
$ dpkg -S libnss3.so*
$ locate libnss3.so*

```

---

### Post by poit on 2008-10-15
> **psyke83 said:**
> You're missing some libraries.

Try:
```
$ sudo apt-get install --reinstall libnss3-1d
```

The libraries may be on your system, but not symlinked correctly.

Please post the output of:
```
$ sudo updatedb
$ dpkg -S libnss3.so*
$ locate libnss3.so*

```

I can't reinstall libnss3-ld, I get the message:

Reinstallation of libnss3-1d is not possible, it cannot be downloaded.

I'm assuming I'm missing a repository. Any idea where it lives?

The locate doesn't find any instances on my computer.

---

### Post by psyke83 on 2008-10-15
> **poit said:**
> I can't reinstall libnss3-ld, I get the message:

Reinstallation of libnss3-1d is not possible, it cannot be downloaded.

I'm assuming I'm missing a repository. Any idea where it lives?

The locate doesn't find any instances on my computer.

That package is from the main archive, so you shouldn't be missing that repository. It seems more likely you have a conflicting package.

Post the output I requested, please.

---

### Post by poit on 2008-10-15
> **psyke83 said:**
> That package is from the main archive, so you shouldn't be missing that repository. It seems more likely you have a conflicting package.

Post the output I requested, please.
Here's the output:


```
dale@eckles:~$ sudo updatedb
dale@eckles:~$  dpkg -S libnss3.so*
thunderbird: /usr/lib/thunderbird/libnss3.so
libnss3-1d: /usr/lib/libnss3.so.1d
dale@eckles:~$ locate libnss3.so*
dale@eckles:~$ 
```

---

### Post by psyke83 on 2008-10-15
> **poit said:**
> Here's the output:


```
dale@eckles:~$ sudo updatedb
dale@eckles:~$  dpkg -S libnss3.so*
thunderbird: /usr/lib/thunderbird/libnss3.so
libnss3-1d: /usr/lib/libnss3.so.1d
dale@eckles:~$ locate libnss3.so*
dale@eckles:~$ 
```

Can you (temporarily) uninstall thunderbird, and try installing libnss3-1d again?

---

### Post by poit on 2008-10-15
> **psyke83 said:**
> Can you (temporarily) uninstall thunderbird, and try installing libnss3-1d again?

Doesn't seem to make a difference. I uninstalled thunderbird, (afraid to do a full purge right now) 

the instance linked to thunderbird is gone:
dale@eckles:~$ dpkg -S libnss3.so*
libnss3-1d: /usr/lib/libnss3.so.1d

Still get the same message though:

dale@eckles:~$ sudo apt-get install --reinstall libnss3-1d
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reinstallation of libnss3-1d is not possible, it cannot be downloaded.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by psyke83 on 2008-10-15
> **poit said:**
> Doesn't seem to make a difference. I uninstalled thunderbird, (afraid to do a full purge right now) 

the instance linked to thunderbird is gone:
dale@eckles:~$ dpkg -S libnss3.so*
libnss3-1d: /usr/lib/libnss3.so.1d

Still get the same message though:

dale@eckles:~$ sudo apt-get install --reinstall libnss3-1d
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reinstallation of libnss3-1d is not possible, it cannot be downloaded.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Did you enable a third-party repository with Mozilla (Firefox/Thunderbird, etc) packages?

Post the output of:
```
$ apt-cache policy libnss3-1d
```

---

### Post by poit on 2008-10-15
> **psyke83 said:**
> Did you enable a third-party repository with Mozilla (Firefox/Thunderbird, etc) packages?



Post the output of:
```
$ apt-cache policy libnss3-1d
```

Not that I know of. This is an upgrade to intreped, but I am using just the assigned repositories, except for the addition of yours.

Here you go:

```
dale@eckles:~$ apt-cache policy libnss3-1d
libnss3-1d:
  Installed: 3.12.1~cvs20080501t1828-0ubuntu1~fta1~hardy
  Candidate: 3.12.1~cvs20080501t1828-0ubuntu1~fta1~hardy
  Version table:
 *** 3.12.1~cvs20080501t1828-0ubuntu1~fta1~hardy 0
        100 /var/lib/dpkg/status
     3.12.0.3-0ubuntu5 0
        500 http://mirrors.xmission.com intrepid/main Packages
dale@eckles:~$ 
```

---

### Post by psyke83 on 2008-10-15
> **poit said:**
> Not that I know of. This is an upgrade to intreped, but I am using just the assigned repositories, except for the addition of yours.

Here you go:

```
dale@eckles:~$ apt-cache policy libnss3-1d
libnss3-1d:
  Installed: 3.12.1~cvs20080501t1828-0ubuntu1~fta1~hardy
  Candidate: 3.12.1~cvs20080501t1828-0ubuntu1~fta1~hardy
  Version table:
 *** 3.12.1~cvs20080501t1828-0ubuntu1~fta1~hardy 0
        100 /var/lib/dpkg/status
     3.12.0.3-0ubuntu5 0
        500 http://mirrors.xmission.com intrepid/main Packages
dale@eckles:~$ 
```

Ok, those third-party repositories are causing problems.

What I recommend is that you disable *all* third-party repositories and attempt to downgrade as many packages as possible back to the official versions.

Look at my post here: [http://ubuntuforums.org/showpost.php?p=5967675&postcount=27](http://ubuntuforums.org/showpost.php?p=5967675&postcount=27)

Although in that post I'm describing how to downgrade packages to the Hardy version, in principle everything is the same. The only thing you need to keep in mind is that if you need to downgrade via the terminal, use the syntax "<packagename>/intrepid".

---

### Post by poit on 2008-10-15
> **psyke83 said:**
> Ok, those third-party repositories are causing problems.

What I recommend is that you disable *all* third-party repositories and attempt to downgrade as many packages as possible back to the official versions.

Look at my post here: [http://ubuntuforums.org/showpost.php?p=5967675&postcount=27](http://ubuntuforums.org/showpost.php?p=5967675&postcount=27)

Although in that post I'm describing how to downgrade packages to the Hardy version, in principle everything is the same. The only thing you need to keep in mind is that if you need to downgrade via the terminal, use the syntax "<packagename>/intrepid".
OK, I just did something real stupid and pretty much uninstalled my whole sytem. No desktop, not much past the kernal. I'll need to reinstall from the command line at this point. I don't know if I have much more time to deal with this now, and I'm hoping that when I do reinstall things will just work. We'll see. 
Anyway, thanks for all the help.

---

### Post by ubulette on 2008-10-15
> **poit said:**
> Not that I know of. This is an upgrade to intreped, but I am using just the assigned repositories, except for the addition of yours.

Here you go:

```
dale@eckles:~$ apt-cache policy libnss3-1d
libnss3-1d:
  Installed: 3.12.1~cvs20080501t1828-0ubuntu1~fta1~hardy
  Candidate: 3.12.1~cvs20080501t1828-0ubuntu1~fta1~hardy
  Version table:
 *** 3.12.1~cvs20080501t1828-0ubuntu1~fta1~hardy 0
        100 /var/lib/dpkg/status
     3.12.0.3-0ubuntu5 0
        500 http://mirrors.xmission.com intrepid/main Packages
dale@eckles:~$ 
```

those are very old packages from my PPA, and for hardy, not even for intrepid.

If you are running intrepid, using old debs from hardy is not a good idea. If for some reasons you don't want to update those packages, you'd better not use PPAs at all as it will sure cause unnecessary troubles.

The problem you have with nss is long gone. In fact, it is/was not even a problem as it was fine at that time but a lot of things changed since.

---

### Post by McQuaid on 2008-10-15
I have the same problem, flash 9 via the repository pkg works fine.  Installed the deb from adobe, installs successfully but no flash at all.  I don't get a gray box or anything, web sites like youtube state flash isn't installed.  about:plugins does not show flash details.

I thought something might be borked in my ~/mozilla acct, tried as another user with a fresh .mozilla dir, same thing.  Not really sure what to do now.  I removed 10, went back to 9 no problems.  I removed 9 again, installed 10, back to the same thing.

I"m running hardy 8.04 32bit. I don't have any mixed sources like something from intrepid, but I do have a couple un-official reps.  One is for xbmc, and the other is for multimedia codecs.  I scanned through those in the sections and don't see anything from those sources that should be from official, or anything that would remotely affect firefox.

got it working.  I needed to upgrade libnspr4-0d.

I kinda figured this out when running ldd libflashplayer.so in the dir containing flash10

I got:
        libplds4.so => not found
        libplc4.so => not found
        libnspr4.so => not found

Was up to date on plds but spr had an update available.  Maybe this should be a dep?

---

### Post by Justin Trouble on 2008-10-16
> **ubulette said:**
> those are very old packages from my PPA, and for hardy, not even for intrepid.

If you are running intrepid, using old debs from hardy is not a good idea. If for some reasons you don't want to update those packages, you'd better not use PPAs at all as it will sure cause unnecessary troubles.

The problem you have with nss is long gone. In fact, it is/was not even a problem as it was fine at that time but a lot of things changed since.

Thanks to everyone's help on this thread!

I am running 32 bit Kubuntu 8.10 Intrepid with the flashplugin-nonfree package installed.

I had the same problem with Flash 10, and I had the same problem with the Hardy version of libnss3-1d (3.12.1~cvs20080501t1828-0ubuntu1~fta1~hardy) installed and causing problems (see [http://ubuntuforums.org/showpost.php?p=5972101&postcount=23](http://ubuntuforums.org/showpost.php?p=5972101&postcount=23)).

I solved the problem by:

[LIST=1]
[*]Downloading the Intrepid version of libnss3-1d from [http://packages.ubuntu.com/intrepid/libnss3-1d](http://packages.ubuntu.com/intrepid/libnss3-1d)
[*]Running: sudo dpkg -i --force-downgrade libnss3-1d_3.12.0.3-0ubuntu5_i386.deb
```

# dpkg -i --force-downgrade libnss3-1d_3.12.0.3-0ubuntu5_i386.deb
dpkg - warning: downgrading libnss3-1d from 3.12.1~cvs20080501t1828-0ubuntu1~fta1~hardy to 3.12.0.3-0ubuntu5.
(Reading database ... 227407 files and directories currently installed.)
Preparing to replace libnss3-1d 3.12.1~cvs20080501t1828-0ubuntu1~fta1~hardy (using .../libnss3-1d_3.12.0.3-0ubuntu5_i386.deb) ...
Unpacking replacement libnss3-1d ...
Setting up libnss3-1d (3.12.0.3-0ubuntu5) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place

```
[/LIST]

```
ldd /usr/lib/flashplugin-nonfree/libflashplayer.so
``` now shows no missing libraries and

```
Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 10.0 r12
```
appears in Firefox's about:plugins page!

I hope this helps others.

---

### Post by kickbackSpain on 2008-10-16
Hi! I'm an Ubuntu user from Spain and I had the same problem. Until I've read this thread I was very lost. Finally (thank you) I got flash 10 working perfectly.
I want to give a suggestion: I read [here]("http://ubuntulife.wordpress.com/2008/09/28/flash-player-10-rc2/#comment-9223")some instructions to install Flash 10 RC2 and the final lines say the following: make some links in that way. 

sudo ln -s /usr/lib/libssl3.so.1d /usr/lib/libssl3.so
sudo ln -s /usr/lib/libnss3.so.1d /usr/lib/libnss3.so
sudo ln -s /usr/lib/libnspr4.so.0d /usr/lib/libnspr4.so
sudo ln -s /usr/lib/libsmime3.so.1d /usr/lib/libsmime3.so
sudo ln -s /usr/lib/libplds4.so.0d /usr/lib/libplds4.so
sudo ln -s /usr/lib/libplc4.so.0d /usr/lib/libplc4.so

That works for me, and I want post it because I think it could be useful and it's related with the content of the last posts.

Thank you and hope see you soon!

PD: sorry for my poor English!

---

### Post by poit on 2008-10-16
OK, 
I''m back!

Thanks to everyone for the help, and hopefully this helped someone else besides me. 

Since I ended up accidentally deleting a bunch of packages I ended up reinstalling Hardy from CD. After I got that working I ran the online upgrade to Intrepid. Now flash seems to work fine. I suspect the ppa repositories may have been the issue, but I'll never know now.

---

### Post by DigitaLink on 2008-10-28
Justin - THANK YOU!!!  The forced downgrade made Flash magically re-appear in Firefox.

That was drivin' me NUTS!!  I installed it manually ... I installed it from the command line installer ... I installed the .deb ... I installed through Synaptic ... I installed from apt-get CLI ... NOTHING!

Now I have flashy goodness again.  Thank you!!

---

