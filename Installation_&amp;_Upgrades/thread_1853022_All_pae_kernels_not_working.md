---
title: "All pae kernels not working"
date: 2011-10-01
forum: Installation &amp; Upgrades
---

### Post by akshayas1986 on 2011-10-01
Hey guys,

I have upgraded to 11.04 and after having fixed many issues, I have two gnawing issues left one of which is explained here

Basically, no PAE kernel boots. All the kernels which are not PAE boot fine. The splash screen loads for a split second and then disappears after which nothing responds. Cant even switch to tty1, tty2. It appears to be a video driver issue but since its a PAE kernel, it could be anything else too. 

Any help would be greatly appreciated.

Thanks
akshayas1986

---

### Post by dino99 on 2011-10-01
check that PAE is set into the bios
then dkms, kernel-source & kernel-dev need to be installed

when things are going wrong on my side, i usually purge then reinstall the package(s):
 so purge the pae kernel(s) (2 headers+1 image for each), video drivers, jockey*
then reinstall them and reboot, finally check driver activation

sudo dpkg-reconfigure -phigh -a

---

### Post by MAFoElffen on 2011-10-01
> **akshayas1986 said:**
> Hey guys,

I have upgraded to 11.04 and after having fixed many issues, I have two gnawing issues left one of which is explained here

Basically, no PAE kernel boots. All the kernels which are not PAE boot fine. The splash screen loads for a split second and then disappears after which nothing responds. Cant even switch to tty1, tty2. It appears to be a video driver issue but since its a PAE kernel, it could be anything else too. 

Any help would be greatly appreciated.

Thanks
akshayas1986
@both

Please- Slowdown a bit first...

Before you try dino99's suggestions... Nothing on those, because I think he is one of PAE's biggest supporters here... But I do think he and you are overlooking something there when you said:
> 
The splash screen loads for a split second and then disappears after which nothing responds. The splash screen doesn't load until after the kernel finishes booting > The X-Session starts it's init after the kernel boot. <> The splash screen is part of the early X init...

To verify that the kernel is booting > Reboot> Bring up the Grub Menu (If only OS, hold down the shift key) > Arrow down to the kernel menu item you want to test > Press <cntrl><e> to put it into an edit mode > Aroow down to the linux boot line (starts with "linux") > Arrow Right to "quiet splash" and replace those words with "--verbose text" > Press <cntrl><x> to boot...

That should boot the kernel to TTY Text console, where it will ask you to log in.  If it doesn't boot, is has verbose messaging turned on and should have errors hinting at the why.  (Review with <shift><pgup> and <shift><pgdn>) If it does, that confirms that the kernel is working and your problem is more likely an X problem...

---

### Post by akshayas1986 on 2011-10-03
Hey

First off, thanks to  dino and MAFoElffen for helping me out here.

As a first step, I removed the "quiet splash" and replaced it with "--verbose text". When I booted with the changes, it shows "loading please wait" and then I can see about 3 lines of text for a split second (Just like I saw the splash screen for a split second before) and the screen goes blank again. As before, the system does not respond to anything, no CTRL+ALT+F(1-to-7) combination works. 

So I purged all the PAE related packages and completely removed them. I also installed the latest AMD Radeon HD drivers from AMD's website. I re-installed all the PAE kernels again. As before, all the non PAE kernels booted just fine but PAE kernels gave me a blank screen. 

Do you guys have any other suggestions I could try?

Thanks

---

### Post by akshayas1986 on 2011-10-04
I am almost sure that this has something to do with the video driver and here's why I say it. When I boot using PAE with "--verbose text nomodeset", I get some text on screen at the lowest resolution and then it goes blank. When I boot a non PAE kernel with same parameters, I get the same text till the same point at the lowest resolution after which the resolution of the screen changes. 

So basically, the PAE kernel throws a blank screen at the point where the resolution of screen resolution is supposed to improve.

---

### Post by akshayas1986 on 2011-10-04
All right, I fixed it. The issue seems to be startup display resolution. The best my Radeon HD can do is 800 x 600 on my PAE kernel. 

Now I have all the 4GB available to me!! Thanks for all your help guys.

---

