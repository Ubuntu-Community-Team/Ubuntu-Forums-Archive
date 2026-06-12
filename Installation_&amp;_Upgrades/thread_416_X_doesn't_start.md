---
title: "X doesn't start"
date: 2004-10-13
forum: Installation &amp; Upgrades
---

### Post by spaaz9 on 2004-10-13
I have an eMachines T1100
It has onboard graphics, but I am using a nVidia TNT2 32MB PCI card.
When Ubuntu boots up, it says starting GDM, but then the XServer never starts.  I just get a blank page.  Is there a way to specify which card I want it to use?  Lycoris Desktop/LX identifies the onboard graphics, but I am able to change it to the nVidia driver.

I think this is the problem... Any suggestions

---

### Post by ubuntu-geek on 2004-10-13
I had this problem on my test machine using a older nvidia card, to get it to work I did the following.

sudo apt-get install nvidia-glx
sudo nvidia-glx-config enable

Then rebooted and it was happy.. Maybe that will work for you.

---

### Post by spaaz9 on 2004-10-13
I can't even get a console though.

---

### Post by FLeiXiuS on 2004-10-13
**How to boot in to recovery**
Upon boot, your system will preform a post to check hardware installed.  Right after this post grub will then be booted.  Push ESC to enter the grub menu.  From there select by default option 2.  Push enter and await boot.  If you haven't set a ROOT password just wait until it prompts for root password.  Push enter and then voila root is now loaded.  I would enable a password immediately. 
```
passwd root
```

After this then I would follow what ubuntu-geek said.

[quote=ubuntu-geek]sudo apt-get install nvidia-glx 
sudo nvidia-glx-config enable[/quote]

---

### Post by spaaz9 on 2004-10-13
I looked right at that option, and didn't use it.. Thanks!  I'll try it when I get home.

---

### Post by spaaz9 on 2004-10-13
Ok.. still doesn't work.  On boot, I noticed that it says ignore pci display device on PCI:01:0e.0
I'm assuming that's my pci card.  Now how do I get that to work?

---

### Post by spaaz9 on 2004-10-14
figured it out... BusID wasn't correct in XF86Config-4.  I ran lspci and got the right BusID and then entered that into XF86Config-4 and it all runs peachy now.  Thanks for your help though.

---

### Post by daniels on 2004-10-14
[quote=spaaz9]Ok.. still doesn't work.  On boot, I noticed that it says ignore pci display device on PCI:01:0e.0
I'm assuming that's my pci card.  Now how do I get that to work?[/quote]

That's not actually a bug, that's just hotplug being too noisy about what it does -- it's saying 'hey, I'm not loading a module for your video card' ... but no-one actually cares.

[quote=spaaz9]figured it out... BusID wasn't correct in XF86Config-4.  I ran lspci and got the right BusID and then entered that into XF86Config-4 and it all runs peachy now.  Thanks for your help though.[/quote]

Presumably it was detecting your onboard video -- if you can disable this through the BIOS, that's the best move as we don't have any real support for multiple video cards ... yet.

---

### Post by spaaz9 on 2004-10-14
All I get is the option to choose either PCI or AGP (AGP being the onboard video).  I have it set to PCI.  This could seriously throw off someone who is just trying out Linux for the first time, so maybe this could be a FAQ on the official Ubuntu site.

---

### Post by daniels on 2004-10-14
[quote=spaaz9]All I get is the option to choose either PCI or AGP (AGP being the onboard video).  I have it set to PCI.  This could seriously throw off someone who is just trying out Linux for the first time, so maybe this could be a FAQ on the official Ubuntu site.[/quote]

Yeah; mercifully it's not a hugely common configuration (if you've put in your own video card when you have onboard, chances are you know what you're doing).

Thanks for the report, though.  We should hopefully have proper multi-card configuration in Hoary.

---

### Post by spaaz9 on 2004-10-14
No problem.  Only held me up for a couple of hours, but now I have it running smoothly.

---

### Post by burque on 2004-10-26
Well, I think there are many hundreds of thousands of machines out there with onboard video and aftermarket PCI cards. Many don't even have an AGP slot (like the three I have PCI video cards in.)

As I posted elsewhere, Kanotix and XFLD live CDs boot me into X, and ubuntu resists (Kanotix defaults to vesa, but XFLD correctly finds my sis card). Obviously support for multiple video cards is alive and well out there in the wild.

Regards,
burque

---

### Post by nightmaresc on 2005-02-25
I have a laptop and I think I'm having a similar problem, except I'm using Hoary.

I get the blank screen as well but I can hear the sound effect that plays when the login screen appears so I know its actually there.  Is this the same thing or not?

I tried lspci but I don't see where I get the busid for my display.  The only relevant thing I see under the display is this:

0000:01:00.0 VGA compatible controller:  VIA Technologies, Inc.  VT8378 [S3 UniChrome] Integrated Video (rev 01)

I was told I was to use xorg.conf for Hoary.  The xorg.conf file has BusID: "PCI:1:0:0"

Any advice?

---

