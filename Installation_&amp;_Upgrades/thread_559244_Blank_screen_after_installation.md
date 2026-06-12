---
title: "Blank screen after installation"
date: 2007-09-24
forum: Installation &amp; Upgrades
---

### Post by Raderick on 2007-09-24
My computer:
HP Pavilion dv9000
1.80 gigahertz AMD Turion 64 X2
NVIDIA GeForce Go 6150
Conexant High Definition Audio
2GB RAM

I installed the AMD 64 edition of Ubuntu 7.04. I also have Windows Vista installed on this computer. When I try to load Ubuntu, it would give me a black screen after the splash screen.

---

### Post by Pumalite on 2007-09-24
Try:
sudo dpkg-reconfigure xserver-xorg, accept most defaults, choose 'vesa' as the driver, then: startx
(Ctrl+Alt+F1 to get a command line)

---

### Post by Raderick on 2007-09-24
> **Pumalite said:**
> Try:
sudo dpkg-reconfigure xserver-xorg, accept most defaults, choose 'vesa' as the driver, then: startx
(Ctrl+Alt+F1 to get a command line)

Being the ubunto newbie that I am, I just have to ask....

Whaaa do what? Type what when where?

---

### Post by Jerubaal on 2007-09-25
I have a similar problem, but with Dapper LTS. So far I have:
1. started Ubuntu in recover mode (or whatever it is called) so I just get to a command line that looks like 'ubuntu@mycomputername#'
2. backed up /etc/X11/xorg.conf
```
cp /etc/X11/xorg.conf etc/X11/xorg.conf_backup
```
3. used the text editor 'nano' to look at the xorg.conf file
```
nano -w /etc/X11/xorg.conf
```
but could not find what to change to 'vesa'.
4. I tried 
```
dpkg-reconfigure xserver-xorg
```
but somehow missed the vesa option. Will look for it tonight.

I had Ubuntu installed fine (from LiveCD install), but then did a total reorganisation of the computer & installed with the alternateCD to get the blank screen. I'm sure I never saw the vesa option during installation, though.

---

### Post by Pumalite on 2007-09-25
When you get at the end of the install: Ctrl+Alt+F1 to get a command line
At the command line:
sudo dpkg-reconfigure xserver-xorg

---

### Post by Raderick on 2007-09-25
> **Pumalite said:**
> When you get at the end of the install: Ctrl+Alt+F1 to get a command line
At the command line:
sudo dpkg-reconfigure xserver-xorg

There is no command line. Just a black screen.

---

### Post by Pumalite on 2007-09-25
After Ctrl+Alt+F1, still a blank screen?

---

### Post by thomasaaron on 2007-09-25
Hey, guys.

Vesa is a pretty lousy driver if you've got an nVidia machine.

Run these commands:

sudo apt-get install nvidia-glx
sudo nvidia-glx-config enable
sudo reboot


If all goes well, this should give you the 3-d accelerated graphics you paid for.

If it does not work, try these commands:

sudo apt-get-install nvidia-glx-new
sudo nvidia-glx-config enable
sudo reboot

Let me know if this doesn't do the trick, and I'll help you work through it.

Best,
Tom

---

### Post by Pumalite on 2007-09-25
It seemed to me, they still have to get a command line first.

---

### Post by HobbDogg on 2007-09-25
> **thomasaaron said:**
> Hey, guys.

Vesa is a pretty lousy driver if you've got an nVidia machine.

Run these commands:

sudo apt-get install nvidia-glx
sudo nvidia-glx-config enable
sudo reboot


If all goes well, this should give you the 3-d accelerated graphics you paid for.

If it does not work, try these commands:

sudo apt-get-install nvidia-glx-new
sudo nvidia-glx-config enable
sudo reboot

Let me know if this doesn't do the trick, and I'll help you work through it.

Best,
Tom

Ok i seem to be having the same problem with my nVidia card as alot of people.

Laptop:
Vista Home Premium
nVidia 8600gs
2 gigs ddr2 667mHz
2-100 gig 7200rpm drives
intel core-2 duo T7300

Now i did try what thomasaaron suggested....when i did the nvidia-glx....i received the same problem....x server can't find a screen....when i use nvidia-glx-new...i get the splash screen then completely black. 

it seems i have tried everything for an nVidia card. I have used the 'vesa' driver, the 'nv' driver and the above mentioned....any help would be great, i kinda need linux to run for my programming class.

     thanks again for helpin the newbie

---

### Post by Pumalite on 2007-09-25
Did you use the Alternate CD?.

---

### Post by HobbDogg on 2007-09-25
i had to use the text version/alternate cd to get ubuntu to install. Fiesty 7.04 would not install using the GUI. That was my first problem.

---

### Post by Pumalite on 2007-09-25
I think your Nvidia is too new. That is your problem. You could try Gutsy Tribe 5, but it is in testing and I cannot recommended for anyone depending on his OS for a living. I'm writing to you from Tribe 5 and it has been great to me, but you have to know it is unstable. The merits are that it recognizes newer hardware.

---

### Post by HobbDogg on 2007-09-25
That is what I was afraid of. I need it to be stable, especially because I am just starting out with linux. Just off the top of your head do u think Gentoo would be a good idea? I would like linux with a GUI that I can start out on. I have been told Gentoo is for more advanced users....also what about Fedora?

---

### Post by Pumalite on 2007-09-25
Friendlier would be LinuxMint (it comes packed with all kinds of stuff) and Mepis.

---

### Post by HobbDogg on 2007-09-25
ill give those a try....and do you feel those will support the newer hardware? Or do you have a feeling that I am going to run into problems like in Fiesty

---

### Post by Pumalite on 2007-09-25
I have found people that post back here saying that they installed with LinuxMint and Mepis. I cannot affirm that they had your same video card.

---

### Post by HobbDogg on 2007-09-25
Ok, cool. I will give Linux Mint a try...i think it looks better. Thanks for your help, i really appreciate it. Farthest i have gotten with help in a long time...Thanks again.

---

### Post by Pumalite on 2007-09-25
You are welcome. Good luck.

---

### Post by thomasaaron on 2007-09-25
OK, I've installed nVidia 8*** cards in Desktops before, and they did require nVidia-glx-new.

So, run these commands:

sudo apt-get install nvidia-glx-new
sudo dpkg-reconfigure xserver-xorg

In the resulting utility, choose the default settings for everything EXCEPT:
1. For the video driver, select nvidia (you might have to scroll up or down to find it.
2. For screen resolutions, select all of them. (Don't worry, it will only allow the ones that your card can provide).
3. Choose "Advanced" options near the end, and then continue to choose all defaults.

When the utility is over:
sudo reboot

Does this work?
Do you get a blue death-screen? If so, look for any error messages that might be useful, or post the output here.
If it goes to a command prompt, enter:
sudo cat /var/log/messages

...and post any interesting output in the last 20 lines here.


If this doesn't work, there are a few good tutorials out there for installing nvidia binaries. I've read on other forums that the 8600gs works under ubuntu. It's just a matter of finding the right solution.

Best,
Tom

---

### Post by HobbDogg on 2007-09-26
> **thomasaaron said:**
> OK, I've installed nVidia 8*** cards in Desktops before, and they did require nVidia-glx-new.

So, run these commands:

sudo apt-get install nvidia-glx-new
sudo dpkg-reconfigure xserver-xorg

In the resulting utility, choose the default settings for everything EXCEPT:
1. For the video driver, select nvidia (you might have to scroll up or down to find it.
2. For screen resolutions, select all of them. (Don't worry, it will only allow the ones that your card can provide).
3. Choose "Advanced" options near the end, and then continue to choose all defaults.

When the utility is over:
sudo reboot


Tom

ok i tried this. Followed every step. I am left with a splash screen of Ubuntu (which i can see the bar fully load) then a flash to a black screen. My computer stays here at this black screen.

What i can't determine is if Ubuntu started and i can't see the desktop....or if it has completely crashed. I don't have anything...not even a terminal to type anything.

Any ideas?

---

### Post by Raderick on 2007-09-26
> **Pumalite said:**
> After Ctrl+Alt+F1, still a blank screen?

Still a blank screen

---

### Post by Raderick on 2007-09-26
> **thomasaaron said:**
> OK, I've installed nVidia 8*** cards in Desktops before, and they did require nVidia-glx-new.

So, run these commands:

sudo apt-get install nvidia-glx-new
sudo dpkg-reconfigure xserver-xorg

In the resulting utility, choose the default settings for everything EXCEPT:
1. For the video driver, select nvidia (you might have to scroll up or down to find it.
2. For screen resolutions, select all of them. (Don't worry, it will only allow the ones that your card can provide).
3. Choose "Advanced" options near the end, and then continue to choose all defaults.

When the utility is over:
sudo reboot

Does this work?
Do you get a blue death-screen? If so, look for any error messages that might be useful, or post the output here.
If it goes to a command prompt, enter:
sudo cat /var/log/messages

...and post any interesting output in the last 20 lines here.


If this doesn't work, there are a few good tutorials out there for installing nvidia binaries. I've read on other forums that the 8600gs works under ubuntu. It's just a matter of finding the right solution.

Best,
Tom

Here's the problem, after the splash screen, I can't do anything. No command line, no typing, no screens afterwards, nothing. The only way to shut down my computer is to unplug the computer and take out the battery, neither of which is healthy to my computer.

---

### Post by HobbDogg on 2007-09-26
> **Raderick said:**
> Still a blank screen

Ok i tried to press CTRL+ALT+F1, i started this at the ubuntu splash screen. I could see everything loading, but as Ubuntu did previously, after it "loads" everything it just goes black.

---

### Post by thomasaaron on 2007-09-26
Well, there is a patch that adds the 8600 card to the nv driver.
[http://gitweb.freedesktop.org/?p=xorg/driver/xf86-video-nv.git;a=commit;h=b68f3ada7bd857095c7652c175a0ba18bf45801f](http://gitweb.freedesktop.org/?p=xorg/driver/xf86-video-nv.git;a=commit;h=b68f3ada7bd857095c7652c175a0ba18bf45801f)
I've got to do a little research, though, to figure out how to apply it.

I wonder if it has already been applied...
Can you try running the sudo dpkg-reconfigure... again, same options as above, except choose nv for the video driver instead of nvidia.


Another thing: are you running Gutsy or Feisty. If you're running Feisty, it might be worth it to try Gutsy.  The steps I'd take would be:

1. use an aternate cd to install
2. if it doesn't fire right up, it'll push you to a command line. If it does this, try the steps mentioned above -- nvidia-glx, nvidia-glx-new, dpkg-reconfigure, etc...

This guy is running an 8600gs under Gutsy, and it would seem he has video...
[http://ubuntu-utah.ubuntuforums.org/showthread.php?t=531107](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=531107)

Best,
Tom

---

### Post by HobbDogg on 2007-09-26
Yes, I am running Fiesty. I was told earlier that gusty isn't stable yet....? Also i believe that i used the alternate cd to install Ubuntu. My computer would not let me install using the GUI CD so i had to use the all text installation. I have tried both nvidia-glx and nvidia-glx-new.

Currently i tried the nvidia-glx-new and that is where  am now, a blank screen after the Ubuntu splash screen, and no command line what so ever.

I looked at the patch...i really have no clue where i would start with something like that.

---

### Post by HobbDogg on 2007-09-27
I give up....i will just wait for the linux group on my campus to make it work saturday

---

