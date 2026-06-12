---
title: "Ubuntu 14.04 on HP Pavilion dv6000 Video issues"
date: 2015-07-19
forum: Installation &amp; Upgrades
---

### Post by Vidorin on 2015-07-19
Hello everyone I have seen other threads with issues regarding Ubuntu on an HP Pavilion DV6000 Laptop involving the Nvidia chipset and card with that computer.  However I am at a total loss I will list here what I have done and perhaps a solution can be found.

First attempt: Straight install of Ubuntu 14.04 x64 edition, I couldn't even get past the installation screen due to the strange video issues where I couldn't see what I was doing.

Second Attempt: Straight install of Ubuntu 14.04 x86 edition, it was the same result.

Third Attempt: Install Ubuntu 12.04 x64 edition, downloaded updates while installing and activated the broadcom and nvidia drivers.  Afterwards I then upgraded to 14.04 via the update manager.  That worked until it got in a perpetual loop of failsafe graphics mode and I couldn't even get into the recovery mode of Ubuntu.

Fourth Attempt: I reinstalled Ubuntu 12.04x64 edition didn't download any updates during the installation and then just went straight to upgrading to 14.04.   Now here we are I can get to the login prompt but after I login it just goes to a black screen with no interface.

I tried this from askubuntu.org: 

[http://askubuntu.com/questions/630432/ubuntu-14-04-lts-black-screen-after-login](http://askubuntu.com/questions/630432/ubuntu-14-04-lts-black-screen-after-login)

DO NOT USE NVIDIA PRIVATIVE DRIVERS, something changed since 14.04 that crash Unity. Even though you can't see the toolbars (the upper one and left one) they are there!. Try clicking where has to be the on/off logo and you'll be able to access the Ubuntu settings! and reboot!

First of all, Check (if you can access settings after normal login) in "screen settings" that perhaps a second screen is activated, even if you don't have a plugged in second monitor. It seems like the video card is working with both. Turn the second off, and you'll get more stability.

I had the same problem with my AMD64 an NvidiaN7000 laptop. Now, is running more stable on Ubuntu 15.04. If the previous advice didn't work, try this: 1- Before log in, pulse Ctrl+alt+F1, so you get the console. 2- Once on command line, log in. Then "sudo su" to obtain root privileges. 3- Then Update to Ubuntu 15.04. Some bugs with Nvidia were solved in this new version.

And then this: 

[http://askubuntu.com/questions/449479/ubuntu-14-04-lts-crashes-after-login](http://askubuntu.com/questions/449479/ubuntu-14-04-lts-crashes-after-login)


sudo apt-get install nvidia-current

It still isn't working correctly and I'm at a loss.  Any assistance here would be greatly appreciated.  Because my head has gone kaboom lol

---

### Post by ubfan1 on 2015-07-19
Some approaches I used on my old HP v3000:
1) Use the "nomodeset" option (or manually add to  the linux line in the grub boot paragraph) if you cannot get a live media to boot.
That might help getting started.
 2) After installing the nvidia-current (which drivers does that get for you?), reboot and check that a) the nvidia-xxx module is in the lsmod output and b)If nvidia-xxx is not in the output, does the driver (nvidia-xxx.ko) even exist under /lib/modules/<kernel name>.  I have seen some additional driver selections result in a partially build set of nvidia modules, with the main module missing.  In this case, use apt-get --reinstall install nvidia-xxx
in a terminal and see if there are any errors (my reinstall just worked, creating the correct driver).
 3)Get rid of unity.  That really solved many video issues for me (in my 2G machine).  Actually, I found Lubuntu worked better on this old machine than Ubuntu.  The Lbuntu 14.04 is a long term support version, so try that.
 In situations, not even the nouveau driver is used, just some VGA default, so combine that with unity, and things behave badly.  Actually, I found the nouveau driver in Lubuntu worked acceptably as far as performance, but it really overheated my 6150 video chip, so I did switch to the Nvidia drivers and got things working.

---

### Post by Bucky Ball on 2015-07-20
Yes, nomodeset is what you need, as suggested.

Boot the machine, highlight the kernel you want to use, type 'e' to edit, find the line that ends in 'quiet splash' and, after a space, add 'nomodeset'. 

> quiet splash nomodeset

Follow the instructions at the bottom of that screen to save changes and resume boot. Any luck?

If that works, let us know and we can make it permanent. Don't go to anymore trouble until you have tried this. The classic fix for Nvidia. We can dig deeper once you're in. Good luck. :)

Stick with 14.04 LTS. Do not keep installing the OS which keeps changing the parameters. Not going to make any difference here, just create confusion for helpers attempting to help. Thanks.

---

### Post by Vidorin on 2015-07-20
I add the edit to the line however there is no option to save the changes so I can't see if it works or not.  It says:
"Minimum Emacs-like screen editing is supported. TAB lists completions.  Press Ctrl-x or F10 to boot, Ctrl-c or F2 for a command-line or ESC to discard edits and return to the GRUB menu."  I do not see an option to save my edits and when I do boot it just does the same thing and when I go back to edit it again as stated the edit is not saved.

---

### Post by Vladlenin5000 on 2015-07-20
After editing, *press _Ctrl-x_ or _F10_ to boot* (with the edited changes, once)...

---

### Post by Vidorin on 2015-07-20
I did the Ctrl-x and F10 command after having the change made to be  quiet splash nomodeset and still a no go.  I tried it twice, first time with Ctrl-x and then I rebooted made the edit again and hit F10.

---

### Post by Bucky Ball on 2015-07-20
> **Vidorin said:**
> I did the Ctrl-x and F10 command after having the change made to be  quiet splash nomodeset and still a no go.  I tried it twice, first time with Ctrl-x and then I rebooted made the edit again and hit F10.

Strange. I owned that exact machine and that's what worked for me. :-k

---

### Post by Vidorin on 2015-07-20
Could it be because I had to do the backpedal install from 12.04 and upgrade to 14.04?

---

### Post by Bucky Ball on 2015-07-20
Doubt that. One thing I did notice from your first post, though. Updating with third-party drivers installed commonly cause crashes. You should disable all third-party repos and drivers prior to upgrading and you should also do an update prior to upgrading. The graphics driver breakage when upgrading from 12.04 LTS to 14.04 LTS is not unexpected.

I suggest you install 14.04 LTS and try to fix that rather than coming from 12.04. That is not going to make a difference (as you've discovered), just take more time.

Install 14.04 directly, do not do updates or install third-party drivers on the way. Before the install, when you boot the Live media, hit any key when you are at the icon on the purple screen. That should take you to the 'Try' 'Install' options, etc. Hit F6 there and choose 'nomodeset' from the options that pop up. Proceed and see how you go.

---

### Post by Vidorin on 2015-07-20
I cannot install it without the graphics being all strange I have no interface unless there is a terminal alternative here to install 14.04 properly without these graphical issues from the actual DVD media.  But when I use the GUI installer which is what would normally boot up with the try and install options well I am lucky I can make out "ubuntu" on the screen.  The media I do have is the 14.04.2 version currently available.

> Fourth Attempt: I reinstalled Ubuntu 12.04x64 edition didn't download any updates during the installation and then just went straight to upgrading to 14.04. Now here we are I can get to the login prompt but after I login it just goes to a black screen with no interface.


Also on this current installation I did no third party downloads or updates of any kind.  I went with 12.04 and did the straight upgrade to 14.04 but as stated it made no difference either way aside from actually letting me get to the login prompt.

I say, this is a mind meld Spock would be proud of!

---

### Post by Bucky Ball on 2015-07-20
And as I say, install 14.04 directly but when you first boot from the live media to install, set the 'nomodeset' option at the very first screen with F6> nomodeset before installing, trying or doing anything else.

---

### Post by Vladlenin5000 on 2015-07-20
Using a DVD it's quite easy to add the required *nomodeset* parameter: At the Try Ubuntu / Install /... menu press F6 and choose that option.
You'll be able to install the OS and then the proper drivers, without glitches, albeit with a lower than optimal resolution. After installing the correct graphics drivers you should be able to set the optimal resolution.

---

### Post by Vidorin on 2015-07-20
I did the nomodeset parameter by hitting f6 and all that, however the graphical interface is still all screwy just like before.  Perhaps if I explain it in greater detail that'll help.  When it loads to install ubuntu where you would normally see the ubuntu words in white in the center of the screen with the progress dots below it when loading the installer from the media, the graphic looks screwy where it goes in the lower right hand corner of the screen and I just see a vertically stretched ubuntu in white about 1 inch high and then after that is over, it goes to the silver background with a white mouse pointer.  After that it goes to the white wheel with the progress circle within it then it goes black for a split second and everything is all stretched vertically and  I then see a zoomed in version of the language selection and I have no control over the interface.  It looks like every other line is a horizontal pixelated black line interlaced with the other colors.  It sounds like a hardware issue I know, however with Windows it works perfectly hence why I'm here scratching my head.

---

### Post by Bucky Ball on 2015-07-20
When are you applying nomodeset with the F6 options?

---

### Post by Vidorin on 2015-07-21
The computer boots up, as it boots from the dvd I hit F6 and then that Ubuntu screen comes up with the options.  I hit F6 and turn off nomodeset as instructed.  I continue on to install ubuntu and the graphics get all screwy.

---

### Post by Bucky Ball on 2015-07-21
Turn off nomodeset??? We want you to choose that option, not turn it off ... :-k

---

### Post by Vidorin on 2015-07-22
Select the option yeah thats what I meant. Sorry was tired. I select the nomodeset option. It has a couple of others such as acpi=off and all that. However I DO NOT change any other optons aside from selecting nomodeset. Then I try to install ubuntu and screwy graphics. :-/

---

### Post by Vidorin on 2015-07-23
What if I tried to install lbuntu as suggested in the first reply from ubfan1, would that work?  Unless there is something else I am missing here. Thank you all in advance.

---

### Post by mörgæs on 2015-07-24
Yes, his suggestion about Lubuntu is a good one. As with Ubuntu your options are the closed-source drivers which can be setup automatically during install or the nomodeset boot option.

Here is some advice regarding [power management]("https://help.ubuntu.com/community/RadeonDriver#Kernel_3.11.x_.28Ubuntu_13.10.2FSaucy.29_and_Later").

---

### Post by Vidorin on 2015-07-24
All right well I installed the lubuntu 14.04 and it works perfectly. However, is there a way to make the video better? The generic driver does work however it doesn't look like a sharp or good image. Is there a possibility I can enable or download any other driver? I enabled the broadcom wireless ones and they work perfectly. However Inleft the video driver as the generic default one nevau or whatever its called.

---

### Post by mörgæs on 2015-07-24
Under Software Updater (or something like that) do you get an option to install closed-source drivers?
This part of the application might be slow so patience is a virtue.

---

### Post by ubfan1 on 2015-07-24
These days, look under the Additional Drivers tab in Software and Updates program.

---

### Post by Vidorin on 2015-07-24
Yes under the additional drivers thing i can grab nvidia drivers it has 3 different versions. The same place i activated the broadcom ones.

---

### Post by Bucky Ball on 2015-07-24
Is there one that is 'Recommended' next to it? Try that. Else open a terminal and:

```
sudo lshw -C video
```

Make a note of your video card, do a bit of research to see which one you should be selecting from 'Additional Drivers' and fire away.

---

### Post by Vidorin on 2015-07-24
All right I ran the sudo lshw -c video command as instructed and it corresponded with the video card installed and as described in the Additional drivers.  Now it does not have a recommended driver however I will type out what it says.

NVIDIA Corporation: C67 [GeForce 7150M/nForce 630M]

This device is using an alternative driver.

Using NVIDIA legacy binary driver-version 304.125 from nvidia-304(proprietary, tested)

Using NVIDIA legacy binary driver-version 304.125 from nvidia-304-updates(proprietary)


Using NVIDIA legacy binary driver-version 173.14.39 from nvidia-173 (proprietary)

Using X.Org X server -Nouveau display driver from xserver-xorg-video-nouveau (open source)  <----Currently in use.

So if I am to use an Nvidia driver, which should I use?

---

### Post by Vladlenin5000 on 2015-07-24
"tested" is how it used to be, before they started using "recommended", but either 304 or 304-updates should work.

---

### Post by Vidorin on 2015-07-25
All right I used the tested driver and well now everything works perfectly so I'll mark this thread as solved.  Thank you all so much for your assistance.

---

### Post by Vladlenin5000 on 2015-07-25
Enjoy :p

Take good care of the notebook and it should have a few years more of usable life.

---

