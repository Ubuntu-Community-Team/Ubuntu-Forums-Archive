---
title: "Missed the GRUB install, now won't boot"
date: 2006-10-23
forum: Installation &amp; Upgrades
---

### Post by Harvey Phillips on 2006-10-23
Had all sorts of informative replies as to why I couldn't get ubuntu to load using two HD chosen from the bios, but gave up on the two drive procedure and did what I've was advised not to do... tried to coexist with Win98se on one drive.

I partioned using Partition Magic and made a nice big space for Ubunto.  Install went well until the last section about GRUB. Somehow that screen got by me and GRUB never got installed.

Anyway around this without a complete reinstall?

Thanks,

Harvey

---

### Post by divague on 2006-10-23
[http://www.ubuntuforums.org/showthread.php?t=224351&highlight=grub](http://www.ubuntuforums.org/showthread.php?t=224351&highlight=grub)

---

### Post by SirPecanGum on 2006-10-23
Or this might be useful: [http://freshmeat.net/projects/supergrub/](http://freshmeat.net/projects/supergrub/)

---

### Post by bulldog on 2006-10-23
This will restore grub to your MBR so that grub appears at start up maybe you need to hit ESC to see it.

Boot into the live Ubuntu cd. 

When you get to the desktop open a terminal and enter. 


```
sudo grub
```


This will get you a "grub>" prompt (i.e. the grub shell). At grub>. enter these commands


```
find /boot/grub/stage1
```

This will return a location. If you have more than one, select the installation that you want to provide the grub files.
Next, THIS IS IMPORTANT, whatever was returned for the find command use it in the next line (you are still at grub>. when you enter the next 3 commands)


```
root (hd?,?)
```

Again use the value from the find command i.e. if find returned (hd0,1) then you would enter root (hd0,1)

Next enter the command to install grub to the mbr


```
setup (hd0)
```

Finally exit the grub shell


```
quit
```

That is it. Grub will be installed to the mbr.

This topic might be helpfull too.

[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

---

### Post by Harvey Phillips on 2006-10-25
Is GRUB the opening screen? If so, I do get that screen. But just to be sure, I totally reinstalled the program from scratch and as before I got a checklist that shows each step of the boot and gives an OK for each. But when the list shows the final OK and goes to the next step... that's where I have the problem. At that point, I get a series of quick horizontal flashes and then the program clicks out. 

I am installing to an older machine though it is able to run Win98se without problem and can even run XP though more slowly. I have Ubuntu installed on a 20GB HD; the machine uses a AMD 400mz chip and has 256mb of memory. I was under the impression that Linux does work with limited resources (?).

Might the problem be that my machine just doesn't have enough "oomph" to run Ubuntu; and if so, could you suggest a distro that might be more appropriate?  My main reason for trying Linux is just to get some experience in using another OS. 

Thanks to all for your input.

Harvey Phillips

---

### Post by divague on 2006-10-25
I've heard that xubuntu is lighter than ubuntu, and runs well with > with limited resources

---

### Post by bulldog on 2006-10-25
> **Harvey Phillips said:**
> Is GRUB the opening screen? If so, I do get that screen. But just to be sure, I totally reinstalled the program from scratch and as before I got a checklist that shows each step of the boot and gives an OK for each. But when the list shows the final OK and goes to the next step... that's where I have the problem. At that point, I get a series of quick horizontal flashes and then the program clicks out. 

I am installing to an older machine though it is able to run Win98se without problem and can even run XP though more slowly. I have Ubuntu installed on a 20GB HD; the machine uses a AMD 400mz chip and has 256mb of memory. I was under the impression that Linux does work with limited resources (?).

Might the problem be that my machine just doesn't have enough "oomph" to run Ubuntu; and if so, could you suggest a distro that might be more appropriate?  My main reason for trying Linux is just to get some experience in using another OS. 

Thanks to all for your input.

Harvey Phillips

The question is where it exactly stops and what you see.
I think there's a problem with your graphic's and not GRUB.

If I understand you well,it boots up but when you should see the login-screen,it messes up.

Do you have a possebillity to login in command line mode?
Try entering CTRL-ALT-F1 simultaniously and see if you can login.

If so type```
sudo dpkg-reconfigure -phigh  xserver-xorg
```

Then you can try```
sudo /etc/init.d/gdm start
```

Hope this will work.

---

