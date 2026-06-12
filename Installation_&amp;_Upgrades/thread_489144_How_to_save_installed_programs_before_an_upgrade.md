---
title: "How to save installed programs before an upgrade"
date: 2007-07-01
forum: Installation &amp; Upgrades
---

### Post by frazelle09 on 2007-07-01
i've got 2 partitions, one for the OS and the other for /home.  i'd like to be able to not have to reinstall all the programs again after installing the OS again on the first partition.  Is this possible?

Someone suggested i save my /var/cache... to my /home directory or a CD or ... and then after the reinstall, copy it back.  i did that the last time, but still had to use apt-get install for each of the programs and apt-get did not use the /var/cache... but went directly to the repos on the net.

Any ideas?

Have a great evening!  :)

---

### Post by oldmanstan on 2007-07-01
here, take a look at this thread, you should be able to do this with a bash script, you'd still be reinstalling the software but it would be automatic so the only time wasted would be download / setup time and you wouldn't have to sit there while it worked (except for packages that require input) :)

[http://ubuntuforums.org/showthread.php?p=1701160]("http://ubuntuforums.org/showthread.php?p=1701160")

---

### Post by frazelle09 on 2007-07-01
OutSTANding!!!  Thanks a million!  i'm currently "trying" to help out with the beta testing of Freespire and needed something like this script.

i'll make it up and try it tomorrow when the second beta comes out.  Boy this is great!

Have a wonderful day -- and your photos on your website are very beautiful as well!  :)

---

### Post by frazelle09 on 2007-07-01
Would you be so kind as to check this, please?  i think i saw somewhere that i need a line which allows Unauthenticated installs.

> #!/bin/bash
#
# This script is the first in a series of setup scripts for fred.  Copied from Ubuntu Forums.

# Check for admin rights. If user is not an admin user, exit the script
if [ $UID != 0 ]
then
echo "Fred! You need to be root to run this script! Exiting..."
   exit
fi

# Update the system sources and software
apt-get clean
apt-get update
# apt-get upgrade Uncheck this once you have finished upgrading and see if it's possible to
# do so with Freespire's new beta version.
# aptitude dist-upgrade
# aptitude clean

# Install some desired software
# Any number of apps can be listed for install here, but
# they must be seperated by a space and the whole thing
# needs to be one single line
apt-get install krusader inkscape kpdf picasa amsn opera amarok jpilot glom gnucash kontact synaptic cdcat kpilot wine gimp googleearth hplip

# Cleanup after install
apt-get clean

exit 


Thanks for all your help and have a great afternoon!  :)

---

### Post by oldmanstan on 2007-07-01
> **frazelle09 said:**
> Would you be so kind as to check this, please?  i think i saw somewhere that i need a line which allows Unauthenticated installs.

i've personally never used a script like this before, but it looks alright based on a quick glance, you might try testing it on clean install just to be sure (in other words, one that can afford to get screwed up)

---

### Post by frazelle09 on 2007-07-01
Good man, STAN!  Thanks a lot.  i guess i'll be giving it a try tomorrow when the Freespire beta comes out again.

So, have a great evening!  :)

---

### Post by oldmanstan on 2007-07-03
here's another possible option, might be simpler... [http://www.linuxforums.org/forum/debian-linux-help/40955-need-list-installed-packages.html]("http://www.linuxforums.org/forum/debian-linux-help/40955-need-list-installed-packages.html")

of course this assumes (i think) that you haven't installed any packages that weren't in the repos, since dpkg would see and list those as well but then when you went to apt-get them they wouldn't be there, it shouldn't be a fatal error though so as long as you know which ones you can just let it skip them

---

### Post by frazelle09 on 2007-07-04
Thanks, again, Stan!  i'll try this one the next time.  Since it gave me a very long list, can i just make a list of the programs that i usually install?  i suspect that most of the list consists of the programs that Freespire installs itself and i only need a few more.

Should it be a list with hard returns or one long line with the names separated by a space? e.g "krusader inkscape kpdf picasa amsn opera amarok jpilot glom gnucash kontact synaptic cdcat kpilot wine gimp googleearth hplip"

Have a great holiday!  :)

---

### Post by oldmanstan on 2007-07-04
the list dpkg spits out through awk is one package per line, so yeah, you could do one package per line in a text file, that'd work just fine i should think, according to that person on the other forum anyway

---

