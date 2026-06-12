---
title: "Dual boot 10.10 &amp; Mint 12 - remove Mint 12"
date: 2012-05-20
forum: Installation &amp; Upgrades
---

### Post by pabloikba on 2012-05-20
I have dual boot Ubuntu 10.10 and Linux Mint 12 (installed last). I want to get rid of Linux Mint 12 which is on external drive. But, I am wondering how to get rid of the Grub that Linux Mint 12 installed which makes it the first choice. If I just delete the files on the external drive how do I get the computer to boot directly into Ubuntu 10.10?

Many thanks for any help.

Pablo

---

### Post by darkod on 2012-05-20
If you have only one internal disk, that should be /dev/sda.

Boot your ubuntu once, open terminal and do:
sudo grub-install /dev/sda

That will install grub2 from ubuntu to the MBR of the disk. Test if it will work without the external disk connected. After that you can do what you want with the mint partition(s).

If mint is in the grub2 boot menu after you remove it, run:
sudo update-grub

to update the menu.

---

### Post by pabloikba on 2012-05-20
Many thanks, Darkrod. Worked perfectly.
I appreciate your response.
Pablo

---

### Post by darkod on 2012-05-20
No problem.

You also need to remember that support for 10.10 has already ended. It would be better if you start planning to use a more recent version.

Since upgrading many versions in a row makes no sense, it's probably better to think about a new clean install over the 10.10.

You can make a live cd of the latest 12.04 LTS and test it from the cd to see how you like it and whether it works on your hardware. That would be the first step to see if everything is working.

---

### Post by pabloikba on 2012-05-20
Darkrod,

You have a valid point about 10.10 not being supported anymore. I have a dilemma.....I tried to solve it with Linux Mint 12 (Mate) but was not happy with it.

I am an old fart and am not happy with 11.10's Unity....I was attempting to stay with something familiar which is why I tried Linux Mint 12 with Mate Cinnamon...

Any suggestions that might fit my "getting old mind"?

Pablo

---

### Post by darkod on 2012-05-20
There is a package called gnome-panel which is almost the same as the interface in the older versions of ubuntu.

Unity started with 11.10 but you can install that package and during login select to load the Gnome Classic interface and it will look almost the same. I haven't tried it, but that's what they say.

Also, it remembers the last type of session used, so if you login using gnome classic once, you don't need to select it every time. You just enter your password and that's it, as usual.

I don't think you can try it in live mode because it only works if you log out and try to log in again selecting Gnome Classic session. But it should work OK for you with 12.04 LTS.

---

### Post by pabloikba on 2012-05-20
Thanks,

I didn't know about gnome-panel...I'll give a try....

Pablo

---

### Post by billyseth on 2012-05-20
You could also test out a Xubuntu live CD, I think you might be surprised on how well it fills the void that Unity created for some people

---

### Post by pabloikba on 2012-05-20
Thanks, Billyseth,

I like alternatives....I'll give xubuntu a try also....

Pablo

---

### Post by pabloikba on 2012-05-25
I installed Ubuntu 12.04 as a dual boot with Ubuntu 10.10. Activated gnome-panel. For the most part, I am happy with it. Once I get everything installed and moved over, I will probably delete the 10.10. 

Many thanks for the suggestions and info.

Pablo

---

