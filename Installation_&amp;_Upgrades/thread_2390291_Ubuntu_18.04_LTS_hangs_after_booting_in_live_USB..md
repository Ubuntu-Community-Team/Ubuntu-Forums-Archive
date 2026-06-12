---
title: "Ubuntu 18.04 LTS hangs after booting in live USB."
date: 2018-04-27
forum: Installation &amp; Upgrades
---

### Post by parag-93 on 2018-04-27
I've downloaded newly released Ubuntu 18.04 LTS. I've booted using USB drive. During booting, it shows the following-
[FONT=&amp]
Couldn't get size: 0x800000000000000e[/FONT]
[FONT=&amp]MODSIGN: Couldn't get UEFI db list

After that it boots to the Ubuntu and freezes after about one second is passed. Only mouse cursor moves and nothing works. I am new user to Ubuntu and not sure about what causes this problem. My laptop has AMD graphics card. Is this the thing that causes the problem? I'm not sure. So, please help![/FONT]

---

### Post by Dennis N on 2018-04-27
You can read more talk about these messages here:
[https://ubuntuforums.org/showthread.php?t=2380700](https://ubuntuforums.org/showthread.php?t=2380700)
But, I doubt (but can't say for sure) that they have anything to do with the problem you describe. Keep monitoring your thread for other responses that may help solve it.

---

### Post by arthurnobrega on 2018-04-27
Same problem here guys. How can I check the logs If when Ubuntu Live CD loads It hangs?

---

### Post by parag-93 on 2018-04-28
I've just used 'nomodeset' during boot to ignore the graphics card and it's successfully booted. Now what should I do? Do I have to always use 'nomodeset' during boot? Or, there are some ways to install proper driver for my graphics card so that I don't have to use 'nomodeset' anymore. My graphics card information is given below-

```
 *-display UNCLAIMED       
       description: Display controller
       product: Sun XT [Radeon HD 8670A/8670M/8690M / R5 M330 / M430]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi cap_list
       configuration: latency=0
       resources: memory:a0000000-afffffff memory:c2000000-c203ffff ioport:4000(size=256) memory:c2040000-c205ffff

```
Please, anyone tell me that which driver should be appropriate for me.

---

### Post by djefo on 2018-05-06
hey parag-93

i have the exact same problem just with an nvidia card. one quick question as i am also quite new to ubuntu, espacially with graphics cars. how did you use nomodeset during booting? i tried to do it but could not find it. 

thanks

---

### Post by satansbratenmcfly on 2018-05-16
same thing here. I hope at least.
I created a USB live stick with ubuntu 18.04 (from yesterday)
I boot the USB stick, get the normal expected menu where I choose "Install Ubuntu"
and the  I get the MODSIGN error message, nothing moves a bit
I have to shut down the PC and boot from scretch.

**NOTE**: I am running ubuntu 18.04 on this machine, updated from 16.04, but I want to have a new, fresh, clean install - don't ask why, just accept it ;)

Why is installing Ubuntu 18.04 so complicated, using the distro since 6 years and never experienced such an issue...

System: Zotac EN1070K
[B]i5 6400T
Nvidia GTX 1070[/B]
latest BIOS available
latest microcode in place (according to dmesg |grep microcode)
latest Nvidia driver as per repo (no experiments here)

In BIOS:
secure boot is disabled (tried also enabled with standard keys and custom) always the same result

---

### Post by sudodus on 2018-05-16
1. There is a tutorial post how to add boot options at this link,

[Boot options](http://ubuntuforums.org/showthread.php?t=2230389&p=13370808#post13370808)

2. There are current linux versions of proprietary drivers for nvidia cards, and if you find one, that works with your card, you will release the 'full power' of it.

3. There are no current proprietary linux drivers for Radeon /AMD/ATI cards, but the current built-in linux drivers (free) work with many but not all such cards.

---

### Post by satansbratenmcfly on 2018-05-18
thanks, in principal this sounds like a good tip, most like the  nomodeset will behelpful since I end up with a black screen when  selecting any option from the "try/install/OEM install" screen from the  USB stick.
However, the tutorial linked is not not helping that much  as it indicates to press any key when this one screen appears that will  allow for the "advanced options" with the F-keys.
I do not get this screen.
When  I boot from the BIOS into my Ubuntu Live USB stick, it immediatly shows  the selection screen to either try, install, OEM install or test  memory.
The only options available are "e" to edit - maybe i can use this - but how?
Or "c" for the (I think) Grub console - both work, but I do not know how to use them :(

Any further advice you can give on this - thanks.

---

### Post by sudodus on 2018-05-18
Yes, use 'e' to edit the line which starts with 'linux' (add 'nomodeset' (without quotes) near the end (before the dashes). Leave a space before and after the word 'nomodeset').

It is described with more details in a link from the link in my previous post.

---

### Post by ascii1011 on 2018-05-22
Hi all,

I have a similar issue.

Trying to install Ubuntu 18.04 with a MSI Tomahawk b350 board + Geforce CTX 1050 video card and getting something like this:

Couldn't get size: ...
MODSIGN: Couldn't get UEFI db list
Couldn't get size: ...

ubuntu splash screen comes up, goes through changing 7 of the dots under the ubuntu logo to white... then freezes and keyboard stops working...

I have tried all combinations for boot sequence and have no "secure boot" options...  and the manual seems to be fairly useless as usual :)

I was previously able to install Ubuntu 16.04... can't remember what previous incantation I performed to get it to install... these companies are driving me crazy with the complexity of os installs now...


Thank you :) and Any help would be greatly appreciated

---

### Post by borev41 on 2018-05-25
I Create an USB key for Ubuntu Mate 18.04 
I try it on my computer : No boot

I obtain only this error message :

[ 0.000000] [Firmware Bug]: TSC_DEADLINE disabled due to Errata ; please update microcode to version: 0xb2 or later
[ 0.106253] ACPI Error: Needed type [Reference], found [Integer ] 00000000276ab184 (20170831/exresop-103)
[ 0.106262] ACPI Exception: AE_AML_OPERAND_TYPE, While resolving operands for [Store] (20170831/dswexec-461)
[ 0.106279] ACPI Error: Method parse/execution failed \_SB.PCIO.LPCB.ECO.CPUS,AE_AML_OPERAND_TYPE (20170831/psparse-550
[ 0.106287] ACPI Error: Method parse/execution failed \_SB.PCIO.LPCB.ECO.SASU,AE_AML_OPERAND_TYPE (20170831/psparse-550)
[ 0.106295] ACPI Error: Method parse/execution failed \_SB.PCIO.LPCB.ECO.ECMI, AE_AML_OPERAND_TYPE (20170831/psparse-550)
[ 0.106302] ACPI Error: Method parse/execution failed \_SB.PCIO.LPCB.ECO._REG, AE_AML_OPERAND_TYPE (20170831/psparse-550)
[ 0.244341] platform MSFT0101:00: failed to claim resource 1: [mem 0xfed40000-0xfed40fff]
[ 0.244348] acpi MSFT0101:00: platform device creation failed: -16
[ 8.966831] nouveau 0000:01:00.0: bus: MMIO read of 00000000 FAULT at 022554
[ IBUS] 
[ 8.974084] nouveau 0000:01:00.0: bus: MMIO read of 00000000 FAULT at 10ac08
[ IBUS]
 
BusyBox V1.27.2 (Ubuntu 1:1.27.2-2ubuntu3) built-in shell (ash)

Enter 'help' for a list of built-in commands.

(initramfs) Unable to find a medium containing a live file system

I must add that using the method I install Ubuntu Mate without problem

---

### Post by borev41 on 2018-05-25
I add this post only to suscribe this topic

---

### Post by borev41 on 2018-05-25
Sorry, the last line of my precedent message is not correct. I want to say :

that using the same method I install Ubuntu Mate** version 16.04** without problem on the same computer

Borev41

---

### Post by sudodus on 2018-05-25
@borev41,

Then I suggest that you stay with Ubuntu Mate version 16.04 at least until the first point release 18.04.1 LTS (late July or August). By that time there will be several bug fixes and it is more likely that the new point release will work in your computer.

---

### Post by sudodus on 2018-05-25
@ascii1011,

I am not sure you have a similar problem, so I suggest that you create an own thread with a good descriptive title and as much information as possible in the first post.

---

### Post by gokulprasath on 2018-09-26
The 'nomodeset' worked for me too. Please see this post to understand how to set thisin the grub window before boot - [https://askubuntu.com/questions/38780/how-do-i-set-nomodeset-after-ive-already-installed-ubuntu](https://askubuntu.com/questions/38780/how-do-i-set-nomodeset-after-ive-already-installed-ubuntu)

---

