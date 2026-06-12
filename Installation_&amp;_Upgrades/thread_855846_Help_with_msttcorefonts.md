---
title: "Help with msttcorefonts"
date: 2008-07-10
forum: Installation &amp; Upgrades
---

### Post by James20 on 2008-07-10
Dear Gentleman

I am a new user to linux, and whenever I try to install an application, particulately the K---- ones, eg ktechlabs I get this error

 sudo apt-get install ktechlab
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ktechlab is already the newest version.
The following packages were automatically installed and are no longer required:
  koffice-data libruby1.8
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up msttcorefonts (2.4) ...

These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.

Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
andale32.exe: No such file or directory

All done, errors in processing 1 file(s)
dpkg: error processing msttcorefonts (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 msttcorefonts
E: Sub-process /usr/bin/dpkg returned an error code (1)


Obviously in this instance i alread have this applied, however I cannot find it on my computor, and a lot of these htings give me the msttcorefonts error.

DOes anyone have anything i can do to remedy this?

---

### Post by iaculallad on 2008-07-10
EDIT: Disregard the first post, connection was OK.

Try to edit /var/lib/dpkg/info/msttcorefonts.postinst - and comment out the values below by placing the # sign before the line of text.

```
gksudo gedit /var/lib/dpkg/info/msttcorefonts.postinst -
```

and comment out:

> db_get msttcorefonts/http_proxy
http_proxy=$RET

to:

> # db_get msttcorefonts/http_proxy
# http_proxy=$RET



Then try to purge the ms fonts using terminal and retry install K applications.

```
sudo apt-get remove --purge msttcorefonts
```

---

### Post by James20 on 2008-07-13
OK, so I followed those previous instructions, and unfortunately got the same error while purging!

Any ideas?

james@james-laptop:~$ gksudo gedit /var/lib/dpkg/info/msttcorefonts.postinst -
james@james-laptop:~$ sudo apt-get remove --purge msttcorefonts
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libclucene0ldbl libxine1-x librdf0 libxine1-misc-plugins kdebase-data
  libxcb-xv0 libexiv2-2 libxine1-bin koffice-data librasqal0 krita-data-kde4
  libxine1-ffmpeg libgmp3c2 kdelibs5-data libxcb-shape0 libstreamanalyzer0
  libxine1-plugins libxvmc1 libpq5 libstreams0 libraptor1 libmodplug0c2
  libruby1.8 libxcb-shm0 kdepimlibs-data koffice-data-kde4 libxine1-console
  libxine1
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  msttcorefonts*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 201kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 113862 files and directories currently installed.)
Removing msttcorefonts ...
W: /usr/share/fonts/truetype/msttcorefonts/Verdana.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Arial_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Arial.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Arial_Bold_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Comic_Sans_MS_Bold.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Andale_Mono.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Times_New_Roman_Bold.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Georgia.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Courier_New_Bold.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Trebuchet_MS_Bold_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Times_New_Roman_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Comic_Sans_MS.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Trebuchet_MS_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Times_New_Roman.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Trebuchet_MS.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Georgia_Bold.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Verdana_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Arial_Bold.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Courier_New_Bold_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Georgia_Bold_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Verdana_Bold_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Courier_New.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Webdings.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Arial_Black.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Courier_New_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Times_New_Roman_Bold_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Trebuchet_MS_Bold.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Impact.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Verdana_Bold.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Georgia_Italic.ttf: not registered.
dpkg: error processing msttcorefonts (--purge):
 subprocess pre-removal script returned error exit status 1

These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.

Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
andale32.exe: No such file or directory

All done, errors in processing 1 file(s)
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 msttcorefonts
E: Sub-process /usr/bin/dpkg returned an error code (1)
james@james-laptop:~$

---

### Post by James20 on 2008-07-15
Any ideas?

---

### Post by coffeecat on 2008-07-15
> **James20 said:**
> Any ideas?

Yes. Have you got an installed Windows? Go to C:\WINDOWS\Fonts and copy the .ttf files for the various msttcorefonts. They're listed in those logs you posted. Now go to Ubuntu and make a folder in your home directory called '.fonts' (No quotes). Look carefully - make sure you have a leading stop to the folder name otherwise it won't work. The leading stop makes it a hidden folder, so in a Nautilus (Gnome file browser) window you need to ctrl-H or View > Show Hidden to see it (and all the other hidden files). Simply copy the .ttf files into folder .fonts.

All you have to do now is to restart the Xserver - simplest way is to log in and out. Now you have all the msttcorefonts installed.

I've had problems in the past with msttcorefonts with a very slow server or one that just gives up the ghost altogether. This is why I started using that little trick. I wonder if that was what was happening for you.

A couple of points. You can install any .ttf fonts this way, but they will only be available to you. If you create another user, they won't have access to them. If you need to install fonts system-wide, just post back and I'll tell you how.

---

### Post by Pinkydead on 2008-08-22
Same problem here...

There seems to be couple of solutions that have worked for some people but not me.

The problem for me seems to be a proxy problem.

Anyway I got it working by again editing the post inst file (/var/lib/dpkg/info/msttcorefonts.postinst) and finding the line:
```

if ! wget ...
```

adding --no-proxy after wget, then it worked.  The bug listed for this does say that it's a wget configuration problem and this would confirm that, this is just a hacky way of achieving the same thing.

---

