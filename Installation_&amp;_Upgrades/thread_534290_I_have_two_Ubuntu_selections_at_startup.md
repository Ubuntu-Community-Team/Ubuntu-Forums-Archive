---
title: "I have two Ubuntu selections at startup"
date: 2007-08-25
forum: Installation &amp; Upgrades
---

### Post by edanastas on 2007-08-25
I installed Ubuntu as a dual boot for the first time and it went smoothly and fast! I am really excited to finally get into the Linux OS and hopefully use Windows as little as possible!

The installation seemed to work after rebooting and now after the 117 or so initial updates (from update manager) and a reboot, it shows two Ubuntu installations at startup.

After checking the GRUB configuration using 
```
sudo gedit /boot/grub/menu.lst
```

It appears that the Ubuntu Kernels are different, one at "2.6.20-15-generic" and the top selection (default) is "2.6.20-16-generic". What is the correct approach to take on this, should I comment it out on the GRUB configuration so it doesn't show up? or do you typically just leave it?

---

### Post by Jose Catre-Vandis on 2007-08-25
That's correct. Your updating has also updated to the newer kernel, which is now the default. You do have a choice though, and you can boot into the older kernel still if you have any problems.

You can comment out the older kernel if you wish (just put "#" in front of the boot code in menu.lst)

Keep the recovery option in for your default boot kernel.

---

### Post by bigboy_pdb on 2007-08-25
If you comment out the earlier kernel versions and you later have a problem and want to return to the old kernel, you can always remove the comments by booting from a Live CD. You can't initially change the files on the CD so in order to do this you'd have to unmount the hard drive, remount it using "sudo" in a terminal, and then you can edit the file using "sudo"/"gksudo" and "gedit" (if I remember correctly).

---

### Post by edanastas on 2007-08-25
Okay, Nevermind. That all sounds a little complicated for me. I will leave one old boot Kernel just in case. Once it updates again, maybe then I'll comment out the third old one, unless it does that automatically?

Thanks for the help!

---

### Post by bapoumba on 2007-08-25
I _always_ keep the previous working kernel. Just in case there is a problematic upgrade to a new kernel.

In any case, to remove grub entries for a kernel, you have to uninstall it (from synaptic for ex, look for the exact version number). Grub menu is automatically updated.

---

### Post by bigboy_pdb on 2007-08-25
If I were to elaborate, it wouldn't sound so complicated (let me know if you want me to do that).  I haven't read a post where someone needed to do what I suggested.

If you really don't want the old kernels, but you're still a little worried then you can just keep the newest kernel and the previous kernel that you used on the GRUB boot list and comment out any additional kernels (if there are any). If you've been using a kernel for weeks or months, you haven't had any problems, and you've been doing everything that you had done with your older kernels then I doubt that you're going to encounter any problems with the newer kernel. Besides, if for some reason you do need to get them back and cannot boot into Ubuntu (which isn't as likely to happen if you run the new kernel quite a bit before removing any additional ones) then you can just ask how to fix the "/boot/grub/menu.lst" file using the Live CD. If I were to read it, I'd help you and I'm sure that other people would help you as well (and if they didn't you could always just send me a message).

Personally, I leave the kernels there. If there were to be more than 2 or 3 kernels on the list I might comment the additional ones out. I haven't done that but I've thought about it. However, I don't usually boot into Windows so I don't mind Windows being at the bottom of the list (even if it does get a little long).

---

### Post by edanastas on 2007-08-25
I think bapoumba has a good option. When the time comes that you have too many Ubuntu Kernels, you can just uninstall from Synaptic the earlier version and it removes it from the boot screen automatically.

...I love Synaptic, Mac has something like this called MacPorts, but it is not nearly as developed. I tell everyone about Synaptic when I tell someone about Ubuntu, I am really impressed. I'm even going to try and get my mom on Ubuntu now! Wish me luck...

---

### Post by Gremlinzzz on 2007-08-25
You can also install startup manager and just check only show 1 kernel in the advanced tab
here screen shots 
[http://linux.softpedia.com/progScreenshots/SUM-Start-up-Manager-Screenshot-27320.html](http://linux.softpedia.com/progScreenshots/SUM-Start-up-Manager-Screenshot-27320.html)
and heres were you get it from just click SUM Start up Manager Download
then Debian DEB mirror 1 
[http://linux.softpedia.com/get/System/System-Administration/SUM-Start-up-Manager-27320.shtml](http://linux.softpedia.com/get/System/System-Administration/SUM-Start-up-Manager-27320.shtml)
:guitar: its a deb package easy install

---

