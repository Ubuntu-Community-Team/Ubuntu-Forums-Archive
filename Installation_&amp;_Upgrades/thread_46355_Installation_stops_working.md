---
title: "Installation stops working"
date: 2005-07-04
forum: Installation &amp; Upgrades
---

### Post by nyfreakinrican7 on 2005-07-04
](*,) I am new to linux and am about to give up this is the third distro I am trying to install and none have installed properly. Any way about my problem here. I have a Dell Optiplex Gn+ 166mhz pentium 32mb memory and an 8gb hd. I start the installation cd enter language, keyboard type and it searches for cd-rom. I then get to a screen that says retrieving nic firmware 2.6.10-5-386-di then to unpacking nic firmware 2.6.10-5-386-di it reads 1%. It then goes to a blue screen then a black one with the cursor on the bottom left of the screen and then it starts the cycle over from retrieving nic firmware about two times then just stays on the black screen i can type but it dissapears only option i have is to start over. Unless I am supposed to wait but I don't even have acsses to remove the cd. Please help me!

---

### Post by Seti on 2005-07-04
I'm assuming you burnt the installer disc under Windows? Oftentimes the problem is that an installer was burnt too quickly with the effect of the installation process "hanging" partway through. Usually this is the problem, you want to avoid burning an installer disc any faster than 12x or 16x maximum.

---

### Post by nyfreakinrican7 on 2005-07-04
Thank-you Seti I will try that then because I burned it under windows 98 plus with Nero 5.5 at 24x so I will try again with 12x and see what happens.

---

### Post by nyfreakinrican7 on 2005-07-04
[QUOTE=nyfreakinrican7]Thank-you Seti I will try that then because I burned it under windows 98 plus with Nero 5.5 at 24x so I will try again with 12x and see what happens.[/QUOTE]
 Burnt new disk at 12x and still stuck on the black screen here anyone have any ideas?????

---

### Post by mingus on 2005-07-04
[QUOTE=nyfreakinrican7]](*,) I am new to linux and am about to give up this is the third distro I am trying to install and none have installed properly. Any way about my problem here. I have a Dell Optiplex Gn+ 166mhz pentium 32mb memory and an 8gb hd. I start the installation cd enter language, keyboard type and it searches for cd-rom. I then get to a screen that says retrieving nic firmware 2.6.10-5-386-di then to unpacking nic firmware 2.6.10-5-386-di it reads 1%. It then goes to a blue screen then a black one with the cursor on the bottom left of the screen and then it starts the cycle over from retrieving nic firmware about two times then just stays on the black screen i can type but it dissapears only option i have is to start over. Unless I am supposed to wait but I don't even have acsses to remove the cd. Please help me![/QUOTE]

I can think of two possibilities.  The first may be the RAM.  32MB is the minimum indicated by the installer.  It is conceivable that a portion of that precious 32MB is being pre-allocated and not available for installation.  I assume you are aware that Gnome will perform very poorly (if at all) with 32MB, so it may be desirable to add RAM (or at least expect to use a diff window manager).  You could also try using a Live-CD to create a swap partition on the disk before installation; that will give the installer more to work with.

The second possibility is a BIOS conflict or limitation.  For example, your system probably does not support ACPI, uses a different IRQ interface, has an ISA controller, etc.  What is sometimes necessary is to turn some things off with kernel "arguments", which are commands adding to ":linux" when you start the installer.

Try this:
:linux acpi=off noapci nolapci nodma vga=normal noscsi nousb noapm

---

### Post by WildTangent on 2005-07-04
i think that computers too old...

-Wild

---

### Post by mingus on 2005-07-04
[QUOTE=WildTangent]i think that computers too old...

-Wild[/QUOTE]

I am running Ubuntu on a nearly identical box, but upgraded to 196MB RAM.  When pgms load the CPU spikes to 100%, not good for anything compute or graphics intensive, but is acceptable as long as used for one-average-app-at-a-time or as a dedicated server.

---

