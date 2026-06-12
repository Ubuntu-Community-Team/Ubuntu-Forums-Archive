---
title: "New Install: No CD, Floppy, USB, nothing."
date: 2008-04-12
forum: Installation &amp; Upgrades
---

### Post by lankforddl on 2008-04-12
I've tinker'd around with various methods of installation but I can't get any to work. I have a Dell Latitude C400 laptop that I would like to install Ubuntu on. I don't have a CD drive, floppy drive, and the laptop is not capable of booting from USB. Any suggestions?

Oh, and the caveat is that I don't have an OS installed on the drive. It was clean'd and formated when i purchased it.  

Thanks,
Lankforddl

---

### Post by oilchangeguy on 2008-04-12
> **lankforddl said:**
> I've tinker'd around with various methods of installation but I can't get any to work. I have a Dell Latitude C400 laptop that I would like to install Ubuntu on. I don't have a CD drive, floppy drive, and the laptop is not capable of booting from USB. Any suggestions?

Oh, and the caveat is that I don't have an OS installed on the drive. It was clean'd and formated when i purchased it.  

Thanks,
Lankforddl

you can take the hard drive out, put it in another lappy with a cd drive and install ubuntu. then place the hard drive back in your computer. or get an adapter cable (try ebay) and put the hard drive in a desktop, install ubuntu. then put the hard drive back in your computer. another question, what are the lappy's specs? if it doesn't have a cd drive, or floppy drive, it has to be able to boot from a usb device.

searched google, and the lappy has an optional cd drive. check ebay to see if you can find one.

check this out:
[http://cgi.ebay.com/Dell-Latitude-C400-Floppy-CD-DVD-ROM-Drive-Caddy-07G686_W0QQitemZ300213766631QQihZ020QQcategoryZ177QQssPageNameZWDVWQQrdZ1QQcmdZViewItem](http://cgi.ebay.com/Dell-Latitude-C400-Floppy-CD-DVD-ROM-Drive-Caddy-07G686_W0QQitemZ300213766631QQihZ020QQcategoryZ177QQssPageNameZWDVWQQrdZ1QQcmdZViewItem)

---

### Post by twist2b on 2008-04-12
Create a partition, then get the iso. Unpack the iso with any program, Just add all the information into the iso. I dont know if that works. But you should try it :P

I think your in trouble though, how do you have NO ports?

---

### Post by lankforddl on 2008-04-12
It's a Dell C400 ultralight. 
it's one of those laptops from around 2004 with 1.2ghz pIII. It has one USB port but no floppy or cd bays, etc.. You had to purchase the $200.00 docking station or buy the external floppy, cd drive. 

I've thought about the "putting the drive in my other laptop" and installing it from there but this drive is a 9.5mm (low profile drive), IDE. My other laptop is SATA so that's a dead end. 

Lank

---

### Post by oilchangeguy on 2008-04-12
> **lankforddl said:**
> It's a Dell C400 ultralight. 
it's one of those laptops from around 2004 with 1.2ghz pIII. It has one USB port but no floppy or cd bays, etc.. You had to purchase the $200.00 docking station or buy the external floppy, cd drive. 

I've thought about the "putting the drive in my other laptop" and installing it from there but this drive is a 9.5mm (low profile drive), IDE. My other laptop is SATA so that's a dead end. 

Lank

read my previous post. i edited it, and added a link, to an external drive and caddy on ebay.

---

### Post by lankforddl on 2008-04-12
Thanks oilchangeguy. I haven't seen one that cheap. They usually end up being 70 when the bidding is over and the laptop was only 100 to start with. 

I'm trying to netboot with the bootp firmware on the 3com eth now. This might be a cool way to get it done. 

Lank

Done!! finally. I bought a 2.5" to 3.5" IDE converter ($9.99) and installed the OS from desktop PC: transfered 2.5" drive back to laptop, updated some hardware issues and I'm good to go. I guess no one is reading this anymore but it may give someone else ideas on how to fix a similar problem.

---

### Post by rickatnight11 on 2008-07-08
I had the same issue.  Installed Hardy over the network.  It was pretty easy.  Glad you got it working though.  The kicker was, as soon as I finished I found the external cd-drive!

---

