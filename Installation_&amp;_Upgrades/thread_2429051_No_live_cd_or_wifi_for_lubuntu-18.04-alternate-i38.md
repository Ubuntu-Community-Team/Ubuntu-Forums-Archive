---
title: "No live cd or wifi for lubuntu-18.04-alternate-i386 ?"
date: 2019-10-12
forum: Installation &amp; Upgrades
---

### Post by vayira on 2019-10-12
Wanted to try lubuntu-18.04-alternate-i386 on an old netbook but it just straight into installation. Is that right? Also the installer says it is configuring the network but it seems to ignore wifi. 

I am missing something?

---

### Post by Skaperen on 2019-10-12
maybe it does that if there is not enough RAM to support a live system.  netbooks tend to be rather small.  years ago i had one with only 256M on it.

---

### Post by vayira on 2019-10-12
Its got 1g RAM and booted up lubuntu 14.4 live fine. 

It's just there are screen resolution issues with 14.4 so i thought i'd try 18

---

### Post by Skaperen on 2019-10-12
i wonder if, perhaps, it needs or wants more than 1GB.  can you boot that same ISO on a larger PC just to verify it can let you choose to go to Live/Try?  i don't know if Lubuntu is built different, but i would hope so, since its lighter size should let you run on smaller machines.  i only ran text mode on my netbook so my experience won't be helpful.

---

### Post by guiverc on 2019-10-12
"[COLOR=#333333][FONT=Ubuntu]Alternate ISOs are for low-RAM PCs. Computers with less than 700 MB of RAM are considered low-RAM computers. " [/FONT][/COLOR][https://help.ubuntu.com/community/Lubuntu/Alternate_ISO](https://help.ubuntu.com/community/Lubuntu/Alternate_ISO)

They use the text installer, and do not have a LIVE system; they aren't intended to (that'd require LIVE + installer needing more RAM defeating the purpose of the alternate installer).  The alternate ISOs may not recognize all hardware the "live" or normal ISO will, as it's more akin to the server (debian) installer (with same limitations).

Probably the best link is [https://help.ubuntu.com/community/Lubuntu/Documentation/AlternateInstall](https://help.ubuntu.com/community/Lubuntu/Documentation/AlternateInstall)  but with 1gb I'd use the normal installer.  I have 1gb machines I test Lubuntu with (including up to Lubuntu 19.04) and don't use the alternate installer.

---

### Post by vayira on 2019-10-12
> **guiverc said:**
> "[COLOR=#333333][FONT=Ubuntu]Alternate ISOs are for low-RAM PCs. Computers with less than 700 MB of RAM are considered low-RAM computers. " [/FONT][/COLOR][https://help.ubuntu.com/community/Lubuntu/Alternate_ISO](https://help.ubuntu.com/community/Lubuntu/Alternate_ISO)

They use the text installer, and do not have a LIVE system; they aren't intended to (that'd require LIVE + installer needing more RAM defeating the purpose of the alternate installer).  The alternate ISOs may not recognize all hardware the "live" or normal ISO will, as it's more akin to the server (debian) installer (with same limitations).


Ok that clarifies it. Anyway it has installed fine. The text installer was a bit clunky, especially for partitioning,  but it got me there. I didn't find it easy to find the right versions for download on the lubuntu site, that's why I ended up with that one.

---

### Post by guiverc on 2019-10-12
> **vayira said:**
> I didn't find it easy to find the right versions for download on the lubuntu site, that's why I ended up with that one.


I don't know which site you're talking about, the main reason for this reply is be-careful you go to the official Lubuntu site ([https://lubuntu.me/](https://lubuntu.me/)) and if unsure, do **not** use a search engine/google, but search ubuntu.com for any Ubuntu flavor where you'll be taken to [https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours) which will take you to the official site which is owned by Ubuntu or the official flavor team.  Unofficial sites tend to offer ISOs the official site will not offer, and as we have no control over what they do provide - they *may* or *may-not* be the same as official ISOs.

There are many unrelated sites offering Lubuntu for download. Lubuntu's official site is english only (support is available in other languages but lubuntu.me is english only) so searches in languages other than english tend to get unofficial listed higher in google, but even in english sites which allow advertizing (the official site doesn't) mean google tends to favor unofficial sites that may or may-not offer valid ISOs.  

Unofficial sites (referred to as 'fan' sites by team members) tend to offer older advice; and the alternate installer was last produced 2018-April so later builds of 18.04 LTS are not offered for it.  This shouldn't be a problem as it's usually used on older hardware, so HWE kernel won't likely offer greater functions, but it will mean far more updates are required to bring you up-to-date.

---

### Post by mörgæs on 2019-10-13
Good that you got the problem solved. Please mark the thread so.

---

### Post by vayira on 2019-10-14
> **guiverc said:**
> I don't know which site you're talking about, the main reason for this reply is be-careful you go to the official Lubuntu site ([https://lubuntu.me/](https://lubuntu.me/)) and if unsure, do **not** use a search engine/google, but search ubuntu.com for any Ubuntu flavor where you'll be taken to [https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours) which will take you to the official site which is owned by Ubuntu or the official flavor team.  Unofficial sites tend to offer ISOs the official site will not offer, and as we have no control over what they do provide - they *may* or *may-not* be the same as official ISOs.


oh dear I download the iso from [https://lubuntu.net/](https://lubuntu.net/) is that not bona fide?

---

### Post by PaulW2U on 2019-10-15
> **vayira said:**
> oh dear I download the iso from [https://lubuntu.net/](https://lubuntu.net/) is that not bona fide?
The download links *[SIZE=2]seem[/SIZE]* to point to official ISO images but the Lubuntu Team manage [https://lubuntu.**me**](https://lubuntu.**me**).

The link on [https://ubuntu.com/#download](https://ubuntu.com/#download) also points to [https://lubuntu.**me**](https://lubuntu.**me**) which is hosted by Ubuntu/Canonical unlike the .net site.

---

### Post by mörgæs on 2019-10-15
The risk of downloading a flawed ISO file is close to nil. If in doubt you can do the [md5 test]("https://help.ubuntu.com/community/Lubuntu/Documentation/CheckISO_CD#Check_the_iso_file").

A lot of bad things can be said about lubuntu dot net but after all he does not distribute malware.

Again, please mark the thread solved.

---

