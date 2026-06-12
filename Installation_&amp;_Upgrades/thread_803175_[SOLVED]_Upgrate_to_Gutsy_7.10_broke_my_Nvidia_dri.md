---
title: "[SOLVED] Upgrate to Gutsy 7.10 broke my Nvidia driver"
date: 2008-05-22
forum: Installation &amp; Upgrades
---

### Post by Beatbreaker on 2008-05-22
after i upgraded my Ubuntu to 7.10 my Nvidia drivers broke, claiming that i had two versions of the drivers - the installed driver was inconsistent with the driver that my OS was looking for.

i used this command
```

sudo dpkg-reconfigure xserver-xorg

```

and now i have an xserver error that says

(EE) NV(0) No display devices found
(EE) Screen(s) found but none have....(something i forgot)

what the, is going on?

---

### Post by iaculallad on 2008-05-22
> **Beatbreaker said:**
> after i upgraded my Ubuntu to 7.10 my Nvidia drivers broke, claiming that i had two versions of the drivers - the installed driver was inconsistent with the driver that my OS was looking for.

i used this command
```

sudo dpkg-reconfigure xserver-xorg

```

and now i have an xserver error that says

(EE) NV(0) No display devices found
(EE) Screen(s) found but none have....(something i forgot)

what the, is going on?

Try enabling the Restricted Drivers Manager if it will detect your video adapter. System->Administration->Restricted Drivers Manager

---

### Post by Beatbreaker on 2008-05-22
> **iaculallad said:**
> Try enabling the Restricted Drivers Manager if it will detect your video adapter. System->Administration->Restricted Drivers Manager

...I can't get into the GUI

sorry I didn't say, I'm stuck outside in the terminal. I have been ever since the update. My skills in the terminal are a little limited unfortunately

---

### Post by iaculallad on 2008-05-22
> **Beatbreaker said:**
> ...I can't get into the GUI

sorry I didn't say, I'm stuck outside in the terminal. I have been ever since the update. My skills in the terminal are a little limited unfortunately

Let's try envy to install your driver using the terminal:

sudo wget [http://albertomilone.com/ubuntu/nvidia/scripts/ubuntu/envy_0.9.8-0ubuntu10_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/ubuntu/envy_0.9.8-0ubuntu10_all.deb)

sudo dpkg -i envy*.deb
sudo apt-get install -f
sudo envy -g

and just follow the procedures shown on envy's window.

---

### Post by Beatbreaker on 2008-05-23
I'm a little afraid of Envy because it's never actually worked for me, but i'll give it a shot anyway - I'll let you know. Many thanks!

---

### Post by Beatbreaker on 2008-05-24
i think i see what i've done, i installed EnvyNG by mistake- it doesn't work with 7.10 how do i uninstall it?

and i'm finding that command hard to follow with the big long address in in to install Envy, is there another way? I'm not sure that link is correct either.

i used the command "sudo envy -t" and it ran, but when i went to install the Nvidia driver it said that the version of Envy that i had was not compatible with my current OS version

---

### Post by iaculallad on 2008-05-24
> **Beatbreaker said:**
> i think i see what i've done, i installed EnvyNG by mistake- it doesn't work with 7.10 how do i uninstall it?

and i'm finding that command hard to follow with the big long address in in to install Envy, is there another way? I'm not sure that link is correct either.

i used the command "sudo envy -t" and it ran, but when i went to install the Nvidia driver it said that the version of Envy that i had was not compatible with my current OS version

To uninstall Envy, try this:

sudo dpkg -P envy

---

### Post by PmDematagoda on 2008-05-24
> **Beatbreaker said:**
> i think i see what i've done, i installed EnvyNG by mistake- it doesn't work with 7.10 how do i uninstall it?

and i'm finding that command hard to follow with the big long address in in to install Envy, is there another way? I'm not sure that link is correct either.

i used the command "sudo envy -t" and it ran, but when i went to install the Nvidia driver it said that the version of Envy that i had was not compatible with my current OS version

If you are willing to install the driver manually, you can do so with:-

1) First remove any Nvidia driver packages with:-
```
sudo apt-get remove --purge nvidia-glx-new
```

2) Obtain the Nvidia driver:-
```
wget http://us.download.nvidia.com/XFree86/Linux-x86/169.12/NVIDIA-Linux-x86-169.12-pkg1.run
```
I know, it's a long link. But if you don't want to spend the time writing it down, then you may attempt to reconfigure the X-Server to defaults with:-
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

3) Run the Nvidia installer with:-
```
sudo sh NVIDIA-Linux-x86-169.12-pkg1.run
```

4) After install, reconfigure the X-Server(especially if you ran the previous reconfigure command given).

Then see if that solves your problem.

---

### Post by Beatbreaker on 2008-05-24
ok i've come into a new problem - my internet isn't working in the terminal - please have a look at the thead i started.

[http://ubuntuforums.org/showthread.php?t=805638](http://ubuntuforums.org/showthread.php?t=805638)

---

### Post by Beatbreaker on 2008-05-26
Resolved - I decided not bother trying to fix the broken update and reinstalled hardy. I gotta say i'm VERY impressed. I was worried but i tested the hardest things and they all work now, my web cam - Perfect. My printer, worked after plugging it in. It was TOO easy!!!

Great work guys!

---

### Post by Beatbreaker on 2008-05-26
Resolved - I decided not bother trying to fix the broken update and installed Hardy over the top instead. I gotta say i'm VERY impressed. I was worried but i tested the hardest things and they all work now, my web cam - Perfect. My printer, worked after plugging it in. It was TOO easy!!!

Great work guys!

---

