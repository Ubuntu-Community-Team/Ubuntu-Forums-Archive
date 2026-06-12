---
title: "How to update/downgrade kernel in ubuntu"
date: 2018-02-09
forum: Installation &amp; Upgrades
---

### Post by giobaxx on 2018-02-09
Hello Guys


i'm trying to understand how to manage Kernel Upgrade or Downgrade(if necessary) in Ubuntu.
I've searched in various forum  but i'm still a bit confused sometimes


What i have undestood is:


**apt-get upgrade** --> upgrade only packeges already installed but not Kernel


**apt-get distr-upgrade** --> do also Kernel upgrade


Correct?


I tried in an old VM installed ubuntu 14.04 running **apt-get dist-upgrade** 
and i have upgraded the kernel from  3.16.0.30 to 3.16.0.77


After i have rebooted the system and i tried to run again **apt-get distr-upgrade** 
but no upgrade were available. This means that apt-get distr-upgrade i cannot upgrade
over the 3.16.0.77 version??


In my "experiment" i have updated the kernel till 4.2.0.38 version. this is what i did:


After running  **apt-cache search linux-generic** i had a list of kernel i choose to install 4.2.0.38 running **apt-get install linux-image-4.2.0.38-generic**


I saw a lot of other kernel available, till 4.4.0.98 version if i remember well, but running apt-get dist-upgrade no upgrade are available.


From what i have understood  if i want to upgrade kernel i need to do it "manually", running **apt-install linux-image-x.x.x.x-generic** choosing the version i want.   Correct or not?


With **apt-get dist-upgrade** which kind of kernel upgrade are available?


With google i also find that is possible to update the kernel with dpkg but which packages i have to download?


Last Question, if updating Kernel Something goes wrong how to downgrade to the old version?

---

### Post by #&amp;thj^% on 2018-02-09
> **giobaxx said:**
> Hello Guys


i'm trying to understand how to manage Kernel Upgrade or Downgrade(if necessary) in Ubuntu.
I've searched in various forum  but i'm still a bit confused sometimes


What i have undestood is:


**apt-get upgrade** --> upgrade only packeges already installed but not Kernel



Not completely correct if the kernel is receiving security/feature updates then it will be updated as well.
"dist-upgrade" pulls in all held packages and fully updates your system. (In a nut shell)
_Now if you go outside of your default kernel>>>you may be at risk of security flaws._ Just a heads-up!

**[COLOR="#FF0000"]**Warning** playing with kernels can either make or break your system[/COLOR]**. (Needs experienced user or **know how to get yourself out of trouble if need to**)
Pretty much any Linux distribution you can upgrade and downgrade kernels at will.  Typically just a matter of installing the correct packages.  Make sure you INSTALL, not upgrade with the new package (otherwise it may overwrite the existing one).  

That's the beauty of "kernel" versus "distribution".

There may also be a kernel firmware package that you should install alongside the new kernel package.**(This is where the experience comes in to play)**
 
Or you can use a utility to help with that:
Kernel Update Utility for Ubuntu-based distributions. Provides desktop notifications when new mainline kernel is available. Lists kernels from [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/) with options to install and remove. 
Added with a PPA: [https://launchpad.net/~teejee2008/+archive/ubuntu/ppa](https://launchpad.net/~teejee2008/+archive/ubuntu/ppa)

[COLOR="#FF0000"]IMPORTANT:[/COLOR]Now with adding a PPA to the mix is not something "I would recommend to a Newer User".
Ukuu (short for Ubuntu Kernel Update Utility) makes updating your Ubuntu kernel much easier to perform. It downloads newer kernels from the internet, and changes your system to let it use them. All you really have to do is choose which kernel you&#8217;d like and reboot into it. The kernel is basically an important piece of software found in every operating system. It acts as a mediator between the software you run every day (e.g. web browsers), and the hardware that it&#8217;s running on. Essentially, without a kernel, other programs cannot function since they can&#8217;t access your computer&#8217;s resources. {If Something Goes Wrong, Do Not Panic}
For your last question:
 If you install a new new Linux kernel on your Ubuntu machine and it does not work properly, a piece of hardware fails, or any other issues arise you can easily boot in to an older kernel from the GRUB screen then, when back up, use Ukuu to remove the offending  kernel.

---

### Post by deadflowr on 2018-02-09
> I tried in an old VM installed ubuntu 14.04 running apt-get dist-upgrade 
and i have upgraded the kernel from 3.16.0.30 to 3.16.0.77


After i have rebooted the system and i tried to run again apt-get distr-upgrade 
but no upgrade were available. This means that apt-get distr-upgrade i cannot upgrade
over the 3.16.0.77 version??
That would about as far as the 3.16 kernel sereis went before it hit end of support on Ubuntu 14.04.
So makes sense it won't upgrade any further, regardless of apt command used.
> I saw a lot of other kernel available, till 4.4.0.98 version if i remember well, but running apt-get dist-upgrade no upgrade are available.
kernel upgrades using the updater or apt are tied to the system having the linux-generic or linux-image-generic/linux-headers-generic packages. These are meta-packages and are required for the updater to pull in the newest kernel version.
Otherwise in order to upgrade kernel, you would be need to manually install the kernel version yourself.

Based on the little knowledge at hand I know you installed (the VM) Ubuntu 14.04.2, the .2 point is the second point release for 14.04 and contains an upgraded linux and X hardware stack
[https://wiki.ubuntu.com/Kernel/LTSEnablementStack]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack")
Unfortunately, though, Ubuntu 14.04's hwe stack did not institute a rolling hwe stack, as 16.04 currently does: [https://wiki.ubuntu.com/Kernel/RollingLTSEnablementStack]("https://wiki.ubuntu.com/Kernel/RollingLTSEnablementStack")

So in order to upgrade the hwe stack you need to manually set it up yourself: [https://wiki.ubuntu.com/1404_HWE_EOL]("https://wiki.ubuntu.com/1404_HWE_EOL")

That should help explain to you why you can see new kernel versions like 4.2 and 4.4 but never get them as updates.

I hope something here makes some sense to you.
Good reading and good luck.

---

### Post by giobaxx on 2018-02-10
We miss a Linux SysAdmin since the end of last year, so i tried to do my best linux side but i'm worried to touch kernel. Basically  a user need to install a new Python platform and due to incompatibility he needs to upgrade the Kernel....:(

So if the Kernel receive Security Updated kernel it will be updated also with **apt-get upgrade ....**while **dist-upgrade **it will upgrade** kernel **regardless of whether they are security updates or not
But if i have installed ubuntu with a for exemple the kernel 3.16.0.x i will not able to upgrade over the 3.16....and if i want to do it i need to it manually dowloading and installing packages via **dpkg **or via** apt-get install**.... and this at my risk....

For the Moment i play only with my Virtual machine i don't want destroy the workstation of my collegues but sure i would like to learn to manage that kind of problems, and also downgrade to a working version of kernel if somethig goes wrong.
For my small linux experience most of the failure we had in the past were happened with kernel upgrade with a nvidia card. Form What a collegue told me, after a kernel upgrade the nivdia driver stop working  breaking the system.  i don't know if it's true r not...

Anyway....Tanks a LOT for the adivice

---

### Post by giobaxx on 2018-02-10
Tanks a lot [FONT=Ubuntubeta, Ubuntu, Bitstream Vera Sans, DejaVu Sans, Tahoma, sans-serif][COLOR=#000000]deadflowr  i was reading the link you sent.....the tings start to be more clair!!!!!

[/COLOR][/FONT]TANKSSSSS
[COLOR=#C61919]deadflowr[/COLOR][COLOR=#C61919]deadflowr[/COLOR]

---

