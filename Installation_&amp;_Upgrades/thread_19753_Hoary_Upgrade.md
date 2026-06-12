---
title: "Hoary Upgrade"
date: 2005-03-13
forum: Installation &amp; Upgrades
---

### Post by Juneau on 2005-03-13
Hey Ubuntu people!

I am in need of your assistance.

I downloaded and used Warty for a couple of months, absolutley loved it!

but then Upgraded to hary in the development releases using synaptic and it broke my X, leaving me to use Windows as my main desktop again!!!

Now that the Haory preview release is out, I am downloading it and will burn it on to a CD.

My question is:

Can I upgrade now using a command, in failsafe mode from broken to Hoary to preview Hoary?

I REALLY dont want to format the partition as I worked at Warty for a while getting it perfect.

As I have'nt used Linux in a while I am unsure of the commands, would it be something like updating the APT-GET database to the CD, and doing a APT-GET DISTRO UPGRADE or something?


Thanks in Advance!

---

### Post by elwis on 2005-03-13
How did it break your X? Did you remove all the old Xfree stuff? What graphics card do you have?
(Me, I can't get nvidia to work at all, but if you're ok without it i suppose there's a chance)

---

### Post by Juneau on 2005-03-13
Im not quite sure why X broke. I just did a apt-get distro upgrade.

I think it might be because Xorg did'nt install properly, some Xfree left over. And some other essential components did'nt upgrade.

My graphics cards is a Nvidia GeForce 3

---

### Post by Hackmo on 2005-03-13
[QUOTE=Juneau]Im not quite sure why X broke. I just did a apt-get distro upgrade.

I think it might be because Xorg did'nt install properly, some Xfree left over. And some other essential components did'nt upgrade.

My graphics cards is a Nvidia GeForce 3[/QUOTE]
 Updating to hoary also messed up X on my system.  I followed the instructions from ubuntuguide.org for updating.  I get a lot of errors, to many to list but the last few say something about a missing keymap and some fonts already being registered.

---

### Post by elwis on 2005-03-13
It's sad, of course Hoary is BETA but it should be communicated more clearly that it probaly won't work at all, and that you can't get nvidia 3d accel in it, then I would have stayed Warty

---

### Post by Juneau on 2005-03-13
The reason I tried to upgrade was because Warty was'nt getting more updates, so I was using old software.

---

### Post by Juneau on 2005-03-13
I looked in the forums and someone asked a similar question apparently

sudo apt-cdrom add
sudo apt-get dist-upgrade


does the trick.

I'll try it now

---

