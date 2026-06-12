---
title: "Ubuntu 12.04 stopped booting correctly (blank purple screen)"
date: 2012-06-29
forum: Installation &amp; Upgrades
---

### Post by Btru on 2012-06-29
I hope this is the right forum to post in for my problem...

So my computer was working flawlessly for ~4 weeks on ubuntu 12.04 but today, when I booted it up, It just got stuck on a blank purple screen...
I have tried booting with nomodeset in both regular and recovery mode through the grub screen with no success. Not sure if this info is needed, but the kernel is 3.2.0-25-generic and I am running on an Intel i5 3570k. my graphics card is the Nvidia geforce GTX 550 ti.
I dont know exactly what updates I downloaded the last time I used the computer (i just hit install updates when it prompted me...) 

I'm pretty much a linux noob, so any help or suggestions would be appreciated!

---

### Post by bogan on 2012-06-30
Hi!, **Btru**,

Is the kernal '3.2.0-25-generic', or:'3.2.0-25-generic-pae'?
Or did you update to '-26-'?
This will tell you:```
uname -ar
```What video controllers do you have? Integrated as well as the 'Nvidia geforce GTX 550 ti'?.
Please Post:```
 sudo lspci -nnk | grep -iA2 VGA
```Copy/Paste the cmd and output from the Terminal window to your 'New Entry' Edit box, highlight it and Click on the '#' icon in the top toolbar of the Edit box, to enclose the results in a Codebox.

Also the VGA paragraph[s] of the output from 'lspci'.

If those show that there are both, have you installed Bumblebee? 

If you have installed 'Additional Hardware' drivers, also Post the oputput of:```
sudo apt-cache policy nvidia-current
cat /sys/module/nvidia/version
```Chao!, **bogan**.

---

### Post by Btru on 2012-06-30
Oh, sorry the kernel *is* 3.2.0-26-generic. (it says in grub)

I tried all of the commands you gave me in your post, but all I have access to is the grub menu and command line, so none of them worked... Is there any other way I can enter in these in? I am unable to get into recovery mode or boot normally from grub (I just get a blank purple screen). 

I have never installed  bumblebee (never heard of it)

When I just did ```
lspci
``` it showed one vga controller:```
01:00.0 10de:1244 [0300] VGA Controller
```
Do you have any other suggestions?

Thanks so much for the response!
Brandon

---

### Post by Btru on 2012-06-30
Wait, I just tried booting with ```
nomodeset
```and it booted up correctly...
Sometimes it boots up, sometimes it doesn't...
uname -ar
```
brandon@True:~$ uname -ar
Linux True 3.2.0-26-generic #41-Ubuntu SMP Thu Jun 14 17:49:24 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

```sudo lspci -nnk | grep -iA2 VGA
```

brandon@True:~$ sudo lspci -nnk | grep -iA2 VGA
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GF116 [GeForce GTX 550 Ti] [10de:1244] (rev a1)
    Subsystem: Giga-byte Technology Device [1458:3536]
    Kernel driver in use: nvidia

```lspci:
```

brandon@True:~$ lspci
00:00.0 Host bridge: Intel Corporation Ivy Bridge DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Ivy Bridge PCI Express Root Port (rev 09)
00:14.0 USB controller: Intel Corporation Panther Point USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation Panther Point MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation Panther Point High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 1 (rev c4)
00:1c.4 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 5 (rev c4)
00:1c.5 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c4)
00:1d.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Panther Point LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation Panther Point 6 port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation Panther Point SMBus Controller (rev 04)
01:00.0 VGA compatible controller: NVIDIA Corporation GF116 [GeForce GTX 550 Ti] (rev a1)
01:00.1 Audio device: NVIDIA Corporation GF116 High Definition Audio Controller (rev a1)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
04:00.0 PCI bridge: ASMedia Technology Inc. ASM1083/1085 PCIe to PCI Bridge (rev 03)

```sudo apt-cache policy nvidia-current
```

brandon@True:~$ sudo apt-cache policy nvidia-current
[sudo] password for brandon: 
nvidia-current:
  Installed: 295.40-0ubuntu1
  Candidate: 295.40-0ubuntu1
  Version table:
 *** 295.40-0ubuntu1 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise/restricted amd64 Packages
        100 /var/lib/dpkg/status

```cat /sys/module/nvidia/version
```

brandon@True:~$ cat /sys/module/nvidia/version
295.40

```I shouldn't turn off my computer, right? 

Thanks again,
Brandon

---

### Post by bogan on 2012-06-30
Hi!,** Btru,**

What you Posted confirms my suspicion that you ran an update to 32.0.-26 and do not have on-board integrated graphics.

The driver  295.40 is notorious for bugs, though it should work with the GTX 551ti card.

The likely hood is that the update did not correctly replace the video kernal module for the new kernal.

So that needs to be updated. Try this:

When you have successfully booted to a GUI, Click on the Dash, top-left Ubuntu icon, and type 'add' in the search bar, Click on 'Additional Drivers'. 
It should show two NVIDIA drivers ,' version current' - which you have - and 'post release updates'.

Select the first and if it shows: ' not activated', click on the other and select: 'Activate'.

If it shows: 'activated', click on: 'Deactivate' first.

Reboot and if that does not work, Post again the output of:```
 sudo apt-cache policy nvidia-current
```If it does not, then the next step is a bit more complex, but if you get stuck in the blank screen, try pressing 'Ctrl+Alt+F1' and see if that gives you a Text Terminal Log-in prompt [tty1].

Chao!, **bogan.**

---

### Post by Btru on 2012-06-30
It took a few tries with grub to boot to a GUI, I got it to work by entering some random commands (in grub command line):
 ```
test
continue
videoinfo
normal
```and then I went into edit on the regular kernel ubuntu and put ```
nomodeset
``` like usual. (ctrl-alt-f1 didn't do anything for me...)
Does that give you any information that would help?

Anyways,

sudo apt-cache policy nvidia-current:
```

brandon@True:~$ sudo apt-cache policy nvidia-current
nvidia-current:
  Installed: (none)
  Candidate: 295.40-0ubuntu1
  Version table:
     295.40-0ubuntu1 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise/restricted amd64 Packages
        100 /var/lib/dpkg/status

```
What would the next step be? 

Thanks again,
Brandon

---

### Post by bogan on 2012-07-01
Hi!, **Btru**,

Either from a GUI, or in the blank screen, 'Ctrl+Alt+F1' - or F2-F6 - should give you a tty Terminal Login prompt;  'Ctrl+Alt+F7' would return you to the GUI screen. Please try again as if this does not work there is something else amiss besides the video driver.

The output from 'apt-cache' tells me you used the 'Additional Drivers' to remove 'nvidia-current' but not what is there instead. please Post again:```
cat /sys/module/nvidia/version
 lspci -nnk | grep -iA2 VGA
```Does your description mean that changing thedriver had no effect? - after rebooting you still have the same difficulty in getting to a GUI and a blank screen?

At the moment I cannot tell whether you are using the 'post-release' nvidia driver, or the default nouveau driver. The later would have been the next thing to try.

Chao!, **bogan**.

---

### Post by Btru on 2012-07-02
Hey Bogan,

When i ctrl-alt-F1 (F1-F6) in the GUI, I get a black screen with a purple stripe across the top... I think something is supposed to be displayed, but something is just going wrong with the video for some reason.
Nothing happens when I am in the blank purple screen at startup.

The commands give me:
```

brandon@True:~$ cat /sys/module/nvidia/version
295.49
brandon@True:~$  lspci -nnk | grep -iA2 VGA
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GF116 [GeForce GTX 550 Ti] [10de:1244] (rev a1)
    Subsystem: Giga-byte Technology Device [1458:3536]
    Kernel driver in use: nvidia
brandon@True:~$ 

```And, yes, the exact same thing happens even with the driver change. For some reason, though, those random commands in the command line in GRUB let me get back to a GUI fortunately. Any idea why?

Thanks, 
Brandon

---

### Post by bogan on 2012-07-02
Hi!, **Btru,**

You Posted:>  And, yes, the exact same thing happens even with the driver change. For  some reason, though, those random commands in the command line in GRUB  let me get back to a GUI fortunately. Any idea why?I have no idea what any of those grub Cli cmd's might do, other than give time for some other process in the booting sequence to complete.

If you want to pursue the connection you could try just switching to the grub Cli and back again, without entering anything, or entering those commands one at a time and re-booting, to see if there is a predictable response.

Have you edited the /etc/default/grub file { to put 'nomodset' in } and run sudo update-grub, in order to make that permanent?```
gksu gedit /etc/default/grub #  save and close the gedit window
sudo update-grub # and reboot
```Taking that effect into account, is the boot-up now consistent and acceptable?

I had previously suspected the problem was with lightdm or the Greeter, but I can not see why grub cmd's should influence those.

Chao!, **bogan**.

---

### Post by Btru on 2012-07-07
Sorry for the late reply, but yeah I tested all of the commands separately and in different combinations, but it seems to only work when I do the commands in that specific order... Weird...

Anyways, I think this is fine... a stable boot-up is all I really need even if it takes a few extra seconds.

Thanks so much for your help!

---

### Post by LexRoss on 2012-10-25
This problem hit me after update to 12.10 using neoveau driver (default).
 I get purple and then black blank screen at first boot and every second one, as the kernel driver fails to load and I have to cut off the power. Then it boots as normal.

I tried "nomodeset" kernel parameter, and this results in neoveau driver to set the maximum resolution of 1024x768 whereas I need 1280x800 on my laptop screen. Not good.

Next, I installed nvidia-current driver which gives me no splash screen, same 1024x768 resolution in X and no window manager and compiz after login.

My card is Nvidia GeForce 7000M / nForce 610M] (rev a2)

Anyone has got the same problem?

---

