---
title: "receiving &quot;command not found&quot; error messages after fresh reinstall of Lubuntu 14.04"
date: 2014-06-02
forum: Installation &amp; Upgrades
---

### Post by roler2 on 2014-06-02
Lubuntu 14.04 was working really great. . .until I messed up and had to do a complete fresh reinstall.

Now I receive error messages when I input commands into the Terminal, even after immediately completing the fresh install.

For example I type:

sudo leafpad &#8236;/etc/default/

or sudo leafpad &#8236;/etc/default/grub

I get:

sudo: leafpad: command not found

I type:

sudo update-initramfs &#8236;-u

or sudo update-grub

I get:

sudo: update-initramfs: command not found

or sudo: update-grub: command not found

If I use the command mkdir I get:

mkdir: command not found

I also get this same exact error message, command not found, with sudo apt-get and wget

In other words I can't do anything that I was able to do when inputting commands into the terminal.

So I cannot add any repositories or update anything at all. I am not really sure what is causing the problem(s).

It appeared to me that Lubuntu installed and booted up OK. However just as soon as I enter anything into the Terminal I immediately get the above error messages. I have tried to do the reinstall three times, same error messages.

If anyone can suggest any fixes I would really appreciate it very much. Thank you!

---

### Post by sudodus on 2014-06-02
It seems to me that you have a borked or incomplete installed system. You can check if the HDD is good with the S.M.A.R.T. information. It is available from the BIOS/UEFI menus or via smartctl when you have installed ***smartmontools***.
```

sudo smartctl -H /dev/sda
```
or to get more information
```
sudo smartctl -a /dev/sda
```

See man smartctl for more details.

If the HDD seems OK, I think the easiest way is to reinstall the system (easier than to to to repair it).

---

### Post by roler2 on 2014-06-03
I will re-download and re-burn to disc. I wish Lubuntu would just have a pre-made CD. The hard drive appears to be in good shape. No bad sectors found and I also reformatted in DOS. It is going to take me a couple of weeks as I have to get to a computer that has fast Cable. I have DSL and it would take all night to download. I have an old P4 so I am not able to utilize S.M.A.R.T. however I did run tests and the hard drive showed to be in good condition.

---

### Post by sudodus on 2014-06-04
I'm glad your hard disk drive is in a good condition :-)

You can check your current Lubuntu iso file with md5sum. If it is correct there is no need to download it again.

If you still need to download a good iso file, well, then you have to wait until you get to a computer that has fast cable.

Burn the CD as slowly as possible. It is possible (from the grub menu) to check that the CD is good. With a Pentium 4 computer it should also be possible to create a boot USB drive from the iso file. It is often more reliable than to burn a CD. See this link

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by Bucky Ball on 2014-06-04
Just a point: You should be using 'gksudo' to launch a graphical interface, not 'sudo'. I.e:

```
gksudo leafpad
```

If you type in just 'leafpad' to the terminal, does it launch or you get the 'command not found' error? Can you open leafpad from the apps menu (rather than the terminal)?

---

