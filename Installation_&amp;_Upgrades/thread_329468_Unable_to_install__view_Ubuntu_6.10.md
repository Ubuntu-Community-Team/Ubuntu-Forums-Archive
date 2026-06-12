---
title: "Unable to install / view Ubuntu 6.10"
date: 2007-01-01
forum: Installation &amp; Upgrades
---

### Post by flir48 on 2007-01-01
Thought I'd reinvestigate the Linux world again, and heard about this Distro and I thought I'd give it a go....

But...I cannot install, or run from CD.

When I select option1 (Run / Install Ubuntu).. CD spins up.. hard drive churns..etc..
Then after a bit, it appears that the vid card is being reinitialized..and I'm stuck with a black screen.
DVD/CD drive is still active and judging by activity alone, it appears Ubuntu is loading from the CD, then the drive stops after a few minutes.
But..the screen is still black.  I've tried various VGA Settings to no avail....

I am unable to do a thing... 

Hardware Setup:
 - AMD Athlon 64 /X2 4400
 - Asus A8N-E
 - ATI 1800XT Pro (512megs)
 - Sceptre 22" LCD widescreen
 - 1 GIG Corsair PC3200 - stock timings.. 
 - 1 WD Raptor  75gig
 - LiteON DVD/RW+- (dual layer)
 - Sound, NIC, USB are part of the Nvidid Nforce4 Chipset and Nvidia states
   linux distro's include these already.

Can anyone help?  Keep in mind.. the only thing I know about linux is how to spell it.
(BTW...CD test function reports "ok")

Any help would be appreciated as I'm investigating the possiblity of migrating from windows.


thanks..
Brett
(flir48)

---

### Post by flir48 on 2007-01-02
Bumping for attention...

It appears I'm not the only one going thru this similar issue.

---

### Post by taurus on 2007-01-02
Are you using the 32bit or the 64bit desktop CD/LiveCD?  If you want to install Ubuntu on your machine, I highly recommend you go with the alternate CD...

[http://www.gtlib.gatech.edu/pub/ubuntu-releases/edgy/](http://www.gtlib.gatech.edu/pub/ubuntu-releases/edgy/)

---

### Post by flir48 on 2007-01-02
THanks... I'll give that a go....

I'm using the 32bit CD ISO provided thru a link on the ubuntu site..(d/loads from Georgia tech...) and I it's Edgy EFT.

---

### Post by IntuitiveNipple on 2007-01-02
You can get the Desktop LiveCD to show you what its doing. As soon as you see the Ubuntu CD menu, press F6 so you can edit the boot command line.

Then, at the end, delete "quiet splash"

When you hit enter it'll start booting the kernel and you'll see the text reports of the kernel as it loads, which might help you work out where the problem is.

---

### Post by flir48 on 2007-01-02
no go on that also..

No errors are occuring... except when it wants to throw up the Ubuntu login screen (if that what it is.. I've never seen it)...

Everything loads, but the screen resets and goes blank and stays that way.

The best analogy..is when Windows loads,, you get the WinXP splash screen, then the screen resets to show the login screen.

it's resetting, which I'm guessing, where the Vid card drivers loads.. but doesn't initialize and the screen stays blank.

I downloaded a DVD ISO and I was able to install, but the problem still remains....

how do I uninstall grub and soforth?

---

### Post by flir48 on 2007-01-02
i actually have something usefull..

using nano and editing the xorg.conf file, the ATI driver was already set to Vesa.

I changed it to frglx and I get "no driver found" when loading startx.


So that leave me to assume that the ATI drivers are gone..

I've downloaded the ati drivers, from AMD, but how do I install from the command line.
File is on a CDdrom...

---

### Post by taurus on 2007-01-02
[http://albertomilone.com/driver.html](http://albertomilone.com/driver.html)

---

### Post by flir48 on 2007-01-02
thanks.. taurus... but I don't understand...

the link is at that site is...

deb [http://www.albertomilone.com/drivers/edgy/latest/32bit](http://www.albertomilone.com/drivers/edgy/latest/32bit) binary/

which as you know means nothing to windows..  so what do I do now?
His only installer tool appears to be only for Nvidia......

do I go to the shell prompt and type:
sudo apt-get install deb [http://www.albertomilone.com/drivers/edgy/latest/32bit](http://www.albertomilone.com/drivers/edgy/latest/32bit) binary/
?????

thank you for your time...
Brett

---

### Post by taurus on 2007-01-02
It means you edit /etc/apt/sources.list 

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/apt/sources.list
```
and add that line to the end of it!

```
deb http://www.albertomilone.com/drivers/edgy/latest/32bit binary/
```

---

### Post by flir48 on 2007-01-02
thank you...

Is there a definitive idiots guide to this OS?

Over the years, I have tried linux (redhat / mandrake) in the past but the biggest problems I ran across is lack of consise information in how do to things.

It's quite frustrating.. knowing what you have to do.. but can't find information to help on how to do it.
 ie.. something as simple as switching to the local cdrom drive is a pain.
mount the drive... ok.. easy enough..     mount /dev/cdrom 
ok.. it mounted. how do I switch to the device so can run a simple dir? 
Even the local man repository was useless on how to do that and I know it's because I don't know what to search for....

..and slightly off topic.. ATI releases their linux distro's as a run file....
How can I use that with Ubuntu? or can I?

thanks again..
Brett

---

### Post by supperman on 2007-01-03
Hi, 

Sorry to hijack this thread, but I'm having the same problem as described, except I'm on the integrated graphics on the i865 board.

---

### Post by aberry5555 on 2007-01-03
I had this problem yesterday on an X800, and nearly the same mobo too, it seems the standard drivers that come with ubuntu in no way cover pci-e. 

Firstly start up your live cd then press the "F6" button, this will give you the boot options. delete the word "splash" and then go to the end of the line and type in "break=bottom" (or bottom=break, I can't remember exactly, but try the first one first). Now boot the cd. it should go through some text prompts, ignore any errors about buses and PCI resources or whatever, just make sure the cd and hd are spinning. It should then come up with a prompt asking you to type something. type in "chroot /root nano /etc/X11/xorg.conf". this will bring up your x window configuration file. Scroll down till you find the heading named "Device". Under this heading it should say that the driver being used is "ati", change this to "vesa" now save this file as the same name and exit nano (something like ctrl+w then ctrl+x, the commands are along the bottom, though save is not called save, it's called "write-out" or something similar). Now you should be back at the command line. Type exit to continue booting and you should load up gnome with the vesa drivers. This method is for the normal live-cd desktop version, not the alternate desktop cd.

---

### Post by aberry5555 on 2007-01-03
and in answer to the .run thing you can open up a terminal, type "sudo sh" and then the directory of the file, or simply "copy and paste" the file into the terminal and it should give you the directory. A ".run" file is sort of like an executable but is actually a script, so must be run as such. I think there's a .run file handler somewhere on the web but, off the top of my head, I don't know where to look. take a look at synaptic, it might be there. 

If you're worried about linux then I would just stick with it for a little while, trust me when I say the basics come to you fairly quickly. Anything severely technical can be overcome and you learn certain commands, tips and tricks along the way that make it easier, as a whole, to use the OS. 

Don't give up yet :p

---

### Post by flir48 on 2007-01-03
> **aberry5555 said:**
> This is quite a big problem that affects a fair few people but is easily overcome in a few ways. It happens because the preloaded driver on the CD doesn't work with your card, so you will either have to download the new drivers and use those or change to the "vesa" driver manually. 
[http://www.ubuntuforums.org/showthread.php?p=1961547#post1961547](http://www.ubuntuforums.org/showthread.php?p=1961547#post1961547)
Read my post on here to find out how to do it, once it's booted you should be fine.

I found this yesterday also and it resolved the issue.

you know what sucks tho?.. it's the Xorg fgrlx driver and not ATI.. which there is no help on how to install their driver...

All in all I had to boot to the shell prompt and type these commands in,
once they were done I was able to get in...

---

### Post by aberry5555 on 2007-01-03
yeah I know what you mean, but it isn't as if the people who make the drivers can help it, ATI don't want to make their drivers open source, probably for warranty reasons, who knows. Either linux distro creators have to accept that some proprietary software must be used or hardware manufacturers need to create open source drivers, unfortunately neither of those are likely to happen. 

I agree though, even if it's advised against, there should still be a walk through on how to do it.

---

### Post by supperman on 2007-01-03
I've tried following the instructions, and in my case, instead of the ATI drivers, I had i810, which I'd changed to vesa. Unfortunately, the outcome was still the same.

Should I try the alternate CD then?

---

### Post by aberry5555 on 2007-01-03
Unfortunately, off the top of my head, I couldn't help you with the exact method, though I have a vague idea of what needs doing. Basically you need to get up a command prompt once the desktop has loaded (in the memory if not on the screen) by using ctrl-alt-F2, or something, and then use that command prompt to get and install your i810 drivers using apt-get, though Id have to find out the exact package names. I'm going to be doing a fresh install on my pc at home so Ill investigate how it ought to be done and when I'm up and running Ill post back what I find. 

If you can find out what packages you need from packages.ubuntu.com (search for i810 drivers and any dependencies, I think it's name is "xserver-xorg-video-i810") then write them down and try using 

"sudo apt-get update" first, then, I think 
"sudo apt-get install linux-restricted-modules-$(uname -r)" then 
"sudo apt-get install ("xserver-xorg-video-i810" or other name, if this is not the package)

if the drivers are open source, ie not made by intel (the one in brackets is open source) , then the second line won't be needed, I don't think.

If all of that installs itself OK then type "sudo Xorg -configure" If this works then, hopefully, the desktop should work, press ctrl+alt+backspace (not delete) to try to get the x windows system working, if it doesn't, type startx. If this hasn't worked post back and Ill see if I can help further when Im in front of ubuntu

---

### Post by rbhigday on 2007-01-05
> **aberry5555 said:**
> I had this problem yesterday on an X800, and nearly the same mobo too, it seems the standard drivers that come with ubuntu in no way cover pci-e. 

Firstly start up your live cd then press the "F6" button, this will give you the boot options. delete the word "splash" and then go to the end of the line and type in "break=bottom" (or bottom=break, I can't remember exactly, but try the first one first). Now boot the cd. it should go through some text prompts, ignore any errors about buses and PCI resources or whatever, just make sure the cd and hd are spinning. It should then come up with a prompt asking you to type something. type in "chroot /root nano /etc/X11/xorg.conf". this will bring up your x window configuration file. Scroll down till you find the heading named "Device". Under this heading it should say that the driver being used is "ati", change this to "vesa" now save this file as the same name and exit nano (something like ctrl+w then ctrl+x, the commands are along the bottom, though save is not called save, it's called "write-out" or something similar). Now you should be back at the command line. Type exit to continue booting and you should load up gnome with the vesa drivers. This method is for the normal live-cd desktop version, not the alternate desktop cd.

Thanks for this between this and other I was able to gain access but I had to do it a bit different

the chroot /root did not work this is what I did
cd to bin
find nano 
then type nano /etc/X11/xorg.conf

make the changes stated above and the save which is ctrl +o and then exit which is ctrl +x
then I had to hit enter twice before the batch started up again

hope this helps someone

---

