---
title: "Python-Minimal error in 16.04 LTS"
date: 2016-04-24
forum: Installation &amp; Upgrades
---

### Post by BJones007 on 2016-04-24
Tried doing ```
sudo apt-get upgrade
``` after I updated to Xenial from Wily and I keep getting this error 

> Setting up python-minimal (2.7.11-1) ...dpkg: error processing package python-minimal (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 python-minimal
E: Sub-process /usr/bin/dpkg returned an error code (1)

I tried several different commands 
```
sudo apt-get install -f
``` 
```
sudo apt-get autoremove
```
```
sudo dpkg --configure -a
``` 
```
sudo apt-get clean
```

but none of these commands seem to have fixed the issue. Is this an issue with 16.04 or did I do something during the upgrade process that could have caused this? If I did, is there a way I can fix it without doing a fresh install? Thanks in advance. Cheers!


Footnote: I had VirtualBox and GNS3 installed, but after the upgrade they quit working. Could the above issue be the cause of this?

---

### Post by ian-weisser on 2016-04-25
Please show us the entire ouput of the 'sudo apt-get upgrade' command.
dpkg usually provides more information about most errors.

---

### Post by BJones007 on 2016-04-25
This is for ```
sudo apt-get upgrade
```


> root@brian-Inspiron-3520:/home/brianjones# apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up python-minimal (2.7.11-1) ...
dpkg: error processing package python-minimal (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 python-minimal
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by BJones007 on 2016-04-26
Bump

---

### Post by ian-weisser on 2016-04-26
Delete the package from your cache and try downloading a fresh copy.
```
sudo apt-get clean python-minimal
sudo apt-get upgrade
```

---

### Post by BJones007 on 2016-04-26
Tried this before it, but it didn't work. Still getting the same error

---

### Post by ian-weisser on 2016-04-26
Please show us the entire contents of the file: /var/lib/dpkg/info/python-minimal.postinst

---

### Post by BJones007 on 2016-04-26
That file is now either blank or non-existent. After doing some reading I saw where python-minimal is a dependency of python 2.7 which was already installed, but an older version (I'm assuming python-minimal2.6) was conflicting. So I just ran ```
sudo apt-get remove python-minimal
``` and got this output


> 
root@brian-Inspiron-3520:/home/brianjones# apt-get remove python-minimal
Reading package lists... Done
Building dependency tree 
Reading state information... Done
The following packages were automatically installed and are no longer required:
libasound2:i386 libasound2-plugins:i386 libasyncns0:i386 libdbus-1-3:i386
libflac8:i386 libfreetype6:i386 libgcrypt20:i386 libgpg-error0:i386
libice6:i386 libjack-jackd2-0:i386 libjson-c2:i386 libogg0:i386
libpng12-0:i386 libpulse0:i386 libsamplerate0:i386 libsm6:i386
libsndfile1:i386 libspeexdsp1:i386 libsystemd0:i386 libvorbis0a:i386
libvorbisenc2:i386 libwrap0:i386 libx11-6:i386 libxdamage1:i386
libxext6:i386 libxfixes3:i386 libxrandr2:i386 libxrender1:i386 libxtst6:i386
Use 'sudo apt autoremove' to remove them.
The following packages will be REMOVED
python-minimal
0 to upgrade, 0 to newly install, 1 to remove and 0 not to upgrade.
1 not fully installed or removed.
After this operation, 148 kB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 1315223 files and directories currently installed.)
Removing python-minimal (2.7.11-1) ...
Processing triggers for man-db (2.7.5-1) ...
 

then I did

 ```
sudo apt-get upgrade
``` 

got this output 


> 
root@brian-Inspiron-3520:/home/brianjones# apt-get upgrade
Reading package lists... Done
Building dependency tree 
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
libasound2:i386 libasound2-plugins:i386 libasyncns0:i386 libdbus-1-3:i386
libflac8:i386 libfreetype6:i386 libgcrypt20:i386 libgpg-error0:i386
libice6:i386 libjack-jackd2-0:i386 libjson-c2:i386 libogg0:i386
libpng12-0:i386 libpulse0:i386 libsamplerate0:i386 libsm6:i386
libsndfile1:i386 libspeexdsp1:i386 libsystemd0:i386 libvorbis0a:i386
libvorbisenc2:i386 libwrap0:i386 libx11-6:i386 libxdamage1:i386
libxext6:i386 libxfixes3:i386 libxrandr2:i386 libxrender1:i386 libxtst6:i386
Use 'sudo apt autoremove' to remove them.
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.


So I ran ```
sudo apt-get autoremove
``` and ended up with this

> 

root@brian-Inspiron-3520:/home/brianjones# apt-get autoremove
Reading package lists... Done
Building dependency tree 
Reading state information... Done
The following packages will be REMOVED
libasound2:i386 libasound2-plugins:i386 libasyncns0:i386 libdbus-1-3:i386
libflac8:i386 libfreetype6:i386 libgcrypt20:i386 libgpg-error0:i386
libice6:i386 libjack-jackd2-0:i386 libjson-c2:i386 libogg0:i386
libpng12-0:i386 libpulse0:i386 libsamplerate0:i386 libsm6:i386
libsndfile1:i386 libspeexdsp1:i386 libsystemd0:i386 libvorbis0a:i386
libvorbisenc2:i386 libwrap0:i386 libx11-6:i386 libxdamage1:i386
libxext6:i386 libxfixes3:i386 libxrandr2:i386 libxrender1:i386 libxtst6:i386
0 to upgrade, 0 to newly install, 29 to remove and 0 not to upgrade.
After this operation, 12.5 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 1315197 files and directories currently installed.)
Removing libasound2-plugins:i386 (1.1.0-0ubuntu1) ...
Removing libasound2:i386 (1.1.0-0ubuntu1) ...
Removing libpulse0:i386 (1:8.0-0ubuntu3) ...
Removing libasyncns0:i386 (0.8-5build1) ...
Removing libdbus-1-3:i386 (1.10.6-1ubuntu3) ...
Removing libsndfile1:i386 (1.0.25-10) ...
Removing libflac8:i386 (1.3.1-4) ...
Removing libfreetype6:i386 (2.6.1-0.1ubuntu2) ...
Removing libsystemd0:i386 (229-4ubuntu4) ...
Removing libgcrypt20:i386 (1.6.5-2) ...
Removing libgpg-error0:i386 (1.21-2ubuntu1) ...
Removing libsm6:i386 (2:1.2.2-1) ...
Removing libice6:i386 (2:1.0.9-1) ...
Removing libjack-jackd2-0:i386 (1.9.10+20150825git1ed50c92~dfsg-1ubuntu1) ...
Removing libjson-c2:i386 (0.11-4ubuntu2) ...
Removing libvorbisenc2:i386 (1.3.5-3) ...
Removing libvorbis0a:i386 (1.3.5-3) ...
Removing libogg0:i386 (1.3.2-1) ...
Removing libpng12-0:i386 (1.2.54-1ubuntu1) ...
Removing libsamplerate0:i386 (0.1.8-8) ...
Removing libspeexdsp1:i386 (1.2~rc1.2-1ubuntu1) ...
Removing libwrap0:i386 (7.6.q-25) ...
Removing libxrandr2:i386 (2:1.5.0-1) ...
Removing libxrender1:i386 (1:0.9.9-0ubuntu1) ...
Removing libxdamage1:i386 (1:1.1.4-2) ...
Removing libxtst6:i386 (2:1.2.2-1) ...
Removing libxext6:i386 (2:1.3.3-1) ...
Removing libxfixes3:i386 (1:5.0.1-2) ...
Removing libx11-6:i386 (2:1.6.3-1ubuntu2) ...
Processing triggers for libc-bin (2.23-0ubuntu3) ...

but now when I try to re-install python-minimal I get this message.

> root@brian-Inspiron-3520:/home/brianjones# apt-get install python-minimalReading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package python-minimal


Apologies for the long post, wasn't sure how else to put it

---

### Post by BJones007 on 2016-04-26
Here are the contents of [COLOR=#000000]/var/lib/dpkg/info/python-minimal.postinst[/COLOR]

```

#! /bin/shset -e


python2.7 -m compileall /usr/share/python/ >/dev/null

```

---

### Post by BJones007 on 2016-04-26
Here are the contents of [COLOR=#000000]/var/lib/dpkg/info/python-minimal.postinst[/COLOR]

```

#! /bin/shset -e


python2.7 -m compileall /usr/share/python/ >/dev/null

```

---

### Post by ian-weisser on 2016-04-27
Missing CR. It should look like:
```
#! /bin/sh
set -e

python2.7 -m compileall /usr/share/python/ >/dev/null
```

Use a text editor (as sudo) to fix the file.

---

### Post by BJones007 on 2016-04-27
That's exactly how it looks, seems like when I pasted it it looked like what I had before

---

### Post by squegie on 2016-06-16
I know it's over a month later, but I encountered this same issue and this one is the most relevant thread.

Run the post install  command without redirect to >/dev/null (edit the file, or: `sudo python2.7 -m compileall /usr/share/python/`). This will show you where post installation configuration is failing.
 
Ex:

```
    
Listing /usr/share/python/penemue/lib/python2.7/site-packages/gevent 
Compiling /usr/share/python/penemue/lib/python2.7/site-packages/gevent/_socket3.py ...
   File "/usr/share/python/penemue/lib/python2.7/site-packages/gevent/_socket3.py", line 183
      def makefile(self, mode="r", buffering=None, *,
                                                      ^
    SyntaxError: invalid syntax

```
In my case, it was a custom python package (built using dh-virtualenv) that lived under /usr/share/python. I had to run `dpkg -P penemue` and ultimately remove the `/usr/share/python/penemue` directory. I might have been able to just move the `/usr/share/python/penemue` directory out of the way.

Once I got rid of the bad code, running `sudo apt-get install -f` resolved the issues.

---

### Post by JLH02 on 2016-08-09
> **squegie said:**
> I know it's over a month later, but I encountered this same issue and this one is the most relevant thread.

Run the post install  command without redirect to >/dev/null (edit the file, or: `sudo python2.7 -m compileall /usr/share/python/`). This will show you where post installation configuration is failing.
 
Ex:

```
    
Listing /usr/share/python/penemue/lib/python2.7/site-packages/gevent 
Compiling /usr/share/python/penemue/lib/python2.7/site-packages/gevent/_socket3.py ...
   File "/usr/share/python/penemue/lib/python2.7/site-packages/gevent/_socket3.py", line 183
      def makefile(self, mode="r", buffering=None, *,
                                                      ^
    SyntaxError: invalid syntax

```
In my case, it was a custom python package (built using dh-virtualenv) that lived under /usr/share/python. I had to run `dpkg -P penemue` and ultimately remove the `/usr/share/python/penemue` directory. I might have been able to just move the `/usr/share/python/penemue` directory out of the way.

Once I got rid of the bad code, running `sudo apt-get install -f` resolved the issues.

Thanks for the help.  In my case, it was a version of GNS3 installed from source. Numerous errors, here are just a couple examples.
```
Compiling /usr/share/python/gns3-gui/lib/python3.4/site-packages/gns3/main.py ...
  File "/usr/share/python/gns3-gui/lib/python3.4/site-packages/gns3/main.py", line 130
    print("".join(lines), file=sys.stderr)
                              ^
SyntaxError: invalid syntax

```
and

```
Compiling /usr/share/python/gns3-server/lib/python3.4/site-packages/aiohttp/abc.py ...
  File "/usr/share/python/gns3-server/lib/python3.4/site-packages/aiohttp/abc.py", line 5
    class AbstractRouter(metaclass=ABCMeta):
                                  ^
SyntaxError: invalid syntax

```
I removed /usr/share/python/gns3-server and gns3-gui.  Then `sudo apt-get install -f` worked.

---

### Post by bias2 on 2017-08-02
Wow, thanks a lot for that post, I learned a nice one there.

I upgraded ubuntu and had an issue with python-minimal constantly failing with:

[COLOR=#000000]*Setting up python-minimal (2.7.xx-x) ...dpkg: error processing package python-minimal (--configure):*[/COLOR]
[COLOR=#000000]*subprocess installed post-installation script returned error exit status 1*[/COLOR]
[COLOR=#000000]*Errors were encountered while processing:*[/COLOR]
[COLOR=#000000]*python-minimal*[/COLOR]
[COLOR=#000000]*E: Sub-process /usr/bin/dpkg returned an error code (1)*[/COLOR]. 

Couldn't install any additional package and remove (cleanly) python-minimal didn't work as it kept trying to reinstall with the same error.

This post (removing the/dev/null redirection) allowed me to see that a custom install of rekall-forensic was the root cause.

Once I removed that directory, python-minimal installed successfully.

Great work, thank you very much!!

---

### Post by nknganda on 2018-02-22
Hi guys, getting the same error but running the post install script without the dev/null redirection. It just shows the _struct import error.

Please assist. Thanks.

---

### Post by mathieu-tarral on 2018-03-09
Hey guys !

I just had the same issue, removed the null redirection and discover that rekall-forensic was also breaking the package.

Thanks for helping me fixing my APT !

---

### Post by umair007 on 2018-12-10
I faced same sort of issue while installing, the solution i found out was no file... [COLOR=#000000]/var/lib/dpkg/info/python-minimal.postinst but rather there was python3-minimal file exisit so i just run the same command again adding 3 with phyton and it worked.[/COLOR]

---

