---
title: "How to fix Black screen in Boot Repair Disk?"
date: 2016-10-07
forum: Installation &amp; Upgrades
---

### Post by javierdl on 2016-10-07
[IMG]https://sites.google.com/site/javierwebfolio/_/rsrc/1475842998679/temp/brd_grub.jpg[/IMG]

[cl-netbox advised]("http://askubuntu.com/questions/785873/boot-repair-disk-not-loading-boots-into-black-screen") to add "nouveau.modeset=0" to the Grub parameters. So I did. But I still got the black screen.
Then I replaced it with "nomodeset", but then grub said it didn't recognize that command.
Maybe I'm not putting the command in the right place (?)

Thanks guys,

JDL

---

### Post by Bucky Ball on 2016-10-07
Maybe you could tell us what you're actually trying to do? For what reason are you wanting to run boot repair and how are you trying to run it? You have posted this in Installation and Upgrades, so presuming you are trying to install Ubuntu (which is what this forum is for)? 

You are aware that you can [install bootrepair in a live session or even in a hard disk install]("https://help.ubuntu.com/community/Boot-Repair#A2nd_option_:_install_Boot-Repair_in_Ubuntu")? See the link in my signature re. Boot Repair.

---

### Post by yancek on 2016-10-07
You're not putting nomodeset in the right place.  It should go on the kernel line, the line beginning with 'linux', generally before 'quiet splash --" or replacing  'quiet splash --'.  This should be at the end of the kernel 'linux' line.  Don't know if this will resolve your problem.

---

### Post by javierdl on 2016-10-07
Bucky Ball,
You're right, sorry about that. 
I'm trying to make a dual-boot system with Win10 and Ubuntu 16.04 LTS. In a desktop pc, Acer Predator G3-710. I added an 128 Gb SSD, where both OSs are. And an extra 8Gb ram stick for a total of 16 Gb ram.
I have installed Ubuntu already, and seemingly everything went well. Except that the Grub page showing me to choose between Ubuntu and Win10 is not showing. The pc just loads Win10 directly.
So I thought at this point all I needed to do is to fix the Grub files. 
The problem I had BEFORE, with BRD, is that the screen was black. But thanks to yancek, that is no longer a problem.
However, even though BRD said it had done the "recommended fix" successfully, when rebooting, nothing had changed :(  (still booting automatically into Win10).
This is the [URL]("http://paste.ubuntu.com/23289237/") BRD gave me.

yancek,
Thanks a million for that info. Indeed it helped to move forward, as I was finally able to see the GUI.
As you may have read above, I'm stuck again though.

What should be the next step now?

JDL

---

### Post by oldfred on 2016-10-07
All Acer we have see in UEFI boot mode require you to set UEFI supervisory password and enable "trust" and grub/ubuntu .efi boot files.
Some threads mention downgrading UEFI, but newer threads mention that newest UEFI from Acer works. I would expect the same with your model.

 Acer Trust Settings - details:
[http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
[http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757) 


 Acer Cloudbook shows screen for selecting trust
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392](http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392) 

 Acer Aspire E15 will not dual boot, many details Trust settings in step 35
[http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot](http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot)
Acer Aspire E 15 Downgrade to older UEFI, password & trust (ACPI issues?)
[http://ubuntuforums.org/showthread.php?t=2298380&p=13403062#post13403062](http://ubuntuforums.org/showthread.php?t=2298380&p=13403062#post13403062)
Acer Aspire ES1-512-C39M Details on supervisor password and settings to enable trust on ubuntu entries Also R14 model same fix
One of several with more details:
[http://ubuntuforums.org/showthread.php?t=2297947](http://ubuntuforums.org/showthread.php?t=2297947)
[http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)

---

### Post by javierdl on 2016-10-07
Oh, I see!

Thanks a lot oldfred. I'll look into enabling "trust".

I was going to do this:
Good thing I shot a photo of the result screen showing some important info.
It says, I should try inverting the order, in BIOS, in which Windows and Ubuntu boot.
Should I not be able to do it in BIOS, then I can use this command, in an admin command prompt: 

[B][I]bcdedit/set/{bootmgr}path\EFI\ubuntu\shimx64.efi
[/I][/B]
But I guess I should start with enabling "trust".

Thanks again oldfred :)

JDL

---

### Post by javierdl on 2016-10-07
Unfortunately I don't have that choice in the BIOS to select a trusted file:

[IMG]https://sites.google.com/site/javierwebfolio/_/rsrc/1475895059914/temp/bios-security.jpg[/IMG]

[IMG]https://sites.google.com/site/javierwebfolio/_/rsrc/1475682149620/temp/Bios_booting%20opts.jpg[/IMG]

I guess I should then try that command in the admin command prompt...

JDL

---

### Post by javierdl on 2016-10-07
I am trying to use that BCDedit command, but the [COLOR=#000000]admin command prompt tells me "*An unknown command was specified*" :(
But I am typing the same command that was mentioned in the BRD screen:

[/COLOR][IMG]https://sites.google.com/site/javierwebfolio/_/rsrc/1475895674771/temp/brd_screenmessage.jpg[/IMG][COLOR=#000000]

[/COLOR]

---

### Post by javierdl on 2016-10-07
Never mind!
I was missing some spaces, and I had an extra "/" too:

**bcdedit /set {bootmgr} path \EFI\ubuntu\shimx64.efi**

It's working now!
And best of all, I do get the GRUB page showing me Ubuntu and Windows!!! Yeah!!!

Thanks for your help guys! :)

JDL

---

### Post by Bucky Ball on 2016-10-08
Excellent news and well done. Please mark as 'solved' to help other from Thread Tools at top right and good luck.

---

