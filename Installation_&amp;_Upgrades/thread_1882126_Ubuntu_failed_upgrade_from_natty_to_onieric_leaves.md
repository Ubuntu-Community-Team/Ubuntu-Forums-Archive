---
title: "Ubuntu failed upgrade from natty to onieric leaves OS unusable"
date: 2011-11-16
forum: Installation &amp; Upgrades
---

### Post by artemi89 on 2011-11-16
Hello,

I am not an expert user by a long shot, I have used Ubuntu often in the college computers for programming and other things (I study physics, so programming means simulation programs with fortran, nothing helpful for this) so when I had to install Linux to use some astronomy programs to process and analyse data I went with an Ubuntu 30Gb partition using wubi. In other words: I may not be a complete beginner but if the talk gets technical I will get lost pretty fast (I at least understand and use frequently the terminal, but not much more).

So the problem is the following, I installed the Natty Narwhal version of Ubuntu without problems, managed to install every program I needed and got things working right after MUCH work (astronomer-made spaghetti-programs are nightmares to setup), and then Oneiric Ocelot comes out and the Update Manager prompts me to upgrade my distro. The first few attempts end up canceled because the connection jumps or something, but 2 days ago I finally get to download everything and begin the install, and that's when everything goes to hell. Mid-install the installer begins to popup warnings about files it could not configure or had errors, i copied down which ones:

-gconf2-common (it said something about exit status 107, I think)
-libconf2-4
-libedataserver1.2-15
-libcamel-1.2-29
-libebook1.2-12

After asking me to send reports about the errors and me doing so the manager says that due to an excessive amount of errors the install is canceled (the progress bar was around half full) and it will restore the system to before the installation, but when I boot the Ubuntu partition I get (apart from taking a significantly longer time to boot) the login screen from Oneiric Ocelot!
It accepts my password and user but the desktop showed is with the "default" purple color (the same one that's on the second boot choice screen that appears immediately after selecting Ubuntu instead of Windows in the bios screen) instead of either the images I chose for the desktop or the default one. More importantly, the only thing that appears are the icons for the files and folders that were on the desktop, and apart from the pdf files that show the text preview all the icons are "blank", that is, they appear as a blank page with a corner folded; there is no bar or menu of any sort, only purple and "blank pages" shown.
Firefox does launch when double-clicking its icon, but it cannot connect to the internet, as i do not see the icon for the networks i don't know exactly why, but it should be able to connect to my home Wifi since it's set to do so automatically.

Furthermore, as there is no menu i cannot shut down the computer by software, any combination of keys i have thought of (alt+f4, ctrl+alt+del, ctrl+alt+esc) have absolutely no effect, so i have to manually press down the power button 5 seconds to shut it off manually.

Incidentally, all this is restricted only to the Ubuntu partition, there has been no effect that i can discern in the Windows partition (from which I am writing as I cant access the internet from Ubuntu).

If I had to guess what went wrong I'd have to say that since from the first attempt (first files downloaded) to the final some weeks passed that maybe some of the files already downloaded were changed and when installing the program went crazy from unmatching instructions on the files, but it's purely my speculation.

To sum it all up my Ubuntu is in an unusable state and I urgently need it in working order to proceed with the work that's piling up. Given that it took me weeks (really) to finally get all the programs properly installed, set up, and running, if you managed to get it back to how it was before attempting to upgrade without the need to wipe everything clean you would be my new gods.

If you need additional information or photos just ask and I'll do my best to provide.

Thank you in advance for any assistance.

----------------
I am using a laptop with an i-7 2630 processor, 64 bits system, 8Gb RAM, graphics card Nvidia GTX460 (I properly installed the propietary controllers for the Nvidia card)

---

### Post by Mark Phelps on 2011-11-17
Don't know that this will work -- but if it does, at least you should get a working desktop.  I believe you can launch a terminal by pressing Ctl-Alt-t:

[http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html]("http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html")

---

### Post by artemi89 on 2011-11-17
Thank you for the fast response!

I tried to follow the steps on the link you gave me but I have not been able to complete it because I do not have access to the internet on Ubuntu, so as soon as apt-get had to download files it said it couldn't. Here are the detailed steps i have taken:

First i got to the tty1 with ctrl+alt+f1, checked that unity was installed (it was), so I installed the ubuntu-desktop as was recommended, the manager said it didn't need to install anything and proceeded, but the problem wasn't solved, so following the guide I checked for 'compiz'; a list with 'compiz' came out but 'compizconfig-settings-manager' wasn't there so I attempted to install it with apt-get, but that's when it complained that I did not have access to the internet, so I could not proceed.

On another note, when logging in the screen looks the same as it should, and I have found that clicking on the wheel next to my username I can change the desktop style, the options are Ubuntu, Ubuntu 2D and recovery. If I login with Ubuntu 2D I get the same desktop but with a top and side bar, but the top bar is empty unless I run some program and it shows the menu for that specific program, but I can use the terminal (I couldn't get it to show on the "Ubuntu" desktop with the key shortcut) and it appears that the astronomy programs work (they're all terminal-based), though I cannot ensure they do in their entirety. This takes the rush out as it appears I will be able to continue work regardless, but I certainly would like to fix the problem completely.

I managed to get some screenshots of the desktop and store them on an external disk, so I added them in case they're useful.

Thank you again.

---

