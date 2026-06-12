---
title: "Installing Ubuntu"
date: 2007-11-09
forum: Installation &amp; Upgrades
---

### Post by tehpwnerofn00bs on 2007-11-09
So I had a 7.10 disc sent to me but I cannot get it to work. I boot from the disc and it will go to the first menu, so then I click on install, and it says something about the kernel loading or working- I can't remember- and goes to a blank screen. After a few minutes, my cd drive stops doing anything and the computer justs sits there. Also, my motherboard gives me an error code, so I'm not sure what is wrong with the boot process or the disc. What's wrong, or what am I doing wrong?

On the other hand, is there an alternate way that I can install linux; one that doesn't use a disc? Like a usb drive?

---

### Post by Pumalite on 2007-11-09
You can try the Alternate CD. I'd be interested in your specs.

---

### Post by tehpwnerofn00bs on 2007-11-09
Alternate cd? I've only got one....

my system: Q6600, Evga 680i SLI, 2x Evga 8800gtx, 2gb Crucial Ballistix PC8500, 500gb hd, Vista Ultimate.

---

### Post by Pumalite on 2007-11-09
Download an iso from here:

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
Mark the box below the green sign 'Start Download'

---

### Post by tehpwnerofn00bs on 2007-11-09
I have tried burning the iso myself but I ran into the same issuse I have now. Actually, I don't think that it got as far as it did this time, which is hardly anywhere....

Do I have to load the iso through a cd? could I just save it on a hd partition and boot from my hard drive?

---

### Post by dickinsd on 2007-11-09
I don't mean to hijack this thread - I thought it better to ask in this one as I think my question is similar. 

I want to use Ubuntu on this Laptop I currently have in my posetion - it's my only computer at the minute whilst my MacBook sits on some service desk somewhere for god know how long... 

Back to the point - my Laptop has seriously limited in resources and this great Ubuntu CD does not seem to have an easy way of installing Ubuntu without the Live environment - but the lack of resources seriously don't like the Live environment.

Can someone tell me how I can use the 'desktop CD' to install Ubuntu WITHOUT having to go into the Live environment - I've seen posts where people say type **ubiquity only** or **ubiquity-only** (not sure which is correct). But where do I type this? 

I've tried pressing F6 and just typing both arguments at the end of the string but both options took me to the Live environment again...

Another post says download the install CD - is this my only option? I don't have a CD burner so this really isn't an option. 

If there is not a way of using the Live CD to install WITHOUT having to go into the Live environment - can someone tell me how to get the INSTALL ISO on to a USB drive and how to use it. (Although not entirely sure if this Laptop is cable of booting from USB)...

Any help greatly apprecisated.

Cheers 

Dave.

---

### Post by ragunalth on 2007-11-09
You should start the service that handles the USB, I guess is that it starts after run level 2.  That will do it.

---

### Post by tehpwnerofn00bs on 2007-11-09
> **dickinsd said:**
> I don't mean to hijack this thread - 




Oy! get your own thread! [-X  :lolflag:

I don't know what you mean ragunalth....

---

### Post by Pumalite on 2007-11-09
> **tehpwnerofn00bs said:**
> I have tried burning the iso myself but I ran into the same issuse I have now. Actually, I don't think that it got as far as it did this time, which is hardly anywhere....

Do I have to load the iso through a cd? could I just save it on a hd partition and boot from my hard drive?

You have to download an Alternate CD iso (Evga 8800gtx) and burn it as an 'Image' at 4x after you do md5sum on it and later check for integrity of the CD before install.

[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28)

After the installation you'll have to install nvidia-glx-new to have an xserver

---

### Post by tehpwnerofn00bs on 2007-11-09
xserver? I did the md5sum and it worked fine. Do i just do the cd integrity test in the initial boot up screen?

---

### Post by Pumalite on 2007-11-09
Correct.

---

### Post by tehpwnerofn00bs on 2007-11-09
Ok, so I got it all installed and set up. But now I have the same problem again. after my comp posts it goes to the select OS screen and I click on ubuntu, but it just goes to the blank screen and after a few seconds my mobo gives the error code again...

---

### Post by Pumalite on 2007-11-09
If you have it installed and all set up, is not the same problem. What is the exact error message?

---

### Post by tehpwnerofn00bs on 2007-11-09
error code is 0E which is a Checksum error: "check the integrity of the rom, bios, and message."

---

### Post by unisol on 2007-11-09
if you are having trouble burning the iso, the ubuntu site has a program called infrarecorder,download it and give it a try.

---

### Post by tehpwnerofn00bs on 2007-11-09
I've got that sorted out, using that program in fact. Its the post installation issues now. (see above posts)

---

