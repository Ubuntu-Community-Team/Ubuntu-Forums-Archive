---
title: "installed alternate, can't boot after install"
date: 2007-03-02
forum: Installation &amp; Upgrades
---

### Post by craig2321 on 2007-03-02
Hi there. I installed kubuntu with the alternate install. The install went very smoothly, and I thought i was so close to having a linux system. But when I try to boot after the install, it starts up, I see the kubuntu logo with the loading bar and it's moving...but then it just stops and doesn't do anything, I left it on for a few minutes and still nothing. It won't boot into kubuntu. 

I know it has to be the generic graphic driver that's giving me problems. I noticed in grub, you can boot into recovery mode, or you can press "e" or whatever and get a standard boot but with some options.


I'm wondering, what command line options can i give in recovery mode (or elsewhere), that will allow me to bypass these generic drivers, and boot into kubuntu so that I can install the proper drivers for my card. Please help. Thanks.

---

### Post by taurus on 2007-03-02
Boot into recovery mode and run this command at the prompt.

```
dpkg-reconfigure xserver-xorg
```
Use default if you are not use what it's asking and use **vesa** for your graphic card.  Save the change and reboot.

```
shutdown -r now
```

---

### Post by ffxr on 2007-03-02
mmm u can do pretty much everything from the console... [but workin out the commands is another question.. ]
what graphics card have you got?
and do u have access to pc with an internet connection?

---

### Post by craig2321 on 2007-03-02
> **taurus said:**
> Boot into recovery mode and run this command at the prompt.

```
dpkg-reconfigure xserver-xorg
```
Use default if you are not use what it's asking and use **vesa** for your graphic card.  Save the change and reboot.

```
shutdown -r now
```

K i'll try that and post back with the outcome.


> **ffxr said:**
> mmm u can do pretty much everything from the console... [but workin out the commands is another question.. ]
what graphics card have you got?
and do u have access to pc with an internet connection?

I have an ati x800pro. I know Ati's aren't the greatest for linux, but i've never had a problem like this before. Yes I do have access to a pc with an internet connection.

---

### Post by ffxr on 2007-03-02
that x800 issue should get a sticky ; s)

see here if your still having problems following taurus' advice : [http://www.ubuntuforums.org/showthread.php?t=367358&highlight=x800](http://www.ubuntuforums.org/showthread.php?t=367358&highlight=x800)

---

### Post by craig2321 on 2007-03-02
Ok, i did the reconfigure, and selected vesa..and...IT WORKS!! thanks. Now i just have to get the drivers installed and working.

I think it gave me problems because, my graphics card (connect3d x800 gto)...only came with 12 piplelines. Theres a way to unlock the other 4, so now my x800 has 16 pipelines maybe that's why it's not recognized by the default ati driver thing. I don't know. Anyways, thanks.

---

