---
title: "Install Ubuntu over top of win 8 on Dell Inspiron 15 3521 i5 4g ram radeon gpu"
date: 2013-08-04
forum: Installation &amp; Upgrades
---

### Post by Pedroriel on 2013-08-04
Hey Everyone

I am trying to install Ubuntu on my dell inspiron 3521 instead of win 8. When I put the 12.04 lts (to be safe) version on there, the screen goes black with fuzzy white pattern at top half of screen and laptop freezes. I have tried usb and dvd install, both freeze. I don't care if I have to wipe win 8 and reinstall ubuntu, but I just am not being allowed to do ANYTHING, and I cannot figure out any reason why. I will try 12.10 before I come back here to check.

Please help. How do I get ubuntu on there?

Thanks.

---

### Post by oldfred on 2013-08-04
If you have Windows 8 pre-installed you have UEFI. When you boot live mode installer, you should get grub menu when booting not the BIOS accessibility icons (keyboard & person icons) at bottom of screen.

From grub menu you many need a boot option. use e for editing grub boot stanza and scroll to linux line and replace quiet splash with nomodeset. With Intel these also may be alternatives to nomodeset.
        i915.i915_enable_rc6=1
OR:
      
 Force Intel Video mode as boot parameter in grub menu - change to your screen size
video=1280x1024-24@60
and if that doesn't work you can try
video=VGA-1:1280x1024-24@60


 For Intel graphics running slow:
sudo apt-get install mesa-utils
glxinfo | grep OpenGL | head -n3

   Asus i3 with Intel graphics, 
"acpi_osi=Linux"
"video=1280x1024-24@75" or whatever native resolution is

   acpi_osi=Linux acpi_backlight=vendor 

Or you may just have to test with various alternatives. Let us know which works.

---

### Post by Pedroriel on 2013-08-05
G'day oldfred,

Thanks for your time mate. You have understood the problem spot on, but I don't quite understand. I am no noob, but no expert either. What is nomodset? And what is quiet splash? And I guess understanding no modset will explain the line of code following that paragraph. I see the rest must be to solve the fan and dual graphics card/heat problem this Laptop experiences under Ubuntu Linux.
I was anticipating these, and thanks for telling me about them as well. I am off to get some dinner right now, but will be back at my PC in an hour or so, and I will start researching the info you have given me above so I can know my stuff a bit more if I need to ask you more.
On a separate note, I see you are a mod on here, and your above answer seems to come from a smart cookie. I am doing a degree at uni, so if I have future questions, would there be any benefit to me asking you  specifically? I am REALLY keen to learn, and won't just ask you everything, but it would be nice to know someone was there to help in case of emergency. 
I have only been on Ubuntu for about 6 or 7 years, and I was a cabinet maker for 90% of that time, so have had very little time to learn Ubuntu properly. But now, as I said, I am a student and I am studying computer networking from home here in Australia. So nowadays I get to spend virtually my whole day in front of my PC or Laptop, and would like to make the most of that time backing up my uni knowledge with Ubuntu knowledge! 
Also, even though I have a win 7 PC, and am fairly new to open source, I LOVE IT!!! I truly do. It caters to the handy man in me as well as offering a viable and comfortable career path for me and my family in the future, I hope, as I don't need to be rich. (Ubuntu or Raspberry Pi are my FAVS in open source at the moment) So your help would definitely be appreciated and passed on to anyone I can help in the future too.
Anyway, sorry to ramble so far of topic. Thanks for your reply. I will go and eat then do some research and come back here to inform you what I learn/accomplish, or see if you have any other simpler suggestions, or explanations of the current one.

Thanks so much in advance, I think I am still getting used to how helpful everyone is and how much the open source community leans on each different part of itself. I won't ramble like a surprised newcomer forever!

Thanks, and long live the open source community!

Pedroriel

---

### Post by oldfred on 2013-08-05
Sorry, I should have posted these links which have screenshots for adding nomodeset (or other boot parameters) which booting live DVD or flash drive or booting after install. You want to scroll down to the examples with the grub menu. You use e for edit, scroll to linux line and replace quiet splash with nomodeset.

       How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

The forum is here to help you and many others know other issues a lot more than I do. I only know the basic on video issues. Best just to post a question on any new topic. Just do not post duplicate questions on the same issue.

---

### Post by Pedroriel on 2013-08-05
Hey oldfred,

I am running Ubuntu on my laptop noow. Yay!! I did not really understand the technicalities of the grub menu you discussed, but I researched the grub menu, and found I needed to turn smart boot, fast boot, and secure boot of. Then Ubuntu was able to load. The only problem is the laptop now says:
 PXE over ipv4 press esc to exit
Press esc
PXE over ipv6 press esc to exit
Press esc
Ubuntu loads as normal.

I will go and have a look at the links you have posted up for me, and see if they explain changing the grub menu to load Ubuntu first. Otherwise, do you know why this is happening?

Thanks.
Mat

---

### Post by oldfred on 2013-08-05
In either BIOS or UEFI you specify boot order first hardware devices and then within hard drives which hard drive. With UEFI then you also have which system from the efi partition.
One of the hardware boot choices is a network boot and your PXE over the network is a network type choice. You must have those choices higher in the boot priority? Attached shows network device which would also be a PXE device and the attached has network last which is usually correct as most do not boot it.

---

### Post by Pedroriel on 2013-08-06
G'day oldfred
I got into the efi/bios and there is a list like you said but there does not seem to be any way to change the order of that list. I will have to do some more research and come back in a few days. Thanks for your help, and pls keep an eye on this thread in a day or 2. That is when I will come back and close the thread or ask you some more. Thanks again

Pedroriel

---

