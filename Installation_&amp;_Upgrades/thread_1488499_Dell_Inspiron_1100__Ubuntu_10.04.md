---
title: "Dell Inspiron 1100 / Ubuntu 10.04"
date: 2010-05-20
forum: Installation &amp; Upgrades
---

### Post by Rob Glenn on 2010-05-20
Has anyone got Ubuntu 10.04 working on their Dell Inspiron 1100?  Most of the time, the screen goes black a short time after boot.  Sometimes it goes black right after the splash screen, sometimes I get to log in and then it goes black a little later.  Same results when trying to boot into "safe graphics" mode.  Ubuntu 7.10 works fine on this machine (although I had to do some special configuration in xorg.conf to get it to work way back when I installed it.)  However, it does not appear to be possible to manually configure X in 10.04.  I tried disabling the splash screen in grub based on suggestions I found for other Ubuntu versions, but that had no effect on the problem.

Is it possible to replace X with the most recent version that could still be manually configured?  Would anyone know how to go about doing that?

Alternatively, if it's impossible to get this old machine to run new versions of Ubuntu, has anyone had success with (relatively) new versions of other distros on it?

Thanks!
Rob

---

### Post by MikeG0 on 2010-05-27
I have the exact same problem.  I'm running 10.04 on the dell inspiron 1100.  Very frustrating!!

Searching launchpad for i845g bugs shows a lot of similar issues.

It's been around for a while ... see #316081

I've subscribed to launchpad's bug #578167.  My latest clue is the  results of xrandr:
VGA disconnected (normal left inverted right x axis y axis)
LVDS unknown connection 1024x768+0+0 (normal left inverted right x axis y  axis) 0mm x 0mm

So it must be that the driver isn't recognizing the LCD??  Or it's thinking the VGA is plugged in.  

I'm sorta an Ubuntu newbie.  I'm running a dual boot and will have to live with winxp until this gets resolved.  :(  But I did play around with the xorg.conf file.  There is a way to write out that file to your ~/ dir, then change it around.  I tried some changes, but didn't notice any difference.  Maybe X wasn't even looking at it.  I might try setting it to use the vesa driver ... read somewhere that might work ... and I'll try to remove the VGA display from xorg.conf.

Other things I've tried: added nomodeset/removed splash in grub, uninstalled compwiz, dist-upgrade up to today, and some other weird settings that I can't recall at the moment.  Still crashing in a weird loop pattern ...

  1) Blank screen
  2) VT with last 2 syslog entries
  3) Black screen with a panel of vertical black and white lines top  center
  4) Loop

Hopefully we can get this fixed soon,

Mike

---

### Post by at0msk on 2010-06-07
> **darkod said:**
> You will need to add it in /etc/default/grub. Open  it with:

gksudo gedit /etc/default/grub

Find the line

GRUB_CMDLINE_LINUX=""

and change it to

GRUB_CMDLINE_LINUX="nomodeset"

In that line you can add any parameter you want to set manually. Save  and close the file. To update grub.cfg run:

sudo update-grub

Restart and ubuntu should boot without your intervention.

Hold shift at boot, select ubuntu (not recovery) then hit E. Go to the line that starts with Linux and hit End on your keyboard. Remove splash and type no mode set then hit ctrl+x. After you're in follow what's in the quote.

BTW, i know nothing about ubuntu and just went through the above on my inspiron 1100 so sorry if you've done this already.

---

### Post by MikeG0 on 2010-06-07
Found a way to get fairly stable.  Less than one crash per 10 hours of run time.  It only got stable after I stopped using Firefox and switched over to Chrome.  I also had to remove Shockwave Flash.

This is in my /etc/default/grub file ...
GRUB_CMDLINE_LINUX="video=LVDS-1:e video=VGA-1:d i915.modeset=0"

I find that moving my mouse (attached via usb)  right after the grub boot screen helps.  If X doesn't go to tty7 and load the deskstop (in other words, blank screen), hitting Alt+Ctrl+F1 (or any tty function key through Alt+Ctrl+F6 [tty1 to tty6]) and logging in and restarting X wont work.  X will eventually crash.  If X doesn't load the screen to tty7 correctly, it's best to login and "sudo reboot" and try again.  Once it does load to tty7, X will be fairly stable (minux compiz, flash, and firefox).  Hope this helps.

Cheers,

Mike

---

### Post by sh0nuff613 on 2010-06-15
This may be my first post, but I'm attempting to install a light, fast OS on a clients old and clunky Inspiron 1100.

Seems like lots of people are having issues with the display drivers not running above 640x480, or a black screen.. I found a relatively new article from last year detailing how to install ulite onto an 1100

Article is here

[http://u-lite.org/content/successfully-installed-dell-inspiron-1100-required-some-tweaking](http://u-lite.org/content/successfully-installed-dell-inspiron-1100-required-some-tweaking)

Might be of some use, I'm still trying to figure out what other options I have for putting something OTHER than xp on this slow laptop.

---

### Post by curious-linux-skeptic on 2010-06-23
Hi Guys.

This is my first post to the ubuntu forums. What you're discussing here is the problem that I'm having but mine goes back a little further.  The first distro that I put on my Inspiron 1100 was Hardy Heron.  It booted fine, but I couldn't hibernate or suspend without my screen going completely blank forcing me to do a hard shut down by holding my power button. It was very difficult to get anywhere until I was finally able to get connected to the net by downloading NDISWrapper onto a different computer and transfering it over to mine.

I went through a LOT of upgrading through the synaptic package manager eventually getting all the way up to Karmic.  All of this time I never was able to suspend or hibernate, and so Linux remained mostly unusable for me b/c I need to change locations alot on my laptop. 

I finally decided to try upgrading to Lucid via synaptic and at first it loaded sporadically (though I still couldn't suspend) but lately, I haven't even been able to get it to boot.

Let's assume that I'm the greenest noob that you've ever seen on here (which I pretty much am) and don't understand most of what has been said in the above posts (about X etc.)

Can you guys give me some recommendations about what I could try? The recommendations would basically need to assume my idiocy and involve step by step instructions on what to click and what to type. For my learning, you could also include a little bit of dumbed down rationale behind what you're recommending that i try...or would I be better just to run my Hardy installation CD again and start over?  If I did, I still wouldn't be able to suspend, but at least I could boot so I could work on the issue...

I really appreciate you guys and am excited about linux as a possible XP replacement.  Thanks for your help guys.

-Kevin

---

### Post by MikeG0 on 2010-06-23
The issue is with the intel driver and 3d rendering.  I got my Inspiron 1100 fairly stable on 10.04 by removing compiz and adobe flash and changing a setting in grub.

Try these first steps ...
sudo apt-get update
sudo apt-get remove compiz

Remove flash by renaming the libraries
/opt/Adobe/Reader9/Reader/intellinux/lib/libflashsupport.so -> /opt/Adobe/Reader9/Reader/intellinux/lib/libflashsupport.so.bak
/opt/google/chrome/libgcflashplayer.so ->/opt/google/chrome/libgcflashplayer.so.bak
/usr/share/app-install/desktop/flash10.desktop -> /usr/share/app-install/desktop/flash10.desktop.bak
/usr/share/app-install/desktop/flashplugin-installer.desktop -> /usr/share/app-install/desktop/flashplugin-installer.desktop.bak

Use this command to search for any other instances of possible flash libraries and rename them too ...
sudo find / -name *flash*

Change the GRUB_CMDLINE_LINUX constant in /etc/default/grub (around line 15) to ...
GRUB_CMDLINE_LINUX="video=LVDS-1:e video=VGA-1:d i915.modeset=0"

Then run ...
sudo update-grub

I also try to avoid any application that'l try 3d rendering ... screen savers, games, etc.

Here's the master bug report for this issue.  You should subscribe to it and watch for a fix ...
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/541492](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/541492)

Cheers,
Mike

---

### Post by greenstar on 2010-07-15
I know this is kind of an old thread. Sorry I'm late to the party.

I'm setting up Ubuntu Lucid for a friend on an Inspiron 1100 and have encountered the same problem. What I've found is that this is much simpler than you'd think, as it's not (in my case at least) a software issue. Here's what I did:

1. Boot the laptop and at the POST/ Dell Globe screen press F2 to access your BIOS (aka Setup). On the first page, look about halfway down for a line called "Video Display Device"

2. Note that when you arrow down and highlight that line, it details the 3 options on the right of your screen. Those 3 options are:
   - CRT Mode (external monitor via the D-Sub port on the left side of the laptop)*****
   - LCD Mode (internal monitor *only*)
   - Simul Mode (both CRT & LCD - if both are attached, otherwise defaults to LCD)
***Note** that in CRT mode, the LCD is used by default and works unless an external monitor is connected.

3. I've had the troubles described in the above posts with the Simul Mode enabled. Simul Mode may be the default as that is the one that was selected when I first went into the BIOS looking for video settings. **Note:** My clue to look here was that video was fine in text mode and during boot all the way up to the point where x is loaded for the graphical login screen.

4. What I did was experiment with the different modes. 
 
   - Simul mode, where both LCD and CRT monitors are enabled simultaneously was giving me the problems described in the above posts.
   - LCD mode works fine, but excludes the possibility of plugging in an external monitor.
   - CRT mode works fine and allows for the use of an external monitor if needed, with the caveat being that only the external monitor will function when one is attached.

5. Seems that this laptop prefers to use only one monitor at a time. A BIOS update may correct this, I haven't tried that yet. You'll need a windows installation to update the BIOS from as it's a Windows executable (.exe file). If you want to try that, go to [http://support.dell.com/support/index.aspx?c=us&l=en&s=dhs](http://support.dell.com/support/index.aspx?c=us&l=en&s=dhs) and click Drivers & Downloads. If you need a different language (link is to English page), button is at top left of page. Then choose "Enter Service Tag" (best, most precise option) or "Choose a Model" to browse through the laptop models (sometimes difficult to find your exact model this way).

Hope this helps,
Greenstar

---

### Post by MikeG0 on 2010-07-17
Yep, that's the primary problem ... the CRT/LCD switch in the BIOS (and the Fn+CRT/LCD key comb doesn't work either).  Problem is, in the latest BIOS (ver 32??), they've removed those options!!??  :(  

My work around is to move the touch pad mouse around the moment boot goes from text terminal to video.  It seems to think that if I'm using the touch pad, I must be using the LCD.

---

### Post by greenstar on 2010-07-20
> **MikeG0 said:**
> Yep, that's the primary problem ... the CRT/LCD switch in the BIOS (and the Fn+CRT/LCD key comb doesn't work either).  Problem is, in the latest BIOS (ver 32??), they've removed those options!!??  :(  

That figures.

> **MikeG0 said:**
>  It seems to think that if I'm using the touch pad, I must be using the LCD.

That's funny. Of course, because we all know that *anyone* who uses a USB mouse *must* also use an external monitor, right? ;)

---

### Post by Skip Da Shu on 2010-08-30
> **Rob Glenn said:**
> ...  Ubuntu 7.10 works fine... 

FYI, I didn't have the problem with v9.10 either.  The 'nomodeset' in grub didn't buy me anything in v10.04.

---

### Post by dwpbike on 2010-09-03
i like the sound of this.  would add only a minor item:  upgrade to bios can be done without resorting to windoze.  i upgraded memory, which first required a32 bios.

---

### Post by empusa on 2010-09-07
I bought an old Dell Inspiron 1100 off my sister a couple of days ago. I tried to install Ubuntu 10.04 and Linux Mint 9. Both gave the results that others here have been experiencing here. I tired all of the suggestions above but it still crashed after an hour or so and often still booted up to a blank screen.

I also tried several other distros including OpenSuse, Mandriva, Fedora, Debian 5 and PCLinuxOS. All of which had different problems mostly to so with the screen. OpenSuse Gnome edition was fairly stable but very slow and Skype refused to install. Debian 5 (Lenny) and Fedora were stable but the wireless network kept dropping out.

I've finally found a Linux distro that does work!!! **Linux Mint 9 LXDE** (Mint Debian). It works without any fiddling about at all... But don't attempt to use OpenBox. Just use the default Gnome desktop.

Mint LXDE is a brand new distro and was only released a few days ago. It's a little rough around the edges, but it's petty solid on the 1100 and well worth a try :D

---

### Post by greenstar on 2010-09-08
> **empusa said:**
> I bought an old Dell Inspiron 1100 off my sister a couple of days ago. I tried to install Ubuntu 10.04 and Linux Mint 9. Both gave the results that others here have been experiencing here. I tired all of the suggestions above but it still crashed after an hour or so and often still booted up to a blank screen.

I also tried several other distros including OpenSuse, Mandriva, Fedora, Debian 5 and PCLinuxOS. All of which had different problems mostly to so with the screen. OpenSuse Gnome edition was fairly stable but very slow and Skype refused to install. Debian 5 (Lenny) and Fedora were stable but the wireless network kept dropping out.

I've finally found a Linux distro that does work!!! **Linux Mint 9 LXDE** (Mint Debian). It works without any fiddling about at all... But don't attempt to use OpenBox. Just use the default Gnome desktop.

Mint LXDE is a brand new distro and was only released a few days ago. It's a little rough around the edges, but it's petty solid on the 1100 and well worth a try :D

Thanks for sharing your results with the community. That's what makes Linux so great!

---

### Post by spcwingo on 2010-09-08
I'm using the kernel parameter:

```
i915.modeset=1
```

---

### Post by MikeG0 on 2010-09-09
> **spcwingo said:**
> I'm using the kernel parameter:

```
i915.modeset=1
```

This is set in grub, yes?
modeset means set the video output mode to CRT or LCD?

Thanks!

---

### Post by spcwingo on 2010-09-09
> **MikeG0 said:**
> This is set in grub, yes?

Yes

> **MikeG0 said:**
> modeset means set the video output mode to CRT or LCD?

I not quite sure, but I would think it would be something to that effect.

> **MikeG0 said:**
> Thanks!

No problem.

---

### Post by dwpbike on 2010-09-23
> **empusa said:**
> I bought an old Dell Inspiron 1100 off my sister a couple of days ago. I tried to install Ubuntu 10.04 and Linux Mint 9. Both gave the results that others here have been experiencing here. I tired all of the suggestions above but it still crashed after an hour or so and often still booted up to a blank screen.

I also tried several other distros including OpenSuse, Mandriva, Fedora, Debian 5 and PCLinuxOS. All of which had different problems mostly to so with the screen. OpenSuse Gnome edition was fairly stable but very slow and Skype refused to install. Debian 5 (Lenny) and Fedora were stable but the wireless network kept dropping out.

I've finally found a Linux distro that does work!!! **Linux Mint 9 LXDE** (Mint Debian). It works without any fiddling about at all... But don't attempt to use OpenBox. Just use the default Gnome desktop.

Mint LXDE is a brand new distro and was only released a few days ago. It's a little rough around the edges, but it's petty solid on the 1100 and well worth a try :D


i am repeatedly trying to recreate the scenario to no avail.  i get a blank screen unless i boot from the cd in "compatibility mode" (whatever that means).  mint does boot up with a small screen (640x480) in compiz, which i see no way to change.  i can "add" 1024x768, but how to implement change without total commit to mint 9?

---

### Post by LughClyde on 2010-10-05
I just installed the current version of Peppermint Ice on an Inspiron 1100 with BIOS A32. It's working just fine. I did not try the regular Peppermint OS. Peppermint Linux is a Lubuntu derivative for cloud computing. The Ice variation does cloud apps as SSB.

BTW, Kendall Weaver also worked on Linux Mint LXDE. That may explain why both run on the 1100.

Ice is very fast and stable on this old laptop. It actually boots faster from that slow HDD than Puppy booting from a USB drive. Puppy will open apps faster from its RAM based location, but this situation is only running Chromium and Ice runs that as fast as Puppy. BTW, Ice takes up less RAM than Puppy too.

Thanks,
Clyde

---

### Post by mnorth on 2010-10-08
Linux Mint LXDE booted first time for me, saw the ethernet adapter etc...no problems thus far, will try the Peppermint Ice over the weekend, have BIOS A06...was going to reinstall windows(which I made a vhd of and am now running on an older Mac via VirtualBox) and do the BIOS upgrade but saw this post after much agony installing recent versions of Ubuntu/Kubuntu/Debian/Fedora/Suse etc.. all to no avail...now I just have to get my D-Link dwa-125 wireless usb device working (via very helpful posts elsewhere in the forums)

---

### Post by mnorth on 2010-10-25
Just installed Peppermint Ice over the past weekend...everything works fine, also as a bonus it recognized by d-link dwa-125 usb wireless card, which I'd been having a hard time getting to work on the LXDE version, or any other distro...so am much more happy now  that I've got wireless working

---

### Post by mnorth on 2010-10-30
ended up having problems with peppermint ice after adding power mgmt package, the x server started crashing, and even when switching to a virtual terminal would keeping switching screens back to the crashed x screen making it impossible to log back in...after powering down, holding the power switch, thought I'd give installing ubuntu 10.10 another try...so my 1100 has bios a06, 1gb ram 40gb hard disk...in setup i chose lcd screen for video output, boot from cd, i had my dlink dwa-125 usb wireless adapter connected...boot from cd get the try or install screen, chose try...from the 'try' environment setup the dwa-125, surprisingly it worked...after running firefox etc and just seeing if the machine would stay up i clicked on the install icon and the installation went smoothly, downloaded updates etc and finished up fine...after rebooting the screen was dark for a fairly long time, i thought oh well again no luck, when the splash screen showed up i was quite surprised, booted into gnome, update manager appeared, clicked the wireless icon in the top panel to connect to my home router, updates went fine and it's beeen running fine now for 2 days...a little slow at times and the fan is loud as hell but seems to be working fine for cruising the net, email etc...wouldn't really want to use it for serious work but if you can get past the fan noise not bad for a heavy netbook type machine....

---

### Post by MikeG0 on 2010-11-15
> **mnorth said:**
> ended up having problems with peppermint ice after adding power mgmt package, the x server started crashing, and even when switching to a virtual terminal would keeping switching screens back to the crashed x screen making it impossible to log back in...after powering down, holding the power switch, thought I'd give installing ubuntu 10.10 another try...so my 1100 has bios a06, 1gb ram 40gb hard disk...in setup i chose lcd screen for video output, boot from cd, i had my dlink dwa-125 usb wireless adapter connected...boot from cd get the try or install screen, chose try...from the 'try' environment setup the dwa-125, surprisingly it worked...after running firefox etc and just seeing if the machine would stay up i clicked on the install icon and the installation went smoothly, downloaded updates etc and finished up fine...after rebooting the screen was dark for a fairly long time, i thought oh well again no luck, when the splash screen showed up i was quite surprised, booted into gnome, update manager appeared, clicked the wireless icon in the top panel to connect to my home router, updates went fine and it's beeen running fine now for 2 days...a little slow at times and the fan is loud as hell but seems to be working fine for cruising the net, email etc...wouldn't really want to use it for serious work but if you can get past the fan noise not bad for a heavy netbook type machine....

Sounds promising.  Is it still up and running?  Did you ever get the zebra stripe lockup on 10.10?

---

### Post by MikeG0 on 2011-01-07
Looks like they fixed the video driver problem in 10.10!  I've been running Maverick for about two weeks with no zebra crash ever.  Finally!  I can now use Ubuntu w/out hassles.

Now I have another problem.  After hibernating or suspending the screen is blank.  I'm guessing it has to do with the LCD/CRT switch.  Fn key + LCD/CRT doesn't work for me.  The key mapping for the 1100 mustn't be mapped correctly.  I've played a bit with xmodmap, but to no avail.

Any ideas?

---

