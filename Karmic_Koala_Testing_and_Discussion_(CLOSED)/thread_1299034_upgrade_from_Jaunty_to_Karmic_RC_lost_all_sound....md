---
title: "upgrade from Jaunty to Karmic RC lost all sound... help, please...."
date: 2009-10-23
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by brjoon1021 on 2009-10-23
I saw at distrowatch that the Karmic RC is stable, etc... so I did a distribution upgrade with the update manager to the RC. All went well, or so I thought. I have no sound now at all with CD, Flash on the web or any source.

My audio device is the onboard audio chip for these VIA chipsets:
- Northbridge: VIA® PT880 Pro/PT880 Ultra
- Southbridge: VIA® VT8237S

Motherboard: ASRock 4CoreDual - Sata2[B]

[/B]kernel: 2.6.31-14

*** I have never had ANY trouble with this audio device with any distro, I think the upgrade removed some package and did not replace it. I believe this to be true also because when I right-click on the volume icon in the gnome toobar, I only have "mute" and "sound preferences" as options. The sound preferences option lets me look at Hardware, input, output, etc... there is no hardware detected.

Thanks.

---

### Post by danastasio on 2009-10-23
I've got this problem with my HP. I havent found a decent solution for it just yet, i've read that upgrading to the latest kernel version will fix it but i'm already upgraded to it and i dont really feel like compiling a kernel (i can never get it right...)
ANYWAY...
if you run:
```
sudo alsa reload
```
and then:
```
sudo alsa force-reload
```

you should have sound. I'm not really sure why, but it seems you need to run both of the commands to work. You can put it in a script, but change sudo->gksudo, so you have a graphic password screen and then make the script executable:
```
sudo chmod +x (name of script)
```

so it will run on boot. but that wont really help you if your running a live CD.

i'll repost if i find a better solution.

---

### Post by brjoon1021 on 2009-10-23
I just got sound to work. I had to install the gnome-alsamixer package.

But...

The volume is really low, lower than before. I don't have PCM or Front like I used to have in the preferences or controls for sound... which still makes me think some packages are missing. But, with the system volume up 100% the volume is no more than 60-70% of what I had two hourse ago before the upgrade to Karmic.

Any ideas from anyone ?

---

