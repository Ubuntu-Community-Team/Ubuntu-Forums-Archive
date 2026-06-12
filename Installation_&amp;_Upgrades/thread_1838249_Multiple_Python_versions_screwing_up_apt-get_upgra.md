---
title: "Multiple Python versions screwing up apt-get upgrade.. I think."
date: 2011-09-03
forum: Installation &amp; Upgrades
---

### Post by richardq on 2011-09-03
I recently re-installed 11.04 on my laptop. One of the first things I did was install python 3.2 because I wanted to build Blender. So I have multiple python versions on my machine (2.7 and 3.2). 

Now I am having a problem installing compiz-config-settings-manager. I don't quite understand the update-alternatives mechanism and while most other upgrades have gone flawlessly, for some reason I think the multiple python setup on my machine is screwing up this one. Any help would be greatly appreciated. 

Here's what I'm getting when it tries to install ccsm and following that is the update alternatives config output which may or may not be useful:

```

richard@midge:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up compizconfig-settings-manager (0.9.4-0ubuntu2) ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 2327, in <module>
    main()
  File "/usr/bin/pycentral", line 2321, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 1493, in run
    runtimes = get_installed_runtimes()
  File "/usr/bin/pycentral", line 278, in get_installed_runtimes
    default_version = pyversions.default_version(version_only=True)
  File "/usr/share/pycentral-data/pyversions.py", line 172, in default_version
    raise ValueError, "/usr/bin/python does not match the python default version. It must be reset to point to %s" % debian_default
ValueError: /usr/bin/python does not match the python default version. It must be reset to point to python2.7
dpkg: error processing compizconfig-settings-manager (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 compizconfig-settings-manager
E: Sub-process /usr/bin/dpkg returned an error code (1)
richard@midge:~$ sudo update-alternatives --config python
There are 2 choices for the alternative python (providing /usr/bin/python).

  Selection    Path                                   Priority   Status
------------------------------------------------------------
  0            /home/richard/src/python32/Python-3.2   3         auto mode
  1            /home/richard/src/python32/Python-3.2   3         manual mode
* 2            /usr/bin/python2.7                      2         manual mode

Press enter to keep the current choice[*], or type selection number: 

```

---

### Post by richardq on 2011-09-03
After doing a little more googling.. I managed to get it to work using: 

sudo rm /usr/bin/python && sudo ln -s python2.7 /usr/bin/python

I'm a bit frustrated because apparently the update-alternatives is supposed to be the "correct" way to do this and many people have warned off doing the recreation of the link. Not sure who is right, and while it's fixed I still haven't really learned a damn thing. ;)

---

### Post by Hakunka-Matata on 2011-09-03
not a solution, but another way to learn more, maybe more quickly, 
dselect is the gui.  You'll have to install it probably but just run in a Terminal the following code:
```
sudo dselect
```

after it's installed, do the same again
```
sudo dselect
```

if you haven't already been using it.

---

### Post by kesten on 2011-12-27
I just got roughly the same error trying to upgrade VirtualBox

  	 	 	 	 	 	   ValueError: /usr/bin/python does not match the python default version. It must be reset to point to python2.7  
  
However,
  	 	 	 	 	 	   /usr/bin$ ls -al | grep python 
  lrwxrwxrwx  1 root   root          24 2011-12-04 16:16 python -> /etc/alternatives/python
 /etc/alternatives$ ls -al | grep python 
 lrwxrwxrwx   1 root   root      18 2011-12-04 16:16 python -> /usr/bin/python2.7 
  
so /usr/bin/python is sym linked to /etc/alternatives/python and this is sym-linked to /usr/bin/python2.7

  	 	 	 	 	 	   $ python 
 Python 2.7.2+ (default, Oct  4 2011, 20:06:09)  
 [GCC 4.6.1] on linux2 
 ...
 >>>
  
That is, /usr/bin/python points to the correct (default debian 2.7) python, but it does so through 2 symlinks.  The extra indirection is messing things up.  The bug lies either with the post-installation script (owned by VirtualBox) requesting the version in a way that doesn't support update-alternatives, or with update-alternatives for not conforming to some expected interface requirements.  Submitting a bug report to both.

kesten

---

