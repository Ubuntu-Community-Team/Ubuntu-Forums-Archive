---
title: "E: python-wxgtk2.8: subprocess post-installation script returned error exit status 1"
date: 2009-04-05
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by edwin.galloway on 2009-04-05
Whenever I try to install any package (through synaptic or update manager or terminal) I get the following error:

E: python-wxgtk2.8: subprocess post-installation script returned error exit status 1

When I look at the details, if I am reading correctly, I have python 3.0 installed now (I assume from an earlier upgrade) but the package manager is still looking for the older python bits, i.e.:

...
Setting up python-wtgk2.8 (2.8.9.1-0ubuntu5) ...
INFO: using unknown version '/usr/bin/python3.0' debian_defaults not up -to-date?)
file does not exist: /usr/lib/python2.6/dist-packages/wx-2.8-gtk-unicode/wx/_init_.py

etc., over and over, then:

pycentral: pycentral pkginstall: error byte-compiling files (434)
dpkg: error processing python-wxgtk2.8 (--configure):
subprocess post-installation script returnes error exit status 1
Errors were encountered while processing:
python-wxgtk2.8

Does this sound reasonable?

I can't shake the feeling that if I was smarter I could hop into terminal and get this sorted in a jiffy.

I did read the 'Python is Borked' post from a week ago, as well as what looked like a similar and related issue in the post: 

Intrepid-Upgrade fails - 'Trying to install blacklisted version 'python2.6_2.6.1-'

Neither seemed to have information that would fully resolve my issue. This has been going on the last two days.

---

### Post by edwin.galloway on 2009-04-05
Then seconds later on the 101st page in this forum:

After the alpha-5 release we will update the python interpreter from 2.5.4 to
2.6.1.  For about 24 hours you will no be able to cleanly update jaunty, until
some packages are rebuilt with python2.6. For a better upgrade experience during
 this time, please add the pythoneers PPA to your sources.list, which already
has the rebuilds available:

  deb [http://ppa.launchpad.net/pythoneers/ppa/ubuntu](http://ppa.launchpad.net/pythoneers/ppa/ubuntu) jaunty main

Don't forget to remove this line after the change is complete; I will notice
u-d-a when the change is done for main. For universe you may experience
installability issues somewhat longer.

  Matthias


...So is this my issue? Also, sorry for spamming up the forums.

---

