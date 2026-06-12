---
title: "Python problems -&gt; upgrade 9.10 to 10.x from command line"
date: 2010-10-07
forum: Installation &amp; Upgrades
---

### Post by tintsu on 2010-10-07
I had problems with python stuff and so update manager did not work. Also many other problems, PiTiVi was installed but did not start eg... After many trials of this and that I removed python-gtk2 and so also ubuntu desktop. But was unable to get it back. Now I cannot even shut down. While it is not possible to install desktop or anything else, would it be possible to fix this by upgrading the whole system to 10.04 (10.10?)? Would it fix python installation. How could I do it. Some info tells to change sources.list and run apt-get upgrade, but some tell not to do so.

t@t:~$ update-manager
Traceback (most recent call last):
  File "/usr/bin/update-manager", line 26, in <module>
    import pygtk
ImportError: No module named pygtk

t@t:~$ sudo apt-get install ubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  ubuntu-desktop: Depends: system-config-printer-gnome but it is not going to be installed
                  Recommends: bluez-cups but it is not going to be installed
                  Recommends: empathy but it is not going to be installed
                  Recommends: gnome-games but it is not going to be installed
                  Recommends: gnome-orca but it is not going to be installed
                  Recommends: ibus but it is not going to be installed
                  Recommends: ibus-m17n but it is not going to be installed
                  Recommends: ibus-table but it is not going to be installed
                  Recommends: jockey-gtk but it is not going to be installed
                  Recommends: libwmf0.2-7-gtk but it is not going to be installed
                  Recommends: speech-dispatcher but it is not going to be installed
                  Recommends: transmission-gtk
                  Recommends: ubuntuone-client-gnome but it is not going to be installed
E: Broken packages

Could you please help asap?
:(

---

### Post by sikander3786 on 2010-10-07
First of all try

```
sudo aptitude install ubuntu-desktop
```

Aptitude has always worked better with dependencies for me.

---

### Post by tintsu on 2010-10-07
Thanks, desktop is back. What a relief. :)

But what to do with Python-pprblems? Here again I tried to follow advice that has been given to fix python issues. Update manager is installed but does not start.  python-gtk2 has been installed.

```
t@t:~$ update-manager
Traceback (most recent call last):
  File "/usr/bin/update-manager", line 26, in <module>
    import pygtk
ImportError: No module named pygtk
t@t:~$ python
Python 2.6.4 (r264:75706, Dec  7 2009, 18:45:15) 
[GCC 4.4.1] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import pygtk
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ImportError: No module named pygtk
>>> 
t@t:~$ sudo aptitude install pygtk
...
Couldn't find package "pygtk".  However, the following
packages contain "pygtk" in their name:
  python2.5-pygtksourceview python-zbarpygtk 
Couldn't find package "pygtk".  However, the following
packages contain "pygtk" in their name:
  python2.5-pygtksourceview python-zbarpygtk 
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 35 not upgraded.
...
t@t:~$ sudo aptitude install python-gtk2
...
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 35 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
...

```

Should I continue trying to resolve python or should I try to get help for upgrading to Lucid Lynx (without update manager) and would I so simultaneously get rid of all python worries? Would they disappear by upgrading? I have had huge problems with them, since I cannot install from source any video editor or audacity ... Everthing meets pyhton and fails. Some binaries can be installed but the program would not start running. Could aptitude be used for upgrading? What to write on command line?

Relieved but very :confused:.

---

### Post by sikander3786 on 2010-10-07
Now try,

```
sudo dpkg --configure -a
```

---

### Post by tintsu on 2010-10-07
Did not help. Update manager, Software sources... still not starting.

```
t@t:~$ sudo dpkg --configure -a
[sudo] password for t
t@t:~$ update-manager
Traceback (most recent call last):
  File "/usr/bin/update-manager", line 26, in <module>
    import pygtk
ImportError: No module named pygtk

```

---

### Post by oldfred on 2010-10-07
Did you reinstall python-gtk2?

---

### Post by sikander3786 on 2010-10-07
Ok.

```
sudo aptitude reinstall pygtk
```

```
sudo aptitude reinstall update-manager
```

Please post the output if unsuccessful.

---

### Post by tintsu on 2010-10-07
```
t@t:~$ sudo aptitude install python-gtk2
[sudo] password for t: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 35 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done

t@t:~$ sudo aptitude reinstall pygtk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Couldn't find package "pygtk".  However, the following
packages contain "pygtk" in their name:
  python2.5-pygtksourceview python-zbarpygtk 
Couldn't find package "pygtk".  However, the following
packages contain "pygtk" in their name:
  python2.5-pygtksourceview python-zbarpygtk 
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 35 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done

t@t:~$ sudo aptitude reinstall update-manager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following packages will be REINSTALLED:
  update-manager 
0 packages upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 35 not upgraded.
Need to get 0B/784kB of archives. After unpacking 0B will be used.
Writing extended state information... Done
(Reading database ... 286233 files and directories currently installed.)
Preparing to replace update-manager 1:0.126.10 (using .../update-manager_1%3a0.126.10_all.deb) ...
Unpacking replacement update-manager ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for desktop-file-utils ...
Processing triggers for man-db ...
Setting up update-manager (1:0.126.10) ...

Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done

t@t:~$ update-manager
Traceback (most recent call last):
  File "/usr/bin/update-manager", line 26, in <module>
    import pygtk
ImportError: No module named pygtk


```

Update manager either stopped working right after upgrading 9.04 -> 9.10 in April or short time afterwards (when there could have been some updating, I don`t remenber exactly). I have used apt-get instead. The problems aroused when I started pc activities, programming etc in the autumn again and faced this python nuisance everywhere. Synaptic Package Manager works.

---

### Post by sikander3786 on 2010-10-07
Did you also install a new version of python for programming?

Rename the stackless python version from /usr/local/bin/python to /usr/local/bin/spython.

It probably will help. Revert the file names back to originals in case it doesn' work.

---

### Post by tintsu on 2010-10-08
At first ls -la /usr/local/bin/* only gave start_xephyr.sh. Found out that I have puthon2.6 which was the newest that sudo apt-get install python offered. [http://www.python.org/download/](http://www.python.org/download/) -> Python-3.1.2.tar.bz2. I downloaded into ~/downloads, did:
./configure
    make
    make test
    sudo make install
README says "This will install Python as python3." Installing went ok.

Update manager still not starting. Synaptic Package Manager does not recognize python3 for being installed, but python 2.6 is still there.

```
t@t:~/downloads/Python-3.1.2$ ls -la /usr/local/bin/*
-rwxr-xr-x 1 root root     111 2010-10-08 12:06 /usr/local/bin/2to3
-rwxr-xr-x 1 root root      99 2010-10-08 12:06 /usr/local/bin/idle3
-rwxr-xr-x 1 root root      84 2010-10-08 12:06 /usr/local/bin/pydoc3
-rwxr-xr-x 2 root root 4241404 2010-10-08 12:17 /usr/local/bin/python3
-rwxr-xr-x 2 root root 4241404 2010-10-08 12:17 /usr/local/bin/python3.1
-rwxr-xr-x 1 root root    1401 2010-10-08 12:17 /usr/local/bin/python3.1-config
lrwxrwxrwx 1 root root      16 2010-10-08 12:17 /usr/local/bin/python3-config -> python3.1-config
-rwxr-xr-x 1 root sbox     305 2010-04-24 18:34 /usr/local/bin/start_xephyr.sh

```

So, should I try instead python2.7? Why is it not offered automatically by package managing programs? How to remove python3?

Is it correct behaviour to download and install them on ~/downloads, and can the folders be removed after the installation is finished without errors.

---

### Post by sikander3786 on 2010-10-08
Did you try renaming python the way I suggested above?

Remove Python3 and reinstall 2.6. You can remove Python3 by navigating to its source directory. Read the Install or Readme file for details.

---

### Post by tintsu on 2010-10-09
Yes, but it is in /usr/bin/

```
t@t:~$ ls -la /usr/local/bin/*
-rwxr-xr-x 1 root root     111 2010-10-08 12:06 /usr/local/bin/2to3
-rwxr-xr-x 1 root root      99 2010-10-08 12:06 /usr/local/bin/idle3
-rwxr-xr-x 1 root root      84 2010-10-08 12:06 /usr/local/bin/pydoc3
-rwxr-xr-x 2 root root 4241404 2010-10-08 12:17 /usr/local/bin/python3
-rwxr-xr-x 2 root root 4241404 2010-10-08 12:17 /usr/local/bin/python3.1
-rwxr-xr-x 1 root root    1401 2010-10-08 12:17 /usr/local/bin/python3.1-config
lrwxrwxrwx 1 root root      16 2010-10-08 12:17 /usr/local/bin/python3-config -> python3.1-config
-rwxr-xr-x 1 root sbox     305 2010-04-24 18:34 /usr/local/bin/start_xephyr.sh
tiina@tiina-laptop:~$ ls -la /usr/bin/python
lrwxrwxrwx 1 root root 9 2010-04-23 23:15 /usr/bin/python -> python2.6
t@t:~$ sudo mv /usr/bin/python /usr/bin/spython
t@t:~$ ls -la /usr/bin/spython
lrwxrwxrwx 1 root root 9 2010-04-23 23:15 /usr/bin/spython -> python2.6
t@t:~$ update-manager
Traceback (most recent call last):
  File "/usr/bin/update-manager", line 26, in <module>
    import pygtk
ImportError: No module named pygtk
t@t:~$ sudo mv /usr/bin/spython /usr/bin/python
```

README does not advice to remove python3. (Earlier I had also tried to install python3 with Synaptic PM, so I removed it there.) Then googled advice toe get rid of the outputs of compilig in ~/downloads

```
t@t:~$ yum remove python3
The program 'yum' is currently not installed.  You can install it by typing:
sudo apt-get install yum
...
t@t:~$ yum remove python3
There was a problem importing one of the Python modules
required to run yum. The error leading to this problem was:

   No module named yum

Please install a package which provides this module, or
verify that the module is installed correctly.

It's possible that the above module doesn't match the
current version of Python, which is:
2.6.4 (r264:75706, Dec  7 2009, 18:45:15) 
[GCC 4.4.1]

If you cannot solve this problem yourself, please go to 
the yum faq at:
  http://wiki.linux.duke.edu/YumFaq
  

t@t:~$ sudo apt-get remove python3
...
rmdir: failed to remove `/usr/local/lib/python3.1': Directory not empty
Processing triggers for man-db ...
Processing triggers for menu ...
Processing triggers for desktop-file-utils ...
t@t:~$ which python3
/usr/local/bin/python3
t@t:~$ sudo apt-get reinstall python2.6
E: Invalid operation reinstall
t@t:~$ sudo apt-get install python2.6
Reading package lists... Done
Building dependency tree       
Reading state information... Done
python2.6 is already the newest version.
python2.6 set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 35 not upgraded.
t@t:~$ sudo dpkg --configure -a

```

python3 is in /usr/local/ bin but is not seen by SPM, so could i remove the folder ~/downloads/Python-3.1.2?

But I found instructions: "If there is not any ubuntu-desktop-packet, so that your machine is a server, or does have some alternative desktop or window management system, you can
sudo aptitude install update-manager-core
sudo do-release-upgrade
follow the instructions that are given

What is your guess, would it work? Should I continue solving python issues or try to upgrade it all, what I mean is does upgrading install pythons again? I`m scared to try, I may end up in situation where this pc in totally messed up and even installing OS from cd will fail.

Thank you so much for trying to help many times, so kind of You! :)

---

### Post by sikander3786 on 2010-10-10
I still doubt if upgrading will solve the python issues. I am afraid, it will get even worse with the upgrade and might break the whole install.

It might also be successful but why not be on the safe side. Can you backup all your important data, start the upgrade process as you mentioned above and hope it is successful. And if it is not, you'll need to reinstall.

> and even installing OS from cd will fail.

Python or upgrade issues will have no impact on that. You can fresh install from the disc anytime you want.

---

### Post by tintsu on 2010-10-10
Yes, it might be best to start from a clean table. Anyway upgrading cumulative propably is not as good as installing from cd/usb. But I did try to learn to fix this. In this case the effort put on learning exceeded reasonable amount of time. And there was lazyness to avoid many installations again. 

It seems that there are two growing groups of Ubuntu users: skillfull experts and those who use windows + virtual maschine + Ubuntu. The first group easily knows what to do and the latter one installs an iso-file every now and then. And a smaller third group is in the middle. Let`s keep on trying! :)

---

