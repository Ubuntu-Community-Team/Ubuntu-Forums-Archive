---
title: "msttcorefonts"
date: 2008-03-27
forum: Installation &amp; Upgrades
---

### Post by smallmouth sam on 2008-03-27
every time I upgrade or try to add a program i get an error message 

mssttcorefonts exit falure?

gutsy hp amd 64 chip

---

### Post by i-am-me on 2008-03-27
Do you have msttcorefonts installed? If not, the programs just might be crashing because they can't find the fonts they need (I doubt it though, it's highly unlikely). If you do have it installed, I've never heard of that and I'm sorry I can't help you more than I tried.

---

### Post by jpeddicord on 2008-03-27
Could you paste the full error message here?

Also, try the following in a terminal:```
sudo apt-get install msttcorefonts
sudo apt-get install -f
```

---

### Post by smallmouth sam on 2008-03-27
smallmouth@smallmouth-laptop:~$ sudo apt-get install msttcorefonts
Reading package lists... Done
Building dependency tree       
Reading state information... Done
msttcorefonts is already the newest version.
The following packages were automatically installed and are no longer required:
  libswscale1d
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up msttcorefonts (2.2) ...

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
smallmouth@smallmouth-laptop:~$

---

### Post by i-am-me on 2008-03-27
Try a
```
sudo dpkg --configure -a && sudo apt-get autoremove
```
and try installing again.

---

### Post by smallmouth sam on 2008-03-27
smallmouth@smallmouth-laptop:~$ sudo dpkg --configure -a && sudo apt-get autoremove
[sudo] password for smallmouth:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libswscale1d
The following packages will be REMOVED:
  libswscale1d
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 332kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 97010 files and directories currently installed.)
Removing libswscale1d ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Setting up msttcorefonts (2.2) ...

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
smallmouth@smallmouth-laptop:~$ 


You said reinstall. do you mean the whole os?

---

### Post by i-am-me on 2008-03-27
> **smallmouth sam said:**
> dpkg: error processing msttcorefonts (--configure):


You said reinstall. do you mean the whole os?

the first part was what the dpkg --configure -a was for so I don't know what's wrong and by reinstall, I meant the package (msttcorefonts)

---

### Post by i-am-me on 2008-03-27
Instead of installing from the command line using apt-get or aptitude, try installing the actual .deb file using gDebi or dpkg -i 
Link to file download page[:http://packages.debian.org/etch/msttcorefonts]("http://packages.debian.org/etch/msttcorefonts")
Make sure you get the dependencies too (install those by command line unless there are problems)

---

### Post by i-am-me on 2008-03-27
If that doesn't work, go here:[http://packages.ubuntu.com/gutsy/ubuntu-restricted-extras]("http://packages.ubuntu.com/gutsy/ubuntu-restricted-extras")
The restricted extras package includes msttcorefonts as it says on the page, so just install this package (as in the last post, try aptitude first, then manual)

---

### Post by smallmouth sam on 2008-03-30
I am back and still getting error messages on install or removal of programs including msttcorefont anybody got another guess? 

I tried to install older deb packge 1.8 with ubuntu says new er package installed will not let me remove newer  package.

---

### Post by i-am-me on 2008-03-31
> **smallmouth sam said:**
> I am back and still getting error messages on install or removal of programs including msttcorefont anybody got another guess?

I tried to install older deb packge 1.8 with ubuntu says new er package installed will not let me remove newer  package.

Wait... It says it's already installed? Check. Open OpenOffice and look in the fonts to see if Times, Verdana, and whatever other fonts it installs are there. And I just want to clarify: All programs or just all programs with msttcorefonts as a part of them?

---

