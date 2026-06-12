---
title: "Upgraded to Gutsy - some repos still Dapper"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by genterminl on 2007-10-19
Within the past two weeks, I upgraded from Dapper to Edgy to Feisty to Gutsy.  All done through the Update Manager.  In general, everything actually went smoothly (aside from some long waits).  I had quite a few remnants to manually fully remove at each stage.  I suppose that is to be expected, but it would be nice if you didn't have to select each one individually in Synaptic.  Anyway - the main remaining problem is that when I upgrade my package list, there are lots of failures, finally ending with a popup titled "Could not download all repository indexes" containing ```
http://medibuntu.sos-sts.com/repo/dists/dapper/free/binary-i386/Packages.gz: 302 Found
http://medibuntu.sos-sts.com/repo/dists/dapper/non-free/binary-i386/Packages.gz: 302 Found
``` The non comment lines from my /etc/apt/sources.list are ```

deb-src http://ubuntu.media.mit.edu/ubuntu/ gutsy main restricted

deb http://ubuntu.media.mit.edu/ubuntu/ gutsy-updates restricted main universe
deb-src http://ubuntu.media.mit.edu/ubuntu/ gutsy-updates main restricted

deb-src http://ubuntu.media.mit.edu/ubuntu/ gutsy universe

deb http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://ubuntu.media.mit.edu/ubuntu/ gutsy-security main restricted
deb-src http://ubuntu.media.mit.edu/ubuntu/ gutsy-security main restricted
deb http://ubuntu.media.mit.edu/ubuntu/ gutsy-security universe
deb-src http://ubuntu.media.mit.edu/ubuntu/ gutsy-security universe
deb http://ubuntu.media.mit.edu/ubuntu/ gutsy multiverse universe main restricted

``` I don't believe I have ever manually edited this file.  Only the backports line refers to dapper.  From the Software Sources app, this is for the Unsupported Updates under the Third-Party Software tab..  Can I safely just change dapper to gutsy here?

Also, I have mediabuntu selected, and it also specifies dapper, although I don't see it in sources.txt.

Any suggestions would be appreciated, but if you're going to say RTFM, at least tell me which fine manual I need to read.

Thanks.

---

### Post by genterminl on 2007-10-19
Well, I suppose I shouldn't be replying to my own post, but I did figure it out with a bunch more searching.  It turns out that the official name of the medibuntu (am I the only one who keeps thinking it's mediabuntu?) has changed from medibuntu.sos-sts.com to medibuntu.org.  I went into the Software Sources app and changed the address (as well as changing dapper to gutsy for the other entry under the Third-Party Software tab.

Also, medibuntu isn't in /etc/apt/sources.list, like I expected, but in /etc/apt/sources.list.d/medibuntu.list.

---

### Post by jetpeach on 2007-10-19
haha, no definitely won't tell yo uto RTFM....

i read here 
[http://bapoumba.wordpress.com/2007/10/02/medibuntu-non-free-codecs-for-gutsy/](http://bapoumba.wordpress.com/2007/10/02/medibuntu-non-free-codecs-for-gutsy/)
that for gutsy, for medibuntu replace the one that's erroring with:

# # Medibuntu.  
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) gutsy free non-free 
then to add the key put in command line:
wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update

if your non-free codecs aren't already installed (they may be, but i'm not sure how or if they'd be uptodate if the repository wasn't correct for gutsy
then type
sudo apt-get install non-free-codecs
or you might just need to apt-get update...

but, it seems the necessity of the medibuntu repository is less than it used to be, because is another repository from ubuntu is on the block to handle some of these restricted stuffs, not things like w32codecs but things like flashplugin-nonfree etc, it looks like its already included in your list though

and yes, i think you can just manually change it to gutsy and that should take care of backports.

---

