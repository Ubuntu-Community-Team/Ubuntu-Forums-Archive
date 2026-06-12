---
title: "Kernel Update to 13.10 and now no video"
date: 2013-12-25
forum: Installation &amp; Upgrades
---

### Post by charles_osborne on 2013-12-25
I am setting up a server to use at home as a production server to write php programs and more. I am wanting to make it wireless so that I can move where I want to and be able to still use the server. I also am wanting to set it up to emulate a web server so that I can test programs before release and work out as many bugs as possible.

So far I have installed Ubuntu Server twice and both times I have lost the video card after trying to update the kernel. All I get is a black screen when I reboot. I am trying to update the kernel to 3.12 so that the wireless usb card will work. I have been following the directions at [http://askubuntu.com/questions/386777/lafalink-lf-d10-wlan-driver-install#](http://askubuntu.com/questions/386777/lafalink-lf-d10-wlan-driver-install#) to get this done.

I am new to Ubuntu so when telling me to do something I would appreciate it if you gave me instructions for every little detail.

Is there any way to recover from this or am I going to have to wipe my drive and start over? Is there any way to get a download of Ubuntu 13.1 that has the kernel already updated and I do not have to do it myself and lose the video card again? I am manually updating the files using terminal.

---

### Post by oldfred on 2013-12-25
What video do you have?

I thought servers just worked in terminal mode, or did you also install a gui?

You may have to hold shift key down from BIOS to get grub menu.

       How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

