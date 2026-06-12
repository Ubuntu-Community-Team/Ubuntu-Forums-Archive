---
title: "Installing NVIDIA GeForce 8500 GT (512 MB) DRIVER"
date: 2008-03-24
forum: Installation &amp; Upgrades
---

### Post by bezous on 2008-03-24
Hey, 

I'm new to Ubuntu, I'm running Ubuntu Gutsy Gibbon 7.10
 
But I'm having enormous trouble installing a nVidia GeForce 8500 GT (512MB)

I've tried everything I possibly could find and read, but nothing helps.

can someone please help me step by step with the installation.

i have been on it for almost 2  weeks now.

please please HELP :(

[email]bezousdevil@hotmail.com[/email]
just incase.

thank you all...

---

### Post by liquidfunk on 2008-03-24
Use Envy!

 I have the same card.

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

 Install it, and click install the Nvidia Driver.

 Easy peasy

---

### Post by bezous on 2008-03-26
hey thanx for replying so soon,

well i actually tried Envy, and when i start installing nvidia 
it comes with an error.

i can only go with the manual installation
and when it finishes it restarts auto.

then i get a very bad qualty for resolution.

please any further help
if you want i can print a screenshot if that would help

thanks alot

---

### Post by bezous on 2008-03-26
here 

i have took some screenshots for my case.

the first problem it has been solved by using the update manager
it downloaded the missing files and it worked perfectly.

but i'm stuck in the second problem
which i really don't know how to handle.

ENVY ERROR: Nvidia card not found
with root  /var/log/envy-installer.log

please any idea?

i really need help with this

thank you all

---

### Post by liquidfunk on 2008-03-26
Is it possible that your monitor isn't plugged into the right slot?

 I think every motherboard has onboard graphics, perhaps you have it plugged into there?

 Is there another Blue VGA slot on the back of your PC?

---

### Post by bezous on 2008-03-26
my motherboard doesn't have any VGA Plug-in
but the graphic card come with two slots one is blue
the other one is silver

i'm using the silver which requiers double headed cable if u know what i mean.

if you have the same card then you should have received one small peice that you plug with the monitor so you can use the silver slot.

but still i don't get your point, 
do you think i should try plugging my monitor into the blue VGA Slot of the graphic card?

---

### Post by stchman on 2008-03-26
> **bezous said:**
> Hey, 

I'm new to Ubuntu, I'm running Ubuntu Gutsy Gibbon 7.10
 
But I'm having enormous trouble installing a nVidia GeForce 8500 GT (512MB)

I've tried everything I possibly could find and read, but nothing helps.

can someone please help me step by step with the installation.

i have been on it for almost 2  weeks now.

please please HELP :(

[email]bezousdevil@hotmail.com[/email]
just incase.

thank you all...

Install Envy 0.9.10 and tell it to manually install the Nvidia driver.  The 169.12 will be an option.  The 169.xx drivers fully support the 8xxx line of nvidia cards.  Select the driver and let it do it's thing.

Before you install the driver tell Envy to remove the nvidia driver.  This will undo anything you have done.  You may then be unable to log in to X after reboot, but that is no problem.  If that happens type:

```
sudo envy -t
```

that will bring up the CLI version of Envy.

Tell it to do the manual install of the 169.12 and let it modify your xorg.conf and reboot your PC.

This worked perfectly on my Feisty box.  Now I had to edit my xorg.conf and add "1920x1200" as the first in the line of resulotions.  Reboot the workspace and viola.

This got my 8800GT working on my Feisty box.

---

### Post by bezous on 2008-03-26
hey thanx alot,

i'll give it a try and let you know what will happen with me.

i hope this will get it to work 

again thanx alot

---

### Post by bezous on 2008-03-27
> **stchman said:**
> Install Envy 0.9.10 and tell it to manually install the Nvidia driver.  The 169.12 will be an option.  The 169.xx drivers fully support the 8xxx line of nvidia cards.  Select the driver and let it do it's thing.

Before you install the driver tell Envy to remove the nvidia driver.  This will undo anything you have done.  You may then be unable to log in to X after reboot, but that is no problem.  If that happens type:

```
sudo envy -t
```

that will bring up the CLI version of Envy.

Tell it to do the manual install of the 169.12 and let it modify your xorg.conf and reboot your PC.

This worked perfectly on my Feisty box.  Now I had to edit my xorg.conf and add "1920x1200" as the first in the line of resulotions.  Reboot the workspace and viola.

This got my 8800GT working on my Feisty box.

[B]
ok i have done all these steps
1- installed envy.
2- delete all files for Nvidia using the uninstall Nvidia Drivers.
3- installed the driver using manual installation.
 
now its done installing i reboot and i had no errors at all.

but still it says i'm using S3 video card.

how do i apply the new changes 
please if you can send me the steps.:)

thank you...[/B]

---

### Post by Tomatz on 2008-03-27
Sounds like a problem with the card. Can you return it to where you purchased it from?

---

### Post by Pumalite on 2008-03-27
Before giving up I would download driver from Nvidia (169.12) and try to install it after installing at least build-essential
sudo apt-get install build-essential
At the command line:
sudo /etc/init.d/gdm stop
password
sudo sh /path/to/driver/NVIDIA-Linux-xxx.run
Accept the License
Let the driver compile the module into your kernel
Let the driver reconfigure your xorg.conf file
Then: startx

---

### Post by bezous on 2008-03-27
strange

it was working fine with vista
plus i have been using it for the past 2 years

and you know i have been searching the net night and day
there is too much to do with ubuntu
and it is too complicated

i spent weeks just to know how to install a driver.

don't know what to do anymore
i think i will go back to vista

anyways, thanks alot everyone
i will keep looking for a while more.
i was hpeing to find some solutions today 
but i guess no luck

---

### Post by Pumalite on 2008-03-27
What happened with my idea?

---

### Post by bezous on 2008-06-10
> **Pumalite said:**
> What happened with my idea?
Hello PumaLite

it's been a while
but i'm back 

and this time i'm trying ubuntu on my laptop which using Geforce 8400M GS

i don't know if you have any ideas?

thank you

---

### Post by BlackLight94 on 2008-06-10
The .run file from the nVidia site doesn't work. Just try to install the restircted driver from the hardware drivers tool. It's System > Administration > Hardware Drivers (or something along those lines)

---

