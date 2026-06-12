---
title: "Should I use Ubuntu as host os"
date: 2008-02-07
forum: Installation &amp; Upgrades
---

### Post by KcAV on 2008-02-07
I would like to explorer alternative configurations and trouble shoot Windows XP Professional in a virtual environment.   I am trying to decide which os to use as the host os.  

It seems reasonable that since the guest must execute on the host that the host needs a clock rate at least equal to the quest.  But I sence this is an over simplification of the issues envolved in selecting a host operating system for running vrtual environmements. Could someone enlighten me about virtualization issues and alternative solutions?

Should I run Ubuntu 7.4  instead of Windows as the host os?

Should  I  use VMware Workstation 6.0.2 for Linux to create virtual environmnets in which I run Windows XP and Windows XP 64-bit as quest operating systems inside those environments?


KC

---

### Post by zvacet on 2008-02-07
You should be fine runing Windows in VMware.Do you have Ubuntu installed already?VMware Workstation is commercial product.You can get Vmware server for free,but you can read about that on VMware site.If you have Ubuntu installed you have vmware-server in synaptic.All you need is serial number.if you decide to install vmwae-server let me know and I can give you serial.My answer is bit confused because i don´t know what are you looking for and what is your plan with virtualisation.

---

### Post by KcAV on 2008-02-08
Thank you for replying to my post. I appreciate your interest, and I have a lot of questions.

In your reply you said,” I don´t know what are you looking for and what is your plan with virtualization?”

I am very eager to virtualize two notebooks we have setup. Both notebooks are running Windows XP.  One is used by a mobile worker who works outside the office, and the other is used inside the office on different desktops.  I would like to simulate tasks performed on these notebooks and those tasks involve use of speech recognition.

I wonder, since  the sounds a virtual machine generates are always played by the host machine's sound system will I be able to effectively use a microphone/speaker attached to a host computer running Ubuntu  while inside VMware server  I run Windows XP as a guest operating system?

If this will work I would like to download and install Ubunton and Vmware server. I will be happy to send you specifications for the equipment I have available. I would like to prepare a step-by-step plan for the installation  so I can controll progress.

KC

---

### Post by kcav45 on 2008-02-09
zvacet,

I have down loaded Ubuntu  7.01.  
Ready to download VMware server. Please provide serial number.

KC

---

### Post by Shazaam on 2008-02-09
You get the serial number from VMware.

---

### Post by kcav45 on 2008-02-09
OK, but  Zavcet said, " if you decide to install vmwae-server let me know and I can give you serial." 

KC

---

### Post by KcAV on 2008-02-18
I changed my mind several times: summary

**First **I was going to install Windows XP as host operating systems, Ubuntu as guest. Then I dicovered Ubuntu is faster than Windows, and running a fast quest operating system inside a slower host didn't seem to be a good idea.

**Next, ** I was going to install Ubuntu as the host but I could not find Linux drivers for my peripheral devices.

**Finally, ** I decided to install VMware Workstation 6 on notebook running Windows XP, and create only one virtual environment for Windows XP. This will allow me to learn about how to configure and operate VMware Workstation.  I also plan to install Ubuntu 7.10 on an external hard disk drive and creat a dual boot system. This will allow me to learn about Ubuntu.  By learning how to configure and operate a virtualization environment, and becoming familure with a Linux desktop os on existing hardware, I hope to be in position to create a new virtual environmet in the near future.

KC

---

