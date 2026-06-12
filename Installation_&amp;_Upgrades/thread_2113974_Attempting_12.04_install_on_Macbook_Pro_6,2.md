---
title: "Attempting 12.04 install on Macbook Pro 6,2"
date: 2013-02-08
forum: Installation &amp; Upgrades
---

### Post by leptone55 on 2013-02-08
Hello all,

Please forgive me if this is a repeat question, I've been searching for a solution for weeks. 

Also, I have been really enjoying using Ubuntu for the last couple months but I am admittedly a complete noob. I really am at my wits end here and I don't know what is going on. For these reasons I have walked you through step-by-step everything I've tried, everything I see, what I tried next what I saw next.

Any help at fixing or understanding these issues will be so very appreciated!

I am attempting to install Ubuntu 12.04 on my MacBook Pro 6,2 (Intel HD Graphics, NVIDIA GeForce GT 330m) alongside OSX using refit. With this guide: [https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)

I have a USB disk that I made on a PC with "Universal USB Installer." I have verified this disk by booting to Ubuntu from it on my PC, no problem.

When I put the disk in my Mac and boot refit shows 5 options:
1. Boot EFI\ubuntu\grubx64.efi from EFI 
Picture of three blocks(orange, blue and green) with a Macintosh HD icon in the lower right 

2. Boot Mac OS X from Macintosh HD
Apple icon with Mac HD icon in lower right

3. Boot EFI\boot\bootx64.efi from PENDRIVE
Same three blocks this time with a orange drive icon in the lower right

4. Boot Legacy OS from HD
Four grey squares is a diamond formation. Mac HD icon in lower right. 

5. Boot Linux from PENDRIVE
Tux icon with orange disk icon in lower right. 

I believe (1) is left over from when I had 12.10 on this Mac. I tried to remove it by wiping the partition.
If I boot to (1): 
"rEFit - booting OS 
Starting grubx64.efi
error: no such partition.
grub rescue>"

(2) Boots OS X no problem

(4 & 5) *i have no idea what (4) is i've never seen it before.
Show the icon either tux or squares then boots to a black screen that says: "Missing operating system"

(3) Boots to: 
"GNU Grub version 1.99-21ubuntu3.1
Try Ubuntu without installing
Install Ubuntu
Check Disk for Defeats"

When I select "Try Ubuntu without installing" as the guide instructs, I get a purple screen. Then the word Ubuntu with 5 white dots these dots all change to red then back to white. The dots start changing back to red and at the moment the last dot turns red the second time my keyboard lights up. Then it freezes all dots remain red.

Many articles indicate that I should see a the Ubuntu CD’s boot menu at some point where I can select a langue or press "f6" also that I should see a keyboard+man icon. I never see any of these.
(although i do on my pc)

Research lead me to try: right after I boot rEfit (3) to press "e" from the grub interface and add nomodeset to my boot options. Then I press f10.

Once again I see the dot animation but it does not freeze. Instead I am presented with a black screen with a command prompt: ubuntu@ubuntu:~$

My research seems to suggest that I should install Ubuntu from this prompt. This seems dubious to me for several reasons mainly, I have not configured my partitions yet, etc. (I am stuck at the "Boot your Mac from the CD" step in the tutorial I provided the link for. Although it wouldn't be difficult to do from Disk Utility on OS X). Also I can not find an article that actually says how one would do this.

Research also suggested that I should install NVIDIA drivers from this command prompt and then reboot. I have tried this a couple times/ways and it never worked out well. Most recently I followed this advice:
$ sudo apt-get install linux-source 
$ sudo apt-get install linux-headers-generic 
$ sudo apt-get install nvidia-current-updates 
from: [http://askubuntu.com/questions/236495/installed-ubuntu-12-10-but-cant-login-due-to-gpu-lock-and-i-cant-boot-with-nom](http://askubuntu.com/questions/236495/installed-ubuntu-12-10-but-cant-login-due-to-gpu-lock-and-i-cant-boot-with-nom)

Then I reboot and when I select "Try Ubuntu" or even "Check disk for defects" from grub. I am presented with a pixelated purple screen. I can see that the dots load menu is running because some of the red pixels change to white and back then solid red and my keyboard lights up.

Upon closer examination. Booting "try Ubuntu" with nomodeset once, is enough to cause this pixelated screen problem for then on when I don't use nomodeset. Otherwise, I have to rewrite the image to the disk on my PC and then start over.

I am able to add nomodeset to "Check disk for defects" it runs perfect: "Check finished no errors found. Press any key to reboot your system"

I am also able to do this with the "install Ubuntu" option but instead of a command prompt. I am presented with the GUI installer, which works and I can install Ubuntu. During this I can click around as if I were using Ubuntu. I can look at the calendar in the top left I can open and edit system settings. However, I do not have my dock on the left and I can't find and open apps. This part is what upsets/disconcerts/confuses me the most because Ubuntu is clearly working no problem, no graphics issues or anything. 

I booted back to OSX configured my partitions then did the above and installed Ubuntu. When I reboot it makes it to the log in page (I assume its the log in page because I hear the bongo drum). However, the screen is all pixelated in a similar manor (though it is different technically). So I reboot I am present with a purple grub menu I select the 64-bit recovery mode option then I attempt to boot to fail safe graphics mode. And I get "fatal error no screens found"

So I edit the boot options for recovery mode, remove the word "recovery" leaving "nomodeset" then install the drivers using the same commands as above. Now when I boot Ubuntu 64 bit from grub the ubuntu with the 5 dots comes up all the dots red and not changing. Then I hear the bongo drum and nothing changes on the screen. But no pixelation.

If at this point I try to boot to fail safe graphics mode I get the same error as before. 

At this point grub has installed itself above rEFit so I have to hold option to boot to rEFit. Now there are only three options. What was (1) now boots to grub (I believe this is where my computer is booting to by default). (4) remains but when I select it, it doesn't move past the icon to the black screen like before.

My questions are these:
Overall what is going on with this install?
Am I approaching this issue from the right direction, using nomodeset? Many posts/tutorial tell you to use nomodeset but not what to do once you get there.

Is there something I can do in the command line presented when i boot with nomodeset that I can run/install which will make it so i can boot "try ubuntu" without nomodeset?

Is the fact that I don't see the Ubuntu CD boot option's menu like I do on my PC or like in the tutorial I'm following and that I only see the grub menu the "real" issue. How can I fix this?

I really enjoy the Ubuntu experience but this ordeal is break my soul! Especially because Ubuntu/Canonical says that 12.04 is “highly compatible” with the Macbook Pro: [https://help.ubuntu.com/community/MacBookPro6-2/Precise](https://help.ubuntu.com/community/MacBookPro6-2/Precise)

Again any help would be much appreciated. I am sorry for how long this is but I really don't know what is important and what is not.

---

