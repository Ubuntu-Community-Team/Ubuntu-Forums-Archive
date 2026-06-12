---
title: "How to switch from 2.6.35 to 2.6.35 pae?"
date: 2010-08-30
forum: Installation &amp; Upgrades
---

### Post by MadeTheSwitch on 2010-08-30
All,

I've tried looking for an answer, and I found a number that relate to the problem but do not address it directly. Because this is a kernel installation, I'm really nervous about trying stuff out and screwing myself out of a usable machine because I don't understand what I'm doing.

Basically, I am currently running Lucid with the 2.6.35 kernel. I would like to switch to the pae version to take advantage of all my RAM. 

If I try to install the pae kernel with the apt-get command, what gets updated is the old 2.6.32 kernel which still resides on the system, rather than the running 2.6.35 kernel. If I try to go into Synaptic to look for the various kernel packages, there's dozens of them and I don't know what to do, exactly. 

How do I switch my 2.6.35 kernel to pae? is there a neat command line I can use, or something like that? 

Thanks in advance, folks.

---

### Post by Frogs Hair on 2010-08-30
This may help in your quest . I know you must install the headers prior to the kernel.
[http://www.ubuntuupdates.org/packages/show/205478](http://www.ubuntuupdates.org/packages/show/205478)

---

### Post by MadeTheSwitch on 2010-08-30
Frogs Hair,

Thank you. I tried doing that, but when I type sudo apt-get install linux-generic-pae what I get is an update of the 2.6.32 kernel, rather than the 2.6.35 one. 

Is there any way to force this command to update the 2.6.35 one?

---

### Post by sgosnell on 2010-08-30
No real need for the headers, for most people.  I never bother.  If you're going to compile a custom kernel, you need them, but I don't do that.

Just find the kernel you want, as a .deb file, download and install it.  You don't need to use apt-get or synaptic, and they won't get the .35 kernel for you, because it's not in the repositories.  If the computer won't boot that kernel, just boot from a known good kernel.  You get a choice at boot time, and you can remove the bad kernel.  I prefer doing that with Synaptic, so that I can see what is being removed.

---

### Post by Bachstelze on 2010-08-30
Where dis you get your 2.6.35 from?

---

### Post by sgosnell on 2010-08-30
The standard 2.6.35 is available [here](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.35-maverick/).

---

### Post by Bachstelze on 2010-08-30
I know, but how do you know OP got it from there?

---

### Post by sgosnell on 2010-08-30
I don't.  The pae kernel isn't there.  In any case, neither apt-get nor synaptic will install from there, it has to be done manually.

---

### Post by MadeTheSwitch on 2010-08-30
To get 2.6.35, I followed the instructions here:

[http://theubuntunews.blogspot.com/2010/08/install-new-kernel-2635-on-ubuntu-1004.html](http://theubuntunews.blogspot.com/2010/08/install-new-kernel-2635-on-ubuntu-1004.html)

Worked flawlessly. But I can't figure out how to now go to pae.

---

### Post by Bachstelze on 2010-08-30
If you want PAE, install linux-image-2.6.35-19-generic-pae.

You can get a list of packages on the PPA at: [https://launchpad.net/~kernel-ppa/+archive/ppa/+packages](https://launchpad.net/~kernel-ppa/+archive/ppa/+packages)

---

### Post by MadeTheSwitch on 2010-08-30
> **Bachstelze said:**
> If you want PAE, install linux-image-2.6.35-19-generic-pae.

You can get a list of packages on the PPA at: [https://launchpad.net/~kernel-ppa/+archive/ppa/+packages](https://launchpad.net/~kernel-ppa/+archive/ppa/+packages)

Ah!

I was looking through the packages there and couldn't find the linux-generic-pae one... didn't realize I needed to grab the "image" one!

Thank you for that tip. I'll give it a shot and report back.

---

### Post by MadeTheSwitch on 2010-08-30
Probably a silly question, but... do I need to remove anything first? or will installing this basically move my system to the PAE version?

---

### Post by MadeTheSwitch on 2010-08-30
Bachstelze, this worked. Thank you so much! 

I now can see 3.8GB of RAM, as opposed to 2.9GB I saw before. Yay!

---

### Post by sgosnell on 2010-08-30
As you probably discovered, you don't need to remove anything.  You should get a menu at boot giving the option of all the kernels installed.  You can remove kernels if you want, or keep them, it's up to you.  I always keep at least one older dependable kernel installed, just in case something goes wrong with the one I'm using.

---

### Post by MadeTheSwitch on 2010-08-31
> **sgosnell said:**
> As you probably discovered, you don't need to remove anything.  You should get a menu at boot giving the option of all the kernels installed.  You can remove kernels if you want, or keep them, it's up to you.  I always keep at least one older dependable kernel installed, just in case something goes wrong with the one I'm using.

Yup, discovered that :) thank you. 

Will the system now update the new kernel?

Also, how do I clean all the old kernel packages from a particular kernel? right now by removing one all that goes away is the "image" package, but it leaves behind a bunch. Is there a way to say "please remove all kernel packages for this particular kernel"?

---

### Post by drs305 on 2010-08-31
The system won't update the kernel if it isn't listed in your 'subscribed' repositories. So unless you have installed a ppa or other repository containing the kernel, it won't be updated unless and until that kernel is incorporated into the main Ubuntu repositories.

Ubuntu-tweak is a great app for removing unwanted kernels. It should be included in the Ubuntu Software Center (Ubuntu Configuration Tool) or you can get it here:
[http://ubuntu-tweak.com/downloads/]("http://ubuntu-tweak.com/downloads/")

If you add it's ppa following the instructions on the page, you will get updates to ubuntu-tweak as they are released.

---

### Post by MadeTheSwitch on 2010-08-31
> **drs305 said:**
> The system won't update the kernel if it isn't listed in your 'subscribed' repositories. So unless you have installed a ppa or other repository containing the kernel, it won't be updated unless and until that kernel is incorporated into the main Ubuntu repositories.

Ubuntu-tweak is a great app for removing unwanted kernels. It should be included in the Ubuntu Software Center (Ubuntu Configuration Tool) or you can get it here:
[http://ubuntu-tweak.com/downloads/]("http://ubuntu-tweak.com/downloads/")

If you add it's ppa following the instructions on the page, you will get updates to ubuntu-tweak as they are released.

That's wonderful!

The funny thing is, I already HAVE Ubuntu-Tweak - I just never realized I could use it for this purpose. THANK YOU for pointing me in that direction.

---

### Post by malikkabanis on 2010-09-03
> **MadeTheSwitch said:**
> That's wonderful!
 
The funny thing is, I already HAVE Ubuntu-Tweak - I just never realized I could use it for this purpose. THANK YOU for pointing me in that direction.
 
i installed kernel 2.6.35-19 but i dont see it anywhere..
 
afterinstallin i restarted ubuntu and i show all old boot option no any changes were there.
 
is it because i recently added Ubuntu lucid 64 bit on my dell 1564.
and kernel i intalled on ubuntu lucid 32 bit normally i use 32 bit because all softwares are there and installed ubuntu just for fun..

---

