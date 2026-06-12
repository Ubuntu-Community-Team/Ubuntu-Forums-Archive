---
title: "Re-install 10.10 from 11.04"
date: 2011-07-20
forum: Installation &amp; Upgrades
---

### Post by Maxiejoe on 2011-07-20
I upgraded to 11.04 from 10.10 that was working good but after he upgrade I am only not able to use the full 11.04 due to my older computer it says.   I have tried to make flash sticks to run 10.10 and reinstall it but am unable to run 10.10 from the sticks or  even get the screens to try.  I reset the BIOS to boot from usb also.

I tried unetbootin and live usb install also with no luck.  How can I delete 11.04 and get back to 10.10?
Thanks for any help.

---

### Post by MG&amp;TL on 2011-07-20
You don't need to delete *anything* before you reinstall with version x of ubuntu. If the USBs don't work, I would suggest burning some cds instead (use lowest possible speed, don't extract the .iso, etc.)

Cds tend to be more reliable.

Once you get Ubuntu booting from cd, select the option that says to remove 11.04 and replace with 10.10. If  you want to keep your files, either back them up first, or if you're lucky there might be an 'upgrade' option on the live cd which will install the OS, but keep the files. I've only seen this on *up*grades before though.

What error message does it give when you run 11.04? That's probably the question to ask first, you may need to install drivers or select 'Ubuntu classic' from the login menu. Or any number of other things.

---

### Post by Maxiejoe on 2011-07-20
I am running 11.04 Classic and am getting no error messages,  since I upgraded movie player and  vlc media player crash if volume is changed, also the gnome configeration  power Installation says the Installation is bad at boot.  Due to it telling me that my computer will only run Classic I thought it would be better to go back to 10.10 when everything was good.  

I will try a live CD instead of the flash drive, thanks for the sugestions.

---

### Post by MG&amp;TL on 2011-07-20
Generally, if you have more than two problems with a release, it's not worth trying to fix it, so 10.10 is the best option. Have a go with the cd and see what happens. If the partition menu does not give the options you'd like it to give, just eject the disk and post for advice.

No problem :)

---

### Post by Maxiejoe on 2011-07-20
Thanks,  Will give the CD a go.

---

### Post by MG&amp;TL on 2011-07-20
Actually, is your hardware, 3d-accelerated? It won't solve your other problems, but if it's 3d accelerated and you haven't installed drivers for your card, do so. That might fix Unity problem. If normal unity won't work because your pc is not 3d-enabled, you can get around that by 

a) get a graphics card. Doesn't have to be snazzy. Expensive option though.

b) install Unity 2d. Go to the software centre, and search 'unity', then select unity 2d. Install that and logout, then select Unity 2d from login menu. It might get around your GNOME problem.

---

### Post by Maxiejoe on 2011-07-21
Ok,  I tried twice to use a live CD to boot changed BIOS to CD first , still not able to boot from CDS or Stick,  get the message when trying to open , unable to find Autorun program, 

I did install Unity 2D and I am now running the up to date 11.04 instead of Classic,  need a little more time to see what happens. Thanks for the suggestion.

I have a second hard drive with windows XP so I think I will install it also and try to install 10.04 on it although after boot  the mouse freezes. and will have to solve that problem to use that old HD. I have been using ubuntu for a couple years and have had no use for the old drive.  Have googled the problem several times with no solution so went to ubntu. Any sggestion on that would be welcome also.

Thanks agan

---

### Post by MG&amp;TL on 2011-07-21
> **Maxiejoe said:**
> Ok,  I tried twice to use a live CD to boot changed BIOS to CD first , still not able to boot from CDS or Stick,  get the message when trying to open , unable to find Autorun program, 



You don't put the cd into windows unless you want to use wubi.

Put the cd into the computer with BIOS set to cd, restart, and it should pop up with a series of images like this.

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by Maxiejoe on 2011-07-21
Thanks MG&TL,  I have the BIOS set to CD or USB, it is one selection for both,  the HD is set for second.  It still boots to 11.04,  I do not get the welcome screen or any of the other screens it just boots to 11.04 but itis running good on 11.04 now so  maybe I better just run it as it is for now.  Thanks for the info on Unity it seems to have done the trick.

What I think I will do just for learning purpose is to  run my other hard drive that has windows xp on it in an external case and try to downoad ubuntu to it if I can get it to boot from the CD or Stick.  If you are curious I will post what happens.

---

### Post by MG&amp;TL on 2011-07-21
Your cd hasn't been detected by BIOS as being bootable. Did you extract the files form the .iso? Been there, done that! Took me three cds to work it out.

Please do keep posting what happens until you are free of the any problems, when you mark it as <solved> (under thread tools) :)

---

### Post by Maxiejoe on 2011-07-21
I am going to start over from square one.  Will download  a fresh 10.04 from the web to my home folder and then to a CD using start-up disk,  does that sound ok?   I have tried about three other ways so far, unenetbootin, live usb also.

---

### Post by MG&amp;TL on 2011-07-21
Yep, that sounds the most reliable.

Tips:

Burn on slowest possible speed.

checksums. See here: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Don't extract the .iso

Be careful when handling disks. :)

---

### Post by Maxiejoe on 2011-07-21
Will keep you posted on progress and I will do a fresh download and try again,  It has me stumpted on why it will not boot to 10.04 from the stick or CD.  I did check the files on the CD/Stick and it seems they are all there???

---

### Post by drs305 on 2011-07-21
As long as you have a working Grub 2 menu and can put the ISO file on your hard drive you can boot the ISO directly and then install without ever having to put it on a flash drive or CD.

Here's the guide I wrote for doing the above. I wrote it for users stuck at the Grub rescue prompt, but if you are at the Grub menu it's even easier.
[http://ubuntuforums.org/showthread.php?t=1599293]("http://ubuntuforums.org/showthread.php?t=1599293")

---

### Post by MG&amp;TL on 2011-07-21
This is what I mean about extracting the files. All you should be able to see on your cd/usb is one file labelled version 'x' .iso Don't double click on the file, on some systems, this extracts it so that you can see the files. IDK why, but cds won't boot unless the .iso is untouched.

---

### Post by Maxiejoe on 2011-07-21
Have to give it up for tonight,  will try tomorrow with fresh download and re-post,  thanks again for all the help.

---

### Post by MG&amp;TL on 2011-07-22
No problem...:D

---

