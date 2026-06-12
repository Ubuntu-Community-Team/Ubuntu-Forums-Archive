---
title: "How can I change resolution in recovery mode?"
date: 2005-10-04
forum: Installation &amp; Upgrades
---

### Post by Samurai Whitey on 2005-10-04
Hello all,
I am a noob at linux, and after a friend successfully installed and updated Ubuntu and all drivers he accidentally left my Display settings at a resolution that my old monitor cannot deal with. So when I boot ubuntu, my monitor goes nuts lol. Can someone tell me how i can lower my resolution so i can boot with the x-windows gui? I am using a nvidia geforce 6600gt agp graphics card with updated drivers.
TIA

---

### Post by darkmatter on 2005-10-04
[QUOTE=Samurai Whitey]Hello all,
I am a noob at linux, and after a friend successfully installed and updated Ubuntu and all drivers he accidentally left my Display settings at a resolution that my old monitor cannot deal with. So when I boot ubuntu, my monitor goes nuts lol. Can someone tell me how i can lower my resolution so i can boot with the x-windows gui? I am using a nvidia geforce 6600gt agp graphics card with updated drivers.
TIA[/QUOTE]

After logging in as root in, ener the command

```
dpkg-reconfigure xserver-xorg
```

This will launch an ncurses interface to help configure the x server. Have the specs for your monitor handy, as you will need to input the horizontal and vertical sync ranges. The dialog will also allow you to select the resolutions to use. (hint, deselect (using the space bar over a highlighted entry) any resolutions over that which your monitor can handle by removing the '*' from beside the entry)

Hope that helps. If you still have any problems, be sure to post back.

Good Luck.

---

### Post by Samurai Whitey on 2005-10-04
Hi Darkmatter, ty for the advice! I did some searching and I realized that I could login even though the monitor was crazy. After I got in, I was able to hit ctrl+alt ++ and switch resolution. however, when I rebooted I got the same problem, but only at the login screen; the desktop retained the proper settings. So I am wondering if your solution will fix the resolution at the login screen? Thanks for the help.

---

### Post by darkmatter on 2005-10-04
[QUOTE=Samurai Whitey]So I am wondering if your solution will fix the resolution at the login screen? Thanks for the help.[/QUOTE]

Yes. It should, as it will reconfigure the xserver itself rather than simply changing the desktop resolution.

You have to remember that X starts before GDM, so GDM is dependant upon xorgs configuration.

Since you are able to use the desktop, you can just run
```
sudo dpkg-reconfigure xserver-xorg
```
from a terminal under your user account. You will be asked for your password, then the dialog will open.

---

### Post by Samurai Whitey on 2005-10-04
Thanks, I am going to try it now! after I get this fixed, I am going to see about getting my other monitor to display as well lol. Thank you for the advice; I can see that this is a great community...

---

### Post by darkmatter on 2005-10-04
Is everything working now?

---

### Post by az on 2005-10-04
You do not need to reboot.  Run

init 2

from recovery mode to get back into desktop mode (runlevel two).

---

### Post by Samurai Whitey on 2005-10-05
Yes everything seems to be working well! I must say that moving from M$ to Linux is a humbling and exciting experience. Thanks for the help, although I am certain I'll be asking more questions later :)

---

### Post by darkmatter on 2005-10-05
[QUOTE=Samurai Whitey]Yes everything seems to be working well! I must say that moving from M$ to Linux is a humbling and exciting experience. Thanks for the help, although I am certain I'll be asking more questions later :)[/QUOTE]

It's always humbling at first. I am glad to hear that everything worked out for you.

Oh...Welcome to Ubuntu Forums.;)

---

### Post by raspa_sete on 2005-10-05
(i have a similar problem)
My laptop monitor upon instalation couldn't use the whole screen, only a small square at the center (no that small, but not the whole screen) the problem was with the fact that the computer coul'd estimate the screen refresh rate (or something of the kind) so it sticked with the definitions it knew that would work

So I added this
```
HorizSync       31.5 - 48.5
```
into the "Monitor" section in the xorg.conf file.

But I still have the same problem when I go to the console with ctr+alt+F1:F6.
the console doesn't occupy the entire screen. I tried to do the
dpkg-reconfigure xserver-xorg as sugested but it solved nothing.

sugestions?

---

### Post by az on 2005-10-05
[QUOTE=raspa_sete](i have a similar problem)

But I still have the same problem when I go to the console with ctr+alt+F1:F6.
the console doesn't occupy the entire screen. I tried to do the
dpkg-reconfigure xserver-xorg as sugested but it solved nothing.
sugestions?[/QUOTE]
That is a framebuffer thing.  You need to tell the console framebuffer to use that whole screen

Hit escape when you boot and add this to the kernel line

vga=771


If that works, add it to your kernel options in /boot/grub/menu.list
and run
sudo update-grub

---

### Post by raspa_sete on 2005-10-05
> vga=771
If that works, add it to your kernel options in /boot/grub/menu.list

this code comes from the menu.list in the grub directory, am i to add the vga=771 exactly where?  after the "splash" word in the kernel line?

> 
title           Ubuntu, kernel 2.6.10-5-386
root            (hd0,3)
kernel          /boot/vmlinuz-2.6.10-5-386 root=/dev/hda4 ro quiet splash
initrd          /boot/initrd.img-2.6.10-5-386
boot


(sorry to be asking this. but i don't know how to work with grub and if anything appens i don't how to "rollback" to the previous kernel configuration, I was really thinking in changing the menu.list file before testing it in the grub)

cheers!

---

### Post by az on 2005-10-05
Sorry, I forgot to mention that you can edit the grub menu on-the-fly.  (I have a cold - poor me!)

The changes are not permanent.  They just apply for that boot.

Hit escape and then pick the default boot option

Instead of hitting enter, hit "e" to edit it

Go to the kernel line and change it to

kernel /boot/vmlinuz-2.6.10-5-386 root=/dev/hda4 ro quiet splash vga=771

Hit enter to and then "b" to boot.

If that solves your problem you can edit the menu.list to make the changes permanent.  You need to edit the default kernel options (it is commented out, but that does not apply - it is read then you run update-grub)

---

### Post by raspa_sete on 2005-10-07
humm, thanks.

well, adding your line, the console is now bigger but still not he whole screen (now the console occupies half space more with relation to the unoccupied space from before).

I searched a little bit and ended by writing "vga=ask", and got a list of options (none of them near 771) I tried some, but none of them increased the dimensions of the console (they where about the definition of columnsxlines to be presented in the console) bah...

I also searched in my linux pdf files from "frame buffer" and got nothing and the only reference to the vga option was "normal, extended or ask".

more help please!

---

### Post by raspa_sete on 2005-10-07
aha my friend, i went an researched some more, and found this marvelous answer in the fedoraforum

> vga=794 means that you are trying to get into 1280x1024 resolution. Is that what you want? I know most laptops do not have screens of that resolution, but instead either 1024x768 or 1400x1050. I suggest changing vga=794 to vga=791, which will give you 1024x768.

So I don't really know to which screen definitions the 771 option corresponds.

vga=794 -> 1280x1024
vga=791 -> 1024x768

so ill try with the 791 options then ill say if it worked

EDIT: hum, looks like vga = 791 -> 1024x768x64k  (not so marvelous any more :))

EDIT2: could anyone give me a book/site reference where I can get a copmlete explanation about this?

---

### Post by Milkman Mr. Miller on 2005-10-11
[QUOTE=darkmatter]After logging in as root in, ener the command

```
dpkg-reconfigure xserver-xorg
```

[/QUOTE]

Okay I might be just stupid, but it sounds like solving my problem aswell. I have an old monitor, and my screen behaves just like the one of Mr. Samurai.

Now, I thought maybe I can start up my Ubuntu in VGA-mode and change my settings then. Or is that just plain impossible?

If so, how can I log in as root in? What do I need to press whilst booting? It never asks me what I want, it just starts up (by the way I'm now using Breezy Badger, still this problem occurred also with other Linux distributions)

Thanks in advance.

---

### Post by raspa_sete on 2005-10-11
i found this table with the spec you can pass to the vga option in the kernel boot line.

                  Resolution in pixels
Color depth       | 640x480 - 800x600 - 1024x768 - 1280x1024
256        (8bit)   |  769       -      771      -     773      -    775
32000     (15bit)|  784       -      787     -      790     -     793
65000     (16bit)|  785       -     788     -      791     -     794
16.7 Mill.(24bit) |  786       -    789        -   792     -     795

(I am assuming you have grub boot loader, if you do not, you have to find out the command line that boots up the linux kernel. if you find out, tell me :) )

when you are in the grub boot menu, press "e" and you can edit the hilighted line, then press "e" again to edit the line with the boot option. and add the vga=something (one of the numbers above) option and if it boot alright, go to the command line and:
```
sudo pico /boot/grub/menu.lst
```
and add the vga=something you used to the boot line! save and thats ok!

if you want to have the root shell do "sudo -s".

---

### Post by Milkman Mr. Miller on 2005-10-12
Well, then again, thanks. I haven't been able trying it out - after a long day sitting in front of the computer I went kinda crazy -lol- so I spent the evening playing board games and staring at the ceiling.

But fresh new morning, fresh new start and it feels like I am being a lot closer to the answer to my question with your advice, dear Raspa. So now I'm trying to find out what it means to my situation.

In my case, I've got some videocard from the time millennium bugs came alive, say january 2000. But my monitor is somewhat older, and in my opinion the "problem". Let me give some specs for my monitor (obtained it elsewhere on the net, incredible what you can find nowadays).

My monitor (building year 1993) is a SAMTRON, SC-428 TXL +.
It's 14" screen with a 13" viewable image, with a 0,28 mm dot pitch (whatever that may be). 
H-frequency = 31,5 - 48 Khz / V-frequency: 50-90 Hz
Video bandwith = 65 Mhz
Dimensions and weight: Height: 14, Width: 14, Depth: 15.
Maximum resolution: 1024 x 768.

When I turn on my computer, Breezy Badger being successfully installed, I get these nice texts saying everything is okay (except for that i do not have internet access and that's right). I also get the very nice Ubuntu splash screen, i like the colouring!
But then the login screen is being wicked and mangled; it is shown six times on my screen and everything seems to be original image and mirrored at one time.  I can manage to login, just by entering login name and then my password. Even after log-in, this nice dark screen comes up also being mangled, still six times in one screen and with all the mirrored ones, too (so 12 in total :P).

According to the explanation you gave, I should choose for the VGA=*x*(something) that corresponds with my screen depth of 15 (15bit??) and max resolution of 1024 x 768. **Should **I then go for **VGA=790** in this grub boot loader of which you speak?

Problem is: according to the definition Google gives for Grub (GRand Unified Bootloader), that it is used for dualbooting a system. But unfortunately I only installed Breezy Badger on this computer of mine (now working on a school computer), so there's no need for (and no sign of) any GRUB boot loader.
That might explain why I can't fit in any of the solutions given in the forum.

**Or is there any shortcut key I can press during start up (such as F8 with windows) for showing up a command prompt (or something like that) in which I can type in things like sudo pico /boot/grub/menu.lst ?**

---

### Post by Milkman Mr. Miller on 2005-10-13
I already managed to fix the most important part of the problem, the mangled screen. I should've waited until I tried out the options Raspa gave me, or tried anything at all.

I managed to get the menu working by simply pressing ESC during the beginning of startup (it even says: "press esc for menu" or something simular). I tried to edit a few lines, but it didn't seem to work, because my screen was still mangled up and thus not what I want it to be.
But suddenly I remembered the combination [CRTL]+[ALT]+[+] from a topic elsewhere on this forum, with which you can switch between 3 monitor (or video card) settings. Great!
So probably this is the main important thing to do when having mangled up screens. Now its up to me changing the resolution from 640x400 to an higher one. But for me, until this point my problem is solved, and I will manage to find solutions to this resolution problem elsewhere on the forums.
Thanks!

---

### Post by r4wMUnt34q on 2007-12-18
Hello guys,

Im new to ubuntu, I have it for several days, I must say I am really satisfied with it, but I was trying to use a data projector and it resized my resolution to 800x600 after I hit the Fn+F8. I didnt want it to happen, so I tried to setup a secondary screen and restart my pc. Now, when Ubuntu is done loading, the logging screen has a unreadabla graphics, I cant recognize my mouse, only the vertical position, and I can log in, but I still cant recognize whats on the screen without remembering what I have done and so on.
I know not how to repair this via recovery mode since im a total noob into linux yet. I may try to put the command mentioned above into the terminal, because I have a keyboard shortcut on terminal, but Im not sure if it asks me roots or mine password and if I will type it right... Any help appreciated!

P.S.: I may only need to know how to change my primary screen resolution to generic, plug n play, 800x600 in the recovery mode as root, thanks loads ! I dont know if I can edit some files from windows, I found just an utility to read ext3 FS.

---

