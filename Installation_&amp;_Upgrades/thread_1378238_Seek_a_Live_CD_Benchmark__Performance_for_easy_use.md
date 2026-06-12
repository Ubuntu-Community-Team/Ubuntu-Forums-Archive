---
title: "Seek a Live CD Benchmark / Performance for easy use."
date: 2010-01-11
forum: Installation &amp; Upgrades
---

### Post by zongpog on 2010-01-11
Dear everybody,

  I am close to buying a second hand laptop from a shop nearby and they have several notebooks.

I would like to check that some of these systems are 

i) capable of running Ubuntu smoothly and

ii) because the same models of the laptops can come with different hardware, be able to verify which hardward (e.g graphics cards) are installed.

To this end, I seek a Live CD that can accomplish this and will produce meaningful & quick to interpret results.  I won't have the time, nor the patience of the vendor, to compare Mb/s disc through-put across ten machines in the shop.  I would like to have a simple set of results:
  * Yes this can run Ubuntu 9 without Compiz and watch youtube, 
  * The hard disc is PATA connected to a SATA interface. (as in the Thinkpad R51)

Any clues?

Yours faithfully, z

---

### Post by zongpog on 2010-01-12
Sorry to bump this thread, but did anyone have any ideas.  

Does Ubuntu 9 have a live CD option on it, and also the ability to verify hardward inside the target system regarding compatibility and performance?

---

### Post by tommcd on 2010-01-12
> **zongpog said:**
> 
Does Ubuntu 9 have a live CD option on it, and also the ability to verify hardward inside the target system regarding compatibility and performance?
Ubuntu has always had a live CD. Starting with Dapper 6.10, or Edgy 7.04, (iirc) the Ubuntu live CDs can also be used to install Ubuntu.
For verifying hardware compatibility, just boot up the Ubuntu live CD in the store and verify that everything works. You should at least be able to determine if the video, sound, and wired networking all work from the live CD. (Note that running the live CD will require you to set the laptop's BIOS to boot from the cdrom as the first boot device).
While on the live CD, open a terminal and run: **lspci -v**. This will list all hardware that Ubuntu recognizes. Also go to: system > administration > hardware drivers, and see if Ubuntu offers to install any proprietary (nvidia, ati, atheros etc) hardware drivers.  
Take note of the wireless device the laptop has. It should be near the end of the output of lspci. Wireless is the thing you would most likely have to fiddle with to get it to work. 
To see what modules Ubuntu has loaded, run **lsmod**. See if Ubuntu has loaded modules for the wireless. 
A quick google search should determine if the wireless card works in linux. Most wireless devices can be made to work in linux these days. Some just require more work than others.

As for compiz, many people use compiz on netbooks that have intel graphics. If you want really good performance with compiz and 3D, get a laptop with a nvidia graphics card if you can. ATI can be more difficult to get proprietary 3D drivers installed, although it is usually possible to enable 3D with ati.

Any modern laptop will be able use flash and watch YouTube videos, so that will not be a problem.
Hope this helps.

---

### Post by zongpog on 2010-01-12
Dear Tom,

  This certainly does clarify the process and does help.

Best regards, 
z

---

