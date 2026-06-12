---
title: "Ubuntu CD Stops on Installation"
date: 2007-01-28
forum: Installation &amp; Upgrades
---

### Post by Matand009 on 2007-01-28
I'm running on a Toshiba satalite 4060CDT and when i try to install Ubuntu it stops...

i dont know what to do...

It gets to this orange/pinkish screen and loads forever and then eventually stops...

can someone plz help...

---

### Post by meng on 2007-01-28
What are the specifications on your machine? Try using the Alternate CD to install instead.

---

### Post by hodad on 2007-01-28
Hi,

I'm having the same problem; what do you mean by "alternate CD"? Didn't see an alternate choice on the Edubuntu download site.

In my case, I'm trying to load Edubuntu on an older '486 machine (about 7 years old) for my kids, I changed BIOS to boot from CDROM first.  I get an error message on boot up from CDROM saying "Failure...", and Windows 98 starts instead. No other info, checked out CD and it has the Edubuntu 6.06.1-install-i386.iso on it.  Opened up the CD and it all seems to be there (on my Linux PC). On the older machine, the CDROM drive registers the .iso file, so I know the CDROM is working.

Thanks

---

### Post by meng on 2007-01-28
> **hodad said:**
> Hi,

I'm having the same problem; what do you mean by "alternate CD"? Didn't see an alternate choice on the Edubuntu download site.

In my case, I'm trying to load Edubuntu on an older '486 machine (about 7 years old) for my kids, I changed BIOS to boot from CDROM first.  I get an error message on boot up from CDROM saying "Failure...", and Windows 98 starts instead. No other info, checked out CD and it has the Edubuntu 6.06.1-install-i386.iso on it.  Opened up the CD and it all seems to be there (on my Linux PC). On the older machine, the CDROM drive registers the .iso file, so I know the CDROM is working.

Thanks
Your problem is different - you shouldn't have copied the iso file to the CD. You use the iso file to generate a complete filesystem that then gets burned to CD. Look here:
[www.psychocats.net/ubuntu/iso](www.psychocats.net/ubuntu/iso)

---

### Post by HedleyQ on 2007-01-28
I have tried to get Ubuntu, Kubuktu, various versions, to install so that I can evaluate them.
They all fail to complete, just freezing up.
eg Ubuntu 6.06 seems to be going well but freezes when installing hardware drivers.
Perhaps a raw beginner who is wanting to escape the clutches of Bill would be better buying a commercial offering like Red Hat?
HedleyQ

---

### Post by meng on 2007-01-28
> **HedleyQ said:**
> I have tried to get Ubuntu, Kubuktu, various versions, to install so that I can evaluate them.
They all fail to complete, just freezing up.
eg Ubuntu 6.06 seems to be going well but freezes when installing hardware drivers.
A common reason for this is a bad CD burn. I have myself been victim of this problem countless times, I just reburn at a lower speed.

---

### Post by Matand009 on 2007-01-28
ok go here...

[http://www.ubuntu.com/products/GetUbuntu/download?action=show&redirect=download]("http://www.ubuntu.com/products/GetUbuntu/download?action=show&redirect=download")

click on your area and stuff...

than click on a server and click the 3rd selection...

you should be at a different page...

pick the one for your processor and stuff...

ps. when you burn it you have to burn the iso as an image...

go here for on how to do that:

[https://help.ubuntu.com/community/BurningIsoHowto]("https://help.ubuntu.com/community/BurningIsoHowto")

its working for me :) ...

well now it is...

---

### Post by hodad on 2007-01-29
Meng,
Thanks; I'll give it a try.

---

### Post by hodad on 2007-01-29
Wow! I visited the "Psychocats" link.

Seems like a hugely complicated procedure!  Every time I try something that involved, something *Always* goes wrong.  Isn't there an easier way?

---

### Post by hodad on 2007-02-05
I found out the problem: 
The download file wasn't clean.  On the Ubuntu help website (listed below), I found out that I needed to run the command "md5sum <filename>"  and get a "hash" #  (a checksum calculation).  Then I compared the hash to those published on the Ubuntu website .  The hash wasn't correct, so I redownloaded, then checked the hash on the new download, and it was correct.  The  CD I created using the file with the correct hash worked just fine.  Find directions here:

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

