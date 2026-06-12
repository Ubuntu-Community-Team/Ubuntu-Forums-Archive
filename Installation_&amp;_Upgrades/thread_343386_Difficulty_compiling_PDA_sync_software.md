---
title: "Difficulty compiling PDA sync software"
date: 2007-01-21
forum: Installation &amp; Upgrades
---

### Post by m_vrik on 2007-01-21
I am running Ubuntu Dapper on a Compaq N600c laptop.  I would like to sync my Windows CE based PDA with the Evolution calendar and also my contacts.  Downloaded SynCE 0.9.0 from, Spourceforge.net.  This included several tar balls.  Extracted all of the tar balls to base files.  When I tried to run "./configure" I get an error message that there is no appropriate C compiler in the $PATH.  How do I get these files installed?  Here are the instruction for installing the first file where I encountered the above mentioned error message:

        Compile libsynce:

        tar zxf synce-libsynce-X.X.tar.gz
        cd synce-libsynce-X.X
        ./configure
        make
        make install
        cd ..

And so on with the next file.  Well I havn't gotten through the configure issue on the "libsynce" file yet.  Thanks in advance.

---

