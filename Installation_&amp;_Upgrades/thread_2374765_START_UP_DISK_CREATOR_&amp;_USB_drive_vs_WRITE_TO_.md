---
title: "START UP DISK CREATOR &amp; USB drive vs WRITE TO DISK &amp; DVD for Iso Images"
date: 2017-10-18
forum: Installation &amp; Upgrades
---

### Post by mark bower on 2017-10-18
When I use Start Up Disk Creator to write the iso image to the USB drive, the booted USB does not behave like the DVDs I burn.  Specifically, it is not an install USB drive; it is only a live session of Ubuntu.  In other words, I would like to get the outcome of the following link:

[https://www.howtogeek.com/howto/linux/create-a-bootable-ubuntu-usb-flash-drive-the-easy-way/](https://www.howtogeek.com/howto/linux/create-a-bootable-ubuntu-usb-flash-drive-the-easy-way/)

What I read re Start Up Disk Creator is that after writing the iso image to the USB drive, booting the drive would behave just like the burned DVD as per link above; it doesn't.  I also tried the "dd" cmd line function with similar results, live session only, not install capability.

So what GUI and/or how will get me to a USB drive that behaves just like a DVD install disk?

Note:
I am doing this on Ubuntu 17.04 using "ubuntu-14.04.05-desktop-i386.iso", 8gb SanDisk.  The ISO file is good since verified using a DVD.

---

### Post by C.S.Cameron on 2017-10-19
mkusb will make an install disk, either Live or Persistent: [https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

---

### Post by mark bower on 2017-10-19
I used the following which I understood to be a sub-function of mkusb: sudo dd if=./ubuntu.iso of=/dev/rdiskN bs=1m

Tomorrow I will attempt the GUI version of mkusb itself - optimistic after your comment.
Thanks

---

### Post by mark bower on 2017-10-19
I employed mkusb to write the iso to the USB, trying both the "L", "C" options.  Neither produced a USB that boots with options to either "Try Ubuntu" or "Install Ubuntu" to the HD.  (The L & C options did boot Ubuntu for a live session).  

So help still needed: I need to boot and install Ubuntu from a USB drive.

---

### Post by sudodus on 2017-10-19
This is strange. Both the Ubuntu Startup Disk Creator and mkusb are **cloning tools** (except when you use mkusb to create a persistent live drive). And cloning tools copy the content of the iso files as it is (every byte is copied, there is no editing, no conversion). This means that there should be the same menu when booting from a DVD and from a USB pendrive, you should get the options 'Try Ubuntu', 'Install Ubuntu' etc.

Something must be very wrong, when this happens. Maybe some function of the tools that are used by the Ubuntu Startup Disk Creator and mkusb under the hood is failing. Maybe dd itself or some low level tool writing to the USB drive or some electronics in the computer or the USB pendrive itself is glitchy or failing.

I suggest that you try the same procedure in another computer and/or with another USB pendrive. See also this link, particularlly the section about Analysis.

[Answer at AskUbuntu - Analysis of the problem](https://askubuntu.com/questions/144852/cant-format-my-usb-drive-i-have-already-tried-with-mkdosfs-and-gparted/933035#933035)

You can try according to this list,

> 
-    On some pendrives and on many memory cards there is a small mechanical switch for write protection, that can toggle between read/write and read-only. You might have set it read-only without intention.

-    Reboot the computer and try again to restore or wipe the first megabyte with mkusb.

-    Disconnect other USB devices. Sometimes USB devices can disturb the function for each other.

-    Try other USB ports and another computer.

-    Try another operating system (Windows, MacOS) in another computer.

-    If you still cannot wipe the first megabyte of the drive, and the drive is read-only, it is probably 'gridlocked', and the next stage is that it will be completely 'bricked'. There is a limit, when you have to accept that the pendrive is damaged beyond repair, at least with tools available to normal users like you and me.


---

### Post by mark bower on 2017-10-19
o.k.  Good to know that mkusb should do what I want!  Incidentally, the boot screen off the USB has the Gnome screen, and a foot print with 3 dots under it.  I have forgotten, but I guess 14.4 Ubuntu was still Gnome default.  While the appearance seems normal, the drop down menus freeze.  So there is even a problem with a clean Ubuntu being booted.  I tried the USB drive on another computer, 64 bit vs the 32 bit I am using for this process, and that computer would not recognize the inserted USB, although the USB could be seen with lsusb.

So I will try installing the .iso on the USB drive with mkusb on my 64bit PC.

---

### Post by grahammechanical on 2017-10-19
> but I guess 14.4 Ubuntu was still Gnome default.

No. As far as I remember Unity became default on Ubuntu as far back a 11.10. Mind you, Ubuntu 17.10 now defaults to Gnome 3 shell. I know it is possible to install Unity 7 but I do not think that it is part of a default install of Ubuntu 17.10.

Perhaps you are installing Ubuntu Gnome 14.04. The downloaded ISO images of Ubuntu and the flavours are confusingly all called "Ubuntu." That may have changed recently. I have not tested that.

Regards.

---

### Post by sudodus on 2017-10-19
> **grahammechanical said:**
> No. As far as I remember Unity became default on Ubuntu as far back a 11.10. Mind you, Ubuntu 17.10 now defaults to Gnome 3 shell. I know it is possible to install Unity 7 but I do not think that it is part of a default install of Ubuntu 17.10.

Perhaps you are installing Ubuntu Gnome 14.04. The downloaded ISO images of Ubuntu and the flavours are confusingly all called "Ubuntu." That may have changed recently. I have not tested that.

Regards.

+1 (I agree)

---

### Post by mark bower on 2017-10-19
mkusb works for me.  Thank you C.S.Cameron and sudodus who got me started on the right track by suggesting I try a different computer.

In short, the problem seems solely due to not making the USB the 1st boot device in the BIOS in the process of booting it.  In the long of it, I was fooled on the computer for which I first asked for help; I did nothing with the BIOS and the grub menu displayed a 2nd HD with 14.04 on it (installed with a DVD), which I assumed was from the USB boot.  I selected and booted it, and that put me into Ubuntu 14.04 - of course.  After messing on another computer which did not display the USB flavor, I was forced to make the USB the 1st boot device in the BIOS.  mkusb then worked, and when I returned to the original computer and did the same,ie make the USB drive the 1st boot device, mkusb worked as desired - Try and Install options available.  What a folly on my part and neither of you would have suspected such a mistake.

Question:  I used mkusb in both the &#8220;C&#8221; (cloning iso file,[compressed] image file or device) & &#8220;L&#8221;(&#8216;Live-only&#8217; or installer from iso file) modes, and both write to the USB drive so that Try and Install are available upon boot.  Which should I be using, C or L, and why?

And yes, you are both correct.  Where I declared I had the Gnome Classic desktop was true, but only a result of my having installed Gnome in place of Unity.  That is, 14.04 was/is Unity until modified.  I have always resorted to Gnome Classic as my preference.

---

### Post by C.S.Cameron on 2017-10-19
Command line to install Ubuntu is:

```
ubiquity
```

---

### Post by mark bower on 2017-10-19
under what circumstances would I use ubiquity?

---

### Post by sudodus on 2017-10-20
> **mark bower said:**
> Question:  I used mkusb in both the “C” (cloning iso file,[compressed] image file or device) & “L”(‘Live-only’ or installer from iso file) modes, and both write to the USB drive so that Try and Install are available upon boot.  Which should I be using, C or L, and why?


The C and L options in mkusb are equivalent, they do the same. One describes the method, the other the result. The cloning method creates a live-only USB drive.

---

### Post by sudodus on 2017-10-20
> **mark bower said:**
> under what circumstances would I use ubiquity?

When you want to make a full installation, install Ubuntu into an internal drive or into another external drive. Ubiquity is the name of the installer, that is behind the desktop icon "Install Ubuntu 16.04.1 LTS", "Install Ubuntu 17.10" (or whatever version you intend to install).

---

### Post by C.S.Cameron on 2017-10-20
Right, if you can't find the install icon on the Live desktop, open terminal and type "ubiquity". It should start the installation process.

---

### Post by mark bower on 2017-10-20
o.k. Thank you both again.

@ sudodus - However, and not to be picky, I do not quite understand the C vs L choices. You say C and L are "equivalent", which is what I thought I verified by trying both and booting with each of them: Both produce a USB installation drive.  But then you follow that comment with  "The cloning method creates a live-only USB drive" which is the C option ("cloning iso file,[compressed] . . .), which seems to contradict that C works to produce an install USB drive? 

(Please note, I am not trying to beat this to death.  I am a literal thinker and want to make my notes for future use of mkusb as succinct as reasonable.  IE, I would prefer to narrow the C,L choices to just one that is "proper")

And, I have not said it before, but mksub is so nice and easy to use.  Much easier than burning the iso image to DVD.  In fact, I now will be able to drop the use of DVDs and DVD drives from my two computers.

---

### Post by sudodus on 2017-10-20
@mark bower,

I would recommend that you use the L option (Live-only); use the option that feels natural for you to use.

[hr][/hr]
An iso file is a synthetic and not compressed image file, created from data in a development environment. Cloning such a file is what *you* were doing, and it created a live-only system. But this is a special case.

An image file can be created as an image of a real system (but also from data in a development environment), often using cloning with **dd** or some similar tool.

Image files in general often have the extension .img (and compressed image files can have the extensions .img.gz and .img.xz) depending on the compression method. Compressed images can be images of anything, a drive with only data, a drive with a live or persistent live system or an installed system. [Operating systems for Raspberry Pi](https://www.raspberrypi.org/downloads/) are often distributed as compressed image files (and they are installed systems, not live systems). There are other examples of compressed image files [here](https://help.ubuntu.com/community/mkusb/persistent#Compressed_image_file_with_a_persistent_live_system).

[hr][/hr]
Can you formulate a detailed suggestion how to change the wording in the menu with C and L?

I am reading your feedback about mkusb carefully and considering it (but cannot promise to use it, because I have to consider what other people think and want too). Anyway, thank you for the feedback :-)

---

### Post by mark bower on 2017-10-20
@sudodus

Well, what you said is a bit over my head, however, I would offer the option below re mkusb.
But first, I always think of the term &#8220;XXX install disk&#8221; as as disk which will install an OS to the HD, eg, Windows 7 install disk.  A 2011 Ubuntu book I have uses the term &#8220;install disk&#8221;.   And I think of a &#8220;live disk&#8221; as one which will place the OS into the computer memory.  Not meaning to be a pedant here, just to be sort of exact and simple in my thinking.  

So for my pea brain and to leave no doubt, I would suggest a mkusb choice where "disk" is substitued with "USB drive" as follows, where X is the letter choice 
 
	** &#8220;X"= create an OS install plus OS live USB drive from iso file**

Had I seen this choice, it would be the only one I would have tried.  Hope this makes sense and does not offend.  Again, I like the simplicity of mkusb.

---

### Post by sudodus on 2017-10-21
Thanks @mark bower :-)

---

