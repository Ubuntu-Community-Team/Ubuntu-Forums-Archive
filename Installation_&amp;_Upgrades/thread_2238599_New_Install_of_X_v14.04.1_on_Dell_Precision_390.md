---
title: "New Install of X v14.04.1 on Dell Precision 390"
date: 2014-08-08
forum: Installation &amp; Upgrades
---

### Post by Rick St. George on 2014-08-08
Does anyone have any suggestions as to how to get Xubuntu 14.04.1 to install on a Dell Precision 390 which has a dual core Intel with 2MB Ram and 1TB HD ? ? ?

I get a blank screen after seeing the first screen showing XUBUNTU  14-04.

Thanks!
Rick

---

### Post by grahammechanical on 2014-08-08
Do you get this blank screen when trying to run the Xubuntu live session? Or is this after Xubuntu has been installed? You might need to set an F6 boot option.

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Look down the page at that link and study section 6 - F6. You could try the nomodeset option.

Regards.

---

### Post by kc1di on 2014-08-08
Hi Rick St. George,

You need to install the correct Nvidia Driver for you card. I believe it's a Nvidia Quadro FX 4400 -- if so you can install it by
hitting the tab key when ubuntu just begins to boot. you should see an option of Ubuntu advanced select that then select recovery mode.  
it will take you to a screen that has an option for network click on it.  when it's finished setting up the network select Root it will take you to a root terminal
now install the Nvidia Driver by typeing the following command
```
apt-get install nvidia-331
```

---

### Post by Rick St. George on 2014-08-08
No INSTALL - Can't even get it to install.... Don't see the Options Page, as previously mentioned, I ONLY see UBUNTU and then blank screen and nothing. I installed a PCI video card for VGA monitor. The Precision 390 has a dual core INTEL 1.86 Ghz 64 bit CPU. Downloaded the 64 bit PC (AMD64) Desktop Image aka; (xunbuntu-14.04.1-desktop-amd64.iso).  Hopefully this is supposed to work with a INTEL 64 bit cpu and not just an AMD 64bit cpu. I see not version for INTEL 64 bit cpu.

Any help would be appreciated.  Thanks!

---

### Post by kc1di on 2014-08-09
Ok this is a live boot session then your trying to boot.  The steps that grahammechanical  gave you should work. and get you to the GUI , where you can install.
Some machines are very fast and you have to hold down the Tab (or some other key) at exactly the right moment.  But you should get to the options page 
hit f6 and select ```
nomodeset
```

---

### Post by Rick St. George on 2014-08-09
Got to that menu using TAB, and F6, selected nomodset - but still the screen blinks and then goes black. After waiting for 5 - 10 minutes (waited as long as 15) I hit the ESC key and then I see some shutdown notices on screen. I can't seem to get pass the point where the screen blacks out and it stops reading from the DVD. I get the impression that it is waiting on input, but I can't see anything via the black screen.

Any more suggestions?  I would really love to get this Dell Precision 390 up and running for my buddy. Since we have two of them, I'll fix the other one up for me once we figure it out. Using a 1TB HD - should I format it first?  Maybe try installing WinXP and the Xubuntu??  I have the 1 TB HD on a SATA connection, avoiding the PATA connection. Could this be for RAID only? I am stumped!

Thanks!

---

### Post by Rick St. George on 2014-08-09
I tried with v13.10 64 bit and do F6, NOAPIC, NOMODESET, and get ... "KVM: Disabled by BIOS".
Any idea what that means ? ? ?

Thanks!

---

### Post by kc1di on 2014-08-09
KVM disabled by BIOS is normal and not a  problem.
KVM stands for Kernel Virtual Machine.  And it's most likely turned off in your bios settings.

---

### Post by Rick St. George on 2014-08-09
Installed WinXP No Problem. How come I cannot install Xubuntu 14.04.01 or v13.10 64 bit versions on this Dell Precision 390 ? ? ?

Any suggestions?
Thanks!
Rick

---

### Post by Rick St. George on 2014-08-09
Went back to UbuntuStudio 64bit v12.04.5, with NoAPIC, NoModeSet, and installed No Problem .... EXCEPT that now WinXP will not boot. Will post in new thread.
Thanks!

---

### Post by kc1di on 2014-08-10
you can most likely fix the boot problem with boot-repair found [here.]("https://help.ubuntu.com/community/Boot-Repair")

---

### Post by Rick St. George on 2014-08-10
Boot Repair did not fix .... I get a black sreen showing "Cannot Display this Video Mode - Optimum Resolution 1280 x 1024 60 Hz". However, upon Boot-up, I arrow down 3 times and get RECOVERY MODE. How many times should I arrow down to get to WinXP ???  Anyone know?  Strange can't see the first boot screen. After about 15 -20 seconds, it boots right up into UbuntuStudio.

Any suggestions?
Thanks!

---

### Post by Rick St. George on 2014-08-10
Temporary Fix - - - Assuming the Screen is there, just can't see it, I arrowed down 3 and got the Test Memory screen. Rebooted and arrowed down 5 times and Entered Win XP. So both are installed just have to know what you want to boot into. 

Thanks everyone! Will mark SOLVED.
Rick

---

### Post by kc1di on 2014-08-10
go to a terminal and open an editor as root ```
sudo gedit [\CODE] for ubuntu.

then open /etc/default/grub

when it opens scroll down until you find the following line:
[CODE]# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

```

change the #GRUB_GFXMODE=640x480 to read like this ```
GRUB_GFXMODE=1024x768 
```
save the file then exit it.
now type this command
in the terminal 
```
sudo update-grub
```
then reboot. you should now be able to see the grub menu. 
good luck

---

### Post by Rick St. George on 2014-08-12
Thanks KC .. In GRUB tried both - 1024x768 and 1280x1024 (which is what it reads on the screen) but didn't work. I still get a black screen with "Cannot Display this Video Mode - Optimum Resolution 1280 x 1024 60 Hz" When Ubuntu or WinXP boots up, the display is 1280x1024 in both. In WinXP is shows that is Max. and it is an ATI 3d Rage Pro PCI.

Thanks!

---

