---
title: "lubuntu 11.10 installer hangs while installing it on ibm thinkpad t21"
date: 2019-09-13
forum: Installation &amp; Upgrades
---

### Post by mg7134 on 2019-09-13
Hi people

i have an old IBM thinkpad t21 computer with 512 mb of ram and 10gb of hdd. I want to install lubuntu 11.10 because it is the last version of lubuntu to support s3 savage xi graphics and infrared port. When i made the usb and started installing it via usb, it showed up the installation screen but when i clicked install lubuntu without trying, the installer just hangs. Do anyone know how to fix this problem. (FYI i am new to Linux)

Thanks & Regards

---

### Post by guiverc on 2019-09-13
Lubuntu 11.10 was the 2011-October release of Lubuntu, it came with 15 month of supported life, which is now well since gone.  I wouldn't suggest using it online!

Did you verify your download of the ISO?  ([https://tutorials.ubuntu.com/tutorial/tutorial-how-to-verify-ubuntu#0](https://tutorials.ubuntu.com/tutorial/tutorial-how-to-verify-ubuntu#0))  then use the 'check disc for defects' option to verify your write-to-install-media (which I'm guessing is a cdr?).  The option I mean can be seen on the first picture of [https://manual.lubuntu.me/1/1.3/installation.html](https://manual.lubuntu.me/1/1.3/installation.html)  (current Lubuntu manual)[IMG]https://manual.lubuntu.me/_images/boot_installer.png[/IMG]
*ps: your screen will differ from this; I stole this screen from current manual*

The most common reason for what you describe in my experience is a bad download, or bad write to install-media, so it's where I'd check.  It's not the only problem (graphics can be next) - but squashfs errors are what first come to mind with your issue.

If you can't verify the media on that box; use another box to verify media as being perfect.

---

### Post by pcfan1234 on 2019-09-13
Why don't you try 18.04, maybe with xforcevesa and nomodeset?

Older versions aren't supported anymore.

---

### Post by mg7134 on 2019-09-13
I also tried using iso of lubuntu version 18.04 but it says " Peter Al Elvin" with some other words and a blinking "_" and just hangs at that moment.

I also have a video about this 
[file:///C:/Users/Maharshi/Downloads/WhatsApp%20Video%202019-09-12%20at%206.16.12%20PM.mp4](file:///C:/Users/Maharshi/Downloads/WhatsApp%20Video%202019-09-12%20at%206.16.12%20PM.mp4)

The link doesn't work

---

### Post by guiverc on 2019-09-14
I don't know your t21; but I do recall newer kernels having trouble with intel pentium M's that gave false information about their [cpu] specs.  This problem started mid-late in the 11.04 life-cycle as I recall and it took some time before it was finally discovered to be bugs in the intel processors & intel provided fixes...  This could be your issue. 

*[COLOR=#333333][FONT=Ubuntu]A number of older [/FONT][/COLOR][Pentium M]("http://en.wikipedia.org/wiki/List_of_Intel_Pentium_M_microprocessors")[COLOR=#333333][FONT=Ubuntu] processors produced around 2003-4 (the Banias family) do not display the PAE flag, and hence a normal installation fails. However, these processors are in fact able to run the latest (and PAE-demanding) kernels if only the installation process is modified a little. The problem is not missing PAE, it's about the processor not displaying its full capabilities.[/FONT][/COLOR]*

[https://help.ubuntu.com/community/PAE](https://help.ubuntu.com/community/PAE)

I forget what *Ubuntu version booted without issue on these pentium M's  (ie. intel providing a fix in the kernel for the pentium M flaws), but I do suspect Lubuntu 16.04 LTS installed without issue on my thinkpad t42, though with it now running Lubuntu 18.04 LTS I can't look.

You've posted a local link (local to what I'm guessing is a windows machine) - you need to upload it to the web if you wish for anyone here to see it.

The "Peter El Alvin" sounds to me like a bad download, or bad write to install media. Did you `check-disc-for-defects` (though if you can't get this to run, most likely it was a bad download or write to media, the writing to media can be harder for people not familiar with doing it).

---

### Post by deadflowr on 2019-09-14
> **mg7134 said:**
> I also tried using iso of lubuntu version 18.04 but it says " Peter Al Elvin" with some other words and a blinking "_" and just hangs at that moment.

I also have a video about this 
[file:///C:/Users/Maharshi/Downloads/WhatsApp%20Video%202019-09-12%20at%206.16.12%20PM.mp4](file:///C:/Users/Maharshi/Downloads/WhatsApp%20Video%202019-09-12%20at%206.16.12%20PM.mp4)

The link doesn't work

It's not a link to a web server.
It's a link to a file in your computer.
So no one has access to it.
You need to upload the video to some video sharing service (like youtube).
Sometimes in some instances you can upload the file as an attachment.
But in this case, I do not think mp4 files are valid attachment types.

FWIW, Peter Alvin is the developer of the isolinux boot loader program that's used to load the cd image.
It's copyrighted under his name.


All that said, you might want to look for another distro,
as none of Ubuntu's current releases are light enough to run on that system anymore.
(that includes the Ubuntu flavors such as Lubuntu)

---

### Post by mörgæs on 2019-09-15
The Thinkpad T21 has a Pentium 3 processor so PAE is not a problem here. 

In my signature is a selection of advice for old hardware but still your Thinkpad might be too old. 

If you want to try Lubuntu then begin with a minimal install and add a GUI later. Getting stuck at the Peter Alvin name means that the install is stuck, not that anything is wrong in the ISO.

Other options are Tiny Core and Bodhi Linux.

---

### Post by mg7134 on 2019-09-15
This is the working video link

[https://vimeo.com/360135523#](https://vimeo.com/360135523#)

For the OS version i used lubunt 11.04

---

### Post by mg7134 on 2019-09-15
Plus, i am chainloading from prop boot manager

---

