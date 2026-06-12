---
title: "Can't do anything because of broken python"
date: 2012-07-31
forum: Installation &amp; Upgrades
---

### Post by Raccoon&#9789; on 2012-07-31
When I tried to install python3 using the Ubuntu Software Centre it said there was an error and gave me a box to submit a bug report which I did: [https://bugs.launchpad.net/ubuntu/+source/python3-defaults/+bug/1031232](https://bugs.launchpad.net/ubuntu/+source/python3-defaults/+bug/1031232)

But now I have a broken python and I can't do anything.  I can't remove package python3 using aptitude:

```
(Reading database ... 201088 files and directories currently installed.)
Removing python3 ...
/var/lib/dpkg/info/python3.prerm: 4: /var/lib/dpkg/info/python3.prerm: py3clean: not found
dpkg: error processing python3 (--purge):
 subprocess installed pre-removal script returned error exit status 127
No apport report written because MaxReports is reached already
                                                              /var/lib/dpkg/info/python3.postinst: 47: /var/lib/dpkg/info/python3.postinst: py3compile: not found
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 127
Errors were encountered while processing:
 python3
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Press return to continue.
```I can't remove it with the software centre:

```
installArchives() failed: (Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 201088 files and directories currently installed.) 
Removing python3 ... 
Traceback (most recent call last): 
  File "/usr/bin/py3clean", line 24, in <module> 
    import logging 
EOFError: EOF read where not expected 
dpkg: error processing python3 (--remove): 
 subprocess installed pre-removal script returned error exit status 1 
Traceback (most recent call last): 
  File "/usr/bin/py3compile", line 25, in <module> 
    import logging 
EOFError: EOF read where not expected 
dpkg: error while cleaning up: 
 subprocess installed post-installation script returned error exit status 1 
Errors were encountered while processing: 
 python3 

```I can't do normal things when running python3:

```
>>> import hashlib
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
EOFError: EOF read where not expected

```And this is a fresh install of 12.04; I am just getting it set up for working with.

I will continue trying things, but any help or pointers would be helpful.

---

### Post by dino99 on 2012-07-31
[https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)
[http://askubuntu.com/questions/146150/unable-to-fix-broken-packages-with-sudo-apt-get-install-f](http://askubuntu.com/questions/146150/unable-to-fix-broken-packages-with-sudo-apt-get-install-f)

---

### Post by Raccoon&#9789; on 2012-07-31
Thanks for those.  I am familiar with Synaptic, I'm trying Ubuntu again after a while with Debian.  However, the problem is everything needs a working Python (I also) which I don't seem to have, so it can't fix the broken packages and Reinstalling Python or anything from within Synaptic produces the same EOFError.  See below:

```
jacob@skunk:~$ [COLOR=Blue]**sudo apt-get install -f**[/COLOR]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up python3 (3.2.3-0ubuntu1) ...
running python rtupdate hooks for python3.2...
running python post-rtupdate hooks for python3.2...
[B][COLOR=Red]Traceback (most recent call last):
  File "/usr/bin/py3compile", line 25, in <module>
    import logging
EOFError: EOF read where not expected[/COLOR][/B]
dpkg: error processing python3 (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 python3
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

And note it's not just the logging module that causes this error.

---

### Post by drmrgd on 2012-07-31
Do you still have the original Python version on your system (I believe it's 2.6.5 - or at least that's what my system is showing)?  And if so, what happens if you create an alteratives list for Python and select that version as the default instead of v3.2?  

If you don't have the original version on the system anymore (i.e. you replaced it with a newer version), you might be hosed.  I suppose you could try to install 2.6.5 from source and then with some creative symbolic links and / or setting up an alternatives list trick the system into using 2.6.5 as the default.  It might be better to re-install, though, just to make sure nothing else is broken.

---

### Post by Raccoon&#9789; on 2012-07-31
I do still have 'python' which is 2.7 on this system.

If I do re-install Ubuntu, I don't know how I would avoid running into the same problem, as all I did was install python3, which I need, through the Software Centre.

---

### Post by drmrgd on 2012-08-01
So, if you run:

```
python --version
```

What is the output?  If the default you're seeing is 3.x then I think you need to force the system to use 2.7 as the default, which I've done before by setting up an alteratives entry.  There probably is none setup by default, so you'll need to make one by doing something like this:

```
sudo update-alternatives --install /usr/bin/python python /usr/bin/python3.2 10 #Change '3.2' to the correct version you see
sudo update-alternatives --install /usr/bin/python python /usr/bin/python2.7 20 #Again, change '2.7' to the correct version
```

Then once you've set up the list, you can select the default by running:

```
sudo update-alternatives --config
```

Which should spit out the list and allow you to select which version you want as the default (i.e. Python2.7).  Then when you simply type 'python' you'll load 2.7 by default (also if you run 'python --version' you should see 2.7).  But, when you need to run 3.2, you can simply run 'python3.2' and that should load Python3.2 for you.  

Hope that helps!

---

