---
title: "Problem installing libx11-dev: &quot;The following packages have unmet dependencies&quot;"
date: 2013-11-17
forum: Installation &amp; Upgrades
---

### Post by aleksandar.rachkov on 2013-11-17
Hi.

I am somewhat new to the UNIX environment, but I think I have started catching up recently. My problem is I need to install this software called HEASOFT, which when I do, I get the error message:

> checking for X... no
checking X11/Xlib.h usability... no
checking X11/Xlib.h presence... no
checking for X11/Xlib.h... no
configure: error: X11 Development package is required in order to build HEASOFT!


Now, this is is weird, because I thought I had X11 installed already. But I went ahead anyways and typed :"sudo apt-get install libx11-dev". BUt then I get the following error message:

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help resolve the situation:

> The following packages have unmet dependencies:
 libx11-dev : Depends: libx11-6 (= 2:1.4.99.1-0ubuntu2) but 2:1.4.99.1-0ubuntu2.2 is to be installed
              Depends: libxcb1-dev but it is not going to be installed
              Recommends: libx11-doc but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

And I don't know what the problem is or how I can fix it. Could anyone help, please?

---

### Post by clay7 on 2013-11-17
Have you tried going to Update Manager, Settings, and then checking all the boxes on the "Ubuntu Software" and "Other Software" tabs? On the "Update" tab, are the boxes checked?

If not, try that, then: 
sudo apt-get update

...and then try to install the package.

---

### Post by aleksandar.rachkov on 2013-11-17
Yes, this worked fine. THank you so much!
On the "Update" tab, all the boxes were unchecked.

---

### Post by clay7 on 2013-11-17
Great! I'm glad it worked.

---

