---
title: "Use A 32it Distribution"
date: 2008-01-10
forum: Installation &amp; Upgrades
---

### Post by JayDeePlus on 2008-01-10
Hey i just bought a computer from a yard sale, it was running windows 2000 NT. I _THOUGHT_ it was a 64bit processor. but when i try to run the 64bit version of ubuntu 7.10 i get this message, Your CPU does not support long mode. Use a 32bit distribution.

Now, i have looked through other posts on this problem, but i'm bot sure which one from the download page is hte 32bit version.

can someone give me a link or a better suggestion.

---

### Post by taurus on 2008-01-10
[http://www.gtlib.gatech.edu/pub/ubuntu-releases/7.10/ubuntu-7.10-desktop-i386.iso](http://www.gtlib.gatech.edu/pub/ubuntu-releases/7.10/ubuntu-7.10-desktop-i386.iso)

---

### Post by JayDeePlus on 2008-01-10
ok..........so if i burn that to a CD and put it into my 64amd 32bit processor computer it should boot?

---

### Post by brucewagner on 2008-01-10
> **JayDeePlus said:**
> my 64amd 32bit processor computer

I've never heard of one of those.  Are you sure you know what you have?

Try to Google the manufacturer and model number of your system, and read the specs carefully.

---

### Post by taurus on 2008-01-10
You can install i386 on an AMD64 if you wish.  Works just as well.  Make sure you burn it as an image file, not a data file, and try to burn it at a slow speed, like 4x if you can.

---

### Post by JayDeePlus on 2008-01-10
well........before i tried installing ubuntu i thought it was a 64 bit processor........i downloaded and burned the 64bit version to a disc..........the only good news out of that is that it was able to boot from it............but when i get to ubuntu install menu..........i try to install it, but it just takes to a scan saying your Your CPU does not support long mode. Use a 32bit distribution.

So obviously it's not a 64bit ............ so is the i386 the version i need to run on a 32 bit processor?

---

### Post by Craigus on 2008-01-10
It's extremely unlikely that a second hand computer that had windows 2000 installed on it would have a 64 bit CPU.

---

### Post by chewearn on 2008-01-10
> **JayDeePlus said:**
> so is the i386 the version i need to run on a 32 bit processor?

Yes

---

### Post by Partyboi2 on 2008-01-10
> **JayDeePlus said:**
> ok..........so if i burn that to a CD and put it into my 64amd 32bit processor computer it should boot?
Make sure in your bios it is set to boot from the cd rom first
then reboot with the ubuntu cd in the drive and all going well  should boot the disk

---

### Post by JayDeePlus on 2008-01-10
ok, hopefully this works. for some reason the link the the other felo gave earlier is taking a extremely long time to download considering that i have a cable connection. i don't have ne thing else running, nothing else downloading, but when it started downloading it said estatemated time 1hr, 47ms. well, i've been waiting it out and it's like at 59ms . but, maybe it's that server it's downloading from? um, it's this the only good copy?

 i've downloaded the standard copy first, tried burning it, and i put it into the computer and it said it couldn't find nothing to boot from. I thought it was the bios on new computer. So, i figured out how to get into a Emachine computer's bios ( i have never had one, i've heard bad gossip about.), After talking with they tech rep, who says the computer is so old that he didn't have any "walkthoughs" on. Found out it wasn't the bios, see Windows 2000 NT was good because of it's Security, So it would always ask for a password no patter what. I mean, That is the hole reason basically why i'm putting Ubuntu onto the computer. So, It wouldn't let me bout into safe mode and rset the password, couldn't run a system recovery, So i downloaded a free formatting tool called Active@ Killdisk Free, Suit and i formatted the hard drive.

Now, i'm trying to install the new Op after i format, and then i get the error that i'm at now with the Standard Copy of Ubuntu, It doesn't found data on the disc. so i put the disc back into the computer i'm on now and i can't open it this one. So, i burn the 64bit, put it into new computer. And it runns. but back to this problem. i hope it's not the burner or something.

---

### Post by Laibcoms on 2008-01-10
AMD64 is 64-bit, if it won't work, then you were scammed.

Regarding which to download, here's a short help:

i386 or x86 = always refer to 32-bit
x86-64 or x64 or AMD64/amd64 or Intel64/Intel 64 = always refer to 64-bit


Many applications who are now providing 64-bit versions will use one of those above for their filenames so you can distinguish which is which.

If you want more info, you can read: [http://en.wikipedia.org/wiki/x86-64](http://en.wikipedia.org/wiki/x86-64)
One of the few wikipedia entries that is correct :p

---

### Post by JayDeePlus on 2008-01-11
right on! it worked, but i think it needs some more RAM or something, because it's sloooww. i think it didn't just auto installed it, i think it brought it up for me to install it. i say that because ever time i do something with the mouse or the keyboard, the CD start running hard. It's 2 icons on the desktop, Examples and a icon that says install beneath it. I have double clicked on it like 15 - 20 ms ago and the computer and CD is running hard. But nothing yet to majorly happen other then that yet.

---

### Post by Partyboi2 on 2008-01-11
What is the specs of your machine?
You might be better trying the alternate cd if you have a machine with old hardware. The alternate cd is a text base installer and works better with older machines.
[http://releases.ubuntu.com/releases/7.10/](http://releases.ubuntu.com/releases/7.10/)

---

### Post by brucewagner on 2008-01-11
> **JayDeePlus said:**
> right on! it worked, but i think it needs some more RAM or something, because it's sloooww. i think it didn't just auto installed it, i think it brought it up for me to install it. i say that because ever time i do something with the mouse or the keyboard, the CD start running hard. It's 2 icons on the desktop, Examples and a icon that says install beneath it. I have double clicked on it like 15 - 20 ms ago and the computer and CD is running hard. But nothing yet to majorly happen other then that yet.

JayDeePlus, you have not installed it yet!   

You are simply running Ubuntu from the CD.  That is why it's so slow....  (That's called running it from the "Live CD".)

You must now double-click on the icon on the Desktop called "INSTALL".....

Then... you'll be guided through the installation of Ubuntu onto your hard drive.

---

