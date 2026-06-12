---
title: "kernel with PAE only 3GB of Ram"
date: 2008-02-20
forum: Installation &amp; Upgrades
---

### Post by amkirwan on 2008-02-20
I have both compiled my own kernel with CONFIG_HIGHMEM64G=y and I have also run the the server kernel and both only see 3GB of ram in the system. I am running a Dell Optiplex with a P4 3.8GHz that supports pae. The bios sees 4GB of ram and reports no problems with it. If I do a dmesg | grep HIGHMEM I get 2174MB HIGHMEM available on either kernel. I am not sure what the issue it is my understanding is that the system should be able to see the full 4GB of Ram with PAE enabled. I am currently running Gutsy.

---

### Post by njparton on 2008-02-20
Are you running the 32 or 64 bit version of gutsy?

---

### Post by amkirwan on 2008-02-20
32 bit version. That is why I compiled with PAE support which allows the 32bit kernel to access up to 64GB of ram. Also the server version has PAE support by default.

---

### Post by njparton on 2008-02-20
Do you have some hardware that's preventing you from running the 64 bit version?  That would seem the simplest solution to me.

Also, the amount of RAM shown by an OS will be the total amout of ram - any other memory in the system which isn't generally addressable such as the onboard RAM for the BIOS and most importantly video RAM which can be up to 1GB these days.  You have to take that into account.

---

### Post by amkirwan on 2008-02-20
Yes it is a P4 so I can only run 32bit. I have 4GB of ram installed so with PAE support it should show up.

---

### Post by njparton on 2008-02-21
Hmmm, I wasn't aware that P4's could only run 32 bit OS's.

---

### Post by andydread on 2008-05-19
NOT because hardware supports 64bit means that everyone should run 64bit.  
There are things that DO NOT work as smoothly with 64bit FLASH anyone?  along with all the other tweakings just to get things going.   Its ridiculous the notion that on cant apt-get install linux-image-bigmem like in Debian.  I need 32bit 4GB support.  And this arguement that you have to move to a 64bit os and deal with all the broken  things like flash and skype etc that come along with that is a farce.   When we build systems with 4GB or ram for a customer the last thing we want is for them to fiddle with apps that wont work out of the box.   The server kernel is not optimized for workstation workloads and will not even run Compiz.   What a mess this is.  A terrible oversight.  Who makes these decisions anyway?

---

