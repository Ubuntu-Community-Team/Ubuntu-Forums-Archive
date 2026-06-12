---
title: "Install problem - laptop screen too small"
date: 2006-12-30
forum: Installation &amp; Upgrades
---

### Post by bushidomeister on 2006-12-30
Hello, 

I can not seem to get past square 1 in when attempting to install ubuntu 6.10 on my Dell Inspiron 1100 laptop.  
I see the welcome screen to select the language but cannot click the "Forward" button to continue.  I have not been able to resize the desktop.  

The bios has been revised to A32.

Can anyone point me in the right direction?  Is there something so glaringly obvious that I am not seeing it?  
Thank you,

---

### Post by foolsh on 2006-12-31
you could download the alternate version, it installs in a text mode, but is the same ubuntu after the install is finished 
it has helped me out a few times with laptop installs.

---

### Post by tuffstuff on 2006-12-31
Yes, I had the same problem. I moved the configured the bottom tool bar to the side of the screen by navigating the right click menu options. After it moved I could access the forward botton. After the install however, the screen is still too small. I'm am also looking for an answer on how to correct this problem.

---

### Post by bushidomeister on 2007-01-01
Thank you for your responses.  They are greatly appreciated.

I did some more digging and found some info in the "Laptops and Hardware" section which ended up working for me.  

Hopefully this can help you as well Tuffstuff.  

------------------------------------------------------------------
Installing on a Dell Inspiron 1100    - ssnitily

I had the EXACT same problem. Here's what I did:

1) In a terminal window type: sudo gedit /etc/X11/xorg.conf

2) Change your data to what I have below (actually, add this info, <i>in addition to</i> what you already have):

Section "Monitor"
Identifier "Monitor0"
VendorName "Monitor Vendor"
ModelName "Dell 1024x768 Laptop Display Panel"
HorizSync 31.5 - 48.5
VertRefresh 59.0 - 75.0
Option "dpms"
EndSection

and in Section Screen, change the monitor line to read

Monitor "Monitor0"

3) Save, close gedit, and then restart the x drive (crtl, alt, backspace). It should work.

4) Now, this is the part where you'll need help elsewhere... After a hard restart, this will probably go back to the small screen. You'll need to configure things so that this loads earlier in the startup sequence. I had a friend help w/ this... sorry, I don't know how he did it. Ask around the forums. At least you'll be able to easily fix it every time until you can get help with the part I can't help you with.
------------------------------------------------------------------

---

### Post by Heratiki on 2007-05-09
Changing your xorg.conf is just a work-a-round...  Try and fix the problem the right way... Evidently Linux and the Inspiron 1100 have always had problems so they've coded workarounds into the vid drivers...  And this has all been fixed by Dell...  It has something to do with how the BIOS supports the Video RAM...  Linux want's to know right away and the BIOS wants Linux to make the decision for you...  So if you update the BIOS of your Inspiron 1100 then the BIOS will handle that at boot time before the OS and you won't have any problems...  You can even install in 1024x768 no problems...  Hope this helps and if it does please sticky it as this seems to be a very large problem...  You need to have atleast BIOS A32 for the Inspiron to see this problem end...  I've tried many flavors other than Ubuntu and all have basically the same problem unless they coded a workaround.  So here ya go...

---

