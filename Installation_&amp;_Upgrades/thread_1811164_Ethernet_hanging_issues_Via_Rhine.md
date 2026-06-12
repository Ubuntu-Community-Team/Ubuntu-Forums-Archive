---
title: "Ethernet hanging issues Via Rhine"
date: 2011-07-24
forum: Installation &amp; Upgrades
---

### Post by greenslade on 2011-07-24
First off, this is my first ever Linux project.

I'm setting up a media file server with Mediatomb and Transmission on an old machine, and I've got a peculiar problem.

I've installed the latest version of the server distribution. I've got everything set up, I can SSH in, I've mounted a big LVM volume spanning all my drives and the UPnP server works. I've got Samba and SSHFS mounts working.

However, whenever I do any large file transfers over ethernet the system will suddenly decide it doesn't want to play with ethernet any more. It will just stop, whether it's streaming or copying, until I hit a key on the server keyboard. It's not related to power saving functions because it doesn't happen at a consistent time. The server runs absolutely fine until I start copying or streaming large files, then it starts to choke and needs me to hit "enter" on the server (which is annoying because it is in another room, which is the point of a media server) with increasing frequency.

Googling makes me think that it's related to the ethernet card itself, and other people have fixed the problem with a driver update. 

modinfo via_rhine gives me my existing driver information here:
```
filename:       /lib/modules/2.6.38-10-generic-pae/kernel/drivers/net/via-rhine.ko
license:        GPL
description:    VIA Rhine PCI Fast Ethernet driver
author:         Donald Becker <becker@scyld.com>
srcversion:     10C91FD8F4DD73CFE48BB3C
alias:          pci:v00001106d00003053sv*sd*bc*sc*i*
alias:          pci:v00001106d00003106sv*sd*bc*sc*i*
alias:          pci:v00001106d00003065sv*sd*bc*sc*i*
alias:          pci:v00001106d00003043sv*sd*bc*sc*i*
depends:        
vermagic:       2.6.38-10-generic-pae SMP mod_unload modversions 686 
parm:           max_interrupt_work:VIA Rhine maximum events handled per interrupt (int)
parm:           debug:VIA Rhine debug level (0-7) (int)
parm:           rx_copybreak:VIA Rhine copy breakpoint for copy-only-tiny-frames (int)
parm:           avoid_D3:Avoid power state D3 (work-around for broken BIOSes) (bool)

```

After a lot of scraping around and looking at the chip number on the motherboard (VT6103), I think that this is the most recent driver for my device:

[http://www.viaarena.com/displaydrivers.aspx?PageID=1&OSID=60&CatID=3760&SubCatID=127](http://www.viaarena.com/displaydrivers.aspx?PageID=1&OSID=60&CatID=3760&SubCatID=127)

That page says it supports 10.04 but obviously I'm using 11.04. When I follow the compile instructions in the text file (bear in mind that this is the first time I have tried to install any sofware without using apt-get) I get the following pile of errors on "make install"

```
make -C /lib/modules/2.6.38-10-generic-pae/build SUBDIRS=/home/tmp/Rhine_5.20 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.38-10-generic-pae'
  CC [M]  /home/tmp/Rhine_5.20/rhine_main.o
/home/tmp/Rhine_5.20/rhine_main.c: In function ‘rhine_receive_frame’:
/home/tmp/Rhine_5.20/rhine_main.c:1308:24: warning: cast from pointer to integer of different size
/home/tmp/Rhine_5.20/rhine_main.c: In function ‘rhine_set_multi’:
/home/tmp/Rhine_5.20/rhine_main.c:1982:18: error: ‘struct net_device’ has no member named ‘mc_count’
/home/tmp/Rhine_5.20/rhine_main.c:1990:37: error: ‘struct net_device’ has no member named ‘mc_list’
/home/tmp/Rhine_5.20/rhine_main.c:1990:65: error: ‘struct net_device’ has no member named ‘mc_count’
/home/tmp/Rhine_5.20/rhine_main.c:1990:97: error: dereferencing pointer to incomplete type
/home/tmp/Rhine_5.20/rhine_main.c:1991:57: error: dereferencing pointer to incomplete type
/home/tmp/Rhine_5.20/rhine_main.c:1998:37: error: ‘struct net_device’ has no member named ‘mc_list’
/home/tmp/Rhine_5.20/rhine_main.c:1998:65: error: ‘struct net_device’ has no member named ‘mc_count’
/home/tmp/Rhine_5.20/rhine_main.c:1999:38: error: dereferencing pointer to incomplete type
/home/tmp/Rhine_5.20/rhine_main.c:2000:56: error: dereferencing pointer to incomplete type
make[2]: *** [/home/tmp/Rhine_5.20/rhine_main.o] Error 1
make[1]: *** [_module_/home/tmp/Rhine_5.20] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-10-generic-pae'
make: *** [default] Error 2
```

I'm now officially well beyond any level of expertise or being able to busk through this.

Does this look obviously fixable to someone who isn't a complete amateur at this stuff? Would I be better off sacking it in and spending a tenner on a cheap PCI Card that's not so old and incompatible? Am I barking up the wrong tree looking at the ethernet driver in the first place?

---

### Post by greenslade on 2011-07-25
Nobody?

---

### Post by greenslade on 2011-07-26
OK new information.

It's not just hitting a key that wakes it up. Sending a http request, i.e. to the webmin panel, also wakes it up.

Also, when it went to sleep just now, it took out the internet on my brother's laptop. But not to my laptop. He's Windows, I'm OSX, but we're both on wireless while the server is on ethernet.

Does this sound more like something people have seen before? Because it's got me stumped.

---

### Post by greenslade on 2011-07-27
OK I guess this is a problem that nobody has seen before.

I'm going to try and get a PCI ethernet card and see if that fixes it. Does anybody have a recommendation for a PCI ethernet card that "just works" with Natty? Google gives me lots of things for 10.04 but I'm justifiably wary at this stage.

---

