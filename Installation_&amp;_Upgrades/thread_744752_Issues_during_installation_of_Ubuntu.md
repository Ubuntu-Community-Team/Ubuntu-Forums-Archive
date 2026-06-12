---
title: "Issues during installation of Ubuntu"
date: 2008-04-03
forum: Installation &amp; Upgrades
---

### Post by Aninda on 2008-04-03
I am trying to install Ubuntu 7.10 on a notebook running XP Home. 
The processor is Turion 64 x2 with 1 GB RAM. I am using the i386 version of Ubuntu.

During installation, I initially get an error message BIOS BUG#81 found but the system automatically goes into the Welcome Screen where I select the option for installing /running live CD. The initial steps seem to run ok when I get messages that the drivers aare being loaded, etc. The last message I get is "Starting GNOME Display Manager" after which I get a blank screen. The color of the screen starts to change till it tuns black and the PC stops responding. I have to shut of the power button.

I tried to use the option of installing it with the safe display mode but the installation stops in the same way. Am I using the correct version of Ubuntu or should I get the 64 bit version? Or is there some other problem? Please help

---

### Post by dstew on 2008-04-04
> Am I using the correct version of Ubuntu or should I get the 64 bit version?No, you are using the correct version. Your problem is that the video drivers on the live CD are having trouble handling your display.

There are several ways to work around this. You can try some kernel parameters. You add these to the kernel line, press F6 at the opening menu. For display problems, try **vesa=force** or **vga=791**. But, probably the most direct way to get around this problem is to use the Alternate Install CD. It installs the same Ubuntu desktop using a text-based installation interface that almost always works. You get it from the [Ubuntu download page]("http://www.ubuntu.com/GetUbuntu/download"), just check the box below the Start Download button.

---

### Post by Aninda on 2008-04-04
Thanks for your reply. I followed your advice to try and install by  using the alternate cd. Installation went successfully so that now I have both Win XP and Ubuntu on my notebook. However I face the same problem when I try to boot using Ubuntu. The screen goes into some weird color and finally blank. What can be done in this case?

---

### Post by dstew on 2008-04-05
This means the display driver in your installed Ubuntu is not working with your display hardware properly. To get a useable desktop, and try to reconfigure, do the following.

When you get to the blank screen, press ctrl-alt-F1. This will get you a text-based interface, with a command line. On the command line enter this command:```
sudo dpkg-reconfigure xserver-xorg
```This begins a text-based reconfiguration of your xserver, the software that runs the graphical desktop. Answer the questions the best you can (read the explanations). Usually the default answers are correct. When you get to the part about the display configuration, select the **vesa** driver. When you are done configuring, press ctrl-alt-backspace. This key combination re-starts the xserver. You should get a useable desktop.

Once you have your desktop, if you are connected to the internet, you should be able to update your system software. If you wait 5 minutes or so, you usually get an update notification. Or, you can go right away to System --> Administration --> Update manager. Do the updating. After you have finished updating, look in System --> Administration --> Restricted Drivers Manager, and see if you can install a restricted driver for your display. If so, install it, then reboot. If not, there are some things we can try to get you a better driver for your display. Post back your results.

---

### Post by Aninda on 2008-04-05
I get the initial Ubuntu splash screen after selecting Ubuntu from the Grub menu. I rogress bar shows the system to be loading but the next screen continues to take the strange color but does not respond to any input. 

Pressing ctrl+alt+f1 does not seem to help. I can not get a text based interface at this point.

I tried to alter the sequence by using ctrl+alt+f1 just after selecting the OS from the grub menu. Now a lot of text commands are displayed on the screen very fast. I can not stop the stream of commands to input the code suggested by you. And after the stream of commands, I again have the same strange screen.

I am absolutely new to Linux so maybe I am not doing something which I should be. Where am I getting this wrong somehow? Again thanks for your replies. I am at a complete loss here.

---

### Post by Pixcalcis on 2008-04-06
im trying to put ubuntu on a friends computer...also Turion 64 x2 with an Nvidia card.

Exact same problem:
I had to use the alternate Cd to install and his computer also will begin to boot but will go to a blank screen and i am unable to do anything. I tried pushing Crt Alt F1 before this point but of course, it just went into the text mode and continued booting up and once it gets to "Starting Gnome Desktop Manager", it will go to the blank screen.  
Any further help on getting input prompts before the blank screen comes up will also be appreciated by me.



I have one idea but i have to wait until i can get back to his computer tomorrow.

---

### Post by dstew on 2008-04-06
> I get the initial Ubuntu splash screen after selecting Ubuntu from the Grub menu.Try selecting Recovery Mode from the boot options. That should get you the command line, and you can do dpkg-reconfigure xserver-xorg.

To Pixcalcic: Wait for a while after the blank screen comes on before pressing ctrl-alt-F1

---

### Post by Pixcalcis on 2008-04-06
how long of a wait are we talking? I just let it sit there for a bit before i tried, didnt work and tried later multiple times. It sat there for over 6 minutes.  Should it be longer than that?

I also tried to boot in recovery mode and the screen get stuck with the following text:

[0.484000]   ..TIMER : vector =0x31 apic1= pin1=2 apic2=-1 pin2=-1


it stays here and doesnt  move for atleast a couple minutes. My friend had to leave for a bit so I asked him to just leave this screen up and see if it will eventually progress or something.

---

### Post by dstew on 2008-04-06
Is Ubuntu installed on the hard disk, or are you having trouble getting the installation CD to run? In either case, it looks like there is an interrupt problem. You can turn off the Advanced Programmagle Interrupt Controller by adding **noapic nolapic** to the kernel line, either in the grub menu item, or on the Live CD kernel by pressing F6 at the first menu.

---

### Post by Aninda on 2008-04-06
Thanks for the last update. Adding noapic nolapic to the kernal line solves the problem.

---

### Post by Pixcalcis on 2008-04-07
If you were referring to me, Ubuntu is installed on the hard disk

im not sure how to add things to the kernel line from the Grub Screen but I will try it via the CD method you mentioned tomorrow  and hopefully that will work for me as well.  Thank you very much for your help thus far.

---

### Post by dstew on 2008-04-07
I was referring to you, Pixcalcis. To add the options temporarily (to see if they work), at the grub menu highlight the kernel you want to boot, but instead of pressing 'enter', press 'e'. This gets you into edit mode. Now, highlight the kernel line of the menu item, and press 'e' again. Add the kernel parameters to the end of the kernel line, press 'enter', then 'b' to boot.

If this works, you can add them permanenty by editing your /boot/grub/menu.lst file. You simply place them at the end of the #kopt line (near the top), then run **sudo update-grub**. Next time you boot, the kernel options will be added to the kernel line automatically.

---

### Post by Pixcalcis on 2008-04-07
i havent had a chance to try this  yet ( i will in a few hours) but i was just wondering about the fix and had some questions about it.  I was wondering if you could satiate my curiosity about it.

what is the usual purpose of the APIC?   What would ORDINARILY cause it to interrupt your boot (if that is its main purpose)?  If i turn it off permanently will it have any other negative effects on his system?

---

### Post by dstew on 2008-04-07
The APIC was designed with multi-processor systems in mind, to give the system more flexibility in handling interrupts, and to allow the use of many more interrupts. See [this Wikipedia]("http://en.wikipedia.org/wiki/Intel_APIC_Architecture") article. Most single-processor system do not get any performance enhancement from APIC, and it is often not implemented correctly in the hardware. The only time you might miss APIC is with a multi-processor system that was doing heavy lifting, like video editing, or big-time gaming. But, you would need a board with Intel-compliant hardware for it to work properly.

---

### Post by Pixcalcis on 2008-04-07
oh so basically  if I turned off APIC to my laptop,which is an Intel Core Duo i may tell a difference,  but since his is an AMD processor then  APIC wouldnt help anyways.  The wikipedia article is still loading  :( he has horrible wireless signal in his room but i willl check it out when i get back to mine.


Alright it worked wonderfully. Thank you very much!!!

---

