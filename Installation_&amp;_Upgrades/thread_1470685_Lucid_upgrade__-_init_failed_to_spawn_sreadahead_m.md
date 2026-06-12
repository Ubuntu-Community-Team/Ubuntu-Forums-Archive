---
title: "Lucid upgrade  - init: failed to spawn sreadahead main process"
date: 2010-05-03
forum: Installation &amp; Upgrades
---

### Post by eye12b12 on 2010-05-03
upgraded from 9.10 to 10.04  (old IBM R51 laptop, dual boot  XP w/grub loader).   If I boot "normal"  I receive the following:

'init: failed to spawn sreadahead main process: unable to execute no such file or directory'
followed by splash screen, then blank screen, unresponsive machine.

After hard boot, chose "recovery" option received same error but made it into recovery menu.  pretty much tried everything in that menu and discovered that I could get a normal looking boot by choosing the safe graphics mode.  So at least at this point I have a work around.

did some digging around in /etc/init and looked at the sreadahead.conf  
found that it was pointing to /sbin  for a file called sreadahead.  
at this point the error makes sense as there is no sreadahead in /sbin   BUT  there is a ureadahead. So I open terminal, navigate to /sbin then:

sudo cp ureadahead sreadahead

on reboot (normal option) i now get:
 'init:sreadahead main process (270) terminated status 1'
 
My work around is still good and returns the same (new) error. So i delete the sreadahead  that i created above.  

Any ideas on where to get a copy of the correct sreadahead file that goes in /sbin ?  Any other way to get around this?  I can't boot without going into the recovery mode and selecting low graphics; but if I do, it all seems good.  It strikes me however that this really has nothing to do with my graphics or display.  It makes me think I must have messed something up in the upgrade cuz I can't find any new posts about init or sreadahead :confused:
Please help.  

BTW- The init error messages might be a little off, they don't flash for that long, I tried to copy them down as best I could.

---

### Post by marg0 on 2010-05-03
What graphical desktop environment do you use? During the upgrade process kde packages for example are upgraded too. And I believe, that some valuable kde packages are not reinstalled. I got the same error and I installed manually the following packages: kdebase, kdeadmin, kde-apps, kdegraphics, kdeutils. You can do it from console using apt-cache and apt-get or you can run startx and then press Alt-F2 and call synaptic (although the screen is black and there's no desktop screen graphical applications are executed normally using Alt-F2 in my situation).
Hope this will help you.

---

### Post by grandtoubab on 2010-05-03
sreadahead is useless now it is replaced by ureadahead
see descrition in Synaptic
[I]sreadahead has been replaced by ureadahead, this package ensures
that you are transitioned over and may be safely removed.[/I]

```
sudo apt-get --purge remove sreadahead
```

---

### Post by eye12b12 on 2010-05-03
> **grandtoubab said:**
> sreadahead is useless now it is replaced by ureadahead
see descrition in Synaptic
[I]sreadahead has been replaced by ureadahead, this package ensures
that you are transitioned over and may be safely removed.[/I]

```
sudo apt-get --purge remove sreadahead
```

I used the code indicated and received the following output:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sreadahead is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

When I reboot,  still have same "init: fail to spawn...."  
So since my machine doesn't "think" sreadahead  is installed I am going to remove /etc/init/sreadahead.conf

HOPEFULLY, I will be back in a minute or too to post my results.

---

### Post by eye12b12 on 2010-05-03
So I thought that I would be tricky and use

sudo mv sreadahead.conf ~/desktop

from inside /etc/inti thereby moving the file to my desktop rather than deleting it right off. Or so I thought... Now I can't find it. Not a big file, not a big concern other than not knowing where it went. 

oh well off to reboot...

---

### Post by eye12b12 on 2010-05-03
It didn't go as I had hoped. Have managed to rid myself of the "init: failed to spawn..." but I still have to use my work around (ie recovery from grub and then failsafe graphics mode" to get into a gnome session. 

currently if I try a normal boot, it seems to go OK until  the ubuntu logo and dot graphics appear.  after 1-2 seconds this disappears and I get an empty black screen.  So, the ONLY difference is that I don't get the init failure.  
 I am not clear what marg0 was talking about above. (a bit of a noob) am going to try to figure it out. 

chime in if you have any thoughts.

---

### Post by Jordanwb on 2010-05-04
I'm getting the same error on my parent's frankenstein computer that I built for them a year ago. Sreadahead is not installed.

---

### Post by eye12b12 on 2010-05-04
> **Jordanwb said:**
> I'm getting the same error on my parent's frankenstein computer that I built for them a year ago. Sreadahead is not installed.

have no fear in deleting /etc/init/sreadahead.conf  that will get rid of the init error. 
right now I am looking into it as a poss vid chipset driver issue (some what like marg0 suggested). Do you have the same blank screen issue?   

I am going to use the following as a startpoint when I get some time to mess around:

[http://ubuntuforums.org/showthread.php?t=1457135](http://ubuntuforums.org/showthread.php?t=1457135)
[http://ubuntuforums.org/showthread.php?t=1301433](http://ubuntuforums.org/showthread.php?t=1301433)

for now, the workaround is irritating but not quite my priority.

---

### Post by dino99 on 2010-05-06
check: system admin hardware driver, to see if your driver is activated

sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a

---

### Post by eye12b12 on 2010-05-07
latest update, my actions after post #6 - ultimate fail.  Have now  completely lost my work around -no way into Gnome. On the other hand, I am learning alot  about manual system configuration from the command prompt.  Basically, I  did a real bonehead move and installed the wrong video driver (ATI  driver - don't ask me why I did it - I have no answer) and am now trying  to fix my Xorg.conf file.  
I had been using a ZTE broadband modem for access at first but am now  tied to a wired connection due to the command prompt limitation (or my lack of know how).  This  is a difficulty as I am not at the house and getting a wired connection  is, well, difficult in the current  location.  So my ability to work on  my linux partition has been retarded somewhat by the circumstances.  
In re-installing the open source video drivers for intel and the  libgl1-mesa-dri 
```
sudo apt-get install --reinstall xserver-xorg-video-intel  libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
```I notice that  libgl1-mesa-dri is coming off my alt-install CD (I am  prompted to put it in the drive)  is there a way to redirect this?   Everything else pulled off the net when I executed the above code. When I  put the CD in it starts to read but then scroll a TON of I/O errors.  I  am in my "other" O/S right now and am downloading the ISO again just in  case the other one is corrupt.

---

### Post by eye12b12 on 2010-05-07
latest status:
Normal boot attempt from Grub menu results in ubuntu splash followed by black screen
Recovery mode boot from Grub menu will only allow me a TTY session.

have tried following advice from links in post 8 above to manually reinstall and reconfigure xorg
current errors are: 
load module vesa: doesn't exist
load module fbdev:doesn't exist

It seems to me from my reading man pages and threads  that this shouldn't be so hard to fix.  my video chipset is intel 82852/855m.

one question I have is how do i get the modules "vesa" and "fbdev" loaded?  there are probably still other hurdles but these seem to be the de'jour for me.

if any one can help or give a link to a "how to re-install default video drivers in lucid from TTY session"  please put it in here.
I would rather figure this out than just give up and completely re-install (rather learn than cheat the experience).

---

### Post by dino99 on 2010-05-08
i've search about your problems/your config:

you have started from:

****upgraded from 9.10 to 10.04 (old IBM R51 laptop, dual boot XP w/grub loader). If I boot "normal" I receive the following:

'init: failed to spawn sreadahead main process: unable to execute no such file or directory'*******

so that means: there are still oldish karmic settings braking the lucid process. No need to take care of the others errors, as they are children errors.

1):  clean the room and check the repos
- sudo apt-get clean
- sudo apt-get autoclean
- sudo apt-get autoremove

- sudo nano /etc/apt/sources.list
be sure you only have genuine lucid repo activated, no more karmic or ppa
( look messages on bottom line: ctrl x to validate then enter)
- sudo apt-get update
- sudo apt-get install ubuntu-desktop
- sudo apt-get install -f
- sudo install xserver-xorg-video-intel

2): custom grub
- sudo nano /etc/default/grub
change the line to:
 GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i915.modeset=1"
- sudo grub-config && update-grub
- sudo dpkg --configure -a

now you can try to boot again, if it fail:
- sudo nano /etc/X11/xorg.conf
change yours like this one:

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "vesa"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

Try again to boot

Your problem is known and is related to kernel conflict with 855 chipset.

Other workarounds:
a) One user reported that downgrading to the 2.6.31-10 kernel resolved the issue completely. 
b) xorg.conf looks like:

Section "Screen"
        Identifier      "Configured Screen Device"
        Device  "Configured Video Device"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Option          "AccelMethod"   "UXA"
        VideoRam        130560
EndSection

But the real solution seems be found with a newer kernel:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33.3-lucid/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33.3-lucid/)

howto:
thats suppose the previous workaround(s) have worked, then you need to install kernel 33 from url above, but in that strict order, by double clicking on the packages ( need gdebi to be installed):
** linux-source....all.deb
** linux-headers...all.deb
** linux-headers (choose i386 or amd64)
** linux-image (choose i386 or amd64)

then reboot with this kernel, update xorg.conf (or hardware driver) to use "intel" driver

good luck

[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

note: in normal configuration, lucid dont need xorg.conf, so if all is ok you can renamed it (in case you need it later) or delete it.

---

### Post by eye12b12 on 2010-05-09
Thanks for your suggestion dino99.  It caused a different result, but not the desired result:

Now when I choose the "normal" boot option from grub, I end up with a TTY login prompt.  Before I was just looking at a blank/black screen.  So the gnome environment is still not coming up. Thus I basically get the same result using "normal" or "recovery" modes. 

Based on what dino99 said about the 32 kernel possibly being an issue, I downloaded the i386 desktop iso and burned it. When booting to that CD I chose the "try it" option just to see what would happen. Result:
Ubuntu splash, followed by blank screen. (like I had previously experienced with the "normal" boot from grub)

So the kernel issue may be spot on.  So, right now the options I am considering are:
1)moving to the 33 kernel or the 31 kernel (as suggested)
2)reverting back to karmic or jaunty- along with the kernel change/ if kernel change doesn't fix issue.

On Option 1, I need a little more "how to" help on accomplishing this from the command line as  I can't "double click" packages as dino99 suggests above.  

On Option 2 please confirm or deny my plan:
```
sudo nano /etc/apt/sources.list
```activate karmic or jaunty entries (which ever I decide) and deactivate lucid entries
then:
```
sudo apt-get update
sudo apt-get install ubuntu-desktop
sudo apt-get install -f
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove
```If option one works- going to 33 kernel well, no need for option 2.  If 33 kernel doesn't work and I move to 31 with no improvement then its off to karmic or jaunty (in that order) but I think that either way, I will need to get off this current 32 kernel.  Will my process for option 2 work?  If so, will that revert me to an older kernel automatically or will i still need to change that manually?  OR are old kernels still on my machine, just not in use and all I need to do is switch to one of them? 
Suggestions?

---

### Post by Catharsis on 2010-05-09
Edit: Nevermind

---

### Post by eye12b12 on 2010-05-09
Can someone tell me if this is the correct way to change/update my kernel  to ver 33 from a TTY prompt:
```
sudo nano /etc/apt/sources.list
```then add:
```
deb http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33.3-lucid
```to list
then use
```
sudo apt-get update
sudo apt-get install linux-source-2.6.33-02063303_all
   linux-headers-2.6.33-02063303_2.6.33-02063303_all
   linux-headers-2.6.33-02063303-generic_2.6.33-02063303_i386 
   linux-image-2.6.33-02063303-generic_2.6.33-02063303_i386
```I figured this out through research and reading, fairly confident in it but would like an experienced opinion before I execute.

---

### Post by Catharsis on 2010-05-09
If you have 32-bit Ubuntu:
```
wget -c http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33.3-lucid/linux-headers-2.6.33-02063303-generic_2.6.33-02063303_i386.deb http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33.3-lucid/linux-headers-2.6.33-02063303_2.6.33-02063303_all.deb http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33.3-lucid/linux-image-2.6.33-02063303-generic_2.6.33-02063303_i386.deb
sudo dpkg -i linux-headers-2.6.33-02063303-generic_2.6.33-02063303_i386.deb linux-headers-2.6.33-02063303_2.6.33-02063303_all.deb linux-image-2.6.33-02063303-generic_2.6.33-02063303_i386.deb
```

---

### Post by eye12b12 on 2010-05-09
Thanks Catharsis for pointing me in the correct direction.  I will try to get this done later this evening- need to go find a wired connection. Will post results when complete

---

### Post by eye12b12 on 2010-05-11
Thanks to everyone who chimed in on this.  I appreciate every thing I learned.  

In the end, upgrading to the new kernel and specifying  Driver "intel" in the device section of xorg.conf got me back up and running.  

I have noticed that there are a number of people with this same problem cropping up. 
Hopefully they will find this solution a little quicker than I did.

---

### Post by marc88 on 2010-09-17
[COLOR=#000000]Hi, I have the same problem. [/COLOR]I'm Italian and I do not understand / speak English well: D
Can you tell me a summary of how you solved?

Thanks

---

### Post by el_oscuro on 2010-10-11
I got this message after upgrading to Lucid, but it did not affect any functionality, just an annoyance.

To get rid of the message, I just renamed the /etc/init/sreadahead.conf, ie:

suso mv /etc/init/sreadahead.conf /etc/init/sreadahead.conf.old

---

