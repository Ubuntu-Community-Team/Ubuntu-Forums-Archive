---
title: "Karmic black screen, then errors in GRUB and no GRUB menu"
date: 2009-10-17
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by peachtree195 on 2009-10-17
I reinstalled the system to Karmic yesterday in the night by typing in the command line: update-manager -d. The problem that i had in the morning right away was the black screen and no GUI loaded at all. I tried rebooting a couple of times and sometimes there would be sound of ubuntu starting (just no screen) and sometimes nothing just black. System was reporting it could not open display. The thing has been mentioned in some threads
 [[SOLVED] Karmic Alpha 5 Install - No Display Found - Ubuntu Forums]("http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=7895898")
but because i had a graphic card that apparently was not in the software support list (GeForce105M) i was a bit confused what command line to apply here - at the end i decided that i would install nvidia-glx-185

It is maybe worth mentioning that i have had some previous minor GRUB problems that were never solved - applying different values for default booting system in boot/grub/menu.lst never brought any change - it was always by default windows Vista. [http://ubuntuforums.org/showthread.php?t=1292774](http://ubuntuforums.org/showthread.php?t=1292774)

So i tried booting ubuntu with a plan of executing the sudo apt-get install nvidia-glx-185 command but this time after choosing UBUNTU but before full booting i tried pressing ESC to see what linux kernel loading options i had. It went to the menu that showed me some options of menu.lst pathways, and whichever i chose it was bringing me to GRUB command line and it kept returning "load kernel first".

I got frustrated and thought I might use ubuntu live CD Ubuntu Jaunty 64-bit - there was no option of starting a recovery of any kind. So i booted through Windows and started the CD. I thought that the only thing that could save me now is reinstall to the version that was relatively working fine with me. The installer said it has to uninstall the previous Ubuntu. I clicked 'YES' and after a few seconds it said it can't locate something and has to abort. Maybe it has started deleting something?

Now: there is no grub menu at startup at all and I am stuck with Karmic that has some grub problems and I can't even load to try the driver update for my display problems.

Any ideas how to bring things back now? 
I don't really enjoy working in Windows anymore, I would really like to go back to Ubuntu.

Should i wipe the sectors for ubuntu and reinstall ubuntu again from scratch including GRUB? Will it let me do this now? And if so - is it okay to go back to Jaunty or it is not recommended?

Thanks for all help!

---

### Post by VMC on 2009-10-17
> **peachtree195 said:**
> I reinstalled the system to Karmic yesterday in the night by typing in the command line: update-manager -d. The problem that i had in the morning right away was the black screen and no GUI loaded at all. ...
 
but because i had a graphic card that apparently was not in the software support list (GeForce105M) i was a bit confused what command line to apply here - at the end i decided that i would install nvidia-glx-185

It is maybe worth mentioning that i have had some previous minor GRUB problems that were never solved - applying different values for default booting system in boot/grub/menu.lst never brought any change - it was always by default windows Vista. 

So i tried booting ubuntu with a plan of executing the sudo apt-get install nvidia-glx-185 command but this time after choosing UBUNTU but before full booting i tried pressing ESC to see what linux kernel loading options i had. It went to the menu that showed me some options of menu.lst pathways, and whichever i chose it was bringing me to GRUB command line and it kept returning "load kernel first".

I got frustrated and thought I might use ubuntu live CD Ubuntu Jaunty 64-bit - there was no option of starting a recovery of any kind. So i booted through Windows and started the CD. I thought that the only thing that could save me now is reinstall to the version that was relatively working fine with me. The installer said it has to uninstall the previous Ubuntu. I clicked 'YES' and after a few seconds it said it can't locate something and has to abort. Maybe it has started deleting something?

Now: there is no grub menu at startup at all and I am stuck with Karmic that has some grub problems and I can't even load to try the driver update for my display problems.

Any ideas how to bring things back now? 
I don't really enjoy working in Windows anymore, I would really like to go back to Ubuntu.

Should i wipe the sectors for ubuntu and reinstall ubuntu again from scratch including GRUB? Will it let me do this now? And if so - is it okay to go back to Jaunty or it is not recommended?


Boot using livecd. Then output ```
sudo fdisk -l
``` ```
sudo blkid
```

You mentioned about menu.lst. Do you know if in fact your using grub2 or grub-legacy? If you know for sure output either grub.lst or grub.cfg. I'm assuming grub.cfg since you said you installed karmic and not that it was an upgrade.

We will see from the output of fdisk what's next.

The load linux first usually means wrong or missing partition number.

---

### Post by peachtree195 on 2009-10-17
I was upgrading the system to Karmic from recently installed Ubuntu Jaunty 9.04, the iso CD downloaded 3 weeks ago, but i was not paying attention to what kind of Grub came with it.
[IMG]file:///C:/Users/baa-win/Desktop/IMG_2517.png[/IMG][IMG]file:///C:/Users/baa-win/Desktop/IMG_2517.png[/IMG]

---

### Post by peachtree195 on 2009-10-17
and after booting from liveCD this is what i got from terminal:

grub> find /boot/grub/stage1
find /boot/grub/stage1

Error 15: File not found

and when I put
sudo gedit /boot/grub/menu.lst

it shows a completely empty file, blank, white, nothing

---

