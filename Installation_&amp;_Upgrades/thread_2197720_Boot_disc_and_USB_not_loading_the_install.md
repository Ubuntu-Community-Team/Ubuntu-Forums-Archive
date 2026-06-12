---
title: "Boot disc and USB not loading the install"
date: 2014-01-05
forum: Installation &amp; Upgrades
---

### Post by bignoisetransmissi on 2014-01-05
Hello, 

I currently have a HP Pavilion 7000 series, model - p7-1058uk, I7-2600 CPU @3.4GHz 8GB RAM, currently running Windows 8.

Now in the past installing Ubuntu on here I know it has worked fine with it before, but now I am wanting to wipe Windows 8 replacing with Ubuntu, I have used both the Boot disc and USB and both experinces the same problem on power up.

The following options apply:

[LIST]
[*]Try Ubuntu without Installing 
[*]Install Ubuntu 
[*]OEM install (for Manufacturers) 
[*]Check disc for defects 
[/LIST]

Afer trying every option after the initial Install Ubuntu option they all have the same problem, where after about 30 seconds of a blank screen, the whole system restarts then back to the option menu again, If someone could help me on this please would be very appreciated:)

---

### Post by Bucky Ball on 2014-01-05
Welcome. When you get to that options screen with Try, install, etc. press F6. From the menu that pops up choose 'nomodeset'. Proceed and Try Ubuntu.

---

### Post by bignoisetransmissi on 2014-01-05
Hello, I have just tried what you suggested and when pressing F6 nothing happens from that point, for the sake of it tried the other F buttons and still nothing, only other advanced options it is suggesting is 'e' to edit the commands before booting and 'c' for a command-line.

---

### Post by Bucky Ball on 2014-01-05
? You have Ubuntu installed or you are booting from the install disk? I am referring to when you are booting from the install media, you are looking at the options 'Try Ubuntu' 'Install Ubuntu' etc. 

Your description sounds like you have Ubuntu installed and are looking at the menu list before login, or ... are you using the alternate or the desktop install ISO?

---

### Post by bignoisetransmissi on 2014-01-05
No sorry for the confusion, the only OS I have installed at the moment is Windows 8, i am booting from the install disc and yes as you said to with the options to either try Ubuntu or install it (while wiping Windows 8) but it's when i select the following options the screen goes blank then the PC restarts back to the menu from the intsall disc, I have attached a photo of the menu, just to make sure we are both on the same line.

---

### Post by Bucky Ball on 2014-01-05
Okay. What release are you trying to install, BTW? Seeing as you're getting the option to edit the entry, with Try Ubuntu selected, hit 'e' and see if there's a kernel line. It will end in 'quiet splash' or something like it. Make the end of that line look like this:

quiet splash nomodeset

Follow instructions at the bottom of the screen to save and proceed.

I've never seen a screen quite like the one in your screenshot so interested to know what you are trying to install.

---

### Post by bignoisetransmissi on 2014-01-05
The release is Ubuntu 12.04, tried both the Disc very recently created and USB which I have used many times in the past going back a few months and worked perfectly,`now both with same problem, left me somewhat lost.

Now after finding 'quiet splash' i typed nomodeset as you say, the I follow the instructions at the bottom, "Press ctrl x or F10 to boot,, ctrl c or F2 for a commnd-line or ESC to discard edits and return to the GRUB menu"  Now I assume the first option to boot was the one but pressing F10 or ctrl x to do so then does nothing from that point

---

### Post by Bucky Ball on 2014-01-05
Are you holding down 'Ctrl' and 'x' keys at the same time? Silly question, perhaps, but had to be asked ...

---

### Post by bignoisetransmissi on 2014-01-05
It did make me smile Lol And yes F10 nothing and while holding both ctrl and x together all that happens is x will come up wherever the underscore is located on the screen so the ctrl button is taking no effect on the x

---

### Post by Bucky Ball on 2014-01-05
Hmm. Just a thought. If it is a Win8 computer it could have something to do with EFI or secureboot or some other MS guff. Can you get into the BIOS and see what mode it is booting in. I don't know a lot about this, but I think you can boot in EFI, GPT, or Legacy. Choose Legacy boot in the BIOS and try again. 

It is odd that it is booting to the list of options, but have a look around in the BIOS and see if there are any clues.

---

### Post by bignoisetransmissi on 2014-01-05
After finding out the BIOS mode, it is already set to Legacy at this moment...

---

### Post by bignoisetransmissi on 2014-01-05
See what you may think of this, I thought it may explain why it wasn't working then reading the rest got my somewhat confused, [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by Bucky Ball on 2014-01-05
Even though you are going to wipe Win8, that is probably EFI and you possibly need to boot in EFI. Try that. If that doesn't work, try any other options in there. Experiment.

---

### Post by oldfred on 2014-01-05
If you boot Ubuntu installer in UEFI mode, you do get grub menu. You then edit grub just like first boot after install whether UEFI or BIOS.
And then have to use e for edit, scroll to linux line and replace quiet splash with nomodeset.
Nomodeset works for nVidia video, but different parameters are usually required if using Intel video or AMD.
       
Shows install with screen shots for both BIOS & UEFI, so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Best to have secure boot off. And in Windows 8 (and UEFI) have fast boot off.

 How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

