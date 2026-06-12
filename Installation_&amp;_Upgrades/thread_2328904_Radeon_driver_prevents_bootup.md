---
title: "Radeon driver prevents bootup"
date: 2016-06-25
forum: Installation &amp; Upgrades
---

### Post by Concession on 2016-06-25
Yesterday I went to install ubuntu through the xubuntu 16.04 live cd and it would fail to install after getting an error in the boot console: "radeon: ring 0 stalled for more than 10500 ms" and would keep printing that with larger time until it eventually just showed a garbled mess of colours on my screen.

I was able to do the full installation when I set "nomodeset" in the boot up of the live cd (abet with a really low resolution). Now, I have it installed and can't boot up xubuntu unless I use the "nomodeset" parameter in grub. Otherwise, it just displays a garbled mess of colour on the screen almost immediately and presumably crashes. I've updated all of the packages in the computer and used it with the "nomodeset" parameter enabled but it's really really really not ideal. Is there anything I can do to better this situation? My understanding is amd's fglrx driver doesn't work on 16.04 and their replacement amdgpu is still on the way.

My computer is a desktop with an amd graphics card and I can't use intel integrated graphics because my processor is a xeon and doesn't have it.

---

### Post by banceu_sergiu_ione on 2016-06-26
You may want to consider another [ubuntu flavour]("https://wiki.ubuntu.com/XenialXerus/ReleaseNotes") since with only generic graphic in use is not nice to see. Try Lubuntu or Mate Ubuntu/ PowerPC if you have and old pc.

---

### Post by yoshii on 2016-06-27
You need to update the grub with the nomodeset command so that you don't have to keep inputting it at boot.  
Here's how I did it on my system:  [http://ubuntuforums.org/showthread.php?t=2322014&p=13477330#post13477330](http://ubuntuforums.org/showthread.php?t=2322014&p=13477330#post13477330)

You don't need better graphics support if you are just doing basic things and not anything involving 3D rendering or texture mapping or digital lighting or video DSP.  
I still watch and edit HD youtube videos, compose music (with animated screen graphics for the meters).  Everything works fine without the hardware support.  
But I had to install VLC Media Player instead of Parole and it works better than Xine too.  Parole kept crashing, even on the alternate video driver mode.  
VLC is reliable and freeware.  

If you do gaming you will need a better solution, but for everything else, it will be all sorted once you get the grub settings permanent.  Good luck

---

### Post by mastablasta on 2016-06-28
> **Concession said:**
> Is there anything I can do to better this situation? My understanding is amd's fglrx driver doesn't work on 16.04 and their replacement amdgpu is still on the way.

My computer is a desktop with an amd graphics card and I can't use intel integrated graphics because my processor is a xeon and doesn't have it.

what is your GPU?

is the OS a fresh install?

---

### Post by mastablasta on 2016-06-28
> **banceu_sergiu_ione said:**
> You may want to consider another [ubuntu flavour]("https://wiki.ubuntu.com/XenialXerus/ReleaseNotes") since with only generic graphic in use is not nice to see. Try Lubuntu or Mate Ubuntu/ PowerPC if you have and old pc.
They did consider  - we are talking about Xubuntu 16.04 which should work well even with old GPU chips.

---

