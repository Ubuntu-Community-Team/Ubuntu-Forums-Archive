---
title: "HOWTO: Installing SpamBayes plugin for Evolution under Gutsy"
date: 2008-02-12
forum: Installation &amp; Upgrades
---

### Post by jfrorie on 2008-02-12
IMO, spamassasin and bogofilter suck most egregiously under Evolution.  I've used SpamBayes under w*indows and it beats everything, opensource and commercial.  However, the plugin doesn't install under gutsy for some reason.

After flogging my system for about an hour, I got it installed.  Behold:

# install spambayes
sudo apt-get install spambayes

# Get the source archive for the evolution plugin 
[http://dev.infonet.dk/debian/dists/testing/source/evolution-plugin-spambayes_0.1.5.tar.gz](http://dev.infonet.dk/debian/dists/testing/source/evolution-plugin-spambayes_0.1.5.tar.gz)

# Pull up the file manager and extract all the files
# click-click-click :)  I dunno the command
# tar -xvf evolution-plugin-spambayes_0.1.5.tar.gz perhaps??????

# cd to that directory (or where ever you put it..)
cd ~/sb-eplugin

# gedit configure.ac file and replace every instance of evolution-plugin-2.10 to evolution-plugin (two places) 

# Install the libraries
sudo apt-get install libtool
sudo apt-get install libgtk2.0-dev
sudo apt-get install evolution-dev

# Generate magic stuff
sudo ./autogen.sh

# Configure, build and install
./configure
sudo make
sudo make install

# The plugin should appear.  You will have to turn off bogofiler and spamassasin if installed.

I'm still a newbie, so I'm not sure if I can answer any questions if things get gnarly...

Enjoy
Jim

---

### Post by JohnnyS987 on 2008-04-02
Thanks very much for the info. 

I still have a problem: I did all that and I still get an error when I try to select SpamBayes in the Evolution Junk mail configuration: It says "Spambayes plugin is not available. Please check whether the package is installed." 

I definitely have the spambayes package installed. Any ideas?

JS

---

### Post by jfrorie on 2008-04-03
I really don't have a clue.  Have you tried running spambayes by itself?

---

### Post by causticburning on 2008-04-10
# Generate magic stuff
sudo ./autogen.sh

For me, this step fails with the error:

laren@laren-desktop:~/sb-eplugin$ sudo ./autogen.sh
./autogen.sh: 9: aclocal: not found
./autogen.sh: 10: autoconf: not found
./autogen.sh: 13: autoheader: not found
./autogen.sh: 14: automake: not found
laren@laren-desktop:~/sb-eplugin$ 

No idea what to try next?

---

### Post by jfrorie on 2008-04-11
sudo apt-get install automake autoconf autoheader aclocal

---

