---
title: "[SOLVED] fresh install, no X"
date: 2008-03-08
forum: Installation &amp; Upgrades
---

### Post by keratos on 2008-03-08
Hi

I've just installed Ubuntu on a totally new, fresh, clean machine.

CD booted fine, got a GUI, clicked the "install" icon and away it went.

Post install, I get a wierd desktop, all corrupted, mostly black with the word "ubuntu" across the screen several times at the top, but blocky and hardly visible. Lots of distortion and its totally unreadable.

How do I get the machine to autodetect my graphics card and sort the screen out. It was fine during install. Got a nice brown desktop!

After much gooleing I tried

dpkg-reconfigure xserver-xorg

I selected a "safe" bet and went for "vesa" but now I dont even get a desktop, just an error message from X about " sys error calls".

I'm on another PC and cannot copy/paste the other PC errors to these forums.

HELP

It cannot be my machine's hardware because the install went a breeze. No probs with the screen.

Someone please help
 
I tried

---

### Post by kellemes on 2008-03-08
What videocard do you have?

---

### Post by keratos on 2008-03-08
I've no idea

I'm a Windows to Linux n00b

No idea.

Just thought it was like windows...put the cd in, and it works. 

Like I said, the install went fine. Had a desktop there!

Can you still help?

---

### Post by Pumalite on 2008-03-08
Boot the Live CD and from the Terminal, post:
lshw

---

### Post by keratos on 2008-03-08
just looked at the m/b manual

it says 

"Integrated VIA DeltaChrome Graphics Processing Unit (GPU)
Supports upto 256MB shared memory
Supports Direct X9"

---

### Post by Pumalite on 2008-03-08
Use the Alternate CD to install.

---

### Post by keratos on 2008-03-08
Just managed to write down what the PC screen says

```

(EE) VESA(0): V_BIOS address 0xef0 out of range
(EE) Screen(s) found but none hav a usable configuration

Fatal server error
...
...

```

????

---

### Post by keratos on 2008-03-08
> **Pumalite said:**
> Use the Alternate CD to install.

what alternate CD?

Hang on...I've just remembered...

I changed the CPU to AMD.

It was an Intel when I downloaded and burnt the CD.

I havent used the CD until today.

Do I need to download another CD for AMD


I bet I do dont I

---

### Post by keratos on 2008-03-08
> **Pumalite said:**
> Use the Alternate CD to install.
Found it!

But will this definitely work? I need to buy some blank CDs just to do this.

Why do I need it anyway. The current CD loads fine, desktop appears, I can use it, browse internet, write documents and print them, install to HDD. Just no good when rebooting from HDD.

But it still worked as a LiveCD

---

### Post by keratos on 2008-03-08
> **Pumalite said:**
> Use the Alternate CD to install.

I cant post.

No way of getting the output from the brokwn PC to this one, without writing the whole text down.

Can you narrow the advice please, is there something I should be looking for?

---

### Post by Pumalite on 2008-03-08
The Alternate CD is especially made to avoid graphical problems, which is what you seem to have.

---

### Post by keratos on 2008-03-08
> **Pumalite said:**
> The Alternate CD is especially made to avoid graphical problems, which is what you seem to have.

I've just noticed from the lshw command, that my CPU is x86_64. Thus, Im downloading the x86_64 iso. Is this okay or should I still download the alternate x86_64?

---

### Post by Pumalite on 2008-03-08
I always use the Alternate CD for my installations, regardless. You have more control.

---

### Post by keratos on 2008-03-08
> **Pumalite said:**
> I always use the Alternate CD for my installations, regardless. You have more control.

ok.

so what should I do/expect.

with the other CD , it "just worked" ... to a point :-)

---

### Post by Pumalite on 2008-03-08
This is a good link to read:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by keratos on 2008-03-08
> **Pumalite said:**
> This is a good link to read:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

yes!

but it all works fine from the liveCD

its just than when i boot from HDD, it falls over.

the problem isnt my machine, its ubuntu.

---

### Post by keratos on 2008-03-08
if i stick an XP CD in the PC, it works and installs.

thus I have an inclination that it is ubuntu that is in error and not the machine.

I have heard so much about ubunutu, all the greatest, the messiah of linux.

well, perhaps not.

if n00bs like me are to be converted, then i dont expect to have to go through this just to INSTALL an O/S.

I'm out of my depth here, I just want to put a CDROM in the drive, install an O/S and use it.

Is it really, THAT difficult?

thanks for the support but I dont know what to do.

---

### Post by Pumalite on 2008-03-08
I'd burn a new CD after doing md5sum on iso, burn at 4x or less in good quality CD-R media, check CD integrity after burn and before install. I'd download a new iso if necessary. I forgot if you are using the Alternate CD or not, but I'd definitely give that a shot.
Follow this guide:
[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28)
You have a graphics problem that can be fixed at the end of your installation with the Alternate CD.

---

### Post by keratos on 2008-03-09
> **Pumalite said:**
> I'd burn a new CD after doing md5sum on iso, burn at 4x or less in good quality CD-R media, check CD integrity after burn and before install. I'd download a new iso if necessary. I forgot if you are using the Alternate CD or not, but I'd definitely give that a shot.
Follow this guide:
[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28)
You have a graphics problem that can be fixed at the end of your installation with the Alternate CD.

Well, had to give up last night my friend, needed some sleep.

GOOD NEWS!

The alternate AMDx64 CD worked. Lots of text inputs to which I ignorantly entered "OK" or whatever the default was.

Not sure if it was the media, burnspeed,  the build (this time I was using AMDx64 rather than x64 [intel]) or whatever..

but it works now.

incidentally, I was googleing around this morning and discovered the attached script which beautifully installs automatically, the openchrome driver for my VIA K8M8900 chipset. Currently X was using vesa driver... not any longer :-)

Thanks buddy for your advice.

---

### Post by Pumalite on 2008-03-09
You are welcome. Good luck.

---

