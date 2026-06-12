---
title: "ubuntu won't boot up on dual boot"
date: 2016-02-25
forum: Installation &amp; Upgrades
---

### Post by spencer2 on 2016-02-25
i just got a new laptop --- its an acer aspire F15, F5-571T-569T. 
Win 10, 1Tb hd, I'm doing a partition and dual boot; 150g to Win, 850g to Ubuntu. Downloaded iso from ubuntu official site, burned to disc, ran and installed, went through partition set up and ubuntu install; but upon reboot never got OS boot option and each time I boot up it goes straight to Windows. I did piggy-back a previous post:

[http://ubuntuforums.org/showthread.php?t=2314730](http://ubuntuforums.org/showthread.php?t=2314730)

Got a tip, used link: 
[http://ubuntuforums.org/showthread.php?t=2147295](http://ubuntuforums.org/showthread.php?t=2147295)

I went to that link but there is a lot of info on that page so I would greatly appreciate some more help please (& thank you). 
Since my laptop isn't giving me a OS choice, I can't use terminal to download any boot managers... Help would be appreciated.

---

### Post by spencer2 on 2016-02-25
As I'm reading the UEFI link page, maybe an important caveat is that I've already installed ubuntu and done my partition split. It looked like the UEFI directions are more for if ubuntu is not yet installed. 
again, any help would be greatly appreciated: thank  you.

---

### Post by grahammechanical on 2016-02-25
> It looked like the UEFI directions are more for if ubuntu is not yet installed.

That is so that we avoid situations like this. Windows 10 will surely have been installed in EFI mode. So, the question is, did you install Ubuntu in EFI mode or in BOIS/Legacy/CSM mode.

It is time you became familiar with Boot Repair. We can download & install it in a live session. Run the option to get a Bootinfo summary. You will be given a URL to where the Bootinfo summary is stored at pastebin. Place the URL in this thread and we can then click in it a see for ourself the summary.

Boot Repair also has an option to fix certain boot problems. You might want to wait for advice before you accept that option. Or, you can judge for yourself.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Regards.

---

### Post by spencer2 on 2016-02-25
awesome; I'm not at all surprised that I screwed this up somehow. OK --- a couple of things. While I'm reading and trying to run the bootinfo summary: 
1) When i go into the disk manager I do see the partition and I did originally start there but I can't seem to shrink the partition as much as I want (the cap was roughly 450000m out of the 950000 available): is that a problem?
2) I have the bios settings opened and read some about changing login permissions; if i do that in the bios will that do anything good?
3) since i just got the laptop there is no important data that I need; do i need to run the usb backup option in the Win main menu section?

I would like feedback on the info that I get so I would appreciate further help --- and this maybe a stupid question, but how do i go about the boot repair in a "live session" (i'm unclear on the specific jargon meaning of the term "live session"). 
thank you again and am reading boot repair link now

---

### Post by spencer2 on 2016-02-25
my first question is, it seems like the boot repair info is done in ubuntu; i can't get to ubuntu -- it doesn't boot --- all i have is win10.

---

### Post by spencer2 on 2016-02-29
Does anyone have any tips on how I can fix my issue? 
I still can't boot into ubuntu (so i can't do the ubuntu boot repair). 
Is there a way to go into my uefi settings and just change the password enable/disable thing and be able to boot into ubuntu?
If not, can I just delete the partition and start again?
If that is an option?

---

### Post by oldfred on 2016-02-29
Your first link on Acer and setting password and then you can set "trust" on the Ubuntu/grub efi boot files.
Many posts show details. I do not have Acer but many have had issue and followed procedure to resolve it.

---

