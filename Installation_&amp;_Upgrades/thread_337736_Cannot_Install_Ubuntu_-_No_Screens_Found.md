---
title: "Cannot Install Ubuntu - No Screens Found"
date: 2007-01-13
forum: Installation &amp; Upgrades
---

### Post by ClintiePoo on 2007-01-13
I have been trying to install ubuntu for a long time now.  I have a Dell Dimension 9150 with a dual output ATI graphics card and another Nvidia card.  I have tried several options, hoping one will work:

[IMG]http://i15.photobucket.com/albums/a366/clintiepoo/PICT1747Medium.jpg[/IMG]

...

No matter what I do, I keep ending up with this screen.

[IMG]http://i15.photobucket.com/albums/a366/clintiepoo/PICT1746Medium.jpg[/IMG]

I'm stuck.  I really like ubuntu but I cannot install it.  The live CD works on a laptop I tried, but the x server will not start on my desktop.  Thanks for the help.

---

### Post by icefaerie on 2007-01-13
What are the specific models of the graphics card(s?) you have?

---

### Post by ClintiePoo on 2007-01-13
> **icefaerie said:**
> What are the specific models of the graphics card(s?) you have?

My primary one is a Radeon X300 SE 128MB HyperMemory, according to the windows device manager.  This is the only one I got to work when using Linux before, and it's the one that came with the computer.

---

### Post by ClintiePoo on 2007-01-14
I still don't know what to do here...

I used to have ubuntu installed with this hardware setup.  I had to use the "Safe Video Mode" to install it and then install the flgrx (? Not sure if that's the name, the ATI Driver) afterwards.  Now I can't get anything to work.  I have a copy of a xorg.conf file that works with my setup on a USB drive, but I don't know how to get it all going.  Please help.  I assume I'm just missing something simple.

---

### Post by icefaerie on 2007-01-15
Okay, so, if I'm reading correctly, you have an xorg.conf on a USB stick you want to copy to your computer.  Here's how to do that:

Make a mount point for your USB stick:
```
sudo mkdir /mnt/usb
```
You can make it something else...sometimes people use /media instead of /mnt.  It doesn't really matter for this though.

Find out where your usb stick is.  Plug it in, and then do this:
```
dmesg | tail 
```

Here is mine, for example:
```
liz@sirius:~$ dmesg | tail
[17221996.184000] sda: Write Protect is off
[17221996.184000] sda: Mode Sense: 03 00 00 00
[17221996.184000] sda: assuming drive cache: write through
[17221996.188000] SCSI device sda: 2001888 512-byte hdwr sectors (1025 MB)
[17221996.188000] sda: Write Protect is off
[17221996.188000] sda: Mode Sense: 03 00 00 00
[17221996.188000] sda: assuming drive cache: write through
[17221996.188000]  sda: **sda1**
[17221996.188000] sd 1:0:0:0: Attached scsi removable disk sda
[17221996.188000] sd 1:0:0:0: Attached scsi generic sg0 type 0
```
I have bolded the important part.  This means it's at **/dev/sda1**.

Now we will mount it:
```
sudo mount /dev/sda1 /mnt/usb -o uid=*user*
```
Replace *user* with your username.  This is just so you'll have full permissions to the drive.

Okay!  Now you should be able to look at the files on your usb stick.
```
ls /mnt/usb
```

Now you can copy your xorg.conf, but first you should probably backup your current xorg.conf just in case...
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

Now we'll copy it from the USB drive to your computer:
```
sudo cp /mnt/usb/xorg.conf /etc/X11/xorg.conf
```

That should do the trick.  Hopefully that's what you meant...

---

### Post by ClintiePoo on 2007-01-15
icefaerie,

That's great.  I wish I had read it sooner....   I ended up doing this another way and it worked.  Here's a rundown of what I did, in case anyone reads this later.

This is from[ bug#67487]("https://launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/67487"), which talks about X not starting on the live CD with an ATI card...

For Ubuntu 6.10

1) In the boot option on Live CD boot screen (F6), add:
break=bottom

**This gives you a command prompt before you boot**

2) Boot the CD, and wait for the (initramfs) prmpt.  At the prompt do:
mv /root/etc/X11/xorg.conf /root/etc/X11/xorg.conf.disabled

**Moving the xorg configuration file forces boot in vesa mode, which works with an ATI Card**

3) At the prompt do:
exit

**This allows the LiveCD to boot**

OK, now you can see SOMETHING.  If you try to install ubuntu, it fails.  You moved xorg.conf, remember?  Move it back.

4) At a command prompt, enter
sudo mv /root/etc/X11/xorg.conf.disabled /root/etc/X11/xorg.conf

5) Install Ubuntu like you would normally.

6) Reboot

7) X fails to start again....  Hit Ctrl + Alt + F1 and login.  Now install the ati drivers:
sudo apt-get-install xorg-driver-fglrx fglrx-control
sudo aticonfig --initial

8) Start x, and everything is fine

startx

;) 

Thanks again for the help icefaerie.

---

### Post by BU2007 on 2007-01-18
ClintiePoo - Great help! Worked like a charm on my Dell Dimension 9150 w/ ATI card...

However, everytime I reboot now I get the (initramfs) prompt. I just type in 'exit' and everything works fine. It's annoying though. Anyway I can remove this (initramfs) prompt now?

Thanks again.

---

### Post by anubis24 on 2007-01-18
ClintiePoo,

Thanks for the info.  Worked like a charm on my Dell Optiplex GX620 with a Radeon card.

---

### Post by supaphly42 on 2007-03-01
> **BU2007 said:**
> ClintiePoo - Great help! Worked like a charm on my Dell Dimension 9150 w/ ATI card...

However, everytime I reboot now I get the (initramfs) prompt. I just type in 'exit' and everything works fine. It's annoying though. Anyway I can remove this (initramfs) prompt now?

Thanks again.

I followed the instructions (which worked, thank you!), but I'm left with having to exit at this prompt every time I boot up as well. Any ideas?

---

### Post by supaphly42 on 2007-03-22
Ok, I figured out how to stop the prompt from appearing. Open a terminal, and edit the file ```
/boot/grub/menu.lst
```Do a search for the word "break", and remove it. In VIM you can do ```
:%s/break//g
```That will take the break out of the boot sequence.

---

### Post by SilverZero on 2007-03-31
You guys are great! You've gotten me farther than anything else in my 6.10 adventure. I've got a Dell XPS400 (same as a 9150) with an ATI X300 in it. I got as far as installing Ubuntu, but now I'm having trouble with the final steps.

When ClintiePoo says to run "aticonfig --initial" and then "startx," my system goes to a black screen when I try to restart X. It also black-screens when I just reboot. It will sit forever, but it will respond when I Ctrl+Alt+Del it, and it even flashes the Ubuntu splash (a bit mangled, maybe) when it does, so I know the system is there, just kinda "stuck" in the background.

Any ideas? Is it a problem with the fglrx installation? I don't see why some of you with the same system are getting through this, and I'm having this black screen problem.

Thanks!

---

### Post by SilverZero on 2007-03-31
UPDATE:

I can start X if I run the dpkg-reconfigure process and choose VESA as the driver (not fglrx or ati), but obviously the performance is weak - jumpy scrolling and so forth.

I guess I just haven't got the right drivers installed for my X300 PCI-e card. Any suggestions?

UPDATE 2:

I used [this guide]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI") (2nd part - "install from ATI") and the latest installer from the ATI website, and it worked!

---

