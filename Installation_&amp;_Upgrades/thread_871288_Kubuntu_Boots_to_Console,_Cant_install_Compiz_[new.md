---
title: "Kubuntu Boots to Console, Cant install Compiz [newbie]"
date: 2008-07-26
forum: Installation &amp; Upgrades
---

### Post by ghost2 on 2008-07-26
Ok, I'll try to keep this short, but attention to detail might make that impossible :) :

My current system is a 2.2 ghz P4 with 1024 Mb of ram and a BFG nVidia GeForce 7800 GS OC video card.  I currently have two harddrives, a 250 Gb seagate, and a 120 Gb WD.  I have XP Pro (My primary OS) installed onto the 250 Gb drive, and the 120 Gb has recently been installed with Kubuntu 8.04.

Now the 120 Gb was a leftover from when I upgraded to a larger drive (the 250 Gb), and for a while I used it as backup storage.  After a while I decided I would try to set up a dual boot with linux.  I tried the Fedora Distro twice, before giving up both times, mainly because of difficulties with the wireless card I was depending on at the time, and the complete inability to get ndiswrapper working.  So I cleared the drive, found some way to remove grub, and everything went back to the way it was.

Fast forward to about a week ago, where I decided to give linux another shot.  I decided to try ubuntu, and wanting a 'less bubbly looking' window manager, I decided to go with KDE4, in the form of kubuntu 8.04.

After playing with it for a while, and several web searches/reboots, I figured out apt-get and managed to install firefox, flash plugin, alien (to convert install packages), and some grub configurator (I forget it's name, but I know its mainstream, and begins with a 'k').

Everything was running (fairly) fine for a while, but then I wanted to get a more advanced-looking window manager with decent effects.  Did a little research, and settled with compiz.

In order to set it up right, I followed their instructions for upgrading my nvidia drivers here:
[http://compiz.org/NVidia](http://compiz.org/NVidia)

I had originally installed the distros version of the drivers a few sessions earlier, but I wanted the most recent version from the chip maker, instead of a potentially more limited version (I have a dual-monitor setup, which the stock drivers didn't support).

The first step from the instrs. didn't return anything (I think it didn't recognize one of the commands) 

> This only applies for those who have an older version of the nvidia driver installed from your distribution's repositories. To check what version of the nvidia driver you have installed now type this into a terminal: 

glxinfo | grep "OpenGL version string:"This should return something like this: 

OpenGL version string: 2.1.0 NVIDIA 96.31

So, I proceeded to continue with the guide.  I didn't know how to remove the 'linux-restricted-modules' package, so I went with their suggestion:

> Please also ensure that the "linux-restricted-modules"-packages have been uninstalled. Alternatively, you can edit the /etc/default/linux-restricted-modules configuration file and add the following: 

DISABLED_MODULES="nv nvidia_new"

I went on with it, but because "sudo /etc/init.d/gdm stop" failed (no gdm file there, prolly b/c of kde), I ran the next step from the recovery console (as root):

> Now you must navigate to the directory where you downloaded the nvidia driver. Once there you must type this: 

sudo sh NVIDIA-Linux-x86-1.0-9631-pkg1.runBe sure to replace the "x86-1.0-9631-pkg1" with the appropriate architecture and version for the file you downloaded. For example "NVIDIA-Linux-x86_64-100.14.11-pkg2.run" for an amd64 kernel. 

Now follow the instructions and if it complains about not finding a matching kernel-interface choose to download a new one. Most probably it will fail and create a matching interface of its own. If it asks you whether to modify your xorg.conf, choose "Yes". Now essentially you are done and most pro 1000 bably you could just c 1000 ontinue with "Now reboot you system ...". The following detailed instructions tell you how to deal with some special problems. 

The new module is created as the file "/lib/modules/`uname -r`/kernel/drivers/video/nvidia.ko" . You can query where "modprobe" thinks the module "nvidia" is located. It should be:

$ modprobe --show-depends nvidia
insmod /lib/modules/2.6.22-8-generic/kernel/drivers/i2c/i2c-core.ko 
insmod /lib/modules/2.6.22-8-generic/kernel/drivers/video/nvidia.ko 


Unfortunately, after intalling the new driver, kde stopped loading, and whenever I boot into a new session, it goes straight to console, which spends the next few seconds flashing a screen with a blue background, and 'x' shaped crosshair in the center, before stopping.  After this, it stops flickering, and stops with the (functional) console.  Pressing ctrl+alt+F7 reveals a black screen with a static underscore "_" in the top left corner.

I tried to follow the rest of the steps, but I cant get past the last part, because modprobe says it can't find "nvidia_is":

> If this is the case, you can skip the next few lines and continue with "Now reboot your system ...". If instead you get 

$ modprobe --show-depends nvidia
install /sbin/lrm-video nvidia

then you probably decided to keep the linux restricted modules (See "Removing the old Nvidia driver") and the restricted driver manager is still in the way. It will load a module from the linux-restricted-modules package. One way to circumvent this is to rename the newly compiled driver file to "nvidia-is.ko": 

cd /lib/modules/`uname -r`/kernel/drivers/video
sudo mv nvidia.ko nvidia-is.koand make a new entry in the modprobe aliases: 

sudo gedit /etc/modprobe.d/nvidia-install-scriptwith the lines 

# Make --modprobe nvidia-- look for nvidia-is
alias nvidia nvidia-isYou can check that this worked with: 

$ modprobe --show-depends nvidia
insmod /lib/modules/2.6.22-8-generic/kernel/drivers/i2c/i2c-core.ko 
insmod /lib/modules/2.6.22-8-generic/kernel/drivers/video/nvidia-is.ko

Now I think I broke the window manager by installing the nvidia driver (likely fuxed xconf), but I can't figure out why the rest of the steps aren't working.  I don't have gedit, so I had to modify the text files with windows notepad (via ext2ifs), then used a hex editor to swap out the CrLf newline character's with 'Lf' characters, to make it linux-compatible.

I guess I need to know if there's any way to un-brick it, before I go wipe the drive and start over.


p.s.
On a side note, I find linux in general to be confusing and difficult to use (given that I've been using windows for the past 12 years), and the fact that ubuntu doesn't allow login as root to be a major hinderance.  I don't like having to type 'sudo' in front of everything, and the fact that tasks like this one almost cripple the ability to use graphical methods to enact changes, due to the limited permissions those apps have.  It there any way to circumvent all of these limitations? I found some guide that let me add my user account to the admin/sudo groups, but that hasn't helped much.

p.p.s
Thanks for reading my long-winded post, and please forgive any mis-used terms and spelling mistakes that are undoubtedly present.  I can share any useful log files/etc that you may need.  Though this is my first post here, I really hope I don't come off as being too demanding.  Cheers.

---

### Post by jimv on 2008-07-27
Lets try installing the driver with Envy.  Usually has a high success rate when other things don't work.

sudo apt-get install envyng-gtk
envyng -t

Press 1 to install the Nvidia driver.

> On a side note, I find linux in general to be confusing and difficult to use (given that I've been using windows for the past 12 years), and the fact that ubuntu doesn't allow login as root to be a major hinderance. I don't like having to type 'sudo' in front of everything, and the fact that tasks like this one almost cripple the ability to use graphical methods to enact changes, due to the limited permissions those apps have. It there any way to circumvent all of these limitations? I found some guide that let me add my user account to the admin/sudo groups, but that hasn't helped much.

Note:  Enabling the root login is much less secure, but hey, it's your computer.

To enable root login, open a terminal and type:

sudo nano /usr/local/share/config/kdm/kdmrc

Find the line that says AllowRootLogin=false and change it to true.
Press control+x to exit nano, and press y to save the changes.  Then you need to set a password for the root account before you can login.  Here's the command to do that:

sudo passwd

Then just type the desired password.  You should be able to log in at this point.

ALSO, if you're logged in as yourself and you want to run a bunch of terminal commands as root, type 'sudo bash' and it will turn it into a root terminal and you won't have to type sudo before everything.

---

