---
title: "No boot manager after installing Ubuntu on usb hard disk"
date: 2011-08-09
forum: Installation &amp; Upgrades
---

### Post by gshacte on 2011-08-09
From [http://www.ubuntu.com/download/ubuntu/windows-installer](http://www.ubuntu.com/download/ubuntu/windows-installer)

My OS is W7 on an Acer Laptop. 

I saved  wubi.exe to c:  and when running wubi, I pointed it to my usb hard drive for installation of ubuntu.   

When I rebooted my PC, I got a message that there was no boot manager. Even cntl-alt-delete did not work, so I unplugged the pwr cord and battery and reconnected them. I interrupted the boot to get to BIOS and found that Ubuntu was first in the boot chain. Apparently, when it is, no boot manager is found. So I removed the usb from the pc and was able to boot into W7.

Any suggestions about addressing this? 

Thanks much. 

Gerry Shacter

---

### Post by oldfred on 2011-08-10
Wubi uses the windows boot loader to boot. It only adds its entry to allow to you also boot it. You probably do not have a boot loader in the external device and that is why you get an error. BIOS should just be set to boot from internal hard drive first.

If you want to know exactly where everything is run this with external plugged in from the Ubuntu liveCD or from wubi.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

### Post by gshacte on 2011-08-10
Thanks muc for your reply. I thought that I was downloading a version of Ubuntu that would run under W7 without a virtual machine. I was not expecting to boot off Ubuntu, but its unclear to me how to get into Ubuntu and use it as a W7 user.

---

### Post by dino99 on 2011-08-10
ubuntu is not an app, its an OS, so you cant directly run it, you need a sandbox like wubi or better virtualbox

but the best choice is to make a real install:

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by gshacte on 2011-08-10
I think I found the issue. To run Ubuntu under Windows as a Windows app, ([ttp://www.ubuntu.com/download/ubuntu/windows-installer)]("http://www.ubuntu.com/download/ubuntu/windows-installer") I think I needed to have installed the version of Ubuntu I downloaded from the latter site into the same partition as Window's rather than onto the usb harddrive I put it on. 

I say this because after I got your previous note, I looked around a bit and found the followling:


[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

The above mentions that the Ubuntu install should be in the Window's partition.

---

### Post by bcbc on 2011-08-10
Nope, *oldfred* is right. You probably have your bios set to boot from the USB before the hard drive. You can install Wubi on any partition.

---

