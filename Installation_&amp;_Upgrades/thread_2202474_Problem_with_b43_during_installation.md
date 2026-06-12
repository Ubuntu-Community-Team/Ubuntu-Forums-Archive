---
title: "Problem with b43 during installation"
date: 2014-01-29
forum: Installation &amp; Upgrades
---

### Post by DoktornTheFirst on 2014-01-29
Got an old computer from a friend and a trying to install Lubuntu on it with little success. 

It's an aspire 3003LMi. Mobile Sempron Processor 3000+. 80 Gb. 512MB Ram. It's Lubuntu 13.10 for 32-bits systems I'm trying to install. 

I get to the screen where I can chose to Try it out, Install it, Control for errors, Memory check (rough translation from swedish). 

When I chose Try it out or Installing it starts to load, but a few seconds in something like this pops up; 

> b43-phy0 ERROR: firmware file “b43/ucode5.fw” not found
b43-phy0 ERROR: firmware file “b43-open/ucode5.fw” not found
b43-phy0 ERROR: You must go to [http://wireless.kernel.org](http://wireless.kernel.org) and read all the instructions on this website.

and quickly vanishes again and then the system halts, jumping between a completly black screen and a black screen with a cursor I'm able to move. Note that I have copied the text from another site as the text vanishes to quickly for me to write it down. I know the last line is a bit different in wording, although not in essence.

I have tried to go F6, Esc and entering 
> b43.blacklist=yes
and Enter, but it doesn't help in any way. 

Here is [two]("http://ubuntuforums.org/showthread.php?t=1966655&p=11883375#post11883375") [links]("http://linux-software-news-tutorials.blogspot.co.uk/2012/04/installing-ubuntu-1204-crashes-because.html") to what seem to be the same problem as I'm having. THey are suggesting the b43.blacklist=yes approach, but as said, that doesn't work for me. 

Any ideas?

---

### Post by tfrue on 2014-01-29
If you can, I would try and connect with ethernet to get the OS installed, then we can worry about getting the Broadcom driver installed. If thats not an option, then we will get the driver installed!

---

### Post by DoktornTheFirst on 2014-01-29
Thanks! Tried with a cable but it didn't help. 

So how do we get the driver installed? I can run the stick on another computer with internet connection without any problem.

---

### Post by carl4926 on 2014-01-29
> **DoktornTheFirst said:**
> Thanks! Tried with a cable but it didn't help. 

So how do we get the driver installed? I can run the stick on another computer with internet connection without any problem.
Another computer with the identical hardware? Uh?

If you have the actual firmware you can copy the folder b43 to /lib/firmware  in the live session
Then modprobe it like this

```
sudo modprobe -rv b43
```
```
sudo modprobe -v b43
```

I have a copy of the firmware folder
[https://dl.dropboxusercontent.com/u/10573557/b43_firmware/b43_wireless_20_09_2013.zip](https://dl.dropboxusercontent.com/u/10573557/b43_firmware/b43_wireless_20_09_2013.zip)

---

### Post by DoktornTheFirst on 2014-01-29
No, very different hardware.

Ok. I downloaded and installed the firmware in your folder carl4926. I ran the commands on the other, working, computer. Switched to the computer I want to install Lubuntu to an ran it. Same problem. Restarted and by using Ctrl+Alt+F2 right after I chose "Try Ubuntu before installing" I got a command line and entered the commands. Restarted again and still the same problem. :(

Did I do something wrong or do you have any more suggestions?

---

### Post by SeijiSensei on 2014-01-29
It's much more troubling that you cannot seem to connect with a network cable.  Can you try that again please?  It's been a very long time since I've encountered a machine that could not use wired Ethernet out-of-the-box.  If both wired and wifi connections don't work, there is something more fundamentally wrong than just the b43 firmware.  I installed Kubuntu on a older machine with a Broadcom wifi adapter and could not connect with it, but I could still connect using the Ethernet adapter.

Some Broadcom problems can be [quickly solved]("http://ubuntuforums.org/archive/index.php/t-2011756.html") by installing the "linux-firmware-nonfree" package and rebooting.  That worked for me.

---

### Post by DoktornTheFirst on 2014-01-29
I'm pretty sure it does connect to internet through the wired cable. (It does on Windows XP that is installed.)

My problem is I don't get far enough for a connection to internet to be an issue at all. I can't get into the Live session and I can't reach the installation guide. I get to where I can chose to try Lubuntu out, install it, check the disc for errors, etc. But when I chose to try it out or install it it starts to load and then crashes with the message I quoted in the OP.

---

### Post by carl4926 on 2014-01-29
[http://wireless.kernel.org/en/users/Drivers/b43](http://wireless.kernel.org/en/users/Drivers/b43)

Is your device supported

---

### Post by SeijiSensei on 2014-01-29
> 
6. You should now have a cursor from which you can enter commands below the boot options: Type
b43.blacklist=yes
**making sure there is a space before and after the text you enter**.

Perhaps you left out a space?

---

### Post by DoktornTheFirst on 2014-01-29
@carl4926
Yes. My device is supported. BCM4318 to exact.

@SeijiSensei
Space before and after was included. (Without also. And with space before, but after and vice versa.)

---

### Post by carl4926 on 2014-01-30
Have you actually be able to run the media check and with success?

---

### Post by DoktornTheFirst on 2014-01-30
Uhmm... is the media check the same as the memory test? Then yes I have. No problems found. 
No defects on the disc test either.

Windows XP is running on it and an older version of Xubuntu with non-working wifi. And I can run the USB-stick on other computers. So the computer and the USB-stick seem to work fine; Just not together.

---

### Post by carl4926 on 2014-01-30
Media check = Check disk for defects

If you can get the result of this?

```
lspci -nnk
```

---

### Post by DoktornTheFirst on 2014-01-30
Here comes the result of lspci -nnk. Obtained by using Ctrl+Alt+F2 after choosing Try Lubuntu... (copied by hand, expect some errors)

> 00:04.0 Ethernet controller [0200]: Silicon Integrated Systems [SiS] Sis900 PCI Fast Ethernet [1039:0900] (rev 91)
     Subsystem: Acer Incorporated [ALI] Device [1025:0083]
     Kernel driver in use: sis900
00:06.0 Cardbus bridge [0607]: Texas Instruments PCI1410 PC card Cardbus Controller [104c:ac50] (rev 02)
     Subsystem: Acer Incorporated [ALI] Device [1025:0083]
     Kernel driver in use: yenta_cardbus
00:0b.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
     Subsystem: AMBIT Microsyste Corp. TravelMate 2410 [1468:0312]
     Kernel driver in use: b43-pci-bridge
00:18.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] Hypertransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] Adress Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
     Kernel driver in use: k8temp
01:00.0 VGA compatible controller [0300]: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter [1039:6330]
     Subsystem: Acer Incorporated [ALI] Device [1025:0083]

---

### Post by carl4926 on 2014-01-31
I know this is going to sound silly or condescending but are you sure the wifi is toggled on? There isn't a Fn combo that turns it on/off is there?

Also worth installing rfkill and post the result of

```
rfkill list
```

---

### Post by DoktornTheFirst on 2014-01-31
Ask me silly questions! Whatever it takes to make it work. :)

There is a button for the Wifi on the front. But it is not working when I start the computer with the USB-stick. Can't turn in it on (it does turn on and off in the installed Windows XP). 

rfkill list doesn't give any result at all. When running on another computer I get a result, but I guess that doesn't count.

---

### Post by DoktornTheFirst on 2014-01-31
It crashes with Xubuntu also. But the installing process are built a bit different. Xubuntu loads a lot more from the get-go than Lubuntu, which results in the Xubuntu installation crashing before get to any kind of menu.

I will probably try with another Linux distribution like Puppy Linux or something like that to see if that works.

---

### Post by carl4926 on 2014-01-31
Every device I have ever worked on with SiS GPU was basically a no go

---

### Post by DoktornTheFirst on 2014-02-01
I also tried with Lubuntu 12.04 without success. So I have now given up on *ubuntu. 

I  went on and tried Puppy Linux instead and luckily it works. While not  the perfect solution, it is nevertheless a fine solution. 

Thanks for all the help and advice in any case! I really appreciate it! [****]("https://www.google.com/search?client=ubuntu&hs=QiM&channel=fs&q=appreciated&spell=1&sa=X&ei=S0PtUtLyOeGE4gT51IDQAw&ved=0CCQQvwUoAA")


*  As the issue wasn't really solved I won't mark the thread as solved,  but instead just let it drop. If I should do anything else just tell me  and I'll do it.

---

