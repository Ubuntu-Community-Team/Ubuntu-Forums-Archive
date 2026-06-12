---
title: "Intel® Core™ 2 Duo T7500 and ubuntu cd"
date: 2007-11-21
forum: Installation &amp; Upgrades
---

### Post by phil12 on 2007-11-21
Hi every1,
Gee, I got really stuck with my ubuntu installation. Just bought some laptop with Intel® Core&#8482; 2 Duo T7500 and I do not know what installtion c I should use. Already tried amd64, but it collapsed, ie. black screen. Then tried x86 (6.10). Actually tell me what installation cd I should use. Which one is proper?
Greetings
philY

---

### Post by Pumalite on 2007-11-21
Post brand and complete specs of laptop.

---

### Post by phil12 on 2007-11-21
It is compal, F90,
Intel core duo 2 T7500
nvidia 256 MB
harddisc - I do not know
some dvd drive, who knows what brand it is
philY

---

### Post by Pumalite on 2007-11-21
Memory?

---

### Post by phil12 on 2007-11-21
2048 MB
2,2GHz - processor

---

### Post by Pumalite on 2007-11-21
'ompal
	

F90*
	

* can be 0-9, A-Z or blank
	

19
	

Display - CRT
	

TCO 1999'

???

---

### Post by phil12 on 2007-11-21
Can't you just tell me what is proper installation cd for Intel® Core™ 2 Duo T7500. Forget the rest. Then I willnot have to try all the 64bit and x86... 
-----------
15,4 - screen

---

### Post by Pumalite on 2007-11-21
Do you have a laptop or a Desktop? What brand is it?

---

### Post by phil12 on 2007-11-21
It is a notebook with this Intel® Core™ 2 Duo T7500 2.2GHz. It is Compal, some taiwaneese-chinese **** brand...
And I got confused and do not know what installation cd I should use or what installation cd should be used for this specific processor.
Greetings
philY

---

### Post by Pumalite on 2007-11-21
'512MB NVIDA 8600GT GPU'

This means you are better off installing with the Alternate CD and configuring your xserver at the end.

---

### Post by phil12 on 2007-11-21
which one
PC (Intel x86) alternate install CD
64-bit PC (AMD64) alternate install CD
------
Greetings
philY

---

### Post by Pumalite on 2007-11-21
Either one, it's your choice. Make sure is the Alternate though. Install the new driver too.
[http://www.nvidia.com/object/linux_display_ia32_169.04.html](http://www.nvidia.com/object/linux_display_ia32_169.04.html)

---

### Post by bcn17 on 2007-11-22
you want the amd-64 because a core 2 duo is a 64 bit processor.

---

### Post by knock86 on 2007-11-22
use x86 version of 7.10
i have the same processor, ram, and graphic card...
> **bcn17 said:**
> you want the amd-64 because a core 2 duo is a 64 bit processor.
T7500 core duo IS NOT a 64 bit processors but a 32 bit with 64 bit emulation!!!

find here your next location where download:
[http://www.ubuntu.com/getubuntu/downloadmirrors](http://www.ubuntu.com/getubuntu/downloadmirrors)
and next chose desktop of x86 version...when you try to download the distro, something like this will be appear "[COLOR="Orange"]ubuntu-7.10-desktop-i386.iso[/COLOR]".
that's the right version for you, trust me (i've a laptop with the same characters: core duo T7500, 2GB ram, 160GB HD, Geforce 8400m G 256MB, bluethoot, wireless,ecc.)
and with 7.10 all work for me..
Remember to do the update and download the driver that ubuntu advising to you...

---

### Post by BrendaEM on 2008-01-13
> **knock86 said:**
> use x86 version of 7.10
i have the same processor, ram, and graphic card...

T7500 core duo IS NOT a 64 bit processors but a 32 bit with 64 bit emulation!!!

find here your next location where download:
[http://www.ubuntu.com/getubuntu/downloadmirrors](http://www.ubuntu.com/getubuntu/downloadmirrors)
and next chose desktop of x86 version...when you try to download the distro, something like this will be appear "[COLOR="Orange"]ubuntu-7.10-desktop-i386.iso[/COLOR]".
that's the right version for you, trust me (i've a laptop with the same characters: core duo T7500, 2GB ram, 160GB HD, Geforce 8400m G 256MB, bluethoot, wireless,ecc.)
and with 7.10 all work for me..
Remember to do the update and download the driver that ubuntu advising to you...

Can you show you reference your source of information. 

Intel seems to be of the idea that this processor IS 64-bit. If you have a differing reference please post it.
[http://www.intel.com/products/processor_number/chart/core2duo.htm](http://www.intel.com/products/processor_number/chart/core2duo.htm)

---

### Post by rvdavid on 2008-01-20
> **knock86 said:**
> use x86 version of 7.10
i have the same processor, ram, and graphic card...

T7500 core duo IS NOT a 64 bit processors but a 32 bit with 64 bit emulation!!!

find here your next location where download:
[http://www.ubuntu.com/getubuntu/downloadmirrors](http://www.ubuntu.com/getubuntu/downloadmirrors)
and next chose desktop of x86 version...when you try to download the distro, something like this will be appear "[COLOR="Orange"]ubuntu-7.10-desktop-i386.iso[/COLOR]".
that's the right version for you, trust me (i've a laptop with the same characters: core duo T7500, 2GB ram, 160GB HD, Geforce 8400m G 256MB, bluethoot, wireless,ecc.)
and with 7.10 all work for me..
Remember to do the update and download the driver that ubuntu advising to you...

Does this claim about T7500 Core Duo not being a 64 bit processor hold any water? 
Can anyone confirm that this claim is noise or signal? 

Tried having a look, but could not find any sources.

Thank you in advance.

---

### Post by derbouka on 2008-04-05
**This post could be related to an Ubuntu bug filed at**: ]https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/194187 [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hello!

Looking at specs from intel on [Intel® Core™2 Duo Processors]("http://developer.intel.com/products/processor/core2duo/index.htm") it says that this processor supports the "[Intel® 64 Architecture]("http://developer.intel.com/technology/architecture-silicon/intel64/index.htm")" which "*delivers 64-bit computing on server, workstation, desktop and mobile platforms when combined with supporting software*". Anyway in the [64-bit PC (AMD64) desktop CD]("http://releases.ubuntu.com/releases/8.04/") there says that this version is intended  "*to take full advantage of computers based on the AMD64 or EM64T architecture (e.g., Athlon64, Opteron, EM64T Xeon, Core 2)*". 
I thought that  [Intel® Extended Memory 64 Technology (Intel® EM64T)]("http://www.intel.com/technology/64bitextensions/index.htm") was to allow 64 bit processors to run 32 bit applications, but I couldn't confirm this this information because when I try to access to it's [page]("http://www.intel.com/technology/64bitextensions/index.htm"), I get the following warning "*The web page you are trying to access may not display properly with your current browser version. Before continuing, we recommend that you upgrade your browser to:*" ;)
Anyway I also have this processor and I can't also use 64 bit Ubuntu version...

Best regards

---

### Post by Namgyel on 2008-04-24
Will 8.04 be able to support it? I have Intel Core2 Duo T7500 2.2 GHz in MSI laptop but hadn't tried installing AMD64 version, the i386 version runs as it should.

---

### Post by derbouka on 2008-04-24
I haven't tried it yet, but it seams to work( at least "they" say it does, [https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/194187](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/194187) )
Download the livecd and try it out ;)

**Correction**
I've tested and at least the livecd is working

---

### Post by Namgyel on 2008-04-25
cool :D

---

### Post by chewearn on 2008-04-25
Intel Core2Duo is 64-bit processor.  I have been running it for more than 6 months on the amd64 platform; first using gutsy, now hardy.

My laptop is:
Dell Latitude D620
Intel Core2 T7200
nVidia Quadro NVS 110M/GeForce Go 7300

---

### Post by Namgyel on 2008-04-25
works on the 64 platform :) -thanks! but there are less programs on this platform... hope i'll find some answers soon :D

---

### Post by chewearn on 2008-04-25
> **Namgyel said:**
> works on the 64 platform :) -thanks! but there are less programs on this platform... hope i'll find some answers soon :D

What makes you say that?  I have not find any application that don't have 64-bit version, except sun-java plugin (which can be worked around).

If you have the time, read the sticky threads in this sub-forum to find out more:
[http://ubuntuforums.org/forumdisplay.php?f=343](http://ubuntuforums.org/forumdisplay.php?f=343)

---

### Post by Namgyel on 2008-04-26
and skype, video codecs (which are ment for 386 version automatically)... i have now i386 because I need ubuntu working asap - don't have time (for now) to search for alternatives...

---

### Post by chewearn on 2008-04-26
> **Namgyel said:**
> and skype, video codecs (which are ment for 386 version automatically)... i have now i386 because I need ubuntu working asap - don't have time (for now) to search for alternatives...

I have not encounter any video codecs limitation in 64-bit.  I'm not sure what you meant by video codecs are for 386 version automatically.

I don't personally use skype.  But, there are workaround to make it work:
[http://ubuntuforums.org/showthread.php?t=432295](http://ubuntuforums.org/showthread.php?t=432295)

If you visit the 64-bit subforum, there are tons of info.  Take a look at the sticky threads.
[http://ubuntuforums.org/forumdisplay.php?f=343](http://ubuntuforums.org/forumdisplay.php?f=343)

---

### Post by Namgyel on 2008-04-26
thanks :)! 

what i meant was when I tried installing codecs for let's say flash - ubuntu downloaded the torrents for 32 OS not 64 and tried to use it. since I'm new I don't really know yet how to work with these things :)

---

### Post by chewearn on 2008-04-26
> **Namgyel said:**
> thanks :)! 

what i meant was when I tried installing codecs for let's say flash - ubuntu downloaded the torrents for 32 OS not 64 and tried to use it. since I'm new I don't really know yet how to work with these things :)


First, just want to make clear that I'm not picking on you here.  If what I said offended you, I apologised.  However, I do want to make sure the correct information is presented, so as not to confuse people.

Now, I don't know how you got confused between flash codec and torrent.  You don't use torrent to download flash codec.  In ubuntu (it does not matter whether you have 32-bit or 64-bit), you install "flashplugin-nonfree" to install Adobe Flash.  You can use the "Add/Remove" application, or simply type the following in a terminal:
```
sudo apt-get install flashplugin-nonfree
```

You do the same for 32-bit and 64-bit.  The flash plugin is 32-bit, but this is transparent to the user because you use the same way to install.

As you can see, there is no torrent involved.  Not sure where you get that info.

---

