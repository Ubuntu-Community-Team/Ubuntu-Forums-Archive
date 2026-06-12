---
title: "Is a re-installation needed after hardware upgrade?"
date: 2013-01-07
forum: Installation &amp; Upgrades
---

### Post by SpudULike on 2013-01-07
Hi,
     I had a 12.10 system running on a:-

* Processor	2x Intel(R) Pentium(R) 4 CPU 3.40GHz
* Memory	2060MB 

but I have now updated the hardware, swapped out the motherboard, processor, and memory so I now have:-

* Processor	6x AMD FX(tm)-6200 Six-Core Processor
* Memory	8269MB

The machine still boots from the existing installation, once I found it on my sprawling collection of hard dives and got the boot order established.

Is it necessary to do a new installation to take full advantage of the new hardware?  I would prefer not to do a complete install, but would much rather refresh the current.  How would I do this?

---

### Post by Bufeu on 2013-01-07
No, I don't think so.  Linux should handle new hardware quite well. Just be sure that you download and install the latest drivers for your graphic card and CPU (use Jockey, a.k.a. "Additional drivers").

---

### Post by grahammechanical on 2013-01-07
You can run the command

```
sudo lshw -html > hardwareprofile.html
```

That will create a document called hardwareprofile.html. It will open in a web browser and it should list all the hardware. See, if it matches the specification given in the motherboard user guide and what you know of the hardware.

Regards.

---

### Post by darkod on 2013-01-07
I agree. There is no need to "refresh" anything. If it works, it works.

I don't remember right now whether the AMD FX has integrated graphics like the AMD A series, but i think it doesn't. If you are using the same video card you did before, no need to do anything about the video drivers too.

If the CPU has integrated graphics that you started using now, you might need to activate the fglrx driver for AMD/ATI in Additional drivers.

Apart from that, nothing. In effect you only changed the CPU which doesn't involve much. Enjoy your faster ubuntu. :)

---

### Post by oldfred on 2013-01-07
Because your old system only had 2GB did you have the 32bit version? While the 32bit versions now include PAE so it will see your 8GB of RAM, you really need the 64 bit version for that to be fully utilized.

       [http://ubuntuforums.org/showthread.php?t=2028717](http://ubuntuforums.org/showthread.php?t=2028717)
Ubuntu 12.10: 32-bit vs. 64-bit Linux Performance
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_1210_3264&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_1210_3264&num=1)
Assuming your hardware is x86_64 capable (basically any modern Intel/AMD CPU) and have at least 2GB of RAM, you really should be running the 64-bit version.
Essentially says if you can use the 64bit kernel you should.April 2011
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_natty_pae64&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_natty_pae64&num=1)
[https://help.ubuntu.com/community/32bit_and_64bit](https://help.ubuntu.com/community/32bit_and_64bit)
Ubuntu 32-bit, 32-bit PAE, 64-bit Kernel Benchmarks Dec 2009
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1)
Linus does not like PAE or 32 bit.
[http://cl4ssic4l.wordpress.com/2011/05/24/linus-torvalds-about-pae/](http://cl4ssic4l.wordpress.com/2011/05/24/linus-torvalds-about-pae/)
    
You do have to do a new install to convert from 32bit to 64 bit. If separate /home it is easier or fully backup /home. Also export list of installed apps to make it easier to reinstall.

---

### Post by gordintoronto on 2013-01-07
With PAE, a single program can not use more than 4 GB of memory. There are very few programs which want that much memory, so switching to a 64-bit version should be low priority -- unless you plan to do large video-editing projects.

If you change video cards, that can trigger a re-install, CPUs not so much. (Even the video card should be OK if you remove any Additional Driver *before* you make the change.)

---

