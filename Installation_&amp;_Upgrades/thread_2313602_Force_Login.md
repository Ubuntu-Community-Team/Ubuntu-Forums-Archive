---
title: "Force Login"
date: 2016-02-14
forum: Installation &amp; Upgrades
---

### Post by woodsyboredom on 2016-02-14
I tried to upgrade to 15.10 and there was a power failure. now I have 15.10 on my computer and I know there are some errors that need fixing. all I get on my monitor after the boot attempt is two  lines of text that read thus:

Ubuntu 15.10 woodsy-Dell-DXP061 tty1

woodsy-Dell-DXP061 login:


I can't for the life of me remember the correct login. I've tried to make a USB boot drive but that fails. I had this problem with my laptop once but I could remember the login. Is there someway to find my login or somehow bypass it so that I can run some command line fixes. I'm sure they will work if I can just get beyond the Login. 
the drive. 


THANKS. WOODSY

---

### Post by Bucky Ball on 2016-02-14
If you have only just installed then might be just as easy to re-install and write down username and password. Then you'll have no power cuts, the right username and password, and hopefully a stable install from go. 

The USB drive issue is for another thread. Please edit and post one about it if you're after support with it.

Good luck.

---

### Post by steeldriver on 2016-02-14
You should be able to use this procedure to set a new password from recovery mode

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by woodsyboredom on 2016-02-15
> **steeldriver said:**
> You should be able to use this procedure to set a new password from recovery mode

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

thank you. I was hoping this would work but alas. Booting in recovery mode only allows me to see a bunch of system checks and library and file loads. I just end up with the login screen. I never get to the screen where I can choose root. Is there a way to change or access one's username in Grub? I can get to a grub command line but I very unfamiliar with grub commands.

---

### Post by lisati on 2016-02-15
> **woodsyboredom said:**
> thank you. I was hoping this would work but alas. Booting in recovery mode only allows me to see a bunch of system checks and library and file loads. I just end up with the login screen. I never get to the screen where I can choose root. Is there a way to change or access one's username in Grub? I can get to a grub command line but I very unfamiliar with grub commands.

The login message in your first post isn't from Grub, it's from a text-mode startup of Ubuntu. You'll need to choose "recovery mode" before you get anywhere that prompt. If you don't get a choice of what you boot into before the prompt appears, you'll need to reboot and hold down the shift key.

---

### Post by woodsyboredom on 2016-02-16
> **lisati said:**
> The login message in your first post isn't from Grub, it's from a text-mode startup of Ubuntu. You'll need to choose "recovery mode" before you get anywhere that prompt. If you don't get a choice of what you boot into before the prompt appears, you'll need to reboot and hold down the shift key.

I know. I go to a screen that has some boot options: Ubuntu; Advanded Ubuntu Options; Memory test; another Memory test; a Dell partition set up thingy. I choose Advanced Ubuntu Option and I go to a new screen that has a bunch of Ubuntu options; Ubuntu, with Linux 3.13.0-78-generic; Ubuntu, with Linux 3.13.0-78-generic (recovery mode); Ubuntu with Linux 3.13.0-77-generic; etc., etc. with and option for recovery mode with each kernel change. When I choose recovery mode (any of them) it boots up but instead of doing it with a blank screen and the spinning Ubuntu icon, I seen a bunch of script lines, (starting this, running that, Dell mouse support ok) all sorts of stuff and then it dumps me back to the text mode startup page. The dialogue box with the Root choice option never appears to me. Are there any other routes to the password page?

---

### Post by MAFoElffen on 2016-02-16
Along the lines that you have physical security of you own machine and are not trying to break into something that is not your own...

2 other ways... Since it was upgrading when you lost power, then the latest version of the kernel is most likely the one that was interrupted before it finished. So sounds like it is broke.

At the boot menu, go back one-to-two kernels back and select the recovery menu option.

If that one is still broke, then go to my Graphics Resolution  sticky in my sigline > Got to the first half of the 3rd post and follow the directions to mount the installed filesystem and chroot into it from a LiveCD. Then change your user password. (you will already be root.)
```

passwd woodsy

```
While chrooted, you might as well finish fixing it
```

apt-get update
agt-get install -f
apt-get clean
apt-get dist-upgrade

```
And follow any other recommendations that it prompts you to do...

---

### Post by woodsyboredom on 2016-02-17
My problem remains unsolved. it's all booting correctly but I need to know my login and I cannot figure out what it is or how to discover or force it. I followed all instructions from all of you nice people but it does't matter which kernel I use, whether in recovery mode or not, I end up with a screen that says Ubuntu 15.10 woodsy-Dell-DXP061 tty1 (or tty2-6) and then two lines down woodsy-Dell-DXP061 login and that is it. I can't seem to get anywhere else. I can get  into a grub edit screen but nothing that I do there fixes it. I seem to have some sort of problem making a bootable usb stick (it's formated for fat32 but still fails everytime) so booting from a live usb is not an option as yet. I know what the Password is because I've only ever used one specific one for all of my computers. I just can't remember the login and I can't get past that part.

---

### Post by Geoffrey_Arndt on 2016-02-17
Recently, I've also experienced substantial difficulties in creating a live usb-flash stick in Ubuntu Wily (15.10).   Have done it dozens of time in past (especially with 14.04 LTS) . . . so, there could well be issues with 15.10 & unetbootin, startup disk creator, etc.    So . . . . do you still have working optical drives where you can (on another pc), download and create a Live DVD and re-install from that???

---

### Post by lisati on 2016-02-17
It's odd that when you choose " Linux 3.13.0-78-generic (recovery mode)" you are given a login prompt similar to what you described earlier. On my system, I'm given further options, including resuming normal boot, trying to fix broken packages, cleaning up space, and dropping to a command-line prompt (which shouldn't need a login/password).

---

### Post by woodsyboredom on 2016-02-17
Halleluja! I remembered my login! now I just need to run the repairs to the upgrade which are fairly easy. Whew! Thank you all for trying to help and for listening.

---

### Post by woodsyboredom on 2016-02-17
Done.

---

### Post by Bucky Ball on 2016-02-17
Excellent news. Please see the first link in my signature and mark as solved officially. Enjoy! ;)

---

