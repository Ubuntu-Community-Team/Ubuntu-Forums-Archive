---
title: "Boot Repair"
date: 2013-10-03
forum: Installation &amp; Upgrades
---

### Post by tommy2k10 on 2013-10-03
I upgraded to Ubuntu 12.04 earlier this year, and since then, I get a screen with strange graphics on and the only thing I can do is power off the computer.  I downloaded the Boot Repair CD, which made a difference once, but then it went back to the strange graphics when starting up again.  I ran a Boot Repair this morning, and got this url, which is suggested that I paste here:

[www.paste.ubuntu.com/6187488](www.paste.ubuntu.com/6187488)

Thankyou

---

### Post by mastablasta on 2013-10-03
what are your system specs? do you have any proprietary drivers installed?

---

### Post by tommy2k10 on 2013-10-03
It is a 64-bit processor, 250GB HDD, 2.5GB RAM, and I did install the NVidia driver for Linux

---

### Post by oldfred on 2013-10-03
Did you edit grub to add boot parameters?

line 1143 in Boot Info report:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="vga=792 splash"

you have this and two splash on linux boot:
vga=792 splash  quiet splash

      
 vga=xxx is a deprecated boot option

                "VGA Deprecated" Message on Boot
[http://ubuntuforums.org/showthread.php?t=1453524](http://ubuntuforums.org/showthread.php?t=1453524)

   VGA conversions:
[http://wiki.archlinux.org/index.php/Gensplash](http://wiki.archlinux.org/index.php/Gensplash)
[http://wiki.antlinux.com/pmwiki.php?n=HowTos.VgaModes](http://wiki.antlinux.com/pmwiki.php?n=HowTos.VgaModes)


 gksudo gedit /etc/default/grub
[https://help.ubuntu.com/community/Grub2#A.2BAC8-etc.2BAC8-default.2BAC8-grub_.28file.29](https://help.ubuntu.com/community/Grub2#A.2BAC8-etc.2BAC8-default.2BAC8-grub_.28file.29)

> GRUB_CMD_LINUX
Entries on this  are added to the end of the 'linux' command  (GRUB legacy's "kernel" ) for [COLOR=#ff0000]both normal and recovery modes[/COLOR]. It is used to pass options to the kernel. 

 GRUB_CMD_LINUX_DEFAULT="quiet splash"

[LIST]
[*]This  imports any entries to the end of the 'linux'  (GRUB legacy's "kernel" ). The entries are appended to the end of the [COLOR=#ff0000]normal mode only[/COLOR]. 
[/LIST]
        o To view a black screen with boot processes displayed in text, remove "quiet splash". To see the grub splash image plus a condensed text output, use "splash".

One thing Boot-Repair does is install grub of one install to all MBR with mulitple drives. I prefer to have each MBR had a different boot loader usually for the install I have on that drive. If you uncheck the auto fix option and check update MBR then in advanced options you can choose which system's boot loader to install to which MBR.

---

### Post by tommy2k10 on 2013-10-03
I'm a newbie to Linux code, so what do I do now to make it load into 12.04?

---

### Post by oldfred on 2013-10-03
Remove the entries on this:
GRUB_CMDLINE_LINUX="vga=792 splash"

       gksudo gedit /etc/default/grub
sudo update-grub

---

### Post by tommy2k10 on 2013-10-04
I did that - and now I get the following:
command not recognised: gksudo
command not recognised: gkedit
then it looks like it is going to boot properly.
I put in my password, then I get a blank screen, a flickering cursor, and then flickering graphics

---

### Post by oldfred on 2013-10-04
You need to enter command after booting at Ubuntu terminal, not at grub command line. Grub only has a few limited commands for booting.
You may need to use recovery mode.
You should be able to use e on grub menu and remove the vga=792 and second splash. You may need nomodeset just to get low quality but working video. Often then proprietary nVidia video drivers work better, but you have to install the correct version for your video card.

 Re: How To Install Nvidia Drivers [v8.1.2.12 by Bogan]. post 1126
[http://ubuntuforums.org/showthread.php?t=1743535&page=113](http://ubuntuforums.org/showthread.php?t=1743535&page=113)
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
[http://ubuntuforums.org/showthread.php?t=2081649](http://ubuntuforums.org/showthread.php?t=2081649)

---

### Post by tommy2k10 on 2013-10-04
Thankyou.
I went into my older Ubuntu installation and changed the Grub command to:
GRUB_CMDLINE_LINUX="NOMODESET" and it booted into 13.04!

---

### Post by tommy2k10 on 2013-10-11
It worked for 2 days and then the same thing.
But... this time after booting, I get a message telling me that vga=792 is deprecated.  I have tried using the boot repair disk to try and edit Grub, but it won't let me.  From my older ubuntu installation (11.10) I edited Grub, as suggested here:

[http://ubuntuforums.org/showthread.php?t=1341868](http://ubuntuforums.org/showthread.php?t=1341868)

That didn't work.

When I ran Boot Repair, I got given this new url:

[http://www.paste2.org/newpaste](http://www.paste2.org/newpaste)

Any more suggestions please?

---

### Post by oldfred on 2013-10-11
Your link is not correct. It should have 6 numbers at the end.

If getting the vga depreciated error you have not corrected the Linux boot line. You still should be able to hold shift key to get grub menu and with e edit linux line to remove it for that boot only. Then you need to edit grub to make it permanent. See posts #6 & #4.

---

### Post by tommy2k10 on 2013-10-16
I edited Grub and removed the vga=792 line permanently, saved it, it worked.
I turned it on this morning, Ubuntu 13.04 booted, entered my password, blank screen, and nothing happens!
When I edited Grub from the Terminal and saved the changes, in the Terminal, I got 'attempting to set the permissions of 'root/local/share/recently-used.xbel.  No such file or directory

---

### Post by oldfred on 2013-10-16
Does recovery mode boot?
Did you install nVidia drivers from system settings? I think with 13.04 it is other software, drivers tab? It used to be just drivers icon.

---

### Post by tommy2k10 on 2013-10-22
The menu comes up, I ask it load into 'failsafe' graphics mode, the only option is to start one session in low graphics mode, but then I get 'Stand by one minute while the display restarts' and then it hangs - I have to manually power off!

---

### Post by tommy2k10 on 2013-10-22
I managed to boot into Ubuntu 13.04 once!, and changed the resolution to 1024x768 using the Grub Configurator, restarted to see if it would boot up properly, and same as before - no!  
How do I install the latest NVidia drivers for Ubuntu 13.04?

---

### Post by oldfred on 2013-10-22
See post #13

---

### Post by tommy2k10 on 2013-10-24
Thankyou, worked fine!

---

