---
title: "Graphics screwed on GeForce 6600"
date: 2007-01-21
forum: Installation &amp; Upgrades
---

### Post by Blednik on 2007-01-21
Dear Ubuntu users.

I have recently decided to try out Ubuntu linux. I have downloaded a 6.10 DESKTOP ISO image and burned it on a cd with no probs (all MD5 sums matched). However when I tried to install the operating system I encountered a number of frustrating problems. So before my patience completely runs out and my last nerve snaps (which is very thin already) I'd like to ask for some help. ](*,)

Allow me to tell my tale. I began by booting from the CD. The choice menu appeared fine so I choose to run/install ubuntu. The installer loaded the vmlinuz thing and after that a loading screen appeared that looks much like the XP one. After the loading screen finished I got some weird graphics displayed on my screen and the monitor telling me an "out of range" error. I thought that was a standard loading process, but after leaving it alone for a while longer nothing changed. I did hear some sound from my speakers at the point where gnome desktop was supposed to load, but the graphics were messed up. At first I thought my LCD monitor was the problem, but I ruled that out by using a different monitor and the same problem occurred. I also tried GFX safe mode and multiple other resolutions (VGA was default). No, the PC didn't lock up when the weird graphics displayed because I could see it change a bit when I moved my mouse. Additionally tty1 (Ctrl+Alt+F1) had similar graphic problems.

Finally I managed to find a good and working resolution at 1024x768x32 (16 bit didn't work). The desktop loaded fine now, but the mouse cursor didn't show up tho the mouse worked fine as I could click and interact with the desktop. Anyway I managed to install Ubuntu to HDD and after reboot it gave me the same GFX problem, however, this time no option to choose resolution mode. So now I have an installed Ubuntu that I cannot boot into Gnome. The recovery mode will boot into console fine and I used this to poke around a bit. Managed to get the networking working. Still, I use dula boot and use Windows XP to downlaod files. In XP, the graphics card works flawlessly.
PS. The screwed graphics look a lot like the ones displayed here: [http://ubuntuforums.org/showthread.php?t=324414](http://ubuntuforums.org/showthread.php?t=324414)

I've searched the internet for a solution and I found out it might be the fault of my graphics card GeForce 6600. An interesting article can be found here: [http://www.uberdose.com/kbase/ubuntu-and-nvidia-geforce-6600/](http://www.uberdose.com/kbase/ubuntu-and-nvidia-geforce-6600/)
I did try to install the newest linux drivers from nVidia website, but as expected something was to go wrong. There were no precompiled things on the website available and the installer failed to compile (no libc availavle error or something like that). So now I'm stuck with a semi-working installation of Ubuntu and a drop of patience left before I go /format.

It should be easy to fix as long as the recovery mode boots fine, but I mysef are fairly new to linux and I don't think I can manage on my own. Can you assist, please?

reg.

---

### Post by taurus on 2007-01-21
I have a XFX GeForce 6800XT and didn't have any problem installing and running it.  Of course, I used the alternate CD to install it and used this guide to install nVidia driver for my card.

[http://albertomilone.com/driver.html](http://albertomilone.com/driver.html)

---

### Post by Blednik on 2007-01-21
The main reason I went for desktop is because I wanted to try Beryl. Are you suggesting I try the alternate CD and what difference does it bring?

---

### Post by Duppy on 2007-01-21
I dont think its a problem with your GFX card.

What are the other specs?

---

### Post by Blednik on 2007-01-21
Let's see now...

HDD: 80GB Maxtor IDE
- Microsoft Windows XP SP2 (partition 1)
- Ubuntu 6.10 (partition 2)
CPU: AMD Athlon XP 2400+ 2GHz
RAM: 1024 MB DDR
Mobo: Gigabyte K7 Triton nVidia nForce 2 (model name: GA-7N400S-L)
GFX: nVidia GeForce 6600 AGP 8X 256MB DDR / 128 bit (model name: GV-N66256DP)

Well when I said problem with my GFX card I really meant problem with its driver ^^

---

### Post by Blednik on 2007-01-24
Solved. See this thread: [http://www.linuxquestions.org/questions/showthread.php?t=521743](http://www.linuxquestions.org/questions/showthread.php?t=521743)

---

