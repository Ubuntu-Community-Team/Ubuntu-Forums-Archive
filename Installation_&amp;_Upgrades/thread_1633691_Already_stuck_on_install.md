---
title: "Already stuck on install"
date: 2010-11-29
forum: Installation &amp; Upgrades
---

### Post by Paragon009 on 2010-11-29
I first downloaded the .iso to my C:/ drive, then I burnt the .iso file to a CD-R. I was originally going to install on two separate HD's, but I said "What the heck," let me just do one HD. I didn't partition beforehand. Instead, I am going to partition using GParted during the Ubuntu install. I found an exceptional site ([here]("http://www.dedoimedo.com/computers/dual-boot-windows-7-ubuntu.html")), and those are the directions I'm following. 
 
I inserted the disc into the CD/ DVD drive and then turned off the computer. When it rebooted, the CD/ DVD began to spin and read the disc. When all was said and done, it came to a screen with an Ubuntu logo with four white dots underneath it that periodically changed color from white to red. Then, nothing more. The screen would all of a sudden turn off. I could turn it back on manually, but then it would go to "sleep" again. That's where I'm at. My monitor won't stay on when Ubuntu is being installed from the CD-R.
 
Any suggestions? I've read some threads about this issue, but don't know if my situation is similar.
 
I'm using 1600x900 resolution on an HP 2009m monitor with AMD Radeon HD 5870 2GB Eyefinity graphics card.

---

### Post by TBABill on 2010-11-29
First things to verify anytime you download a .iso is the quality of the file. In Linux you run ```
md5sum nameoffilehere
``` and compare it against the website where you downloaded the file from. It will output a very long string of alphanumerics that you compare. If they match then the file downloaded without errors. If not, delete and try again.
 
When you burn the file you burn at the very slowest speed possible to prevent burn errors.
 
Did you do those things first? If not, perhaps verifying your iso and then burning slowly would help. Beyond that you could have a driver/video issue causing a lockup.

---

### Post by Paragon009 on 2010-11-29
> **TBABill said:**
> First things to verify anytime you download a .iso is the quality of the file. In Linux you run ```
md5sum nameoffilehere
``` and compare it against the website where you downloaded the file from. It will output a very long string of alphanumerics that you compare. If they match then the file downloaded without errors. If not, delete and try again.
 
When you burn the file you burn at the very slowest speed possible to prevent burn errors.
 
Did you do those things first? If not, perhaps verifying your iso and then burning slowly would help. Beyond that you could have a driver/video issue causing a lockup.
 I did burn it using 16x which was the slowest my CD/ DVD drive would spin.
 
I downloaded 10.04 LTS 64-bit straight from Ubuntu's website.
 
I'm not sure how to verify the files. How do I verify it using Linux when I don't have Linux (Ubuntu) installed, or am I missing something? I'm sorry. Tech wise, I'm average. I can work on my own computer and follow instructions to the letter, but I'm not sure how to verify this file. I admit.

---

### Post by siddarthkaki on 2010-11-29
Here is a way to do a MD5 checksum on Windows:

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Or this to save some scrolling time:

[https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM%20on%20Windows](https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM%20on%20Windows)

I would probably use Cygwin, but other options would work as well. Here are Ubuntu's ISO hashes:

[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

Tell me how this works out.

---

### Post by Hippytaff on 2010-11-29
Do you know what graphics card you have?

---

### Post by Paragon009 on 2010-11-29
> **Hippytaff said:**
> Do you know what graphics card you have?
 
[quote=Paragon009]I'm using 1600x900 resolution on an HP 2009m monitor with **AMD Radeon HD 5870 2GB Eyefinity graphics card**.[/quote]
It's a Sapphire.
 
So, I downloaded MD5Sum. I compared the hash of the .iso with the known hash value of version 
ubuntu-10.04.1-desktop-amd64.iso, and they are both identical ("MD5 Check Sums are the Same").
 
Edit: Followed the instructions. Integrity check of the CD passed.

---

### Post by Hippytaff on 2010-11-29
Try this courtesy of Ruby1200
> 
Put the LiveCD in and boot up;

when you see the Ubuntu logo hit Enter;

Choose language and leave the default Try as a live cd or whatever it says again;

Important: hit F6 and then Esc to see the boot line

file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash --

Now, again this is important, move the cursor backwards and remove quiet splash;

Add the following parameter:

nomodeset

In other words, the boot should look like this:

file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz nomodeset --

Now hit Enter.

You may have to toggle the F6 option a bit (do it first etc.).

If this gets the LiveCD booted and to the desktop, then we can go from there for a more permanent solution.


Sorry, missed the graphics card specs :-s

---

### Post by Paragon009 on 2010-11-29
Booted the LiveCD .iso and held any key down. It came up to the language screen where I then selected "English." After that, I chose to perform an integrity check of the CD. It passed; no problems.
 
Then, I tried to install, and same problem occurred.
 
So, what I know is that both the .iso and the CD are faultless.

---

### Post by Quackers on 2010-11-29
Did you look at Hippytaff's post? Try it?

---

### Post by Paragon009 on 2010-11-29
> **Quackers said:**
> Did you look at Hippytaff's post? Try it?
Tried it but didn't work.
 
However, I'm happy to announce that I have successfully installed Ubuntu.
 
According to my observation, the issue is the DVI connection between the monitor and the GFX card.
 
With my monitor connected via DVI port to one of the AMD Radeon HD 5870's Eyefinity mini-display port (via an adapter that converts mini display port to DVI port), my screen would turn off after the Ubuntu logo appeared after booting the Ubuntu LiveCD (which I burned from the .iso file). It works perfectly with Windows 7. Once I try it with Ubuntu (well, I only got to the Ubuntu logo with it on), the screen turns off.
 
The reason I know this is when I switched off the PCI-E 16 graphics card (the 5870) and switched back to the onboard HD 4200 graphics card, and then used the VGA port on the monitor and the PC, everything was okay. The screen no longer turned off. I could proceed normally with the install (which I did).
 
At this point, I'm still using the VGA until I can research more and see if this is a known issue (it has to be). I'm thinking there is some compatibility problem with this GFX card and Linux/ Ubuntu. I'm not sure. 
 
Any suggestions would be appreciated. As far as Ubuntu goes, aside from the monitor issue, install went perfectly.

---

