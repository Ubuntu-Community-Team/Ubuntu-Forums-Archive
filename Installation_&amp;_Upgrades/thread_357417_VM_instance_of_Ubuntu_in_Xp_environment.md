---
title: "VM instance of Ubuntu in Xp environment"
date: 2007-02-09
forum: Installation &amp; Upgrades
---

### Post by flymantang on 2007-02-09
Hi everyone,

Am really interested in having Ubuntu installed on my system (labtop, and desktop). 
I've been searching around on the forums and on the web on how to install Ubuntu on a vm instance in WinXP and I've found the following links.

1) [http://johnbokma.com/mexit/2005/11/07/vmware-player-ubuntu-installation.html](http://johnbokma.com/mexit/2005/11/07/vmware-player-ubuntu-installation.html)
2) [http://homepage.sunrise.ch/mysunrise/ekeller00/ubuntu/2a_UbuntuInWindows_VMware_e.html](http://homepage.sunrise.ch/mysunrise/ekeller00/ubuntu/2a_UbuntuInWindows_VMware_e.html)

Q1: Is anyone using this method? What are the advantages of using vm _VS_. partitioning & dual boot? Reading some of the threads, it seems like quite a few number of people are encountering issues during and after installations. Perhaps installing an vm instance of Ubuntu is the way to go. Any thoughts?

Q2: I want to install this on my labtop as well, and I was wondering how wireless access works? If I can connect to the net through wifi, will I be able to connect to the web from within the vm instance of Ubuntu?  

Q3: Are there any specifications that I should be aware of such as video cards, etc?

Thanks in advance!

---

### Post by shoaibi on 2007-02-09
well i am currently reading the links, while you can read a long post of mine here:
[http://www.ubuntuforums.org/showthread.php?t=356091](http://www.ubuntuforums.org/showthread.php?t=356091)
(Read Post #6)
this might help you, while i will be back after i read the links.

---

### Post by shoaibi on 2007-02-09
Hmmm well its the same method.
Except that if you sue VMware Player you gotta download a Virtual Appliance of Ubuntu from their site which is actually a Zip file containg two files, which is a generlised already installed version of Ubuntu for your machine, which you cna customize later.
While if you use VMware workstation, you can install the Ubuntu yourself with the iso download from Ubuntu mirrors, and have a custom installation which would be the best possible for your system, and later customize it.
And then in Virtual appliances the size of the Disk assigned to teh Guest OS is 8Gb as i remember, which can't be changed AFAIK,(i.e. to use that virtual appliance image in VMware Palyer you gotta need 8GB free) so i use my own insatllation in which i allocate space to Ubutnu upto my needs.

About WiFi, i don't really know about Wireless networking but probably there shouldbe somthing in the Edit on Virtual Machine that you create in the "ADD" option which ads hardware privilages to Guest OS.

Well you need to know a little, incase if your guest Os isn't picking the drivers, you gotta install them by yourself. else no need.

---

### Post by flymantang on 2007-02-09
> **shoaibi said:**
> Hmmm well its the same method.
Except that if you sue VMware Player you gotta download a Virtual Appliance of Ubuntu from their site which is actually a Zip file containg two files, which is a generlised already installed version of Ubuntu for your machine, which you cna customize later.
While if you use VMware workstation, you can install the Ubuntu yourself with the iso download from Ubuntu mirrors, and have a custom installation which would be the best possible for your system, and later customize it.
And then in Virtual appliances the size of the Disk assigned to teh Guest OS is 8Gb as i remember, which can't be changed AFAIK,(i.e. to use that virtual appliance image in VMware Palyer you gotta need 8GB free) so i use my own insatllation in which i allocate space to Ubutnu upto my needs.

About WiFi, i don't really know about Wireless networking but probably there shouldbe somthing in the Edit on Virtual Machine that you create in the "ADD" option which ads hardware privilages to Guest OS.

Well you need to know a little, incase if your guest Os isn't picking the drivers, you gotta install them by yourself. else no need.

Why is it better to download the Virtual Appliance of Ubuntu from Vmware instead of getting it from [http://www.ubuntu.com/download](http://www.ubuntu.com/download)? 

If I download from [http://www.vmware.com/vmtn/appliances/directory/ubuntu.html](http://www.vmware.com/vmtn/appliances/directory/ubuntu.html), how will that affect the setup process? Am thinking that everything still remains the same, right?

---

### Post by shoaibi on 2007-02-10
Seems like  i wasn't clear,sorry for that, how is this:

Hmmm well there is difference:

The virtual Appliance that you will download from there will run only if you have VMware Player installed on your Machine. Its a generlised setup for i386, or AMD64, This setup might have some conflicts with your system, i.e. not picking sound card or video or etc. It has a defined space i.e. 8GB AFAIK, and you can't exceed that, that 8GB you gotta use  for software installations in Ubuntu.

The ISO file that you will download from Ubuntu site is independent of VMware, you can use it with out even Installing VMware Workstation by burning it on a CDR/DVDR, and running it. But if you use it with VMware, you will need VMwareWorkstation/Server to run it. VMware Player won't run ISOs AFAIK. Now by running that ISO you can install Ubuntu on your system by yourself and customize it during setup then after, and also this would be the best possible setup for your machine as Ubuntu setup will try to load all drivers if possible and has more possibility of sound card working or etc. You can decide how much space you want to give to Ubuntu during the Virtual Machine Creation.

Clear?
:(

---

### Post by flymantang on 2007-02-10
Yup :) Ubuntu looks and works great, Am using Ubuntu right now to reply :).  

thanks for the help, Much appreciated.

---

### Post by shoaibi on 2007-02-10
No problem as long as it helps you.....
The Spirit of Ubuntu:
"Humity towards others........."

---

