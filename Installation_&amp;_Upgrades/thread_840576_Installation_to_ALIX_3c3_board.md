---
title: "Installation to ALIX 3c3 board"
date: 2008-06-25
forum: Installation &amp; Upgrades
---

### Post by rklauco on 2008-06-25
Hi, everyone.
I am trying to install ubuntu server edition on alix board, model 3c3.
The board does have a video module.
Everything works just fine.
But, the system should be able to operate with no screen attached.
And here is the problem - something, not sure what, causes ubuntu to stop, when there is no screen. During the boot I end up with message Starting up... and that's about it.
I tried Voyage linux, it is debian based, too, works just fine - it is able to boot and operate even without display attached. But it is missing some packages I need.
I am unable to find out, where to start the investigation.
Is it a different kernel configuration? Does it have something with initrd image?
Please, help...

---

### Post by vplata on 2008-07-01
I'm trying to install on an Alix board also, but mine has no display support, so I'm stucked in the Starting up... message, now I know is because of the display.
Please let me know if you find a solution
Thanks

---

### Post by rklauco on 2008-07-02
Well, finaly, I downloaded the [Voyage linux]("http://www.voyage.hk"), installed and set apt sources to local debian mirror for my country.
Since than everything works smooth and nice, so I did not investigate the initrd any further (I should, but I have too much work).
The only thing on Voyage that is not very good is the fact, that since I have the 3C3 board, the led drivers are not working - it will for yours, as it have different bios.
The Voyage installation is pretty simple, you will need just to download the latest version (5.1), get a CF reader to your standard workstation, answer few questions and that's about it.
Let me know if you need some assistance.

---

### Post by cgl72 on 2008-07-29
rlauco
Could you give us more details about how well your system is working? Have you stuck with Voyage, did you install ubuntu or xubuntu after all? Did you install a windows manager?

I am thinking of buying the Alix 1C and using the Vesa mounts on my monitor, but before ordering wanted to know how it went with you.

Thanks.

Christian

---

### Post by rklauco on 2008-07-29
Actualy I moved from Voyage to debian and set up the filesystem as read only. I did not test any Xserver/window managers, so I can't give you some good advice, but I can test it again and let you know. It will take me a day or two.

---

### Post by alfonso78 on 2008-08-20
Hi,

I'm thinking to buy an alix 3c3 also.

Can I ask you how did you practically start installation given there is no CD reader? Do you need an external usb cd reader, or is there a way around it?

Thank you.

Cheers,

alfonso

---

### Post by christofu on 2008-10-31
> **vplata said:**
> I'm trying to install on an Alix board also, but mine has no display support, so I'm stucked in the Starting up... message, now I know is because of the display.
Please let me know if you find a solution
Thanks

Get a paperclip and carefully insert into the VGA header plug, shorting pin 6 to pin 12 (middle row far right to bottom row 2nd from the right). Whenever you don't have a monitor attached leave the paperclip in. Your Alix 3c3 will now boot up without a monitor attached.


Chris.

---

### Post by christofu on 2008-10-31
> **alfonso78 said:**
> Hi,

I'm thinking to buy an alix 3c3 also.

Can I ask you how did you practically start installation given there is no CD reader? Do you need an external usb cd reader, or is there a way around it?


Yes. Use an external USB CDROM or even a USB flash drive with the image installed.

The Alix 3c3 uses the Award BIOS, so enter setup as soon as the system powers on and select the appropriate boot devices from the BIOS advanced settings menu.

---

### Post by alfonso78 on 2008-10-31
> **christofu said:**
> Yes. Use an external USB CDROM or even a USB flash drive with the image installed.

The Alix 3c3 uses the Award BIOS, so enter setup as soon as the system powers on and select the appropriate boot devices from the BIOS advanced settings menu.

I don't have any external usb cd drive, and as far as I know alix does not boot from usb flash (I tried). Not sure about usb cdrom...

I tried with several ubuntu flavours (also alternate) but never worked for me (I got alix3d3).

I ended up installing voyage linux. It's meant for this boxes  (so the file system is read only, for example) and it's a real breeze to install.

alfonso

---

### Post by christofu on 2008-10-31
> **alfonso78 said:**
> I don't have any external usb cd drive, and as far as I know alix does not boot from usb flash (I tried). Not sure about usb cdrom...

I tried with several ubuntu flavours (also alternate) but never worked for me (I got alix3d3).

I ended up installing voyage linux. It's meant for this boxes  (so the file system is read only, for example) and it's a real breeze to install.



Did you update your boot sequence in the Award BIOS? By default the sequence only includes booting from hard drive (the compact flash card, in this case). I change our sequence to 1. Removable media, 2. CDROM then 3. Hard drive.

We've had great success with the 3c3 and most recently with the 3d2 (we didn't need the VGA support).

---

### Post by alfonso78 on 2008-11-01
> **christofu said:**
> Did you update your boot sequence in the Award BIOS? By default the sequence only includes booting from hard drive (the compact flash card, in this case). I change our sequence to 1. Removable media, 2. CDROM then 3. Hard drive.

We've had great success with the 3c3 and most recently with the 3d2 (we didn't need the VGA support).


Hi, 

thank you.

Yes, I tried to change booting sequence in the bios.
Can you explain which success do you mean? Booting from USB CD or USB flash drive?

I tried ubuntu-8.04.1-desktop-i386.iso and xubuntu-8.04.1-alternate-i386.iso using PXE (network boot) to install, but the kernel never booted. It was always stuck at "Starting up..." right after GRUB. Interesting enough, memtest run just fine.

Then I found a post somewhere saying ubuntu kernel was not supported and I gave up.

Anyway, I think voyage is really simpler, plus the read-only file system is very important for the CF.

alfonso

---

### Post by DefineByte on 2008-11-01
Ubuntu should work but you need to recompile the kernel with 'CONFIG_FIRMWARE_EDID=n'.

Without that it will still boot up but you will have to wait a while.

---

### Post by alfonso78 on 2008-11-01
> **DefineByte said:**
> Ubuntu should work but you need to recompile the kernel with 'CONFIG_FIRMWARE_EDID=n'.

Without that it will still boot up but you will have to wait a while.

Hi,

thank you! :)

How long it's "a while"? I think I was waiting more than two minutes and nothing showed up on the screen after "Starting up"...

Is there a way to recompile the ubuntu kernel on a standard pc and then use it to install on the alix?

Let me change question:

what would be the fastest way to get the alix up and running with ubuntu since I can't boot it with pxe?

thanks a lot!

alfonso

---

### Post by DefineByte on 2008-11-01
By a while I mean 15-30 minutes.

The quickest way is to follow [this post](http://ubuntuforums.org/showpost.php?p=6076430&postcount=7) in this very thread and then install it as is. :)

---

### Post by surfer on 2008-11-01
hi!

the paperclip works perfectly! thanks a lot.

did anyone try to compile a kernel with the 'CONFIG_FIRMWARE_EDID=n' option?

---

### Post by servedgreen on 2008-11-12
I have not tried booting without a monitor, but I have had luck installing full xubuntu and the command line ubuntu install from the alternate CD.  I used an IDE CD attached to the Alix 1c board for the initial install, then moved the CF card to to the 3c3 machine.  Booting was relatively fast and no kernel changes were necessary.  This was done for 8.04....  Neat boards!  3.8W idle.

---

### Post by DefineByte on 2008-11-12
> **surfer said:**
> did anyone try to compile a kernel with the 'CONFIG_FIRMWARE_EDID=n' option?
I've tried and it works as expected, i.e. no wait at boot-up. :)

The only problem I'm having now is with MFGPT timers failing to initialise at boot but I'm putting that down to a dodgy IDE cable disabling DMA (although I have no real clue if that's relevant, for all I know I turned something off/on in the kernel config I shouldn't have).
edit: Turns out it's a problem with the AwardBIOS on the 1C so I guess I'm stuck with it. Ah well. :)

---

### Post by Bottlegreen Elderflower on 2008-11-21
Ok, I have a new 3D3 board. It has been very frustrating for me.  So far I can get imedia linux, fedora and mandriva running ok on it, but not much else.  I have tried ubuntu,xubuntu 8.04 and xubuntu 8.10 either from a usb CD rom drive or by installing them on a different machine over CF adapter.  I have even tried to install windows XP lite and Vista to no avail.  The problem occurs in the same place for every try.  It boots, reads the CD or the OS on the CF card says its loading and then hangs.  I get a little blinky cursor in the corner indefinitely.  I haven't waited an hour for boot yet but that is kind of unreasonable.  I have a monitor attatched so it should work with out a paper clip.  I have no clue how to rebuild a kernel.  I don't have another similar system to start with like 1C.  How functional is xubuntu on the alix 3 series anyway, do you have X running, is it slow, what are you doing with it?  I was thinking about flying this on a balloon payload to do data aquisition, is that reasonable?  Too many questions I know.  Thanks.

Josh.

---

### Post by DefineByte on 2008-11-22
It could be that the VGA cable you're using doesn't support DDC (pin 12, I think). I have a Belkin cable that has the wire disconnected so I got the same hang with a monitor attached.

[This](http://ubuntuforums.org/showthread.php?t=311158) should take you through what's required to build a custom kernel on a debian-based system, if you have one at hand (you don't really need to be root though, you can run it in /home and use fakeroot :)).

---

### Post by Bottlegreen Elderflower on 2008-11-22
Well I actually got XPLite to load after setting the bios to optimal and changing the boot order.  But xubuntu still hangs in the same spot.  I will check my VGA cable.  The tutorial you linked tells how to build a new kernel, and uses the same options of the old kernel, I am wondering how to rebuild your existing kernel with different options such as stated here [http://ubuntuforums.org/showthread.php?p=6079774#post6079774?](http://ubuntuforums.org/showthread.php?p=6079774#post6079774?)  If its the same way where do I change/add this option? BTW XPLite that have runs pretty quick I am quite impressed, but that won't stop me from trying to install xubuntu.  Thanks

Josh.

---

### Post by Bottlegreen Elderflower on 2008-11-22
Ok, the paper clip thing worked, so its the VGA cable or monitor, but I will eventually need the system to run with out a monitor, which still means a kernel recompile.

---

### Post by DefineByte on 2008-11-23
To get the source for your existing kernel you'd run```
apt-get build-dep linux-image-$(uname -r)
apt-get source linux-image-$(uname -r)
```then follow the tutorial from that point on (I must admit I couldn't personally get Ubuntu's kernel to build).

It does take you through how to change the configuration. You use```
make menuconfig
``` or ```
make xconfig
``` to make any changes you want (xconfig is probably slightly easier to use). :)

Of course there are alternative tutorials out there such as [this](http://blog.avirtualhome.com/2008/10/28/how-to-compile-a-custom-kernel-for-ubuntu-intrepid/). There's slightly more faffing around setting up the config with that one though.

---

### Post by Bottlegreen Elderflower on 2008-11-23
Ok, great, thanks so much, I will be trying this soon. I used Virtual Box on my Windows pc to install to a CF card successfully, very handy.  I also inserted a very fine wire between pins 6 and 12 so that I would not have to disconnect the VGA cable during boot up, to stick a jumper in.  This worked, but I still want to recompile the kernel.  As soon as some on unplugs the VGA cable I'll have to replace or fix the wire.  I noticed xubuntu uses very nearly 100% of the proc almost all the time, it was getting very noticably warm.  I hadn't looked at the power usage, but I can do that later.  I am guessing there is a way to strip down the system to use minimal CPU, but then again I was running the GUI.  Thanks.

Josh.

---

### Post by DefineByte on 2009-03-18
Just thought I'd mention the presence of a beta BIOS on the [PC Engines site](http://www.pcengines.ch/) which is supposed to fix the VGA boot problem.

I haven't tried it myself, so if anyone does I'd be interested in the results.

---

### Post by feh on 2009-04-08
Has anybody exercised the video capability of these boards? Are they capable of higher resolutions (ie. 1280x720), or is 640x480 or 800x600 the practical limit?

Thanks.

---

### Post by nephish on 2009-05-21
OK, the last date of a post in this topic is a while back. Anyone manage to get debian or ubuntu on one of these ALIIX 3D3 boards? And if so, how?

thanks

---

### Post by DataMatrix on 2009-06-04
> **nephish said:**
> OK, the last date of a post in this topic is a while back. Anyone manage to get debian or ubuntu on one of these ALIIX 3D3 boards? And if so, how?

thanks
Yes, I've got Lenny (debian) to work with the 3D3, but only with a monitor attached. Otherwise it hangs after "Starting up..." and "Detecting EDD". As the PAPERCLIP approach seems too risky for me I am now trying to recompile the kernel. If it doesn't work I'll make a few phonecalls and see if someone knows how to trick the hardware into thinking that there is a monitor (I've heard that I'll need a 75 Omh resistor from the RGB pins to ground, but that sounds too much like "BRICK ALIX" and I'll try that as a last resort)
I'll write if I find something. Oh, and I've installed the debian with the debootstrap program, it's in jaunty's repositories. I made a grub-install from a chroot-ed shell (keep in mind that you need to tell it to install the bootloader on /dev/sdb or /dev/sdc, else you'll blow up your own computer's boot)
This might be helpful: [http://debian-on-alix.blogspot.com/](http://debian-on-alix.blogspot.com/)

---

### Post by DefineByte on 2009-06-04
Install [this](http://www.pcengines.ch/file/alixbio7.zip) beta firmware and the hang should be fixed.

---

### Post by DataMatrix on 2009-06-04
I've recompiled the kernel (2.6.29.4) and now everything works smooth.
See my post here: [http://blog.datamatrix-bg.net/?p=80](http://blog.datamatrix-bg.net/?p=80) , there I have posted the .config file and also the generated .deb package. 

> **DefineByte said:**
> Install [this](http://www.pcengines.ch/file/alixbio7.zip) beta firmware and the hang should be fixed.
About that - there are alix0.bin and alix2.bin in there, which one?

PS: As it's running just fine with the recompiled kernel I have no intention in patching the bios (If it works, don't fix it :P )

---

### Post by DefineByte on 2009-06-04
I'd guess one was for the ALIX 1x and the other for the 3d3. You should'nt really have to worry about that though because sb.com will pick the right one for your board.

You would get HPET support too, so if you need that it might be worth it. Probably safer to do what you did though. :)

---

### Post by DataMatrix on 2009-06-04
I've posted another article on my blog - a how-to on how to install debian from an archive file I made from my installation: [http://blog.datamatrix-bg.net/?p=95](http://blog.datamatrix-bg.net/?p=95)

---

### Post by binary_dreamer on 2009-08-24
I got alix 3d3 and i would like to ask if it is possible to have a 1.8'' or 2.5'' hard disk instead of the compact flash by making use of cf to ide 2.5'' adapter
any ideas?

---

### Post by ab5602 on 2009-11-02
> **nephish said:**
> OK, the last date of a post in this topic is a while back. Anyone manage to get debian or ubuntu on one of these ALIIX 3D3 boards? And if so, how?

thanks

Here is an article I wrote about getting the Alix 3D1 to boot Ubuntu using the serial port and PXE:

[http://sun3.org/archives/158]("http://sun3.org/archives/158")

---

### Post by trunet on 2010-05-06
I summarized the commands to install ubuntu lucid lynx in an alix 2d13 using debootstrap in a blog post: [http://www.wsartori.com/blog/2010/5/3/how-install-ubuntu-lucid-lynx-alix-board/]("http://www.wsartori.com/blog/2010/5/3/how-install-ubuntu-lucid-lynx-alix-board/")

Wagner Sartori Junior

---

### Post by skrite on 2010-05-06
great write up. Did you have the issue with this board taking forever to boot up?

---

### Post by ppatrick on 2011-07-16
give Jeoss a try, it PXE installs directly on the CF controlled by a remote serial or SSH console.
[http://www.vercot.com/~jeoss/](http://www.vercot.com/~jeoss/)

---

