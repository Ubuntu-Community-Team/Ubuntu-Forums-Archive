---
title: "kernel panic or frozen screens AMD 64 Athlon system"
date: 2006-06-22
forum: Installation &amp; Upgrades
---

### Post by vibhu on 2006-06-22
Hi, 

I have been trying to run the Ubuntu 6.06 CD, but have not been able to boot up even once. 

Either the bootup freezes at the first screen after the text showing all the initializations has scrolled by ( with a brown background and a dialog with ubuntu in the right side), or if I use noapic nolapic, I get kernel panic about killing init. 

My system : 
processor : AMD 64 Athlon 3700+
memory    : 2 GB RAM
hard disk  : Seagate 200GB Sata
mother brd: Asus K8N VN
Graphics card : Nvidia 7900GT
DVD : Sony DVD RW

I dont know what is going on. I have tried to disable legacy USB also in the BIOS, but still having the problems :(

Any help will be really appriciated. This is the first time that I have not been able to install linux on my PC. This is also the first time I am using AMD.

The WinXP is working fine and I am able to play games on it without any problems.

---

### Post by taloche on 2006-06-22
I have an amd64. I had the same problem when I first tried to install dapper. I don't know if it's related, but you might try to disable acpi and smp. In order to do this, when you reach the installation program, edit the command line. You should get something like:

linux root=/dev/hda1 ro quiet ... --

insert "acpi=off nosmp noapic nolapic" right after ro.

If it doesn't work, try to locate the crash. Remove the "quiet" option and disable the framebuffer (the graphic logo). That should get you additionnal informations about the kernel panic, including the address of the crash. Then, look in the System.map associated with your kernel to identify the function where the crash occured (or alternatively, post the address and the exact version of your kernel here if you can't get a working linux).

---

### Post by vibhu on 2006-06-22
Thanks for the reply !

I tried by setting the options. 

The last message I see is something to do with squashfs, after which it shifts to the graphical mode with the ubuntu screen. A background sound is heard, and then it gets stuck with the sound being looped. The keys and mouse stops responding at this time. 

I do not know how to get the system.map 

I am using Ubuntu 6.06 CD.

---

### Post by vibhu on 2006-06-22
ok. some more stuff i tried out - this time using ubuntu 5 CD.  

Since Ubuntu5 has a text based install interface, it is a bit better in the sense that it does not hang trying to load the graphics. Instead it copies the files to the harddisk, modifies the boot loader and then starts on the actual installation - when it dies . After many page scrolls I get this at the end of it :

```

[4294953.192000] =====================
[4294953.192000] [<c0104a3a>] do_coprocessor_error+0x0/0x11
[4294953.192000] [<c0104b45>]do_simd_coprocessor_error+0x0/0x6f
[4294953.192000] [<c0102e44>]sysenter_entry+0x0/0x7
[4294953.192000] [<c0102e44>]sysenter_entry+0x0/0x7
[4294953.192000] [<c01039d3>]device_not_available_emulate+0xe/0f
[4294953.192000] [<c0104158>]do_overflow+0x0/0x5e
[4294953.192000] [<c01041b6>]do_bounds+0x0/0x5e
[4294953.192000] [<c0104214>]do_invalid_op+0x0/0x86
[4294953.192000] [<c010429a>]do_coprocessor_segment_overrun+0x0/0x5e
[4294953.192000] [<c0104bb4>]do_spurious_interrupt_bug +0x0/0x1
[4294953.192000] =======================
[4294953.192000] Unable to handle kernel paging request at virtual address 538bc031
[4294953.192000] printing eip:
[4294953.192000] c0103bdb
[4294953.192000] *pde = 00000000
[4294953.192000] Recursive die()failure, output suppressed
[4294953.192000]  <1>Unable to handle kernel paging request at virutal address 00ac2500

```

At this point the computer becomes unresponsive, and I have to manually reset it.

---

### Post by taloche on 2006-06-23
Ok, so it's not the problem I had in mind. Since the crash happens when the graphical mode starts, it's probably related to your X.org server. You can append "init=1" to your boot option. This will start your system in single user mode (it won't start the graphical mode at all). This way, you should be able to access your system.
   Then, you can look in /var/log/X.0.log (might be a slightly different name) to see if there is something wrong. If you see an error, you might try the following:

* First, backup you config file: sudo cp /etc/X11/x.org /etc/X11/x.org.bad
* Then, reconfigure your server: sudo dpkg-reconfigure xserver-xorg
* Choose "vesa" as a display driver to be sure, and pick the safest defaults.
* You can test your configuration by running "sudo /etc/init.d/gdm start" or "sudo startx" (I'm not sure if gdm will start in single user mode and I can't check at worm).
* If you still have the problem, you can restore the previous config file.

---

### Post by tseliot on 2006-06-23
Please follow these instructions:

1) you install Ubuntu using the alternate installation CD.

2) After the installation the xserver will crash

3) You will be able to boot in RECOVERY MODE from the GRUB Menu almost as soon as you turn on your computer (it will take you to the command line).

Then you will need to type:
```
dpkg-reconfigure xserver-xorg
```

and select the "vesa" driver. Press ENTER whenever you don't know the answer to a question.

4) Type:
```
reboot
```

The Xserver should work fine

---

### Post by vibhu on 2006-06-24
Ok. Will try the steps given by ***tseliot***. Downloading the alternate-amd64 via torrent. Will update once I have downloaded and tried the steps given above.

---

### Post by vibhu on 2006-06-25
Thanks for the steps ! It worked !

I also had to disable glx in the config screens which come up. 

Now I have been able to install Ubuntu, and am doing the other essential installs ( gcc, LAMP, nvidia drivers etc).

---

### Post by vibhu on 2006-06-26
Thanks Guys ! 

Uploading a screenshot of how my system looks :-). A small [writeup also on my blog]("http://vibhurishi.blogspot.com/2006/06/finally-gone-to-64-bits.html"). 

[IMG]http://photos1.blogger.com/blogger/2628/376/1600/ubuntu-1.png[/IMG]

---

