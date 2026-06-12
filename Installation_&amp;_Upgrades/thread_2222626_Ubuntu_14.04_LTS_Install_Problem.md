---
title: "Ubuntu 14.04 LTS Install Problem"
date: 2014-05-07
forum: Installation &amp; Upgrades
---

### Post by 2ndCharter on 2014-05-07
Greetings,

First I must say I am a complete Linux noob. I am quite adept at Windows but want to try Ubuntu as a dual boot on my laptop. I have a cd burned with the 14.04 LTS Desktop for 64 bit machines and am attempting an install on a Toshiba Satellite U840. I have previously shrunk the existing OS partition and have 150 GB of free unallocated space.

I have made several unsuccessful install attempts and keep getting hung up at the same spot. For reference, I am following the install guide at [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall).

I get past the "Preparing to install Ubuntu" step but I never get the prompt displayed under "Installation type" as shown in that install guide. What I get instead is a blank table, a "+", "-" and "Change..." button and a dropdown that has "/dev/sda" as the only option for "Device for boot loader installation". This view I am seeing is akin to the 5th screen located at the following install tutorial:

[http://www.linuxtechi.com/ubuntu-14-04-installation-guide/](http://www.linuxtechi.com/ubuntu-14-04-installation-guide/)

However, the differences are that I don't have that drive space graphic, the details listed under the table (Device, Type, Mount point etc.) nor options after the /dev/sda option like you see in that graphic. The "New Partition Table..." and "Revert" buttons are disabled. I can click the "Install Now" button but I'm afraid to since I'm obviously not seeing anything like what both install guides are showing me.

Does anyone have any insight into what I should do to get the install to do a side-by-side install as a dual boot with my existing Windows OS?

---

### Post by grahammechanical on 2014-05-07
One of the first screens that we see should give us options like these,

Install Ubuntu alongside
Erase disk and install Ubuntu
Encrypt the new Ubuntu installation for security
Use LVM with the new Ubuntu installation
Something Else 

What do you see? Do you get the option to install alongside? What is your existing Windows OS? 7 or 8? It can make a bit of a difference. It seems to me that the installer is not recognising the disk partitions. And this is why you are not getting any opportunity to select and change the use of partitions.

Regards.

---

### Post by 2ndCharter on 2014-05-07
I am running Windows 7.

First thing I do when the install is available is to connect to an available WIFI. When I was presented that option in the installer, it would never let me enter my WEP key meaning that it doesn't recognize that a password is required. So this allows me to get further along, to the problem I've identified above.

Here are the screens I get, in order:

1. Try Ubuntu / Install Ubuntu: I chose install.
2. Wireless: I get options to chose a wireless network. As I mentioned, if I use this step, it won't let me enter the key. Here I select the option that "I don't want to connect to a wi-fi network right now".
3. Preparing to install Ubuntu: Here, all three requirements show that I am ok to install; I have enough drive space, I'm plugged into a power source and I am connected to the internet. I check to download updates while installing and allow the installation to install third party software.
4. Installation type: This is where I, by the guide descriptions, should see what you are mentioning but instead I get the view I described above which is the problem I am having.

---

### Post by 2ndCharter on 2014-05-07
Just to ensure it wasn't a bad CD, I just put the ISO on a USB with pendrivelinux and ran into the same problem.

---

### Post by pfeiffep on 2014-05-07
Possibly opt to "Try Ubuntu"

---

### Post by 2ndCharter on 2014-05-07
Yes, I can use the try option just fine, or as best as I can tell. If your advice is to do this as a trial and forgo installation, that doesn't solve my problem. I want to dual boot Windows and Ubuntu. There are some things for work I can not do without Windows for.

---

### Post by pfeiffep on 2014-05-07
> **2ndCharter said:**
> Yes, I can use the try option just fine, or as best as I can tell. If your advice is to do this as a trial and forgo installation, that doesn't solve my problem. I want to dual boot Windows and Ubuntu. There are some things for work I can not do without Windows for.
No ... it wasn't meant to solve anything but rather fully explore your system with the live DVD / USB. There is an option from within the *Try* that provides install also. 

Do you get to the point that provides the option of 'Something Else'? If so than you should be able to proceed with the install - be careful not to choose your Windows partitions.

---

### Post by 2ndCharter on 2014-05-07
Oh, ok. Yes, I tried install from that desktop a few times as well. I even went way outside of my linux experience (which is 0%) and followed some guidance here:

[http://www.rodsbooks.com/missing-parts/index.html](http://www.rodsbooks.com/missing-parts/index.html)

And took that unallocated partition and formatted it as ext4, saved changes and rebooted... still nothing is showing up. I question why I don't get that prompt screen and go directly to partition table manipulation and it sees nothing. There must be something that needs to be tweaked either in Windows, the bios or in the "Try" that should work but I am a very green noob.

---

### Post by 2ndCharter on 2014-05-07
> **pfeiffep said:**
> Do you get to the point that provides the option of 'Something Else'? If so than you should be able to proceed with the install - be careful not to choose your Windows partitions.
No, I never see that screen. If you look above at my 2nd post, that's the screen I expect to see at #4 but instead I'm in what looks like where I should select the partition to install to yet there are no partitions listed there. GParted though lists the partitions.

---

### Post by pfeiffep on 2014-05-07
I believe the screen to which I'm referring is labeled "Installation Type" and has these options - the last of which is Something Else
[http://pix.toile-libre.org/upload/original/1349879961.png](http://pix.toile-libre.org/upload/original/1349879961.png)


Some Partitioning [guidance]("https://help.ubuntu.com/community/DiskSpace")

---

### Post by 2ndCharter on 2014-05-07
Right. I never get that screen. It goes to this instead:

[http://imageshack.com/a/img836/5443/ialp.png](http://imageshack.com/a/img836/5443/ialp.png)

---

