---
title: "Windows 7 &amp; Ubuntu duel booting using"
date: 2012-03-17
forum: Installation &amp; Upgrades
---

### Post by Scott Tabor on 2012-03-17
a Virtual Machine program. I am trying to run Ubuntu on my laptop while still having my Windows 7 OS on the same machine. I know that you folks would be able to help me here. I wanted to be able to use a Virtual Machine software but don't know which to use that isn't nerd heavy. I have NO experience with VM software. Would love to be able to run both OS's at the same time if possible. 

Is this possible? And if so would somebody please give me a step by step instruction or guide me to said tutorial? I have Oracle VM VirtualBox Manager software already downloaded and installed but I don't want to use it due to the fact that I don't want to mess up my system. Also, I have Windows 7 Ultimate on my laptop if it has something better already in it's guts. Please help. I am eager to start learning Ubuntu.
):P

---

### Post by Old_Grey_Wolf on 2012-03-17
> **Scott Tabor said:**
> 
Is this possible? And if so would somebody please give me a step by step instruction or guide me to said tutorial? I have Oracle VM VirtualBox Manager software already downloaded and installed but I don't want to use it due to the fact that I don't want to mess up my system. Also, I have Windows 7 Ultimate on my laptop if it has something better already in it's guts. Please help. I am eager to start learning Ubuntu.
):P

You already have VirtualBox installed, it is one of the easiest to use. You should already have the documentation; however, it is [here]("https://www.virtualbox.org/wiki/Documentation").

You really do need a backup of your system before playing around with the operating system. Even those of us with quite a few years of experience have messed up our systems. Backups are a wonderful thing to have.

Knowing you have a backup of your system may help you overcome the anxiety you have about messing up your system. Having a backup of the system is important when dealing the anxiety of go forward with system modifications.

If you still have anxiety then wait until you have a second system to play with that you don't mind rebuilding.

---

### Post by Scott Tabor on 2012-03-17
We have ten computers in the house. I am very virginal on using/playing with VM's. I have no XP with this medium. So if I install Ubuntu on a partition, can I use VM to load them both into my computer at the same time?

---

### Post by Old_Grey_Wolf on 2012-03-17
Each OS uses some amount of memory and cpu. You can run multiple operating systems on a computer provided it has the cpu and memory to do the job. 

The screenshot I attached is from my laptop. It has Ubuntu 10.04, Fuduntu, and Debian Stable 6 running at the same time. I noticed that the conky display on the right of the Ubuntu desktop in the screenshot shows the three operating systems are using 45% of the laptops memory and about 30% of the CPU cores.

I have the 3 operating systems running on this laptop that has 4GB of RAM and a dual-core 1.7 GHz CPU.

In order to replace your 10 computers with a single server using virtualization you may need a server with one or two quad-core processors. It all depends on how you use the computers.

---

### Post by Scott Tabor on 2012-03-17
I have installed Ubuntu on another partition but I still can figure out how to use, Oracle VM Virtualbox so both OS's are running. I don't know how to setup the VM.

---

### Post by Old_Grey_Wolf on 2012-03-17
> **Scott Tabor said:**
> I have installed Ubuntu on another partition but I still can figure out how to use, Oracle VM Virtualbox so both OS's are running. I don't know how to setup the VM.

If you have Oracle VirtualBox installed then start it from the applications menu/icon. 

Then install the operating system you want to use within VirtualBox using VirtualBox's "New" button.

VirtualBox will want the location of the CD for the new OS. Navigate within VirtualBox to the .iso of the OS you downloaded then let VirtualBox install the OS on the VM.

---

### Post by Scott Tabor on 2012-03-18
I have installed it using teh Ubuntu via windows function. But I don't know the exact proceedure for getting it to work along side windows where I can have both loaded in memory. There is a screen that askes me what I want to do vm machine, vm hd, etc. I am confused on this option. I am BRAND new to Linux and just learning.

---

### Post by Alberonn on 2012-03-19
I am currently using VirtualBox to run an XP install so I can play some old, XP-only games. (Since I don't have the right version of Win7 to get free XP mode and I still have a good XP licence number.) I am considering making an Ubuntu install, and I'm wondering what system settings I should use to run Ubuntu? (How big can I make the sandbox?) I'm pretty certain it does not need all the resources it takes to keep Windows running. lol

I'm currently running a Dell Inspirion N5110 Laptop with a 2.1GHz i3-2310M CPU and 8GB of RAM.

---

### Post by Old_Grey_Wolf on 2012-03-19
> **Scott Tabor said:**
> I have installed it using teh Ubuntu via windows function. But I don't know the exact proceedure for getting it to work along side windows where I can have both loaded in memory. There is a screen that askes me what I want to do vm machine, vm hd, etc. I am confused on this option. I am BRAND new to Linux and just learning.

Can you post a screenshot of this?

---

### Post by Old_Grey_Wolf on 2012-03-19
> **Alberonn said:**
> I am currently using VirtualBox to run an XP install so I can play some old, XP-only games. (Since I don't have the right version of Win7 to get free XP mode and I still have a good XP licence number.) I am considering making an Ubuntu install, and I'm wondering what system settings I should use to run Ubuntu? (How big can I make the sandbox?) I'm pretty certain it does not need all the resources it takes to keep Windows running. lol

I'm currently running a Dell Inspirion N5110 Laptop with a 2.1GHz i3-2310M CPU and 8GB of RAM.

If you are asking about dual booting Windows 7 and Ubuntu so you can run XP as a VM on Ubuntu, you should give the Ubuntu partition about 20GB to 40GB but that depends on what you install on the VM. For disk space, it really needs about 4GB for Ubuntu, plus the space for the XP VM and whatever the games need. You should give the XP VM at least 1GB of RAM and at lest 1 virtual CPU.

---

### Post by Alberonn on 2012-03-19
Actually I was thinking of using VirtualBox to create a Ubuntu install. However, I just tried out Wubi and I like the fact that I'm not sharing as many resources with Windows so I can take full advantage of my hardware under Ubuntu.

I was originally wondering how much RAM, ect. I should allocate for the virtual Ubuntu machine. I'm still curious since I'm still experimenting with the system though. 

Since I have Win7 Home Premium, I don't have free access to XP mode. I also have a valid XP key so when I discovered VirtualBox, it was a no-brainer to create a virtual XP machine for old games and software. (Command & Conquer: The First Decade was a big one.) I also installed a tiny virtual Debian machine using the Raspberry PI YouTube instructions for fun--which is how I discovered VirtualBox--but I really wanted a bigger Linux install to try to get a better handle on the system.

To be honest, I've only been using Windows for a few years now as I was using an Amiga almost exclusively until around 2007. I still kinda miss my old towered A4000 and OS 3.9.

---

### Post by Old_Grey_Wolf on 2012-03-19
Alberonn,

Can you be specific about the help you need? It looks like you are experimenting with WUBI and VirtualBox; however, I can't determine what you need help with. :confused:

---

### Post by Alberonn on 2012-03-19
I was wondering what I should use for system settings for VirtualBox and Ubuntu. For instance, I'm asking how much system RAM should I allocate, how many CPUs (I have the i3 which has dual-threaded, dual cores), how much graphics memory? Or like I said before, how big should I make the Virtual machine on my current laptop?

I may stick with Wubi, but I'd like to see how well VB runs things before I decide which way to go.

---

### Post by Old_Grey_Wolf on 2012-03-19
> **Alberonn said:**
> I was wondering what I should use for system settings for VirtualBox and Ubuntu. For instance, I'm asking how much system RAM should I allocate, how many CPUs (I have the i3 which has dual-threaded, dual cores), how much graphics memory? Or like I said before, how big should I make the Virtual machine on my current laptop?

I may stick with Wubi, but I'd like to see how well VB runs things before I decide which way to go.

Look at this post above where I think I gave you some suggestions [http://ubuntuforums.org/showpost.php?p=11778493&postcount=10](http://ubuntuforums.org/showpost.php?p=11778493&postcount=10).

---

### Post by Alberonn on 2012-03-19
Those are great specs for the Virtual XP machine. I think mine's set for 3GB, 1 CPU. I forget the hard drive space, but I think I set it to only take up the space it actually uses with a size cap. No I was talking about good setting to VB running Ubuntu on Win7

---

### Post by Old_Grey_Wolf on 2012-03-19
> **Alberonn said:**
> Those are great specs for the Virtual XP machine. I think mine's set for 3GB, 1 CPU. I forget the hard drive space, but I think I set it to only take up the space it actually uses with a size cap. No I was talking about good setting to VB running Ubuntu on Win7

I thought you wanted to run Windows XP as a VM on Ubuntu in order to play old XP games. So, all you want to do is run Ubuntu as a VM on Windows 7 using VirtualBox?

---

### Post by Alberonn on 2012-03-21
Yup. I was wondering what the best settings would have been given my current hardware.

---

### Post by Old_Grey_Wolf on 2012-03-21
> **Alberonn said:**
> Yup. I was wondering what the best settings would have been given my current hardware.

I usually give a Linux VM 1 GB of RAM and 1 virtual CPU in VirtualBox to start with. Depending on how I use the VM I will change the memory and CPU setting in VirtualBox until I get the performance I am happy with. I have gone to 2 GB RAM and 2 virtual CPUs for some VMs. 

The amount of disk space depends on a calculation of the OS size, additional application sizes, data I expect to store, and so fourth.

There isn't one answer that fits all people.

When you build your VM it is not that different from building a desktop. You need to determine what RAM to put in the desktop, what CPU to buy; such as, single-core, dual-core, quad-core, and how big the disk drive needs to be. The advantage of virtualization is, that you don't actually have to mess around with hardware.

---

