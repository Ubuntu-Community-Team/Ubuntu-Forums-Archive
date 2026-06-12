---
title: "Installation of NVIDIA drivers crashes X.org"
date: 2007-05-09
forum: Installation &amp; Upgrades
---

### Post by Tarrasque on 2007-05-09
Hello.

I followed the steps for installing the NVIDIA drivers on 7.04 from Synaptic.

I had to use the nvidia-glx ones because my card is a GeForce 4, but everything seemed to go well.

Unfortunately, when I reboot the X server crashes on startup and dumps me in console mode with an error.

Unfortunately I cannot paste the error now since I'm not home and I forgot to copy it.

IIRC, anyway, it complained about a "nvidia driver" not being found or something like that. I'll try to post it later.

Could it just be an error in the script updating xorg.conf? Can I correct it by hand?

Thx.

---

### Post by starcraft.man on 2007-05-09
Ok... quick way to fix that I believe since your still having console access is to run this:

```
sudo dpkg-reconfigure xserver-xorg
```

follow the prompts, when you get to driver... select "nv" and NOT "nvidia". Then when your done configuring, restart. Should get your GUI back, unless you've done a lot of harm...

---

### Post by Tarrasque on 2007-05-09
Yes, I will surely be able to do that, since I have console access.

But, won't this just bring me back to the point where I don't have 3D acceleration?

Is'nt there a way to solve the problem?

---

### Post by starcraft.man on 2007-05-09
> **Tarrasque said:**
> Yes, I will surely be able to do that, since I have console access.

But, won't this just bring me back to the point where I don't have 3D acceleration?

Is'nt there a way to solve the problem?

Course there is, I guess I was just really gonna wait till you got home and were at your computer, one step at a time and all that :)

Since when you switched to the "nvidia" drivers your GUI crashed, I can only assume they were badly/not installed.

So, easiest way to fix this is [envy]("http://www.albertomilone.com/nvidia_scripts1.html") :)

After you get back to your gui of course, log in, download that. You prolly want 0.9.2 unless your using dapper, then you need older copy. Then double click and install it. Then open it, Applications > System Tools > Envy.
Click "automatically install nvidia drivers" and say y/yes to any prompts from the terminal or a dialog. When you reboot you should have your drivers in properly and configured :)

---

### Post by Tarrasque on 2007-05-09
Thank you very much for your help.

It was greatly appreciated, expecially since, well I didn't provide much detail.

I will get back to the console (gee, I didn't say this for a long time, actually it's the first time my server crashed in years, since I installed the NVIDIA drivers on Mandrake 10...:lolflag: ) tonight and try this "envy" which seems quite a nice idea.

Can't wait to have Beryl. ;)

---

