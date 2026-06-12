---
title: "New build, can't boot Ubuntu 13.10 LiveCD or Live USB to install- UEFI problems?"
date: 2014-01-24
forum: Installation &amp; Upgrades
---

### Post by Jacob_Chang on 2014-01-24
I just completed a new build...everything apparently is going well  except for the small little issue of not being able to get my favorite OS--Ubuntu--loaded up on it.:)

I downloaded the Ubuntu 13.10 .iso and used Unetbootin to create a Live USB. I then boot from it to proceed with the install, where I can get to the Unetbootin menu. I choose "Install Ubuntu" or "Try Ubuntu without installing", where my machine hangs at a BusyBox shell prompt. At that point, I have to do a hard reset. The keyboard freezes.

To rule out a bad image being written to the flash drive or a bad download, I try another computer where it comes up to the installer or the live desktop.

 I try burning an .iso of the Ubuntu 13.10 image and try to boot from that DVD, it doesn't work. Same thing. But, it works on another machine.

Here's what I have...

[LIST]
[*]AMD A8-5500 quad core APU 
[*]MSI FM2-A75MA-E35 system board -- Uses UEFI but does have the option for "Legacy" 
[*]8 GB DDR3 (2x 4GB) RAM 
[*]1TB Western Digital SATA HDD 
[*]Asus SATA DVD-RW 
[*]an .iso of Ubuntu 13.04 x64, on both a flash drive *and* a DVD-R, that WILL NOT work with my new build. 
[/LIST]

Here's what I've done...
[LIST]
[*]I've tried booting from both UEFI and "Legacy" (where I suppose it emulates BIOS since UEFI and BIOS are two different things), nothing. Black screen with a BusyBox prompt. 
[*]I've tried booting a flash drive *and* a DVD disc, no dice. Both worked fine on another UEFI machine.
[*]I've made sure that Windows 8-specific optimizations were disabled, no luck.
[*]I've tried IDE mode and AHCI mode (and I want to use AHCI), nothing.
[*]I've reset the firmware settings to the defaults, no luck. 
[/LIST]

I can install (and use) Windows 7, which I've resorted to for the time being for this particular machine, so I can stress test. I've installed to a UEFI-based machine before (with Secure Boot at that) and never had an issue. Am I missing something? Is something incompatible, like the motherboard? Can anyone help me? I don't use Windows as my daily driver, I use it in Vbox for Active Directory/sysadmin labs and simulations and the rare instance that I need to use a Windows app.


Any help would be appreciated...I would love to get Ubuntu up and running on this:P

---

### Post by sudodus on 2014-01-25
Welcome to the Ubuntu Forums :-)

Apparently it boots (to the Unetbootin menu). Could it be a problem with the graphics?

- Please specify the graphics chip/card

- You can try some boot options. Start with ***nomodeset*** and ***text*** (text will boot into a text screen, but at least you will be able to run text commands and for example install proprietary drivers for your graphics card.

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by Jacob_Chang on 2014-01-25
Thank you. I've been here before, but I forgot my login details and the email that I had associated with it. It's been a while since I last logged in, so I'm not really new...the last time was probably when I was just entering the 11th grade. I'm now in my 2nd year of university.

As for the graphics, they are integrated onto the processor (APU). As far as I know, AMD's A-series/Radeon has good compatibility with Linux (at least enough to get a driver downloaded if there's any issues). I don't play video games or do graphic design, so the integrated Radeon graphics on my A8-5500 will be more than enough for just a rig to virtualize different OSes, which is what it is mainly used for.

---

### Post by sudodus on 2014-01-25
Yes, many Radeon graphics chips work well with the built in drivers, but there are also chips that don't work unless you use ***boot options***. So I really recommend that you try that (and ***nomodeset*** is a good starter). There could be other issues too, that might be fixed with other boot options.

---

### Post by Jacob_Chang on 2014-01-25
I've tried your advice with using the boot options (nomodeset and text), unfortunately, it isn't working. I'm wondering if I downgrade to 12.04 LTS if I would have any issue or not.

When I chose my motherboard and APU, both were compatible (according to the reviews). As for being specifically compatible with 13.10, I'm not sure.

My APU, which is an A8-5500 with Radeon HD 7560D built-in, doesn't appear to have any outstanding issues (or an issue like this one) according a quick Google search...

---

### Post by sudodus on 2014-01-25
If the mobo and APU are brand new, chances and better with a new version. You might even try with the one being developed now, Trusty Tahr, to become 14.04 LTS in April. But if you have a good internet connection, you can download and test several versions.

You can also try other boot options, acpi, noapic, nolapic

---

### Post by Jacob_Chang on 2014-01-25
So, I downloaded 12.04 and wrote the iso to a USB drive via Unetbootin, and I can successfully boot to an installer or to the live session without inputting any commands. It works just as it should. I was able to load 12.04 x64 without a problem.

I wonder why 13.10 was proving to be a problem on my machine? I'm thinking that because it is a non-LTS version, something specific was lacking. Hopefully 14.04 will not have this issue. Because of the nature of the problem, with the bootloader hanging at a Busybox prompt, I cannot get any information as to why it's happening. I cannot do anything with the keyboard at that point, I have to phyiscally reset the machine.

Should I try out 14.04, just to see if I can boot the installer on this machine (I don't want to *use* alpha-stage software...just download the iso to see if 14.04 will have an issue...)? I mean, it's in alpha stage, what works now may not in the RTM version (and vice-versa). Downloading a ton of .iso files isn't a problem, I have a 250GB data cap, it's just that I've come upon the unexpected and I really don't have the time.

---

### Post by sudodus on 2014-01-26
I'm glad 12.04 LTS works for you :-)

I suggest that you download and test the daily build of Trusty, and help us develop it to really good distro. Chances are that you can make it work better with your hardware, if you find bugs now.

[http://iso.qa.ubuntu.com/](http://iso.qa.ubuntu.com/)

But use 12.04 LTS as your production platform!

---

### Post by Jacob_Chang on 2014-01-27
I've just realized that the version I'm intending on using, which is the standard Ubuntu desktop w/ Unity, isn't even released in its alpha stages and will only be released in beta. I suppose that the other versions (Xubuntu, Lubuntu, etc...) may or may not be an accurate indicator if the standard (Unity) 14.04 version will even work or not. I'll try anyways with Xubuntu and report back...

---

### Post by sudodus on 2014-01-28
Good luck! It will be interesting to read your report after trying Trusty :-)

---

### Post by frank18 on 2014-01-28
Hi guys it happens to me too but with  1404 64bit, i can boot it on to try it , it runs ok except the screen is too large and it doesn't let me fit it in the screen with lower resolution,besides that i can run it in try mode, but when i boot to install it it hangs past the logo with just Unity coulor screen checking the system.

---

### Post by vicshrike on 2014-01-30
Here is the solution to boot problem with live usb;

[https://bugs.launchpad.net/ubuntu/+source/casper/+bug/1241589](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/1241589)

---

### Post by sudodus on 2014-01-31
There are a lot of posts in that bug report. Which one has the solution for you?

---

