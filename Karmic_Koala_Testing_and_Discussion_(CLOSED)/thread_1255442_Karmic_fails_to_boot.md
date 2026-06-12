---
title: "Karmic fails to boot"
date: 2009-09-01
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by ELD on 2009-09-01
For the past few days i have been trying each daily cd and none of them have booted for ubuntu, kubuntu karmic boots and installs perfectly.

Ubuntu goes past the two loading screens, first the normal one where it shows a side to side progress bar, then it goes to a new one where there is a weird white line moving up and up and then the screen flickers and then it goes back to what seems the same loading screen only stuck and nothing happens.

---

### Post by rbmorse on 2009-09-01
See bug 419126 in launchpad.  Seems to affect users with ATI R6XX or newer GPUs.

---

### Post by ELD on 2009-09-01
Yeah i'm sure that is my bug, thank you for the information, i hope this will be fixed by alpha 5 or this seems to single out a lot of users with similair cards to me.

---

### Post by Philip Farrugia on 2009-09-04
Can't get alpha 5 to boot from live cd. Stalls the whole pc at the time it should be showing a login screen or desktop. ATI HD4670. So probably same bug? Tried safe graphics mode but same thing. Annyone got a fix yet???

---

### Post by tsger on 2009-09-05
Same problem here, ATI HD3670.  GDM login screen is stuck in a loop.  No workaround found yet!

---

### Post by ELD on 2009-09-05
I tried todays daily cd and still the same issue, second loading screen has a loading bar, flickers back to that screen but loading bar is static and nothing happens still :\

If anyone has a decent workaround for now or even a fix i would be greatful.

---

### Post by taavikko on 2009-09-05
> **ELD said:**
> I tried todays daily cd and still the same issue, second loading screen has a loading bar, flickers back to that screen but loading bar is static and nothing happens still :\

If anyone has a decent workaround for now or even a fix i would be greatful.

It makes no difference if you test the daily CD a week from now if the bug isn't fixed.

Use older alpha to install, and then tweak xorg.conf to disable DRI.

---

### Post by ELD on 2009-09-05
> **taavikko said:**
> It makes no difference if you test the daily CD a week from now if the bug isn't fixed.

Use older alpha to install, and then tweak xorg.conf to disable DRI.

That is what i was checking for, to see if the bug has been fixed as i saw mention of it, but the changes have not been applied yet.

---

### Post by taavikko on 2009-09-05
> **ELD said:**
> That is what i was checking for, to see if the bug has been fixed as i saw mention of it, but the changes have not been applied yet.

The bug isn't fixed yet. There is only a suggestion from few users to upload to repos the packages from xorg-edgers.

but that brings new bugs...

---

### Post by ELD on 2009-09-05
Ah right i got a little ahead of myself then, i will bookmark the bug and keep an eye on it.

---

### Post by tsger on 2009-09-05
OK, here's my workaround.  Somewhat convoluted, but it works!

1.Install Ubuntu 9.10 Alpha 5 from live CD.
2.Upon first boot, login to xterm (not Gnome).  You will see the choice to choose the xterm session after you click on your user name, but before you enter your password.
3.Ctrl+Alt+F1 takes you to command line (choose root console without networking).
4.To kill the X Server (if you're not root already, prepend with sudo), type ```
telinit 1
```
5.Now do ```
Xorg -configure
```.
6.Then copy the file that was just generated to /etc/X11/xorg.conf
7.Now do ```
nano /etc/X11/xorg.conf
```
8.Add the following line under the Device section: ```
Option “DRI” “off”
```
9.Ctrl+O to save the file
10.Ctrl+x to quit nano.
11.Reboot: ```
shutdown -r now
``` 
12.Upon reboot, you should be able to log in to the desktop without the annoying loop in GDM.
13.Get connected to the internet, then upgrade any available packages via Synaptic.
14.Reboot (may not be necessary, but I did)
15.Go to System – Administration – Harware Drivers.  Enable the ATI driver.
16.Reboot.
17.Now you can edit /etc/X11/xorg.conf to comment out the line you added earlier.  ```
#Option “DRI” “off”
```
18.Reboot.  Still logs in to the Desktop!
19.Double check your /etc/X11/xorg.conf file.  I noticed that enabling the proprietary ATI driver added a new xorg.conf file, which still had the Option DRI turned off.  I commented it out again and rebooted.  Still good!

Hope this helps you!

---

### Post by ranch hand on 2009-09-05
> **tsger said:**
> OK, here's my workaround.  Somewhat convoluted, but it works!

1.Install Ubuntu 9.10 Alpha 5 from live CD.
2.Upon first boot, login to xterm (not Gnome).  You will see the choice to choose the xterm session after you click on your user name, but before you enter your password.
3.Ctrl+Alt+F1 takes you to command line (choose root console without networking).
4.To kill the X Server (if you're not root already, prepend with sudo), type ```
telinit 1
```
5.Now do ```
Xorg -configure
```.
6.Then copy the file that was just generated to /etc/X11/xorg.conf
7.Now do ```
nano /etc/X11/xorg.conf
```
8.Add the following line under the Device section: ```
Option “DRI” “off”
```
9.Ctrl+O to save the file
10.Ctrl+x to quit nano.
11.Reboot: ```
shutdown -r now
``` 
12.Upon reboot, you should be able to log in to the desktop without the annoying loop in GDM.
13.Get connected to the internet, then upgrade any available packages via Synaptic.
14.Reboot (may not be necessary, but I did)
15.Go to System – Administration – Harware Drivers.  Enable the ATI driver.
16.Reboot.
17.Now you can edit /etc/X11/xorg.conf to comment out the line you added earlier.  ```
#Option “DRI” “off”
```
18.Reboot.  Still logs in to the Desktop!
19.Double check your /etc/X11/xorg.conf file.  I noticed that enabling the proprietary ATI driver added a new xorg.conf file, which still had the Option DRI turned off.  I commented it out again and rebooted.  Still good!

Hope this helps you!

This is handy to have all in one place.

The problem that I am having now is that the grub update has it so that nothing is booting in 64bit installs.  I have 6 variations.  I 1 that would boot and have been working from it on the others and building custom menus for it.  I now have 2 that boot.

I hope to have them up and running in time for A6.

---

### Post by ranch hand on 2009-09-06
I have the bugger so that it will boot to the GDM and then freeze.

If I edit xorg.conf so that it reads - Driver   "vesa" - then it will try to boot and end with a terminal login allowing me to update.

Did that.

Changed back to the "DRI"  "0" setting and now I can boot to the recovery menu.  If I hit resume normal boot I go right to the frozen login screen.

When I say frozen I do mean frozen.  There are 2 ways to get out;
1= unplug the bugger
2= alt SysRq b  (I believe that SysRq is pronounced SysWreck)

I have 5 9.10 variations on this 94bit dedicated drive.  This is (was) a clean install of A2 updated daily.  It is up to date now.

My Radeon HD 2400 PRO is not covered so I never use the driver anyway, just makes things go bad.

I currently have 3/5 installs working.  One is unupdated from -5 and it is handy to change to as boot/root when every thing goes south.  One is a clean install of A4 updated daily.  The other is an upgrade from 9.04/A5 updated daily.

The two that are current work fine.  It took about a day and some editing and updating to get the A4 working but it never lost the terminal login at least.

The GDM logs are huge (near 2000 lines to the first one) where they are looking for some way to run.

The ones for the install I am working on are, many times, blank.

---

### Post by ELD on 2009-09-07
I don't mean to be a pain but how do we do "6.Then copy the file that was just generated to /etc/X11/xorg.conf" this is command line stuff which i am still not amazingly comfortable with.

---

### Post by ranch hand on 2009-09-07
As I have several that I am working on I go to another OS (9.04) and use Nautilus as root.  I know, I know.  I am a bad boy.  I can also do 3 or 4 files at once this way.

Yes, I can screw up 3 or 4 OSs at once this way.  It works.

If working on one you should be able to do this from a Live CD and a text editor (nano, vim, screem, gedit) with the above commands.

---

### Post by Galban on 2009-09-07
Same problem here too. So...it's officially a bug....hmmm...well lets see!

I've opened a thread about my troubles with Karmic, but instead I will one eye on this one. Mine is here: [http://ubuntuforums.org/showthread.php?t=1259354]("http://ubuntuforums.org/showthread.php?t=1259354")

---

### Post by ELD on 2009-09-07
Well Kubuntu karmic boots fine for me so it is definitely a gnome issue, time for me to get used to KDE ^_^

---

### Post by SeePU on 2009-09-07
Ubuntu Karmic is a real POS.  It is the only LiveCD distro that freezes on my laptop.  Each and every time.  It boots up but soon later while I'm there, the entire system freezes and I have to re-start the machine.  

Karmic fails, period.  They have a lot of work to do, I guess.

---

### Post by ranch hand on 2009-09-07
I have had no problem up to the A5 CD.  I suspect that the A6 will be fine.

I downloaded the daily build today (A5 will not boot) and while it gets to the login screen, it just loops (this is an improvement).  On the other hand using the "install ubuntu" option gives me an installer where the partition editor does not work.

I will try it again in a couple days.

Meanwhile I have all 4 32bit variations on 9.10 working and 4 out of 5 64bit variations (I am loosing hope for the fith one, several files are just not there).

---

### Post by ELD on 2009-09-07
> **ranch hand said:**
> 
I downloaded the daily build today (A5 will not boot) and while it gets to the login screen, it just loops (this is an improvement).

I will try it again in a couple days.


Exactly what i am getting, i got a little further than the other builds, it seemed to get passed the second loading screen, give me the login tune and then loop back to a frozen second loading screen.

I have bookmarked the bug i am pretty sure it is and one aspect of it is confirmed the other is marked as "incomplete" which is annoying since it is such an obviously big issue.

Is it just 64bit that is buggered, i am tempted to d/l a 32bit edition just so i can play heh.

---

### Post by patasenko on 2009-09-07
32 bit wont help you. Believe me, i tried.
The only work around i got for me was to boot from cd then choose install instead of Live version. After instaliation, while booting ctrl+alt+f1 and get aptitude running, doing updates, so the new fgrlx modules get installed, and install the new fglrx which works fine, but i do know that its not opensource drivers.
Strangely Kubuntu Karmic Koala (KKK :D ) works fine from live.

---

### Post by tsger on 2009-09-07
> **ELD said:**
> I don't mean to be a pain but how do we do "6.Then copy the file that was just generated to /etc/X11/xorg.conf" this is command line stuff which i am still not amazingly comfortable with.

No prob.  Here's how to copy it:

```
sudo cp /root/xorg.conf.new /etc/X11/xorg.conf
```

---

### Post by Sophont on 2009-09-08
Apologies for the off-topic interruption.

> Dell Studio XPS 1640, 2.6 GHz processor, 4 GB RAM

tsger,

I see you have the same laptop as I do - I'm curious if you have 3D going with the recent fglrx update?

4670 or 3670?

TIA

---

### Post by jim-fwb on 2009-09-12
Similar problems

1) Installed "K-K" w/ xubuntu-alternate AMD64.  It failed to boot from the get-go: "out of range" according to grub. I'd left a empty partition for a BSD install & thought that might be the problem, so I deleted it when-reinstalling... Wrong-o.

2) Installed K-K w/ kubuntu desktop and a considerably simpler partition layout: / swap /home.  Installed fine; booted fine.  Then, using apt-get, I did an update & dist-upgrade which included updates to the kernel, grub, and xorg.  At one point apt-get asked if I wanted to install the grub maintainer's config, file, and I took the default (NO).  Then installed synaptic. On reboot I got the now-familiar "out of range" message.  

3) The problem does not seem to be fixable with the CD, as attempting to re-nstall grub fails in a spectacular sea of red and black. I suspect this is some kind of grub problem, and that I should have installed the maintainer's grub config ... but what do I know? duh ... very little.  Off to visit Launchpad.

---

### Post by jim-fwb on 2009-09-12
My problem is ... was bug 424503 at launchpad.  There's a working fix from robin0800:

1) boot alternate cd and select "rescue System"

2) set correct root (in my case it is /dev/sda5)
... follow prompts to Rescue Menu

3) Choose Console Window in my case, it was "execute a shell in /dev/sda5" because this is root already sudo is unneeded

4) code:
   nano /etc/default/grub
then uncomment the line saying: GRUB-TERMINAL=console
save file and quit nano

5) execute "update-grub"
 then "exit" and choose reboot from rescue menu.

Worked for me.  My hat would be off to robin0800, if I wore one.

A great day to all!

---

### Post by ELD on 2009-09-12
I tested 12/09 daily cd and the issue is still there for me, not looking good :(

---

### Post by sgosnell on 2009-09-12
What kernel is Karmic using?  I'm still running Jaunty, but have been installing the new kernels as Linus cranks them out.  I've had no issues until I installed 2.6.31, and I get the same boot failure discussed on this thread.  It starts, gives the splash screen, then hangs completely, requiring holding the power button or removing power.  It's a kernel problem, not a distribution problem, as far as I can tell, because the .30 kernel works perfectly for me.  I'm on an EEE PC 900, Gnome desktop with compiz.

---

### Post by ELD on 2009-09-16
Well it seems that they are FINALLY properly looking into this bug!

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/419126](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/419126)

Has been updated and due by the beta, but it still means a lot of us have to mess with settings (which i won't do) to even get karmic to boot to test. Annoying!

---

### Post by Ansenyi on 2009-09-17
A nice, I was also bumping into this bugger!

---

