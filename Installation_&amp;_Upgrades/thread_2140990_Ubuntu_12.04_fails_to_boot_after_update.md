---
title: "Ubuntu 12.04 fails to boot after update"
date: 2013-05-01
forum: Installation &amp; Upgrades
---

### Post by damog88 on 2013-05-01
Hi everyone,

I've got installed Ubuntu 12.04 (64bits) in my laptop. I usually install updates from the update manager without taking so much care, and it never gave any problem.

The thing is that it's been a little while since I don't update, and last Sunday I decided it was the right time to go with it. It all went ok, just like normal, but I was suprised when, after the system told me to reboot, that full reboot never came to happen. In the GRUB I selected the Ubuntu OS as I always did, but after this, the screen went dead (all black, as it was turned off, not even the brownish colour typical of Ubuntu "black screens"). I left it like that for an hour or so, hoping it finished the reboot, but when I saw it was doing nothing, I had to poweroff by force (reboot button).

And, since then, until now, when I try to boot into Ubuntu, I get fails (sometimes it doesn't boot, sometimes it does, but it takes a lot of time (before updating it was almost "instantaneously" boot), sometimes I get a blinking prompt and it stays there forever, sometimes after the prompt the system boots, and the last few times I tried to boot, it did nothing at all (after selecting OS, dead screen).

The only way I have to boot into the OS is selecting the "Recovery mode". But I want to get it to its prior state, or, if not, somehow fix it, because I have to work with this system, and, although I also have Windows working on the same laptop, I have to use Linux...besides I got used to it and I like it.

Does anyone know the possible solution??





Thank you very much!!

---

### Post by ibjsb4 on 2013-05-01
In grub, do you have the option to use the previous kernel?

---

### Post by damog88 on 2013-05-01
Yep! I have the option "Previous linux versions", and there I can select 39,38,37...and selecting 37-38 is what is working better. Thank you very much!

But I'd like to know if I can make (f.e.) the kernel 37 the principal boot option. I have seen that if you press 'e' in the GRUB you access a code menu in wich you can modify somethings, but I don't want to touch without knowing what I'm doing...

---

### Post by dino99 on 2013-05-01
install & open synaptic, then purge the kernel(s) you does not want to use (2 headers + 1or 2 image(s) for each removed kernel)

note: its a good idea to have at least 2 kernels installed (when one is borked)

---

### Post by ibjsb4 on 2013-05-01
Yep, you can set the default kernel.

[http://ubuntuforums.org/showthread.php?t=1535779&p=9617164&viewfull=1#post9617164](http://ubuntuforums.org/showthread.php?t=1535779&p=9617164&viewfull=1#post9617164)

more here

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=edit+grub+kernel&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=edit+grub+kernel&sa=Search&cof=FORID:9)

---

### Post by damog88 on 2013-05-06
SOLVED. Thank you all!!! :D

---

### Post by ibjsb4 on 2013-05-06
And welcome to the forums :)

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

