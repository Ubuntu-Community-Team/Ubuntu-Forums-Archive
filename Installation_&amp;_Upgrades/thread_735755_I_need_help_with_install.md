---
title: "I need help with install"
date: 2008-03-26
forum: Installation &amp; Upgrades
---

### Post by rkinman on 2008-03-26
AMD Turion 64 x2 TL - 52  1.6GHz
958 ram
NVIDA gforce go 6150

I'm noob here and I can't seem to figure out how to fix this.

I insert the CD in my laptop and boot.

After the loading the screen, there is a screen the displays different files that are loading with the [ok] on the right side.

After that I have nothing. Just a blank screen and the computer completely idle.

I select the first option for installing/running Ubuntu and should run off of live cd. 

Any Ideas why this his happening?

---

### Post by brownknight on 2008-03-26
hi rkinman

I am thinking of several ways you can try:

1. when you booth in live cd, click the option to check the cd for errors. it might take a while to finish but it is good to know if the cd has the problem. it maybe caused by burning the cd using max write speed so a lower write speed is better, or...

2. when you booth on the first screen, the boot menu on the cd, press F6 (extra options) you will be presented with some preloaded parameters. Append the pre-existing parameters by adding &#8220;noapic nolapic pci=noacpi acpi=off&#8221; at the end of the line (without the "")

good luck

---

### Post by rkinman on 2008-03-26
Let me give this a try. I will keep you informed.

---

### Post by rkinman on 2008-03-26
> **brownknight said:**
> hi rkinman

I am thinking of several ways you can try:

1. when you booth in live cd, click the option to check the cd for errors. it might take a while to finish but it is good to know if the cd has the problem. it maybe caused by burning the cd using max write speed so a lower write speed is better, or...

2. when you booth on the first screen, the boot menu on the cd, press F6 (extra options) you will be presented with some preloaded parameters. Append the pre-existing parameters by adding “noapic nolapic pci=noacpi acpi=off” at the end of the line (without the "")

good luck

The code seemed to work. I was able to get to the desktop. I did notice that during bootup it said my BIOS was causing problems when it was trying to do different things.

Also would I have problems if I did a full install after I append the parameters?

---

### Post by dstew on 2008-03-26
Another thing to try is Safe Graphics Mode, which I think is an option you get when you press F6.

---

### Post by dstew on 2008-03-26
> Also would I have problems if I did a full install after I append the parameters?After you install, you might have some problems with your graphics card, but those can be dealt with then. Just go ahead and install.

---

### Post by rkinman on 2008-03-26
> **dstew said:**
> Another thing to try is Safe Graphics Mode, which I think is an option you get when you press F6.

Safemode graphics = black screen as well.

---

### Post by dstew on 2008-03-26
That's ok, I posted before I saw your response that the kernel parameters worked. It seems it was either an acpi or apic issue. Anyway, go ahead and install. Usually, those issues are limited to the Live CD.

---

### Post by rkinman on 2008-03-27
I was able to get the live cd to boot with just acpi=off and also pnpbios=off

I did a full install and now I have this very annoying repeating sound that plays non stop. I have to hit the mute button on my laptop to make it stop. any ideas on this?

---

### Post by dstew on 2008-03-27
A new thread? I don't have a lot of experience with sound issues. Sorry.

---

