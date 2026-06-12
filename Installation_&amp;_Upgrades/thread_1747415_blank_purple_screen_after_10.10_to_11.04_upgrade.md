---
title: "blank purple screen after 10.10 to 11.04 upgrade"
date: 2011-05-02
forum: Installation &amp; Upgrades
---

### Post by astroboy123 on 2011-05-02
Hi all,

Last night I upgraded to 11.04.

Upon restart of my server ( its acting as a server even though its ubuntu desktop edition ) the screen for log in is just purple. 

This is exactly what happens when I start the server from a cold boot. 

BIOS displays
Blank screen
Blank purple screen
Flashes to black screen
Back again to purple, mouse appears and is moveable across the screen. The ubuntu double bongo sound happens. Screen remains purple. 

You can move the mouse to certain parts of the screen and the curser and it will change to the text editing curser. 

I have been able to get to login screen once on the third reboot if the machine. But upon restarting again its stuck at this stage. 

I can ssh to the server if you need me to tell you any information. Its important that I can get to the login screen and login as there is applications that start upon my account login. 

Also a have 3 tb of data located in zfs. So yeah. Um help me please

Thanks in advance,

Astro

---

### Post by MAFoElffen on 2011-05-02
> **astroboy123 said:**
> Hi all,

Last night I upgraded to 11.04.

Upon restart of my server ( its acting as a server even though its ubuntu desktop edition ) the screen for log in is just purple. 

This is exactly what happens when I start the server from a cold boot. 

BIOS displays
Blank screen
Blank purple screen
Flashes to black screen
Back again to purple, mouse appears and is moveable across the screen. The ubuntu double bongo sound happens. Screen remains purple. 

You can move the mouse to certain parts of the screen and the curser and it will change to the text editing curser. 

I have been able to get to login screen once on the third reboot if the machine. But upon restarting again its stuck at this stage. 

I can ssh to the server if you need me to tell you any information. Its important that I can get to the login screen and login as there is applications that start upon my account login. 

Also a have 3 tb of data located in zfs. So yeah. Um help me please

Thanks in advance,

Astro
Which just means you are runing server services on a desktop edition = understood.

1. Are you running 32bit or 64bit?
2. What is your hardware base, video hardware and monitor?
3. Have you read this sticky? (It may help)
 [http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

---

### Post by astroboy123 on 2011-05-02
> **MAFoElffen said:**
> Which just means you are runing server services on a desktop edition = understood.

1. Are you running 32bit or 64bit?
2. What is your hardware base, video hardware and monitor?
3. Have you read this sticky? (It may help)
 [http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

Thanks for the quick reply,

1. 64 bit
2.2500k CPU
Zotac h-67-mitx-WiFi motherboard. This the one that uses the sandybridge CPU as the gpu. Ie onboard gfx
Monitor: acer 2029 inch wide screen that is connected by dvi to vga from the back io plate to the monitor
3. I'll have a read of the sticky and reply back here shortly on whether it assisted.

Thanks

Astro

---

### Post by MAFoElffen on 2011-05-02
> **astroboy123 said:**
> 1. 64 bit
2. 2500k CPU, Zotac h-67-mitx-WiFi motherboard. This the one that uses the sandybridge CPU as the gpu. Ie onboard gfx. Monitor: acer 20 29 inch wide screen that is connected by dvi to vga from the back io plate to the monitor
3. I'll have a read of the sticky and reply back here shortly on whether it assisted.

Ew...

Been hearing things here and there with this GPU... Funny that support was only added for it recently:
> 
Ubuntu 11.04 Alpha 2 includes **X.org Server 1.10, Mesa 7.10 and X.Org 7.6**. This means that it now provides **support for Sandy Bridge graphics**, better **3D support for ATI AMD Radeon** hardware, support for more OpenGL extensions and better multi-head functionality.

But looking forward to getting you fixed up and productive soon...

---

### Post by astroboy123 on 2011-05-02
Hey again,

I had a look over the sticky and there is probably something i can do there.

<Ctrl><Alt><F1> to the terminal session and do the sudo service gdm start command.

But if im able to get a mouse on the screen and hear the sound of Ubuntu's gui wanting me to login. Doesn't that mean that I have the gdm service started. (thats assuming that gdm is the the login screen for Ubuntu's GUI)

My server worked fine in 10.10 graphically speaking.

I wont be able to do anything graphically for about 10 hours from now, as the server is at home and I am at work.

Is there anything diagnostic wise that I can do via command line via my ssh connection.

Thanks,

Lachlan

---

### Post by astroboy123 on 2011-05-03
Hi mate,

I tried <Ctrl><Alt><F1> and <F2> and wasn't able to access a cmd line.

I have restarted gdm. Stopped it and Started it via my SSH connection and all that comes into view is a black screen, the mouse and the ubuntu double bongo sound.

Ill try some reading over the sticky agian. But is there any ideas that can get the login screen again.

thanks in advance,

astro

---

### Post by astroboy123 on 2011-05-03
Hi Mate,

UPDATE:

I've gone into the grub menu pressed "e" and changed the line to the section that has the nosplash text. I did have a grub setting that was listed in the sticky guide (something like ro single)

> linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=32939def-1f4a-4134-9b56-bed2319a9216 ro  nosplash text

I added it and now the gdm (login window works) and i can login, but the login screen only opens every time i spam the left shift key upon boot.

any ideas?

thanks astro.

---

### Post by astroboy123 on 2011-05-05
Hi mate,

Just updating you on the status of this, I am still spamming the shift keys (left and the right one) and the system does boot correctly sometimes (when it doesn't boot it just does the purple screen thing).

Is there any log files that I can give you? that can tell you the difference between a successful start up and a non-successful?

Its weird because I can boot into the gdm correctly with the old kernel but as soon as a put in my password in, it will log in and a black screen with text will appear (super fast like I cant even make out what its saying)and then it will take me back to the login window again.

thanks astro.

EDIT:- the kernel version that works correctly (sometimes wit the shift key spaming) is 2.6.38-8-generic

---

### Post by nava69 on 2011-05-05
Hi
i installed 11.04 64bit but when im booting to ubuntu (choose 11.04 in boot loader) my screen start to flashing white and purple and i cant see any thing after that,also i tried 32bit but it had same problem
I have ATI HD6870
 
sory for my english

---

### Post by mysticBoer on 2011-05-06
> **astroboy123 said:**
> Hi mate,

I tried <Ctrl><Alt><F1> and <F2> and wasn't able to access a cmd line.

I have restarted gdm. Stopped it and Started it via my SSH connection and all that comes into view is a black screen, the mouse and the ubuntu double bongo sound.

Ill try some reading over the sticky agian. But is there any ideas that can get the login screen again.

thanks in advance,

astro

Been looking everywhere to see if somebody else has this problem as well. I can confirm I have EXACTLY the same issue..>

Hardware:
CPU - SandyBridge 2600k
RAM - 16Gb Kingston Value Ram
Mobo - DH67BL (Bearup Lake)

I'm thinking the H67 + Sandy Bridge processor combo is the issue here. When I do the <ctrl> + <alt> + <f1> I get a black screen, not terminal...

Anybody have some help here? 

I also installed 11.04 (I'm using the 64-Bit versions by the way) and had the same problem there...

---

### Post by nava69 on 2011-05-06
> **mysticBoer said:**
> Been looking everywhere to see if somebody else has this problem as well. I can confirm I have EXACTLY the same issue..>

Hardware:
CPU - SandyBridge 2600k
RAM - 16Gb Kingston Value Ram
Mobo - DH67BL (Bearup Lake)

I'm thinking the H67 + Sandy Bridge processor combo is the issue here. When I do the <ctrl> + <alt> + <f1> I get a black screen, not terminal...

Anybody have some help here? 

I also installed 11.04 (I'm using the 64-Bit versions by the way) and had the same problem there...

Same here,when <ctrl> + <alt> + <f1> i got just black screen,and befor it falashing between white and purple color

I tried both version 32bit and also 64

---

### Post by astroboy123 on 2011-05-08
> **mysticBoer said:**
> Been looking everywhere to see if somebody else has this problem as well. I can confirm I have EXACTLY the same issue..>

Hardware:
CPU - SandyBridge 2600k
RAM - 16Gb Kingston Value Ram
Mobo - DH67BL (Bearup Lake)

I'm thinking the H67 + Sandy Bridge processor combo is the issue here. When I do the <ctrl> + <alt> + <f1> I get a black screen, not terminal...

Anybody have some help here? 

I also installed 11.04 (I'm using the 64-Bit versions by the way) and had the same problem there...

Yeah, i get the same thing. the crtl+alt+f1 takes me to a blank screen aswell

---

### Post by MAFoElffen on 2011-05-08
> **mysticBoer said:**
> Been looking everywhere to see if somebody else has this problem as well. I can confirm I have EXACTLY the same issue..>

Hardware:
CPU - SandyBridge 2600k
RAM - 16Gb Kingston Value Ram
Mobo - DH67BL (Bearup Lake)

I'm thinking the H67 + Sandy Bridge processor combo is the issue here. When I do the <ctrl> + <alt> + <f1> I get a black screen, not terminal...

Anybody have some help here? 

I also installed 11.04 (I'm using the 64-Bit versions by the way) and had the same problem there...
On what I've looked into (various sandy bridge threads) seems so.  I do have an idea... I'm thinking that the devs are working on this bug anfd I know that there is a proposed kernel in the repo's that fuxes some of the graphics issues for some other people that I helped.  I'm thinking that since support for this chipset is recent, that some of those fix may be in there. 

Since you are booting "*sometimes*"... on a time you can boot the GUI, try this:
> (Quote from another of my posts)
Start the Synaptic Package Manager > Settings > Repositories >  Updates Tab > select the "Pre-released Updates (natty proposed)  checkbox and close that dialog box.

Select the "Reload" button. (Upper left, below menu's.)

Select filter "Origin" (lower left) > Select  "natty proposed maiin" (Left) > select package "linux-image-generic" (right)

Current kernel tonight is 2.6.38.8.22, proposed is 2.6.38.9.23.
It couldn't hurt to try this.

---

### Post by mysticBoer on 2011-05-11
@MAFoElffen

Will give it a go, thanks!

---

### Post by MAFoElffen on 2011-05-11
> **mysticBoer said:**
> Been looking everywhere to see if somebody else has this problem as well. I can confirm I have EXACTLY the same issue..>

Hardware:
CPU - SandyBridge 2600k
RAM - 16Gb Kingston Value Ram
Mobo - DH67BL (Bearup Lake)

I'm thinking the H67 + Sandy Bridge processor combo is the issue here. When I do the <ctrl> + <alt> + <f1> I get a black screen, not terminal...

Anybody have some help here? 

I also installed 11.04 (I'm using the 64-Bit versions by the way) and had the same problem there...
On those I've helped with the Sandy Bridge Chip, so far the only consistent thing that has worked for the majority of them is to add " nomodeset " in the kernel boot line.  Some have had to set the GFXMODE to a resolution that both their Video card supports and add " vga=xxx " where xxx= a decimal vesa mode their video card supports to the kernel boot line.  A Few have had to add "  noacpi " but adding this one adds other minor problems of it's own. 

I really think there has been challenges with supporting these chips and their drivers. 

IMHO- I feel everyone having problems with the Sandy Bridge chipset should get together to subscribe to a bug at LP.  Then maybe the problems with this chipset would get some support.  I'm trying to help, but I can't report a problem I'm not personally having.

---

### Post by mysticBoer on 2011-05-11
> **MAFoElffen said:**
> On those I've helped with the Sandy Bridge Chip, so far the only consistent thing that has work is to use " Nomodeset " in the kernel boot line.  some have had to also use "  noacpi ".  I really think there been a challenge with these chips and their drivers. 

IMHO- I feel evryone having problems with this chipset should subscribr to a bug at LP.  Then maybe the problems with this vhipset would get some support.  I'm trying to help, but I can't report a problem I'm not personally having.

Yes, if I use i915.modeset=1 (AFTER 'quiet' and 'splash')  it works fine for me as well (Fine being "I can boot into unity and use my box). I'll look to see if a bug is logged, and I'll then subscrube as well.

Thanks for your help!

---

### Post by MAFoElffen on 2011-05-11
> **mysticBoer said:**
> Yes, if I use i915.modeset=1 (AFTER 'quiet' and 'splash')  it works fine for me as well (Fine being "I can boot into unity and use my box). I'll look to see if a bug is logged, and I'll then subscrube as well.

Thanks for your help!
There is an open bug at LP just for for i915 chipsets... 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/683775:](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/683775:)

I thinks theres three majotr parts to it.  One of the issue with it is that folks with that chipset "_**cannot**_" use a "vga=xxx" modeset without going black screen. Another is that it cannot use any kind of frammefuffer other than it's own without going black screen,  I can't remember the third part to it...

You can use the GFXMODE=WIDTHxHEIGHTxDEPTH in /etc/default/grub to set your resolution and color depth.

Edit- One workaround on that LP Bug was to change /etc/default/grub/
```

GRUB_GFXPAYLOAD_LINUX=text                      

```

---

### Post by astroboy123 on 2011-05-11
> **MAFoElffen said:**
> On those I've helped with the Sandy Bridge Chip, so far the only consistent thing that has worked for the majority of them is to add " nomodeset " in the kernel boot line.  Some have had to set the GFXMODE to a resolution that both their Video card supports and add " vga=xxx " where xxx= a decimal vesa mode their video card supports to the kernel boot line.  A Few have had to add "  noacpi " but adding this one adds other minor problems of it's own. 

I really think there has been challenges with supporting these chips and their drivers. 

IMHO- I feel everyone having problems with the Sandy Bridge chipset should get together to subscribe to a bug at LP.  Then maybe the problems with this chipset would get some support.  I'm trying to help, but I can't report a problem I'm not personally having.

Hi Mate,

So in my command line in the grub loadered  i should see something like this..

> linux /vmlinuz-2.6.38.8-generic root=UUID=b5941e18-5b4a-403e-9a10-1526aa9e07f7 ro quiet splash vt.handoff=7linux nomodeset

Is that right?

or is it?

> linux /vmlinuz-2.6.38.8-generic root=UUID=b5941e18-5b4a-403e-9a10-1526aa9e07f7 ro nomodeset

---

