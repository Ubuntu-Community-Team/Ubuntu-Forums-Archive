---
title: "OpenCV configuration file not found"
date: 2012-01-03
forum: Installation &amp; Upgrades
---

### Post by mathprof on 2012-01-03
Using an Ubuntu 11.04 system...

I'm trying to install PyOpenCV (a computer vision library), and having some problems.  This requires a few other items like OpenCV (2.1.0-3ubuntu1), Boost (1.42.0), Boost.Python (1.42.0).   So far I installed everything (except PyOpenCV) from the Ubuntu Software Center.  Thus my problem.  When I try to run the command

# python setup.py config

I get the error message: " Could not find a configuration file for package OpenCV."

I noticed that it was finding Python 2.7, rather than the version that I need to use (2.6).  So even if that library was found. this would be a problem.  So I thought I should uninstall Python 2.7, since I don't use it and then the setup script would find Python 2.6.  When I tried to uninstall Python 2.7 using the Ubuntu Software Center it wouldn't let me (due to other stuff that somehow needs Python 2.7).   

Ready for my question?   My question is, what should my question be???? .      :wink:

Here's a more concrete question:  In some of the online blogs, and sometimes hinted at in the documentation on the software webpages, it is suggested that installing it all from scratch manually may be a better way to proceed, for then one has a bit more control over the process, and where everything is.   Should I uninstall everything possible in the Ubuntu Software Center, and then reinstall it all using get-apt, tar, and all that?   

One benefit is I would end up with more up-to-date versions, and I have step-by-step tutorials to get everything up and running.  Sometimes Ubuntu doing everything for me reminds me a little too much of the MS world, which I recently (FINALLY) escaped.

Any ideas??

---

### Post by mathprof on 2012-01-08
I'm using Ubuntu 11.04...  It seems better not to use PyOpenCV (if you even can anymore).    
Instead, simply use the Ubuntu Software Center to install:

OpenCV (version 2.1.0-3ubuntu1).    Ubuntu breaks this up as:
              *     libcv2.1
                     *     libcv-dev  
                     *     libcvaux2.1
                     *     libcvaux-dev 
                     *     libhighgui2.1
                     *     libhighgui-dev
                     *     python-opencv  (the python bindings)

Then you can import the OpenCV library into your python applications thusly:   
        *     import cv

-Rafael Espericueta

---

