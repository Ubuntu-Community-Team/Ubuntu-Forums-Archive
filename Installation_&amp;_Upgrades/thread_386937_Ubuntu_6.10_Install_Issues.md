---
title: "Ubuntu 6.10 Install Issues"
date: 2007-03-17
forum: Installation &amp; Upgrades
---

### Post by msgmikeh on 2007-03-17
Hi!
I'm very new to Linux and Ubuntu. I could use some help with a boot issue on 6.10. 

First here is my hardware:
Pentium D 2.8 
2GB DDR
Geforce 7800 GT
Apple 23' LCD
 
I have tried both the graphical and the alternate iso files for 6.10. The alternate seemed to install fine, as Grub is installed and I'm able to boot to 6.10. Here is where the problem comes in. I can get to the username screen, I enter my info and the OS goes to an orange background with gibberish on the screen that looks like bad pixels. I can't see to do anything. The graphical install iso went to the orange background with gibberish as soon as it booted to up.

Here is the process:
1) I select 6.10 from Gruib
2) OS starts to load (black screen with gibberish) guessing this is the Ubuntu splash screen.
3) OS boots to orange background (with gibberish black lines across screen)
4) Username/Password screen comes up (I can see this one first fine, no gibberish).
5) Orange background comes up, with gibberish and I can see the mouse pointer fine, but can't make out anything else. 


The ironic thing, is I see the mouse pointer fine. I'm stumped. Thank you for the time. 

Mike

---

### Post by vincedia on 2007-03-17
I am having the same exact issue. I'm using a AMD64 but with the same vid card and ram.
My LCD is a 20" Dell set at 1680X1050 right now.

I tried disconecting my second LCD and that got rid of some of the "bad pikel" looks, but everything else is the same issue as yours.

Might it be our vid cards?

Are you using the X64 or X32 version? I tried both, same result.

Quick google search found this for our cards:
[http://ubuntuforums.org/showthread.php?t=379807](http://ubuntuforums.org/showthread.php?t=379807)

Going to try now!

Vince

---

### Post by msgmikeh on 2007-03-17
Nice find. I'll give that a shot. Thank you for the quick response.

---

### Post by vincedia on 2007-03-17
Let me know how it goes, I am having a little trouble with the steps.

I am getting a blank page after typing [chroot /root nano /etc/x11/xorg.conf]

Nothing there to edit.


V

---

### Post by msgmikeh on 2007-03-17
I finally got it up and running. I had to use the alternate (text based, doesn't load the GUI) iso file. Once, U 6.10 was installed, I booted to the recovery console and followed the directions from the link you provided. I still get the garbled ubuntu splash screen, but once that passes all is "A OK".

Try downloading the alternate ISO, instead of the Live CD version. 
[http://www.ubuntu.com/GetUbuntu/downloadmirrors](http://www.ubuntu.com/GetUbuntu/downloadmirrors) (click on "other install options)

Hope that helps!

Mike

---

### Post by vincedia on 2007-03-17
OK, thanks...I will give that a shot.


Vince

---

### Post by vincedia on 2007-03-18
Wow! I just got it working using vesa drivers. So I am officially posting this from a linux machine.

I figured out why I was getting a blank page. I was typing a lowercase X in the line:
sudo nano /etc/X11/xorg.conf

Now to start getting the right vid drivers running.

---

### Post by msgmikeh on 2007-03-18
Nice. I used the Envy script to install the Nvidia driver. It worked well for me.

---

