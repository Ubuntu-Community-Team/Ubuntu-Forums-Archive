---
title: "geforce ti4600 nvidia drivers not installing"
date: 2010-05-24
forum: Installation &amp; Upgrades
---

### Post by w1dmerox on 2010-05-24
Hello, I just installed a fresh copy of unbuntu 10.04 and downloaded the  lastest drivers for my video card  but when double click the file, i  get a message that says "could not open file/home/desktop  name/download/n...nux-86-96.43.16-pkg1.run."

Anyone know why this is happening?  A friend told me to try to run them  in terminal so when i opened the drivers with terminal I get a message  saying "error: nvida-installer must be run as root"

---

### Post by SlidingHorn on 2010-05-24
> **w1dmerox said:**
> Anyone know why this is happening?  A friend told me to try to run them  in terminal so when i opened the drivers with terminal I get a message  saying "error: nvida-installer must be run as root"

I don't know what would cause the issue in your first question, but if you open with the terminal, use "sudo" before the command:

```
sudo ./filelocation/filename
```

---

### Post by w1dmerox on 2010-05-24
Ok, I just came from windows so my question is, if i type the file location, why is there a period in front of /filelocation? does this look right?

sudo ./home/me/downloads/nvidia-linux-x86-96.43.16-pkg1.run

---

### Post by cryptotheslow on 2010-05-24
Why not just install the drivers via the System menu...  System > Administration > Hardware Drivers


If you install manually you will have to re-install them with every kernel update.

To manually install you must stop the desktop service. So...

1. Close any applications you have open & save your work!
2. Ctrl+Alt+F1    -  this will take you to a terminal login - login with your usual username / password
3. Enter this command:   sudo service gdm stop    (this will ask for your password - so enter it!)
4. Change directory to the directory where you downloaded the installer to.
5. Set the file to be executable with:   chmod +x ./NVIDIA-Linux-x86-195.36.24-pkg1.run    (or whatever the filename is)
6. Run the installer: sudo sh ./NVIDIA-Linux-x86-195.36.24-pkg1.run   (or whatever the filename is)
7. At the end of the installer answer Yes to the question about updating your xorg configuration.
8. The installer will exit once completed then enter this command to restart the desktop:  sudo service gdm start

That should put you back at a graphical login screen.

---

### Post by cascade9 on 2010-05-24
> **w1dmerox said:**
> Hello, I just installed a fresh copy of unbuntu 10.04 and downloaded the  lastest drivers for my video card  but when double click the file, i  get a message that says "could not open file/home/desktop  name/download/n...nux-86-96.43.16-pkg1.run."

Anyone know why this is happening?  A friend told me to try to run them  in terminal so when i opened the drivers with terminal I get a message  saying "error: nvida-installer must be run as root"

Not only must it be run as root, but to install video drivers that way, you've got to be out of 'X' (desktop).

Why not try doing it the easy way? System-> administration-> drivers.

---

### Post by w1dmerox on 2010-05-24
Ok, i'll try that, thanks, but when I tried the first option slidinghorn, terminal said comand not found. What did I do wrong?

---

### Post by cryptotheslow on 2010-05-24
> **w1dmerox said:**
> Ok, I just came from windows so my question is, if i type the file location, why is there a period in front of /filelocation? does this look right?

sudo ./home/me/downloads/nvidia-linux-x86-96.43.16-pkg1.run


The ./ indicates the current directory you are in.

Typically when you open a Terminal session you will be in your Home directory which will most likely be /home/me

To run a file in a folder called downloads in your folder at that point you could use:

sudo /home/me/downloads/nvidia-linux-x86-96.43.16-pkg1.run
---- notice there is no dot as you are giving the full path

sudo ./downloads/nvidia-linux-x86-96.43.16-pkg1.run
---- you know you are already in /home/me so the dot is effectively saying "from here"

Another useful one is the tilde ~

~ refers to your Home directory. So whatever your current directory entering:
cd ~

will take you back to your Home directory. In your example you could use that wherever you are in the filesystem by:
sudo ~/downloads/nvidia-linux-x86-96.43.16-pkg1.run

One last one:
..

refers to the directory above the one you are currently in. So:
cd ..

will take you one level up the directory structure.

Enough for now! They are basically just simple ways to refer to common locations I guess.

---

### Post by w1dmerox on 2010-05-24
Easy way sounds right up my ally.
I didn't know I could do that, it only has 1 driver in there (version 96), is that the one that I just downloaded?

---

### Post by cryptotheslow on 2010-05-24
> **w1dmerox said:**
> Ok, i'll try that, thanks, but when I tried the first option slidinghorn, terminal said comand not found. What did I do wrong?

I suspect you didn't specify the path correctly or the executable permission bit has not been set on the file (that is what the chmod +x command does). Typically shell scripts and the like that you download and save will be saved without the execute bit set - so you have to manually make the concious decision to make the file executable (chmod in a Terminal, or right-click in Nautilus, goto Properties and tick the Execute box.

---

### Post by cryptotheslow on 2010-05-24
> **w1dmerox said:**
> Easy way sounds right up my ally.
I didn't know I could do that, it only has 1 driver in there (version 96), is that the one that I just downloaded?

It is the same version that you downloaded yes. It is not the file you just downloaded no.

The one in Hardware Drivers is in the repositories.

---

### Post by w1dmerox on 2010-05-24
Cool, much appreciated. :)

---

### Post by ratcheer on 2010-05-24
It ***should*** have a selection for "NVIDIA accelerated graphics driver (version current) [Recommended]".

---

### Post by cascade9 on 2010-05-24
> **w1dmerox said:**
> Easy way sounds right up my ally.
I didn't know I could do that, it only has 1 driver in there (version 96), is that the one that I just downloaded?

It might be a differrent revision, eg you d/led 96.43.16, it might be 96.35.11 (I just made that up, I have no idea what the last 96.xx driver version was). It wont make much, if any, differrence though.

---

### Post by w1dmerox on 2010-05-24
I see, these drivers are the ones I installed yesterday, I get really low fps in WoW so I need to install the ones from the nvidia website I think.

---

### Post by cascade9 on 2010-05-24
> **w1dmerox said:**
> 96.43.16

The drivers you d/led. 

96.43-17- the version in the ubuntu 10.04 repos- 

[http://packages.ubuntu.com/lucid/nvidia-96](http://packages.ubuntu.com/lucid/nvidia-96)

You are gettign newer drivers from the unbuntu repos than you d/led ;) 

> **w1dmerox said:**
> I see, these drivers are the ones I installed yesterday, I get really low fps in WoW so I need to install the ones from the nvidia website I think.
  
I doubt that a minor revision in the drivers is going to make any real difference to your WoW framerates.

*edit- if you are running compiz, try turning it off before you lauch WoW.

---

### Post by w1dmerox on 2010-05-24
Hmm,  after I installed the drivers from the respository yesterday and tried Wow, my fps was horrible.
I have better fps with windows. 

I tried the ones from the respository but there are some problems with those. I use two monitors and I have more problems with those than the default drivers.

---

### Post by w1dmerox on 2010-05-24
Does anyone know if PlayONLinux will help even though I have wine installed?

---

### Post by w1dmerox on 2010-05-24
Ok so wow won't even load with default drivers, lol. 
I'll try the drivers from the repository again.

Does it have to be so complicated to install drivers I downloaded? I just installed linux and have no idea wtf im doing half the time.

---

