---
title: "Installing KontrolPack"
date: 2010-11-03
forum: Installation &amp; Upgrades
---

### Post by newperson on 2010-11-03
I downloaded version 3.0.0 of this software. I downloaded the windows and mac versions also because I want to try and set up a network of computers using the internet and people I know.

I was following the readme file to how to install it.

So far I have extracted the tarball to a folder called Kontrolpack in my home directory and I have done step 1 which is:
> 
sudo apt-get install g++and step 2, which is:> 

 sudo apt-get install libqt4-dev libssl-dev libxml2-dev libsqlite3-dev

And step 3, which is:

> 3. Download sources from kontrolpack.com and uncompress the tarball kontrolpack-x.x.x.tar.gz :

 I am having problems with step 4, 5 and 6.

They are:
> 
4. Go into the libsecuretcp bin directory

    cd libsecuretcp/

And run the following command :

    qmake

Then run :

    make

You should see the libsecuretcp binary into the bin/ directory
 
5. Go to the kontrolpack directory

    cd kontrolpack/

And run the following command :

    qmake

Then run :

    make

You should see the kontrolpack binary into the bin/ directory, run :

    ./kontrolpack

6. Have fun :-)Can someone help me?

Thanks.

---

### Post by newperson on 2010-11-03
Anyone?

---

### Post by newperson on 2010-11-03
Version 2.0.3, which is what this distro came with works fine, but when I load it up it says version 3.0.0 is available. 

I try to install it, and follow all the instructions perfectly, and it says it is all done, but when I try and run the KontrolPack file it doesn't work, and off the Ubuntu server I still get version 2.0.3, instead of version 3.0.0 from the KontrolPack website.

Is it backwards compatible? Because if it is I guess I have not much to worry about anyway, and the upgrade is unnecessary.

---

