---
title: "how do I install driver from a .ppd file?"
date: 2008-07-06
forum: Installation &amp; Upgrades
---

### Post by hill0093 on 2008-07-06
I have downloaded file Xerox-DocuPrint_P12-ljet2p.ppd  
to  /home/user1/Desktop/ and 
I want to install this driver for my 
Xerox DocuPrint P12 laserjet on my parallel port.
How do I do this?

---

### Post by jpkotta on 2008-07-06
Go to [http://localhost:631](http://localhost:631), add a printer, and when it asks for a driver selection, give it the ppd.

---

### Post by hill0093 on 2008-07-06
Thanks, it seems to have worked.
But I don't have my Xerox printer at the same place
that I am using the internet.

---

### Post by jpkotta on 2008-07-06
> **hill0093 said:**
> Thanks, it seems to have worked.
But I don't have my Xerox printer at the same place
that I am using the internet.

It doesn't have anything to do with the internet.  "localhost" is the computer that you are on right now (it is not a placeholder, either - literally type "localhost").  There are other ways to configure CUPS (the print system in Ubuntu), but I think the web interface is good because it is always there and is just as easy as the other ones I've used.

---

### Post by hill0093 on 2008-07-06
Another big thanks to you for the clarification.
The other aspect of not trying it yet is that 
I downloaded the .ppd from the internet and 
don't have internet where I am going to use the printer.

---

### Post by jpkotta on 2008-07-07
You don't have a USB drive?  Go pick one up at any electronics store, the cheapies are less than $10.

---

### Post by hill0093 on 2008-07-07
Sorry, I don't understand the relationship to the USB drive.
Yes, I have 1,2,&4 GB sticks and a 120GB 5000rpm.
In any case, I believe I am setup for the P12 thanks to you.
But I haven't tried it yet.

---

### Post by wpshooter on 2008-07-07
> **jpkotta said:**
> Go to [http://localhost:631](http://localhost:631), add a printer, and when it asks for a driver selection, give it 
the ppd.

I don't think you have to do all of this.

All you need to do is go to System/Administration/Printing and from there setup your print on just about the same basis that you would under a M/S windows machine.

Thanks.

---

### Post by jpkotta on 2008-07-07
> **hill0093 said:**
> Sorry, I don't understand the relationship to the USB drive.
Yes, I have 1,2,&4 GB sticks and a 120GB 5000rpm.
In any case, I believe I am setup for the P12 thanks to you.
But I haven't tried it yet.

I thought you meant you didn't have a way to get the .ppd to the machine you want to print from.

There is a "Print test page" button at [http://localhost:631/printers/](http://localhost:631/printers/) if you want to test.

---

### Post by hill0093 on 2008-07-08
Yes, I took it to my printer and it works. Thanks again.

---

