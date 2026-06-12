---
title: "Update manager won't update( I must use Terminal)"
date: 2010-02-06
forum: Installation &amp; Upgrades
---

### Post by livetobefree on 2010-02-06
I can't add apps or Update from UpDate Manager anymore.  I already know how to add and install them from the terminal ( that is sometimes annoying an inconvenient) but I can't figure out why I can't update from the Update manager or add apps from Synaptic like I used to be able to.  Is there Any way to find out,  ALL  the hidden programs that are installed on my computer perhaps its one of them I installed that I forgot about and are somehow blocking them ?   

  I think I installed something that blocks it,  I did have **nmap** and** zenmap( not sure if it was Zenmap or Zenmap as root) ** ( but I removed them)  I did suspect it had something to do with those two programs but Im not sure.

 Any advice would be helpful, thanks and have a great day.

---

### Post by oldos2er on 2010-02-06
How exactly does Update Manager fail? Can you post any error messages, or a screenshot?

---

### Post by livetobefree on 2010-02-07
> **oldos2er said:**
> How exactly does Update Manager fail? Can you post any error messages, or a screenshot?


Hi Ann,

  Thanks for asking, I copied the message as follows , it says practically the same thing for everything I try to add or up grade

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/3/3dchess/3dchess_0.8.1-15_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/3/3dchess/3dchess_0.8.1-15_i386.deb)
  Unable to connect to 114.30.47.10 8080:

---

### Post by oldos2er on 2010-02-07
114.30.47.10 seems to be down. Have you tried any different servers? System, Administration, Software Sources, click the drop-down menu after Download from:, Other, Select Best Server.

---

### Post by livetobefree on 2011-06-24
I really don't know what to do.  I really need someone in the mIlwaukee area to take a look at my laptop.  

This is what I get when I try to open UPDATE MANAGER;;;;;



An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/ubuntu.mirrors.tds.net_pub_ubuntu_dists_lucid_universe_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'

I'm totally lost , and have no idea what to even do.

---

### Post by livetobefree on 2011-06-24
this is what happened when I changed to the server for the U.S.    

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/binary-i386/Packages.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/binary-i386/Packages.bz2)  Sub-process /bin/bzip2 returned an error code (2)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/source/Sources.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/source/Sources.bz2)  Sub-process /bin/bzip2 returned an error code (2)
Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by Rubi1200 on 2011-06-25
Have you managed to resolve this issue yet?

If not, please run this command and post any error messages:

```
sudo apt-get update
```

Thanks.

---

