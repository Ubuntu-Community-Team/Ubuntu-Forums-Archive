---
title: "Running Ubuntu Studio after installing it aside Vista"
date: 2008-11-19
forum: Installation &amp; Upgrades
---

### Post by yonyz on 2008-11-19
Hi,

I've just installed Ubuntu Studio 8.10.
I already have Vista installed in a different partition.

I followed the Ubuntu Studio installation wizard, and then selected to install the Ubuntu Studio Desktop software,
because it says "must install".

At the GRUB selection at system boot, I waited a few seconds for it to automatically select Ubuntu Studio, the first option (there are 3 options for Ubuntu Studio).

So it asked me for main login and password, and it worked, and then nothing happened,
there was just something written about Ubuntu's website and something that looks like "yonathan@Main:~$"

"yonathan" is the login name, and "Main" is the host name.

What's wrong?
Why it doesn't start and show a desktop?

This my first attempt on using Linux.

Thanks in advance.

---

### Post by snowpine on 2008-11-19
Hi Yonyz,
Welcome to the forums! yonathan@Main: is the Linux command line. It is a good sign that you got that far, now all we need to do is get you to a graphical desktop!

My first suggestion? Try typing 'startx' (without the quotes). Does that work? (X is the basic graphical desktop and startx starts it.)

---

### Post by yonyz on 2008-11-19
Here's what is being showed to me after I write "startx" and press Enter:

> The program 'startx' is currently not installed.
You can install it by typing:
sudo apt-get install xinit
-bash: startx: command not found

So I wrote "sudo apt-get install xinit", pressed Enter and it replied:

> Reading package lists... Done
Building dependency tree
Reading state information... Done
Package xinit is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, 
or is only available from another source.
However the following packages replace it:
x11-common
E: Package xinit has no installation candidate

And now I get the opportunity to command it again:
> yonathan@Main: ~$


---

### Post by snowpine on 2008-11-19
I think the easiest thing for you to do at this point is to install the (non-Studio) Ubuntu desktop. This will NOT erase all of the multimedia apps that you (presumably) installed with Studio, no worries. 

```
sudo aptitude install ubuntu-desktop
```

The install will take a while, but should give you a full graphical desktop environment. When the install is complete, reboot the computer, and with any luck, will see the graphical login screen.

---

### Post by yonyz on 2008-11-19
Actually, I didn't install anything in addition to Ubuntu Studio Desktop software,
because the installation allows me to select only one, and I assume
you can add whatever you want after the operation system install.

I've also read somewhere on the net that it's possible to install Ubuntu Studio over Ubuntu Desktop, and so I'll do.

---

### Post by snowpine on 2008-11-19
You are correct. Once the Ubuntu install is complete, you can open the Synaptic Package Manager (in the System menu, or 'gksu synaptic' from the terminal) and search for 'ubuntustudio'. You'll see about a half dozen metapackages for adding the audio, video, etc. apps. Good luck, ask if you get stuck!

---

### Post by yonyz on 2008-11-19
I will. Thank you.

---

### Post by yonyz on 2008-11-20
I've installed Ubuntu 8.10, and it works.
Problems that I need to fix:

I don't have an internet connection, and don't know how to install my wireless network adaptor on Linux.
I also don't even know if there's a Linux version of it.

When I will have an internet connection, I will be able to download and install drivers for my audio and graphics cards.

I will also be able to download and install codecs for playing MP3 and MPEG4 encoded files.

Of course, I don't have any of the Ubuntu Studio version's programs installed.

---

### Post by yonyz on 2008-11-20
bump.

---

### Post by snowpine on 2008-11-20
You should find out which wireless adaptor you have and use the search function and/or start a separate thread with a descriptive title.

If there is no Linux driver, you can use a program called ndiswrapper to use the Windows driver instead. It is really no big deal, but the instructions are specific based on exactly which card you have.

Once you're online, open a terminal and type 'sudo apt-get install ubuntu-restricted-extras' to get all the codecs.

---

### Post by yonyz on 2008-11-22
Apparently I can't boot into Vista.
When I select it with the GRUB bootloader, I can see Vista loading (that loading bar..) and then the computer restarts. 

What should I do?

Snowpine, I've started a new topic regarding networking on Linux.
Please take a look, maybe you can help:
[http://ubuntuforums.org/showthread.php?p=6230310#post6230310](http://ubuntuforums.org/showthread.php?p=6230310#post6230310)

---

### Post by yonyz on 2008-11-22
OK, so I need to re-install the Windows Vista MBR.
I can do this by using the Recovery Console, which can be accessed with the Vista installation DVD, but unfortunately the Vista installation DVD can't find any operating systems installed in my computer,
so I can't access the Recovery Console.

Any suggestions?

---

### Post by namten on 2008-11-22
I used this to dual boot..  This being my first hour or so using linux.. 

[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=4](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=4)


It says -This puts the Vista bootloader back into the MBR, but the machine will only boot into Vista. 

I haven't finished this step (wasn't going to) but maybe it will work for you?

---

