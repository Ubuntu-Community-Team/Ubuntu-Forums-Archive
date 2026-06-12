---
title: "My Lenovo requires a windows installation?"
date: 2016-04-23
forum: Installation &amp; Upgrades
---

### Post by izznogooood on 2016-04-23
Well, it seems that way. I´ve been trying different solutions all weekend.
I can not install (ANY) Linux on the _**entire disk **_(Along side works fine). I have to have a windows installation!
When i say everything I mean everything:
[LIST]
[*]Every possible BIOS settings (CSM, SECURE BOOT, etc etc etc)
[*]Tried installing on another HDD (Replacing SSHD)
[*]Different installation media (DVD, USB, Originals)
[/LIST]
As long as i have Win10 on the drive, I can install every linux out there... (Along side)

This is VERY frustrating to say the least!

This is a Lenovo K450 Desktop: [http://support.lenovo.com/no/en/products/desktops-and-all-in-ones/ideacentre-k-series-desktops/ideacentre-k450-desktop?c=1&beta=false](http://support.lenovo.com/no/en/products/desktops-and-all-in-ones/ideacentre-k-series-desktops/ideacentre-k450-desktop?c=1&beta=false)

---

### Post by QDR06VV9 on 2016-04-23
Hi izznogooood it can be done.
By creating an UEFI boot usb stick and boot from that.
[https://www.thomas-krenn.com/en/wiki/Creating_Windows_UEFI_Boot-Stick_in_Windows](https://www.thomas-krenn.com/en/wiki/Creating_Windows_UEFI_Boot-Stick_in_Windows)
Good luck

---

### Post by izznogooood on 2016-04-23
I think you misunderstood?

I can make and boot a UEFI usb just fine, but the installation wont boot after the install finishes :(
Or are you saying this guide is different from others programs such as Rufus ?

---

### Post by izznogooood on 2016-04-24
Maybe the moderator can move this to Installation? I do however think this is a BIOS issue.

---

### Post by jeremy31 on 2016-04-24
"*Thread moved to **Installation & Upgrades**.*" as requested

---

### Post by QDR06VV9 on 2016-04-25
> **izznogooood said:**
> Maybe the moderator can move this to Installation? _**I do however think this is a BIOS issue.**_
I would also agree..The link i had sent you earlier is a bit complex, and not very transparent as per what to do.
Later when I can get some free time I will try this myself and if satisfied with the results i may put a how to in the tutorial section in the forum.
But I know for your machine(Specs) most of the folks having issue's with not booting after installing were due to not having **"Fast Boot"** or **"Fast Start Up"** disabled.
Regards

---

### Post by grahammechanical on 2016-04-25
> I can install every linux out there... (Along side)

I am curious. Are you not getting the Erase disk and install Ubuntu option? If you are getting it, what happens when you select it? Likewise, with the Something Else option?

I have heard that some motherboard manufacturers go against the UEFI specification and fix their UEFI boot system so that it only loads an OS that is labelled Windows. I have heard there is a way around that. Is that the situation?

Regards.

---

### Post by izznogooood on 2016-04-25
> **runrickus said:**
> I would also agree..The link i had sent you earlier is a bit complex, and not very transparent as per what to do.
Later when I can get some free time I will try this myself and if satisfied with the results i may put a how to in the tutorial section in the forum.
But I know for your machine(Specs) most of the folks having issue's with not booting after installing were due to not having **"Fast Boot"** or **"Fast Start Up"** disabled.
Regards

Hm, I never disabled that! Im not going through this again, so there will be a while until I can test this. But I will remember that...
I just needed (felt I) a fresh install after all the testing i did in the 16.04 Beta... (And I only use win in VM)

This is not a space issue, I just dont like being forced to have a Windows installation.

And thank you for the link, theres just not enough time between work and kids to do a lot of testing anymore, thats why i choose Ubuntu ;). (Not that this is their fault!)

> **grahammechanical said:**
> I am curious. Are you not getting the Erase disk and install Ubuntu option? If you are getting it, what happens when you select it? Likewise, with the Something Else option?


I get all the options, and it installs fine (nothing indicates otherwise). It just wont boot. Even if I set up the partitions my self...

> error 1962: No operating system found

> **grahammechanical said:**
> I have heard that some motherboard manufacturers go against the UEFI specification and fix their UEFI boot system so that it only loads an OS that is labelled Windows. I have heard there is a way around that. Is that the situation?

My thoughts exactly...

---

### Post by QDR06VV9 on 2016-04-25
> **izznogooood said:**
> Hm, I never disabled that! 
Maybe then?
> error 1962: No operating system found
Is the error they reported with Fast boot still enabled.
Sorry i never posted that earlier but with your experience I **assumed **you already did that.:confused:
From what i understand windows 10 just hibernates with a shut down.
EDIT: Yes grahammechanical has a good point I put a 600MB partition in front of the other partition's.

---

### Post by izznogooood on 2016-04-25
> **runrickus said:**
> Sorry i never posted that earlier but with your experience I **assumed **you already did that.:confused:.

Turns out i don't have "Fast boot", I have something called "Quick boot" which i believe is something related to self testing of RAM etc... (I tried turning that off now resulting in a nice "beep" like a 0x86 after boot :popcorn:) 

As for my experience, lets just say there where no UEFI the last time I had to play around in the BIOS settings.

---

### Post by QDR06VV9 on 2016-04-25
> **izznogooood said:**
> Turns out i don't have "Fast boot", **I have something called "Quick boot" which i believe is something related to self testing of RAM etc**.ets just say there where no UEFI the last time I had to play around in the BIOS settings.

Yes Pretty close.
> Using Quick Boot Feature of the BIOS

All systems initialize in more or less the same way. During the POST mentioned earlier, the BIOS checks the hardware devices and counts the system memory. Out of all the different types of system memory, the random access memory, better known as RAM, takes the longest to be checked. Checking the RAM takes time, and on a machine that has large amounts of RAM, this calculation can take several seconds. For example, a machine that has 512MB of RAM may take up to three seconds just to check the memory. On top of the RAM counting, a few other tests need to be done because your computer wants to make sure that all the hardware in your computer is working properly.

The complete version of these tests is not needed every time you boot and can be turned off to save time. Most system BIOSs offer a feature called Quick Boot. This feature enables the user to turn off the full version of the test and sometimes enables you to run a shorter quick check test instead. Other BIOSes allow you to turn off the Memory Check only, which will still cut down on a lot of time.


UEFI has been a real learning curve for myself also.:D

---

