---
title: "missing python files after successful install"
date: 2011-01-05
forum: Installation &amp; Upgrades
---

### Post by ashish_agarwal on 2011-01-05
I ran 'sudo apt-get install python', which completed successfully. According to [http://packages.ubuntu.com/karmic/python](http://packages.ubuntu.com/karmic/python), this should have created the directory /usr/lib/python2.6, but I do not see any such directory.

This is causing problems:


$ python
Could not find platform independent libraries <prefix>
Could not find platform dependent libraries <exec_prefix>
Consider setting $PYTHONHOME to <prefix>[:<exec_prefix>]
'import site' failed; use -v for traceback
Python 2.6.4 (r264:75706, Dec  7 2009, 18:43:55) 
[GCC 4.4.1] on linux2

I've tried 'apt-get purge python' and then reinstalling but this has not resolved the issue. Thank you for any help.

---

### Post by Cheesehead on 2011-01-06
Yes, it should install that directory.
Curious, do try the command 'which python' and post the result.

But...

All default installations of Ubuntu come with Py2.6 already. You shouldn't need to install it. The ability to purge it without removing half your system is also suspect. So there's something interesting and possibly important about your system that you haven't told us yet.

---

### Post by ashish_agarwal on 2011-01-06
$ which python
/usr/bin/python

$ python --version
Python 2.6.4

So python still runs, although supposedly I uninstalled it. It is also the case that I did indeed uninstall half the system. Oops. A full reinstall will be best at this point. For education sake, I would still be interested to know exactly what's happening. Any insight on why uninstalling python still let's me run it, and reinstalling it, supposedly successfully, does not install files listed in the package?

---

