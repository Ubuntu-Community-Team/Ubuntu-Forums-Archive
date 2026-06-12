---
title: "VT1300 video card does not work with Ubuntu"
date: 2007-09-23
forum: Installation &amp; Upgrades
---

### Post by Kevin Jones on 2007-09-23
Hello all,
I have a dell xps 210 with Ubuntu nicely installed in a partition.
I put in a video card ..Radeon VT1300.
Window (vista) can recognize the card but....
Ubuntu does not recognize the new card.
I installed the hardware with the disk, I  cannot remember removing any drivers,(I have never removed a driver, so I perhaps I did) 
Is there any way I can get Ubuntu to recognize the new hardware?

kevin Jones

---

### Post by Pumalite on 2007-09-23
Get the Alternate CD and at the end of the installation I'll help you configure your xserver. I don't see another solution, unless you want to go back to the shop and exchange your ATI for an Nvidia.

---

### Post by Kevin Jones on 2007-09-23
Pumalite,

I am beginning to regret getting the Vtek card.
I have gone to this page..[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
I checked the radio button for Alternate CD (which is text based)
It is downloading now. I will get back to you, You may need to help me with the burn, since I have never been able to burn on this  pc. I do have a second PC that is connected to the internet in case this one really crashes.
Thanks for the help
will be in touch

kevin

---

### Post by Pumalite on 2007-09-23
[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

---

### Post by Kevin Jones on 2007-09-23
Pumalite,
I have the cd burned Ubuntu 7.04-alterante-I386.
Is there anything I should do apart from rebooting from disk and following the instructions. I have already downloaded unbuntu twice. will I get a fourth partition?
Any way, let me know if there is anything I should look out for, and when to stop installing and concentrate on the video card

kevin

---

### Post by Pumalite on 2007-09-23
Make sure your partition is clean. The problem with your video card you'll have it at the end when you end up without xserver. Then post back.

---

### Post by Kevin J on 2007-09-24
I have the alternate cd and am ready to install
which option should I use to install.
Install in text mode
text mode install for manufacturers
rescue a broken system
memory test 
boot from first hard disk.
?

I am guessing it should be the 'install in text mode"

thanks 
Kevin Jones

---

### Post by Pumalite on 2007-09-24
Text Mode. Make sure you did an md5sum on iso before burn.

[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

---

### Post by Kevin J on 2007-09-24
Install is hanging after the following:

Sending SIGKILL to all processes
Please stand by while rebooting system
[3003.574795] synchronizing SCSI cache for disk sda
[3003.595121] ACP1:PXI  interrupt for device 0000:00:19.0 disabled
[3003.6109701] restarting system.

the message has been there for thirty minutes
should I reboot?

Thanks  for the help

Kevin J

---

### Post by Pumalite on 2007-09-24
At this point it looks to me as a no go. Someone will have to chime in.

---

### Post by Kevin J on 2007-09-24
Thanks for the help,
can anyone help me open ubuntu iwth a vtek 1300 video card?
I am hoping that the next release of ubuntu may be handle this issue. But in the  meantime, can anyone help me to configure the video card

Kevin

---

### Post by Kevin Jones on 2007-09-25
I have rebooted, and I am back to my original position of Ubuntu not recognizing any video. Is there any way to get Ubuntu to recognize my new video card now that I have installed the alternate cd?

Kevin

---

### Post by Pumalite on 2007-09-25
According to post # 9 you have not installed yet. If I'm wrong, please explain:

'Install is hanging after the following:

Sending SIGKILL to all processes
Please stand by while rebooting system
[3003.574795] synchronizing SCSI cache for disk sda
[3003.595121] ACP1:PXI interrupt for device 0000:00:19.0 disabled
[3003.6109701] restarting system.

the message has been there for thirty minutes
should I reboot?'

---

