---
title: "firefox 29 installation issues"
date: 2014-05-28
forum: Installation &amp; Upgrades
---

### Post by prat22 on 2014-05-28
Dear All,

I have downloaded the firefox 29 tarball from mozilla site, but I am unable to install firefox. The following are the details:

My system: Lubuntu 13.04
RAM: ~1GB
Processor: Intel Pentium M, 2.13GHz

I have extracted the contents of the tarball, and copied the same to /opt/firefox


```

pratik@pratik-laptop:/opt$ ls
firefox  libreoffice4.2



```


Further, when I ls-l my firefox folder,

```

pratik@pratik-laptop:/opt/firefox$ ls -l
total 70184
-rw------- 1 pratik pratik      671 May  7 05:34 application.ini
drwxr-xr-x 7 root   root       4096 May 28 13:29 browser
-rw------- 1 pratik pratik       40 May  7 06:33 chrome.manifest
drwxr-xr-x 2 root   root       4096 May 28 13:29 components
-rw------- 1 pratik pratik   123476 May  7 06:33 crashreporter
-rw------- 1 pratik pratik     4003 May  7 04:18 crashreporter.ini
drwxr-xr-x 3 root   root       4096 May 28 13:29 defaults
-rw------- 1 pratik pratik      127 May  7 06:20 dependentlibs.list
drwxr-xr-x 2 root   root       4096 May 28 13:29 dictionaries
-rw------- 1 pratik pratik   138520 May  7 06:33 firefox
-rw------- 1 pratik pratik   138524 May  7 06:33 firefox-bin
drwxr-xr-x 2 root   root       4096 May 28 13:29 icons
-rw------- 1 pratik pratik      899 May  7 06:33 libfreebl3.chk
-rw------- 1 pratik pratik   434200 May  7 06:33 libfreebl3.so
-rw------- 1 pratik pratik     7504 May  7 06:33 libmozalloc.so
-rw------- 1 pratik pratik   756852 May  7 06:33 libmozsqlite3.so
-rw------- 1 pratik pratik   230852 May  7 06:33 libnspr4.so
-rw------- 1 pratik pratik  1013448 May  7 06:33 libnss3.so
-rw------- 1 pratik pratik   453672 May  7 06:33 libnssckbi.so
-rw------- 1 pratik pratik      899 May  7 06:33 libnssdbm3.chk
-rw------- 1 pratik pratik   146264 May  7 06:33 libnssdbm3.so
-rw------- 1 pratik pratik   128208 May  7 06:33 libnssutil3.so
-rw------- 1 pratik pratik    15748 May  7 06:33 libplc4.so
-rw------- 1 pratik pratik    14116 May  7 06:33 libplds4.so
-rw------- 1 pratik pratik   144244 May  7 06:33 libsmime3.so
-rw------- 1 pratik pratik      899 May  7 06:33 libsoftokn3.chk
-rw------- 1 pratik pratik   225748 May  7 06:33 libsoftokn3.so
-rw------- 1 pratik pratik   207004 May  7 06:33 libssl3.so
-rw------- 1 pratik pratik 58403596 May  7 06:33 libxul.so
-rw------- 1 pratik pratik   129564 May  7 06:33 mozilla-xremote-client
-rw------- 1 pratik pratik  8560957 May  7 06:33 omni.ja
-rw------- 1 pratik pratik      138 May  7 06:19 platform.ini
-rw------- 1 pratik pratik   120076 May  7 06:33 plugin-container
-rw------- 1 pratik pratik     2321 May  7 06:33 precomplete
-rw------- 1 pratik pratik      682 May  7 06:33 removed-files
-rw------- 1 pratik pratik     8915 May  7 04:17 run-mozilla.sh
-rw------- 1 pratik pratik      825 May  7 04:18 Throbber-small.gif
-rw------- 1 pratik pratik   169752 May  7 06:33 updater
-rw------- 1 pratik pratik      681 May  7 06:21 updater.ini
-rw------- 1 pratik pratik      132 May  7 05:35 update-settings.ini
drwxr-xr-x 2 root   root       4096 May 28 13:29 webapprt
-rw------- 1 pratik pratik   171876 May  7 06:33 webapprt-stub
pratik@pratik-laptop:/opt/firefox$ 



``` 


The firefox file in the firefox folder is executable. Therefore, if I run it in terminal,

```

pratik@pratik-laptop:/opt/firefox$ firefox
The program 'firefox' is currently not installed. You can install it by typing:
sudo apt-get install firefox
pratik@pratik-laptop:/opt/firefox$ 



``` 

Further, if I try to compile firefox,

```

pratik@pratik-laptop:/opt/firefox$ ./firefoxbash: ./firefox: Permission denied
pratik@pratik-laptop:/opt/firefox$ sudo ./firefox
[sudo] password for pratik: 
sudo: ./firefox: command not found
pratik@pratik-laptop:/opt/firefox$ 



```

Please can you point out the underlying problem? 

PS: The downloaded folder doesnot contain a readme, or configure, or install file or howto s.

---

### Post by m_duck on 2014-05-28
Is there a reason you don't want to use the repo version? I guess on 13.04 it isn't up to date. That said, it looks as though 13.04 reached end of life on 27th January this year. You should probably upgrade to make sure you stay up to date with security fixes and whatnot.

That said, info for running tarball'd Firefox is [here]("https://support.mozilla.org/en-US/kb/install-firefox-linux").

The reason the first attempt didn't work ("...'firefox' is currently not installed...") is because running a command like that will check for binaries called **firefox** in your $PATH variable. Presumably **/opt/firefox** is not in your $PATH.

The second attempt is not compiling. Most Linux OSs don't let you run an executable from the current directory (otherwise known as ".") unless it is in your $PATH. Using **./** gives a path to the executable in the current directory so the executable can be found - much like running **/usr/bin/xterm** would allow you to run **xterm** if **/usr/bin** wasn't in your $PATH (it is though, this is just an example). The reason you get the **permission denied** error is because the firefox binary is not executable and **./firefox** tries to execute the firefox binary.```
-rw------- 1 pratik pratik   138520 May  7 06:33 firefox
-rw------- 1 pratik pratik   138524 May  7 06:33 firefox-bin
```
To make it executable and try to run it again, make sure you are in **/opt/firefox** and run the following:```
$ chmod u+x firefox
$ ./firefox
```
The first command makes the binary executable for the owner of the file (you) and the second attempts to run it again. If you run **ls -l** on the directory again, you will see something like the following, noting that the binary now has executable permissions:```
-rwx------ 1 pratik pratik   138520 May  7 06:33 firefox
-rw------- 1 pratik pratik   138524 May  7 06:33 firefox-bin
```

If you get errors, a couple are mentioned in the link I gave above, if not, post it here and I'll try to help.

---

### Post by monkeybrain20122 on 2014-05-28
> **m_duck said:**
> Is there a reason you don't want to use the repo version? I guess on 13.04 it isn't up to date. 

It is fully up to date on 13.10. FF gets update through the normal software channel. I see no point in OP's question whatsoever.

BTW, the tar ball doesn't need compiling or intsalling, nor do you need to move it to /opt. just extract it, open the folder and click firefox, that's it.

---

### Post by m_duck on 2014-05-28
> **monkeybrain20122 said:**
> It is fully up to date on 13.10. FF gets update through the normal software channel. I see no point in OP's question whatsoever.
prat22 is using 13.04 as it says in the OP which has [Firefox 26.0 in the repos](http://packages.ubuntu.com/raring/web/firefox). My recommendation is to update from 13.04 to a newer release, but the rest of my post answers their question.

> **monkeybrain20122 said:**
> BTW, the tar ball doesn't need compiling or intsalling, nor do you need  to move it to /opt. just extract it, open the folder and click firefox,  that's it.
You are correct, the tarball contains pre-compiled binaries. It depends on how you wish to organise your binaries or if other users need access to the binary - if that is the case, it is not best of in the users home, but better in e.g. /usr/local or /opt.

---

### Post by prat22 on 2014-05-28
Thanks m_duck for your extensive support and help. And thanks for your elaborate explanation too! Thank you again, it solved the issues.
Special thanks to monkeybrain20122 too for your constructive support.

However, I thought that superuser privileges may give necessary permissions.

And I am going for an upgrade this weekend. :)

---

