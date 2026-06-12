---
title: "Install freeze"
date: 2005-10-06
forum: Installation &amp; Upgrades
---

### Post by OakRand on 2005-10-06
Hello,

I am trying to install Hoary Hedgehog. The install process was going fine: the first stage completed, I removed the installation CD and the system rebooted, Grub detected my other OS which is Win98 (which I am now using to access the internet), but when the install process began loading other packages it seemed to freeze. All that remained was an unblinking underscore (_) at the top left of the screen. I rebooted and ubuntu produced typical linux boot messages but when it came to "Starting Ubuntu" the screen just turned black and that's it.

I have an install guide ([http://archive.ubuntulinux.org/ubuntu/dists/warty/main/installer-i386/current/doc/manual/en/index.html](http://archive.ubuntulinux.org/ubuntu/dists/warty/main/installer-i386/current/doc/manual/en/index.html))
which suggests: "If you are booting directly into Ubuntu, and the system doesn't start up, either use your original installation boot media, or insert the custom boot floppy if you have one, and reset your system. This way, you will probably need to add some boot arguments like root=root, where root is your root partition, such as /dev/sda1."

Can anyone help me to get Ubuntu working? I don't understand what is meant by "reset your system". I was planning on installing this weekend but I just couldn't wait.

---

### Post by MrCheese on 2005-10-07
[QUOTE=OakRand]Hello,

I am trying to install Hoary Hedgehog. The install process was going fine: the first stage completed, I removed the installation CD and the system rebooted, Grub detected my other OS which is Win98 (which I am now using to access the internet), but when the install process began loading other packages it seemed to freeze. All that remained was an unblinking underscore (_) at the top left of the screen. I rebooted and ubuntu produced typical linux boot messages but when it came to "Starting Ubuntu" the screen just turned black and that's it.

I have an install guide ([http://archive.ubuntulinux.org/ubuntu/dists/warty/main/installer-i386/current/doc/manual/en/index.html](http://archive.ubuntulinux.org/ubuntu/dists/warty/main/installer-i386/current/doc/manual/en/index.html))
which suggests: "If you are booting directly into Ubuntu, and the system doesn't start up, either use your original installation boot media, or insert the custom boot floppy if you have one, and reset your system. This way, you will probably need to add some boot arguments like root=root, where root is your root partition, such as /dev/sda1."

Can anyone help me to get Ubuntu working? I don't understand what is meant by "reset your system". I was planning on installing this weekend but I just couldn't wait.[/QUOTE]

It sounds like Ubuntu is working but the X config is screwed. Try 
[B]
[http://ubuntuforums.org/archive/index.php/t-37157.html](http://ubuntuforums.org/archive/index.php/t-37157.html)[/B]

 for a thread dealing with reconfiguring x, or you can hand hack /etc/X11/xorg.conf (you'll need to log into a text console, when the screen goes black try ctrl-alt-F2, hopefully you'll get a standard bash console. do "**sudo nano /etc/X11/xorg.conf**". Delete any silly high-res entries in the Screens section (like 1600x1200 is silly on a 15" display....).

---

### Post by OakRand on 2005-10-07
Cheers. I'll give that a try later today.

I tried reinstalling last night after I posted and the same thing happened. I watched the installation closer to look for error messages. It seems to have problems installing font-config but then resolves the errors on its own. The installation continues until "Registering Documentation info... please wait" or something to that effect. This is when the black screen and underscore appear.

---

### Post by OakRand on 2005-10-07
Tried getting into a bash console but it didn't work.

I guess that's me for Ubuntu. I'm about to try Kubuntu instead, and if that doesn't work then it's on to Mandriva.

---

### Post by OakRand on 2005-10-09
Well, Kubuntu 5.04 did the same thing, which I guess shouldn't be a surprise since it's essential the same OS.

---

