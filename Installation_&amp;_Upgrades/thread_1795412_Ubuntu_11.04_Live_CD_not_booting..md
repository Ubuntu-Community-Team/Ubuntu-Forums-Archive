---
title: "Ubuntu 11.04 Live CD not booting."
date: 2011-07-02
forum: Installation &amp; Upgrades
---

### Post by SolidarityK on 2011-07-02
Hi everyone,

I am not too new to the Linux scene, I mainly use CentOS on a day to day basis on my server, however, I would like to start using Ubuntu on a full time basis, I am sick of how slow Win7 can be and all of the bulk. Sooo, I downloading ubuntu, burned it, verified it, y'know, the usual.

Backed up everything I needed and restarted pc. The purple splash screen came up and started to load. After about 3 minutes I see a very distorted version of my Win7 desktop! I am then unable to Ctrl+Alt+F1 as my keyboard becomes unresponsive. I have disabled my graphics card (Nvidia 240 GT (I think)) and just used the on board Intel chipset but still this happens. What is going on? I am desperate to use it and I am finding this really frustrating.

Also I did manage to ctrl alt f1 at one point and I tried to restart gdm but it errored out on me.

Help :(

Regards,
Ben

---

### Post by ~!geek!~ on 2011-07-02
I hope u burned ubuntu on cd (although clear from your statement livecd). 

It happened with me a couple of times when I burned ubuntu iso on usb-disk using some linux distro's startup-disk-creator utility. 

It works all the time when I burn iso to usb using universal-usb-creator mentioned on ubuntu website. So if you burned iso on usb, you can try reburn usb on windows-machine.

---

### Post by MAFoElffen on 2011-07-02
> **SolidarityK said:**
> Hi everyone,

I am not too new to the Linux scene, I mainly use CentOS on a day to day basis on my server, however, I would like to start using Ubuntu on a full time basis, I am sick of how slow Win7 can be and all of the bulk. Sooo, I downloading ubuntu, burned it, verified it, y'know, the usual.

Backed up everything I needed and restarted pc. The purple splash screen came up and started to load. After about 3 minutes I see a very distorted version of my Win7 desktop! I am then unable to Ctrl+Alt+F1 as my keyboard becomes unresponsive. I have disabled my graphics card (Nvidia 240 GT (I think)) and just used the on board Intel chipset but still this happens. What is going on? I am desperate to use it and I am finding this really frustrating.

Also I did manage to ctrl alt f1 at one point and I tried to restart gdm but it errored out on me.

Help :(

Regards,
Ben
Welcome to Ubuntu Forums.

Let me back you up a few and ask a few questions so that we are on the same understanding.

First, from your description, you "are" currently running Win7 on this PC?  ...and want to run Ubuntu?  As dual-boot or using Wubi?

Next . I need a little clarification on your hardware... video onboard as Intel and an NVidia 240 GT... When you have the NVidia card installed does the BIOS turn off the onboard or do you have to manually turn it off?

One thing that wasn't clear was: where these problems occurring while trying to boot on the LiveCD?  Did you check the MD5sum of the iso to confirm that you have a good downloaded image and did you run the "check disk" option of the LiveCD to see that it burnt to disk OK?

With the Nvidia card installed and while trying to boot from the LiveCD... when it gets to the initial purplish screen with the keybaord and person icon at the bottom > press <esc> or <enter> > When the keyboard/language box appears, press <esc> ... The box will disappear and show the main "Try" and "Install" menu screnn > Press <F6> > a drop down menu will come up... arrow down to where it says "nomodeset" and press <enter>.  An X will appear to the left of that option.  > Pree <esc> and that dropdown box will disappear. > Select "Try" by arrowing until it hightlighted and press <Enter>.

It should display okay and boot into the LiveCD.  If you install, after the installation, on reboot, press an arrow key as the Grub menu displays... > arrow to the main Ubuntu boot item. > Press the <e> key to get into an edit mode for that menu item > Go to the linux line (kernel boot line) and append nomodeset to the end of the kernel boot line. > Press <cntrl><x> to boot.

Once it boots, go to System > Administration > Additional Drivers > select the nvidia-current driver ... after if installs. press the Activate button to activate it...

On reboot, If there is any problem with that, you can back out of that by booting in safemode and renaming /etc/X11/xorg.conf to anything besides that filename (such as xorg.conf.old).

If you need more info or have other problems, please read this sticky:
                         **[B]Sticky:**[/B]                                      [COLOR=#008C00]**[all variants]**[/COLOR]                          [Graphics Resolution- Upgrade /Blank Screen after reboot]("http://ubuntuforums.org/showthread.php?t=1743535") 
Then post back here.  I do hope that we can get this resolved quickly.

---

### Post by SolidarityK on 2011-07-02
Thanks for all of your help, I will keep that all in mind, however, I have just removed my nvidia card and voila, it's booted fine!!!! I will be back in case I have problems, and also for your advice, thank you.

Ben

---

