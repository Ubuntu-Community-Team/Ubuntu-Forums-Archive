---
title: "Resolution/Graphics Problems"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by PrinceArithon on 2007-10-19
Ok, here is the situation....

I just updated from Feisty to Gutsy...I know how cute right??  Anyway, all went well after 10 hours of expected downloading.  I reboot the system after all is done, and behold I'm having a graphics problem.  Something about I need to reconfigure my situation, so I go into reconfigure and I pick my nvidia driver (I'm using an NVidia 7900 GS by the way).  Anyway, I go from there into my restricted drivers and I check the checkbox for the nvidia driver.  It asked me to restart my system and so I did....I still got the same thing asking me to either reconfigure my drivers.

Ok so I go in and I do the sudo dpkg reconfigure xorg or something like that.  Set everything up for nvidia, even clicked on all of the resolutions it had to offer me.  This usually fixes everything...and this time it did not.....

So ok I went into my xorg.conf file and checked to see if everything was all nvidia friendly, not to mention to see if my resolutions were in the file.  Sure enough everything was in the file as it should have been....yet still I'm stuck in this aweful 800x600 resolution and I don't have that nice little compiz fusion thing going on...or whatever it is that Gutsy is supposed to have.

Can anyone please tell me what I maybe over looking??  I feel kinda frustrated and ashamed that I'm even having this problem....

Aaron

---

### Post by PrinceArithon on 2007-10-19
I just tried the nvidia-glx-new driver, and it doesn't work either, I'm still at a loss.

By the way here is my useful dmesg

 NVRM: API mismatch: the client has the version 1.0-9639, but
 NVRM: this kernel module has the version 1.0-9755.  Please
 NVRM: make sure that this kernel module and all NVIDIA driver
 NVRM: components have the same version.

I'm not 100% sure what this means


Aaron

---

### Post by Chainz on 2007-10-19
Have you tried removing Compiz first, then trying to fix resolution?
I've seen couple of people complaining on this: Gutsy + Compiz = resolution problems ;)

---

### Post by PrinceArithon on 2007-10-19
Tried it and it still doesn't work.  I'm still stuck in the low graphics mode.

Aaron

---

### Post by PrinceArithon on 2007-10-19
Bumping this on up, still can't get it work...

---

### Post by Temporo on 2007-10-19
Bump...

---

### Post by hansie99 on 2007-10-19
I have just upgraded my system from Feisty to Gutsy and I also have strange resolution/graphic problems. 

Starts in low-res 800x600 mode and even with compiz disabled I have lots of screen artifacts. And it is very, very slow... Wrong driver I guess, but no matter what ATI driver I select (I use a ATI Radeon 9000 so I ve tried Ati mach..etc., radeon, vesa, I even tried Envy prog but it says that my card supports Legacy driver and this driver isn't supported under Gutsy ) I get the same problems or worse. Even Vesa mode does not work; I get a totaly distorted screen. 

It does not recognize my monitor rigth either, and even after selecting the rigth one + a higher resolution, after a restart I'll get the low-res back... It works for one session, but as mentioned with lots of artifacts and very very slow.

Direct rendering is off and also I get 'Mesa' instead of Ati.. So, definitly wrong driver, but what do I have to do to install the right driver??? 

Thanx in advance for any suggestions!

---

### Post by enchesss on 2007-10-19
This system is also stuck in 800x 600 after installing Gutsy using alternative CD.

Was reallly excited because the text based installation went really well and I got through the whole thing with the video card (ATI radeon HD2900 pro) - this is a first!!

But the system reboots itself on start up about 2 bars into the orange line.

When swapping to internal card everything worked fine until I enabled restricted drivers through system admin to give the card another go. 

The card again rebooted the system on start up and now the internal card is stuck on 800 x 600 and there are no other choices.

---

### Post by PrinceArithon on 2007-10-19
Yeah I know what you guys mean, I'm just still wishing smeone had an answer for this...I've tried a few more things since this and nothing is working at all.

Aaron

---

### Post by Thebigdee on 2007-10-19
I seem to be having a problem related to this issue aswell.

I'm trying to install 7.10 from a live disk, but when the disk loads up, my monitor goes on standby as if it is trying to display a resolution it cannot. 

Any ways around this discovered yet?

---

### Post by Blara on 2007-10-19
same issue, but different.

Can't get the ati driver to load no matter what I do, lspci outputs this:
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AR [Radeon 9600]
01:00.1 Display controller: ATI Technologies Inc RV350 AR [Radeon 9600] (Secondary)
so it finds my card I just can't get the correct driver to load :(

---

### Post by fmc6338 on 2007-10-24
using nvidia 7600 gs stuck in low res. 640 by 480.

---

### Post by MrHobbit on 2007-10-24
Video card: Asus EN8600GT (based on GForce8 chipset of nVidia).
My upgrade to gutsy went fine.
The resolution problems came when I upgraded the nVidia driver (download from nVidia website) from 100.14.11 to 100.14.19. 
I ended up with a resolution of 640x480, and this was the only choice I had.
Going back to 100.14.11 worked and gave me back a reasonable resolution.
Then I decided to delete (rename) /etc/X11/xorg.conf and run the 100.14.19 installation again.
This seemed to resolve my issue. I have plenty of resolutions to choose from now.

Just in case it may help somebody ...

---

### Post by alainhenry on 2007-10-24
And I have a similar problem with a Nvidia Geforce 4000.  Upgrade went OK, but I am stuck with a 800x600 resilution.  Though the restricted driver is activated, the dialog box for resolution settings does not allow me to select it.  I'm stuck with a default VESA driver, if I understand correctly. 

Hint for upgraders to be: Maybe I should have uninstalled the nvidia driver before the upgrade, and then reinstall it after the upgrade ?

---

