---
title: "Horizontal line display glitches after installing updates on fresh Lubuntu 18.04.4"
date: 2020-08-13
forum: Installation &amp; Upgrades
---

### Post by ashton001 on 2020-08-13
This is my first time installing Linux, so apologies for my ignorance in advance.

After installing a fresh copy of Lubuntu or Xubuntu it seems to work fine up until I install updates then 64 columns of randomly placed horizontal lines (1 to a few pixels in with) appear after restart.
I tried reinstalling Lubuntu then only installing all updates except drivers, but the problem still appears, so I still have no idea which of the hundreds of updates is the problem.
Is anyone familiar with this type of problem and how to best fix it?

The computer is a IBM ThinkPad T42
OS = Lubuntu 18.04.4-desktop-i386 or Xubuntu 18.04.4-desktop-i386
forcepae boot option is applied

[ATTACH=CONFIG]286699[/ATTACH]

Thanks,
Ashton

---

### Post by guiverc on 2020-08-14
One of the machines used to test Lubuntu is a IBM Thinkpad t43 (pentium m, 1.5gb ram, radeon x300), and at least on that machine *forcepae* is not required. I've never had any issues on that machine (and as I use it semi-regularly I would for sure notice it).

I do have an older r50p that I sometimes use for testing (it does require forcepae as it's an older pentium m) but I haven't used it for some time (I'm lazy, as it's always running I tend not to reboot it and use other laptops). I can't recall when I last tested on the r50p, but I know it wasn't in the recent 18.04.5 series so I went and had a play...

I booted the Lubuntu 18.04.5 LTS ISO on my r50p (using `forcepae --forcepae` the box requires) and yep... the image is *somewhat* as you describe & picture.  I don't believe I saw this in the 18.04.4 testing (I'm convinced I used the r50p for some tests that cycle), but that DOES fit with your description (*fine with install, but after upgrades... issues; testing cycles end on the release*).

I'll do some more testing, likely file a bug... but I suspect the fix will be to return to using the GA kernel (instead of the HWE stack; ga = general; hwe = hardware enablement better for later devices... my installed OS on the r50p is running the older stack so I'd never noticed issues..)

I'll refer you to 

[https://discourse.lubuntu.me/t/reviving-thinkpad-x31-problems-with-messed-up-screen/1457/6]("https://discourse.lubuntu.me/t/reviving-thinkpad-x31-problems-with-messed-up-screen/1457/6?u=guiverc")

where I give a little information and suggest

```
sudo apt install linux-image-generic xserver-xorg
```

which can be done at terminal (I used CTRL+ALT+F4 and terminal was fine on my r50p).. I can't test the command I offer currently on my current system as it's running *live* and thus cannot reboot, but I believe/expect that will fix the issue.  Boot with the 4.15 kernels.. the linked post may provide more details, or if you're unsure - please just ask and I'll return..

I've linked this post to the Lubuntu discourse (aforementioned post), I may even test Xubuntu 18.04.5 as I have it around somewhere here, but I'm 100% sure it'll be identical too; as it's the HWE stack I'm convinced which is identical for all flavors.

I'll do some testing when I can.

---

### Post by ashton001 on 2020-08-14
Thanks for the reply.
It will not install without forcepae -- forcepae on my T42, also the T42 uses an older mobility radeon 7500.  I tried just installing updates other then kernel related ones and it still produced the same problems, but I am not familiar with Linux so maybe I missed something.
I have since reinstalled xubuntu again rather then lubuntu, is it best just to install all the updates and then run that command, or should I avoid installing certain updates this time?

I will do some reading and check out that other thread in the mean time.
Thanks again.

---

### Post by guiverc on 2020-08-15
That command will install the GA kernel (Ubuntu 18.04's original 4.15 kernel; updated of course) plus the graphics stack (xserver-org) for that stack.  It does **not** remove the older stack, so when you boot you can use the newer 5.4 HWE kernel, or select the older 4.15 kernel I believe will be flawless (what I run on my t43 anyway, and works on my R50p).  I provided the link to the Lubuntu discourse as I provided the command there to remove HWE kernel (which I'd not do quickly, I would just use the GA/4.15 kernel and now and again try the newer HWE to see if it's fixed.. if over time it's not then you can remove it.  I've seen newer machines using 5.4 report like issues too)

If you don't want to use commands like I provided, you can always install using either the Lubuntu 18.04 LTS or 18.04.1 LTS ISO, and the GA kernel will be used by default (this applies to Xubuntu, or any other Ubuntu *flavor* equally). HWE kernels are only used (and default) on installs made with 18.04.2 or later media/ISO.  My belief is using the GA kernel will avoid this issue (it resolve it in my testing on r50p).

---

### Post by guiverc on 2020-08-16
My filed bug can be found at [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1891790](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1891790)
(I'm still trying to run `apport-collect`, since I was unable to file on an impacted box using `ubuntu-bug`)

---

### Post by ashton001 on 2020-08-20
So I was messing around some recently, and I find that 5.3.0-28-generic works fine whereas 5.4.0-42-generic does not.  Is there any reason to downgrade to 4.15?  I was not able to run the command you gave me because it was complaining about dependencies and my efforts to solve that just led to more problems and consequently deciding to reinstall, this time with lubuntu.

Do you want me to switch to the 5.4 kernel and run "apport-collect"?  I'm not familiar with it, but I assume it collects relevant info for bug fixing.

---

### Post by guiverc on 2020-08-21
The reason to use 4.15 is  4.15 is supported, and has security fixes backported to it, where as the 5.3 kernel (from 19.10) is unsupported & thus doesn't have security fixes back-ported to it.  If security matters to you, I'd for sure recommend the supported 4.15 kernel.

If you want an installation to start with the 4.15 kernel, use the 18.04 or 18.04.1 ISOs. Being older ISOs you'll have more upgrades to install during or post-install, but you'll be on 4.15 kernel & remain on it (ie. HWE is disabled by default with those ISOs, enabled for all subsequent ISOs).

To help with the command I gave I'd need to see errors you received to understand the issues. (as I recall I just tested the command on my thinkpad t43 which responded the packages were already installed which was expected - it already uses the GA kernel stack).

 I just booted a 18.04.5 iso on a box & entered the command.. :(  Yeah I get some errors (conflicts between xorg-core & xorg-hwe-core..  If you want me to look at it, let me know as I'll likely have some 18.04.5 QA-test installs I can play with.. (one got blown away yesterday being replaced by a *groovy* install.. but for now I still have some)

Thank you for offering to run `apport-collect`, but it won't let you as I filed the bug, it'll require me to login. Yes you are correct, it collects details about system, when installed, packages & versions installed, etc on the box it's run on and uploads to launchpad. You can if you'd like, file your own bug & then the bugs get linked (*one marked a duplicate of the other*), or by far the easiest is to login & say "*affects me too*" & leave a comment providing some details (ie. *how it impacts you*). 

FYI: A duplicate bug report is not a negative thing, in fact it's very powerful as it gives developers far more useful information to track the issue & come up with cause, and eventual fix. In the bug tracking world, duplicates add heat which gets bugs noticed.

I personally don't think that bug will get much traction. In my testing I had no issues with the GA (4.15) kernels, so I'll just suggest that for Lubuntu users.  If it gets worked on/fixed, it'll only be because the same issue  also impacts other more modern hardware I suspect (*I've seen other modern boxes with the same artifacts/glitches when using 5.4 kernel, but that doesn't mean it's the same cause/same bug; also  it was only on support sites rather than bug tracking sites like launchpad*.  *If interested, the fact that it didn't also impact my thinkpad t43 makes me think the issue on our older systems have differs to more modern systems*).

---

### Post by ashton001 on 2020-08-21
Ah ok, I will just reinstall using the 18.04.1 iso this time then, I see now that it is supported for another 3 years.  Maybe I will report the bug and apport-collect too if I am able to with the screen all messed up.

Thanks for the help!

---

### Post by guiverc on 2020-08-21
FYI:  You can file the bug using `ubuntu-bug linux` (*which will file it on the kernel, which is what I did*) and `apport-collect` won't be required, as `ubuntu-bug` will upload all details when run.

I was unable to get `ubuntu-bug` to work, so eventually resorted to filing my bug online using firefox; which is why the bot pinged me asking for `apport-collect`to be run.

---

