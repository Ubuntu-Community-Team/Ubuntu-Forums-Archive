---
title: "No Internet After Updates!"
date: 2008-06-02
forum: Installation &amp; Upgrades
---

### Post by Zero_Cool on 2008-06-02
Getting a little frustrated with internet and Ubuntu!!!! Currently running Dual-Boot with this so called stable OS called Windows XP!! lol Anyways... I installed ubuntu and upgraded to 8.04 (which isn't working) and wanted it off my computer, well when i went to reinstall 7.04 and try to overwrite it, it stayed and still will not load all the way, (8.04 to clarify). Now i have Ubuntu 7.04, 8.04, and XP all on the OS Boot, and i have had internet problems before with 7.04, but all was working good before i installed updates then everything went down from there. I have the Realtek RTL8168/8111 PCI-E Gigabit Ethernet NIC... Which is pre-installed/connected to my MSI Motherboards ([http://www.newegg.com/Product/Product.aspx?Item=N82E16813130057](http://www.newegg.com/Product/Product.aspx?Item=N82E16813130057))
Any suggestions on what to do???



*Edit (I still want to uninstall 8.04 too if any help with that also!)

---

### Post by Zero_Cool on 2008-06-02
Any help?!

---

### Post by jualin on 2008-06-02
If you have a separate /home partition you should burn a new live CD and just install Ubuntu 8.04 and format the "/" partition. I dont know why the Ethernet is not working properly, how about you give it a try with a LiveCD, usually ethernet cards work almost out of the box, especially Realtek ones which are very common. My suggestion is to stick a Live CD on your computer to test the internet with it and then just install it if everything works fine.

---

### Post by tropdoug on 2008-06-02
Hi there

not sure if this will help I am pretty new to Linux too. Is there a reason that you haven't tried gutsy gibbon (Ubuntu 7.10) I am currently using that, and advice from this forum, is probably to wait off a while before upgrading to 8.04 cos its still a little buggy. 

 If you decide to install 7.10, either make or use the live cd and _**Carefully**_ format the partition/s that do not contain your XP setup. Make two ext3 partitions one for / (root) and one for /home and allow the system to make the swap partition as normal. This way if you stuff your system later on whilst playing (something I have done a few times now lol), you can simply reinstall without losing any data or settings stored on your /home partition.

Then once your in, follow the directions here, to enable your internet and set your browser correctly. 

[http://ubuntuforums.org/showthread.php?t=759250](http://ubuntuforums.org/showthread.php?t=759250)

Hope that helps.

---

### Post by Zero_Cool on 2008-06-03
Well before i upgrade to 8.04 i was on 7.10 which worked fine, but after upgrading to 8 everything crashed from there, which is why i reinstalled 7.04, i have the livecd for 7.04 so was just gonna upgrade from that to 7.10.

---

### Post by tropdoug on 2008-06-03
well I guess that the same should apply with 7.04. have aread of my thread in relation to the internet stuff. if I can help just post.

---

### Post by alguin2 on 2008-06-03
Did you try a powerdown/unplug/wait30secs/reboot sequence to see if 8.04 came up with the network?  My PC came with the Realtek RTL8168C/RTL8111C PCI-E Gigabit Ethernet NIC,
which couldn't come up after 8.04 installation.  

Check exactly which card you have, and if the updated Linux driver from realtek (at **[http://www.realtek.com.tw]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#2") **) is needed to be recompiled and included into the 2.6 kernel (used by Ubuntu 8.04). 

If so, please follow the instructions at:
 **[http://ubuntuforums.org/showthread.php?t=799662&page=2]("http://ubuntuforums.org/showthread.php?t=799662&page=2")**


Hope this was helpful.

---

### Post by Zero_Cool on 2008-06-04
K update from working on, 8.04, when i get it to run, internet works just fine, it recognizes the ethernet cards and runs normally, but when i switch over to 7.04 it knows the cards are there, but doesnt pick up that the line is connected. there are 2 ethernet plugs in the back, PCI-E and Family regular one, when plug into the main PCI-E one no lights on the back and acts like the hole is just an empty place to put the cable into. When plug into the other one it recognizes that its plugged in but doesnt give out internet. Tried the powerdown, left off all night unplugged. Tried your forum Trop, and still nothing. anymore suggestions?? would really like to get back on track with linux!!

---

### Post by tropdoug on 2008-06-04
Sorry mate, your beyond my tiny bit of knowledge now. Have you checked the /var/log files to see if there is a generated fault log relating to your card or the net? (don't ask me what it would be called) 

have you looked in System>administration>network or system>administration>network tools and tried to see if there is a relevant setting to your card in either of these? in 7.10 you can use the ping utility from the gui to see if your connecting to the wan.

Other than those I am out of suggestions except maybe re posting the question on the 'network and wireless  threads which might elicit more knowledgeable help. 

Keep at it, it is worth it in the long run.

---

### Post by Zero_Cool on 2008-06-08
Well been away for a couple of days, got on and tried everything but nothing seems to work.. anything else?

---

### Post by tropdoug on 2008-06-09
what version OS are you running now? did the updates all download and can you ping any addresses?

are you using a router?

---

### Post by Zero_Cool on 2008-06-09
im still on 7.04 i updated about 212 updates when i first re-installed, and internet worked fine, just after those updates, it can't recongnize even that cord pluged in, but it notices the Network Card. I usaully do not use a router but for this week i will. same thing tho when tried again.

---

