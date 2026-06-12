---
title: "Newbie lost...."
date: 2009-12-15
forum: Installation &amp; Upgrades
---

### Post by RazzyDaz on 2009-12-15
Hello--
  I have been a Windows user for a long time, but have come to love Ubuntu.  Actually, I used to use the original Fedora, back in the day.  Anyway, I need some help....
  
Here is a little background....I was using Vista and spyware took over. Needless to say, I tried to clean my hard drive and screwed up. I would love to use Ubuntu, but I have a small problem. My computer isn't recognizing my cd rom drive in the boot sequence. So, I'm not able to use the live Cd. I had an older copy of Ubuntu on my flash drive and was about to load Wubi, via safe mode in Vista. 

What I'm looking to do really is, load 9.10 ontop of wubi. I can not get into vista, only in safe mode. So, loading the live cd at startup is out of the question. Is there a way to copy files from live CD onto my flash drive? Can I download the ISO and will it install over Wubi?  I would love to use Ubuntu as my only OS.....

Thanks

---

### Post by darkod on 2009-12-15
Can you boot from usb? You could use the stick as boot device and create so called LiveUSB, instead of the LiveCD (the same image just on a usb stick).
And if your computer is infected you might also try creating the usb stick on another computer, either from ISO image, or the LiveCD itself. Just boot it on any computer, plug the usb stick too, and the LiveCD in System-Administration has USB Startup Creator tool.
Another option might be mounting the ISO as virtual cd-rom, if it "boots" the LiveCD Ubuntu, you can create your usb stick that way too (never tried that myself).

---

### Post by houseworkshy on 2009-12-15
"Not recognising your cd at start up" is a problem in itself as if you can only boot from the hard drive what happens if it goes down.  If you go into bios there will be an option to change the boot order.  I'd recomend putting  your cd/dvd drive at the top of the list ( first make a careful note of what your drives are called as the method is to scroll through various options ) then perhaps your usb and the hard drive last.  Your system will then check for boot records in removable media first.  On my machine I get into bios by pressing the del key during the bootup.  I think that this is the most common but if you google for your machine you will find out which key does the same for you.  A word of caution, be very careful not to change anything else as bios is something one can really mess ones system up with.

---

### Post by h4sunoit on 2009-12-15
hi, im new to linux and have started using it at uni, i had to install it via virtual pc on my home machine but every tie i do, oh its ubuntu by the way, it always tells me that kdevelop C++ and kdesvn are programs that im not allowed to download free or something, is there anything anyone on here knows that can help me please? much appriciated.

---

### Post by houseworkshy on 2009-12-20
>h4sunoit  I don't think that is related to your operating system.  Ubuntu will ask for your permission to install some classes of software, usually things that are not open source or "restricted", then on you putting in your password will let you. Have a chat to your network admin'.

---

