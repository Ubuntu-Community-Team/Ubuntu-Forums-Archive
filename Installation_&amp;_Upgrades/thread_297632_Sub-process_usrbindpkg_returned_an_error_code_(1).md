---
title: "Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2006-11-11
forum: Installation &amp; Upgrades
---

### Post by adrian1979 on 2006-11-11
From several days now I keep on reading and trying ways to update my system but I just can't.
Iam not an expert at all so please be specific in your reply.
Thanks a lot for your help and time in advance.

From the terminal:

$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
The following packages have been kept back:
skype
The following packages will be upgraded:
cpio fglrx-control imagemagick info language-pack-en language-pack-gnome-en libavahi-client3 libavahi-common-data
libavahi-common3 libavahi-glib1 libavahi-qt3-1 libimlib2 libmagick9 libmusicbrainz4c2a libpq4 libqt3-mt libruby1.8
linux-restricted-modules-2.6.15-27-386 linux-restricted-modules-common python-matplotlib python-numpy python-scipy
python2.4-examples ruby1.8 screen xinit xorg-driver-fglrx xorg-driver-fglrx-dev
28 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
5 not fully installed or removed.
Need to get 0B/38.1MB of archives.
After unpacking 10.5MB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
python-numpy python-matplotlib python-scipy
Install these packages without verification [y/N]? y
Preconfiguring packages ...
Setting up python2.4-minimal (2.4.3-0ubuntu6) ...
Compiling python modules in /usr/lib/python2.4 ...
Compiling /usr/lib/python2.4/scipy/lib/python2.4/test/badsyntax_future3.py ...
SyntaxError: ('future feature rested_snopes is not defined',)

Compiling /usr/lib/python2.4/scipy/lib/python2.4/test/badsyntax_future4.py ...
SyntaxError: ('from __future__ imports must occur at the beginning of the file',)

Compiling /usr/lib/python2.4/scipy/lib/python2.4/test/badsyntax_future5.py ...
SyntaxError: ('from __future__ imports must occur at the beginning of the file',)

Compiling /usr/lib/python2.4/scipy/lib/python2.4/test/badsyntax_future6.py ...
SyntaxError: ('from __future__ imports must occur at the beginning of the file',)

Compiling /usr/lib/python2.4/scipy/lib/python2.4/test/badsyntax_future7.py ...
SyntaxError: ('from __future__ imports must occur at the beginning of the file',)

Compiling /usr/lib/python2.4/scipy/lib/python2.4/test/badsyntax_future8.py ...
SyntaxError: ('future statement does not support import *',)

Compiling /usr/lib/python2.4/scipy/lib/python2.4/test/badsyntax_future9.py ...
SyntaxError: ('not a chance',)

Compiling /usr/lib/python2.4/scipy/lib/python2.4/test/badsyntax_nocaret.py ...
File "/usr/lib/python2.4/scipy/lib/python2.4/test/badsyntax_nocaret.py", line 2
[x for x in x] = x
SyntaxError: can't assign to list comprehension

Compiling /usr/lib/python2.4/scipy/src/matplotlib/matplotlib/examples/embedding_in_wx.py ...
Sorry: IndentationError: ('unindent does not match any outer indentation level', ('/usr/lib/python2.4/scipy/src/matplotlib/matplotlib/examples/embedding_in_wx.py', 65, 44, ' self.toolbar.SetSize(wxSize(fw, th))\n'))
Compiling /usr/lib/python2.4/scipy/src/matplotlib/users_guide/code/matplotlib_matlab.py ...
File "/usr/lib/python2.4/scipy/src/matplotlib/users_guide/code/matplotlib_matlab.py", line 2
from pylab import * % no import necessary
^
SyntaxError: invalid syntax

Compiling /usr/lib/python2.4/scipy/src/matplotlib-0.87.3/examples/embedding_in_wx.py ...
Sorry: IndentationError: ('unindent does not match any outer indentation level', ('/usr/lib/python2.4/scipy/src/matplotlib-0.87.3/examples/embedding_in_wx.py', 65, 44, ' self.toolbar.SetSize(wxSize(fw, th))\n'))
dpkg: error processing python2.4-minimal (--configure):
subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
python2.4-minimal
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by pwnb0t on 2007-03-31
I'm having a similar problem that I posted about here:
[http://www.ubuntuforums.org/showthread.php?p=2381898#post2381898](http://www.ubuntuforums.org/showthread.php?p=2381898#post2381898)

Did you ever get this figured out?

---

### Post by pwnb0t on 2007-03-31
If you're still having problems, then check out the post I mentioned, I may have come up with a work-around.

---

