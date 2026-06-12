---
title: "proper os of ubuntu for windows 2000"
date: 2012-11-07
forum: Installation &amp; Upgrades
---

### Post by maglax on 2012-11-07
Hey I have been trying to convert my old Windows 2000 computer to a Ubuntu os. Unfortunately I have no idea of what version of Ubuntu I need. Can anybody tell me what is the best version of Ubuntu to use? Thanks!

---

### Post by firstlinux7 on 2012-11-07
> **maglax said:**
> Hey I have been trying to convert my old Windows 2000 computer to a Ubuntu os. Unfortunately I have no idea of what version of Ubuntu I need. Can anybody tell me what is the best version of Ubuntu to use? Thanks!

Obviously, I am new here. Anyways, I think that a good place to start would be with the hardware specifications of the machine in question. How large is the hard disk? How much RAM does it have? What sort of CPU does it have?
Questions like this these will help narrow down which distributions (Ubuntu, Kubuntu, Lubuntu, or outside of the Ubuntu family) will work.

---

### Post by maglax on 2012-11-07
I cannot tell you the space on the hard drive or the amount of RAM because it does not say on their and it was given to me by my uncle. I can tell you though it has a Pentium 4 possessor

---

### Post by firstlinux7 on 2012-11-07
> **maglax said:**
> I cannot tell you the space on the hard drive or the amount of RAM because it does not say on their and it was given to me by my uncle. I can tell you though it has a Pentium 4 possessor

Is the Windows OS still bootable? If so, you can find system information by using msinfo32.exe,

---

### Post by maglax on 2012-11-07
Ok then I just opened her up and found she has a 20.4GB hard drive and more then 236MB of RAM. There were two 128MB cards and two without lables.

---

### Post by maglax on 2012-11-07
No Windows is not bootable i tried installing 10.10 and it went really slow.... :O

---

### Post by firstlinux7 on 2012-11-07
> **maglax said:**
> Ok then I just opened her up and found she has a 20.4GB hard drive and more then 236MB of RAM. There were two 128MB cards and two without lables.


By my rough estimate, it seems that, of the two, your RAM is going to be the biggest issue (of course, it depends how much those unlabeled cards are). I had a dual booted Ubuntu/Windows combination with only 16GB of hard disk space dedicated to Ubuntu, and I still had plenty of room left for programs and files.

Finding out how much memory it actually has would be helpful. In the BIOS of most computers is some way to view the amount of installed memory. Look for the computer to tell mention some hotkey (delete, f10, etc.) during bootup to get into your BIOS configuration screen.


Also, here are some helpful links:
[https://wiki.ubuntu.com/Lubuntu](https://wiki.ubuntu.com/Lubuntu)
[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

---

### Post by maglax on 2012-11-07
I do only want to be running Linux on this machine so it wont be sharing with windows

---

### Post by maglax on 2012-11-07
on the boot screen it goes kinda fast but i saw 265 and i think it was MB so i am assuming it was the RAM

---

### Post by maglax on 2012-11-07
[IMG]https://mail.google.com/mail/u/0/?ui=2&ik=2ef0fe8e5d&view=att&th=13ade4a650bc22c2&attid=0.1&disp=thd&zw[/IMG]
There is a picture of the boot screen. Sorry it is kinda blurry.

---

### Post by firstlinux7 on 2012-11-08
> **maglax said:**
> I do only want to be running Linux on this machine so it wont be sharing with windows

Correct. Since you will be using the entire 20GB disk for your Linux installation, you should be OK there.

If you really only have 256MB RAM, I think you should take a look at Lubuntu. Note, however, that the Lubuntu documentation page mentions the possibility of needing the alternate installer with as much as 800MB RAM. 

Do you have a lot of spare record-able media or a re-writable CD/DVD? If not, you can always try to use USB booting, which may or may not be BIOS supported.

---

### Post by maglax on 2012-11-08
i guess what i am asking is not what favor but what version like the release i guess of ubuntu

---

### Post by maglax on 2012-11-08
And also i tryed installing the newest version of Lubuntu and it wont even past the partition part

---

### Post by oldos2er on 2012-11-08
> **maglax said:**
> i guess what i am asking is not what favor but what version like the release i guess of ubuntu

I would stick with newer versions of Lubuntu if I were you. With so little RAM though, it's not going to be a pleasant experience. See [https://wiki.ubuntu.com/Lubuntu#System_Requirements](https://wiki.ubuntu.com/Lubuntu#System_Requirements)

---

### Post by maglax on 2012-11-08
the only problem with lubuntu is the newest version WONT install

---

### Post by firstlinux7 on 2012-11-08
> **maglax said:**
> the only problem with lubuntu is the newest version WONT install

I would definitely agree that using the latest version is preferable to using an older one. At a minimum, try to find a release that is still supported (ie. software updates).

Hmm. Do you have the opportunity to try the alternate installer CD? The community documentation page mentioned that the alternate installer might be the only way to get it installed with low RAM. 

Also, I could not view that image of the BIOS screen (maybe something about the forums with new users???). Perhaps you could try to post a link to the file in Google Drive or some other file sharing website.

---

### Post by maglax on 2012-11-09
Ok i might try the alternate install cd.

---

### Post by deadflowr on 2012-11-09
For something that old, I'd go with either

[Bodhi Linux]("http://www.bodhilinux.com/")

[Crunchbang]("http://crunchbang.org/")

or [Puppy Linux]("http://puppylinux.org/main/Download%20Latest%20Release.htm")

These are all super light. Great on older machines.

---

### Post by lisati on 2012-11-09
> **maglax said:**
> [IMG]https://mail.google.com/mail/u/0/?ui=2&ik=2ef0fe8e5d&view=att&th=13ade4a650bc22c2&attid=0.1&disp=thd&zw[/IMG]
There is a picture of the boot screen. Sorry it is kinda blurry.

The link to your image didn't work very well. You can add an image to your message here by uploading it with the "manage attachments" button when composing a new reply.

---

### Post by maglax on 2012-11-09
ok it should show up now it is a little blurry tho

---

### Post by maglax on 2012-11-09
> **deadflowr said:**
> For something that old, I'd go with either

[Bodhi Linux]("http://www.bodhilinux.com/")

[Crunchbang]("http://crunchbang.org/")

or [Puppy Linux]("http://puppylinux.org/main/Download%20Latest%20Release.htm")

These are all super light. Great on older machines.
ok thanks i will try one of those i have tried ubuntu 6.10 but many of the programs no longer work -___-

---

### Post by kurt18947 on 2012-11-09
+1 on Puppy.  I got it to load on an original Celeron with 64 MB. RAM.   About all it would do is load, though:).  If you have a P4, you might look into adding RAM.  I have an old PIII notebook with 512 RAM.  It had one 256 DIMM.  I got another off Ebay for about $5.  Lubuntu uses around 200 MB.  Works fine for web browsing but won't run flash.

---

### Post by mastablasta on 2012-11-09
also to try out: 
 
Debian with LXDE is going to be lighter than Lubuntu.
 
Slitaz is another super light linux. can run on very low ram.
 
if you feel adventurous you could try TinyCore or DSL (i think this one still uses old kernel so there could be security issue)
 
if you can it would be good to get an old ram stick and increase the ram (if that is possible on your motherboard). if you could increase the ram then Xubuntu would play well.
 
Consider that RaspberyPI, a credit card sized computer on 700Mhz ARM CPU and 256MB ram (previous model) is running modified Debian LXDE. so there is hope.
 
Bodhi has 128MB as requirement and looks nice.
 
as for which verison of *buntu t use - if you go lubuntu then use 12.10 otherwise 12.04 LTS will be ok on your hardware.
 
edit: 
 
if you don't mind the looks you can also try AntiX Linux (debian based)

---

### Post by robert shearer on 2012-11-09
[http://www.bodhilinux.com/](http://www.bodhilinux.com/)
Bodhi is ubuntu based and should run sweetly on your old hardware.

---

