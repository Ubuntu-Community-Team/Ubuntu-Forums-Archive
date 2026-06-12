---
title: "ATI onboard graphic driver"
date: 2010-03-06
forum: Installation &amp; Upgrades
---

### Post by Cariboo1938 on 2010-03-06
Mystery...
I upgraded my hardware with a GA-MA785GMT mother board which has the ATI785 graphic chip on board. I don't have to install an additional video card for my daily work on an old CRT monitor!
During installation from the Ubuntu 8.04 LTS remastered Life CD, done on my previous GA-K8NS Ultra-939 hardware, I was happy with the onboard graphic which was likely 1024x728 resolution.
After the installation was done and the system was restarted, the screen was a mess - green instead of black, blue not red and so on - and I had to change /etc/X11/xorg.conf to a failsafe version with only 800x600 resolution. 
Why is the video driver, running during installation, not working after the system is installed?
:popcorn:

---

### Post by zvacet on 2010-03-08
Did you tried to install driver from system<admin<hardware drivers?I use ATI Radeon HD 3200 and it have better support in Jaunty or Karmic then in Hardy.You can always download driver from ATI site.

---

### Post by Cariboo1938 on 2010-03-09
The issue is that I wonder ...
why is there a  graphic driver on the Live CD... ( I would be happy with this one until I install an additional video card)... which is not running properly after installation of the system (8.04) to hard drive?:?:


PS.: I tried to use xorg.conf from the Live CD in the final installation but it's not working properly:?::?:

---

### Post by Cariboo1938 on 2010-03-10
Hello...Has any body an idea on this issue which I repeat here again?:?:

Facts: 
1) Hardware GIGABYTE MoBo GA-MA785GMT with on board graphic chip ATI785
2) Operating system Ubuntu 8.04 LTS on original Live CD

Issue: 
Why is the video driver, running with the Live CD and during installation, not working after the system is installed?:?::?:
or
How can I have the same graphic driver which runs on the Live CD after system installation to the hard drive? :?::?::?:

---

### Post by Cariboo1938 on 2010-03-12
Hello...Any ideas...?.....OR
Is the question not clear enough...?
:o:(:?:

---

### Post by Herman on 2010-03-13
:D Hello Cariboo1938
It's nice to see you here, remember the historic thread when we used Super Grub Disk to get your computer to boot so we could run grub-install, **[B][Xubuntu and XP Pro Dual Boot Problems]("http://swiss.ubuntuforums.org/showthread.php?t=229909") **[/B]?
That turned out to be a milestone for SGD and Super Grub Disk became well known and very popular after that, and I think more people had the confidence to install Ubuntu when they had Super Grub Disk.

I'm not familiar with the Ubuntu 8.04 LTS remastered Life CD, I'm guessing that's the kind of CD you make by following the instructions in this page, [LiveCDCustomization]("https://help.ubuntu.com/community/LiveCDCustomization") - Ubuntu Community Docs?

In any case, I think that most normal Live CDs use the vesa video driver.

You should be okay if you can enable the vesa video driver somehow I think.

Hardy Heron was the first version of Ubuntu to use the Xorg Xwindow system from the X.Org Foundation and we didn't need to run 'sudo dpkg-reconfigure xserver.org anymore if we moved a hard disk or a USB full install from one computer to another.

Try looking in some of these links and see if you can find anything helpful, 

**[[B]How do i manually configure xorg.conf ?**]("http://ubuntuforums.org/showthread.php?t=788765")

[/B] Ubuntu Documentation > Community Documentation > [XORGHardy]("https://help.ubuntu.com/community/XORGHardy?action=fullsearch&context=180&value=linkto%3A%22XORGHardy%22") 

[X Configuration]("https://wiki.ubuntu.com/X/Config") - ubuntu wiki

Regards, Herman :)

---

### Post by Herman on 2010-03-15
You could try appending the boot option: xforcevesa
to the end of your boot options on your kernel line at boot-up by pressing your 'e' key from your GRUB Menu to see if that helps.

If that fixes your problem you can add that kernel option to your menu.lst to make the change persistent. :D

---

### Post by Cariboo1938 on 2010-03-17
Thanks Herman for the hints..
In the meantime my Hard drive crashed ](*,)  and right now there is no opportunity to work on the issue...
I'll keep you posted when the machine is running again...
Cheers
;)

---

### Post by Cariboo1938 on 2010-03-26
:KS "vesa" solved the Mystery...:D

What I did:
Copied xorg.conf from the Live CD and modified the "Screen" Section.
Now /etc/X11/xorg.conf for my monitor LG Flatron T710BH is: See attached file ;)

:KS Special thanks to you, Herman, for the hint, although I solved it differently!;)

---

### Post by Herman on 2010-03-26
:D Well done, Cariboo1938 :D

---

