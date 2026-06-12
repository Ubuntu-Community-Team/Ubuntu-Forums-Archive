---
title: "new mobo"
date: 2009-12-30
forum: Installation &amp; Upgrades
---

### Post by teepee on 2009-12-30
hello, anyone know if i need to reinstall os ubuntu after replacing mobo, cpu, and ram but keeping hard drive. I did this last night and a few minor changes to reflect the new graphics but it still doesn't look great.

---

### Post by djheadley on 2009-12-30
I did this once, actually just took the hds from one computer and put them in another computer.  The video was NOT on the mobo so I had to transfer that too.  I didn't have any problems.  I  assume that your video is on the mobo?

---

### Post by teepee on 2009-12-30
ya -- both old mobo and new. both cpus are amd so i think although the new one is a four core vs a single i'm still ok
But my moitor doesn't look good in video playback and even some other things -- itss not really bad though

---

### Post by falconindy on 2009-12-30
Drivers are always loaded based on hardware detection on bootup. That means that you could move a hard drive from a 486 to a Core i7 and there (in theory) shouldn't be any problems, nor should there be much in the way of "residuals" left around as there would with Windows.

That said, video can cause some issues if you used an extra driver (such as an nvidia package) and didn't uninstall it before moving  the drive.

---

### Post by kevinatkins on 2009-12-30
Hi,

You shouldn't need to reinstall but your problems appear to be graphics / video related and might be solved by reconfiguration of the graphics setup.

To do this, you'll need to reboot into recovery mode. This can be accomplished by restarting the computer - you may need to press 'Esc' so that the Grub list of boot options is displayed. Then choose 'Recovery Mode'. After a moment or two, a screen will appear with some options - choose 'Drop to root shell', after which a command prompt will appear. Then type the following at the prompt, and press enter -

```
dpkg-reconfigure xserver-xorg
```

Ubuntu will then reconfigure your graphics and drop back to a command prompt. Then type 'reboot' and the system will restart. Hopefully your graphics will then at least be reasonable, but depending on what graphics chipset you have, further tweaks may be required - it might be worth then going to System -> Administration - > Hardware Drivers and seeing if a proprietory video driver is available (NOTE - you might need to enable 3rd-party software sources)...

---

