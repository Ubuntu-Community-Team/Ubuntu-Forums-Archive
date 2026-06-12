---
title: "New to Kubuntu  - Installation Problems"
date: 2006-06-26
forum: Installation &amp; Upgrades
---

### Post by DerAndere on 2006-06-26
I downloaded the Live CD File to my notebook just to take a look at it.
Burned  it to CD, and tried. 

The burning program gave me some weired Error concerning the tracklength of the downloaded image. (I just clicked "ignore").

I restarted the computer to boot from CD. I get the first "start screen" without any problems. But as soon as I try to Start Kubuntu the installation gives me an error message saying: 

I/O error
Error reading Boot CD
>>Reboot<<
:-k 
Can anyone help me out on this one?

---

### Post by tonyr on 2006-06-26
This sounds like a bad cd image.  The download site should have had a file called
**md5sums**, or some refence to md5sums.  You should run an md5sum program
against your downloaded image.  If you are burning the CD image from Windows,
read [this]("http://psychocats.net/ubuntu/iso.html") and/or [this]("http://www.users.bigpond.net.au/hermanzone/p17.htm").

If you are using another Unix/Linux system use the program **md5sum**.

Check the result against the checksum value in the **md5sums** file.

---

