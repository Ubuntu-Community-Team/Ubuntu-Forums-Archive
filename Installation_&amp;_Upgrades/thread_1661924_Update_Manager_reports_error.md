---
title: "Update Manager reports error"
date: 2011-01-07
forum: Installation &amp; Upgrades
---

### Post by Rocket J Squirrel on 2011-01-07
What does one do when Update Manager squawks then reports this:
[INDENT]installArchives() failed: 
Extracting templates from packages: 71%
Extracting templates from packages: 100% 
Preconfiguring packages ...
[/INDENT]That is exactly all it says. Could be more helpful, I bet.

Update: Update Manager ended with one package downloaded but not installed. I told it to install it. It reports:

Preparing to replace libobasis3.3-en-us-help 3.3.0-17 (using .../libobasis3.3-en-us-help_3.3.0-18_i386.deb) ... 
Unpacking replacement libobasis3.3-en-us-help ... 
dpkg: error processing /var/cache/apt/archives/libobasis3.3-en-us-help_3.3.0-18_i386.deb (--unpack): 
 trying to overwrite '/opt/libreoffice/basis3.3/help/en/sdraw.cfg', which is also in package libobasis3.3-en-us-draw 3.3.0-17 
dpkg-deb: subprocess paste killed by signal (Broken pipe) 
Errors were encountered while processing: 
 /var/cache/apt/archives/libobasis3.3-en-us-help_3.3.0-18_i386.deb

---

### Post by sikander3786 on 2011-01-07
From Applications > Accessories > Terminal, try these commands and post _complete_ outputs.

```
sudo apt-get clean
```

```
sudo apt-get install -f
```

```
sudo dpkg --configure -a
```

While posting, click the # icon in post menu and paste your text in between the generated [code] tags.

---

### Post by Rocket J Squirrel on 2011-01-07
Thank you. Second command failed:

```
jackelliott@TheJackUbuntuNetbook:~$ sudo apt-get clean
[sudo] password for jackelliott: 
jackelliott@TheJackUbuntuNetbook:~$ sudo dpkg install -f
dpkg: need an action option

```

---

### Post by sikander3786 on 2011-01-07
In fact, the second one was not dpkg install -f but it was apt-get install -f. Please copy/paste the commands from post # 2 to your Terminal instead of re-typing them.

---

### Post by Rocket J Squirrel on 2011-01-07
Ah, totally my bad and very embarrassing. I have been unable to paste anything into Terminal after upgrading to 10.10 netbook (Unity) -- can't even cut and paste within Terminal -- and I fumbled the typing of the suggested commands. 

```
jackelliott@TheJackUbuntuNetbook:~$ sudo apt-get install -f
[sudo] password for jackelliott: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  lobasis3.3-images
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
jackelliott@TheJackUbuntuNetbook:~$ sudo dpkg --configure -a
warning, in file '/var/lib/dpkg/status' near line 18670 package 'sitquietly':
 'Depends' field, reference to 'python': error in version: invalid character in version number
warning, in file '/var/lib/dpkg/available' near line 19821 package 'sitquietly':
 'Depends' field, reference to 'python': error in version: invalid character in version number
jackelliott@TheJackUbuntuNetbook:~$ 

```

The errors noted in package 'sitquietly' is one I see all the time. 

It's not clear to me whether these two errors might have caused this morning's error from Update Manager. 

In case there is something worth looking at:

Line 18670 of '/var/lib/dpkg/status' is the "Depends:" line:

```
Package: sitquietly
Status: install ok installed
Priority: extra
Section: Utilities (universe)
Installed-Size: 292
Maintainer: Richard Barker <richard.barker@quietwatercourse.co.uk>
Architecture: i386
Version: 1.0.1-1
Depends: python (>= 2.4.3*11)
Description: A meditation timer application.
 Sitquietly allows you to time your meditation session by setting an introduction time and a sitting time.  At the end of both the introduction and sitting periods, a bell will chime.
```

Likewise, Line 19821 in '/var/lib/dpkg/available' is also the "Depends:" statement:

```
Package: sitquietly
Priority: extra
Section: Utilities (universe)
Installed-Size: 292
Maintainer: Richard Barker <richard.barker@quietwatercourse.co.uk>
Architecture: i386
Version: 1.0.1-1
Depends: python (>= 2.4.3*11)
Size: 186718
Description: A meditation timer application.
 Sitquietly allows you to time your meditation session by setting an introduction time and a sitting time.  At the end of both the introduction and sitting periods, a bell will chime.
```

---

### Post by Rocket J Squirrel on 2011-01-07
Wait - that asterisk in the Depends line (2.4.3*11) is totally not visible when viewing the file in gedit. I'll hand-edit that thing out.

Okay, good, now 'dpkg --configure -a' returns no errors.

---

### Post by Rocket J Squirrel on 2011-01-07
But how can I tell if fixing the odd error in the two files also takes care of the error from Update Manager?

---

### Post by sikander3786 on 2011-01-08
You can try using an older /dpkg/status file.

```
sudo mv /var/lib/dpkg/status /var/lib/dpkg/status.bad
```

```
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
```

```
sudo apt-get install -f
```

```
sudo dpkg --configure -a
```

---

### Post by Rocket J Squirrel on 2011-01-08
Thank you . . . but why? I edited out the errors in each file, and now get this:
```
jackelliott@TheJackUbuntuNetbook:~$ sudo apt-get install -f
[sudo] password for jackelliott: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  lobasis3.3-images
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

jackelliott@TheJackUbuntuNetbook:~$ sudo dpkg --configure -a
jackelliott@TheJackUbuntuNetbook:~$ 
```

Which seems pretty clean to me. So what I'm curious to know is if there is a way to ask Update Manager to check to see if it''s happy now -- my original issue was an error from Update Manager, as noted in my original post, and the error was
```

installArchives() failed: 
Extracting templates from packages: 71%
Extracting templates from packages: 100% 
Preconfiguring packages ...
```

---

### Post by sikander3786 on 2011-01-08
No need to revert to an older status file as you are not getting any errors anymore. Fire up Update Manager and check for Updates. Install any available Updates.

If there are no errors on the command line, I am more than sure Update Manger won't return any errors.

---

### Post by Rocket J Squirrel on 2011-01-08
Thank you. 

Update Manager just now offered a new update so I accepted it. It reports

```
installArchives() failed: (Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 257064 files and directories currently installed.) 
Preparing to replace libobasis3.3-en-us-help 3.3.0-17 (using .../libobasis3.3-en-us-help_3.3.0-18_i386.deb) ... 
Unpacking replacement libobasis3.3-en-us-help ... 
dpkg: error processing /var/cache/apt/archives/libobasis3.3-en-us-help_3.3.0-18_i386.deb (--unpack): 
 trying to overwrite '/opt/libreoffice/basis3.3/help/en/sdraw.cfg', which is also in package libobasis3.3-en-us-draw 3.3.0-17 
No apport report written because MaxReports is reached already
dpkg-deb: subprocess paste killed by signal (Broken pipe) 
Errors were encountered while processing: 
 /var/cache/apt/archives/libobasis3.3-en-us-help_3.3.0-18_i386.deb 

```

So I will now re-run those commands in Terminal:
```
jackelliott@TheJackUbuntuNetbook:~$ sudo apt-get clean
[sudo] password for jackelliott: 
jackelliott@TheJackUbuntuNetbook:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  lobasis3.3-images
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
jackelliott@TheJackUbuntuNetbook:~$ sudo dpkg --configure -a
jackelliott@TheJackUbuntuNetbook:~$ 
```

So that's clean. 

Running Update Manager gives the same error as above. 

So, run 'apt-get autoremove' as 'apt-get install -f' suggested:
```
jackelliott@TheJackUbuntuNetbook:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  lobasis3.3-images
0 upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
After this operation, 26.4MB disk space will be freed.
Do you want to continue [Y/n]? 
(Reading database ... 257063 files and directories currently installed.)
Removing lobasis3.3-images ...
jackelliott@TheJackUbuntuNetbook:~$ 

```

Try Update Manager one more time -- nope, same error:
```
installArchives() failed: (Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 257058 files and directories currently installed.) 
Preparing to replace libobasis3.3-en-us-help 3.3.0-17 (using .../libobasis3.3-en-us-help_3.3.0-18_i386.deb) ... 
Unpacking replacement libobasis3.3-en-us-help ... 
dpkg: error processing /var/cache/apt/archives/libobasis3.3-en-us-help_3.3.0-18_i386.deb (--unpack): 
 trying to overwrite '/opt/libreoffice/basis3.3/help/en/sdraw.cfg', which is also in package libobasis3.3-en-us-draw 3.3.0-17 
No apport report written because MaxReports is reached already
dpkg-deb: subprocess paste killed by signal (Broken pipe) 
Errors were encountered while processing: 
 /var/cache/apt/archives/libobasis3.3-en-us-help_3.3.0-18_i386.deb 

```

Any idea what the problem might be? Thank you for your help.

---

