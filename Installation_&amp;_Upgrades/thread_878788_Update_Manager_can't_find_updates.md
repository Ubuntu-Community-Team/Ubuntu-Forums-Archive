---
title: "Update Manager can't find updates"
date: 2008-08-03
forum: Installation &amp; Upgrades
---

### Post by dbirran on 2008-08-03
Downloaded updates yesterday but 5 updates were not found.  Don't have a clue about what to do now.  I am a recent Windows XP convert to Ubuntu.  

Thanks, 
Dennis

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/p/python2.5/python2.5_2.5.2-2ubuntu4.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/p/python2.5/python2.5_2.5.2-2ubuntu4.1_i386.deb)
  404 Not Found


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/p/python2.5/python2.5-minimal_2.5.2-2ubuntu4.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/p/python2.5/python2.5-minimal_2.5.2-2ubuntu4.1_i386.deb)
  404 Not Found


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/o/openldap2.3/libldap-2.4-2_2.4.9-0ubuntu0.8.04.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/o/openldap2.3/libldap-2.4-2_2.4.9-0ubuntu0.8.04.1_i386.deb)
  404 Not Found


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/libx/libxslt/libxslt1.1_1.1.22-1ubuntu1.2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/libx/libxslt/libxslt1.1_1.1.22-1ubuntu1.2_i386.deb)
  404 Not Found


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/libx/libxslt/xsltproc_1.1.22-1ubuntu1.2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/libx/libxslt/xsltproc_1.1.22-1ubuntu1.2_i386.deb)
  404 Not Found

---

### Post by kajillin on 2008-08-03
ive got the same problem

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/libx/libxslt/libxslt1.1_1.1.22-1ubuntu1.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/libx/libxslt/libxslt1.1_1.1.22-1ubuntu1.1_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/libx/libxslt/xsltproc_1.1.22-1ubuntu1.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/libx/libxslt/xsltproc_1.1.22-1ubuntu1.1_i386.deb)
  404 Not Found

---

### Post by dbirran on 2008-08-03
I, apparently, may have accidentally resolved this issue.  I went into Synaptic Package Manager, Software Sources, Third Party Software and unchecked references to Gutsy and Fiesty.   When I ran the update again, it found the five packages it could not find before.  Was this do to unchecking the Gutsy and Fiesty sources or was it something else?  I may never know...:confused:

Dennis

---

### Post by coffeecat on 2008-08-03
> 404 Not Found

The server was down. It happens occasionally. Just wait a few hours and try again.

Or, in Synaptic, Settings > Repositories > Ubuntu Software - select another download server.

---

