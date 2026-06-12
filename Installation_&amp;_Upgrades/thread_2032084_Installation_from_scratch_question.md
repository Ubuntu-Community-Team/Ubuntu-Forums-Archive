---
title: "Installation from scratch question"
date: 2012-07-23
forum: Installation &amp; Upgrades
---

### Post by jbobman on 2012-07-23
Hi, I will soon be building a new pc, and I wanted to know if I can just pop a cd with ubuntu in right when it starts up and have ubuntu as the sole browser. Also, right now I only have macs, so would it even be possible to download ubuntu on a mac and then burn it to a cd for the new computer? Is there just one download for this? Finally, is ubuntu usable for someone who has never worked with linux in the past? Thank you!

---

### Post by darkod on 2012-07-23
Burning the cd from the iso on a Mac shouldn't be a problem. I'm only not sure if the Mac will try to do something funny with the bootloader on the cd.

Yes, you can simply boot the new computer with the cd and install. I recommend using the manual method, so you have best control of partition sizes, but it's up to you.

As for usage, I guess you shouldn't have any major problems. Of course, you will have to learn where some things are, but generally it's not a huge problem.

For the standard live cd (desktop image) there are two images, 32bit and 64bit.

Then there is the alternate cd image (both 32bit and 64bit also), which is used for raid or lvm installations, and in some cases when the live cd doesn't work. It installs the same desktop OS, just the installer is text based, not GUI.

---

### Post by mastablasta on 2012-07-23
> **jbobman said:**
> Hi, I will soon be building a new pc, and I wanted to know if I can just pop a cd with ubuntu in right when it starts up and have ubuntu as the sole browser.!
yes, but ubuntu is not browser but an operating system (like windows or Mac OS)
 
> 
Also, right now I only have macs, so would it even be possible to download ubuntu on a mac and then burn it to a cd for the new computer? 

yes. you would burn it it same as any other image.
you can also use USB stick so it's faster and if you want to try another verison of the OS you can simply delete the USB and put a new live image on it (to do that use this tool: [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)).
 
> 
Is there just one download for this? 

What do you mean? Ubuntu has a couple of downloads availabe in each version of the os (12.04 being current)
Ubutnu 32 bit (for the old 32bit CPU)
Ubuntu 64bit (for new CPUs)
Ubuntu Server (for servers)
Ubuntu Alternate disk (for text based install - good for older mashcines or for those with graphics issues)
Ubutnu Minimal (base install and then you install other things from internet - for advanced users).
 
There are also other desktp versions such as Kubuntu, Xubutnu, Lubuntu. Do a search on them and check out how they look like and their differences.
> 
Finally, is ubuntu usable for someone who has never worked with linux in the past? 
 
Preety much. most of configuration is done wthrough GUI or is autoconfigured.
I am using Kubuntu as it looks more like windows and is has plenty option via GUI. I also use Xubuntu on another maschine as it's easy to configure and uses less resources then other desktop environments.

---

### Post by jbobman on 2012-07-23
Ok thanks. I didnt mean browser, sorry, it was 3:10 AM. What i meant by the one version is that can i download any one ubuntu/xbunutu etc. os onto a cd on my mac and then be able to use it on a pc, i.e. the versions of ubuntu dont differ from mac to pc?

---

### Post by mastablasta on 2012-07-23
if mac has intel based CPU then no. they are then the same as for PC.
you are after desktop versions (probably AMD64 image if you have newer 64bit hardware).
 
i think there is another image for ARM processors (ment for tablets, smartphones and some barebones mini computers)

---

