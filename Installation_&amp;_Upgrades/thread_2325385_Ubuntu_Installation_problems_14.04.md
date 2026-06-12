---
title: "Ubuntu Installation problems 14.04"
date: 2016-05-21
forum: Installation &amp; Upgrades
---

### Post by Duff1234 on 2016-05-21
I used to have ubuntu 14.04 installed on my computer that I built.  I then tried out installing 16.04 but they did away with my FLXGR graphics or something to that effect so I could not get the resolution that I wanted for my TV that it is hooked up to.  I then tried to reinstall 14.04 from my live USB that I keep on hand.  It installs just fine and it tells me to restart then remove my media.  I restart, access the bios and change the boot priority to the SSD that Ubuntu was installed on.  It then gives me the same error message no matter what I do, "restart and select proper boot device"  I have tried several times to erase the disk and install ubuntu again. Did not work.  I have tried following instructions for loading the live USB and doing boot repairs for recommended and advanced options. Neither work.  I have a URL showing whatever information the boot-info program provided 
[http://paste.ubuntu.com/16583836/](http://paste.ubuntu.com/16583836/) .  If anyone can assist me in trying to find out how to resolve it so I can get my system to boot again I would be very grateful!

---

### Post by Duff1234 on 2016-05-22
I seem to have solved my own problem.  I'm not sure why something changed but I will describe how I fixed it to help anyone else who might come across it.  

After scouring countless forums and options other people had tried for the same or similar problems, I found what solved it for me was changing my BIOS to boot only UEFI.  Previously it was set to boot UEFI + Legacy and it had been working for years that way but for some reason it would not work for me now when trying to reinstall Ubuntu unless I changed the BIOS to only boot UEFI without the support for legacy booting.  I hope this helps someone in the future without having to spend as many hours as I did searching for an answer.

---

