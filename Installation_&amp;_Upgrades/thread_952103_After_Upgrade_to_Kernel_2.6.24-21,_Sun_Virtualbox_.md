---
title: "After Upgrade to Kernel 2.6.24-21, Sun Virtualbox Broke [FIXED]"
date: 2008-10-18
forum: Installation &amp; Upgrades
---

### Post by SuperMike on 2008-10-18
I have Ubuntu 8.04 and I guess I ended up last night upgrading when prompted so that I'm on 8.04.1? Anyway, it moved me from Kernel version 2.6.24-19 to 2.6.24-21. And when it did, everything was working except Sun Virtualbox. It was telling me that the kernel driver for it wouldn't load. And when I launched Sun Virtualbox and looked at the error message, it told me what to do. Well, that fix worked, so I wanted to share it with you. The command it recommended was:

$ sudo /etc/init.d/vboxdrv setup
$ sudo shutdown -r now

On reboot, it loaded just fine and Sun VirtualBox works great again.

Thanks to Sun for making that easy, and for Ubuntu and Debian for making a great operating system.

---

### Post by NewNerd99 on 2008-10-21
Mike,
still getting the same old msg as per the old thread


VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel, e.g. virtualbox-ose-modules-generic..
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

---

### Post by SuperMike on 2008-10-22
> **NewNerd99 said:**
> Mike,
still getting the same old msg as per the old thread


VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel, e.g. virtualbox-ose-modules-generic..
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

You need to uninstall the one from Ubuntu and go get the Sun version. That's what I did. However, it broke after a kernel update and I had to do what I posted at the top of this thread to fix it.

---

### Post by NewNerd99 on 2008-10-24
Thanks Mike,
   Uninstalled the Ubuntu version and downloaded the Sun package. this is the error I get now. Hopefully moving forward....

---

### Post by SuperMike on 2008-10-24
> **NewNerd99 said:**
> Thanks Mike,
   Uninstalled the Ubuntu version and downloaded the Sun package. this is the error I get now. Hopefully moving forward....

Ah, you may have uninstalled virtualbox, but may not have done the following. First, uninstall Sun Virtualbox again. Then, do this:

$ sudo apt-get --purge remove virtualbox-ose-modules-generic
$ sudo shutdown -r now  # yes, this will reboot your computer

On reboot, you should be clean with no vbox drivers loading in your kernel. Now go forth and install the Sun Virtualbox again and reboot. That should fix you.

BTW, perhaps a reboot might be necessary on any of this, but since it involves the kernel instead of user space, it seems to me to be your safest bet. If I'm wrong on that, well, I'm wrong.

---

### Post by NewNerd99 on 2008-10-26
Ok new error. I have attached the screen shot of the error window on the install package.

Also on the boot up screen it says I have

three kernels: 16, 19 and 21?

Do I need to be removing any of these?

Cheers
Chris

---

### Post by SuperMike on 2008-10-27
Are you trying to run that deb as a normal user or as root? I think you'll need to run as root. So, you could go to command line, 'cd' to that directory, and do:

$ sudo dpkg -i vir*.deb

I'm surprised you're having so much trouble. I didn't have much trouble at all. I just knew that you have to do an apt-get --purge remove <whatever> of everything dealing with vbox and virtualbox before you can install the Sun version. And an apt-cache search "virtualb" can suggest to you some package names that should probably be purged before installing the Sun version. I then did:

$ sudo su
# 

And went to town as root to install the Sun deb file. It's been wonderful ever since. BTW, Microsoft is giving away a free trial of Windows 2008 Server that lasts for like 280 days (but you have to follow the renewal instructions), so I've been using that.

As for the other kernels, actually, you want to keep a couple of those there until you are certain things are stable. If not, then what people normally do is to boot back to the previous kernel and file a bug report, then wait to see if a patch is issued or something. Then, flip to that new kernel. And you might not know the kernel is bad until 3 kernel revisions down and you activate a rarely used app that may have fault with a kernel revision starting 2 revisions back. So, it's good to keep earlier kernels. They don't consume that much space.

Eventually, however, yeah -- you'll want to Google on how to remove old kernels. But by then, it's probably time to reinstall or upgrade to a new version of Ubuntu. In fact, we're about to hit that point again.

---

### Post by alexcckll on 2008-10-27
Umm - not really how it should be done ideally, though.. is it?  Best practice would have Release Candidate updates... with all the bugs being trapped by kernel testers before being released into the wild - I'm trying to get this Brainstorm looked at...

[http://brainstorm.ubuntu.com/idea/14802/](http://brainstorm.ubuntu.com/idea/14802/)

---

### Post by alexcckll on 2008-10-27
Umm - not really how it should be done ideally, though.. is it?  Best practice would have Release Candidate updates... with all the bugs being trapped by kernel testers before being released into the wild - I'm trying to get this Brainstorm looked at...

[http://brainstorm.ubuntu.com/idea/14802/](http://brainstorm.ubuntu.com/idea/14802/)

---

### Post by SuperMike on 2008-10-29
> **alexcckll said:**
> Umm - not really how it should be done ideally, though.. is it?  Best practice would have Release Candidate updates... with all the bugs being trapped by kernel testers before being released into the wild - I'm trying to get this Brainstorm looked at...

[http://brainstorm.ubuntu.com/idea/14802/](http://brainstorm.ubuntu.com/idea/14802/)


???

---

### Post by alexcckll on 2008-10-29
Wanna join us on this thread - [http://ubuntuforums.org/showthread.php?t=948584&page=1](http://ubuntuforums.org/showthread.php?t=948584&page=1) ?

I was referring to a better release model...

-Proposed (development), release to -PreRelease, test the butt off it by people who choose to do acceptance testing.. ensure it's bulletproof... THEN release to Production (-update or -security).

Y'know... where you have a lot more trusting USERS out there in the wild...

A lot of people are EXTREMELY annoyed with the kernel bods at the mo...

Care ot join us?  We're trying to get the developers to see the full scope of the problem.

---

### Post by NewNerd99 on 2008-10-29
I cant work it out....

If I cd to the directory above it (misc) and ls it says there is no 'vboxdrv.ko' in that directory yet I still get the same error msg that it is trying to overwrite it.

Thanks for staying on the thread, I'm away from the PC with work quite frequently but should be here for the remainder of the week

....and I am certainly gaining confidence in using the terminal!!!

---

### Post by NewNerd99 on 2008-10-31
Mike?

---

### Post by SuperMike on 2008-11-01
> **NewNerd99 said:**
> Mike?

Whoa, dude. This is messed. If it were me in this bad of shape, I would be copying everything off onto a portable USB hard drive, and all my .hidden files out of /home/<me> (if you understand what I'm even talking about), backing up my web bookmarks and email, writing down the names of apps I have installed beyond the basic install, and then formatting down to 0 and starting all over again, but this time, using the Sun Virtualbox version instead of the one from Ubuntu. That is, unless they fixed it in the latest Ubuntu. But the Ubuntu I have now, 8.04, it only worked with the Sun Virtualbox.

The good news on this, at least, is that Ubuntu installs super fast on these new PCs and laptops. I upgraded from a P4 to a brand new AMD64 laptop with 1GB of RAM and my Ubuntu install went by super fast.

However, this decision must be performed with a lot of planning and care so that you can get all your stuff back and all your mail and settings back.

---

### Post by NewNerd99 on 2008-11-02
Yea roger that...may be the quickest way out!

Thanks for the info thus far

Chris

---

### Post by alexberi on 2008-11-29
Cannot start my VirtualBox since last updates.
On Friday put latest ubuntu updates for AMD 64bits. Version now is for:
- kernel 2.6.24-22-generic
- VirtualBox 2.6.24-21-generic

Since Friday I cannot start my Virtual Machine, I receive:
VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel, e.g. virtualbox-ose-modules-generic..
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}
=======================================================

I tried to get latest virtualbox version:
aberindei@abeubu64:~$ sudo apt-get install virtualbox-ose-modules-2.6.24-22-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package virtualbox-ose-modules-2.6.24-24-generic
aberindei@abeubu64:~$ sudo apt-get install virtualbox-ose-modules-2.6.24-21-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
virtualbox-ose-modules-2.6.24-21-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by SuperMike on 2008-11-29
[QUOTE=alexberi;6277374]Cannot start my VirtualBox since last updates./QUOTE]

Oh shoot. Let's hope not! I haven't reboot my computer yet after the updates.

---

### Post by lpanebr on 2008-11-30
hi,

I'm having the same issue. It is also already registered at launchpad:
[https://bugs.launchpad.net/ubuntu/+source/virtualbox-ose-modules/+bug/303199](https://bugs.launchpad.net/ubuntu/+source/virtualbox-ose-modules/+bug/303199)

From what I read there it happens because the specific module VBox-OSE uses is not rebuild automatically and that is why it breaks until some next update.

Apparently the non-free version of VBox (Fuel) does not have this issue.

It also seems that the new ubuntu release Intrepid solves that issue. 

Also Angel Sanchez says that booting and choosing your previous kernel enables you to revert to the state where Vbox works. (I never did this but will try in a while and get back here to tell you)

Luciano

---

### Post by lpanebr on 2008-11-30
Yes, it works.

Just reboot and choose the .21 kernel (NOT the recovery one)

I am not sure if the next boot will let me choose the new kernel but thats not problem I guess, will wait for the vbox module to be out anyway.

luck to all!

---

### Post by SuperMike on 2008-12-07
> **lpanebr said:**
> Yes, it works.

Just reboot and choose the .21 kernel (NOT the recovery one)

I am not sure if the next boot will let me choose the new kernel but thats not problem I guess, will wait for the vbox module to be out anyway.

luck to all!

I didn't have any problem. I'm on the 8.04.1 distro with 22 generic kernel. I followed the instructions that started this thread back on the 21 generic kernel, which, again, were:

$ sudo /etc/init.d/vboxdrv setup
$ sudo shutdown -r now

On reboot, it loaded just fine and Sun VirtualBox works great again.

I didn't have to do this on the 22 generic kernel because I had done them back on the 21 generic kernel.

And again, I'm on the Sun Virtualbox, not the one that ships with my 8.04 distro.

---

