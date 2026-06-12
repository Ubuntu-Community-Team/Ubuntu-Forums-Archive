---
title: "USB DVD Install"
date: 2005-05-31
forum: Installation &amp; Upgrades
---

### Post by pashby on 2005-05-31
Hello all

Nothing like jumping in at the deep end!

I have been a Computer user/experimenter and Windows user for more years than I care to remember but for a challenge and knowledge I have been experimenting with different versions of Linux over the last few weeks. I have tried Fedora, Mandrake, Fedora again and now Ubuntu.

I have worked with all these get each version to run and boot from a USB drive - I want to keep XP and Linux seperate and maybe transport my USB drive from machine to machine.

I read a review of Ubuntu and have been looking for a distribution accompanying a computing magazine. I found one which indicated that it was a full distribution on DVD.

So -- I blew away my working but flaky Fedora and installed Ubuntu to the USB drive. After some searching I found the method needed to change the initrd to make the booting from USB work.

Here is the problem - I get a good boot and everything loads OK but it drops me into a shell interface and not a desktop. I have installed from DVD 4 times and have made VERY sure that I have either typed Linux or pressed return when making my choice of install. No way have I ever asked for a SERVER install, but this seems to be what I keep getting as I have no GUI/Desktop.

This wouldn't be so bad if I could load the desktop from DVD BUT the system keeps ignoring the DVD and wants me to put in a CD with the required distribution. What does this mean? How can I move on from here?

I'm sorry about this rambling post but I am getting frustrated and need some guidance -- Help

Peter

---

### Post by Mez on 2005-05-31
assuming your computer is connecting to the net ok (try ping [www.yahoo.com](www.yahoo.com) to see if it is)

then you should be able to edit your /etc/apt/sources.list so that it downloads packages from the internet.

Your /etc/apt/sources.list should show the following to download from the net
 
```
# deb cdrom:[Kubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


deb http://gb.archive.ubuntu.com/ubuntu hoary main restricted
# deb-src http://gb.archive.ubuntu.com/ubuntu hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu hoary-updates main restricted
# deb-src http://gb.archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://gb.archive.ubuntu.com/ubuntu hoary universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu hoary universe

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
# deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

deb http://security.ubuntu.com/ubuntu hoary-security universe
#deb-src http://security.ubuntu.com/ubuntu hoary-security universe
```

this will allow you to downlaod form the internet (to edit the file run the ommand "sudo nano /etc/apt/sources.list" )

Anyway, once you've made you sources.list look like that, then you can go ahead and run the following commands to install a gui (if it's not already installed)

```
sudo apt-get update
sudo apt-get install ubuntu-desktop
```

This should install a GUI for you

[edit]Remeber to replace "gb" in the above with your country code to get your local mirror (if you are un the UK though, feel free to use gb!)[/edit]

---

### Post by pashby on 2005-06-01
I'm at work now and am looking foward to trying this later.

Thanks Peter

---

### Post by pashby on 2005-06-01
Thanks Mez

I got home late and followed your instructions.

Worked well and after a 2 and half hour download I was able to get the desktop up and running.

Looks great

Unfortunately the refresh rate was stuck at 60 hz and I tried to increase it to 75 hz to help viewing.  Followed some instructions and rebooted but lost the XWindows.  I have made a copy of the old file so should be able to get it back but I would still like to change the refresh rate.

I have a Radeon 9600 128 meg card which should be able to give at least 75 hz as my resolution.

I'll troll though the forums to see if there is a way of doing this.

Peter

---

