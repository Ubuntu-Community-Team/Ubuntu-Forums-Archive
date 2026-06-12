---
title: "Cannot install.  Cannot use Live CD"
date: 2014-03-11
forum: Installation &amp; Upgrades
---

### Post by javajeff1 on 2014-03-11
I installed a new video card, and now I can do nothing.  nvidia Geforce GTX 750 it.  Is this card too new?  When I try to install or go to the live CD, it hangs after the ubuntu animation starts.  Any ideas?

---

### Post by Bashing-om on 2014-03-12
javajeff1; Hi !

What results when you attempt to boot by a "recovery" kernel from the grub boot menu ?

Maybe from the recovery console, option "with networking" -> resume normal boot -> desk top -> Additional Drivers; and install the recommended driver ?

[INDENT]just try'n to help
[/INDENT]

---

### Post by grahammechanical on 2014-03-12
If you are trying to run a live session you can try this:

1) At the first purple screen press Enter.
2) At the language selection screen select the language (the default is English) and press Enter.
3) At the screen that offers you options to Try Ubuntu - Install Ubuntu and other options, press F6
4) At the bottom right of the screen a small drop-down menu will appear. Select nomodeset and press Enter.
5) Press Esc to get back to the Try Ubuntu - Install Ubuntu screen. Make sure that Try Ubuntu is chosen and press Enter.

Does that get you to a live Ubuntu desktop session? You may need to try a combination of those F6 options.

We can install Ubuntu from a live Ubuntu desktop session. During the installation process you will be asked if you want to install third party software. My advice is to not tick that box.

When the installation process is finished you will need to reboot. If that reboot gets you to a desktop then you can do two more things.

1) Open Ubuntu Software Centre and install Ubuntu Restricted Extras. That will get you the third party software that was not installed during the installation process.

2) Depending on whether you are using Ubuntu 12.04 or 13.10 (it helps us to know and you have not told us) you can stay with the Nouveau open source video driver if that gives you an acceptable user experience or activate a proprietary video driver using the Additional Drivers utility.

But first you need to get Ubuntu installed and working.

Regards.

---

### Post by javajeff1 on 2014-03-12
Thank you all that responded.  My USB thumb drive is the latest version of Ubunutu, 64 bit 13.10.  Here is what I have done so far.  I had Mint 16 already installed, but could not boot to it either.  At Grub, I hit e and added nomodeset xforcevesa to the Linux line so I could boot.  Then I added this to Grub config GRUB_CMDLINE_LINUX_DEFAULT="nomodeset xforcevesa" so I could continually boot in software rendering mode.  I cannot install the latest nvidia drivers from the nvidia website.  I get an error stating that it cannot install because xserver is running.  I cannot go into hardware and see any available drivers.  I am thinking about a fresh install of Ubuntu to see if I can get it going.  Is my card too new for this kernel?

---

### Post by Bashing-om on 2014-03-12
javajeff1; Hey ,

With only a limited amount of investigation it presently, to me, does appear that you require the x86_64-334.21.run driver that is only available from the Nvidia web site.
This link has the instructions to install the driver for your graphics card.
[http://askubuntu.com/questions/425140/unable-toboot-with-nvidia-gtx-750-ti-even-with-latest-beta-drivers](http://askubuntu.com/questions/425140/unable-toboot-with-nvidia-gtx-750-ti-even-with-latest-beta-drivers)

Included in these directions are the instruction on how to stop the xserver to install the driver.


[INDENT]I help little
[INDENT][INDENT]but point you to where there is better help
[/INDENT][/INDENT][/INDENT]

---

### Post by javajeff1 on 2014-03-12
Thanks, that is really awesome.  I am glad to see that I am not the only one.

---

### Post by Bashing-om on 2014-03-12
javajeff1; Yuk !

Returning the card is a bummer, as that is a fairly decent gamer's card. Just Too new for the driver to have trickled down to the linux repositories !

If your desk top is unity -> to stop xserver (for future reference):
```

sudo service lightdm stop

```

As this situation is now concluded, please mark this thread as solved as this aids others and helps keep the forum tidy.

[INDENT][INDENT]other days
[INDENT][INDENT][INDENT]other problems
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by javajeff1 on 2014-03-12
Actually, I only printed the return label tonight.  I am going to try to do a fresh install one more time.  I was actually concerned that the card was defective since I had trouble finding any posts on it.  Also, the card it is replacing is an ATI HD 6850 which performs well.  My goal was to go nvidia to play some games in Linux

---

### Post by javajeff1 on 2014-03-13
Did a fresh install of Ubuntu with the new card, and I cannot follow the instructions.  Ctl-Alt-F1 does not work as it goes to a black screen.  I have no way to stop the xserver to install the drivers.  I also had the same issue when I had Mint installed.  The solution I found on the internet was to install the nvidia drivers to solve the black screen issue.  :P  STUCK IN SOFTWARE RENDERING.  ARRRGGGG!

---

### Post by nibal on 2014-03-13
> **javajeff1 said:**
> Did a fresh install of Ubuntu with the new card, and I cannot follow the instructions.  Ctl-Alt-F1 does not work as it goes to a black screen.  I have no way to stop the xserver to install the drivers.  I also had the same issue when I had Mint installed.  The solution I found on the internet was to install the nvidia drivers to solve the black screen issue.  :P  STUCK IN SOFTWARE RENDERING.  ARRRGGGG!

That is not a black screen. That is a very useful terminal, for when you cannot use the Xserver. In fact it is tty1 (there are 6 of those with the <ctrl><alt><F1-6> keys). <ctrl><alt><F7> will return you to Xwindows.
You can do much more in a terminal, than in an X environment. I have not read the nvidia instructions. But if you login with your user/pass, you will get a shell. From there you can install packages with

```


sudo apt-get install <package>


```

or if you already have downloaded the nvidia driver from their site you can type:

```


sudo dpkg -i <package>

```

 You can even compile it, if it is in sources.

Terminals can be your best friend, so I suggest to get used to them. :)

Let me suggest another procedure if you feel uncomfortable working with terminals:

Boot with the live CD. Select "Try Ubuntu". After a while it will get you to Xwindows (from the CD). Open a terminal and type:

```

sudo mount <root partition> /mnt
sudo mount --bind -t proc /proc /mnt/proc
sudo mount --bind /dev /mnt/dev
sudo mount --bind /sys /mnt/sys
chroot /mnt

```

where <root partition> is your "/" filesystem (i.e. /dev/sda7)
You are now root on your installation (no need for sudo ;-)
Go to where you have downloaded your nvidia driver and install it as if you do not have an Xserver (except that you have one, running from the CD)
If you don't have the driver, type:

```

exit

```

to return to your CD environment, donwload it with a browser and sudo copy it to /mnt/. chroot again and go install it. 
This is a very useful procedure if you have problems with your boot loader. You should install Ubuntu just once. Then you can fix (almost) anything. 
But that's another thread.

HTH,
Nikos

---

### Post by javajeff1 on 2014-03-13
Hi, I got the drivers installed.  YAY!  The black screen had no terminal input options, but a reboot got me to it.  I decided to stick with Mint until the new Ubuntu in April, so anyone else following this can use mdm instead of lightdm to stop the service with Cinnamon.  Thank you to everyone that contributed to this post.

---

### Post by nibal on 2014-03-13
> **javajeff1 said:**
> Hi, I got the drivers installed.  YAY!  The black screen had no terminal input options, but a reboot got me to it.  I decided to stick with Mint until the new Ubuntu in April, so anyone else following this can use mdm instead of lightdm to stop the service with Cinnamon.  Thank you to everyone that contributed to this post.

Sorry, I missed completely your topic "Cannot use live CD". I don't think that a different dm is your problem. Video card is not a module any more, it is part of the kernel. Best ask nVidia about it.

---

### Post by Bashing-om on 2014-03-13
javajeff1; Great !

You are doing good. Pleased you are up and running .

As this matter is now concluded, please mark this thread solved - aids others seeking a similar solution and helps keep the forum tidy.
Feel free to open as many additional threads as needed for you to become comfortable with your operating system. We are here to help.


@ nibal; appreciate your participation and worthy input in this thread, three heads are always better than just 2 ! I look forward to other adventures.

[INDENT][INDENT]no one was born knowing ->
[INDENT][INDENT][INDENT]it is all a matter of learning
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by javajeff1 on 2014-03-13
Done!  This community is awesome!

---

### Post by Bashing-om on 2014-03-13
:d

---

