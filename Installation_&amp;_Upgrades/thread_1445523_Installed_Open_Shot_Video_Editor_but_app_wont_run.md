---
title: "Installed Open Shot Video Editor but app wont run"
date: 2010-04-02
forum: Installation &amp; Upgrades
---

### Post by shipp on 2010-04-02
The title on this pretty much explains my problem.  I installed it using the ppa instructions here [http://www.openshotvideo.com/2008/04/ppa-instructions.html](http://www.openshotvideo.com/2008/04/ppa-instructions.html).

The terminal says this when I try to run the program:

 tshipp@Harold:~$ openshot
--------------------------------
   OpenShot (version 1.1.2)
--------------------------------
*** ERROR: MLT Python bindings failed to import ***
*** ERROR: MLT Python bindings failed to import ***
Exception in thread Thread-1:
Traceback (most recent call last):
  File "/usr/lib/python2.6/threading.py", line 525, in __bootstrap_inner
    self.run()
  File "/usr/lib/pymodules/python2.6/openshot/classes/thumbnail.py", line 170, in run
    mlt.Factory().init()
NameError: global name 'mlt' is not defined

-------------------------------------------------------
Error:  OpenShot has not been installed in the Python path.
(Both the site-packages and /usr/share/openshot folders were checked)

Use the following command to install OpenShot:
  $ sudo python setup.py install

tshipp@Harold:~$ sudo python setup.py install
[sudo] password for tshipp: 
python: can't open file 'setup.py': [Errno 2] No such file or directory
tshipp@Harold:~$ $sudo python setup.py install
python: can't open file 'setup.py': [Errno 2] No such file or directory

I know there is probably a simple solution for this, but I dont know it and Im still new to ubuntu.  BTW I am running Karmic, which is supposed to be compatible. So, how do I do this?

---

### Post by shipp on 2010-04-04
I found out that I had to create the following link to use the mlt pathways needed to start open shot.  This worked for me.  Openshot has a good forum with more options on it as well.

$ sudo ln -s /usr/lib/libmlt++.so.0.5.0 /usr/lib/libmlt++.so.

---

### Post by cocopuffz on 2010-04-05
I did my update yesterday from 0.9 to 1.1 and had the same problem as you. It just didn't want to open. I'll give this a try right now.

thanks!

---

### Post by cocopuffz on 2010-04-05
It didn't work for me...

******@*****-laptop:~$ openshot
Added /usr/share/openshot to system path
--------------------------------
   OpenShot (version 0.9.54)
--------------------------------

(openshot:27388): libglade-WARNING **: could not find glade file '/usr/share/openshot/windows/glade/Main.glade'
Traceback (most recent call last):
  File "/usr/bin/openshot", line 50, in <module>
    main()
  File "/usr/share/openshot/openshot.py", line 57, in main
  File "/usr/share/openshot/windows/MainGTK.py", line 47, in __init__
  File "/usr/share/openshot/windows/SimpleGladeApp.py", line 102, in __init__
  File "/usr/share/openshot/windows/SimpleGladeApp.py", line 340, in create_glade
RuntimeError: could not create GladeXML object

I don't know why it has a reference to "windows"  as I'm installing via the deb provided on the site.
---------------
*EDIT*
---------------
I figured it out... turns out the 1.1 isn't compatible with Ubuntu 8.10... they went from LibGlade to a new version of GTK that's only installed on 9 & 10. Oh well. I guess it's almost time to update my OS...

---

