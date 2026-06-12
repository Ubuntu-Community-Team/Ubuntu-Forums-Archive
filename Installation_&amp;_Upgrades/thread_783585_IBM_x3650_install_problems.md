---
title: "IBM x3650 install problems"
date: 2008-05-05
forum: Installation &amp; Upgrades
---

### Post by RichardMullins on 2008-05-05
G'day.

I did a quick search and couldn't find anything that helped but if I missed it happy to be pointed in the right direction.

OK short version of the problem...

I have an IBM x3650 on which I want to install ubuntu (its listed in [Validated Hardware]("http://webapps.ubuntu.com/certification/hardware/200802-220/")). I loaded up a disc I already had (Kubuntu 7.10 desktop) and selected install from the menu. The splash screen did its thing and at the point where the desktop would normally load the monitor switched off. I tried again with acpi=off as a boot option but still no video (the monitor didn't stay off but its power led changed to orange (guessing thats means the video signal is out of range)). I tried a different monitor but still no joy. I could switch to console (CTRL-ALT-F1) and use that just fine. I downloaded and tried 8.04 as well but the result is the same.

So the question is do I need to do something else to get it to boot properly? Alternatively can I get the install going without needing to get to the desktop. I don't want to install the server version although if I have to I will. The reasons are outlined below if your interested.

More information...

OK so I have this machine by chance. Our servers have been Gentoo based for some time but the upkeep is getting difficult and is perceived as out of reach to others in the company. There was talk of going to Windows SBS but I thought I would try them on a easier, GUI based solution first to see if that helped. And it did, they love the KDE desktop, using adept, etc, etc. and can manage the machine through webmin. So all good. I want to use the same distro throughout if I can and we already have two of these servers set up with Kubuntu 7.10 Desktop. I guess I can get the same software installed on all the machines (in gentoo I could copy across the world file - all the programs that have been installed, is there an equivalent in debian?).

Sorry for the long (first) post. hopefully someone can set me straight.

---

### Post by apalacheno on 2008-07-25
I have an IBM (Lenovo) ThinkPad Z61m with an ATI X1400 graphics card. Using 7.10 I had the exact same problems as you - and since the IBM x3650 uses (AFAIK) ATI as well, our problems might be connected.

You might try the alternate installer, which works fine.

Using 8.04 works right out of the box for me, but if it doesn't for you, there is a simple workaround (by installing fglrx, which shouldn't be installed on a server due to its closed-source nature, but I post it anyway):

First off, you need to be connected to the internet. When the screen turns black or an X-server error message appears, switch to a console Windows using Ctrl+Alt+F1 for example and manually install the fglrx driver.

```
$ apt-get update

$ apt-get install xorg-driver-fglrx

$ depmod -a

$ aticonfig --initial

$ startx
```

Then you should have an x-server running at your displays native resolution.

---

