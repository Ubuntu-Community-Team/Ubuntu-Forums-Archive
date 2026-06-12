---
title: "*SOS* Problems about libavformat52!!!!!!!!!!!"
date: 2010-05-15
forum: Installation &amp; Upgrades
---

### Post by wangyu on 2010-05-15
[SIZE=3]My english is not very well........[/SIZE]

There are some problems occur during i am installing a package(libcv4),it shows that i need to install the libavformat52 package first. 

But the libavformat52 package had installed in my ubuntu systerm(I had checked the Synaptic Package Manager, the status of libavformat52 is installed).

[SIZE=5][COLOR=Red]Why does this situation happen?Anybody can help me solve this problem????[/COLOR][/SIZE]

I used the command [COLOR=Lime][COLOR=Blue]**sudo apt-get  install -f**[/COLOR] [/COLOR],but new problems occured:

WARNING: The  following packages cannot be authenticated!
  libavformat52
Install  these packages without verification [y/N]? y
(Reading database ...  130896 files and directories currently installed.)
Unpacking  libavformat52 (from .../libavformat52_4%3a0.5.1-1ubuntu1_i386.deb) ...
[COLOR=#FF0000]dpkg: error processing  /var/cache/apt/archives/libavformat52_4%3a0.5.1-1ubuntu1_i386.deb  (--unpack):
 trying to overwrite '/usr/lib/libavformat.so.52.31.0',  which is also in package libavformats52 0:0.5-3[/COLOR]
dpkg-deb:  subprocess paste killed by signal (Broken pipe)
Errors were  encountered while processing:
  /var/cache/apt/archives/libavformat52_4%3a0.5.1-1ubuntu1_i386.deb
E:  Sub-process /usr/bin/dpkg returned an error code (1)

[SIZE=6][COLOR=Red]What should i do now????[/COLOR][/SIZE]:confused:

[SIZE=3][COLOR=Blue]Would you please use simple sentences to describe the solution????
Thank you very very much!!!!!![/COLOR][/SIZE]

---

