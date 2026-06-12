---
title: "Complete Ubuntu + n00b Installation Problems"
date: 2012-07-13
forum: Installation &amp; Upgrades
---

### Post by geekyomega on 2012-07-13
Hi Forum Readers, 

I am completely new to ubuntu, linux, and have been learning terminal commands, but still very basic. I just built a PC with mid-level parts, nothing cutting edge and trying to learn Ubuntu too. In short, I can't get it to install. 

**This is what I have done: **

1. Read the Ubuntu Installation and other material (RTM)
1. Googled my problem
2. Searched this forum 

I found a bunch of things about ubuntu commands and things I don't understand. Besides this, they aren't relevant to what I am experiencing. 

**This is my problem: **

1. Installed windows installer on W7 and ran it. When it reboots, I see a black screen with a white flashing underscore line flashing really fast.  When I reboot again, it asks me if I want to to boot into Windows 7 or Ubuntu. If I select Ubuntu, it then becomes a big purple screen. 

2. I downloaded the Ubuntu iso and burned it onto DVD. I booted into the CD and it showed me some options. I pressed 1. Install Ubuntu and then got a black screen and nothing was happening. 

I am so new to Ubuntu and this process I have no idea what could be happening. I suspect it has something to do with hardware (based on my googling) but not sure what could be doing it? I honestly really don't know what is going on. 

**Here is my build: **

CPU: Intel Core i5 2500
RAM: GSkill 8G  
Hardrive: WD 1TB HD
Graphics: VGA EVGA 01G-P3-1556 GTX550
Monitor: Acer 23 inch (Two of them plugged into graphics card)
Motherboard: Gigabyte GA-Z77
DVD-RW: Asus 
Wireless Card: Wintec PCI-N (Most generic part in build and temporary)

I really can't even figure out where this is going wrong and what could be causing this? I am not even to a point where I can try to fix this as I can't even get Ubuntu to install and boot right. Please help. 

Respectfully, 
GeekyOmega

---

### Post by steeldriver on 2012-07-13
I think that's most likely a problem with the nouveau video driver - you can try booting with the 'nomodeset' option (this is a kludge - it doesn't fix anything but it forces the X server to fall back to a generic VESA driver):

See here for instructions:

[http://ubuntuforums.org/showpost.php?p=10069997&postcount=1](http://ubuntuforums.org/showpost.php?p=10069997&postcount=1)

Once you are booted with the VESA driver, you can try to install a proprietary driver that that works - I'm not up with the latest drivers so I'll leave that for someone else to advise

---

### Post by geekyomega on 2012-07-13
Thanks. I think would help and I checked the link you sent me. I am not given any of the options shown on that link you sent me? Scratching my head there. My screen is telling me that I have GNU GRUB version 1.99-21unbuntu3. It does say, "error: prefix not set" before it shows me the GNU GRUB menu when I boot up the machine. Not sure why. So it might be a battle to even change the nomodeset? 


In the meantime, if anyone can instruct me on what is going on with that?  I can add instructions by typing 'e' first, but I don't know what kind of terminal commands I should give grub to tell it to install on nomodeset? I looked too, but most of that seems to be for when it is already installed? Getting lost. 

Warmest Regards and Many Thanks. 

Respectfully, 
GeekyOmega

---

### Post by jmfal on 2012-07-13
Welcome to Ubuntu

Click on the link that Steeldriver gave you and follow the instructions starting at::

[SIZE=4]**How to temporarily set kernel boot options on an installed OS (not wubi)**[/SIZE]

You need to use the up/down arrows on keyboard
to navigate to right line.  The "end" key should be by the print screen key

---

### Post by geekyomega on 2012-07-14
> **jmfal said:**
> 
You need to use the up/down arrows on keyboard
to navigate to right line.  The "end" key should be by the print screen key

Thanks. I appreciate your politness. I realize these are very *newbie* questions and appreciate the gentle help. And yes, it worked! In case anyone google's this in the future, try that link and work through it. Except crtl + x did not work. I had to hit f10. Just an FYI for others. 

**New Problems**

I went through the installation, and now I am just having problem and problem. 

Problem 1: 

This is where I am at now. I installed it twice and then it wants to "restart". After the restart, it gives me the option to boot from Windows or Ubuntu. So I choose Ubuntu. It then gives me the message:

"Windows failed to start." blah blah blah to 
" File: \ubuntu\winboot\wubildr.mb 
Status: 0xc000225
Info: The selected entry could not be loaded because the application is missing or corrupt" 

I know this is because it can't find the loader, but why? I followed advice found here: 
[http://www.techspot.com/community/topics/step-by-step-beginners-guide-to-installing-ubuntu-11-10.172128/]("Step by Step") I know that is for a previous version, but it is so close it should work. 

Any idea why this is happening? Sorry. 

Respectfully, 
GeekyOmega

---

### Post by jmfal on 2012-07-14
Are you using wubi??

You should have stated that from the start.

---

### Post by i argor on 2012-07-14
> **geekyomega said:**
> It does say, "error: prefix not set" 

this relates to bios setting, boot mode..

you must find something in the bios for boot mode hueifi or so.. you need to set it to legacy or at least when both modes anabled.. at order to legacy first...

i had the same problem... i dont know how to spell this stupid new bios feature.. it is a new version of MBR... maybe some one else nows exactly what i mean... i would need to reboot my machine now to look in bios for correct spelling :D I also bet you do have so called EFI Partition...

edit:

i think it was UEFI, switch that of in Bios and set it to Legacy then the message prefix not found schould disappere and you schould get the normal install menü screen

But i dont know how the change of the settings will effect your existing windows installation

---

### Post by geekyomega on 2012-07-16
Hi All, 

I finally got it installed. A lot of things went wrong for me, but this is what I should have attempted from the start.  This is what I did:

(Assumes you already have installed Window 7 on the machine. Please see elsewhere about partitioning the drive so as you can install the OS. I recommend, if you are first time user, to let
Ubuntu make it's own partition. Otherwise, you can create your partition in W7 and then install 
Ubuntu on that, it's beyond the scope of what I want to write here though). 

1. Made a CD for Ubuntu 

2. Restarted the machine and used Wubi to install Ubuntu 

3. Before you install Ubuntu, if you have Nvidia, type e to change boot options. See the first link 
    given on this thread. 

4. Be sure you are connected to the internet with a wired connection. Make sure you allow all options for downloading, something like install updates as you go and another option to go grab propriety software. 

5. Once the machine installs. Be very sure NOT to try to update the grub file. If you did step 4, this should be not be necessary. Actually, if you do try to update GRUB, kiss your stable OS goodbye. It didn't work for me. 

6. Let the machine reboot. It should work now. 

At this point, Ubuntu told me it grabbed the Nvidia drivers. My next job is to figure out how to make it work for dual monitors. I have two 23 inch Acer monitors. However, that is beyond the scope of this thread. So I consider this all answered. Thank you so much for all your help. This was a rough baptism and I almost considered using a different linux OS, but glad I stuck with it. 

Respectfully, 
GeekyOmega

---

