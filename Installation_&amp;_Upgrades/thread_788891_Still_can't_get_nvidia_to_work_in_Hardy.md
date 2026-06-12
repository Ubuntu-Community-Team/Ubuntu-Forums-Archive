---
title: "Still can't get nvidia to work in Hardy"
date: 2008-05-10
forum: Installation &amp; Upgrades
---

### Post by Royke on 2008-05-10
Please can someone make it clear to all people (in plain English) how to install the nvidia drivers. I downloaded the fixed driver, placed it on my desktop and tryed every possible solution that the Ubuntu-forum has offered. Still with no success. How will i ever convince my friends to get Ubuntu when a black screen appears or when there are no advanced desktop-effects:confused: It took too much time and i reinstalled Gutsy out of dispare. I now have triple-boot: Gutsy, Vitsa and Hardy. My graphics card is NVIDIA 7300. All that sudo-ing has brainwashed me, please explain it to me and to possible new ubuntu-users. It is important enough! This kind of problems scares people off on switching from M$, so again: Someone PLEASE HELP:KS

---

### Post by bulldog on 2008-05-10
Go to your menu and choose add/remove,go to system-tools and find the nVidia binary X-Org driver (new driver) install this one.
Then go in your menu to system-administration-hardware-drivers and enable the nvidia driver. Maybe you have to reboot before you can do so.
If enabled right click your desktop,choose change your background and than the tab visual effects,enable the one you want to use and you are done.

---

### Post by Royke on 2008-05-10
Thank you bulldog for your response. I did try this way about 50 times allready, but maybe it works this time (because of updates). I'll let you know if succeeded or not:-P

---

### Post by Royke on 2008-05-10
:( Hello bulldog,
I did exactly what you said, but it's still the same black screen after enabling nvidia-driver, after reboot. It looks like i'm the onlyone left with this problem, so i see just one thing left to do: Reinstall the whole shthouse again and start over. 
But if it don't work then........maybe i'll rewrite the whole kernel myself someday or i'll just trow away that graphics card and use my old 64mb card. (why can't this just be fixed by a simple update, stupid restrictions, AAAAaaaaaaaaah!)
I just want to create music with my UbuntuRoyStudio:guitar:, it did work excellent before. To be honest: Feisty Fawn did better than Gutsy Gibbon and Gutsy does better than Hardy for me, at the moment.
Sorry for my bad advertisement, i love Ubuntu and i'll never leave :wink:

---

### Post by tenmoi on 2008-05-10
Royke,
Please go the Nvidia website and download the right (32 bit or 64 bit, depending on your version of Ubuntu) stable version 169.12 for your Ubuntu. Then open synaptics, click search and type this into the box "linux-restricted". You should then **purge-**remove everything that is linux-restricted-*.
Now open the terminal and do this:
sudo apt-get install build-essential libxft-dev

when you're done, do a ctr+alt+F1 and do
sudo /etc/init.d/gdm stop

Now, I suppose you downloaded the Nvidia driver onto your /home/yourname/Nvidia.run, you do this
sudo sh /home/yourname/Nvidia.run
then follow the instructions on the screen.

Note that you have to accept "yes" from now onwards. If the a message saying that no pre-compiled image is found, just hit yes and get on. When the compilation of the driver is finished you do:
sudo /etc/init.d/gdm restart and there you go!

Wish you best luck!

---

### Post by ztirffritz on 2008-05-10
Have you tried to use Envy to install the nVidia drivers?  It is a program that installs/removes the drivers and configures the xorg.conf file automatically.  It is the best solution that I've found.  Open Synaptic and search for EnvyNG.  Install EnvyNG and then run it.  It will be under Applications, System Tools.  Installation of the nVidia drivers is pretty straightforward.  It will also install ATI drivers, so make sure you select the correct manufacturer from the list on the left.

---

### Post by Royke on 2008-05-10
Many thanks for the explanation tenmoi, i think i understand it now and i will try it tomorrow. 
ztirffritz, I did try Envy but it installed the older driver for the previous kernelversion.
I have a good feeling about removing the linux restricted drivers and after that install the latest that i've downloaded.
So this will hopefully be the last but great Gutsy Gibbon-session for me!
Somewhere tomorrow i will let know how it went ):P

---

### Post by creekchub on 2008-05-10
i to have the same problem.  i an only on my 7th day using any type of linux system.  i have opened up envyng.  enabled the nvida graphics driver, the sudo x thing. here is exactly what happens.  when i reboot after enabling and downloading.  my sign on screen is resized after typing in my password the screen goes black and i get a over range message.  i have to reboot in recovery mode then run xfix to get my screen back at a 800x600 resolution.  
so far i like what i see.  this is on a totally new build i have not graphics card just onboard nvidia 6100 chipset.  so you are not the only one left with this problem

---

### Post by BoredOutOfMyMind on 2008-05-10
> **ztirffritz said:**
> Have you tried to use Envy to install the nVidia drivers?  It is a program that installs/removes the drivers and configures the xorg.conf file automatically.  It is the best solution that I've found.  Open Synaptic and search for EnvyNG.  Install EnvyNG and then run it.  It will be under Applications, System Tools.  Installation of the nVidia drivers is pretty straightforward.  It will also install ATI drivers, so make sure you select the correct manufacturer from the list on the left.

I have 4 yrs and many different times have installed upgrades of hardware and  software.  Envy does not work for me here on 8.04 It was a clean 07.10 install with "sudo aptitude update -d" and update-manager doing the upgrade. 

Here for anyone else is the direct link to the driver from Nvidia

[http://us.download.nvidia.com/XFree86/Linux-x86/169.12/NVIDIA-Linux-x86-169.12-pkg1.run](http://us.download.nvidia.com/XFree86/Linux-x86/169.12/NVIDIA-Linux-x86-169.12-pkg1.run)

---

### Post by infinideas on 2008-05-11
> **tenmoi said:**
> Royke,
Please go the Nvidia website and download the right (32 bit or 64 bit, depending on your version of Ubuntu) stable version 169.12 for your Ubuntu. Then open synaptics, click search and type this into the box "linux-restricted". You should then **purge-**remove everything that is linux-restricted-*.
Now open the terminal and do this:
sudo apt-get install build-essential libxft-dev

when you're done, do a ctr+alt+F1 and do
sudo /etc/init.d/gdm stop

Now, I suppose you downloaded the Nvidia driver onto your /home/yourname/Nvidia.run, you do this
sudo sh /home/yourname/Nvidia.run
then follow the instructions on the screen.

Note that you have to accept "yes" from now onwards. If the a message saying that no pre-compiled image is found, just hit yes and get on. When the compilation of the driver is finished you do:
sudo /etc/init.d/gdm restart and there you go!

Wish you best luck!


Hi guys, I have got a similar problem. Using a Viewsonic vb930b LCD monitor plus a Nvidia Gforce 4 Ti4200 display card, I've been asked by Ubuntu to configure my display settings everytime I restart after my upgrade to Hardy. I've tried Royke's solution, but got held when try to compile the Nvidia package. It said the kernal compiler is 4.1 and diff. from the 4.2 running kernal. 

I've not idea how to fix that and can only go back to graphical mode and hope for the best. Now noticed that I can't even enable proprietary drivers since with Royke's solution I must have removed the drivers now I have no idea how to get my display to go to work.......please help~!

---

### Post by veneroso on 2008-05-11
Well, having just figured out this problem for myself, I thought I'd throw in what worked for me into the hat.

My system uses an older Geforce MX 200 card, so I needed to use the new-legacy driver.

None of the mainstream solutions helped me, including envy, so I was forced to take the manual approach.  I cleaned up all of the linux-restricted packages (to avoid conflicts) and removed envy(since it was useless to me).

I used version 96.43.05 from the website, and then I got the following error:

```
sh: /sbin/lrm-video: not found
FATAL: Error running install command for nvidia

```

Referenced here:

[https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/149934](https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/149934)

My best guess as to the cause of this is that removing the linux-restricted package does not clean up all of its modprobe configuration files.

As the link suggests, comment out (using the #) the lines in /etc/modprobe.d/lrm-video.  This allowed my X server to load with full nvidia (and 3D support).

I know it may not be a pretty fix, but it was either this or re-install kubuntu (and programs, files, etc), as the default drivers failed me after this upgrade.

---

### Post by Royke on 2008-05-11
Hello people, i have some great news: It is working!!!
The explanation of tenmoi did it for me.
This is exactly what i did:

First i downloaded the updated(beta)driver from the NVIDIA-site. It is important to have the right version for the latest linux-kernel. The driver is: NVIDIA-Linux-x86-173.08-pkg1.run and i put it in my home-directory

Second i opened synaptec and removed everything with linux-restricted in it's name.(complete removal, config-files included)

Third i took a piece of paper and a pencil and wrote down what tenmoi said to type in terminal (because after ctrl+alt+F1 will hide the fancy desktop, this website included!) I wrote down and typed in later:
Ctrl+ALT+F1
sudo /etc/init.d/gdm stop
sudo sh /home/yourusername/NVIDIA-Linux-x86-173.08-pkg1.run
*now the NVIDIA installation started asking some questions, i couldn't believe my eyes:lolflag:*
Finally i typed what i wrote down:
sudo /etc/init.d/gdm restart
I then immediately tryed-out the extra visual effects, and see now a new system rising:popcorn:
I hope this solution works for all, if not please let it know. Today my new UbuntuRoyStudio will shake the neighborhood, that's for sure:guitar:

---

### Post by gnivler on 2008-05-11
> **tenmoi said:**
> Royke,
Please go the Nvidia website and download the right (32 bit or 64 bit, depending on your version of Ubuntu) stable version 169.12 for your Ubuntu. Then open synaptics, click search and type this into the box "linux-restricted". You should then **purge-**remove everything that is linux-restricted-*.
Now open the terminal and do this:
sudo apt-get install build-essential libxft-dev

when you're done, do a ctr+alt+F1 and do
sudo /etc/init.d/gdm stop

Now, I suppose you downloaded the Nvidia driver onto your /home/yourname/Nvidia.run, you do this
sudo sh /home/yourname/Nvidia.run
then follow the instructions on the screen.

Note that you have to accept "yes" from now onwards. If the a message saying that no pre-compiled image is found, just hit yes and get on. When the compilation of the driver is finished you do:
sudo /etc/init.d/gdm restart and there you go!

Wish you best luck!

Thanks for the tips, I was having problems with conflicts apparently and the purge did the trick.  Up and running with the 173 beta driver now.

---

### Post by tenmoi on 2008-05-11
Very happy I could help. 
That has been the way I use to install Nvidia driver. 
One reminder: 
If you should upgrade the kernel to a newer version like 2.6.24.17, you will have to first uninstall the nvidia driver and to do that:
sudo /etc/init.d/gdm stop
then
sudo sh /path to nvidia driver.run --uninstall
and then you boot into Ubuntu with the new kernel and then recompile the NVidia module driver again.

---

### Post by tenmoi on 2008-05-11
To infinedeas:

I quote "Hi guys, I have got a similar problem. Using a Viewsonic vb930b LCD monitor plus a Nvidia Gforce 4 Ti4200 display card, I've been asked by Ubuntu to configure my display settings everytime I restart after my upgrade to Hardy. I've tried Royke's solution, but got held when try to compile the Nvidia package. It said the kernal compiler is 4.1 and diff. from the 4.2 running kernal."

I just cannot figure out what method you followed. 
And to resolve the version mismatch error, you should log in to Ubuntu with the newest kernel, do a sudo update and sudo upgrade and then follow my instructions. 

*Don't ever try to log in using the older kernel and compile anything there.*

wish you best of luck

---

### Post by shadowber on 2008-05-18
Oh wow!!!!
Thank you Thank you Thank you Tenmoi!!!!
I have ubuntu working on 2 comps, and one I never had a problem with, the other would not install my nvidia card...... and I knew how much better ubuntu could be....

so after 6 months of on and off trying, I finally get clear instructions, and voila... it works like a dream!

it should be noted that while installing the driver, there is no clear indication of what you are choosing (yes, no, etc.) so when the choice is surrounded by white (or gray, wtvr) that is what is selected...

---

### Post by Cheeseroue on 2008-05-18
These instructions worked fine for me up until the point where I restart gdm. Then Ubuntu goes into low-graphics mode, saying that it couldn't detect my graphics card.

Any suggestions? I need the NVIDIA drivers to properly get TV out working...

---

### Post by Radoka on 2008-05-20
I also have a NVIDIA 7300 card that refuses to work and I'm a pretty experienced linux user after at least 10 years with the OS. First of all I tried the usual way to just check the box that says there is drivers avaiable for my hardware. After reboot the screen is black and nothing at all can be done. No response of keyboard activity... nothing. So I power of and uses recovery mode to change "nvidia" to "nv" in my xorg.conf tostart all over again. Next option is Envy but it gives me completely the same result. I've also tried to install it the way tenmoi explained at least 10 times after the final realease of Hardy Heron. It's starting to get annoying as ****!!! I can't play World of Warcraft any more and the computer doesn't feel as fast as it should be with hardware renderig.

Now... Any suggestions? Or am I forced to downgrade to Gutsy? The card worked fine with all Ubuntu releases since 5.10.

Edit: Forgot to say that my version f Ubuntu is Ubuntu Studio with the rt-kernel and I got the Amd64 version.

---

