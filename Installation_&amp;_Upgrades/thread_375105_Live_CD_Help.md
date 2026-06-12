---
title: "Live CD Help"
date: 2007-03-03
forum: Installation &amp; Upgrades
---

### Post by Austin6641 on 2007-03-03
I am new to Linux, and thought I should try Ubuntu first. But when I am installing Ubuntu 6.06 I get past this screen:
[IMG]http://img144.imageshack.us/img144/9720/w2u218vo.png[/IMG]
and then I get a message saying "Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?" And when I select yes or no it gives me this message: "The X server is now disables. Restart GDM when it is configured correctly." I have tried making new CDs, 5 to be exact, and nothing I try works.
By the way, my computer specs are:
512 mb of ram
40 gb hard drive
GeCube Radeon 7000 graphics card
I am not sure of the processor, but I do know it is an Intel

**EDIT**
I have now installed Ubuntu 6.10 using the alternate CD image. But I still get the X Server error after I see the Ubuntu loading screen. And the command confused57 gave me does not do anything when I enter it when the console screen comes up. Please help.

---

### Post by Austin6641 on 2007-03-03
Disregard this...

---

### Post by Austin6641 on 2007-03-03
Disregard this...

---

### Post by confused57 on 2007-03-03
> **Austin6641 said:**
> By the way, my computer specs are:
512 mb of ram
40 gb hard drive
GeCube Radeon 7000 graphics card
I am not sure of the processor, but I do know it is an Intel
It's probably your graphics card...if you're returned to a console(command prompt) or you may need to press ctrl+Alt+F1, type in ```
sudo dpkg-reconfigure xserver-xorg
``` and try selecting "vesa" as the driver, if this doesn't work, try "ati" or "radeon".
Here's an excellent guide for using this command:
[http://users.bigpond.net.au/hermanzone/p7.html](http://users.bigpond.net.au/hermanzone/p7.html)

---

### Post by Austin6641 on 2007-03-03
I tried the "vesa" and the "ati" options, and neither of them work. I am still getting the error. Also, the radeon option was not there.

---

### Post by Austin6641 on 2007-03-03
I have now installed Ubuntu 6.10 using the alternate CD image. But I still get the X Server error after I see the Ubuntu loading screen. And the command confused57 gave me does not do anything when I enter it when the console screen comes up. Please help.

---

### Post by confused57 on 2007-03-03
> **Austin6641 said:**
> I have now installed Ubuntu 6.10 using the alternate CD image. But I still get the X Server error after I see the Ubuntu loading screen. And the command confused57 gave me does not do anything when I enter it when the console screen comes up. Please help.
When you get the X server error, press Ctrl+Alt+F1, which should get you to a console, login & try the following:
```
sudo /etc/init.d/gdm stop
```
then
```
sudo nano /etc/X11/xorg.conf
```
scroll down to the video section and change the driver to "radeon", with quotes.
Ctrl+X, y, enter...this will save the file.

then try to restart:
```
sudo /etc/init.d/gdm start
```
if this doesn't work, try entering startx...or you may need to reboot.

A lot of people have problems getting ATI video cards to work...Nvidia offers much better Linux support by supplying drivers, etc.

I don't personally have an ATI card, but here's a thread for getting certain ATI cards to work...may or may not help you, since it doesn't list your specific card.
[http://www.ubuntuforums.org/showthread.php?t=190133](http://www.ubuntuforums.org/showthread.php?t=190133)

If you're able to get to a gui, you might want to check out the link given by taurus in this thread:
[http://www.ubuntuforums.org/showthread.php?t=375514](http://www.ubuntuforums.org/showthread.php?t=375514)

---

### Post by Austin6641 on 2007-03-03
Thanks for you help, but now I get an error after I did what you told me to do that says:
> no screens found
XIO: fatal IO error 104 (Connection reset by peer) on X server ":0.0"
after 0 requests (0 known processed) with 0 events remaining.
I am going to try what is on the two threads you gave me right now and I will post when I am done.

**EDIT**
Neither of the threads helped me...

---

### Post by Austin6641 on 2007-03-04
I have been trying countless things and nothing seems to be working. I am doing something wrong or is it just the X Server?

---

### Post by Austin6641 on 2007-03-04
Is there anyway to use my integrated graphics and then update the drivers or whatever needs to be done in Ubuntu? Because when I edit the xorg.conf file, that is the name of the device. But when I tried to use the integrated graphics nothing showed up on the screen.

---

### Post by confused57 on 2007-03-04
> **Austin6641 said:**
> Is there anyway to use my integrated graphics and then update the drivers or whatever needs to be done in Ubuntu? Because when I edit the xorg.conf file, that is the name of the device. But when I tried to use the integrated graphics nothing showed up on the screen.
Might be a setting in your bios to enable the "onboard" graphics or disable the video card...if you have  intel integrated graphics, or even if you don't, maybe there's something in this thread that will give some ideas:
[http://doc.gwos.org/index.php/Nvidia_Intel_Integrated](http://doc.gwos.org/index.php/Nvidia_Intel_Integrated)

---

### Post by Austin6641 on 2007-03-04
I am still getting the error even with the integrated graphics. Any other suggestions?

---

### Post by Austin6641 on 2007-03-04
I reinstalled Ubuntu 6.10 while using the integrated graphics card, yet I am still getting X Server errors.

---

### Post by confused57 on 2007-03-04
> **Austin6641 said:**
> I reinstalled Ubuntu 6.10 while using the integrated graphics card, yet I am still getting X Server errors.
What's your integrated video controller?  You may need to specify a different driver for it using "sudo dpkg-reconfigure xserver-xorg".

---

### Post by lttmik on 2007-03-04
hwo do u get into the command propmpt to use that line of code?

---

### Post by mgmiller on 2007-03-04
ctrl>alt>F1

---

### Post by Austin6641 on 2007-03-04
> **confused57 said:**
> What's your integrated video controller?  You may need to specify a different driver for it using "sudo dpkg-reconfigure xserver-xorg".
Here is a link to my exact computer:
[http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=2719679&CatId=1873]("http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=2719679&CatId=1873")
Accept I have this graphics card installed:
[http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=2155016&CatId=319]("http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=2155016&CatId=319")
**EDIT**
I did the command and found out that the video card's name is "Intel Corperation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device." If that helps. Oh, and what should I change the PCI Bus number to? Since the integrated card is not in a PCI slot.

---

### Post by vijayanand_sodadasi on 2007-03-04
Hi,

I had the same problem.  But my system seem to have a work around.

I boot with the second option on the grub menu (failsafe or resure mode or something of that kind).  It gives me just the text interface without GUI.  Then I enter the command
```
sudo gdm
```Then the xserver starts and gives me the login screen.  After this if I reboot the system and boot into the first option (which is _not_ the rescue mode), the xserver will work.  I dont know if this is right to do or not but it works for me.  I tried a lot to figure out what the problem is and even modifed /etc/X11/xorg.conf file and reconfigured xserver-xorg, but nothing seem to work.

---

### Post by lttmik on 2007-03-04
I tried your line of code and it doesn't work for me  i still am at a blank screen

---

### Post by Austin6641 on 2007-03-04
> **vijayanand_sodadasi said:**
> Hi,

I had the same problem.  But my system seem to have a work around.

I boot with the second option on the grub menu (failsafe or resure mode or something of that kind).  It gives me just the text interface without GUI.  Then I enter the command
```
sudo gdm
```Then the xserver starts and gives me the login screen.  After this if I reboot the system and boot into the first option (which is _not_ the rescue mode), the xserver will work.  I dont know if this is right to do or not but it works for me.  I tried a lot to figure out what the problem is and even modifed /etc/X11/xorg.conf file and reconfigured xserver-xorg, but nothing seem to work.
Still does not seem to be working... Thanks for the suggestion though.

---

### Post by confused57 on 2007-03-04
> **Austin6641 said:**
> Still does not seem to be working... Thanks for the suggestion though.
If you can get to a console, you might try changing your video driver to "i810" in your /etc/X11/xorg.conf.

You might want to check the output of this command to see if your integrated graphics is recognized:

```
lspci
```

If you can't get this to work, you might want to start a new thread with a descriptive title, including your integrated video controller in the title...the title of your current thread wouldn't attract the attention of someone who has experience with this problem.

---

### Post by Austin6641 on 2007-03-04
> **confused57 said:**
> If you can get to a console, you might try changing your video driver to "i810" in your /etc/X11/xorg.conf.

You might want to check the output of this command to see if your integrated graphics is recognized:

```
lspci
```

If you can't get this to work, you might want to start a new thread with a descriptive title, including your integrated video controller in the title...the title of your current thread wouldn't attract the attention of someone who has experience with this problem.
I can see both my integrated card and the PCI card when I type in "lspci". But after changing the driver to i810, I still get the error. I will start a new topic with more specific details tomorrow.

---

### Post by Austin6641 on 2007-03-05
Link to new topic:
[http://www.ubuntuforums.org/showthread.php?p=2252391]("http://www.ubuntuforums.org/showthread.php?p=2252391")

---

