---
title: "InstallingPackagesViaCD"
date: 2011-09-04
forum: Installation &amp; Upgrades
---

### Post by bikewrecker on 2011-09-04
Hello all, I am relatively new to ubuntu so I need some help. (Using ubuntu 10.10)
I cannot connect to the internet via eithernet cable and am forced to use wifi, the only problem I'm having is that I cant get my computer's wifi card's driver to work on my ubuntu partition. I got the driver working on my windows 7 partition, (after about 6 hours of work due to lynksys not putting out new drivers for like 3 years) but I cant get the driver working on my ubuntu. 

Here's what ive done so far:
I went to look for a solution on the forums and the ubuntu help site and they say to download a package called ndisgtk or ndiswrapper or whatever works; however, without my wifi card working i cant connect to the internet to get the packages i need to get my wifi card working... so i found the following site:

[https://help.ubuntu.com/8.04/add-applications/C/offline.html](https://help.ubuntu.com/8.04/add-applications/C/offline.html) 

This says to burn an .iso image onto a CD or DVD then to get the packages off of that. The only problem is in the instructions it says to go to System > Administration > Software Sources; however, on my computer there is no "Software Sources" under the Administration tab.  What I did instead was go to the Synaptic Package Manager and search for "software." Software Sources still didn't come up  but Software-properties did so I went to my Terminal and opened that up and followed the rest of the instructions on the link i posted earlier. Now when I insert my new iso DVD when it tells me to insert my new iso DVD it gives me a warning that says, 

"**Error scanning the CD**
E:Failed to mount the cdrom."

I then messed around with the mount command for a bit and didn't get anywhere and I then decided it was time to ask y'all for some help. 

Thank you in advance!

---

### Post by mörgæs on 2011-09-05
You would do yourself a great service by installing by cable, if necessary by moving the computer to a place where you can borrow a connection. There are hundreds of bug fixes available for 10.10, some of which could be relevant for the wirefree internet access.

---

### Post by bikewrecker on 2011-09-12
So I had my buddy come over who is very good with linux, and it turns out that the reason I can't connect to the Internet isn't because the drivers for my wi-fi card weren't working, but because the signal was so weak that the ubuntu couldn't see any wifi hot spots. Got a repeater in the house and now it works just fine. 

The reason I couldn't get packages off of the CD was because I was running a 64 bit ubuntu and plugged in a 32 bit CD... duh! but the iso I downloaded was for "Intel CPUs" and the only ones that were 64 bit were for AMD 64 bit systems... because they don't think intel makes 64 bit CPUs? I just downloaded the AMD 64bit and it worked fine. Oh well. Got it all figured out.

---

### Post by mörgæs on 2011-09-12
Good that it works, please mark the thread 'solved'.

Yes, the names of the 32/64 bit ISOs are confusing. The 64 bit is not less suitable for Intel, though it says AMD in the name. 
[http://brainstorm.ubuntu.com/idea/7370/](http://brainstorm.ubuntu.com/idea/7370/)

---

