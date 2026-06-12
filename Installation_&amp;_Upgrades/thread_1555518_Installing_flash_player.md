---
title: "Installing flash player"
date: 2010-08-18
forum: Installation &amp; Upgrades
---

### Post by sukumarreddy on 2010-08-18
Hi friends,

I am using UBUNTU 10.04 64-bit . when I am trying to install flash player through synaptic package manager ,it will try to connect some website which is not reachable.I had tried to paste add-on to /usr/lib/firefox/Plugins, fail to play videos.

Can any body solve this problem.

---

### Post by zvacet on 2010-08-18
I don´t use it,but found [https://help.ubuntu.com/community/AMD64/FirefoxAndPlugins](https://help.ubuntu.com/community/AMD64/FirefoxAndPlugins) and [http://conradmiguel.com/install-flash-player-10-on-ubuntu-10-04-64-bit-lucid-lynx](http://conradmiguel.com/install-flash-player-10-on-ubuntu-10-04-64-bit-lucid-lynx)

---

### Post by JOHNNYG713 on 2010-08-18
close firefox Open your home folder,click view,show hidden files, Find .mozilla open it, create a new folder. name it, plugins ,place the libflash in the plugins folder and close home folder, open firefox, and go to your favorite video site and enjoy!
Google libflashplayer-10.0.22.87 That is the one I use!

---

### Post by sukumarreddy on 2010-08-18
Thank you very much

---

### Post by howefield on 2010-08-18
> **JOHNNYG713 said:**
> Google libflashplayer-10.0.22.87 That is the one I use!

You might want to explain the security issues in using that version of flash before recommending it.

---

### Post by howefield on 2010-08-18
> **sukumarreddy said:**
> 64-bit . when I am trying to install flash player through synaptic package manager ,it will try to connect some website which is not reachable.

To use the latest version of flash you would need the 32 bit version as the 64 bit version has been temporarily withdrawn.

The way to do this is to use flashplugin-installer via Synaptic Package Manager, which is giving you the issue, it is trying to download flash from Adobe website.

You could also try flash-aid, a firefox add-on.

[https://addons.mozilla.org/en-US/firefox/addon/161939/](https://addons.mozilla.org/en-US/firefox/addon/161939/)

This is useful as it will purge the system of any old versions before downloading the latest from Adobe.

---

### Post by sukumarreddy on 2010-08-18
I had copy pasted in home folder(i.e. ~/.mozilla/plugins/). But did not helped me.
I had used flash-aid. It says 32-bit flash player to be installed,in the running process it repeatedly connecting to adobe site since it is not responding.

How to solve by directly copy and pasting[COLOR=Red] libflashplayer.so[/COLOR] file.

---

### Post by Gwilmouski on 2010-08-18
Flash for 64 bit is not available right now, I can recommend 'Flash-Aid" which is available on Mozilla (add-ons page, I think). At this point it can only install 32 bit but promises to upgrade as soon 64 bit becomes available. It also will remove all the old flash and conflicting flash clones.

---

### Post by sukumarreddy on 2010-08-26
I had tried all the things, still flash player not working.
After loading data it just hang.See attachment.Can anybody have solution.

location of  libflashplayer.so file

```


$ sudo locate libflashplayer.so
/home/sukumarreddy/.local/share/Trash/expunged/3628705457/flash-plugin-10.1.82.76/debian/flash-plugin/usr/lib/flash-plugin/libflashplayer.so
/home/sukumarreddy/.local/share/Trash/expunged/3628705457/flash-plugin-10.1.82.76/usr/lib/flash-plugin/libflashplayer.so
/home/sukumarreddy/.mozilla/Plugins/libflashplayer.so
/home/sukumarreddy/.mozilla/plugins/libflashplayer.so
/usr/lib/firefox/plugins/libflashplayer.so
/usr/lib/mozilla-firefox/plugins/libflashplayer.so


```

---

