---
title: "nvidia driver update"
date: 2010-04-25
forum: Installation &amp; Upgrades
---

### Post by oohbuntoo on 2010-04-25
[FONT=System]From the [/FONT]Nvidia web site I was given:

 NVIDIA-Linux-x86-195.36.15-pkg1.run

When I double-click on this from my desktop where it is saved I receive an error message:

Could not open the file /home/spock/Desktop/NVID...ux-x86-195.36.15-pkg1.run.
gedit has not been able to detect the character coding
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again.

_______________________________________________________________________

This package is what the Nvidia website gave me when searching for updates for my graphics card.  I am running Karmic Koala 9.10 32-bit.  I have a Nvidia 6600gt card.  I have no idea what to do, if I can do anything at all.  HELP!!!

---

### Post by wmatthews on 2010-04-25
chmod 775 /home/spock/Desktop/NVIDIA-Linux-x86-195.36.15.pkg1.run
sudo /home/spock/Desktop/NVIDIA-Linux-x86-195.36.15.pkg1.run

Those two command should get it going for you.  Make sure that you run them fro the terminal.

---

### Post by r.osmanov on 2010-04-25
Not sure, but it seems gdm should be stopped before update with /etc/init.d/gdm stop and started after the driver installation with /etc/init.d/gdm start 

I had an issue with NVIDIA driver after update. It failed to launch gdm on the next boot. The fix was removing /etc/X11/xorg.conf file to let it create new one.

---

### Post by Linuxforall on 2010-04-25
Place the driver in the home folder and don't do anything to it.

in terminal do a sudo apt-get --purge remove nvidia*

sudo apt-get install build-essential

then hit ctrl+alt+F1 and you will be logged out of GUI into terminal.

type your login and then do a sudo service gdm stop

after that do a sudo .sh NVIDIA and hit tab for autocomplete

say yes to all the prompts

when you are back in command prompt, do a sudo reboot.

remember with this process, everytime there is a kernel update, you need to go out of gui and remove nvidia driver with the command sudo nvidia-uninstall and then reboot and go into terminal mode and re-install the driver. This method always gives you the latest cutting edge drivers from nvidia.

---

### Post by oohbuntoo on 2010-04-25
> **wmatthews said:**
> chmod 775 /home/spock/Desktop/NVIDIA-Linux-x86-195.36.15.pkg1.run
sudo /home/spock/Desktop/NVIDIA-Linux-x86-195.36.15.pkg1.run

Those two command should get it going for you.  Make sure that you run them fro the terminal.

This is what happened when I entered those commands in my terminal:

[FONT=Fixedsys][COLOR=Green][B]spock@ubuntu:~$ chmod 775 /home/spock/Desktop/NVIDIA-Linux-x86-195.36.15.pkg .1run
chmod: cannot access `/home/spock/Desktop/NVIDIA-Linux-x86-195.36.15.pkg': No such file or directory
chmod: cannot access `.1run': No such file or directory
spock@ubuntu:~$ sudo /home/spock/Desktop/NVIDIA-Linux-x86-195.36.15.pkg1.run
[sudo] password for spock: 
sudo: /home/spock/Desktop/NVIDIA-Linux-x86-195.36.15.pkg1.run: command not found[/B][/COLOR][/FONT]

---

### Post by oohbuntoo on 2010-04-25
Here's another question.  My Karmic is running fine.  Do I even [COLOR=Red]NEED [/COLOR]to update my graphics card drivers??  I don't wanna screw up my current settings or possibly end up having to do a fresh install and start over if it's not worth it.  By the way, thanks for all the input so far 'cuz I am still a newbie at this.

---

### Post by quadproc on 2010-04-25
> **oohbuntoo said:**
> This is what happened when I entered those commands in my terminal:

[FONT=Fixedsys][COLOR=Green][B]spock@ubuntu:~$ chmod 775 /home/spock/Desktop/NVIDIA-Linux-x86-195.36.15.pkg .1run
chmod: cannot access `/home/spock/Desktop/NVIDIA-Linux-x86-195.36.15.pkg': No such file or directory
[/B][/COLOR][/FONT]
There is a typo at the end of the file name: 1.run vs. .1run

quadproc

---

### Post by oohbuntoo on 2010-04-25
> **quadproc said:**
> There is a typo at the end of the file name: 1.run vs. .1run

quadproc

[COLOR="RoyalBlue"]Oh snap, I didn't peep that.  Let me jump back on it.[/COLOR]

---

### Post by oohbuntoo on 2010-04-25
> **oohbuntoo said:**
> [COLOR="RoyalBlue"]Oh snap, I didn't peep that.  Let me jump back on it.[/COLOR]

Alright.  Second attempt, no dice:

[COLOR="SeaGreen"][COLOR="SeaGreen"][B]spock@ubuntu:~$ chmod 775 /home/spock/Desktop/NVIDIA-Linux-x86-195.36.15.pkg1.run
chmod: cannot access `/home/spock/Desktop/NVIDIA-Linux-x86-195.36.15.pkg1.run': No such file or directory
spock@ubuntu:~$ sudo /home/spock/Desktop/NVIDIA-Linux-x86-195.36.15.pkg1.run
sudo: /home/spock/Desktop/NVIDIA-Linux-x86-195.36.15.pkg1.run: command not found[/B][/COLOR][/COLOR]

---

### Post by richs-lxh on 2010-04-25
Just put the file in your home directory "spock".

Then use the Tab button once you have got to NVIDIA to autocomplete (the terminal will finish the rest for you). It avoids typing errors:

```
chmod +x /home/spock/NVIDIA
```
Hit Tab and you should get:
```
chmod +x /home/spock/NVIDIA-Linux-x86-195.36.15.pkg1.run
```

Then hit Ctrl+Alt+F1 to leave the graphical desktop.

Login.

Kill GDM with either:
```
sudo killall gdm
```
or
```
sudo /etc/init.d/gdm stop
```

Now install the Nvidia binary with:
```
sudo sh NVIDIA-Linux-x86-195.36.15.pkg1.run
```

Once it's installed, load the module with:
```
sudo modprobe nvidia
```

And start the desktop with:
```
startx
```

You may need to configure X if there is a problem, Nvidia is like that sometimes.

---

### Post by oohbuntoo on 2010-04-25
[FONT="Fixedsys"][COLOR="Red"]ALRIGHT!!!! [/COLOR] [COLOR="Green"]I'd would like to send a special thanks to all those who contributed to this task.  I successfully completed installation of said driver.  My "show mouse" is crazy detailed now.  I wasn't expecting to see a difference.  I'm glad you guys stuck with me through the typos and all.  Thanks again.  Linux kills!!!!  =] [/COLOR][/FONT]

---

