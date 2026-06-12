---
title: "Unity 3d and live cd"
date: 2011-08-15
forum: Installation &amp; Upgrades
---

### Post by Hewjr100 on 2011-08-15
I have tried to run both fedora 15 and unity live cd with no luck.  Apparently my ati radeon hd 4250 with 256mb memory is not supported by either fedora or ubuntu, as far as 3d goes .  However I can choose to boot with basic video in fedora cd, but I do not see this option with ubuntu 11.04.  So how do I boot the live cd with basic video

Henry

---

### Post by mastablasta on 2011-08-15
you need to use additional drivers menu to download and install proprietary drivers provided by AMD/ATI.

the only problem is that upon reboot all changes (including this driver install ) will be lost. that is unless you are suing live3USB key to boot from in which case there is an option to make the liveUSB permanent (i.e. will save some settings)

also the only ATi cards that have issues are some old mobility series cards and some very new ones.

---

### Post by Hewjr100 on 2011-08-15
Thanks for your reply, will get on it asap.  If I choose to install will the additional drivers also be installed?

Henry

---

### Post by Hewjr100 on 2011-08-15
I did fail to mention, that I am currently dual booting win 7 and fedora 14.  Will I be able to access additional drivers from the ubuntu live cd at boot up.  My problem with both fedora 15 and unity is when booting from cd both do the same thing, which is boot to desktop wallpaper with no menus and or launchers/panels, or access to command line.

Henry

---

### Post by coffeecat on 2011-08-15
> **Hewjr100 said:**
> Apparently my ati radeon hd 4250 with 256mb memory is not supported by either fedora or ubuntu, as far as 3d goes .

Since you seem to be talking about a laptop, I guess you would mean the *Mobility* Radeon HD4250. I have an Acer laptop with the Mobility Radeon HD4200, which you can see from this chart...

[http://en.wikipedia.org/wiki/Comparison_of_ATI_Graphics_Processing_Units#Mobility_Radeon_HD_4xxx_Series](http://en.wikipedia.org/wiki/Comparison_of_ATI_Graphics_Processing_Units#Mobility_Radeon_HD_4xxx_Series)

... has the same RV620 chipset as yours. Indeed, I can't see anything different between the two in that particular table.

Whatever, I get Unity 3d out-of-the-box with the default open source driver and the Mobility HD4200 GPU. And the live CD boots fine. So I should think your problem with the Ubuntu 11.04 CD is not related to your video card. Exactly what is the problem when you try to boot the 11.04 CD?

---

### Post by Hewjr100 on 2011-08-15
When I boot the cd everything goes fine until I get to the desktop, then all I get is the wallpaper with no launcher and no panels.  No login screen nothing, same thing with fedora 15. Currently dual booting win 7 and fedora 14.

Henry

---

### Post by coffeecat on 2011-08-16
Make sure the md5sum of the ISO is correct, and also check the integrity of the CD. You can do this by tapping any key when the two small icons of a stick figure and keyboard appear at the bottom of the screen when you first boot the CD. This takes you to the old-style text menu. The disc check is about third in the menu.

If your graphics card was incapable of supporting 3d Unity, then you would be taken to the classic desktop, not just wallpaper and nothing else. Something else must be going wrong, hence the need to check the ISO and the disc.

Try this. Boot the CD and go to the old text menu as described above. Choose the first item in the menu - "try Ubuntu" or words to that effect. When you get just the wallpaper, press the key combination Alt + PrintScr + k. If that does nothing try AltGr + PrintScr + k. That should take you to the login screen. Enter the username "ubuntu". Now choose "classic" from the bottom of the screen. Now you can enter the password which is blank - that is don't type anything in the password field, but just press enter. Does that take you to the classic desktop? If the system doesn't respond to username "ubuntu" and a blank password then you have a faulty CD.

If you get a usable classic desktop, logout with the AltGr + Print + k key combo as before. Now login again with "ubuntu" and no password, but this time choose "Ubuntu" at the choice at the base of the screen - this is Unity. Do you get the Unity desktop?

If you can get the classic desktop but not Unity this still doesn't necessarily mean that this is a graphics/driver issue. But let's see what the result of all that is.

---

### Post by coffeecat on 2011-08-16
@Hewjr100, I've found something interesting, but also some good news.

I've tried booting both a 64-bit live 11.04 CD and a 32-bit live 11.04 USB with my Acer laptop with the HD4200 graphics. In both cases I get only a purple screen and mouse cursor when selecting Unity (Ubuntu), but a working classic gnome desktop if I select that from the login screen. So my apologies. I was going from the fact that I had a working 11.04 on that machine, installed when 11.04 was in beta, and I didn't recall any problem with the live CD/USB

However - the good news. I had a spare partition on the laptop, so I made a fresh installation of 11.04 from the live USB. When I boot into it I get the Unity desktop just fine - 3d and all - and using the default open source driver

I can't explain why I can't get the Unity desktop from the live CD/USB, but can when it's installed. But if your machine, with a near-identical graphics card, behaves like mine you'll get the Unity desktop when you install Ubuntu 11.04 to the hard drive.

**EDIT**: by the way, I don't know why Fedora won't display either. I gave up on Fedora 15 when [I couldn't get it to install in a VirtualBox virtual machine.](http://ubuntuforums.org/showthread.php?t=1777454) The whole wretched experience made me take a solemn vow never to touch Fedora again! :wink:

---

### Post by Hewjr100 on 2011-08-17
Well here is  what I found out.  I installed fedora 14, and then ati driver 11.7 no problem.  When I went to catalyst control panel and looked under info, it stated that my gpu was 2d only no 3d support.  This laptop is a low end system from dell

Henry

---

### Post by Hewjr100 on 2011-08-17
I am not getting email notifications from this forum, I have set it up to notify me of replies, but none come thru.

Henry

---

### Post by coffeecat on 2011-08-17
> **Hewjr100 said:**
>  When I went to catalyst control panel and looked under info, it stated that my gpu was 2d only no 3d support.  This laptop is a low end system from dell

It doesn't matter whether it's low-end, high-end or mid-end, it's got nearly the same GPU as mine and mine will run Unity 3d with the ati open source driver so long as I install it the hard drive. But if you've got the catalyst control panel, that means that you've installed the proprietary fglrx driver, which is not necessary, and in my experience gives you worse performance than the open source one with this GPU. I can't help you.

---

### Post by Hewjr100 on 2011-08-17
I agree the performance sucks under fedora 14, uninstalled it.  Guess I will live with fedora 14, and wait for fedora 16 and ubuntu 11.10 or 12.04.

Henry

---

