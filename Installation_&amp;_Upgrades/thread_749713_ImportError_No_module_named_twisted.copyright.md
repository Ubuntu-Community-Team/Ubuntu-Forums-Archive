---
title: "ImportError: No module named twisted.copyright"
date: 2008-04-08
forum: Installation &amp; Upgrades
---

### Post by Nicepen on 2008-04-08
Hello,

I've been trying to get Hellanzb installed for a few days now and this import error has been in my way the whole time.  I have followed [these instructions]("http://ubuntuforums.org/showthread.php?t=169749&highlight=install+twisted") to install hellanzb.  Once I get to step 9 to run the program I type in hellanzb.py and I get this response from terminal:

Traceback (most recent call last):
  File "/usr/local/bin/hellanzb.py", line 14, in <module>
    from Hellanzb.Core import main
  File "/usr/local/lib/python2.5/site-packages/Hellanzb/Core.py", line 9, in <module>
    from Hellanzb.HellaReactor import HellaReactor
  File "/usr/local/lib/python2.5/site-packages/Hellanzb/HellaReactor.py", line 11, in <module>
    import twisted.copyright
ImportError: No module named twisted.copyright

I have followed these instructions to fix the problem and they have not worked.
------------------
sizzam
April 22nd, 2007, 04:31 PM
I was having the same problem with hellanzb installed from source on a fresh install of Feisty. Here is how I fixed it:

hellanzb is now in the repositories.

First, I got rid of the copy of hellanzb that I installed:

$ sudo rm /usr/bin/hellanzb.py
$ sudo rm -rf /usr/lib/python2.5/site-packages/Hellanzb/
$ sudo rm /usr/etc/hellanzb.*

I then installed hellanzb from the repos. Note that if you are doing a fresh install from the repos, you also need unrar and par2.

$ sudo aptitude install hellanzb unrar par2

I then executed hellanzb from a command line

$ hellanzb

and it worked. After that, I killed hellanzb and configured it. Note that your configuration file is now /etc/hellanzb.conf instead of /usr/etc/hellanzb.conf

Now I add this command to start hellanzb using screen whenever I log into Gnome:

screen -S hellanzb -d -m hellanzb

and I use this shortcut in Gnome to connect to that screen (make a custom shortcut with type 'Application in Terminal'):

screen -R hellanzb
-----------------------

Since the error message I get has to do with twisted I went to their site and found something similar to my problem in their FAQ.  [HERE]("http://twistedmatrix.com/trac/wiki/FrequentlyAskedQuestions#WhyamIgettingImportErrorsforTwistedsubpackagesonmy64bitinstallationofRedHatFedoraCentOS")
I don't know how to move the correct "parts" to the /usr/lib folder.  I don't know what the correct "parts" are.  Also I don't know how to "supply the --install-lib parameter."

Could someone please advise me on how to deal with this and let me know if I'm on the right path.  

Thanks,

Aaron

---

### Post by Nicepen on 2008-04-14
AWESOME!  I got it.

This is a problem for lots of people and it is a know error with a simple solution. For whatever reason the solution doesn't get shared very often.  I worked through a few errors before I ended up at just another error and that was the final one.  Install hellanzb v0.11 and you should be good. .8, .9, and .13 didn't work for me but .11 did.  You can get it here:
[http://www.hellanzb.com/distfiles/](http://www.hellanzb.com/distfiles/)

Good luck!

---

