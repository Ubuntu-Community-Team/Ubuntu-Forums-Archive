---
title: "Windows 7 USB Boot Loader on Lubuntu?"
date: 2013-04-13
forum: Installation &amp; Upgrades
---

### Post by Spaztrooper on 2013-04-13
I did a bit of research and could not find the answer to my question (or maybe I completely missed it). 

Here we go:

I am trying to install windows 7 on another net book and I was curious to know if I can download the windows 7 USB Boot loader (or something similar) on lubuntu and do it that way and then install on my other net book. In general, I need to know if a program exists in order for to do that. 

Thanks.

---

### Post by C.S.Cameron on 2013-04-13
You can use gparted from the Lubuntu Live CD to format the USB NTFS and set boot flag.
Then you can use Archive Manager from the Live CD to extract the Win 7 iso to the USB.
This you can boot and use to install Windows 7.

---

### Post by Spaztrooper on 2013-04-13
> **C.S.Cameron said:**
> You can use gparted from the Lubuntu Live CD to format the USB NTFS and set boot flag.
Then you can use Archive Manager from the Live CD to extract the Win 7 iso to the USB.
This you can boot and use to install Windows 7.
[COLOR=#000000]
So, I set the file system to NTFS and the flag is set to Boot. Do I need to mess with the free space options etc.?


[/COLOR]

---

### Post by C.S.Cameron on 2013-04-13
I didn't.

---

### Post by Spaztrooper on 2013-04-13
> **C.S.Cameron said:**
> I didn't.

So, even though the Windows 7 .ISO is...what? 4Gigs? I don't need to do anything else. I just want to make sure.

---

### Post by C.S.Cameron on 2013-04-13
Just format NTFS, set boot flag and extract the files in the iso to the root of the USB.

I've seen complicated ways of doing it but I tried the above and it worked perfectly.
Please let us know if it doesn't work for you.

---

### Post by Spaztrooper on 2013-04-13
Awesome. Thank you. Will let you know what happens.

---

### Post by Spaztrooper on 2013-04-13
Ok, so I formatted the USB and I have the .iso file. I copied the .iso file and pasted it in the USB.  That should do it right...

I put the USB in the drive and when I boot from the USB in BIOS it starts and tells me "BOOTMGR is missing" 

What did I do wrong??

---

### Post by C.S.Cameron on 2013-04-14
As I said above, you need to **extract** the iso file to the USB.
Open the iso file using Archive Manager and **extract** the files inside it to the root of the USB.

Edit:
You should end up with a set of files and folders just like are on the Win 7 DVD.
Or if you have a Win 7 DVD you can just copy it to the USB.

---

### Post by Mark Phelps on 2013-04-14
If this netbook originally came with Win7 (as most do) and you're trying to put it back -- be sure you have the same version as the activation code on the netbook case will not work if they are different.  Many Netbooks came with Win7 Starter (which is the main reason I did not buy one) and that is generally not available for legal purchase.

---

