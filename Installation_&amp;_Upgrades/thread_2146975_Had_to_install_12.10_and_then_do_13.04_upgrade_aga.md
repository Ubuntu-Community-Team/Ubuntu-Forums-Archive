---
title: "Had to install 12.10 and then do 13.04 upgrade again on a second machine"
date: 2013-05-20
forum: Installation &amp; Upgrades
---

### Post by arrowcatcher on 2013-05-20
I finally got 13.04 installed on my newish Lenovo G780 notebook but had do to the same trick I discovered myself with the HP H8 Envy desktop = install 12.10 x64 first and then upgrade to 13.04.

When I put the 13.04 disc into the G780, it churned for a while and then died at a black screen.  A non-starter.  So remembering the trick I did on my H8, I used my 12.10 x64 to install, and that worked.  Neither the 13.04 x32 nor x64 disc would work in the machine.  Once I got 12.10 installed, I updated it to current and then upgraded to 13.04 as I had done on my H8.

However, when the machine tries to boot into Ubuntu with 13.04, it dies at a black screen just as the original install disc did.  Undaunted, I use the "3.8.0-21 (Recovery)" option in Grub to start the machine and find I can boot the machine into that kernel with no prob with a few clicks.  It won't boot on a simple startup from Grub, but it boots and works fine when I use "(Recovery)".

Not wishing to get tangled up with UEFI on top the other install problems, I did this all in Legacy mode.  So the boot process is messy = to start in Ubuntu I have to do as above when the machine is turned on, but to get to Windows 8, I have to use the "Novo" button to start the machine and then choose "Windows Boot Manager" in its Boot options.

So whew, the machine dual boots and works perfectly in both OS', but it sure is messy.  For one thing, on both of my recent machines I had to start with the 12.10 and then do an upgrade to 13.04.  It worries me that many people with newer machines may just give up and never use Ubuntu before they try this trick I found on my own.  You guys need to figure out what's missing on the 13.04 install file such that I had to begin with 12.10 to install Ubuntu in two separate cases.

The boot mess was expected.  I have to screw around to get my desktop to start in a similar way as above.  When my energy returns, I'll try fiddling with "boot-repair" and EasyBCD to see if I can make the boot neater.  I can also look at boot logs to try and figure out why 13.04 won't start properly in the Lenovo.  For that laptop, it's good security since only an unlikely knowledgeable thief could get the thing to run at all in either OS.  All 5 of my computers can now dual boot Windows/Ubuntu 13.04 but what a hassle on the newer ones.

---

### Post by dino99 on 2013-05-20
try one of these workarounds:  [http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it](http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it)

but from a terminal (ctrl+alt+t), that command might do the trick:
> gsettings set org.gnome.desktop.background show-desktop-icons true && gsettings set org.gnome.desktop.background show-desktop-icons false

---

