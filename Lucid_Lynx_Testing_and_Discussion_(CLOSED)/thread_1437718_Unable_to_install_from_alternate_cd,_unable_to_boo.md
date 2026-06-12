---
title: "Unable to install from alternate cd, unable to boot to desktop cd."
date: 2010-03-24
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Omoronovo on 2010-03-24
After burning the Desktop beta cd of 10.04 and booting it, everything seems to go well - until, I get past the Ubuntu 10.04 logo with the 4 dots to indicate progress. After that, my display turns off, but is still showing as enabled (the light on the front doesn't flash as if the display was not connected; rather, it stays solid but does not have any display).

I believe the system still boots properly however; after the graphical issue starts occurring, I can hear my soundcard activating (It has an onboard preamp which "clicks" when the card is activated). Additionally, after a few moments, by pressing Enter, the CD spins up again as if I had progressed in the installer (I know this, as I tested the iso in a VM first to make sure it worked properly).

This happens with the Desktop AND Alternate ISO's; the Alternate works perfectly in text-based install mode, but will not boot graphically after the install completes.

For reference, my system specs are:

ATI Radeon 5870 1GB graphics card.
Intel Core 2 Duo E8500
8GB DDR2 ram
Intel P45-based motherboard.

If any additional information is required, or if you have any advice, please post to let me know.

Thanks.

As an afterthought: I have not tried the Alpha releases to see if those work properly, or if the problems have been occurring during the entire 10.04 development process.

UPDATE:

Ubuntu 9.10 works perfectly on my system, with all drivers functioning out of the box, excluding my wireless which I expected. Upgrading from 9.10 to 10.04 results in the same problems. The desktop is definitely there - I hear the ubuntu login sound after the screen goes blank - however, nothing works to bring it back.

- Things I have tried so far:

. Clean install from the beta 1 cd image (alternate) as well as booting from beta 1 desktop cd. Alternate text-mode works fine, but fails to load with the same problem after the splash.
. Upgrading from 9.10, which causes the same problems.
. nomodeset, modeset.radeon=0, noacpi, vga=xyz grub modifications. They had no effect on the outcome.
. Alpha releases also do not work. I have tried Alpha 1 and alpha 2 releases, and both demonstrate the same issues. Whatever has changed, will have changed between the 9.10 stable branch and the lucid 10.04 alphas.
. Attempting to drop to a tty does not function either. At the very least, it's influenced by the same non-display issues.

I'm beginning to hope that I am not the only one experiencing this problem, as if it is (or if its very rare/specific), it could be difficult for a solution to be found. That would be a horrible outcome, as lucid is the first version of any desktop Linux distro that I have been excited about in a long time.

---

### Post by Omoronovo on 2010-03-24
I am going to attempt to install an older prerelease and upgrade to the beta.

Failing that, I'll try doing the same with 9.10 - however, I've had a whole host of problems with every Ubuntu release since 8.10, so I guess I should ask if it's even possible to upgrade from that far back?

---

### Post by VMC on 2010-03-24
Try adding "nomodeset" and the end of the linux boot line from grub menu.

Very likely a driver issue.

---

### Post by Omoronovo on 2010-03-24
> **VMC said:**
> Try adding "nomodeset" and the end of the linux boot line from grub menu.

Very likely a driver issue.

I expected it to be a driver issue, but getting around it is where I was lost. nomodeset option does nothing. I removed the quiet line to see if I could see any specific issues that could be causing it, but the output only lasts approximately 3 and a half seconds before the screen dies and the audio card is activated.

On a sidenote: Assuming this graphical bug can be worked around, this build boots EXTREMELY fast on my system. From grub to login screen in approximately 6-8 seconds I'd wager, since the audio card is activated about 4 seconds in. Excellent work.



And now: to try to get it working. Do you have any other possible fixes? Are there any other Ubuntu users running a radeon 5800-series graphics card experiencing the same/similar problems, and found a workaround or solution?

---

### Post by amsterdamharu on 2010-03-24
Kernel parameter xforcevesa and noacpi might do the trick. 
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Then get the driver:
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1433477](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1433477)

Hope that helps, I love lucid.

---

### Post by Omoronovo on 2010-03-24
> **amsterdamharu said:**
> Kernel parameter xforcevesa and noacpi might do the trick. 
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Then get the driver:
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1433477](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1433477)

Hope that helps, I love lucid.

Thanks for your input - I tried both of those, and thanks to the link you sent, I also tried forcing some vesa modes as well - nothing worked.

However, there is one thing I just realised that may be important: My display is driven from the HDMI port of the card, not the DVI port. Whether or not this is of any importance, I don't know, but I thought I'd add that now.

I really want to get this to work - the staggeringly fast boot (that I can see) is just astounding. With any luck, a newer build will sort this by default, but for now I'm still open for suggestions.

---

### Post by amsterdamharu on 2010-03-24
The driver thread is only 5 days old and is for Karmic, pretty close to Lucid.

You could send the op a message on how he/she got the option for the restricted driver in the first place since you do not even get to a gui or command prompt. I assume control + alt + F1 through F7 all give black screen.

I am sorry, other than the xforcevesa and noacpi I have no experience with this.

---

### Post by Omoronovo on 2010-03-24
Thanks, I have done so.

If anyone else is around and having a look at this, has anyone else ever experienced issues with displays connected via HDMI (Not a DVI > hdmi adapter mind; an actual hdmi port on your card/motherboard)?

I'm starting to think that might be the problem, which is a shame if a simple thing like HDMI is not supported properly yet.

---

### Post by Longinus00 on 2010-03-24
Does any version of ubuntu work for you? (specifically older versions) Your videocard is relatively new and I'm not sure how well supported it is, AMD only pushed out open source driver code for it in the beginning of februrary, so it wouldn't surprise me if some things weren't working right.

---

### Post by Omoronovo on 2010-03-24
> **Longinus00 said:**
> Does any version of ubuntu work for you? (specifically older versions) Your videocard is relatively new and I'm not sure how well supported it is, AMD only pushed out open source driver code for it in the beginning of februrary, so it wouldn't surprise me if some things weren't working right.

The last version of Ubuntu that would even install properly on my system was 8.10; however, that was before I purchased my 5870. 9.04 and 9.10 have been nothing but headaches; 9.10 forced me to factory reset my SSD as it did something nasty to it, making it unreadable in any operating system, unable to be reformatted, and showed up in the bios as a garbled line of text instead of the SSD identification string. Luckily, it's not too difficult to flash a firmware update (it was long overdue anyway), but still.

I haven't really been all that impressed with linux in general; debian works great on my home server, but I have never been able to happily run linux on any of my desktop systems, not without issues at least.


Regardless, I digress. Do you believe that this is something that may be improved upon with the beta 2 release due next week?

---

### Post by oldfred on 2010-03-24
I am getting the same issue (monitor turns off) with nvidia 9600GT and DVI connection. After monitor is off can only recover with hard reboot.
LiveCD works with beta and and monday's daily build. 

I could not get either boot nor recovery to work until I blacklisted nouveau. Then I was only able to get recovery to work. I ran all the updates and did get to a terminal login. Since I blacklisted nouveau do I even have any video mode? startx turns monitor off. No change, still boots but turns monitor off. Tried noapci, apci=ht, nomodeset but no luck. From command line tried downloading nvidia-current, only get errors.

Any other suggestions.

---

### Post by oldfred on 2010-03-25
ok, I got past the turnoff of the monitor.

Blacklist nouveau
nomodeset on recovery line
continue boot after all updates
this worked this time:
sudo apt-get install nvidia-current
startx got me to low quality video

ran from terminal to get default xorg.conf
sudo nvidia-xconfig

---

### Post by Omoronovo on 2010-03-25
> **oldfred said:**
> I am getting the same issue (monitor turns off) with nvidia 9600GT and DVI connection. After monitor is off can only recover with hard reboot.
LiveCD works with beta and and monday's daily build. 

I could not get either boot nor recovery to work until I blacklisted nouveau. Then I was only able to get recovery to work. I ran all the updates and did get to a terminal login. Since I blacklisted nouveau do I even have any video mode? startx turns monitor off. No change, still boots but turns monitor off. Tried noapci, apci=ht, nomodeset but no luck. From command line tried downloading nvidia-current, only get errors.

Any other suggestions.

> **oldfred said:**
> Re: Unable to install from alternate cd, unable to boot to desktop cd.
ok, I got past the turnoff of the monitor.

Blacklist nouveau
nomodeset on recovery line
continue boot after all updates
this worked this time:
sudo apt-get install nvidia-current
startx got me to low quality video

ran from terminal to get default xorg.conf
sudo nvidia-xconfig

Thanks for your input, but that is not related to my problem - I never get to see the desktop from a clean installation. After install from text mode installer (graphical installer has no display output), the system splash appears, and after that, all display disappears. I cannot access the additional TTY's, nor do I see or get the option to drop to a command line mode.
The desktop CD has the same problem; after getting past the splash, it loses display and I cannot do anything.
Additionally, since my problem involves a radeon 5870, the options you suggested wouldn't apply here.

Anyone else got any ideas? At this point, all I'm left to try is to download an older build (or an older release), and try to upgrade.

---

### Post by Omoronovo on 2010-03-28
I updated the first post with what I have tried so far. Any further suggestions would be much obliged, as nothing so far has worked.

---

### Post by Omoronovo on 2010-03-29
Bumping for anyone to have any other suggestions. I had a look on launchpad, but I cannot see any bug reports even remotely resembling this one - and I wouldn't know where to begin with creating one.

---

### Post by shindou01 on 2010-03-29
I'm on ati radeon hd3200 maybe a mix of this
assuming you have a working internet connection, 
try to do this "blindfolded"

alt+f2 after hearing the sound which means that you should be on the login screen
then :

sudo apt-get install fglrx fglrx-dev fglrx-amdcccle  fglrx-modaliases            
dpkg -l | grep fglrx 
sudo aticonfig --initial -f

and reboot...

(I'm a noob but I want to try to help and this is just my conclusion after reading the posts on this thread and on some other threads so don't expect too much out of it but what have you got to lose right?) give some time after each command to make sure they're working....

---

### Post by shindou01 on 2010-03-29
I just recalled something else, I read somewhere in this forum that after they installed proprietary drivers on Karmic and upgraded to lucid the drivers remained so I think you could try to re install karmic, install propietary drivers using these commands :

sudo apt-get install fglrx fglrx-dev fglrx-amdcccle  fglrx-modaliases             
dpkg -l | grep fglrx 
sudo aticonfig --initial -f

then upgrading to lucid and see if that works.

---

### Post by Omoronovo on 2010-03-30
Thanks for all your input - after discovering the issue was related to HDMI, I submitted a bug report on launchpad and I decided just to buy a DVI cable for my monitor instead of the HDMI one I was using at the moment. I believe it should work, as my old monitor displayed fine yesterday via DVI.

I'll let you know how it goes.

---

### Post by dannyboy79 on 2010-04-08
> **Omoronovo said:**
> Thanks for all your input - after discovering the issue was related to HDMI, I submitted a bug report on launchpad and I decided just to buy a DVI cable for my monitor instead of the HDMI one I was using at the moment. I believe it should work, as my old monitor displayed fine yesterday via DVI.

I'll let you know how it goes.
you removed quite from teh boot line but did you remove splash also? you should be getting a tty1 at a min. after it boots up and you hear its done you could hit ctrl-alt-f1, then type in username, hit enter, type in password, hit enter. you're now at the cli and you could try to issue a startx command after installing ati drivers. good luck. or you could even try to ssh after installing ssh blindly. good luck

---

### Post by bsmith1051 on 2010-04-08
> **Omoronovo said:**
> after discovering the issue was related to HDMI, I submitted a bug report on launchpad and I decided just to buy a DVI cable for my monitor instead of the HDMI one I was using at the moment. I believe it should work, as my old monitor displayed fine yesterday via DVI.
Thanks for reporting back!  So it's something to do with HDMI support.  Do you know which ATI driver was being used, the included (open-source) or the ATI proprietary?

Also, did you try this with a fresh install of the latest Beta?  This would clarify which video driver was being used, i.e., it would definitely be the included one.

Also, also, now that you're up-and-running, have you tried installing the latest ATI proprietary and _then_ switching to the HDMI cable again?  (You'd probably be best served shutting-down, switching the cable, then restarting)  I'd be curious to know if it works properly with the ATI proprietary but just has an issue 'getting to that point' during the upgrade/install.

---

### Post by Omoronovo on 2010-04-09
> **dannyboy79 said:**
> you removed quite from teh boot line but did you remove splash also? you should be getting a tty1 at a min. after it boots up and you hear its done you could hit ctrl-alt-f1, then type in username, hit enter, type in password, hit enter. you're now at the cli and you could try to issue a startx command after installing ati drivers. good luck. or you could even try to ssh after installing ssh blindly. good luck

I did try without splash, I thought I had mentioned it. Basically, as soon as the "would be" splash finishes, the same issue ocurrs. Attempting to get to the additional TTY's by pressing ctrl+alt+F1-6 fails also, although I'm pretty sure it's actually giving me the TTY login, but due to the configuration error I simply cannot see anything.

> **bsmith1051 said:**
> Thanks for reporting back!  So it's something to do with HDMI support.  Do you know which ATI driver was being used, the included (open-source) or the ATI proprietary?

Also, did you try this with a fresh install of the latest Beta?  This would clarify which video driver was being used, i.e., it would definitely be the included one.

Also, also, now that you're up-and-running, have you tried installing the latest ATI proprietary and _then_ switching to the HDMI cable again?  (You'd probably be best served shutting-down, switching the cable, then restarting)  I'd be curious to know if it works properly with the ATI proprietary but just has an issue 'getting to that point' during the upgrade/install.


Thanks for your great info, I tried this initially after the daily build on 31/3/10, but at that point there were still issues with the fglrx driver not installing properly and giving purple/grey screens. The driver being installed by default was the open source (radeon) driver, so it at least detected my card properly, and when my old monitor was connected via DVI it worked flawlessly at resolutions up to 1280x1024 - the native res for the monitor is 1600x1200.

After this happened, I tried to do exactly what you said - installing the fglrx drivers, but as I mentioned it produced the purple boot issue that plagued a lot of others. However, after another reinstall on 2/4/10, I had received the DVI cable I had purchased for my standard monitor, and by that time the driver on the repos was the more updated binary fglrx driver, which I then installed without a hitch. After that installed HDMI functined flawlessly, even with multiple monitors.

Therefore, at that point in time (a week ago) the open source radeon driver was DEFINITELY the cause of this HDMI issue, and if you can connect via DVI (even temporarily) to install the proprietary drivers, it should work properly after that.

I have been quite busy lately so I have gone back to using 9.10 for production purposes, but I will give the latest spins a shot later today/tomorrow to see if the issue has been fixed by now, and if not, I will file a bug report specifically regarding the radeon driver itself, which may serve to get it fixed before release.

Thanks again for your input though =)

---

### Post by dannyboy79 on 2010-04-09
> **Omoronovo said:**
> I did try without splash, I thought I had mentioned it. Basically, as soon as the "would be" splash finishes, the same issue ocurrs. 

Thanks again for your input though =)
it's probably a mut point by now but there should be no "would be splash" appearing as you removed "splash" from your boot line. it should take you right to gdm without using plymouth. then at that point, you could get to a tty1, login, then kill gdm, then startx. and you would be at your desktop. that's how I have been running since I installed a daily build on 4-5-10. I have been upgrading daily and still plagued with the gdm login staying in a crash loop. Plymouth is a huge mess as far as I am concerned. as you said though you may have another issue as I am not using ATI nor HDMI. good luck

---

### Post by kansasnoob on 2010-04-09
> Plymouth is a huge mess as far as I am concerned

+1!

Actually it's working OK with my Intel 82945G/GZ graphics but it stinks with my P4/M800 VIA graphics.

Although reading what I have in this thread I think this may go beyond Plymouth, possibly an Xorg bug?

Bugs in X are a real bear to troubleshoot :(

[https://wiki.ubuntu.com/X/Reporting](https://wiki.ubuntu.com/X/Reporting)

---

### Post by kansasnoob on 2010-04-09
I had a thought, perhaps a silly one, and I've not reviewed each post in this thread so apologies in advance if this has already been suggested and/or tried.

If you boot into Recovery mode now, when it's completed running you're presented with the following options:

Resume
Clean
Dpkg
FailsafeX
Grub
Netroot
Root

So, if you still have the install that was completed with the Alternate CD you might try selecting "FailsafeX" from those options and seeing if you can get to X.

Since I'm not having the same problem I have to do some guessing, but you may well get a text login prompt rather than GDM. If so you'll have to enter your username followed by your password.

You may also have to enter: 

```
startx
```

After entering your username and password. to begin the xsession.

---

