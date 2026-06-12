---
title: "[SOLVED] Beginner install problems: Partitions, Network, Mouse"
date: 2008-02-07
forum: Installation &amp; Upgrades
---

### Post by Peter Kenny on 2008-02-07
Hi. I have just got a Kubuntu 6.06 live/install DVD. I have run it as a live disk on my two Windows XP machines, and I intend to install it on one of them, making it a dual boot machine. I have three questions about what to do next - I am terrified of fouling up Windows beyond repair!

a. Can anyone give me a link to detailed step by step instructions on disk partitioning on an XP machine. Which partitions do I need to create? Should I use a Windows partition manager to create them before installing? Does the Kubuntu installer create them, and can I trust it not to foul up Windows?

b. Using the live disk, on both machines the system fails to locate the network connection. Each machine has a Belkin wireless network adapter in a USB port, communicating with a Belkin 54g wireless hub which in turn links to the internet and to a networked printer. Do I need to do something in Kubuntu to activate the network, or should it find it automatically? Is it likely to be easier to do this from an installed system tham from a live disk?

c. On one of the machines, Kubuntu seems to go haywire when I move the mouse - new windows open without any mouse click, the cursor jumps wildly unrelated to my mouse movemnts, I have to use reset to exit the Kubuntu OS. If I start in safe graphics mode the mouse behaves OK for a while, but after a minute or two the same problems occur. On the other machine all works OK - yet it's the same mouse and keyboard, connected to both machines through a KVM switch. Unfortunately the troublesome machine is the one I want to install Kubuntu on! Can anyone suggest a remedy?

Thanks for any help. This is my first post here, so I'm not too sure about etiquette. Have I got the right forum? Should I have posted it as three separate questions?

---

### Post by Carl H on 2008-02-07
> **Peter Kenny said:**
> b. Using the live disk, on both machines the system fails to locate the network connection. Each machine has a Belkin wireless network adapter in a USB port, communicating with a Belkin 54g wireless hub which in turn links to the internet and to a networked printer. Do I need to do something in Kubuntu to activate the network, or should it find it automatically? Is it likely to be easier to do this from an installed system tham from a live disk?


You really need a wired internet connection for installing.

---

### Post by jan quark on 2008-02-07
always do a back up

I have to say this

do a back up now... :)

> a. Can anyone give me a link to detailed step by step instructions on disk partitioning on an XP machine. Which partitions do I need to create? Should I use a Windows partition manager to create them before installing? Does the Kubuntu installer create them, and can I trust it not to foul up Windows?


a)

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)



> b. Using the live disk, on both machines the system fails to locate the network connection. Each machine has a Belkin wireless network adapter in a USB port, communicating with a Belkin 54g wireless hub which in turn links to the internet and to a networked printer. Do I need to do something in Kubuntu to activate the network, or should it find it automatically? Is it likely to be easier to do this from an installed system tham from a live disk?

b)
[https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29?highlight=%28WifiDocs%2FDevice%29)

found this in the official ubuntu documentation, 

if you know the exact model name you can have a look here and see if your card is supported

[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBelkin](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBelkin)

c)

cant say anything to the mouse problem, because I have not enough input.. what are your specs ? graphic card, cpu, ram, drives? for the future start always with your specs..

by the way why aren't you using the newest version of ubuntu? if you have a internet connection I would recommend to download the gutsy gibbon 7.10 version or wait till april because then the new Hardy Heron 8.04 LTS / Long Term Support version will be released.

Many issues have been fixed during the latest releases, and also the package repositories are up to date.

just a thought

feel free to ask more...

PS: it is better that way:   one thread - one qestion  helps to keep the forum organized
:)

---

### Post by cryptozoologist on 2008-02-07
the safest and simplest way to avoid munging up windows is to install kubuntu onto a separate hard drive.

please post some more info about your keyboard, mouse and kvm.  are they usb, ps2, serial, and do you know if you have a 'smart' kvm which tries to fake out the machines it is connected to into thinking a mouse is connected or a 'dumb' kvm that is merely a switch.

i had a computer that would not boot at all with a 'smart' kvm attached but when a keyboard was plugged into it directly, all was fine.  also are you booting with the kvm switched to the mackine that is giving you fits or are you switching between boxes, thus possibly confusing hardware detection?

peace
cryptozoologist

---

### Post by Peter Kenny on 2008-02-07
Many thanks for the comments, especially Jan Quark for the 'psychocats' links. This site gave me so much information that I wish I had known earlier. I think I now understand the basics of partitioning.

The first link on networking refers exactly to my wireless adaptor, so I now know how to get a working driver for it. (If I had looked at the Belkin box, I would have seen that it specifies Windows OS only!)

However, compiling and installing the driver looks like a hassle, and there is still the unresolved mouse problem. Having read psychocats, it occurs to me that I could bypass both issues by doing a virtual install using VirtualBox, even if  I might have to upgrade my 512MB RAM to 1GB to get decent performance. Does this look sensible, remembering I want to keep Windows, or are there other snags I haven't thought of?

> by the way why aren't you using the newest version of ubuntu?

Pure ignorance. I found the documentation on versions very confusing. I saw the LTS tag on 6.06, I read about the hassles of upgrading between versions, and I thought I would use 6.06 until the next LTS version appears (which apparently *might* have easy updating). Did I get it wrong? It will take only a couple of days and 4GBP plus postage to get a disk for 7.10 (I don't want to wait forever for a download, and my broadband capacity is capped.)

---

### Post by Peter Kenny on 2008-02-07
> **cryptozoologist said:**
> the safest and simplest way to avoid munging up windows is to install kubuntu onto a separate hard drive.

Unfortunately my Shuttle box cannot take a second hard drive. I could use an external drive with a USB link; would that work?

> **cryptozoologist said:**
> please post some more info about your keyboard, mouse and kvm.  are they usb, ps2, serial, and do you know if you have a 'smart' kvm which tries to fake out the machines it is connected to into thinking a mouse is connected or a 'dumb' kvm that is merely a switch.

i have a Logitech wireless keyboard and mouse, which comes with USB and ps2 plugs, which is connected via the ps2 plugs to a Belkin OmniView KVM switch, which I think is a pretty dumb pure switch. I did not switch between machines while trying the live disk.

As mentioned above, I am now thinking of using a virtual install over Windows, which I think would mean the virtual OS would take its keyboard input from Windows.

Thanks for the input.

---

### Post by Peter Kenny on 2008-02-09
Well I think it's solved. I installed VirtualBox on the machine I want to use Kubuntu on, and then installed Kubuntu from the live/update disk. This machine has only 512MB RAM, so the VM had only 256MB. The process was very slow, and gave frequent 'Host memory low' warnings. It would not install from the first option on the start menu; I had to use the 'Text mode install' option, and it took two hours to complete! Still, it worked, the internet connection worked and the mouse was well behaved; it was just painfully slow.

Having decided that this was safe, I then did the same on my main machine, which has 2GB of RAM; I gave the VM 1GB, and was able to install from the first option on the start menu. Includiing the time to do the live disk start and to do the install, the total was just under half an hour. The operation of the system is much slicker than on the smaller RAM. The start-up still seems slow, but I have found that I can short-circuit this by saving a snapshot of the VM and starting from that.

So I now have a working system (well two really, but the smaller one is unusable), and I am now starting to explore Kubuntu. If I get on well with it, in April I shall try 8.04. I think I shall try that in a VirtualBox VM first of all. It should be easy to have two versions around at the same time in different VMs, and if I can work out how to use shared folders I can transfer any useful results from one to the other.

Thanks again for all the comments. The link to 'psychocats' was the crucial thing. If anyone else has doubts about fouling up a Windows system, I would recommend trying it out in VirtualBox first - provided you have enough RAM!

---

