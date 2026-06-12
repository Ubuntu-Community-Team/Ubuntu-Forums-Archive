---
title: "Installation help."
date: 2007-09-19
forum: Installation &amp; Upgrades
---

### Post by ticklemebougy on 2007-09-19
my stats
Processor	AMD Turion(tm) 64 X2 Mobile Technology TL-52, 1600 Mhz
 RAM: 2gb DDRII
 Hard Drive: 160GB Serial ATA 5400rpm
GraphicsATI Mobility Radeon X1300

in the instalation it goes to the uduntu logo then a load of text then i get this error message

"failed to start the X server (your graphical interface). It is likely that it is not set up correctly.Would you like to view the X server output to diagnose the problem?"

im using an acer aspire 5103wlmi

ive installed it from the Standard personal computer download

should i use the 64bit?

---

### Post by Pumalite on 2007-09-19
Say no to checking your xorg file, then at the command line:
sudo dpkg-reconfigure xserver-xorg, choose most defaults, choose 'vesa' as the driver, then: startx

---

### Post by ticklemebougy on 2007-09-19
startx right after i choose that option or after the whole configuration? sorry im a complete newbie

do i keep configuring everything? mouse keyboard etc?

i gt upto deciding the color (24bit) etc when a little comand line comes up but i dont know how to confirm the awnser

im going to bed now so ill check again in the morning

---

### Post by ticklemebougy on 2007-09-20
after startx i get this error

[http://ubuntuforums.org/showthread.php?t=527548](http://ubuntuforums.org/showthread.php?t=527548)

there are solutions but i cant make any sense of them.

---

### Post by ticklemebougy on 2007-09-20
anyone?

---

### Post by Pumalite on 2007-09-20
I looked at your link, but there are many possibilities. You will have to be specific about your problem and specific about error messages and when they occur.  I'm sure we can solve it with appropriate data.

---

### Post by GordonMorgan on 2007-09-20
Hi all, is it ok to jump in on the thread? 
I have the same problem as ticklemebougy with an Acer Aspier 5100 same specs as above but only 1Gb RAM. The problem is to do with the ATI X1300, i also get the xserver error and after trying numerous 'fixes' found in various posts such as:

the alternate ubuntu 7.4 x86 cd (at least this allowed me to install Ubuntu as the live cd wont boot on my sys)

still wont boot into ubuntu desktop get no screen detected error so tried:

sudo nano /etc/X11/xorg.conf

then changing the driver in the Device section to ati, vesa and even radeon (None of which have worked still get no screen detected error)

then tried:

dpkg-reconfigure xserver-org

still the same though during this i cannot get wireless network to connect essid is same as my router but router is using WPA encryption and ubuntu setup only has WEP, at least thats all i can find (Noob so dont know the ins and outs of linux cmd line) So assume that is the reason.

If i allow ubuntu to go as far as it can during boot up it dumps me to a screen with the xserver error log etc canceling this dumps me into a screen with text from previos options, with no real command prompt but i can type cmds in if im quick enough as every 10 seconds or so i get an error message that keeps popping up on the screen:

bcm43xx-microcode5.fw not available or failed to load.

I've also tried from Boot: live vga=771
&                                       live vga=771 noapic nolapic

as ive seen that posted on a forum elsewhere. Any joy?...... U guessed it nope. Am just about ready to quit which is a bummer as i wanted to compare the JVM's on windows vista and Ubuntu for a BSc Hons dissertation. Do u have any ideas or maybe can  suggest a possible alternative to Ubuntu 7.4 that is known to definitely work with ATI X1300 and Turion X2 laptops (though have seen posts stating that Ubuntu 7.4 will work).

Only thing i havent tried yet is to add the following to the xorg.conf which has been suggested elsewhere:

Section "Extensions"
           Option "Composite" "Disable"
EndSection

Apparently this has something to do with the fact that by default Ubuntu boots with Composite enabled, and when using the generic ati / vesa driver it causes problems with the X1300 but as i say im a Noob so im only paraphrasing what ive seen posted elsewhere.

---

### Post by Pumalite on 2007-09-20
Your laptop is a real problem and your card a real pain, but I'll give you a collection of boot parameters you can try:

[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)

[http://www.tldp.org/HOWTO/BootPrompt-HOWTO.html](http://www.tldp.org/HOWTO/BootPrompt-HOWTO.html)

[http://www.hispafuentes.com/hf-doc/HOWTOs/BootPrompt-HOWTO-html/BootPrompt-HOWTO-3.html](http://www.hispafuentes.com/hf-doc/HOWTOs/BootPrompt-HOWTO-html/BootPrompt-HOWTO-3.html)

Good luck.

---

### Post by GordonMorgan on 2007-09-20
Thanks  Pumalite can i be a real pain though and ask if u know the grub boot paramater for disabling Composite, which is really the last option that i feel i have after trying all the other 'fixes' i posted above. Perhaps disabling the broadcom wireless network adapter may help too which i believe the bcm43xx-microcode5.fw error message refers to

---

### Post by Pumalite on 2007-09-20
You got me there. Sorry.

---

### Post by GordonMorgan on 2007-09-20
lol thx anyways, will have to find something else for my dissertation (sigh)

---

