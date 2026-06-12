---
title: "using .exe files"
date: 2008-07-17
forum: Installation &amp; Upgrades
---

### Post by alexrev on 2008-07-17
So what replaces the exe file from windows in ubuntu. I was trying to upload the drivers to a wireless linksys usb but got stopped in my tracks.

What type of deal replaces an install wizard?

---

### Post by snowpine on 2008-07-17
> **alexrev said:**
> So what replaces the exe file from windows in ubuntu. I was trying to upload the drivers to a wireless linksys usb but got stopped in my tracks.

What type of deal replaces an install wizard?

Hi Alex, welcome to the forums! Not sure which model Linksys you have. I have the WUSB54Gv4, and the instructions in the first post of this thread worked perfectly for me: [http://ubuntuforums.org/showthread.php?t=563547](http://ubuntuforums.org/showthread.php?t=563547)

In a nutshell, there is an application called 'ndiswrapper' that can translate Windows drivers. If you follow the instructions in that link, you'll get ndiswrapper working, then use it to load the Linksys driver. It's a looooong thread, so chances are any question you might have is already answered in there. :) Let me know if you need help.

Obviously, if you have a different model than I do, those instructions may or may not work.

---

### Post by alexrev on 2008-07-17
hi snowpine, I have a WUSB54GC model  usb network adapter.
thanks for the link. I am gunna try readin it and see if it points me in the right direction.

---

### Post by snowpine on 2008-07-17
> **alexrev said:**
> hi snowpine, I have a WUSB54GC model  usb network adapter.
thanks for the link. I am gunna try readin it and see if it points me in the right direction.

One thing I will mention is that you will be using the command line terminal interface a lot if you follow those directions. Don't be scared by it :). Copy and paste is your friend.

---

### Post by alexrev on 2008-07-17
> **snowpine said:**
> One thing I will mention is that you will be using the command line terminal interface a lot if you follow those directions. Don't be scared by it :). Copy and paste is your friend.

I don't understand the language of the thread you linked me to to be honest. I'm really new to linux. and well all things computers.

---

### Post by snowpine on 2008-07-17
> **alexrev said:**
> I don't understand the language of the thread you linked me to to be honest. I'm really new to linux. and well all things computers.

I was in your shoes just a few months ago, so I can relate. :)
Here is some reading material on what the "terminal" is:
[http://www.psychocats.net/ubuntu/terminal](http://www.psychocats.net/ubuntu/terminal)
[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

When giving advice on these forums, we use terminal commands whenever possible, even if there is a "point-and-click" way of doing the same thing. It is too easy to misinterpret advice like "Click the red button halfway down the screen," because what if I have a different size screen than you, or a different color scheme? But with terminal instructions, there is no room for mis-interpretation.

Now that you understand that, let's look at the instructions on the page I linked you to:

```
Get the latest version of the Windows driver for your card from Linksys' website or from the CD that came with your device (whatever vendor).
```

You already did this, right? That's your .exe file. Good! Next step.

```
sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9
```

That is a terminal command. Copy that line, open the terminal (in Ubuntu it's under Applications-->Accessories), and paste it in. Press enter; it will ask you for your password, type your password and press enter. Hopefully all goes well, but if you get any error messages, you can copy them and paste them right into a post here on the forums, that way whoever is trying to help you can see exactly what's wrong! It's much better than saying "yeah, I tried doing ___ and I got a weird error message." Another reason to love the terminal. :)

Good luck, hope that gets you started, and if you have problems, I suggest adding a reply to that mega-thread I gave you the link to, because an expert on wireless drivers is more likely to be following that thread than one called "using .exe files." :KS

---

