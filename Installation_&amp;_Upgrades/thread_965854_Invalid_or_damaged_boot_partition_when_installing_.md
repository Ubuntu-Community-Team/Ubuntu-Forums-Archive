---
title: "Invalid or damaged boot partition when installing 8.10 on acer aspire one"
date: 2008-10-31
forum: Installation &amp; Upgrades
---

### Post by joy83 on 2008-10-31
So I have the Acer Aspire One 120Gb version and I am planning to install ubuntu 8.10 on it. Since it doesnt have a CD rom drive I got mself a 2Gb flash drive and was following the instructions on this link on how to install ubuntu from a USB drive 

[https://help.ubuntu.com/community/AspireOne110L?highlight=%28%28AspireOne%29%29](https://help.ubuntu.com/community/AspireOne110L?highlight=%28%28AspireOne%29%29)

Now when I put the flash drive in my acer and then tell it to boot from the USB drive it gives me the error "Invalid or Damaged boot partition". 

Someone please help since I really want Ubuntu on my acer.

---

### Post by joy83 on 2008-10-31
Any suggestions?

---

### Post by noremaku on 2009-01-10
Same problem here. The iso is fine. Occurs on any computer.

---

### Post by CJWertz on 2009-01-20
I had the same problem today. maybe I can help someone by telling what I did to resolve it. The very short version of the story is that I had to completely clean a brand new usb device in order to install successfully.

I have Toshiba satellite notebook - el cheapo. It came with (ugh!) vista and I'd like to free it from that.

I decided to ease into ubuntu by installing to a usb stick. I have an 8.10 live cd I downloaded. The cd seems to work just fine. It is, in fact, the best live cd I've tried. It automatically recognizes my wireless adapter and my printer and works them just fine.

I ran the install to an 8 gb kingston data traveler: 
System-->Administration-->Create a usb startup disk. It seemed to work. When I tried to boot from it, it said, "invalid or damaged boot partition"

This usb device came with some security software. I figured I needed to get rid of that or something. So, I went to windows and formatted the usb. Then, I went back to ubuntu and ran the install again. I got the same bad result. 

I noted several others have asked about this on the ubuntu forum but have not received any answers. I also saw the same thing on a few other forums.

Finally, I got creative - at first I thought maybe I was too creative. I booted ubuntu again, and without knowing what I was really doing, started partition manager: 
System-->Administration-->Partition Editor, and selected Create Partition Table. I went for msdos. It told me all data on the device would be destroyed. I said OK. I seemed to have bricked the usb. Neither ubuntu nor windows would do anything with it.

So, I went back to ubuntu, ran the editor again, and created a 7648mb partition. ext2 came up as default. I decided to go for fat32 instead.

Then I went back to the install. It said /dev/sdb needs to be formatted. I clicked format. Then I clicked install once again. 

Voila. She flies. Well, she doesn't fly. Running from the usb is relatively slow, but it does work. 

Now I need to spend some time learning how to work things. Something as simple as installing the Flash plug-in for Firefox is different from what I've been used to.

Charlie Wertz

---

### Post by shane8002 on 2009-01-20
Same problem here, u half to remember man we don't have cd  rom drives so theres no way to ubuntu at all to add a new partition.

---

### Post by joethehax0r on 2009-02-06
> **CJWertz said:**
> I booted ubuntu again, and without knowing what I was really doing, started partition manager: 
System-->Administration-->Partition Editor, and selected Create Partition Table. I went for msdos. It told me all data on the device would be destroyed. I said OK. I seemed to have bricked the usb. Neither ubuntu nor windows would do anything with it.

So, I went back to ubuntu, ran the editor again, and created a 7648mb partition. ext2 came up as default. I decided to go for fat32 instead.

Then I went back to the install. It said /dev/sdb needs to be formatted. I clicked format. Then I clicked install once again. 

Voila. She flies. Well, she doesn't fly. Running from the usb is relatively slow, but it does work. 

Now I need to spend some time learning how to work things. Something as simple as installing the Flash plug-in for Firefox is different from what I've been used to.

Charlie Wertz

Mr. Wertz, 

Had to register to thank you for this post, confirmed this worked on my 2gb kingston.  First deploy was on a HP Pavillion dv6000 laptop.  Had the same problem as everyone else "Invalid or damaged boot partition", i formatted it as FAT32 from Vista first and it failed but when i partitioned from ubuntu it worked like a charm!

---

