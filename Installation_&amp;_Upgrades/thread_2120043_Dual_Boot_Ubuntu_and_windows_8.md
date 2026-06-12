---
title: "Dual Boot Ubuntu and windows 8"
date: 2013-02-25
forum: Installation &amp; Upgrades
---

### Post by GageP on 2013-02-25
Hi everyone,

First time poster, but I have been using Ubuntu for awhile. I just recently installed Ubuntu on my new Thinkpad X230. I installed Ubuntu after i had already installed and configured Windows 8. So i was hoping for a dual boot situation. Now normally what happens here with windows 7 at least is i install Ubuntu and then have to recover my windows. 

but this time... Windows 8 works perfectly fine. But Ubuntu will not load. Grub is my default boot-loader though. In a grub menu(with the pink background and everything). I can choose between the standard Ubuntu or windows 8 to boot from. 

But only choosing windows 8 works. If i choose Ubuntu it just gets a flashing cursor at the top right and nothing happens. 

I'm not really sure where to go from here. Ubuntu works fine in live mode off my USB. 

To be clear i installed Windows 8 first and kept a second partiton for ubuntu. And then later installed Ubuntu on that second partition. Windows 8 works but not Ubuntu. Grub is my boot loader though.

Thanks in advance for everything! ):P

---

### Post by arpanaut on 2013-02-25
Follow this guide and create a BootInfo Summary and post the url to the forum.
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

There is a lot of good info that will enable the help you need.

---

### Post by GageP on 2013-02-25
Hello!

First off, thank you very much for replying. I just ran the boot repair tool. And the url i got was

[http://paste.ubuntu.com/5565995/](http://paste.ubuntu.com/5565995/)

I was just curious what would happen if i run the Recommended repair? I think that would be interesting to try out. But i figured i would follow your directions first!

I would also like to add that I did attempt to reinstall ubuntu because i thought maybe something went corrupt during installation. I ran into the same problem.

This is 12.04.02 LTS 64 bit version.

Thank you very much

-Gage

---

### Post by grahammechanical on 2013-02-25
>  If i choose Ubuntu it just gets a flashing cursor at the top right and nothing happens. 

Perhaps you are assuming that the issue is with Grub. As you say, normally it is Windows that fails to load. The recommended repair is to install Grub into partition sda5 where Ubuntu is. It may work. But I (who is not an expert) cannot see anything wrong.

Grub is in the MBR of /dev/sda. It looks for /boot/grub on msdo5, which is Grub's way of saying sda5. Which is exactly where it should be. and they are there. This is the info for sda5

>   Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

By the way. Ignore all stuff for sdb. That is the live session that you are running Boot Repair from.

The Grub configuration file knows where Windows is

> set root='(hd0,msdos1)'

It also knows where Ubuntu is

> set root='(hd0,msdos5)'

msdos1 = sda1, msdos5 = sda5. Get it? May I make a couple of suggestions?

1) At the Grub menu select Ubuntu and Press E. That stops the countdown timer and puts you into Grub edit mode. In the boot parameters find this line

> linux	/boot/vmlinuz-3.5.0-23-generic root=UUID=4ec647b3-9a3c-43d3-b90b-0ae57e4865bf ro   quiet splash $vt_handoff

And change it to

> linux	/boot/vmlinuz-3.5.0-23-generic root=UUID=4ec647b3-9a3c-43d3-b90b-0ae57e4865bf ro  $vt_handoff

By removing quiet splash you will see messages as you boot. F10 will boot. Those messages will help in know what is happening.

2) At the Grub menu select Recovery Mode. At the Recovery Mode menu select Resume. That will boot without a proprietary video driver. I am wondering if what you are seeing is a video driver issue.

I may be barking up the wrong tree here, but if it gets you to a desktop run Additional Drivers and experiment with another driver.

regards.

---

### Post by GageP on 2013-02-25
> **grahammechanical said:**
> 

2) At the Grub menu select Recovery Mode. At the Recovery Mode menu select Resume. That will boot without a proprietary video driver. I am wondering if what you are seeing is a video driver issue.

I may be barking up the wrong tree here, but if it gets you to a desktop run Additional Drivers and experiment with another driver.

regards.

I appreciate your advice! I will look into doing that. i'm going to wait also and see if anyone else has any input. Because i feel like its not a driver issue because I'm running Ubuntu in livemode perfectly. 

Thanks again for taking your time out to help!:)

---

### Post by oldfred on 2013-02-25
If you have nVidia then you may need nomodeset. Some systems also need other boot parameters. By removing splash quiet you may see what fails as it is posting the loading process. If often stops at battery something, but it is in the issues just before that.

Same procedure as grahammechanical has already posted, but include nomodeset in place of splash quiet.

Screen shots for liveCD or first boot after install until proprietary driver is installed.

       How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

You can just add nomodeset.

       Boot-Repair --> Advanced options --> GRUB options tab --> tick "Add kernel option: nomodeset" --> Apply

---

### Post by GageP on 2013-03-04
I have tried everything you guys have suggested been working and goofing with this for the last 8 days at my cabin. Been a real unpleaseent experience. 

I even went as far as to wipe my whole computer and just try to boot ubuntu. Still to no avail i get the same errors. I even have problems gettng the boot repair to download when in live mode, keeps locking up. 

Sorry for my frustration, but this is starting to bug me a little bit. I really like Ubuntu, but this stuff just makes it really difficult.

Thanks and any input is appreciated

---

### Post by oldfred on 2013-03-04
What video does you system have. nomodeset works for many but not all. If you have Optimus you need to turn one or the other off to get it to boot. Then add bumblebee.

---

### Post by GageP on 2013-03-04
I'm using a thinkpad X230. It has a intel HD 4000 part of my ivy bridge processor. 

I would like to ask one more question, although a system works fine in livemode, after installation there can be other problems? What is live mode not utilizing that changes when it boots from installation?

And following the basic let ubuntu set up my partitions is a good idea right? I hve stopped goofing around with partitions thinking that the intsaller would get it right..

Thanks!

---

### Post by oldfred on 2013-03-05
I always partition myself, but I want more than just / (root) and swap which is all you get with auto install. For newer users I suggest /home and a shared NTFS data partition if dual booting with Windows. Also the auto install with just / often creates a huge system partition. It actually works better with a 25GB / and data in other partition(s). I usually did the same with Windows in making a smaller system partition and separate data, but Windows defaults a lot to c: so it has to be a lot larger.

I thought nomodeset reverted to the default video, but do not know details. LiveCD and install include 30 or 40 video drivers. But there is only one Intel open source driver that supposedly just works.
You can try to newer Intel setting.
  Older Intel video card: i915.modeset=1 or i915.modeset=0 
newer:  i915.i915_enable_rc6=1

Some have to set exact size, change example 1280x1024 to your screen size.

 Force Intel Video mode as boot parameter in grub menu
video=1280x1024-24@60
and if that doesn't work you can try
video=VGA-1:1280x1024-24@60

this may not now be valid:
Limited resolutions with Intel Sandybridge graphics
[http://ubuntuforums.org/showthread.php?t=2057807](http://ubuntuforums.org/showthread.php?t=2057807)
With 11.04:SandyBridge
[http://ubuntuforums.org/showthread.php?t=1817374](http://ubuntuforums.org/showthread.php?t=1817374)
acpi_osi=linux pci=noacpi

For Intel graphics running slow:
sudo apt-get install mesa-utils
glxinfo | grep OpenGL | head -n3

---

