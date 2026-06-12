---
title: "should I upgrade from 12.04 to 14.04.1 LTS?"
date: 2014-08-18
forum: Installation &amp; Upgrades
---

### Post by shahin on 2014-08-18
I have a vm of Ubuntu 12.04 64-bit LTS (running on VMware Workstation) that I used to create a build environment for Android Open Source Project. I am running this on an HP machine with NVIDIA graphic card, and the host operating system is Windows 7. When I check for updates in the update manager window, I see two messages. One says "New Ubuntu release '14.04.1 LTS' is available. But when I tried to do it, I got a pop up message stating: " Your graphics hardware may not be fully supported in Ubuntu 14.04." "Running the 'unity' desktop environment is not fully supported by your graphics hardware. You will maybe end up in a very slow environment after the upgrade. Our advice is to keep the LTS version for now. For more information see [http://wiki.ubuntu.com/X/Bugs/UpdateManagerWarningForUnity3D](http://wiki.ubuntu.com/X/Bugs/UpdateManagerWarningForUnity3D) Do you still want to continue with the upgrade?"
So I say no to the above. The url above states that I can change to ubuntu-classic with no effects. Does it mean that I wont get the alert or would I still see it? I purchased my laptop in 2008, and don't think it is old. The url says that old CPUs and Graphics hardware may have an issue. Can anyone clarify if my laptop is considered old? 

The other message in Update Manager says that "New hardware support is available". My question is: Is this the hardware manager for unity? Should I install this, and then do the upgrade? How can I find out more about this hardware manager please? 

Also is there a software or utility I can use to save a stable image version I can role back to? Kinda like the last known good config or Windows?

---

### Post by sports fan Matt on 2014-08-18
I have the same message.  I think it might be but not sure.  I need to investigate as well.

---

### Post by kansasnoob on 2014-08-18
> The other message in Update Manager says that "New hardware support is available".

[https://wiki.ubuntu.com/1204_HWE_EOL](https://wiki.ubuntu.com/1204_HWE_EOL)

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

So the full release upgrade takes you to [Trusty (14.04.1)]("https://wiki.ubuntu.com/TrustyTahr/ReleaseNotes").

The HWE upgrade upgrades only the kernel and X-stack to the Trusty versions.

Both have proven to be problematic for some users but if you're running Precise (12.04) with the Quantal, Raring, or Saucy HWE you're no longer going to receive kernel updates which are quite often security related updates. 

IMHO if you're being offered both I'd look into the full release upgrade to 14.04.1 simply because it's supported the longest (until April 2019). But maybe it won't work well with either your hardware or your VM.

Whichever you choose I'd suggest preparing for the worst, which means creating a full backup of anything important, and having installation media on hand in case things go wrong and reinstallation is required. If you find that 14.04.1 won't work you may want to consider using [the archived 12.04.1 installation media]("http://old-releases.ubuntu.com/releases/precise/") which uses the original Precise kernel and X-stack since it's supported until April 2017. **[COLOR="#FF0000"]You must avoid using the 12.04.2, 12.04.3, and 12.04.4 installation media to prevent landing in HWE EOL![/COLOR]** And the 12.04.5 media uses the Trusty HWE!

Those faced with reinstallation should also be acutely aware of this installer bug:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

I'm just full of good news ain't I :redface:

---

### Post by shahin on 2014-08-19
Thanks

---

