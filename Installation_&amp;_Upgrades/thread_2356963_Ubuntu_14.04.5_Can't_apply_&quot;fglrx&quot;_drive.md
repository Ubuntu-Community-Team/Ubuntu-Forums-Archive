---
title: "Ubuntu 14.04.5 Can't apply &quot;fglrx&quot; driver"
date: 2017-03-28
forum: Installation &amp; Upgrades
---

### Post by kiicki on 2017-03-28
I just did a fresh install of Ubuntu 14.04.5 and updated everything using the command "sudo apt update && sudo apt upgrade" and when they asked me to upgrade to 16.04, I declined.

In additional drivers I can see the Open source one, fglrx-updates and fglrx, drivers.

From my understanding is that they dropped the support in 16.04 but I'm on 14.04.5 and when I select "fglrx" it doesn't do anything. No warning, no errors. After I select the driver and hit "apply" it just throws me back to the Open source one.

Is it now also impossible to use the "fglrx" at all?

GPU: AMD HD 5450

---

### Post by deadflowr on 2017-03-28
You can run fglrx on 14.04, but to do so you need to install the older 14.04.1 version.
Grab it from here: [http://old-releases.ubuntu.com/releases/14.04.1/]("http://old-releases.ubuntu.com/releases/14.04.1/")
This will give you the Xserver and kernel which still support the fglrx driver.

You can update the system like normal, as long as you do not try install the lts-hardware stack packages.
See:[https://wiki.ubuntu.com/Kernel/LTSEnablementStack]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack")

---

### Post by kiicki on 2017-03-28
Thank you. So what I can do is to clean install with 14.04.1, update everything with "sudo apt update && sudo apt upgrade" decline if they ask to upgrade to 16.04 and then apply fgrlx?

Or should I clean install, apply fglrx and then update everything but of course decline the offer for 16.04?

---

### Post by deadflowr on 2017-03-28
Running the updates first usually works better.
In my experience.
Just from the fact that at least you know all the required packages provided by Ubuntu are up-to-date.

---

### Post by kiicki on 2017-03-28
Will give it a try. ISO is done and will install now. I just hope that I don't install something during the update that I shouldn't. All I know what to avoid is if it's asking me to upgrade to 16.4 or something

---

### Post by QIII on 2017-03-28
Hello!

14.04.5 has the same graphics stack as 16.04, so no fglrx.

You would have to install and  stick to 14.04.1 and do your updates *without allowing* the HWE.

But ...

Depending on your GPU model, the AMDGPU or AMDGPU-PRO driver may work.  When you say "throws me back to the Open source one" do you mean Radeon or AMDGPU?  Both of those are open source.  AMDGPU is used if a supported GPU is present.

---

### Post by deadflowr on 2017-03-28
^indeed, it should not install the updated stacks. 
You can double check yourself after running the system updates by looking at both the current kernel and X stack with
```
uname -a 
Xorg -version
```
the kernel you want is 3.13.XXX and the Xorg version should be 1.15 (currently 1.15.1 on 14.04)

Fwiw though, that driver is getting rather long in the tooth.
I'm not even sure amd even applies security updates for it anymore.
so caveat emptor.

---

### Post by kiicki on 2017-03-28
Honestly, right now  I cannot remember what the Open source one said. I do have a AMD HD 5450 GPU. So like when I open "additional driver" it's default on Open source. I select "fglrx" and hit "apply changes" and then it does something for a quick second and it's back on the Open source one (Which I cannot remember what was called tbh)

But how do I avoid the updates from upgrading my 14.04.1 to 14.04.5 for example? I see that on the AMD sites (Not even sure when they updated it last) but it says that Ubuntu 14.04.2 should work. They have supported drivers for it. Problem is that I see like 8 drivers there and I have no idea what to pick or even how to install it. I have been avoiding that and hoping that the drivers in the "additional drivers" would just work.

Actually here's the drivers for this GPU if I install it from there: [http://support.amd.com/en-us/download/desktop/previous/detail?os=Ubuntu%20x86%2064&rev=15.9](http://support.amd.com/en-us/download/desktop/previous/detail?os=Ubuntu%20x86%2064&rev=15.9)

It says "Ubuntu [COLOR=#000000][FONT=Calibri]14.04.2" but who knows when that was last updated or if this is actually the latest version that works with it.[/FONT][/COLOR]

---

### Post by kiicki on 2017-03-28
Security is not a high priority with this system. Probably not at all. I will be using it as a media server and for Kodi only. Just movies. No personal documents and such. I just need it to get working as it works good on Windows 10 actually but the problem with Windows is that Kodi Windows version has a lot of problems with graphics card. Kodi will crash 9/10 times on startup with this GPU where it will crash sometimes during. The same thing is with my GTX 560M on another system where Kodi Windows won't even launch where the integrated graphics (intel HD 3000) works flawlessly.

Too bad that the system I need to get this working on only has the AMD HD 5450.

So like the options are
1: Get graphics to work on Linux
2: Live with Kodi crashing on windows which is not ideal as this will only be used with a Kodi remote for navigating and even turning off/on the PC. So if something crashes and what not, I have no mouse or keyboard to control it. Not too mention it's also annoying.

---

### Post by QIII on 2017-03-28
You can update without worry.  You actually have to [deliberately upgrade the HWE]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack").  I guess I didn't make that clear.

In terms of the graphics stack, 14.04.2, .3 and .4 are receiving no further updates.  They are still getting normal updates.  But I would steer clear of 14.04.2 for that reason and keep to 14.04.1.

So, you probably would do well with 14.04.1, don't add the HWE and use fglrx.  You will get 2 further years of use out of 14.04.1, but you will have to figure something else out by then.

---

### Post by ajgreeny on 2017-03-28
Just bear in mind that if you run the **lsb_release -a** command to show what version of Ubuntu you have installed it will still tell you that you are running 14.04.5 once it is fully updated, even though you have not upgraded the hardware stack.  It is just one of those weird inconsistencies of OS reporting by that command

Don't be alarmed by that as you will still have the older 3.13 series kernel and xorg-1.15 so fglrx should be OK for you.

---

### Post by kiicki on 2017-03-28
So everything seems to work as good as it can I guess. I installed 14.04.1 and updated everything using command "sudo apt update && sudo apt upgrade" and then rebooted.
I then checked my Kernel and Xorg version which is:

Kernel: 3.13.0-113-Generic
Xorg: 1.15.1

Which is what you said it should be. I applied the driver "fgrlx-updates" and it actually applied without any errors, and even though it didn't ask for a reboot, I did it. AMD Catalyst does also open which has been an issue in some other distro/version. I can't remember anymore. I have tried everything. Without V-sync being enabled, I don't get any screen tears on Youtube which was something that happened before.

I still don't have any errors so I guess everything is working. It's not working as great as it does on Windows 10 but this is good enough I guess. It's a little laggy/stuttery but this is also a bad GPU, but I'm almost positive that I didn't get the same performance in Windows 10. I think it was better there tbh.

Non the less, reason I went with Linux instead of windows 10 with this setup was because Kodi on Windows had issues with this GPU where on the Kodi Linux version it's stable.
Now at least nothing is crashing, I can run it as a media server, I can share my folders with "Samba" and I can watch movies on Kodi (still kinda stuttery but good enough. I might just get another cheap GPU for it that is fully supported with Linux)

So thank you. I have no idea if I'm still on 14.04.1 or 14.04.5 or whatever but things are working. I'm not sure how to notify the other user that was also helpful so I'm gonna leave him a quick reply so he also can read this. Thanks again!

---

### Post by kiicki on 2017-03-28
Thanks, everything seems to be working fine. I left a longer message earlier as I have no idea how to tag users.

---

### Post by Tadaen_Sylvermane on 2017-03-28
I'm curious as to the rest of your hardware. That video card should steamroll general media usage. Open source driver should own it just fine.

---

### Post by kiicki on 2017-03-28
Yes, been trying the Open source one with various Ubuntu flavors and different version. Same with Mint. It's stuttery (It's kinda now too but not as bad I think) and sometimes depending on what version I was using I would get screen tear with Open source one. I just don't think it can be better as it's generic. It should be better to use drivers that was specifically made for this card. I don't understand why it would be worse at least.

Ooh yeah, and I think that I would get error message sometimes at least using Ubuntu with Open source. It randomly pop up

---

