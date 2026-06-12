---
title: "Flash player installation instructions please."
date: 2010-08-22
forum: Installation &amp; Upgrades
---

### Post by RavenStandsAlone on 2010-08-22
Running Ubuntu 9.04 on Dual core Intel x64. I have downloaded all versions of the flash player. There are four separate packages in my Download manager. What is the terminal command line to get this to install.  In my package installer I have this: Error: Wrong architecture 'i386' WTF?

---

### Post by sikander3786 on 2010-08-22
I use to install flash player via firefox where it says "install missing plugins".

You are getting the Wrong Architecture message may be because you are running 64-Bit OS. However it is possible to install 32-Bit flash on 64-Bit Firefox.

[This]("https://help.ubuntu.com/community/AMD64/FirefoxAndPlugins") page might help you installing 64-bit flash player (if that is the problem).

Regards.

---

### Post by lovinglinux on 2010-08-22
Get [FLASH-AID](https://addons.mozilla.org/en-US/firefox/addon/161939/), an extension to remove conflicting flash plugins and install the proper version according to your browser architecture.

---

### Post by mango42 on 2010-08-23
Hi **lovinglinux** - thanks for your efforts to sort out flash plugin problems but it seems that with 10.04.1 it no longer works. On this T43 Thinkpad, Firefox now keeps the CPU working at 100%, no streaming (audio or video) works anymore whatever I try (apart from Adobe, who doesn't have updated drivers for anything beyond Ubuntu 9.04 - not that I would use any code from such a dubious closed source, anyway!)

Same applies more or less with Opera, except it doesn't hog the CPU to anything like the same extent - but Flash is just as non-functional.

What is going on here - does Ubuntu really want to fold to Der Grosse G00gle and take up their all inclusive (yeah right!) Chrome (which apparently does work with Flash!!)

I really feel this issue needs carefully looking into at the political as well as the technical level.

Or are the Linux developers content to allow the likes of Jay Rockefeller to dictate to humanity what can, and what can't be, accessed on the net?

Carry on like this and we may as well go back to being brainless, passive TeeVee gawpers!

A very sad day for Ubuntu, methinks - if this issue cannot be sorted without being herded into g00gle, this will be the very first time I wipe an upgrade and revert to 9.10...

---

### Post by lovinglinux on 2010-08-23
> **mango42 said:**
> Hi **lovinglinux** - thanks for your efforts to sort out flash plugin problems but it seems that with 10.04.1 it no longer works. On this T43 Thinkpad, Firefox now keeps the CPU working at 100%, no streaming (audio or video) works anymore whatever I try (apart from Adobe, who doesn't have updated drivers for anything beyond Ubuntu 9.04 - not that I would use any code from such a dubious closed source, anyway!)

Same applies more or less with Opera, except it doesn't hog the CPU to anything like the same extent - but Flash is just as non-functional.

What is going on here - does Ubuntu really want to fold to Der Grosse G00gle and take up their all inclusive (yeah right!) Chrome (which apparently does work with Flash!!)

I really feel this issue needs carefully looking into at the political as well as the technical level.

Or are the Linux developers content to allow the likes of Jay Rockefeller to dictate to humanity what can, and what can't be, accessed on the net?

Carry on like this and we may as well go back to being brainless, passive TeeVee gawpers!

A very sad day for Ubuntu, methinks - if this issue cannot be sorted without being herded into g00gle, this will be the very first time I wipe an upgrade and revert to 9.10...

Unfortunately, the Adobe plugin is the one that works "best". Chrome works with flash because they distribute the flash plugin shared object with the browser. But if you copy the .so from Chrome and use it with Firefox, you will see that it works too (not recommend tho).

Please provide the output of the following commands and instructions. This will make sure I will have a good understanding of your Firefox and Flash installations, so I don't need to guess what might be happening to your system:

**1 - Flash Version**

Type **about[noparse]:[/noparse]config** in Firefox address bar, then type **plugin.expose_full_path** in the filter, then double-click the same item in the results to make it **true**. Then type **about[noparse]:[/noparse]plugins** in the address bar, find Shockwave Flash, copy the corresponding Path and Version and paste here. it should look lie the image below:

[IMG]http://tinyurl.com/287j7on[/IMG]

**2 - Firefox version and architecture**

To find Firefox version and architecture, click "Help >> About Mozilla Firefox" in the menu. The info will be located at the bottom of the info dialog (you need to resize the window to see it):

[IMG]http://tinyurl.com/26b85o2[/IMG]


**3 - System Info**

Execute the following commands then copy the generated file, named **firefox-report.txt** from your Desktop and upload it here or paste the contents.

To execute those commands, select the entire content below, then go to "Applications >> Accessories >> Terminal" and click the terminal with the middle-mouse button.

```

echo 'Ubuntu Architecture' > ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
uname -a >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Ubuntu Version' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
cat /etc/lsb-release >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox Packages' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
dpkg --get-selections | grep 'firefox*' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox binaries' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
which firefox >> ~/Desktop/firefox-report.txt
file /usr/bin/firefox >> ~/Desktop/firefox-report.txt
file /usr/local/bin/firefox >> ~/Desktop/firefox-report.txt
file /opt/firefox/firefox >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox divertion' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
file /usr/bin/firefox.ubuntu >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Sources' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
ls /etc/apt/sources.list.d >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Flash packages' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
dpkg --get-selections | grep 'flash*' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Plugin locations' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
locate libflashplayer.so  >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
locate flashplugin-alternative.so  >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Flash symlinks' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
file /usr/lib/firefox-addons/plugins/libflashplayer.so  >> ~/Desktop/firefox-report.txt
file /usr/lib/mozilla/plugins/flashplugin-alternative.so  >> ~/Desktop/firefox-report.txt
file /etc/alternatives/mozilla-flashplugin  >> ~/Desktop/firefox-report.txt
file /var/lib/flashplugin-installer/npwrapper.libflashplayer.so  >> ~/Desktop/firefox-report.txt
firefox ~/Desktop/firefox-report.txt
```

---

