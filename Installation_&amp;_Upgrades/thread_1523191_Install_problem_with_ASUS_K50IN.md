---
title: "Install problem with ASUS K50IN"
date: 2010-07-03
forum: Installation &amp; Upgrades
---

### Post by Zipstor on 2010-07-03
Hi there,

I'm trying to install ubuntu-10.04-desktop-i386.iso on my laptop, it's 6 month old.

The problem occurs a few seconds after booting on cd. I can see the Ubuntu logo, its loading and then there is a display bug, something like resolution mismatch, therefore I cannot see anything so the install stops there.

It's strange to me because an os install should be on low res 640x480 vga16 and any machine can reach this.

Any ideas?

Booting:
[IMG]http://hydroxygas.com.au/temp/ABCD0010.JPG[/IMG]

and then...
[IMG]http://hydroxygas.com.au/temp/ABCD0011.JPG[/IMG]

---

### Post by Zipstor on 2010-07-03
still need help thanks

---

### Post by Egor Tensin on 2010-07-08
Hi Zipstor!

I had the same problem installing Ubuntu 10.04 on my Asus K50IN.
I solved it this way:

1) Enter GRUB boot menu (by pressing Shift after Asus logo image).
2) Edit (AFAIR, hotkey 'e', but there is hint message anyway) proper boot line (the one on the top, I guess) by adding " nomodeset" argument.
3) Press <Ctrl>+<X> to boot into your Ubuntu installation.

This allowed me to log in successfully. To avoid editing GRUB menu every time, I edited /etc/default/grub by setting GRUB_CMDLINE_LINUX value to "nomodeset" and ran "sudo update-grub".

---

### Post by Zipstor on 2010-08-09
Egor thanks for your reply.

I have tried once again and did what you told me. I pressed shift to get to to that GRUB menu and nothing happened.

Keep in mind that I'm still a complete newbie to Linux related stuff. Can you try to be a bit more specific?

Thanks a dozen.

z:/

---

### Post by Zipstor on 2010-08-09
[...]

---

### Post by Zipstor on 2010-08-09
I finally managed to get into the Installer boot menu but cant find where to edit a boot line.. There is a command line down the bottom however have no clue how to get to that file i have to edit. Any help still welcome at this stage.

---

### Post by Egor Tensin on 2010-08-12
Oops, I thought you have already installed Ubuntu and are having troubles booting into your fresh installation. Sorry, I haven't read your initial post with enough attention.

What about booting Live CD session, it's all pretty simple:
0) Make sure Ubuntu CD is in your drive and BIOS is set to boot from CD before booting from your hard drive (and it is by default, so you probably don't need to care). 
1) First, you need to press <F6> one or more times after ASUS logo to enter Live CD menu (I don't know why, but it doesn't appears by default since Lucid). Choose your preferred language.
2) There, press <F6> again to open menu with Live CD session booting options. Choose "nomodeset" option and press <Enter>. Exit menu by pressing <Esc>.
3) Choose the global menu first option (it's called "Boot live session from CD" or something like that).

I managed to boot into Ubuntu Live CD session after completing these steps.

---

### Post by Zipstor on 2010-08-13
Actually I made it to install Ubuntu with the live cd... Now this same bug appears when I boot up. So with the help of someone from irc I have added nomodeset onto the first line when you edit the boot (shift then e). It went ahead for a bit then the same bug appeared.. I heard a brief sound of tamtam, this means that my audio card is recognised ... at last!

Do you have msn or icq or are you on an irc channel somewhere? is so what is your time zone, i'm in Sydney Australia.

Thanks a dozen.

---

### Post by Jared Norris on 2010-08-14
According to the comments at [http://www.youtube.com/watch?v=nsWnozx8sn8](http://www.youtube.com/watch?v=nsWnozx8sn8) the following information should help you get it up and running.

To get to the command prompt:
-on the weird screen, hit Ctrl+Alt+F1
-login using the username & password you installed with

Then type the following 2 commands into the prompt:

```
sudo apt-get install nvidia-common nvidia-current
sudo nvidia-xconfig
```

Then
- kill xorg (get its pid using ps ax | grep xorg)

And then finally

```
startx
```

If this doesn't work have a look at the link there are another few ideas that are supposed to work as well.

---

### Post by Zipstor on 2010-08-15
okay so i got an error message when i try to open the prompt

[    16.877397] nForce2_smbus 0000:00:03.2 Error probing SMB2.

btw the prompt wont open

---

### Post by Jared Norris on 2010-08-15
For that problem [http://ubuntuforums.org/showthread.php?t=1483987](http://ubuntuforums.org/showthread.php?t=1483987) seems to have a solution for it that I would be trying in the first instance.

---

### Post by emil.kotsev on 2010-09-03
If your video card is NVIDIA the solution is simple:

When you boot and your screen become crazy all you have to do is:

1. CTRL + ALT + F5
2. Login as user
3. Become superuser: sudo su
4. You have to kill all X sessions: ps ax |grep gdm 
5. kill number of process
6. Download the nvidia driver: wget [http://uctm.edu/e/NVIDIA-Linux-x86-190.42-pkg1.run](http://uctm.edu/e/NVIDIA-Linux-x86-190.42-pkg1.run) ( I have uploaded it for you or you can download it from the Nvidia official site)
7. Give permissions to the file: chmod 777 NVIDIA-Linux-x86-190.42-pkg1.run
8. Run the file: ./NVIDIA-Linux-x86-190.42-pkg1.run

After you run the file you will be prompted for some options about the X11 conf and etc.
After you finish the installation "halt" the pc (when I hit reboot it bug so just hit halt and you are ready)

---

