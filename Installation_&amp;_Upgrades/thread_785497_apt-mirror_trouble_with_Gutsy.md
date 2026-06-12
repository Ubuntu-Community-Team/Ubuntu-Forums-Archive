---
title: "apt-mirror trouble with Gutsy"
date: 2008-05-07
forum: Installation &amp; Upgrades
---

### Post by bstempi on 2008-05-07
Hi all,

I have an Ubuntu Gutsy VM that I wanted to use for doing netinstalls on my LAN.  To do this, I installed apt-mirror.  I intend on installing Hardy on all of my machines, so I opened the mirror.list file and replaced all instances of "gutsy" with "hardy".  When I run "apt-mirror", I get the following output:
```

root@xen01-7:~# apt-mirror
Downloading 22 index files using 20 threads...
Begin time: Tue May  6 14:55:14 2008
[20]... [19]... [18]... [17]... [16]... [15]... [14]... [13]... [12]... [11]... [10]... [9]... [8]... [7]... [6]... [5]... [4]... [3]... [2]... [1]... [0]... 
End time: Tue May  6 15:05:17 2008

Proceed indexes: [Psh: cannot open archive.ubuntu.com/ubuntu//dists/hardy/main/binary-: No such file
apt-mirror: can't open index in proceed_index_gz at /usr/bin/apt-mirror line 382.
```

To me, this appears to be a problem with the script itself.  Any ideas or thoughts?  Any help is appreciated.

Thanks,
Brian

---

### Post by bstempi on 2008-05-07
Funny story....

So, in the mirror.list config file, there's a section for system architecture.  The default is something to the effect of "<local system architecture>".  I assumed that this was a variable that would be evaluated to, in my case "i386" during runtime.  Once I replaced that string with "i386", things began working correctly.

---

