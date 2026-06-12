---
title: "Mass installation of ubuntu servers"
date: 2012-10-20
forum: Installation &amp; Upgrades
---

### Post by b0nehead on 2012-10-20
Hi All,
I need to be able to rapidly deploy Ubuntu VMs for testing. Using Redhat Enterprise or Centos/Scientific I'd use Kickstart and Satellite/Spacewalk. It seems that Ubuntu only has limited Kickstart support, and their Spacewalk equivalent is Landscape (a paid for service), which has no free alternative.

Can anyone recommend any Ubuntu deployment/management tools? Am I missing something obvious?

Cheers...

b0nehead

---

### Post by Lars Noodén on 2012-10-20
You should still be able to use Kickstart.  You can also use the more advanced, but harder, Debian installer preseed.  

[http://wiki.debian.org/DebianInstaller/Preseed](http://wiki.debian.org/DebianInstaller/Preseed)

Also, rather than burning a new disc image for each try, you can burn one that uses HTTP or Anonymous FTP to point to a file on your server.  That way during testing all you have to do is edit the one file to make changes.

---

