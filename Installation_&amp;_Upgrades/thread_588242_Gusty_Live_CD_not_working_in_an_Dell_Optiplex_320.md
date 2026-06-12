---
title: "Gusty Live CD not working in an Dell Optiplex 320"
date: 2007-10-23
forum: Installation &amp; Upgrades
---

### Post by jofre on 2007-10-23
Hi everyone,

My newly burn 7.10-Desktop-64amd, (or Gusty) is not going live...

I get the initial menu ok, the splash screen appears ok, and then after a bit, blank, and nothing.

System: Dell Optiplex 320

Any ideas?

I tried aswell with the safe graphics mode, same result.

Thnaks in advance,
Jofre.

---

### Post by jofre on 2007-10-31
I see that there is no many suggestion...

Is the situation so hopeless?

I am tempted to do a fresh installation of 7.04, and then upgrade from there.

---

### Post by evilc on 2007-10-31
Have you checked the disk for errors? Sometime the 'burning' overruns and you end up with a coaster.:)

---

### Post by jofre on 2007-10-31
Thanks for trying...

Yes I did. 
I read that seems to be a bug with ATI cards, but I can't even switch to another terminal.

Also when I try with safe graphic mode, the screen complains and says that the display mode is not supported and I can not switch to another terminal either.

It is a bit strange...

---

### Post by jofre on 2008-01-10
Just to be a bit annoying...

I left the probelm aside, but know I want to try again to install gusty in my optiplex 320,

any ideas?

---

### Post by ikman on 2008-01-10
I have a Dell Optiplex 320 w/ 2 GB RAM, 150GB HDD, Celeron, etc., And can't boot the live CD either.

When I first try to use gparted livecd to shrink the Windows partition I get this error:

[   42.485593] PCI: Cannot allocate resource region 1 of device 0000: 00: 14.0 

The CD verified good.

When I gave up on the gparted live cd and booted with the known good gutsy livecd I got the splash screen ubuntu with the menu. I tried the default first option and the check disk option. Both options locked up with an "underline" cursor displaying almost immediately after blanking the menu screen. There was also an error saying something about resource or something. (It sounded close enough to the above error that I didn't write it down.)

Maybe this can help supply a few more details to our problem.

Thanks, 

ikman

---

### Post by paisleysdaddy on 2008-01-10
I have this same problem trying to install on an Optiplex 320. I can boot with the live cd and run that, but when I try to install, it just goes to a blank screen after installing. I also have problems with the 320 when trying to use some versions of Ghost software, where I came to the conclusion that the SATA hard drive was not supported. I'm wondering if this may be the same issue trying to use 7.10 on these machines.

---

### Post by ixfnak on 2008-04-22
At the installation screen try hitting F6 and adding the following boot parameter:

hpet=disable

I have seen a lot of potential solutions relating to this hardware, but this one is the only one I have noted that really does anything. You can read about what hpet is here:

[http://en.wikipedia.org/wiki/High_Precision_Event_Timer](http://en.wikipedia.org/wiki/High_Precision_Event_Timer)

If you decide to go ahead and install the system, I suggest amending the boot parameters as such:

[keep the others that were there] priority=medium -- hpet=disable

priority=medium enables more control over the installation process.

NOTE: It is important that hpet=disable is AFTER the -- so that it is saved as a boot parameter in the installed system. To learn more about this, see the installation help documents on the boot CD:

/cdrom/docs/install/manual/en/apbs02.html#preseed-bootparms

NOTE: It is critical to install the lilo boot loader instead of grub, which is the next to the last step. I have had no luck installing grub2. If you don't install lilo there, you will need to go through a painful process of rebooting from the live CD, remounting various file systems, setting up a chroot environment, installing lilo, and configuring lilo before rebooting, which I won't detail here.

If you installed an optional ATI X1100 graphics card with the system and to get the full use of the card (higher resolution and 3d acceleration), run the following from a console window after completing the installation and logging into a new X-session:

sudo dpkg-reconfigure xserver-xorg

You need to select the fglrx driver where prompted, Otherwise, you will probably do well accepting the defaults for the other options.

Log out, then, restart your X-Server:

Ctrl-Alt-Backspace

The new driver should work.

---

