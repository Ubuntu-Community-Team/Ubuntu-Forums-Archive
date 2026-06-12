---
title: "Plymouth lucid"
date: 2010-01-13
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by ccw on 2010-01-13
Should plymouth be working yet? 

I've been running Lucid from upgraded Karmic for months. Its been flickering at a VTTY until GDM loads up for a while. Is there some steps I should be taking to get it running or is this the expected behavior at the moment?

---

### Post by philinux on 2010-01-13
I have it installed but it does not appear to be functioning yet.

---

### Post by ccw on 2010-01-13
> **philinux said:**
> I have it installed but it does not appear to be functioning yet.

Thanks :) Just checking to see if I was missing something.

---

### Post by maheshasolkar on 2010-01-13
I've installed Plymouth and it is working great - absolutely flicker free boot up from Grub to GDM. It was broken for a while, but the latest kernel update (or something along with it) fixed it.

My system uses Intel graphics. I wonder if that matters.

---

### Post by tad1073 on 2010-01-13
Plymouth is not working for me.

Linux thomthom 2.6.32-10-generic #14-Ubuntu SMP Thu Jan 7 17:38:08 UTC 2010 x86_64 GNU/Linux

---

### Post by ccw on 2010-01-13
> **maheshasolkar said:**
> I've installed Plymouth and it is working great - absolutely flicker free boot up from Grub to GDM. It was broken for a while, but the latest kernel update (or something along with it) fixed it.

My system uses Intel graphics. I wonder if that matters.

What do you see?

I just see vtty output.

Plymouth should have some sort of graphical eyecandy like:

[http://fedoraproject.org/w/uploads/5/5f/Plymouth-charge.ogg](http://fedoraproject.org/w/uploads/5/5f/Plymouth-charge.ogg)

---

### Post by LiquidMeson on 2010-01-13
Currently Plymouth is the nice white logo with the text Ubuntu on a black background. If it is to stay like this tho maybe it could have some multi-color glow behind it? The Plymouth image is currently static except for a bar when resuming from hibernation.

---

### Post by ranch hand on 2010-01-13
Mine is working fine on 7 installs, 1 with "edgers", 1 9.10minimal>10.04 upgrade, 1 with Lxde, 19.10>10.04 upgrade, 1 9.04>9.10>10.04 upgrade, 2 spares to test updates on.

The 9.04 upgrade seemed to be ahead of the rest in terms of Plymouth.  The rest have caught up pretty well.  The 9.10 upgrades still flicker when going from login to desktop for some reason.

Get the nice clean Ubuntu logo and text with a gnome "spinner" normally and a progress bar below the logo/text for fsck when that runs.

Simple, clean, fast, I like it.

---

### Post by biasquez on 2010-01-14
i have kubuntu lucic with nvidia 9600 gt (driver closed nvidia). plymouth doesn't work and i have only text

---

### Post by celticbhoy on 2010-01-14
Works fine with me on Aspire One. Unlike some I just waited for it come through the updates rather than install myself.

---

### Post by nilarimogard on 2010-01-14
Screenshot?

---

### Post by celticbhoy on 2010-01-14
I know not everyone is getting plymouth going yet, but I found this theme by oskude and think it should be considered.

---

### Post by celticbhoy on 2010-01-14
> **celticbhoy said:**
> I know not everyone is getting plymouth going yet, but I found this theme by oskude and think it should be considered.

oops forgot the link :-

[http://osku.de/post/plymouth_space-sunrise_ubuntu.ogv](http://osku.de/post/plymouth_space-sunrise_ubuntu.ogv)

---

### Post by garvinrick4 on 2010-01-14
That is nice Splash

---

### Post by celticbhoy on 2010-01-14
Yeah - just having a little bit of trouble getting it to work. Never used Plymouth before, and know little about it, but the directories used in the guys setup files differ.

He uses /usr/share/plymouth, but Lucid uses /lib/plymouth so with a bit of luck I will have it going soon.

---

### Post by durand on 2010-01-14
So should plymouth be working for everyone now? Because I still just get a tty. Nvidia graphics here..

---

### Post by Psumi on 2010-01-14
> **durand said:**
> So should plymouth be working for everyone now? Because I still just get a tty. Nvidia graphics here..

Did you install manually or let it update itself and include itself?

---

### Post by durand on 2010-01-14
Uhm, I didn't install anything extra. I upgraded from karmic so that could be the problem. I get the "Could not connect to Plymouth" message on startup.

---

### Post by nilarimogard on 2010-01-14
I think most people get that for now...

---

### Post by celticbhoy on 2010-01-14
> **durand said:**
> Uhm, I didn't install anything extra. I upgraded from karmic so that could be the problem. I get the "Could not connect to Plymouth" message on startup.

Just to say I am also on intel - maybe they have not got up to speed for the other graphics providers yet.

---

### Post by ranch hand on 2010-01-14
I am wondering if any one has put a background in to replace the black.  I gave it one whack just now and failed.

Well I thought I failed.  I actually did replace the bg, just not the boot up one.  I got the shut down screen to have my wallpaper on it (wrong size but that can be fixed easy enough).

The size of the image, I think needs to be your screen resolution size, in my case that would be 1440x900 (72.000 pix).  I used the standard xsplash/gdm image at 2560x1600.  It was a "little" big.

I replaced the /lib/plymouth/ubuntu-logo.png with one of the same name with the original layered on top of my image in gimp.

I need to go and do some hauling for the dreaded mother in law now but need to find the correct logo image to replace for the boot up.  The script under themes seemed to indicate the one I used but I probably didn't understand what I was reading.

---

### Post by maheshasolkar on 2010-01-14
> **durand said:**
> So should plymouth be working for everyone now? Because I still just get a tty. Nvidia graphics here..

I may be wrong here, but I don't think Plymouth is possible for Nvidia users (like me) since the binary driver does not support Kernel-based Mode-Setting - and doesn't plan to in foreseeable future. Here's quote from an interview in Phoronix in late October last year ([http://www.phoronix.com/scan.php?page=article&item=nvidia_qa_linux&num=6):](http://www.phoronix.com/scan.php?page=article&item=nvidia_qa_linux&num=6):)

> Q: Does NVIDIA have any intentions to provide Kernel-based Mode-Setting support?

Nothing definite, no, but we do get a lot of requests for it and it is something I hope we can pursue in the future.

Unless the plans have changed...

However, Nouveau may be an option. But I have not tried anything there yet.

---

### Post by BwackNinja on 2010-01-14
Plymouth is supposed to work on nvidia cards, even with the proprietary driver. Just not KMS, so you have to use a framebuffer.

---

### Post by maheshasolkar on 2010-01-14
> **BwackNinja said:**
> Plymouth is supposed to work on nvidia cards, even with the proprietary driver. Just not KMS, so you have to use a framebuffer.

That is good to know. My main system has Nvidia card and I'd love to get the smooth boot that I get on my laptop.

What does one do to use framebuffer? Is it automatically configured accordingly when plymouth is installed on a system that has Nvidia card?

---

### Post by biasquez on 2010-01-14
i have this error when i set new theme and update initrd:

could not start boot splash: No such file or directory

---

### Post by celticbhoy on 2010-01-14
what theme and how did you install

---

### Post by philinux on 2010-01-14
Forget plymouth I just got a boot time of 28 secs. At gdm in a flash even with tty stuff.

---

### Post by SevenMachines on 2010-01-14
plymouth not working here but i'm down to 14 sec til working desktop so i'm not too depressed :) still, i'd quite like to get plymouth up and running to fiddle about with some themes

---

### Post by biasquez on 2010-01-14
> **celticbhoy said:**
> what theme and how did you install
theme: solar
sudo plymouth-set-default-theme solar --rebuild-initrd

---

### Post by celticbhoy on 2010-01-14
> **biasquez said:**
> theme: solar
sudo plymouth-set-default-theme solar --rebuild-initrd

Did you first run sudo plymouth-set-default-theme solar --list ?

can you check that the directory exists in /lib/plymouth/themes ?

---

### Post by biasquez on 2010-01-14
yes, solar is in output shown with --list

---

### Post by celticbhoy on 2010-01-14
> **biasquez said:**
> yes, solar is in output shown with --list

First if you check in the /lib/plymouth/themes/solar dir there should be 6 .png files and one called solar.plymouth.
Then check that /lib/plymouth dir contains 8 .so files, 2 sub dirs, and ubuntu-logo.png.

---

### Post by ranch hand on 2010-01-14
It is there along with another one that appears to be animated (spinfinity).

---

### Post by terry_gardener on 2010-01-14
i am not getting plymouth is it because i am using nvidia graphic card 6 series.

just get writing and boots, quick boot so wouldn't be able to enjoy for to long anyway, but still it would be nice to have.

---

### Post by ranch hand on 2010-01-14
> **biasquez said:**
> theme: solar
sudo plymouth-set-default-theme solar --rebuild-initrd
What I want to know is where that command came from.  I admit to being a noob but you fellers seem to pull these commands out of thin air.

I have no idea if it worked or not.  I changed the image to what I wanted and ran the command in chroot.

I am not risking this install on this experiment.  I am going to be booting to that install shortly and see if that worked (no warnings or notices - just a pause and then a new prompt - promising).  I also resized the image for shut down.

Edit;
I just checked my /lib/plymouth/themes/default.plymouth file and it does list the correct theme as opposed to what it said before.

---

### Post by celticbhoy on 2010-01-14
> **ranch hand said:**
> What I want to know is where that command came from.  I admit to being a noob but you fellers seem to pull these commands out of thin air.

I have no idea if it worked or not.  I changed the image to what I wanted and ran the command in chroot.

I am not risking this install on this experiment.  I am going to be booting to that install shortly and see if that worked (no warnings or notices - just a pause and then a new prompt - promising).  I also resized the image for shut down.

I got it by searching on google, if you run it with --help instead of --list or a theme name you will see all available options. It is just the standard way to change themes in Plymouth - checked on Fedora forums.

---

### Post by celticbhoy on 2010-01-14
Meant to say check out the third post here for a run down on theming Plymouth :-

[http://ubuntuforums.org/showthread.php?t=1381109](http://ubuntuforums.org/showthread.php?t=1381109)

---

### Post by ranch hand on 2010-01-14
I will read that with care.

I am just back from checking to see if my images worked and the theme actually was changed.  About all I can say is - YUP it worked very well.

I will have to modify my images some more so that the text will show up if needed.  I think, looking at the original image, that any text thrown up is behind the image which is why the left 1/3 is transparent and the center 1/3 is almost transparent.  If anyone knows better I am certainly open to correction.

As hard as I worked to get images on xsplash and gdm during 9.10-testing I am very happy to have them back.  It is just fun to have the menu bg and the splash bg and gdm bg all match and go, as much as possible, seamlessly from one to the next.  I have some installs that I have not installed plymouth so they do not have the files but when I get around to it that will change.

---

### Post by biasquez on 2010-01-15
> **celticbhoy said:**
> First if you check in the /lib/plymouth/themes/solar dir there should be 6 .png files and one called solar.plymouth.
Then check that /lib/plymouth dir contains 8 .so files, 2 sub dirs, and ubuntu-logo.png.

 ls -al /lib/plymouth/
details.so        label.so          script.so         text.so           throbgress.so     ubuntu-logo.png
fade-throbber.so  renderers/        space-flares.so   themes/           two-step.so

ls -al /lib/plymouth/themes/solar/
box.png           entry.png         progress_bar.png  star.png
bullet.png        lock.png          solar.plymouth

---

### Post by vishalrao on 2010-01-16
I'm able to test run plymouth space-sunrise theme in X but does not play (garbled display) during VESA boot on my nvidia 8800GT... any ideas how to fix it?

---

### Post by philinux on 2010-01-18
Ok clean install alpha2. Nvidia active.

No sign of this mysterious plymouth. I get tty messages about fsck and ureadahead then black screen with spinning cursor, then gdm.

Tried setting plymouth theme to solar and rebooted. Then got additional message about directory does not exist. So I purged and reinstalled plymouth to give me the default settings.

---

### Post by durand on 2010-01-18
I got the same messages as you this morning along with the spinning cursor.

---

### Post by philinux on 2010-01-18
> **durand said:**
> I got the same messages as you this morning along with the spinning cursor.

This seems to be the only bug regarding this.

[https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/504052](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/504052)

---

### Post by ranch hand on 2010-01-18
It is kind of interesting that all seven of my 10.04 installs have plymouth, with all files, and 6 of them work very well and the solar and script themes are installable and work fine.

On the other one plymouth does not work at all.  That is an install with Lxde and Gnome installed and there may be something in that setup that is messing with plymouth but I do not see what it would be.

I am not running encryption as the person that filed the bug is and I am running in a live environment not VB.

I am playing with some of the OS' to see what I can do with plymouth and have not really tried to get it running in that recalcitrant OS.

---

### Post by durand on 2010-01-18
> **philinux said:**
> This seems to be the only bug regarding this.

[https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/504052](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/504052)

Thanks, I've subscribed to the bug.

---

### Post by philinux on 2010-01-18
> **ranch hand said:**
> It is kind of interesting that all seven of my 10.04 installs have plymouth, with all files, and 6 of them work very well and the solar and script themes are installable and work fine.

On the other one plymouth does not work at all.  That is an install with Lxde and Gnome installed and there may be something in that setup that is messing with plymouth but I do not see what it would be.

I am not running encryption as the person that filed the bug is and I am running in a live environment not VB.

I am playing with some of the OS' to see what I can do with plymouth and have not really tried to get it running in that recalcitrant OS.

Maybe it's an nVidia thing. Plymouthd is shown as running in bootchart. I'm running lucid on my internal disk 2, 64 bit.

syslog has these messages. There are no other plymouth errors in any other log.
```
lucid-testing init: plymouth main process (348) terminated with status 1
lucid-testing init: plymouth pre-stop process (1695) terminated with status 2
```

---

### Post by ranch hand on 2010-01-18
> **philinux said:**
> Maybe it's an nVidia thing. Plymouthd is shown as running in bootchart. I'm running lucid on my internal disk 2, 64 bit.

syslog has these messages. There are no other plymouth errors in any other log.
```
lucid-testing init: plymouth main process (348) terminated with status 1
lucid-testing init: plymouth pre-stop process (1695) terminated with status 2
```
Where in all that list are you finding this.

I just checked my syslog and syslog.1 and can find no mention of plymouth at all.  As it works and has a theme active on this install  I am baffled by not finding it.

---

### Post by philinux on 2010-01-18
> **ranch hand said:**
> Where in all that list are you finding this.

I just checked my syslog and syslog.1 and can find no mention of plymouth at all.  As it works and has a theme active on this install  I am baffled by not finding it.

sys>admin log file viewer. Syslog. Then View>Find>plymouth

I'd love this to work I've only seen clips on youtube.

Did plymouth work for you before you activated a theme?

---

### Post by ranch hand on 2010-01-18
> **philinux said:**
> sys>admin log file viewer. Syslog. Then View>Find>plymouth

I'd love this to work I've only seen clips on youtube.

Did plymouth work for you before you activated a theme?
Well, that was interesting.  Never did that before.  I always go to /var/log/whatever to see this stuff.

I am glad to report that I am not blind, all I got from find with plymouth typed in is "Not Found".  Oh well the bugger works anyway.

Yes it was working fine.  This OS is my main deal (daytime) and it is my Stoned Lizard.  Upgrade from StonerEdition1.0 - 9.04>9.10>10.04.  It was kind of interesting that this was the first OS to have plymouth working.  About a week before the others.

Black screen, Ubuntu circle logo followed by the word Ubuntu is all you get on the screen.  I like it.  Sharp, clean.

But we are in testing so you have to spend hours dicking with themes so you can see them for a few seconds.  The messing with them is fun but hardly worth the effort as far as production value goes.  In testing though that doesn't matter because you are TESTING things.  Important stuff here.

And I still have the one OS that seems, except for the added LXDE, to be identical to the other clean install installations where plymouth is working fine.

---

### Post by philinux on 2010-01-18
Ok if I get a terminal up and use

sudo plymouthd

then

sudo plymouth --show-splash

I get two black boxes with the ubuntu logo, so it must not be running at boot properly.

[http://brej.org/blog/?p=158](http://brej.org/blog/?p=158)

---

### Post by VMC on 2010-01-18
> **philinux said:**
> Ok if I get a terminal up and use

sudo plymouthd

then

sudo plymouth --show-splash

I get two black boxes with the ubuntu logo, so it must not be running at boot properly.

[http://brej.org/blog/?p=158](http://brej.org/blog/?p=158)

I get the same thing. My question is Plymouth going to be default in lucid at some point or another release?

If and when this happens goes then 'hal' go away? I still have 'hal' and no Plymouth. I don't necessarily want to go the ppa route at this time. Since this is testing I don't need anymore trouble.

---

### Post by ranch hand on 2010-01-18
I do not think that this is a problem with plymouth.  I think the problem is mountall.

When I get the hankeren to fool with the Lxde OS I am going to remove mount all and then install mount all.

I use synaptic for these things as I can see, easily, the other things effected.  If it can be done without too much damage I will "completely remove" the bugger before installing it.

I am sure that it was a mountall update that got plymouth working on this box with the Radeon video card.  In this case I doubt that the card really is the problem.  Mountall is a little squirely.

---

### Post by philinux on 2010-01-18
> **ranch hand said:**
> I do not think that this is a problem with plymouth.  I think the problem is mountall.

When I get the hankeren to fool with the Lxde OS I am going to remove mount all and then install mount all.

I use synaptic for these things as I can see, easily, the other things effected.  If it can be done without too much damage I will "completely remove" the bugger before installing it.

I am sure that it was a mountall update that got plymouth working on this box with the Radeon video card.  In this case I doubt that the card really is the problem.  Mountall is a little squirely.

What graphics cards are working with plymouth. Is this article still valid for alpha2.
[http://www.omgubuntu.co.uk/2009/12/lucid-to-use-plymouth-non-intel-users.html](http://www.omgubuntu.co.uk/2009/12/lucid-to-use-plymouth-non-intel-users.html)

---

### Post by plun on 2010-01-18
Just some facts.....  last time,  if it was Interepid or Jaunty,  it was possible to run Plymouth with a REAL nVidia driver.

I used this setting for my kernel, frame-buffers
[http://ubuntuforums.org/showpost.php?p=7017508&postcount=130](http://ubuntuforums.org/showpost.php?p=7017508&postcount=130)


Vishalrao wrote this yesterday........

> I had to blacklist the vga16fb module and add the vesafb module (nvidiafb doesnt seem to work for me).?

Within the Plymouth theming thread with this video

[http://www.youtube.com/watch?v=N-4xTkN1_RQ](http://www.youtube.com/watch?v=N-4xTkN1_RQ)

setgfxmode is one more key to this...  ;)

---

### Post by ranch hand on 2010-01-18
That is an interesting write up.  I wonder how well it reflects the real world today though, it is several weeks old and we have had a lot of xorg updates in that time.

My ATI card actually works better than it ever has with the generic driver.  I can go to their site and get a driver from them.  I did that to 9.04 a couple months ago and got rid of it the first day.  So all I have ever used is the generic.

I do have "edgers" on another of my installs and plymouth works there as well (everything is on this box).

---

### Post by dino99 on 2010-01-18
> **ranch hand said:**
> I do not think that this is a problem with plymouth.  I think the problem is mountall.

When I get the hankeren to fool with the Lxde OS I am going to remove mount all and then install mount all.

I use synaptic for these things as I can see, easily, the other things effected.  If it can be done without too much damage I will "completely remove" the bugger before installing it.

I am sure that it was a mountall update that got plymouth working on this box with the Radeon video card.  In this case I doubt that the card really is the problem.  Mountall is a little squirely.

i'm thinking about mountall too, as all the folders i've created are not there in nautilus.

---

### Post by plun on 2010-01-18
This one is important from Vishalraos movie..

[[img]http://ubuntu-pics.de/thumb/38708/snapshot50_WEvbJZ.png[/img]](http://ubuntu-pics.de/bild/38708/snapshot50_WEvbJZ.png)

setgfxmode and payload.

vga=xxx is deprecated as I knows it.

---

### Post by philinux on 2010-01-18
> **plun said:**
> This one is important from Vishalraos movie..

[[img]http://ubuntu-pics.de/thumb/38708/snapshot50_WEvbJZ.png[/img]](http://ubuntu-pics.de/bild/38708/snapshot50_WEvbJZ.png)

setgfxmode and payload.

vga=xxx is deprecated as I knows it.

Yes I tried the vga fix and also found the deprecation.

So do we add the setgfx and payload to /etc/default/grub after quiet spash then run update grub. Is that all there is to get plymouth going?

---

### Post by ranch hand on 2010-01-18
I decided to do a check on removing mountall via chroot to my Lxde install and found that this is a BAD idea.  A huge list comes up with things to be removed, nothing important if you don't mind on having an OS when it is through.

So I don't think I will go that route.  While there I did "apt-get install --reinstall mountall".  Have never had much luck with that doing anything but will see when I boot in there again this evening after running the theme install command and putting solar in straight instead of buggered up by me.

---

### Post by plun on 2010-01-18
> **philinux said:**
> Yes I tried the vga fix and also found the deprecation.

So do we add the setgfx and payload to /etc/default/grub after quiet spash then run update grub. Is that all there is to get plymouth going?

Vishalrao wrote this yesterday
> 
I had to blacklist the vga16fb module and add the vesafb module (nvidiafb doesnt seem to work for me).? 

> NOTE that blacklisting involves ensuring you run update-initramfs AFTER you've set everything in /etd/modules, /etc/initramfs/modules and /etc/modprobe.d/blacklist-framebuffer etc. else it wont pick up everything. I was making the mistake of changing only /etc/initramfs/modules then running update-initramfs before editing the modules/modprobe blacklists...


[http://ubuntuforums.org/showpost.php?p=8678772&postcount=44](http://ubuntuforums.org/showpost.php?p=8678772&postcount=44)

---

### Post by ranch hand on 2010-01-18
Well, that was FUN.

Just crashed my system hard while trying to open another OS in chroot.  I had just finished the Lxde solar theme install and decided to give it a whack.  Works now although the first boot brought it up, looked great, never went to the login screen, just rebooted.  Second time went great and all is good there.

---

### Post by philinux on 2010-01-18
> **plun said:**
> Vishalrao wrote this yesterday

[http://ubuntuforums.org/showpost.php?p=8678772&postcount=44](http://ubuntuforums.org/showpost.php?p=8678772&postcount=44)

I think I'll sit this one out. The time that plymouth will be on screen is about 5 seconds.

---

### Post by vishalrao on 2010-01-18
@phil: check out the next post :) [http://ubuntuforums.org/showpost.php?p=8679455&postcount=45](http://ubuntuforums.org/showpost.php?p=8679455&postcount=45)

because of that apparent bug in the theme script it would show for me in the test X window but would not (or be slow) in the actual bootup until i made those small changes - its quite sweet now that sunrise theme

---

### Post by vishalrao on 2010-01-19
Yay, nouveau is planned to be tried out for Alpha 3: [http://theravingrick.blogspot.com/2010/01/ubuntu-desktop-alpha-2-and-alpha-3-work.html](http://theravingrick.blogspot.com/2010/01/ubuntu-desktop-alpha-2-and-alpha-3-work.html)

:popcorn:

> Switching to -nouveau open source nvidia driver by default to support 3d and KMS (note that this is risky work and will depend on stability and quality of components in xorg and the kernel and will be backed outbefore end of Alpha 3 if necessary)

---

### Post by philinux on 2010-01-19
Many thanks to Vishalrao.

I ran these set of instructions. However I now get plymouth at shutdown but not at startup. Still getting tty1.
> 
1. Edit /etc/default/grub

add the line

GRUB_GFXMODE=1024x768x24
also add vga=792 like so 
GRUB_LINUX_DEFAULTS="quiet splash vga=792"

2. Edit /etc/grub.d/00_header and locate the line which adds "set gfxmode={GRUB_GFXMODE}" and add the line "set gfxpayload=keep" after it. Line 103 without the quotes.

3. sudo update-grub

4. Comment out "blacklist vesafb" in /etc/modprobe.d/blacklist-framebuffer.conf. Line 27
   and also add "blacklist vga16fb"

5. Add "vesafb" to /etc/modules and /etc/initramfs-tools/modules

6. sudo plymouth-set-default-theme --list # to see the list of themes
[sudo] password for philinux: 
details
fade-in
glow
script
solar
spinfinity
text
ubuntu-logo

7. sudo plymouth-set-default-theme solar --rebuild-initrd

Choose your theme from the above list.

Finally

8. sudo update-initramfs -u

9. Reboot.

---

### Post by vishalrao on 2010-01-19
step 7 replace "themename" with the actual theme name :) like "solar"

before step 3 (sudo update-grub) also try adding "vga=792" to the string with "quiet splash" in /etc/default/grub. i know it gives a "deprecated" warning but i have it enabled at the moment...

---

### Post by Tompalaz on 2010-01-20
Thank you (both) for your guide!
vishalrao, what theme were you using in your video?

---

### Post by philinux on 2010-01-20
> **vishalrao said:**
> step 7 replace "themename" with the actual theme name :) like "solar"

before step 3 (sudo update-grub) also try adding "vga=792" to the string with "quiet splash" in /etc/default/grub. i know it gives a "deprecated" warning but i have it enabled at the moment...

Yep I meant as you did that themename was meant to be replaced with one listed. The vga=792 did the trick for boot up. 

Cheers.

I raised a bug report for this, specifically for nvidia.
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/509328](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/509328)

Can someone pop to launchpad and confirm it for me cheers.

---

### Post by koso on 2010-01-20
On what tty are running yours xservers when using plymouth. KDM and KDE4 is after boot on tty8 (ctrl+alt+f8). Also when I restart KDM from tty1, it is started on tty9 ... it is quiet strange, becase when I disable plymouth (remove "quiet splash" from kernel line), it is always on tty7 as expected.

---

### Post by philinux on 2010-01-20
> **koso said:**
> On what tty are running yours xservers when using plymouth. KDM and KDE4 is after boot on tty8 (ctrl+alt+f8). Also when I restart KDM from tty1, it is started on tty9 ... it is quiet strange, becase when I disable plymouth (remove "quiet splash" from kernel line), it is always on tty7 as expected.

According to what I've read plymouth uses tty7 as per the norm.

---

### Post by vishalrao on 2010-01-20
@tompalaz: its the sunrise theme (ubuntu mod) which is quite sweet - see earlier posts in the plymouth theming thread: [http://ubuntuforums.org/showthread.php?t=1381109](http://ubuntuforums.org/showthread.php?t=1381109)

@philinux: bug confirmed, posted comment and subscribed.

---

### Post by philinux on 2010-01-21
> **vishalrao said:**
> 
@philinux: bug confirmed, posted comment and subscribed.

Cheers, many thanks again for your help on this.

---

