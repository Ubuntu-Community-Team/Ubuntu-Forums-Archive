---
title: "Removal and installing of modules."
date: 2007-10-21
forum: Installation &amp; Upgrades
---

### Post by The_Marlboro_Man on 2007-10-21
Hello!.

Recently I upgraded from Ubuntu Fiesty to Gutsy, it was a breeze. In Fiesty I had to do some steps in order to replace a module for my Usb Wireless Network adapter, as seen in [this thread]("http://ubuntuforums.org/showthread.php?t=577480"). 

When going into Gutsy I saw that Gutsy did work "out of the box" with my network card, as I was able to connect via the Network Manager. Still, I had problems when downloading packages and returned to the replacement of the module and "manual connection". That movement wasn't wise at all as all that was happening with the packages was that I forgot to instruct Synaptic on wich repositories to use!.

Replacing the module and deleting the old one results in the Network Manager being unable to "see" that I have a wireless connection and I'd like to revert the modules to the state where I was able to connect "right out of the box". The procedure I followed to get my interface working Fiesty style were:

-rmmod the broken module (rt73usb)
-blacklisting some other modules
-installing the rt73 module

I just tried 

-rmmod the rt73 module
-unblacklist the other modules
-installing the original rt73usb module

But it just doesn't work. I don't know a lot about the inner workings of Ubuntu but I see that I have done something wrong: lsmod shows me that all the unblacklisted modules are running along with the rt73 that I thought I removed with rmmod...

So, how do I get to permanently remove rt73 to revert Ubuntu to the status it had before I installed it?.

Thanks a lot for your help in advance.

---

