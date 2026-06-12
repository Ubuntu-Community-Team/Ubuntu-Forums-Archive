---
title: "[SOLVED] anybody running pidgin on intrepid?"
date: 2008-09-12
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Saint Angeles on 2008-09-12
for some reason, i'm having dependency hell for pidgin on intrepid... check this out:

```
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  pidgin: Depends: pidgin-data (>= 1:2.5.0) but it is not going to be installed
          Depends: pidgin-data (< 1:2.5.0-z) but it is not going to be installed
          Depends: libpurple0 (>= 1:2.5.0-0ubuntu2) but it is not going to be installed
E: Broken packages
```

just wondering if anybody is having this same problem.

---

### Post by Slug71 on 2008-09-12
Pidgin should have been installed be default with Intrepid. It was for me. Have you tried removing it from Synaptic and then reinstalling it with Synaptic again?

---

### Post by psychobillyjekyll on 2008-09-12
My pidgin is working just fine, did you upgrade a Hardy distribution or do a fresh install from a disc?

---

### Post by Gourgi on 2008-09-12
[QUOTE=psychobillyjekyll;5775057]My pidgin is working just fine, /QUOTE]
 +1
working great here with all my accounts and  irc

---

### Post by beercz on 2008-09-12
Works fine here too.

I upgraded from Hardy to Intrepid about a month ago and pidgin has worked flawlessly.

---

### Post by inportb on 2008-09-12
Do you have any nonstandard repositories on your list? Also, you could try removing all these pidgin packages, then installing pidgin again.

---

### Post by Saint Angeles on 2008-09-12
i did an upgrade from hardy... i have nothing but standard intrepid repos.

i've tried uninstalling and reinstalling but no luck... whenevr i try to install each of the components (libpurple, pidgin data...) it points me towards another file... i try to install that and it points me to another files... and another...

its horrible i tell ya! kopete is no good!

---

### Post by avb on 2008-09-13
im using it without any problem. What exact problem are u getting? Seems u was using pidgin package from unofficial repository. 
try to remove pidgin,pidgin-data libpurple0 libpurple-bin, check your repos in sources.list in order to remove unofficial repos, do apt-get update and then try again apt-get install pidgin.

---

### Post by codingwolf on 2008-10-20
> **Saint Angeles said:**
> i did an upgrade from hardy... i have nothing but standard intrepid repos.

i've tried uninstalling and reinstalling but no luck... whenevr i try to install each of the components (libpurple, pidgin data...) it points me towards another file... i try to install that and it points me to another files... and another...

its horrible i tell ya! kopete is no good!


I have to agree, my pidgin was also crashing and locking up/freezing in the same manor. The "sudo apt-get install pidgin" isn't working (complains about libpurple and perl), yet upon downloading the source directly from pidgin.im and configuring it using:

```
./configure --disable-screensaver --disable-startup-notification --disable-gtkspell --disable-gstreamer --disable-meanwhile --disable-avahi --disable-nm --disable-perl --disable-tcl
```

then compiling it using:

```
make
sudo make install
```

Everything is now working perfectly with pidgin.

My guess is the main repo hasn't updated to the latest code yet or they just havn't fixed perl for it yet. Note the --disable-perl in the configure.

I hope this helps someone out.

---

### Post by jfernyhough on 2008-10-20
Try adding the Pidgin Devel repo to your sources.list. This will also have the added bonus of installing 2.5.1. :)

## Pidgin devel
deb [http://ppa.launchpad.net/pidgin-developers/ubuntu](http://ppa.launchpad.net/pidgin-developers/ubuntu) intrepid main
# deb-src [http://ppa.launchpad.net/pidgin-developers/ubuntu](http://ppa.launchpad.net/pidgin-developers/ubuntu) intrepid main

Also try using Synaptic and forcing the correct version.

---

### Post by yellowaeroplane on 2008-10-21
@Saint Angeles, I was having the exact same "dependency hell" issues you were. 

After a few hours of pulling my hair out, this is how I got Pidgin working:

1) Use Synaptic to remove as many of the related packages as you can...

2) Then run these commands:

```

$ sudo apt-get remove pidgin-data
$ sudo apt-get remove pidgin
$ sudo apt-get remove libpurple0
$ sudo apt-get install pidgin

```

I know it doesn't make much sense... but like I said, it worked for me.

good luck!

---

### Post by Saint Angeles on 2008-10-21
thanks for all the help!

this problem fixed itself. but then xorg upgraded to 7.4 and fglrx wasn't compatible so i had to downgrade to hardy.

but then, i upgraded to intrepid AGAIN last night. everything is amazing now!

---

