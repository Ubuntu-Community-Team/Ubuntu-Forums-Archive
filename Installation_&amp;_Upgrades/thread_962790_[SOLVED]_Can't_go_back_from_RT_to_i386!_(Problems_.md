---
title: "[SOLVED] Can't go back from RT to i386! (Problems with X)"
date: 2008-10-29
forum: Installation &amp; Upgrades
---

### Post by emshains on 2008-10-29
I had to install the real-time kernel, because I was curious about the ubuntu-studio packages. Since there is no greater power than curiosity about things in apt in my life, I installed it, and came across a chain-reaction of problems. 
My specs:
Sempron 2400+ 1.6ghz 133mhz FSB
Nvidia 7300GT, 256mb AGP8x
768mb of ram
Silicon integrated Systems motherboard of which I have absolutely no info or what-so-ever. 

My story goes like this: I wanted to check the Ubuntustudio, so I installed their packages, with whom the linux-rt package came along. After that I rebooted, and Woo-Hoo, neither the sound editing works, nor did I cared about anything else, because now my faulty wi-fi card (the realtek chipset), which I had a script for to get it working, started to act weird. I could connect to my AP, but about an hour later, the connection was dead, killing the connection and then rerunning the script didn't work, so now I wanted to get back to my old friend, the i386. And all I did was just a little "sudo apt-get remove linux-rt". After it had removed the ~52kb of kernel, I rebooted. To check if this had worked, didn't boot right into my system, but I checked the boot menu. And you've guessed it, the real-time kernel was still there. So, obviousley, I thought, maybe you can't delete a kernel when you are running on it. So I booted in my usual kernel. Then it booted up to the point where it starts X. And now it panics, because it can't run X and gives a reason for it- bad X server configuration. Since I didn't think that the configuration is to blame, because I don't really mess around the config files of X, I immediately thought that something was wrong with my drivers for the 7300gt. The next thing I checked was the google, and came across a very similar problem(the link ---> [http://ubuntuforums.org/showthread.php?t=586827]("http://ubuntuforums.org/showthread.php?t=586827"), but only upgrading to a real-time kernel. ( I don't actually think about it as an upgrade now.) It said it had problems with running X because of the nvidia drivers, there were 2 cards specified, the 7200 and the 7600, so I thought this was too similar to cross out. It said it fixed it, by running 2 commands. Now, when I try to into the command line, when I boot the normal kernel, it asks for my username and password, and then, I think, it crashes, just freezes with myusername@mycomputer:~$, and there is nothing I can do but the almighty restart button. I haven't tried the recovery mode though, its something I will probably do tomorrow, because I have to hit level 70 till November 13th.


I apologize for:
1. My english
2. Any lack of info
3. My addiction to World of Warcraft.

I hope you will understand what I wrote and try to help. Any help will be apreciated.

---

### Post by emshains on 2008-10-29
News flash!

It must be the nvidia drivers, either I have a different kernel than I should be having (the log told me something about smp, which is just nuts), or the nvidia drivers themselves, because when I did x fix in the recovery mode, I ended up using some default drivers for the video. Then I entered ```
sudo nvidia-xconfig
``` or something like that, and then restarted the X session. And guess what? The same error telling me that the xconfig file is messed up. Although it said something about overwriting the config file when I did the nvidia-xconfig thingy, I didn't pay much attention, because it always yells about overwriting stuff. 

Correct me if I am wrong, the processor is intended to run i386, right ? Although the default kernel mentioned here is the one that came out of the box with 8.10.

Hey, maybe I have to reinstall the nvidia drivers, while I am at the recovery mode, so they get compiled for the kernel needed ? I hope I just made sense of something!

---

### Post by emshains on 2008-10-30
I think the problem is so critical, well, at least for me, that I am already going to bump the thread.

---

### Post by emshains on 2008-10-30
So, after the 5th reboot I had to do just to get my Wi-Fi going again, I decided to make another fix for the X, in the recovery mode, and then I said EnvyNG to do the dirty work and voila, its running again, I didn't even have to set the resolution to the max, because its fixed. Now, to get that bloody realtime kernel off the hdd, at least to get it off or down the grub menu. 

Guess I spoiled a thread, all I did was posting my progress. I hope somebody will find this thread useful, because, for me, it wasn't.


Edit: I just realized that my architecture is i686. Well, that means that this is an equivalent to a P4 Celeron, not P3.

---

