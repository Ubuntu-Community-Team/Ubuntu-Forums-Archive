---
title: "Clean install done &quot;wrong&quot;"
date: 2016-08-26
forum: Installation &amp; Upgrades
---

### Post by dreaddisk on 2016-08-26
Hi, I'm new to linux use and I want to present my case that is making my laptop totally useless right now. *The next QUOTE is from the user "user534381" from askubuntu, who has the same problem as me, so if you have the chance also cooment in his thread :*> I downloaded the ISO file for Ubuntu and put it on a usb drive using  Rufus. I completed the installation, and then it asked me to restart my  computer. I did so, and it launched back up to the black screen where  you choose to try without installing, install, etc. I figured this was  because the computer was still booting the flash drive, so I restarted  it without the drive, and I get a black screen that says "Reboot and  select proper boot device". I did select my hard drive, so I don't know  what I'm doing wrong. This has rendered the computer completely useless,  as it was a clean install. Any help is greatly appreciated!

After that incident, at the next day I boot my computer on *Legacy *mode which let me with this kind outcome:

> [ATTACH=CONFIG]270871[/ATTACH]

Now I dont know what to do, when I type in *"Ubuntu" *it goes to a black screen and it froze there.

Anybody can help me?

---

### Post by oldfred on 2016-08-26
Is system UEFI or BIOS.
You mention you installed in Legacy mode. Is system then set to boot in Legacy/BIOS/CSM mode, not UEFI boot mode? 
Do you have another system installed and is it in same boot mode.

Black screen is most often related to video driver.
What video card/chip do you have?
Can you boot recovery mode (under advanced options)? To at least command line/terminal in Ubuntu?

 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

---

### Post by dreaddisk on 2016-08-26
> **oldfred said:**
> Is system UEFI or BIOS.
You mention you installed in Legacy mode. Is system then set to boot in Legacy/BIOS/CSM mode, not UEFI boot mode? 
Do you have another system installed and is it in same boot mode.

Black screen is most often related to video driver.
What video card/chip do you have?
Can you boot recovery mode (under advanced options)? To at least command line/terminal in Ubuntu?

 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

I installed in UEFI. I change to Legacy mode to take off the secured boot. The installation was in an Acer aspire one 11. I dont' know what kind of integrated graphics it has.

---

### Post by grahammechanical on 2016-08-26
What you are seeing is the Linux/Ubuntu boot loader that is simply called Grub. That may be normal or not. If Ubuntu is the only OS on the machine then the Grub boot menu is usually hidden as it is not needed. If there is more than one OS then it is usual for the Grub boot menu to appear. Your boot menu does not show any OS except Ubuntu. And that could be because Ubuntu is installed in Legacy mode but the other OS is installed in EFI mode.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Regards

---

### Post by dreaddisk on 2016-08-26
> **grahammechanical said:**
> What you are seeing is the Linux/Ubuntu boot loader that is simply called Grub. That may be normal or not. If Ubuntu is the only OS on the machine then the Grub boot menu is usually hidden as it is not needed. If there is more than one OS then it is usual for the Grub boot menu to appear. Your boot menu does not show any OS except Ubuntu. And that could be because Ubuntu is installed in Legacy mode but the other OS is installed in EFI mode.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Regards

Are you saying that I'm screwed? Or I can do a EFI partition during ubuntu installation?

---

### Post by yancek on 2016-08-26
The image in your initial post is the Grub boot menu.  If you have only one operating system installed, you should not see a boot menu.  In your case, it is displayed so what is being asked and not answered is:  do you have another operating system of any king installed? If you do, what is it?

You indicate that you get a black screen when you "type in Ubuntu".  Where do you type in Ubuntu?  From the boot menu you would simply hit  the Enter key on the highlighted item.  Is that what you did?

If you installed UEFI then you need to boot UEFI and you don't change between UEFI and CSM because the files and their locations are different.  I think Acer has some unusual settings in the BIOS that need to be changed.  Hopefully someone more familiar with Acer will post.

---

### Post by oldfred on 2016-08-26
For UEFI boot with Acer you have to set a supervisory password & enable trust.
 Acer Trust Settings - details:
[http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
[http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757) 

Some older threads mention downgrading UEFI. Newer ones say that newest UEFI from Acer works, so make sure you have newest UEFI from Acer.

 Acer Very latest UEFI/BIOS works, downgrade not required:
[http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141](http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141)
Acer E5-573G, downgrade UEFI, supervisor password & trust on Ubuntu efi boot files.
[http://askubuntu.com/questions/706912/getting-a-black-screen-when-installing-or-live-booting-ubuntu-any-version-in-m?noredirect=1#comment1039248_706912](http://askubuntu.com/questions/706912/getting-a-black-screen-when-installing-or-live-booting-ubuntu-any-version-in-m?noredirect=1#comment1039248_706912)
Acer Aspire E15 will not dual boot, many details
[http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot](http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot)

---

### Post by dreaddisk on 2016-08-26
> **yancek said:**
> The image in your initial post is the Grub boot menu.  If you have only one operating system installed, you should not see a boot menu.  In your case, it is displayed so what is being asked and not answered is:  do you have another operating system of any king installed? If you do, what is it?** The only OS installed is Ubuntu 16.04 but it does not boot.**

You indicate that you get a black screen when you "type in Ubuntu".  Where do you type in Ubuntu?  From the boot menu you would simply hit  the Enter key on the highlighted item.  Is that what you did?
**Sorry, yes you are right. I hit the "Ubuntu" line and then gets frozen**

If you installed UEFI then you need to boot UEFI and you don't change between UEFI and CSM because the files and their locations are different.  I think Acer has some unusual settings in the BIOS that need to be changed.  Hopefully someone more familiar with Acer will post.  **What you said here makes sense. thank you.**

so, yea. these are other pictures that I could take:

> [ATTACH=CONFIG]270880[/ATTACH] This picture, is when I boot from UEFI (with the pendrive)


The partition that I have for Ubuntu is ext4

---

### Post by oldfred on 2016-08-26
That still is the standard grub menu, which when booting in UEFI mode you get.

The links posted several times above on UEFI boot, show both the BIOS boot screen & the UEFI with grub boot screen.

---

### Post by dreaddisk on 2016-08-26
> **oldfred said:**
> That still is the standard grub menu, which when booting in UEFI mode you get.

The links posted several times above on UEFI boot, show both the BIOS boot screen & the UEFI with grub boot screen.

I'm sorry for my luck of attention. I will check them out thoroughly. 

What would be the outcome in the worst case scenario?

---

### Post by oldfred on 2016-08-26
Worst case always is reinstall and restore data from backups.

Many times repairs will work if followed correctly, but sometimes the repairs are way more complex than a simple reinstall.

---

### Post by dreaddisk on 2016-08-28
all right... I made some tweaks thanks to the web page that you guys privided. But I got this GNU GRUB "crush"

> ```
GNU GRUB version 2.02 beta2-36ubuntu3.1

Minimal BASH- like editing is supported. For the first word, TAB list possible command completions. Anywhere else TAB list possible device or file completions.

grub>
```

ok, I tried to figure it out my self in the internet but nothing was helpful. Do you guys know what I can do?

thank you.

---

### Post by oldfred on 2016-08-28
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[URL="https://help.ubuntu.com/community/Boot-Repair"]https://help.ubuntu.com/community/Boot-Repair

[/URL]You grub error now is that grub is not correctly installed. Probably best to use Boot-Repair's advanced mode and do the full uninstall/reinstall of grub. Do not run auto fix.

---

### Post by dreaddisk on 2016-08-28
> **oldfred said:**
> Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[URL="https://help.ubuntu.com/community/Boot-Repair"]https://help.ubuntu.com/community/Boot-Repair

[/URL]You grub error now is that grub is not correctly installed. Probably best to use Boot-Repair's advanced mode and do the full uninstall/reinstall of grub. Do not run auto fix.

And then, how do I install grub again? with my usb that installed ubuntu?

---

### Post by oldfred on 2016-08-28
Boot-Repair is the slightly easier way.
You can use Ubuntu live installer, another install on another drive if you have that, or download it as its own live repair ISO/flash drive.

Or you an manually do it.
 [https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

---

### Post by dreaddisk on 2016-08-28
EVERYTHING IS DONE AND RUNNING GREAT!! Oh, my god. It cost me a whole world but thank to you guys I cut the mustard. It's a tricky thing, eh?

Any way, I apologize for my lack of understanding in the matter. But I finally did it and the best thing is that I learned from it.

I change it to [SOLVED}

---

