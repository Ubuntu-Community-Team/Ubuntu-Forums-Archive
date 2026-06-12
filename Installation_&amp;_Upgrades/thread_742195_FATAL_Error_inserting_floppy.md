---
title: "FATAL: Error inserting floppy"
date: 2008-04-01
forum: Installation &amp; Upgrades
---

### Post by calais on 2008-04-01
I know that other's have had similar posts, and the recommended fix has been to do something like

As root, edit /lib/modules/2.6.10/modules.alias. Search for the word floppy. Place a # at the beginning of the line. Save the file and reboot.

But I am trying to boot from a Live CD. I'll confess, however, it's not Ubuntu. But, Would anyone still know how to fix this while using a live CD? Would I have to modify the CD image and re-burn the disc? 

Thanks!

---

### Post by dstew on 2008-04-01
Usually, you can alter configurations and install software on a running live CD system. The only drawback is that it all goes away when you shut down. If you alter a configuration setting, you need to restart the process in order for the configuration settings to take effect. In the case of the suggested floppy fix, this of course will not work because at reboot the file system goes away, and you lose your configuration change.

The way to start or stop a module in a running system is to use the modprobe command. For example, to stop the floppy module, use```
sudo modprobe -r floppy
```To start it again, use```
sudo modprobe floppy
```

The way to stop a module from loading on a live CD system at boot time is to use a kernel parameter. You can add this to Ubuntu Live CD kernel lines by pressing F6 at the first menu.

What is your problem, anyway? Are you trying to get the floppy drive to work properly? See [this document]("http://www.mjmwired.net/kernel/Documentation/floppy.txt") for kernel options to try to improve floppy performance (you can also add these the a modprobe statement). To disable the floppy kernel module at boot time, try adding **floppy=off** to the kernel line. I could not find this documented, but I bet it will work.

---

### Post by calais on 2008-04-01
Haha, what am I trying to do? Well, I don't know if this sort of behavior can be condoned in this forum.

Back Story: My roommate posted a barrage of less than tasteful pictures of me all around the computer science department of my university. We play pranks on each other often, but I kinda feel like when it leaves the apartment and it's posted on my capstone evaluator's door and my department head's door, etc... it's crossing the line. 

Current Story: I'm using trinity rescue to try to get into his window machine so I can delete the picture and maybe leave a harmless message telling him that I'm not amused. 

As I said, not sure if that sort of behavior can be endorsed or condoned here.... but that's what I'm trying to do.

---

