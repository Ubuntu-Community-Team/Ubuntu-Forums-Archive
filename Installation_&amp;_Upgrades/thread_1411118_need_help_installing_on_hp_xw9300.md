---
title: "need help installing on hp xw9300"
date: 2010-02-19
forum: Installation &amp; Upgrades
---

### Post by vuoto on 2010-02-19
Hello, world.

I bought a pair of hp xw9300 workstations, which have dual AMD opterons for the specific purpose of running Ubuntu.  One of them is going to be used by my wife, who is a mathematician and wants to use gfortran (especially the FFTW3 libraries) to do work in fluid dynamics.

The other is going to be a fileserver for music production, where I'll use the Reaper DAW and off-load effects processing and rendering chores using the REAmote service from Cockos.  I've used Ubuntu before for this purpose and know how to set it up.

My problem is installing Ubuntu.  I've tried both the AMD64-bit and regular 32-bit Ubuntu versions and am having the same problem with both.

When I boot from the Ubuntu disk (I burned it to a DVD), it starts up and I see the user-friendly installation screen.  I pick English and it starts to install.  There are a few dozen messages about trying to connect to a timeserver (there IS a live internet connection via ethernet) and then the screen goes black.  It flashes back on every minute or so and shows that whatever the next process is goes up to "30%", but it seems to be in an endless loop with the screen turning off and flashing back on every minute or so.

I got a little further by booting Linux from the Ubuntu disk, and choosing "run ubuntu without changing your computer".  Then I make sure there is an ext3 partition and a swap partition and a small Fat32 partition (I might install Win7 later).  The installation seems to go just fine, but when I reboot it just starts booting and then just restarts the computer.  Again, if I left it alone it would do this endlessly it seems.

The hard drive in the xw9300 is a SATA drive.  I assumed that Ubuntu would be able to use that.  Indeed, when I started GPART from Ubuntu when it was running off the DVD, it saw the disk just fine and let me create and/or delete partitions and format them.

I should mention that I put a Radeon x1650 pro in the computer.  I know it might not be the best choice for Ubuntu because of the drivers, but I thought I'd at least be able to install Ubuntu and then decide whether I want to run one of the available drivers for it.  Since I can run Ubuntu from the DVD and see the Ubuntu desktop, that the video card isn't the problem.

If I select "recovery mode" at the bootloader, I can get to what looks like a linux terminal prompt, but I'm not good enough with Linux to know what to do from there.  I can log in with the user name and password that I created when I installed Ubuntu after booting into the "live" image.  But if I try to start Ubuntu in the normal manner, it just keeps restarting the entire computer.

I was able to install and use Windows XP on this computer with no problem.  I deleted that partition before trying to install Ubuntu.  So I assume that there isn't a problem with the hardware being bad.  

If anyone can give me any suggestions, I'd really appreciate it.  I'm most concerned with getting Ubuntu and gfortran (and the FFTW3 libraries) working for my wife, since I've got another machine running Ubuntu Studio that I can use as my DAW support machine.

Thanks,

---

### Post by NetDesignate on 2010-06-21
FYI - I have recently loaded the new LTS SERVER 10.04 release and it loaded fine.

My only issue is that it does not seem to correctly identify the Dual Cores for each processor.  (The HP xw9300 I have has two hardware CPUs - each one being Dual-Core - so there should be a total of 4 CPUs recognized - unless I am mistaken?)

Note that the SERVER release can easily be made into a DESKTOP release just by a few aptitude commands to add X/gdm desktop support. Note that the "gnome-core" is the basic window manager build, and does not load ANY of the bells and whistles like Firefox, Open Office etc. (which is what I preferred)

```
sudo aptitude install x-window-system-core gnome-core
sudo aptitude install gdm
/etc/init.d/gdm start

# Note: on version 10.04 it complains and suggests 
# using the "service" command below (it works!):
sudo service gdm start
```

See details on this:
[http://www.linuxquestions.org/questions/ubuntu-63/gui-for-ubuntu-server-463053/]("http://www.linuxquestions.org/questions/ubuntu-63/gui-for-ubuntu-server-463053/")

If anyone knows about multi-core support and how to get the additional cores recognized, please let me know...

---

