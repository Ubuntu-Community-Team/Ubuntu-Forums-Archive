---
title: "installation problems, black screen"
date: 2008-02-29
forum: Installation &amp; Upgrades
---

### Post by awhansen01 on 2008-02-29
Hey, I'm installing a copy of 7.10 on my desktop, and I tried to start Ubuntu off the CD in safe graphics mode and the kernel(I believe) starts to load, once the orange bar finishes, the monitor shuts off and I can't get it to respond at all. I know the CD is fine because I tried installing it on Vista via Virtual PC and it worked fine. I have Vista installed and I had previously left 20gb of unallocated space to put Linux on, the rest is with Vista.
I am running:
Intel Core 2 Duo, 1.8GHz
MSI P965 Platinum
ATI X1600 Pro
2 GB Ram
and a 250gb Seagate Barracuda drive.

Any help would be appreciated, thanks.

---

### Post by Pumalite on 2008-02-29
Use the ALternate CD:
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
Mark the box below sign 'Start Download'

---

### Post by awhansen01 on 2008-02-29
well, that worked partially. it installed well, but when i try to boot up ubuntu, i still get the same black screen (i.e. monitor sleeping), but i heard it start up, and i entered my name and password, and heard it startup, but i just cant see anything, is there something i could add to the kernel when booting up that might fix it?

---

### Post by Pumalite on 2008-02-29
Try:
Ctrl+Alt+F1 to get command line
username
password
sudo dpkg-reconfigure xserver-xorg
Accept most defaults, choose vesa as the driver or 'ati'
Then: startx

---

### Post by Lord Graviton on 2008-02-29
> **Pumalite said:**
> Try:
Ctrl+Alt+F1 to get command line
username
password
sudo dpkg-reconfigure xserver-xorg
Accept most defaults, choose vesa as the driver or 'ati'
Then: startx

I've encountered the same problem as awhansen01 where Xorg fails to launch because it doesn't recognize my ATI Radeon X800 video card, but when I tried your solution to run the reconfigure dialog, it (the reconfigure dialog) locks up. :/
Do you think that there might be a workaround for configuring it or is there fix for my problem?

Oh, also.  Not sure if this is an important detail or not, but as Ubuntu was booting up, I had to first Ctrl+Alt+Del and then Ctrl+Alt+F1 in order to access the command line.  Simply trying to Ctrl+Alt+F1 would not yield any response, which ultimately tried to load Xorg, then the screen blanks out and becomes unresponsive.

Thanks.

---

### Post by Pumalite on 2008-02-29
Maybe you should review your defaults. i.e. 'nobuffers'' and stick to 'vesa'

---

### Post by Lord Graviton on 2008-02-29
I believe that the config dialog pops up and locks up immediately.  I can't even begin the reconfigure procedure.  So are those params you mentioned from that procedure?

---

### Post by Pumalite on 2008-02-29
Post you specs and tell me what iso are you using.

---

### Post by Lord Graviton on 2008-02-29
I am running on:
AMD Athlon 64 Dual Core Processor 3800+
1GB of RAM
ATi Radeon X800 GTO

And I am using the ubuntu-7.10-alternate-amd64.iso

---

### Post by Pumalite on 2008-02-29
You should be OK. Burn a new CD. Do md5sum on iso, burn at 4x or less, check for CD integrity before install.

---

### Post by Lord Graviton on 2008-02-29
Gotcha, I'll try that and let you know if it works.

---

### Post by srg86 on 2008-04-11
> **Lord Graviton said:**
> I am running on:
AMD Athlon 64 Dual Core Processor 3800+
1GB of RAM
ATi Radeon X800 GTO

And I am using the ubuntu-7.10-alternate-amd64.iso

Hi I am having a very similar problem. My system:

AMD Athlon 64 Dual Core Processor 4200+
1GB of RAM
ATi Radeon X800 GTO 128MB DDR
nForce4 chipset
M-Audio Delta Audiophile 2496 sound card.

I've just tried the 64-bit Hardy Heron beta and it does exactly this. The trouble for me is that if HH final does this, this will be the fourth version of Ubunut 64-bit that does this, I think the last version I was able to run was Dapper Drake. I get no troubles with the 32-bit version, but the 64-bit version is a no go for me, at least with this graphics card (I don't have another PCI-E card to test).

---

### Post by Pumalite on 2008-04-11
It could be that your processor is an 'emulator' of 64 bit.

---

### Post by srg86 on 2008-04-11
> **Pumalite said:**
> It could be that your processor is an 'emulator' of 64 bit.

An 'emulator'? This processor supports the full x86_64 execution enviroment, all Athlon 64s and X2s do. The only thing this CPU doesn't support is AMD's Pacifica virtualisation stuff.

---

### Post by srg86 on 2008-04-11
FIXED!

I really should have done this a long time ago, don't know why I didn't! I turned off boot splash!

Anyway for some reason, and this is carrying over from multiple versions of ubuntu 64-bit, it seems that the boot splash doesn't like the X800GTO and maybe some other ATI graphics cards.

---

