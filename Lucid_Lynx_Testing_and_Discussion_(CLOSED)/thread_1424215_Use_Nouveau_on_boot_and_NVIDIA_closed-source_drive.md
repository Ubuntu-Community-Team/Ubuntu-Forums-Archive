---
title: "Use Nouveau on boot and NVIDIA closed-source driver on DE"
date: 2010-03-07
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by zoff_ita on 2010-03-07
Is there any way to use Nouveau driver only on boot (to have plymouth working in graphical mode) and activate closed-source driver on DE loading?

Plymouth's graphical mode is not so important for me but if there is a way to get it keeping the 3D acceleration of closed driver would be nice...

Regards,
- zoff -

---

### Post by psyke83 on 2010-03-07
Not possible.

The nouveau driver needs its own DRM kernel modules loaded, which would interfere with the binary driver. Additionally, the binary driver uses a different libGL.so library which interferes with Mesa/open drivers.

---

### Post by gnomeuser on 2010-03-07
Option b) enable the xorg-edgers ppa and enjoy 3d acceleration using nouveau 

(might not work on all setups, beta code, might turn your butter into dinosaur droppings, alter your hamsters sexuality and other potentially undesirable sideeffects)

Per request on the PPA maintainers I am not linking to it, if you don't know how to find it you shouldn't use it.

---

### Post by zoff_ita on 2010-03-08
> **gnomeuser said:**
> Option b) enable the xorg-edgers ppa and enjoy 3d acceleration using nouveau 

(might not work on all setups, beta code, might turn your butter into dinosaur droppings, alter your hamsters sexuality and other potentially undesirable sideeffects)

Per request on the PPA maintainers I am not linking to it, if you don't know how to find it you shouldn't use it.

Already done...

But 3D acceleration isn't even comparable with propretary driver...

---

### Post by gnomeuser on 2010-03-08
> **zoff_ita said:**
> Already done...

But 3D acceleration isn't even comparable with propretary driver...

Should be sufficient and will be improved. For me Nouveau performs far sufficient to be comparable on the desktop, I don't play games  thus so long as Compiz runs I am good.

---

### Post by Ichtyandr on 2010-03-08
I am totally thrilled by this nouveau thing. I want to go ahead and install gallium with 3d support on lucid alpha (or daily as I update), is there a noobish howto with backup precautions that you are aware of?

---

### Post by zoff_ita on 2010-03-08
> **Ichtyandr said:**
> I am totally thrilled by this nouveau thing. I want to go ahead and install gallium with 3d support on lucid alpha (or daily as I update), is there a noobish howto with backup precautions that you are aware of?

Use xorg-edgers PPA: [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

---

### Post by Ichtyandr on 2010-03-08
> **zoff_ita said:**
> Use xorg-edgers PPA: [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

Did that, apparently works, I could enable desktop effects and alpha transparency in new murrine themes works now. This is an impressive piece of work! I figure there is there is no xorg.conf and generally no further configuration is necessary?

---

### Post by zoff_ita on 2010-03-08
> **Ichtyandr said:**
> Did that, apparently works, I could enable desktop effects and alpha transparency in new murrine themes works now. This is an impressive piece of work! I figure there is there is no xorg.conf and generally no further configuration is necessary?

/etc/X11/xorg.conf isn't indispensable but can improve performance...

You can generate one with "X -configure" when gdm isn't running...

---

### Post by habtool on 2010-03-08
I have the Nouveau 3D installed and working fine now, thanks for the info above.

The only major issue now is the fan speed is at full speed and hence very noisy, is there away to set the fan speed when using Nouveau?

If not, is it (fan speed control) something that the Nouveau devs are actively working on yet?

Thanks in advance for any further info

---

### Post by MacUntu on 2010-03-08
> **gnomeuser said:**
> Should be sufficient

Sufficient for what? Wobbly windows aren't the only reason to buy a dedicated graphics card. :KS

---

### Post by gnomeuser on 2010-03-08
> **MacUntu said:**
> Sufficient for what? Wobbly windows aren't the only reason to buy a dedicated graphics card. :KS

It plays Quake 3 and TA: Spring. Sufficient in the sense that doesn't crash and actually runs at a decent framerate. For 90% of all nvidia users on the desktop I would argue that nouveau is now sufficiently stable and performant to warrant not installing the dreaded blob (of recent GPU fan related death and destruction +3).

---

### Post by gnomeuser on 2010-03-08
> **Ichtyandr said:**
> I am totally thrilled by this nouveau thing. I want to go ahead and install gallium with 3d support on lucid alpha (or daily as I update), is there a noobish howto with backup precautions that you are aware of?

1) search for the xorg-edgers PPA and read the disclaimer.
2) learn to use ppa-purge (pretty simple and will become your best friend, it comes with the xorg-edgers ppa)
3) become familiar with recovering from a boot where X doesn't come up, it is rare but it might happen and it is nice to have a way out. I would recommend having a second machine from which to post urgent questions on such matters.
4) now enable the xorg-edgers ppa, update your system and reboot.

Also it is important to note that the ppa is not supported, any bugs you experience relating to X are likely to be affected by the upgrades and such be noted politely in any reports you file. 

For the most part, nouveau with gallium goodness is safe and stable but it is good to come prepared.

---

### Post by habtool on 2010-03-08
I tried to flash the nvidia 8600 card of mine to get the fan to slow down but that did not work. Google Earth did not work properly either, it only showed a portion of the globe image area. (I know G.E. is proprietary, but thought I would mentioned it in any-case)

So looking great but in some ways still needs a bit more time to mature for some users.

---

### Post by psyke83 on 2010-03-08
> **gnomeuser said:**
> It plays Quake 3 and TA: Spring. Sufficient in the sense that doesn't crash and actually runs at a decent framerate. For 90% of all nvidia users on the desktop I would argue that nouveau is now sufficiently stable and performant to warrant not installing the dreaded blob (of recent GPU fan related death and destruction +3).

I would just like to note that your benchmark for "sufficient" is personal and does not reflect the typical demographics of an NVIDIA card owner, especially one who is still using - or recently migrated from - Windows.

I think the nouveau project is fantastic (anything is better than the nv driver), and I would use it if my main Linux desktop still used an NVIDIA card. However, let me suggest that evangelizing open source too aggressively (and to potentially disinterested parties) can have a detrimental effect.

Speaking of the "dreaded" blob: would you find my argument against Linux compelling if I were to cite the case in which a certain kernel version would irreparably brick a piece of hardware, such as when the e1000e kernel module overwrote EEPROM of certain ethernet controllers? Of course not. The recently NVIDIA issue is a rare occurrence, the offending driver was pulled almost immediately, and NVIDIA issued a warning to users.

---

### Post by Ichtyandr on 2010-03-08
> **gnomeuser said:**
> 1) search for the xorg-edgers PPA and read the disclaimer.
2) learn to use ppa-purge (pretty simple and will become your best friend, it comes with the xorg-edgers ppa)
3) become familiar with recovering from a boot where X doesn't come up, it is rare but it might happen and it is nice to have a way out. I would recommend having a second machine from which to post urgent questions on such matters.
4) now enable the xorg-edgers ppa, update your system and reboot.

Also it is important to note that the ppa is not supported, any bugs you experience relating to X are likely to be affected by the upgrades and such be noted politely in any reports you file. 

For the most part, nouveau with gallium goodness is safe and stable but it is good to come prepared.

Thanks a lot for your time, all noted!

I had problem with the latest update to -16 kernel version and reverted back to -15. I can do most of the things that you pointed, but number "3" is unfamiliar, I could not use ppa-purge because it would not even switch to other consoles with Ctr-Alt-F1. instead I booted back to -15 from grub menu. I guess I was relatively lucky. Really no idea what to do if such lockups happen, but I guess that belongs in the general help forum.
Nouveau performance is noticeably better than with the proprietary driver. I hope its not long till it gets to universe.

---

### Post by Ichtyandr on 2010-03-08
> **habtool said:**
> I have the Nouveau 3D installed and working fine now, thanks for the info above.

The only major issue now is the fan speed is at full speed and hence very noisy, is there away to set the fan speed when using Nouveau?

If not, is it (fan speed control) something that the Nouveau devs are actively working on yet?

Thanks in advance for any further info

Could it be the case that with proprietary driver the temperature is higher (according to Xsensor my CPU temperature was 51C, and now 23C), but the fan speed was lower?

---

### Post by psyke83 on 2010-03-08
> **Ichtyandr said:**
> Could it be the case that with proprietary driver the temperature is higher (according to Xsensor my CPU temperature was 51C, and now 23C), but the fan speed was lower?

Yes, that's quite possible. Don't compare your experience to the buggy binary driver - wait until a safe driver upgrade (or downgrade) is released.

Maybe you can try an older driver revision (I think the package is nvidia-173?), if your card supports it.

---

### Post by Ichtyandr on 2010-03-08
> **psyke83 said:**
> Yes, that's quite possible. Don't compare your experience to the buggy binary driver - wait until a safe driver upgrade (or downgrade) is released.

Maybe you can try an older driver revision (I think the package is nvidia-173?), if your card supports it.

I did that, by now I can compare nouveau/3d with both nvidia-current and 173 drivers on lucid, and its both cooler in temperature and uses less fan rpm than with any proprietary driver according to Xsensors on my desktop (GeForce 8400 GS).

---

### Post by gnomeuser on 2010-03-08
> **Ichtyandr said:**
> Thanks a lot for your time, all noted!

I had problem with the latest update to -16 kernel version and reverted back to -15. I can do most of the things that you pointed, but number "3" is unfamiliar, I could not use ppa-purge because it would not even switch to other consoles with Ctr-Alt-F1. instead I booted back to -15 from grub menu. I guess I was relatively lucky. Really no idea what to do if such lockups happen, but I guess that belongs in the general help forum.
Nouveau performance is noticeably better than with the proprietary driver. I hope its not long till it gets to universe.

Yeah bad timing, they just moved the nouveau module. 

Here is what I did (and please do take the time to understand each step, mindlessly copy pasty commands leads to no good):

Boot a livecd, connect to your network and open up a terminal.

sudo mount /dev/sda1 /mnt
sudo cp /etc/resolv.conf /mnt/etc/resolv.conf
cd /mnt
sudo mount -o bind /dev dev
sudo mount -o bind /dev/pts dev/pts
sudo mount -o bind /proc proc
sudo mount -o bind /sys sys
chroot .

ppa-purge xorg-edgers

exit

reboot

voila.

---

### Post by gnomeuser on 2010-03-08
> **psyke83 said:**
> I would just like to note that your benchmark for "sufficient" is personal and does not reflect the typical demographics of an NVIDIA card owner, especially one who is still using - or recently migrated from - Windows.


So is yours, next.

> 
I think the nouveau project is fantastic (anything is better than the nv driver), and I would use it if my main Linux desktop still used an NVIDIA card. However, let me suggest that evangelizing open source too aggressively (and to potentially disinterested parties) can have a detrimental effect.


What is this crap about evangelizing? The point I was making was that come Lucid+1, this is very likely to work out of the box and only special needs (such as VDPAU, being probably the largest one) would need to install the nvidia driver. By the metrics collected observing average people, it should do sufficiently well to be acceptable. People can have it today at a risk, which I am careful to point out as you will no doubt have noticed. I follow every guideline regarding the use of the xorg-edgers ppa including not linking to it or posting exact directions PRECISELY because people should understand the dangers and the added work they might present Ubuntu with in using this.

> 
Speaking of the "dreaded" blob: would you find my argument against Linux compelling if I were to cite the case in which a certain kernel version would irreparably brick a piece of hardware, such as when the e1000e kernel module overwrote EEPROM of certain ethernet controllers? Of course not. The recently NVIDIA issue is a rare occurrence, the offending driver was pulled almost immediately, and NVIDIA issued a warning to users.

Actually I would, software being able to brick hardware sufficiently to require returning it to the vendor is a sign that we are both not good enough and doing something wrong.

---

### Post by psyke83 on 2010-03-08
> **gnomeuser said:**
> So is yours, next.

Yes, because my desktop is an old Pentium 4 with no AGP or PCIe ports, and a GeForce 6200 PCI card, which does not lend itself well to serious gaming.

Most users from a Windows background that have purchased a dedicated card (that's not prefixed with the Quadro label) did so because they needed to satisfy the requirements (Shader Model X, Vertex Shader Model Y) written on the back of some game's case.

Argument: commercial games are rare on the Linux platform nowadays, so high-performance drivers are unnecessary. Q3A, for example, was released in 1999 {and the open source Spring engine, since you mentioned it, has relatively low GPU requirements}.
Counter-argument: [WINE]("http://appdb.winehq.org/").

> What is this crap about evangelizing? The point I was making was that come Lucid+1, this is very likely to work out of the box and only special needs (such as VDPAU, being probably the largest one) would need to install the nvidia driver. By the metrics collected observing average people, it should do sufficiently well to be acceptable. People can have it today at a risk, which I am careful to point out as you will no doubt have noticed. I follow every guideline regarding the use of the xorg-edgers ppa including not linking to it or posting exact directions PRECISELY because people should understand the dangers and the added work they might present Ubuntu with in using this.

I apologise if you took offense. I said this because you appeared to be refuting another person's assessment of what constitutes "sufficient" performance of a dedicated card. That, and also your curiously worded - but related - "nouveau doubters" thread.

> Actually I would, software being able to brick hardware sufficiently to require returning it to the vendor is a sign that we are both not good enough and doing something wrong.

Agreed.

---

### Post by autocrosser on 2010-03-08
A question---Is Nouveau supporting SLI setups? I'm running a dual 9800GT set & use the nvidia-blob because the old NV driver would b0rk all over the place with them (have to un-install one card to install the OS & then reinstall after the blob is ready to run)...

I'm betting that you'll say "mostly no"--would be interesting to try it---the most taxing thing I do is UT 2004 & as it's 6 years old the requirements are not too high.....

---

### Post by psyke83 on 2010-03-08
> **autocrosser said:**
> A question---Is Nouveau supporting SLI setups? I'm running a dual 9800GT set & use the nvidia-blob because the old NV driver would b0rk all over the place with them (have to un-install one card to install the OS & then reinstall after the blob is ready to run)...

I'm betting that you'll say "mostly no"--would be interesting to try it---the most taxing thing I do is UT 2004 & as it's 6 years old the requirements are not too high.....

Not yet, since none of the developers own a SLI setup.

[https://bugs.freedesktop.org/show_bug.cgi?id=16897](https://bugs.freedesktop.org/show_bug.cgi?id=16897)

---

