---
title: "how to &quot;forcepae)"
date: 2015-05-18
forum: Installation &amp; Upgrades
---

### Post by greyowl2 on 2015-05-18
I have an older laptop:  Dell Latitude D600, 1.6 Ghz pentium M processor with 1GB RAM.
I am trying to use a Live CD of Lubuntu 14.10 (32 bit) which I got from Linux Pro Magazine.--I don't want to install it on my computer, just use the live CD.
It will not complete the boot. I get a message"use parameter "forcepae" to enable at your own risk".  
I don't know how to do this.  Please explain the procedure.  Also, what is the risk?
thanks

---

### Post by grahammechanical on 2015-05-18
See the heading Changing the CD boot option configuration line in this link. Look at images 6, 7 & 8

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

We get to that part by pressing Enter at the first screen. We then select the language and press Enter. At the underlying screen press F6.

The Lubuntu wiki says this
> 
After selecting language you arrive at the main menu of the installer. Click on F6 

At the boot menu screen the options are 


[LIST]
[*]Try Lubuntu without installing (in the desktop installer but not in the alternate installer] 
[*]Install 
[*]... 
[/LIST]
With the **Install** choice high-lighted press F6. (This option needs less RAM than installing from 'Try Lubuntu') 

A menu with a number of options appears. The option 'forcepae' is not there, so press Escape to close the list. 

Now a string of options is visible, often with 'quiet' or 'quiet splash --' at the end. Add 'forcepae' to the string **before** and **after** the two dashes. 

... quiet splash forcepae -- forcepaePress return, and the installation begins.

[https://wiki.ubuntu.com/Lubuntu/AdvancedMethods](https://wiki.ubuntu.com/Lubuntu/AdvancedMethods)

The first link shows images but with the purple colour of Ubuntu. With Lubuntu the background colour should be Blue.

Regards.

---

### Post by greyowl2 on 2015-05-18
Thank you for the information.
With this method, is it possible to simply Try Lubuntu on the  CD without installing it on my computer.  So, wouldn't I use the first choice to "Try Lubuntu without installing it".  I don't want to install it.

---

### Post by sudodus on 2015-05-18
***Yes***, the first instance of **forcepae** applies to the live session (both 'Try Lubuntu' and 'Install'), and the second instance of **forcepae** will carry the boot option to the installed system (in case you install it after trying).

---

### Post by greyowl2 on 2015-05-18
It works--thanks for the help to try out Lubutu.

I have a new question:  How do I install Adobe Flash plugin for the Firefox browser?  I downloading it but it did not automatically install.  I had the same problem with Puppy Linux.

---

### Post by sammiev on 2015-05-18
Hi,

If you installed the OS, you can go to Terminal or "Ctrl + Alt + T" and enter.

```
sudo apt-get update
```

```
sudo apt-get install flashplugin-installer
```

---

### Post by greyowl2 on 2015-05-18
I understand--I can't modify anything if I am just using the Live CD--right.

Thank you for clarifying this.

The laptop which I am using is an old Dell Latitude D600 with 1.6 Ghz Pentium M processor and 1GB of RAM.  Do you think that Lubutu would be the best for it or is there another distro which would be better?

---

### Post by Vladlenin5000 on 2015-05-18
Xubuntu or Lubuntu should be fine. Variants with DEs requiring 3D acceleration will work poorly (if at all).

---

### Post by greyowl2 on 2015-05-18
> **Vladlenin5000 said:**
> Xubuntu or Lubuntu should be fine. Variants with DEs requiring 3D acceleration will work poorly (if at all).

Which would be lighter on resources and faster to operate?

Also, I am just using the Live Lubuntu CD right now with an ethernet cable for internet.  Can Lubuntu detect my wireless internet and connect me?  I was able to do this when I tested Puppy Linux.

---

### Post by Vladlenin5000 on 2015-05-18
Lubuntu (with LXDE) is one of the lightest.
All Ubuntu flavors and almost all unofficial spins are the some "under the hood", what really changes is the DE. As such, native support for devices is the same, ie, if you don't have the wireless recognized and working in Lubuntu OOTB the same will happen in any other variant.

Whatever you choose, in case of difficulties, you're welcome to post here. Wireless or other network issues should be in the Networking & Wireless section and while you're there make sure you read the stickies before anything else.

---

### Post by greyowl2 on 2015-05-18
Thanks for the information which is very helpful.

In regard to the wireless issue, I don't find a wizard or utility on the lubuntu CD that detects and connects to wireless as there was with Puppy Linux CD.  I guess this is something that would need to be added after installing lubuntu on the computer.  Or, can it be installed while I am using the Live CD?

BTW, I note that the Lubuntu 15.04 iso download is 696 mb.  It would need to be burnt to a CD or DVD to make it bootable.  Will it fit on a standard CD which holds 700 mb?

---

### Post by mörgæs on 2015-05-18
Always install and apply all updates with wired internet access. Wirefree comes later - you will probably be able to manage on your own if you read the aforementioned sticky notes.

---

### Post by greyowl2 on 2015-05-18
Thanks for the information.

My CD burner will only burn CD up to 700mb--it won't burn DVDs.

I have a Lubuntu 14 disc however from a magazine.  If I install Lubuntu 14, can I then update it via the internet online?

---

### Post by sammiev on 2015-05-18
> **greyowl2 said:**
> Thanks for the information.

My CD burner will only burn CD up to 700mb--it won't burn DVDs.

I have a Lubuntu 14 disc however from a magazine.  If I install Lubuntu 14, can I then update it via the internet online?

Did your wired connection work when you ran Try Ubuntu?

---

### Post by greyowl2 on 2015-05-18
I have only tried Lubuntu 14 from the Live CD--I did not actually install it on my laptop.  The wireless was not detected.

I tried Puppy Linux and it detected and connected to the wireless.

---

### Post by sammiev on 2015-05-18
> **greyowl2 said:**
> I have only tried Lubuntu 14 from the Live CD--I did not actually install it on my laptop.  The wireless was not detected.

I tried Puppy Linux and it detected and connected to the wireless.

Try it again wired and see if it works.

---

### Post by greyowl2 on 2015-05-18
It worked fine when wired with ethernet cable.

---

### Post by sammiev on 2015-05-18
> **greyowl2 said:**
> It worked fine when wired with ethernet cable.

Your wireless will likely work after you install and take all the updates.

---

### Post by greyowl2 on 2015-05-18
> **sammiev said:**
> Your wireless will likely work after you install and take all the updates.

Oh, this is good.

Thank you for the encouraging assessment.

I was just reading the stickies on Networking & Wireless which is also encouraging.

I know that if I run into problem I can get help from this forum.

Thanks for the help.

---

### Post by mattharris4 on 2015-05-18
> **greyowl2 said:**
> It works--thanks for the help to try out Lubutu.

I have a new question:  How do I install Adobe Flash plugin for the Firefox browser?  I downloading it but it did not automatically install.  I had the same problem with Puppy Linux.

The Adobe Flash plug-in for Firefox is hopelessly out of date and Adobe refuses to update it.  However, there is a program called Pepper Flash which takes its place.  Unfortunately you need to actually install Lubuntu to use it, you cannot use it from the Live CD.  Here is a website with instructions:  [http://www.omgubuntu.co.uk/2014/06/install-pepper-flash-chromium-ubuntu-14-04](http://www.omgubuntu.co.uk/2014/06/install-pepper-flash-chromium-ubuntu-14-04) .  It states that the instructions are for Ubuntu but it works with Lubuntu as well -- I have verified this personally, it probably works with Xubuntu and Kubuntu too but I haven't personally tried it with those OSes.

Please note that some documentation states that Pepper Flash only works with Chromium.  It now works with Firefox as well, I have verified this myself.

LATE EDIT:  Pepper Flash also installs and works with Xubuntu just fine.

---

### Post by sudodus on 2015-05-19
> **mattharris4 said:**
> The Adobe Flash plug-in for Firefox is hopelessly out of date and Adobe refuses to update it.  However, there is a program called Pepper Flash which takes its place.  Unfortunately you need to actually install Lubuntu to use it, you cannot use it from the Live CD.  Here is a website with instructions:  [http://www.omgubuntu.co.uk/2014/06/install-pepper-flash-chromium-ubuntu-14-04](http://www.omgubuntu.co.uk/2014/06/install-pepper-flash-chromium-ubuntu-14-04) .  It states that the instructions are for Ubuntu but it works with Lubuntu as well -- I have verified this personally, it probably works with Xubuntu and Kubuntu too but I haven't personally tried it with those OSes.

Please note that some documentation states that Pepper Flash only works with Chromium.  It now works with Firefox as well, I have verified this myself.

Thanks for sharing this information :KS

---

### Post by sudodus on 2015-05-19
> **greyowl2 said:**
> Oh, this is good.

Thank you for the encouraging assessment.

I was just reading the stickies on Networking & Wireless which is also encouraging.

I know that if I run into problem I can get help from this forum.

Thanks for the help.

I'm glad that you are able to run Lubuntu and that our help has been useful for you. Now that your original problem is solved, please click on **Thread Tools** at the top of the page and mark this thread as SOLVED :-)

If you get problems later with networking or something else, it is better to start a new thread with a good descriptive title to get help with those problems. (You can post a link from this thread to that thread if you wish.)

---

