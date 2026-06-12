---
title: "Please help - How long should Ubuntu Install? Curser is just rotating forever."
date: 2012-08-17
forum: Installation &amp; Upgrades
---

### Post by WindsOfChange on 2012-08-17
Hi members,

I am in the process (I think) of installing Ubuntu 12.04 using the Cd I created from the ISO Image that was downloaded from Ubuntu's download page.

I had a consistent error message that I'm sure everyone has encountered that said something like, "Unrecoverable error encountered... etc"

I did find what I think was a fix on a previous post by a member that advised readers to get rid of the slideshow during installation. My assumption is that the slideshow was causing the error message. If the slideshow was working as normal my assumption would be that while the install files installing, the slideshow is suppose to inform you and perhaps teach you some things about Ubuntu. 

Anyway... to remove the slideshow, the post said to go to "terminal" and type in the following command:

sudo apt-get remove ubiquity-slideshow-ubuntu
source: [http://ubuntuforums.org/showthread.php?t=1966588&page=2](http://ubuntuforums.org/showthread.php?t=1966588&page=2)
This is page 2 of 3

Ok, here's where it gets weird. I followed the suggestion and did finally make it past the point where the usual "error message" would appear but the installation curser (little rotating circle) just keeps rotating and there is no activity in regards to the hard drive light on my computer. The hard drive light is not blinking which (to me) is indicating that nothing is being written to the hard drive. Also, the CD light on the drive is not blinking which tells me nothing is happening. In other words there are NO lights "on" or "blinking" on the CD drive or the Hard Drive.

Its been well over 1 1/2 hours and the the curser (pointer) is still rotating. Any suggestions or advice as to what is going on?

Been at this all day yesterday and all morning so far. Just trying to get Ubuntu installed.

System:

iWill DVD266R motherboard Dual processor Pentium III cpu's total 2 GHz cpu
1 gig DDR memory
Installing Ubuntiu on a separate 80 gig hard drive

This is the tutorial I am following to install and dual boot Ubuntu with Windows 2000 (yes, still running windows 2000 on this machine :-)

[http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/](http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/)

Thank you kindly.

---

### Post by oldfred on 2012-08-17
If I get an unrecoverable error, I assume something major is wrong with CD or system. I would first double check that ISO matched md5sum, then reburn CD at slowest speed or if system allows use USB flash drive. I do not normally get unrecoverable errors.

Install time depends on CD read speed, amount of RAM, and if including updates as part of install, your Internet speed. 

Years ago I did get a full version of Ubuntu into a old laptop with less memory than allowed (did not know better then), but I had to leave it overnight. I think the only reason it worked was that swap already existed and is was using the swap to "speed" up the install and make up for missing RAM. Updates then took another overnight. Never did know how long but it was many hours. System worked but too little RAM made it non-functional. Lighter weight Linux systems did then install & work much better.

With my 4GB RAM 6 year old system I have install anywhere from 10 minutes from hard drive to SSD with no updates to about half an hour USB to hard drive, no updates. All installs are with partitions already created so that is not in my time. Updates can vary all over the place as Internet speed and how much needs to be updated.

---

### Post by 2F4U on 2012-08-17
Depending on how fast the machine is the installation should usually take no longer than half an hour or so. Personally, I never had a problem with the slide show on any computer I installed, so I don't think that is the reason for your problems.
My first question would be whether you verified the checksum of the downloaded iso file. It often happens that the iso file get corrupted during download, resulting in problems during installation. Second idea is to burn the iso at the lowest speed to disk.
Third question is whether you have a working network connection during installation. If you choose to install updates or restricted extras during the installation, you need a working network connection. At several occasions, I had problems if one of these options or both were enabled, so I would suggest to disable them and try again.

---

### Post by WindsOfChange on 2012-08-17
Thank you oldfred and 2F4U

Oldfred said:

[COLOR=Blue]>>>I would first double check that ISO matched md5sum, then reburn CD at slowest speed.[/COLOR]

How do I check that ISO matched md5sum? Please explain in laymen's terms. Thank you very much. 

2F4U said:

[COLOR=Blue]>>>My first question would be whether you verified the checksum of the  downloaded iso file. It often happens that the iso file get corrupted  during download, resulting in problems during installation

[COLOR=Black]Likewise, how do I verify the checksum[/COLOR] [/COLOR]of the  downloaded iso file? It apparently copied to the CD without a glitch. In fact my CD burner checked for errors before burning and found none.

I also have 1 (one) gig of ram installed so that should not be an issue.

Thank you.

---

### Post by Jt00 on 2012-08-17
[This page]("https://help.ubuntu.com/community/HowToMD5SUM/") describes how to check the md5sum very well. In layman's terms, it makes sure you downloaded the full iso file and not a partial or corrupted file. Once you get the md5sum, check it against the one posted on the Ubuntu website.
Since your cd burner does not have access to the Ubuntu md5sum postings, it may tell you the iso burned without an error, but if you burn a corrupted iso perfectly, it's still corrupted.


I'm not sure about checksum, I think it's another way of verifying the file's integrity.

---

### Post by WindsOfChange on 2012-08-17
Thank you jt00,

>>>[COLOR=Indigo][This page]("https://help.ubuntu.com/community/HowToMD5SUM/")[/COLOR][COLOR=DeepSkyBlue] [COLOR=Blue] describes how to check the md5sum very well. In layman's terms, it  makes sure you downloaded the full iso file and not a partial or  corrupted file.[/COLOR][/COLOR]

That was surely an extremely detailed "how-to" in regards to md5sum. Before I embark on that journey I will first clean house and free up some space, defrag my hard drive and download the Ubuntu iso image file again. I remember it took forever to download the file originally. I understand it is a large file but I am simply going to download the Ubuntu iso file again and see if it makes a difference when I burn it to a CD and install it (again).

Thank you.

---

