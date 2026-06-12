---
title: "Unable to access UEFi and some BIOS settings on Dell Inspiron 7720"
date: 2013-06-18
forum: Installation &amp; Upgrades
---

### Post by RedMartin on 2013-06-18
Hi,

I upgraded to a Dell Inspiron 17R SE (7720) a few months back and recently decided that I was missing Ubuntu.

I've download 13.04 and done all the necessary. The DVD didn't load but I was expecting that. I understand that fastboot and Intel SRT need to be switched off so I got into the BIOS but there are no options for them anywhere.

I also can't get to the UEFI settings via the hold shift and restart method. There is no UEFI Firmware setting option on the advanced menu as there is in the link below (scroll waaayyy down).
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

So, I'm wondering, is this down to Dell? Have they made it so that I can't tamper with it and, by extension, use an alternative OS?

After 8 hours of tinkering I've given up. Anyone else had this? I'm trying to convince myself that Win 8 isn't that bad but it's no Ubuntu....

---

### Post by grahammechanical on 2013-06-18
Manufacturers are not consistent in their application of industry agreed standards. They often make adjustments of one kind or another to get their products to perform better. A wiki page can only give you a guide. The writer has not tested the advice on all machines available. The best information for you would come from a Dell motherboard user guide. If Dell failed to provide a guide to adjusting BIOS/EFI settings then you may get one from a Dell web site.

I can understand a manufacturer not wanting uneducated purchasers to access areas that could break the system. When the buyer breaks the system they take the machine back for a refund claiming the machine is broken but not admitting they broke it.

Does this machine have Windows 8 installed? Then it will have secure boot set. That is not necessarily a problem. But many have found it to be so. Again it is down to manufacturers not being consistent in applying Microsoft's specification for being allowed to install Windows 8 on their products.

Regards.

---

### Post by oldfred on 2013-06-18
Dell's seem to be consistent across models. If an UltraBook you then need to turn off Intel SRT and will have to manage your dual video until you install Bumblebee.

See more info in link in my signature.

 Dell UltraBook - Instructions & Details in Post #15 & 16 Devine Shine
[http://ubuntuforums.org/showthread.php?t=2144853](http://ubuntuforums.org/showthread.php?t=2144853)
Installing Ubuntu 12.10 x64 on Dell XPS 13 Alongside Windows from USB New user with Details post 10
[http://ubuntuforums.org/showthread.php?t=2108450](http://ubuntuforums.org/showthread.php?t=2108450)
Dell Inspiron 17R SE -  12.04.2 but otherwise similar to XPS13 above
[http://ubuntuforums.org/showthread.php?t=2125701](http://ubuntuforums.org/showthread.php?t=2125701)
Dell XPS 14 Ultrabook what works
[http://ubuntuforums.org/showthread.php?t=2116597](http://ubuntuforums.org/showthread.php?t=2116597)
Dell 14z used Dell Recovery and Refind
[http://ubuntuforums.org/showthread.php?t=2125397](http://ubuntuforums.org/showthread.php?t=2125397)
 HOWTO Ubuntu 12.10 x64 Dell XPS 14 (UEFI + Intel Rapid Start Technology + Flashcache), bumblebee - Details
Do not understand why flash cache is required, just install to SSD?
[http://ubuntuforums.org/showthread.php?t=2117166](http://ubuntuforums.org/showthread.php?t=2117166)
[SOLVED] Dual-boot Ubuntu/Windows8 on Dell XPS 8500, need just a few advices with info on UEFI settings
[http://ubuntuforums.org/showthread.php?t=2151494](http://ubuntuforums.org/showthread.php?t=2151494)
Dell XPS 8500, desktop. Win 8 eventually worked (Ignore sidetrack to EasyBCD)
[http://ubuntuforums.org/showthread.php?t=2086383](http://ubuntuforums.org/showthread.php?t=2086383)
No EFI boot on Dell Inspiron One 2330 UEFI/BIOS update solved issues:
[http://ubuntuforums.org/showthread.php?t=2086631](http://ubuntuforums.org/showthread.php?t=2086631)
Dell XPS13 general info mega-thread
[http://ubuntuforums.org/showthread.php?t=1932965](http://ubuntuforums.org/showthread.php?t=1932965)
Question about Dell's Ubuntu Preloaded XPS 13 Developer Laptop Link to review, Sputnik
[http://ubuntuforums.org/showthread.php?t=2106590](http://ubuntuforums.org/showthread.php?t=2106590)

---

### Post by RedMartin on 2013-06-18
Thanks all. Oldfred, I'd seen your help on other threads and tried most of the advice. I still can't get my laptop to see the DVD at boot. I've got too much on to waste any more time on it. I'll come back to Ubuntu when it really does 'just work'. 

There should be no need for all this malarkey.

Thanks again though.

---

### Post by oldfred on 2013-06-18
I do not think Ubuntu can make it automatic as Windows has locked out anyone else unless you first turn it off with Windows.

And if you follow this video it is a complicated multistep process from Windows 8 to get into UEFI, if your system does not have a one key like f2 to get into UEFI.

 Video on getting into UEFI - 1 Min Acer but all Windows 8
[http://www.youtube.com/watch?v=QGiG1oljjZI](http://www.youtube.com/watch?v=QGiG1oljjZI)

---

### Post by RedMartin on 2013-06-18
That's just it. In the General/restart/advanced settings 'page' I don't have the UEFI button.

Also, when in the BIOS I have no options for fast boot, the intel thing and faststartup. Are they all in the UEFI section which I can't get to?

Does that make sense? The [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) page is asking me to do stuff which I am unable to do as it's simply not there!

---

### Post by oldfred on 2013-06-18
Fast Boot is Windows hibernation.
       Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)

Unless you have an UltraBook you will not have Intel SRT.
      
 Intel SRT - Dell XPS Screen shots of Intel SRT screens & lots of details 
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2036204](http://ubuntuforums.org/showthread.php?t=2036204)

---

### Post by RedMartin on 2013-06-18
Thanks but again no luck. I thought I might be onto something when I found this link:
[http://www.dell.com/support/troubleshooting/us/en/555/KCS/KcsArticles/ArticleView?c=us&l=en&s=biz&docid=603195](http://www.dell.com/support/troubleshooting/us/en/555/KCS/KcsArticles/ArticleView?c=us&l=en&s=biz&docid=603195)

..but nothing seems to get the damn thing to boot.

As I said before I'm going to give up. I've spent the best part of a day of my holiday trying to get a damn disk to boot (which it does on a ye olde XP machine!) and I'm not prepared to waste any more time on it.

Thank you so much for your assistance but there's obviously a very big hurdle that Canonical need to overcome before Ubuntu can be mass-market. It needs to just work.

---

### Post by RedMartin on 2013-06-18
Solved it. It was me all along! Using the Dell link above I set up a boot option for the DVD drive. What I didn't realise is that I needed a DVD in place at the time for the BIOS to add a third option to the set-up. Once I realised this and moved DVD up the boot order the live DVD worked fine.

My only issue now is that Win8 won't load unless secure boot is disabled. Is that an issue and anyone know how to fix it?

Again, thanks for all the help. I'm back in Ubuntu land and happier for it.

Finally, need to mark this solved. How?

---

### Post by oldfred on 2013-06-18
See my signature on Solved.

Not sure having secure boot on is all its cracked up to be by Microsoft.
       [http://www.zdnet.com/torvalds-clarifies-linuxs-windows-8-secure-boot-position-7000011918/](http://www.zdnet.com/torvalds-clarifies-linuxs-windows-8-secure-boot-position-7000011918/)
 the whole UEFI thing is more about control than security

---

### Post by RedMartin on 2013-06-18
Thanks again Oldfred. 

I've got both OSes running although there's a few Ubuntu issues to sort. Tinny sound, touchpad, no additional Nvidia drivers etc etc. I'll leave it all for now and just enjoy Ubuntu as it is.

---

