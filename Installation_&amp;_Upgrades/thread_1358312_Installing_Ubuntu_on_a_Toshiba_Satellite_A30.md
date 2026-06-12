---
title: "Installing Ubuntu on a Toshiba Satellite A30"
date: 2009-12-18
forum: Installation &amp; Upgrades
---

### Post by Linoel on 2009-12-18
Hey

I'm having a really difficult time getting Ubuntu installed on my Toshiba Satellite A30. 
When i try to install Ubuntu, i get the normal instal menu's and so. So far so good. However when the laptop starts the install it suddenly turns Blank and makes some noises. With some luck this can be solved by pushing the enter button like a madmen. If i get the laptop to install it's usually a successful install however when i restart the Laptop it is unable to turn itself out for some reason. after i turn it back on again (after shutting it down my self) It starts up and halfway through it turns blank again. Someone please help me with this!!

---

### Post by darkod on 2009-12-18
> **Linoel said:**
> Hey

I'm having a really difficult time getting Ubuntu installed on my Toshiba Satellite A30. 
When i try to install Ubuntu, i get the normal instal menu's and so. So far so good. However when the laptop starts the install it suddenly turns Blank and makes some noises. With some luck this can be solved by pushing the enter button like a madmen. If i get the laptop to install it's usually a successful install however when i restart the Laptop it is unable to turn itself out for some reason. after i turn it back on again (after shutting it down my self) It starts up and halfway through it turns blank again. Someone please help me with this!!

Is it running fine if you select Try Ubuntu option?

---

### Post by Linoel on 2009-12-18
No, It's the same then. If i'm selecting the option it makes a lot of noise first, then i see the logo and then it turns blank.

---

### Post by darkod on 2009-12-18
Hardware incompatibility of some kind. If Try Ubuntu doesn't work you can't expect the install to work neither.
What sort of graphics chip does that laptop have?

---

### Post by Linoel on 2009-12-18
The graphic controller is Intel® 852GME And a Pentium4 Processor.
I got Ubuntu 8 working without any problem. And since i'm using a Cd that has been shipped to me it ain't the cd either.

---

### Post by darkod on 2009-12-18
> **Linoel said:**
> The graphic controller is Intel® 852GME And a Pentium4 Processor.
I got Ubuntu 8 working without any problem. And since i'm using a Cd that has been shipped to me it ain't the cd either.

I wonder. I've seen few cases where people with shipped CD were ruling out bad CD and it actually turned out to be just that. Can you boot from USB? Do you have any chance to create bootable usb stick?
I think you can do it from the cd (although if it turns out to be bad not sure how would that work), in System-Administration with the USB Startup Disc creator.
Intel chipset has been known to have video problems with ubuntu. And if 8 works it doesn't mean 9.10 will also. I know it sounds weird.

---

### Post by Linoel on 2009-12-18
I'll try A Usb install first thing when i'm home. If that works you'll hear about it. if it won't you'll hear it to. 
Since i'm at work i'm afraid i can't try it now.
For now i thank you for the help darkod.

---

### Post by darkod on 2009-12-18
Also another option is to try the Alternate Install CD. But the installer process is text based (like on XP was), not GUI. Otherwise it will work the same after that, you still get GUI desktop.
[http://releases.ubuntu.com/karmic/](http://releases.ubuntu.com/karmic/)

---

### Post by Linoel on 2009-12-18
Does the alternate Install involve some commands i have to type? Because i've never worked with an alternate install-Cd.

---

### Post by darkod on 2009-12-18
Not specific commands but the whole process is text based and it can look "weird" compared to the GUI we are usually used to these days.

There are some screenshots here to give you an idea:
[http://news.softpedia.com/news/Encrypted-Ubuntu-8-04-85271.shtml](http://news.softpedia.com/news/Encrypted-Ubuntu-8-04-85271.shtml)

This is for installing encrypted 8.04 so you don't have to do exactly the same, just to give you an idea what the screens look like.

---

### Post by Linoel on 2009-12-18
Haha those screens take me way back. Install of Windows 98! But that is no problem. I'll try it as soon as possible.

---

### Post by *desk* on 2009-12-18
I'm having problems with my A30 laptop too.
I can install Ubuntu 9.10 by pressing F6 (other options) and de-functioning "noapic".
However after the reboot it will not install from the hard drive. I have tried in grub to edit the commands eg. "noapic" "noalpc" etc........the best I've had is a small white Ubuntu logo.

---

### Post by Mechmechie on 2009-12-31
I have the same issues, even off a USB stick using LiLi with Ubuntu 9.04, 9.10 and mint.

I suppose this is one of the few non linux friendly systems

---

### Post by Mechmechie on 2009-12-31
I can get Live to run now by using the F6 key and selecting the first 3 apic options. Before this Live would not run either..
Next is to try the install to Hdd

---

### Post by Mechmechie on 2010-01-05
I installed it ok but cant get it to launch.I have tried using the E key from grub,then using pci=off
the best i get then is a command line boot.:confused:

---

