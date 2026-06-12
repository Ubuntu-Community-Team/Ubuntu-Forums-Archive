---
title: "Migrate install from desktop to laptop"
date: 2011-04-12
forum: Installation &amp; Upgrades
---

### Post by kpm1 on 2011-04-12
Complete Ubuntu newbie here...I have a couple of older Windows systems that I'm wanting to migrate to Ubuntu. One is an IBM Thinkpad X40 laptop, and the other is a Dell Dimension desktop.

There is no CD in the laptop and the USB ports don't work anymore. So, I took the HDD from the laptop and connected to the Dell desktop (IDE) and installed 10.10 on the laptop HDD via USB. All good - seems to run fine on the Dell.

Then, put the HDD back into the Thinkpad and nothing...

Am I foolish, and is this process just not possible?

Thanks in advance.

---

### Post by sanguinoso on 2011-04-12
By nothing do you mean it doesn't even show POST messages from the motherboard? Or it just fails to boot? Can you see the hard drive in the bios?

---

### Post by 3Miro on 2011-04-12
Just a guess: when you connected the laptop HDD you still had your desktop HDD connected as well.

If you are going to install Linux this way, then make sure you have no other disks connected to your machine.

If this isn't the case, then make sure you don't install any special drivers on your desktop. Your laptop has different hardware and may or may not need those.

If this isn't helping, post here EXACTLY what is happening i.e. what do you mean by "nothing".

---

### Post by kpm1 on 2011-04-12
I apologize, not very descriptive...

When powering up the laptop, after the BIOS screen shows, the screen is left with just a blinking cursor at the upper left.

I can enter setup screen. I can enter boot setup, which lists the HDD in the option.

Does that help?

---

### Post by kpm1 on 2011-04-12
Also, I DID have the desktop HDD connected when I did the install. Is it possible to re-install with the desktop HDD disconnected? If that may resolve the issue?

---

### Post by sanguinoso on 2011-04-12
Here is an idea, can you partition the disk from the working machine and install a ubuntu installer image on the disk as you would a thumb drive? Then you can use the disk to install ubuntu into another partition? That way the ubuntu setup can find all the correct drivers and what not.

---

### Post by 3Miro on 2011-04-12
What probably happened is that Ubuntu got installed, however, the bootloader (the small part that helps boot the OS) got written to the main HDD. The bootloader is traditionally written to the first HDD and that was probably your desktop one.

BTW check to see if your desktop can still boot.

The easiest thing to do would be to reinstall Ubuntu, but this time make sure there are no other disks attached to the desktop. Alternatively, you can try to reinstall just the bootloader:

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

Look for Reinstalling GRUB 2.

---

### Post by kpm1 on 2011-04-12
Thanks - that makes sense. I will try the full re-install - will let you know how it goes.

BTW, the desktop system runs OK when I have the laptop drive attached but doesn't when it's removed. The Bios says some long alpha-numeric device is not available. 

Do you have suggestion for how to correct Windows system? I was hoping to get the laptop running first and become familiar with Ubuntu before converting the desktop.

Thanks again!

---

### Post by 3Miro on 2011-04-12
For windows, I think you need to fix the windows bootloader. I heard some people are using windows CD/DVD, but I am not sure how and why.

You can boot back into windows if you reattach the laptop CD to the desktop. Then perhaps you can repair the bootloader from within windows. I don't know windows enough to help here.

The technical term for what you need is:

"restore windows bootloader" add XP, Vista, 7 to the windows as they are different. Try Google, the answer should be out there, if you have trouble, start another thread (add "restore windows bootloader") to the title.

---

### Post by sanguinoso on 2011-04-12
I believe the term on Windows is Master Boot Record. I had to restore that when I still had Windows and I installed ubuntu on a usb drive.

---

### Post by kpm1 on 2011-04-12
You guys ROCK!!

Thank you both. I have both systems up and running now. Dell is back running Windows, and Thinkpad is running Ubuntu.

I have much to learn about my new OS - looking forward to it.

Thanks so much for the rapid help!

---

