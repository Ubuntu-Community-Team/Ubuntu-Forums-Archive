---
title: "installation issue !!! please HELP"
date: 2007-08-01
forum: Installation &amp; Upgrades
---

### Post by anantgowerdhan on 2007-08-01
Hi,

This is the third time I'm trying to install Ubuntu on my laptop and its didn't install it properly.

First I tried with Ubuntu, than I used Xubuntu and today I tried Kubuntu all these distro gave me same error message after installation.

I used live CD of Kubuntu and start installation and it went smoothly, no error at all. It asked me to restart the computer and I did so. 

First surprise for me was, the GRUB was not graphical and it had written Ubuntu. Anyways thats not an issue. It showed me Kubuntu splash screen and suddenly dropped me to the command line with the following error

> apt-get is not installed, install it manually apt-get install apt

now please tell me if apt-get is not installed, how will I use apt-get command? and it doesnt even take me to the login screen. Tell me where I'm wrong? and will Alternate installation CD will work for me?

Regards,
Anant

---

### Post by Pumalite on 2007-08-01
Posting your specs would help, but for the looks of it, it seems you'd be better off installing with Alternate CD.

---

### Post by anantgowerdhan on 2007-08-01
Thanks for the reply.

My Laptop is a bit old laptop with 256 MB RAM and 1.6 GHz processor. Kubuntu live CD ran smoothly on that and had no issue during installation. 

I used Mandriva, PCLinuxOS and Dreamlinux on the same laptop and I never had such issue. 

So this alternate CD is a live CD or just an installation CD. Whats the actual difference?

Regards
Anant

---

### Post by Pumalite on 2007-08-01
Glad you posted your specs. Makes everything easier. You need Alternate Xubuntu CD: [http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/](http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/)
Why? Because is the Ubuntu that will run best in your laptop. It's text mode, but it's easy to use. At the end you end up with a graphical interface, only that the Desktop is lighter and makes your laptop run faster.

---

### Post by anantgowerdhan on 2007-08-02
Hi,

I installed using Alternate Install CD and I got the same error.

I'm just being dropped to the Konsole and i get the same message

> apt-get is not installed, please install it using apt-get install apt.

I need help to get rid of this

Regards,
Anant

---

### Post by dabl on 2007-08-02
Usually that error is caused by a mis-match between the /etc/fstab entries for your devices and partitions, and the /boot/grub/menu.lst entries.  Are you trying to use an external drive or thumb drive or anything like that?

When you see the message, it might be possible to press Ctrl-Alt-Del and have it continue to boot.  But, you'll still have the problem that menu.lst doesn't match fstab, and you'll have to fix that.  :)

---

### Post by anantgowerdhan on 2007-08-02
I'm installing on EXT3 partitions which is already created by Mandriva. I'm formating "/" and "/home" partitions as well.

I did CTRL+ALT+DEL and it took me to the loging screen but after login it simply showed me one error message and took me back to the login screen

Regards
anant

---

### Post by dabl on 2007-08-02
If you can log in and use the computer in text mode, you can probably set up a VESA display, which is GUI, but won't use the full capabilities of your graphics card.  Once you've got a GUI, you can install a browser and research how folks have got your particular graphics card to work correctly.  Here's the VESA installation procedure: [http://kubuntuforums.net/forums/index.php?topic=3085112.0](http://kubuntuforums.net/forums/index.php?topic=3085112.0)

It's the same for Ubuntu, except instead of "kcontrol" you'll go to System>Administration>Preferences>hardware information (or something close to that ....)

---

### Post by ccalvinfowler@aol.com on 2007-08-03
did you use the server edition or what

---

### Post by Pumalite on 2007-08-03
If you want a graphical interface, after what dabl told you: sudo apt-get install gnome-desktop ( or KDE-desktop). BTW, after configuring your xorg: startx

---

### Post by anantgowerdhan on 2007-08-03
Hey Gyus, 

Come on, I think you are not understanding my problem.

**apt-get is not installed** this is the error I'm getting after each installation. I thought, there could be something wrong with the apt-get but its not at all letting me enter into the system. Means KDE/GNOME/XFCE nothing installed properly.

Mr. pumalite, if apt-get is not installed, whether will I be able to rum apt-get command as superuser? NO

It clearly says > apt-get not installed, please install apt-get install apt...................what a crap 

regards,
Anant

---

### Post by dabl on 2007-08-03
Try a Ctrl-D when you see that message.

---

### Post by anantgowerdhan on 2007-08-03
Hi,

I did CTRL+ALT+DEL, and it shows me the login screen but after login in it says KDE is not configured.

I'm back to mandriva and I'm not willing to intall Ubuntu sooner, but I really want to know why is that problem there? why the apt-get does'nt install after each installation, even though I'm not receiving any error message while installation.

I used to believe Ubuntu is the best distro, from others but my experience putting it somewhere down because its installation process is not as mature as Mandriva or Dreamlinux........if it doesnt install apt-get

Regards,
Anant

---

### Post by ccalvinfowler@aol.com on 2007-08-06
When you boot, press esc so that you can get to the GRUB 

Go to Revovery mode and fix all errors.

 Then try to restart.

 I had the same problem last night and that is what i did to resolve it

---

