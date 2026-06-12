---
title: "Blank screen during install/CD integrity check"
date: 2007-05-11
forum: Installation &amp; Upgrades
---

### Post by fairman4 on 2007-05-11
I need some help. I am trying to give Linux a chance, but so far all I had are problems. I've downloaded the Ubuntu iso and burned it to a CD. I boot to the Ubuntu menu, no problem. However, if I choose either to "Start or Install Ubuntu" or "Check CD for Defects" it will show a status bar window that says "Loading Kernel", which goes to 100%, then it goes blank, says "Loading, Please Wait...", then it goes blank again. Then nothing. Does anyone have any suggestions what the problem is?

---

### Post by chewjoel on 2007-05-11
I have the similar problem too.
The CD works well with my desktop, but it just doesn't work the way it should on my laptop.

First, it booted from CD.
Then it shows a screen which I chose 'Start or Install Ubuntu'
Then it shows progress of Kernel loading.
After Kernel loading is completed, it goes blank.
The whole screen is black-out with only a flashing _ .

The message 'Loading, Please wait...' doesn't show on mine.

I read that it could take a while for Ubuntu to finish booting, but I waited a long time, nothing changed.  There's no sign of the laptop is working either, except for the flashing _ .

Anybody have any idea why and how to solve this?

Thanks.

---

### Post by stefaan.dutry on 2007-05-11
I have the same problem aswell.

[LIST]
[*]Get to the initial screen
[*]Select Start or install
[*]Screen goes black with 2 lines on the bottom in my case.
[/LIST]

[B]CNT 14: CR2 F8000000 err 00000000 EIP c020c384 c020c384 cs 00000060 flags 00010003
Stack: c00f7d20 c03f129b c0371d8c 00000002 c00f7d29 000f7d20 00000000 00000000[/B]

i posted here already, so you might want to follow progress on this forum aswell
[http://ubuntuforums.org/showthread.php?t=438760]("http://ubuntuforums.org/showthread.php?t=438760")

---

### Post by chewjoel on 2007-05-11
I tried by adding acpi=off in the first option for F6.
And it works.

But after the installation, I found that my pc speaker is not working...

---

### Post by pink_ego_b0x on 2007-05-11
Yes, I'm having the exact same problem as described. Please help someone!!

---

### Post by stefaan.dutry on 2007-05-12
> **pink_ego_b0x said:**
> Yes, I'm having the exact same problem as described. Please help someone!!

Have you tried adding the option acpi=off, like mentioned in the post just before yours?

It worked for me.

---

### Post by pink_ego_b0x on 2007-05-12
yea, but no luck :confused:

---

### Post by Sambooe on 2007-05-12
Not sure if this will help, but I had the same problem trying to install xubuntu. Problem was solved by downloading the Alternate Install CD to install Xubuntu 7.04.

The Alternate CD worked great and solved my display resolution problem as well. My resolution for my 22" Viewsonic should be 1680x1050......the alternate cd lets you set up what ever resolution you want.

Hope this helps .... Good Luck!

---

### Post by chewjoel on 2007-05-12
My friend told me it's a common problem with live cd. So maybe trying out acpi=off or noacpi could do. 
acpi=off works for me.

---

### Post by hanzj on 2007-05-15
I added the text "acpi=off", but it doesn't help. What's wrong?

---

