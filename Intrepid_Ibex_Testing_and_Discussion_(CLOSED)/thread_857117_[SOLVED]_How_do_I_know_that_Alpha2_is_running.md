---
title: "[SOLVED] How do I know that Alpha2 is running ?"
date: 2008-07-12
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Kevbert on 2008-07-12
I've just performed a distribution update (3.6/3.9) on Alpha1.  During the update it asked whether I want to update grub with the latest new boot loader (which I declined as I have other OS).  When I booted only the -2 kernel was displayed (not -3 as expected).  Am I running Alpha2 ?  I'm running KDE 4.1 beta2 according to an About window.  Is there any terminal command that I can use to confirm this as 
```
lsb_release -a 
```
only shows my OS as being 8.10 ?

---

### Post by plun on 2008-07-12
Please take a look at this tutorial.

Gui is for Ubuntu

[http://ubuntu-tutorials.com/2007/01/27/how-to-find-your-ubuntu-or-kernel-version/](http://ubuntu-tutorials.com/2007/01/27/how-to-find-your-ubuntu-or-kernel-version/)

From Cli

The other method to find your version is a command line method. There are two commands you can use:

```
    cat /etc/issue

```
or you can use

```
    cat /etc/lsb-release
```

&#8230;and finally to find your kernel version and a few more details about your machine use the uname command which, per the man pages, shows system information. Examples:

```
    uname -a : print all information

    uname -r : print the kernel release

    uname -v : print the kernel version

    uname -o : print the operating system
```


EDIT

And no updates available for install....

Alpha 2 is just a "snapshot" from Intrepids repo.

---

### Post by Kevbert on 2008-07-12
Both cat commands only show I'm using 8.10.
Uname responses:
```
uname -v
#1 SMP Thu Jun 19 15:49:49 UTC 2008
uname -a
Linux knm-dt1b 2.6.26-2-generic #1 SMP Thu Jun 19 15:49:49 UTC 2008 x86_64 GNU/Linux
uname -r
2.6.26-2-generic
uname -o
GNU/Linux
```
So does this mean I'm not using the latest Alpha release ?
If not how can I reset grub to include the new kernel ?
If I use
```
sudo apt-get dist-upgrade
```
I get no new packages updated, upgraded or installed.  I previously had 63 packages held back (mainly display drivers) and now I have none.
Thanks (sorry to be a bit of a pain).

---

### Post by plun on 2008-07-12
> **Kevbert said:**
> 
So does this mean I'm not using the latest Alpha release ?
If not how can I reset grub to include the new kernel ?
If I use
```
sudo apt-get dist-upgrade
```
I get no new packages updated, upgraded or installed.  I previously had 63 packages held back (mainly display drivers) and now I have none.
Thanks (sorry to be a bit of a pain).

Ok... well, this is not so easy.  

You are also on Kubuntu with several threads about severe trouble

What gives this command

```
sudo apt-get install linux
```

"linux" is the meta package for latest kernel

Description
[http://packages.ubuntu.com/intrepid/linux](http://packages.ubuntu.com/intrepid/linux)

The metapackage for kde4 is now kubuntu-desktop for Intrepid

So output from this ?
```

sudo apt-get install kubuntu-desktop
```

Description:
[http://packages.ubuntu.com/intrepid/kubuntu-desktop](http://packages.ubuntu.com/intrepid/kubuntu-desktop)


And ask and ask.... we have several kubuntu users which also can help you... :)


EDIT

Just a check, do you also update  ?
```

sudo apt-get update && sudo apt-get dist-upgrade
```

---

### Post by Kevbert on 2008-07-12
The following were installed with
```
 sudo apt-get install linux
```
```
Get:1 http://gb.archive.ubuntu.com intrepid/main linux-image 2.6.26.3.4 [2168B]
Get:2 http://gb.archive.ubuntu.com intrepid/restricted linux-restricted-modules 2.6.26.3.4 [2186B]
Get:3 http://gb.archive.ubuntu.com intrepid/restricted linux 2.6.26.3.4 [2180B] 
```
The reply to
```
sudo apt-get install kubuntu-desktop
```
was 
```
The following packages were automatically installed and are no longer required:
  libdns42 libqt4-core djview4 libqt4-gui djvulibre-plugin
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```
I've autoremoved and I'll let you know what happens after I've rebooted.

---

### Post by Kevbert on 2008-07-12
I've performed a reboot and still only get the -2 kernel displayed (not 3.4).  I've checked the version via terminal and uname and it still says -2.
By the way, when I did a distribution upgrade I ran
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```
in that order.
Thanks in advance.
Kevin.

---

### Post by plun on 2008-07-12
> **Kevbert said:**
> I've performed a reboot and still only get the -2 kernel displayed (not 3.4).  I've checked the version via terminal and uname and it still says -2.
By the way, when I did a distribution upgrade I ran
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```
in that order.
Thanks in advance.
Kevin.


Well, I have no clues except if we have Grub bugs for the moment.
There was also late changes within initramfs.  updategrub maybe  :confused:

Something is nevertheless strange with KDE4.


Just a note about "autoremove", be careful !!! and write down package names if you perform a removal.  You can then easily install them again if
it was wrong.   The same with all removals with Apt.

Packages can easy be checked with Ubuntus package database, **search engine directly in Firefox 3 to Ubuntus repo**


Hopefully someone else can add more about this challenge..!

---

### Post by xebian on 2008-07-12
> **Kevbert said:**
> I've just performed a distribution update (3.6/3.9) on Alpha1.  During the update it asked whether I want to update grub with the latest new boot loader (which I declined as I have other OS).  When I booted only the -2 kernel was displayed (not -3 as expected).  Am I running Alpha2 ?  I'm running KDE 4.1 beta2 according to an About window.  Is there any terminal command that I can use to confirm this as 
```
lsb_release -a 
```
only shows my OS as being 8.10 ?

Because you declined, it means you have to edit manually your grub menu to include/or change the kernel line.  You can still do an update by executing 
```
sudo update-grub
```
It saves a backup, but to be sure save one yourself before doing so.

BTW, to confirm what kernel versions are installed do 
```
ls -al /boot 
```

---

### Post by Kevbert on 2008-07-12
> **xebian said:**
> You can still do an update by executing 
```
sudo update-grub
```
Not required as already installed.
BTW, to confirm what kernel versions are installed do 
```
ls -al /boot 
```
The kernel was already installed, it just wasn't displayed as shown by this command.
Thanks for all the help.

---

### Post by xebian on 2008-07-12
> **Kevbert said:**
> The kernel was already installed, it just wasn't displayed as shown by this command.
Thanks for all the help.

I'm not sure you got my post.  The 'update-grub' command is to update the grub menu with the new installed kernel so it can be displayed as one of the choices.

---

### Post by Gina on 2008-07-12
Not running "Update GRUB" means the menu.list won't be updated to the new kernel.  Update GRUB won't affect other OSs in the list - it only touches the current kernel entry - in fact it leaves the original and simply adds two lines - the normal kernel and the recovery mode.  It's perfectly safe to let the updater run update grub.

---

