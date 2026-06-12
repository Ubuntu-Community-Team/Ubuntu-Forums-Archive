---
title: "Could downloading the Ubuntu ISO behind a router corrupt my Ubuntu CD?"
date: 2007-03-04
forum: Installation &amp; Upgrades
---

### Post by elitelinuxnoob on 2007-03-04
This is my last post and if I dont get help which solves this issue then im only left to sticking with Windows so please give me every thing you have of your knowledge to help me get Ubuntu Live CD to work. I have tried the alternate and regular 6.10 and Kbuntu but they all give me installation issues. 

For alternate is says, "Incorrect CD-ROM detected! The CD-ROM drive contains a CD which cannot be used for installation" WHY? THE CD IS IN!

For 6.10 desktop and Kbuntu I always freeze after the loading Ubuntu bar with a part of a corrupted window. I have tried Boot: live vga=771 noapoc nolapic ,and live acpi=off but still get freezes. Is there more commands to try that work? I also tried safemode but I still get freezes.

Furthermore I redownloaded and reburned ISOs but nothing so I dont think that's it.
Could it be that im downloading the ISOs behind a router? I get them from Ubuntu's site too so they have to be legit.

I appreciate all the help you can give
Thank you

---

### Post by bruenig on 2007-03-04
Are you burning the isos as data or images.

---

### Post by elitelinuxnoob on 2007-03-04
ISOs

---

### Post by aysiu on 2007-03-04
I've downloaded from behind a router and *have* had some corrupted ISOs. But I've also had some good ones. Sometimes downloading via BitTorrent helps to keep the integrity of the image.

You may also want to check the integrity of the ISO before you burn it. More details here:
[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

---

### Post by Coelocanth on 2007-03-04
I'm behind a router and I've DLed a couple dozen ISOs in the last couple months and every single one of them that verified with the md5sum has worked.

---

### Post by aberry5555 on 2007-03-05
If you're using windows XP to burn the CD I suggest trying this tool, as it's worked every time for me. install this:

[http://isorecorder.alexfeinman.com/download/ISORecorderV2RC1.msi](http://isorecorder.alexfeinman.com/download/ISORecorderV2RC1.msi)

and then, once installed, right click on your ubuntu .iso file and click "copy image to cd".

it will come up with a dialogue box, one part about the .iso file and another part about the recorder. In the part about the recorder click "options" and move the sliding scale as far left as possible (this will set the burn speed to slow) to ensure a good copy.

Now press OK and let it burn the CD.

---

