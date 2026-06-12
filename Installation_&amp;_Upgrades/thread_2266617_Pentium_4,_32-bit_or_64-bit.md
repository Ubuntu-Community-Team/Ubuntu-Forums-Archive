---
title: "Pentium 4, 32-bit or 64-bit?"
date: 2015-02-24
forum: Installation &amp; Upgrades
---

### Post by sahaj2 on 2015-02-24
I currently have windows 7 installed on my other PC. I'm thinking of installing Ubuntu on it. Here are my PC specs:-


[IMG]http://i.imgur.com/qzyZ8nO.png[/IMG]


Should I install 32-bit or 64-bit? Which one will run smoothly on my PC?


Thanks! :)

---

### Post by slickymaster on 2015-02-24
Hi sahaj2, welcome to the forums.

In order to get a correct answer for your question, can you provide us some more information on your computer specs? In particular your processor architecture, is it 32-bit or 64-bit?

_**EDIT:**_ Have a read at this -> [https://help.ubuntu.com/community/32bit_and_64bit](https://help.ubuntu.com/community/32bit_and_64bit)

---

### Post by mörgæs on 2015-02-24
The 3.06 GHz Pentium 4 comes in a 32 and a 64 bit version. 

If you can't provide more information as requested above you could just try a 64 bit ISO and see if it works.

---

### Post by efflandt on 2015-02-24
Recent Ubuntu versions like current 14.04 or newer include 32-bit libs. If you try 64-bit and your CPU is not capable the live/install will error something like "Attempting to run x64 on i686".

An old 3 GHz Pentium with hyperthreading that I had at work from 2003 was still 32-bit only. It gave me the x64 on i686 error when I tried live/install iso on it. The first 64-bit cpu I had was Athlon64 3200+ (2 GHz) which may have been before mainstream Intel chips could do that. A dual core work laptop from 2005 was 64-bit capable. So which you can use may depend upon how old the computer is. My guess is that if it is 2006 or newer (or came with Win7) it probably supports 64-bit.

Unless your Internet is limited (for downloads) or additional RAM for the old PC is too expensive or computer itself only supports 2 GB, you could always try 64-bit first to see if the live/install boots.

---

### Post by grahammechanical on 2015-02-24
> [COLOR=#000000]Should I install 32-bit or 64-bit? Which one will run smoothly on my PC?[/COLOR]

32 bit Ubuntu will run and run as smoothly as the limits of the hardware allows on a machine with a 32 bit CPU and on a machine with a 64 bit CPU. And this is because the 64 bit CPU architecture is backwards compatible with the 32 bit Intel CPU architecture. And that is because Microsoft was very slow about releasing a 64 bit version of Windows for the general public.

When it comes to modern operating systems I put the video adapter as having equal significance as the CPU and amount of memory. How much of its own memory does the video adapter have? Does it use shared memory (RAM). Can it do hardware 3D video rendering and it there a driver for it?

When we install Ubuntu we get the latest proprietary video drivers but the manufacturers are in a habit of dropping support for what they consider to be obsolete hardware. I advise that whether it is 32 bit or 64 bit Ubuntu when you install do not tick the box labelled "Install third party software." Then you will get an open source video driver. You can always install the third party codecs later by installing Ubuntu Restricted Extras. And install also a proprietary video driver with Additional Drivers. And if the restart breaks the OS you will know the cause.

Depending on the specification of the graphic adapter you may need to consider Lubuntu.

Regards.

---

### Post by mörgæs on 2015-02-24
Sahaj2, please forget what is said in the post above about proprietary / closed source drivers. Since we don't know your graphics adapter we don't know which drivers are available. 

Everybody, let's wait for Sahaj2 to return before posting more advice.

---

### Post by slickymaster on 2015-02-24
> **mörgæs said:**
> Sahaj2, please forget what is said in the post above about proprietary / closed source drivers. Since we don't know your graphics adapter we don't know which drivers are available. 

Everybody, let's wait for Sahaj2 to return before posting more advice.
+1

---

### Post by mattharris4 on 2015-02-25
I know the OP hasn't returned but I will comment as it has general implications.  If you wish to use the full Ubuntu or Edubuntu operating systems (I recommend the latter as I hate Unity and the Edubuntu variant has a GNOME option -- and it comes with educational games and programs appropriate for kids if that is a concern) you may want to bump up your RAM to at least 2.5GB.  I ran Edubuntu with only 2GB of RAM (essentially Ubuntu with a GNOME diaplay option and a slate of educational-use programs) and on the worst RAM-hog site I use (SFGate -- which is San Francisco's main newspaper's site) the computer kept maxing out my RAM and going to my hard drive swap space.  Unfortunately once it did that my computer slowed to a crawl.  I upgraded my RAM to 3.5GB (it is very easy to do) and haven't had the issue since, my monitor states I am using between 2.2 and 2.5GB of RAM on that site.  With the readings I am getting I think if you upgraded to 2.5 or 3GB you would have a much better operating computer.  

Your other option is Lubuntu (a lighter OS by Canonical) and downloading any pertinent programs that come with Ubuntu but not with Lubuntu from the Software Center.  Lubuntu will work just fine on 2GB of RAM.  If you go for this option you will need to download an office suite such as Libre Office (which comes with Ubuntu) separately, that program is not a RAM hog and doesn't require Ubuntu specific features so it should run just fine.  Modern web browsers run well too.

For the record my desktop runs a Pentium 4 at 3.00GHz, your processor is just a touch faster but otherwise I suspect it works similarly.

---

