---
title: "Updated Ubuntu, now booting is a problem"
date: 2010-02-10
forum: Installation &amp; Upgrades
---

### Post by markallenneil on 2010-02-10
I'm getting to where I dread updating Ubuntu, as I always spend hours (or days) fixing issues which occur as a result.  I can't imagine a computer novice handling this.


[LIST=1]
[*]A few hours ago, I booted Ubuntu 2.6.31-17... no issues.
[*]Update Manager says there are updates... so I give it the go-ahead.
[*]Some of the updates are pertaining to a new kernel 2.6.31-19.  Still, I say go-ahead.
[*]Upon rebooting, from the GRUB menu I choose the topmost option 2.6.31-19.
[*] I get the first boot screen, then all goes black.  I wait.
[*] Eventually I hit <enter> and am rewarded with an "initramfs" prompt.
[*] An alert onscreen says "/dev/sdg1" does not exist.  Not surprising, as sdc1 is my boot partition.
[*]Eventually I find that if I edit the GRUB entry for 2.6.31-17 (old kernel) from "sdg1" to "sdc1", I can get Ubuntu to boot.  Well, not always... about half of the time it works.  I hate non-determinism.
[*] Editing the 2.6.31-19 never yields a complete boot.
[*] I tried issuing a "grub-install /dev/sdc1" as this has "fixed" things in the past.  Didn't work.
[/LIST]
 
So I'm not sure where to go from here.  There are very elaborate GRUB2 tutorials I can read to try to get my boot options pointing to the correct drive.  Is this what I should do?

Ever since Ubuntu made GRUB2 standard, I've found the boot situation a nightmare.  GRUB2 keeps installing itself to hd0 without asking... this is my WinXP soft-raid 0 array... and I'm scared witless to be left with a corrupted raid.  I always have to jump through hoops to fix the MBR.  So I boot from a USB disk... too much to ask for GRUB to leave other disk drives alone?

Thanks in advance for any constructive advice.

Mark

PS. I have the custom NVIDIA drivers installed in 2.6.31-17.  Must I reinstall (hidden recompile) with 2.6.31-19?

---

### Post by Kir_B on 2010-02-10
Well, at least you can boot into your Ubuntu, which means you're having a little less problem than some of us poor souls.

A quick couple of questions. Did you install karmic, or did you upgrade tfrom jaunty?

If you upgraded from jaunty, did you upgrade grub legacy to grub2?

If you upgradedyour grub or installed Ubuntu from a Karmic 9.10 cd, try to run the following command:

```
sudo grub-mkconfig -o /boot/grub/grub.cfg

```

Please post the results for all to see.

---

### Post by markallenneil on 2010-02-10
In this case, I'd simply authorized the Update Manager to install the latest updates... I was already running 9.10 (Koala).  I had a horrible experience this last December upgrading from 9.04 to 9.10... and then again last month trying to fix that botched situation by doing a clean install ([documented here]("http://markallenneil.com/articles/an-ubuntu-upgrade-nightmare/")).  But this time I didn't expect a problem as it was such a small "update."  Sigh.

If it is still of interest, the following is the output of the command you'd asked to see:
```
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-19-generic
Found initrd image: /boot/initrd.img-2.6.31-19-generic
Found linux image: /boot/vmlinuz-2.6.31-17-generic
Found initrd image: /boot/initrd.img-2.6.31-17-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Dell Utility Partition on /dev/mapper/nvidia_dcjajgjg1
grub-probe: error: no mapping exists for `nvidia_dcjajgjg1'
Found Microsoft Windows XP Professional on /dev/mapper/nvidia_dcjajgjg2
grub-probe: error: no mapping exists for `nvidia_dcjajgjg2'
done
```Oh, and this is all an issue with GRUB2.  If there was an option to stick with GRUB when I upgraded to 9.10, I must have missed it.

Thanks.

---

### Post by Kir_B on 2010-02-10
> **markallenneil said:**
> In this case, I'd simply authorized the Update Manager to install the latest updates... I was already running 9.10 (Koala).  I had a horrible experience this last December upgrading from 9.04 to 9.10... and then again last month trying to fix that botched situation by doing a clean install ([documented here]("http://markallenneil.com/articles/an-ubuntu-upgrade-nightmare/")).  But this time I didn't expect a problem as it was such a small "update."  Sigh.

If it is still of interest, the following is the output of the command you'd asked to see:
```
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-19-generic
Found initrd image: /boot/initrd.img-2.6.31-19-generic
Found linux image: /boot/vmlinuz-2.6.31-17-generic
Found initrd image: /boot/initrd.img-2.6.31-17-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Dell Utility Partition on /dev/mapper/nvidia_dcjajgjg1
grub-probe: error: no mapping exists for `nvidia_dcjajgjg1'
Found Microsoft Windows XP Professional on /dev/mapper/nvidia_dcjajgjg2
grub-probe: error: no mapping exists for `nvidia_dcjajgjg2'
done
```Oh, and this is all an issue with GRUB2.  If there was an option to stick with GRUB when I upgraded to 9.10, I must have missed it.

Thanks.
Wow. I don't know how to respond to that! I upgraded to karmic from jaunty and afterwards was still running grub legacy. When doing a clean install, you don't have a choice between grubs. 
                                         P.S. sorry it took so long to get back to you, but I keep getting sidetracked . Kir_b

---

### Post by Kir_B on 2010-02-10
The following command in the terminal was what fixed mine.

```
sudo grub-mkconfig -o /boot/grub/grub.cfg

```                     Kir_b

---

### Post by Kir_B on 2010-02-10
Hang on a couple of minutes while I find the make device map command.
                 Kir_b

---

### Post by Kir_B on 2010-02-10
Try the following command:

```
 sudo grub-mkdevicemap
```

Then run the following again afterwards and then post those results:

```
sudo grub-mkconfig -o /boot/grub/grub.cfg

```

                         Peace. Kir_b

---

### Post by markallenneil on 2010-02-10
So I ran both commands... the first output nothing... the second output the same thing it did the first time.

I'm going to reboot... see if there is any change.

Thanks for the continued support...

---

### Post by Kir_B on 2010-02-10
[LEFT]Keep us updated and please post those results it would be nice to see anyhow.
                                      Kir_b
[/LEFT]

---

### Post by markallenneil on 2010-02-10
Wow... it now boots correctly... both 2.6.31-17 and 2.6.31-19.  And with the latest kernel, the NVIDIA drivers are clearly still operational.

So... THANK YOU... you saved the day, Kir_B... :D

When I edit the entries in the GRUB boot screen, I see a few differences...

One, there is a "set root=(hd2, 1)" command... this is new (and correct).
Two, instead of "/dev/sdg1" as the boot partition... there is now a long command employing a UUID... "root=UUID=xxxx...xxxx".  The UUID is obviously an indirection... but whatever, it works now.

Thanks much for the help.  I'll be posting these commands in a journal article at my site... so I'll have them on hand the next time I'm stuck.

Mark

---

### Post by Kir_B on 2010-02-10
> **markallenneil said:**
> Wow... it now boots correctly... both 2.6.31-17 and 2.6.31-19.  And with the latest kernel, the NVIDIA drivers are clearly still operational.

So... THANK YOU... you saved the day, Kir_B... :D

When I edit the entries in the GRUB boot screen, I see a few differences...

One, there is a "set root=(hd2, 1)" command... this is new (and correct).
Two, instead of "/dev/sdg1" as the boot partition... there is now a long command employing a UUID... "root=UUID=xxxx...xxxx".  The UUID is obviously an indirection... but whatever, it works now.

Thanks much for the help.  I'll be posting these commands in a journal article at my site... so I'll have them on hand the next time I'm stuck.

Mark

The uuid is a more accurate description for grub to find the correct partition to boot from {I think}. I do believe this is a good thing. I'm glad I could help in some way.

P.S post your website, as I'd love to see what you got going on.
      Peace. Kir_b

---

### Post by markallenneil on 2010-02-10
I've got a few websites... something to keep me occupied between jobs.

[www.markallenneil.com]("http://www.markallenneil.com")... my personal site.  Employs the Symphony CMS.
[www.authorcollector.com]("http://www.authorcollector.com")... a place to track your favorite authors and their books.  In Drupal.
[www.sparklegram.com]("http://www.sparklegram.com")... an AS3 application I did to demonstrate persistence of vision. Plain old XHTML.

My initial motivation to install Ubuntu was to get a local LAMP stack running... IMO a better web development environment than Windows.

Cheers... Mark

---

### Post by Kir_B on 2010-02-11
> **markallenneil said:**
> I've got a few websites... something to keep me occupied between jobs.

[www.markallenneil.com]("http://www.markallenneil.com")... my personal site.  Employs the Symphony CMS.
[www.authorcollector.com]("http://www.authorcollector.com")... a place to track your favorite authors and their books.  In Drupal.
[www.sparklegram.com]("http://www.sparklegram.com")... an AS3 application I did to demonstrate persistence of vision. Plain old XHTML.

My initial motivation to install Ubuntu was to get a local LAMP stack running... IMO a better web development environment than Windows.

Cheers... Mark

Awesome. Thanks for the links, I'll check them out. I don't have a website, but would love to have one, and if I could afford it I would. I believe that linux is a better environment for just about everything and I try to avoid Microsoft at all costs {it is a monopoly that should be criminalized for holding humanity back}. I remember a time when monopolies used to be frowned upon, I guess it depends on who operates the monopolies.
                          Thanks. Kirby

---

### Post by markallenneil on 2010-02-11
I host all three websites at GoDaddy... costs me about $4.25 per month... so a vente latte at Starbucks per month.  Not so expensive... :D

Not that I recommend GoDaddy... there are better choices.  But a good starter host.

As to MS... they've done good and bad.  IMO not really more or less evil than many other big companies I've dealt with... perhaps their misdeeds are just more publicized.  If it weren't for games, our house would probably be all Macs by now.  But can't live without video games.

Cheers.

---

### Post by Kir_B on 2010-02-11
Ah Microsoft. I wouldn't be here if it wasn't for their "[COLOR=#00cccc][COLOR=#000000][COLOR=#cc33cc][Microsoft .net framework]("http://en.wikipedia.org/wiki/Mozilla_Firefox#.Net_Framework_3.5_Service_Pack_1")[/COLOR][/COLOR][/COLOR]", which forced me into following [COLOR=#cc33cc][Brad Abrams]("http://blogs.msdn.com/brada/archive/2009/02/27/uninstalling-the-clickonce-support-for-firefox.aspx") [/COLOR][COLOR=#cc33cc][removal instructions]("http://blogs.msdn.com/brada/archive/2009/02/27/uninstalling-the-clickonce-support-for-firefox.aspx"). M$ installed it into my vista and my firefox. There was no uninstall button on it {in firefox} and it kept crashing my browser every half hour or so, which could only be remedied by rebooting 20 times per day. As far as I'm concerned, there should be a class action lawsuit for lost productivity. I, alone should be compensated for the 100's of hours I spent trying to fix it. Needless to say, if they hadn't pulled this little stunt on their biggest competitor, I would still be putting up with their crappy operating system {there really is no comparison to Ubuntu and Linux}.
I really have to remember to send them a great big thank you.:p
[/COLOR]

---

### Post by markallenneil on 2010-02-11
Odd... I've got .NET and FireFox and (as far as I know) the two coexist peacefully.  I'm not running Vista though... still on WinXP... which serves me well enough.  I'm pretty careful though to deselect the "toolbars" which everyone seems to want to install for me (MS, Apple, Sun... all guilty of this).

I'm in rather deep with MS products... the bulk of my career in product development (and leading development) has been on MS operating systems using MS tools.  I've cursed MS more times than I can count.  Yet my experience with Ubuntu has also been very frustrating... I'd have to go back to Windows 3.1 to find a comparable experience.

Anyway, not to rain on your parade... it is heartening to hear you're so happy with Ubuntu.  Best wishes, and again thanks for the helping hand.

---

### Post by SalishSea on 2010-02-11
I am also having trouble after upgrading mindlessly to .19 on by 64 bit NVIDIA box (4 Gig) 

Here's where I am at:

1) I have half-installed GRUB2, which I chain load from 1.5.
2) I select kernel 2.6.31.19 or .17 and continue on.
3) Karma loads, then I am presented with the new splash screen; there is some visual noise on the splash screen.
4) Whether I sing in or not, the system reboots after ~10-15 seconds.
5) I have purged and re-instaled xserver-xorg, and I have run the nvidia diver program ENVYNG and installed 185.18.36-0ubuntu9 which it tells me is correct and reommended.

6) I have rebooted, only to again have the same problems. Suggestions?

---

### Post by SalishSea on 2010-02-11
Well, success, of a sort.

I (again) issued the 

sudo grub-mkconfig -o /boot/grub/grub.cfg

suggested previously, but this time after having migrated completed to Grub 2.

Then I reconfirmed with envyng that I was using the right NVIDIA drivers.
A bit of hand to hand combat with xorg.conf and nvidia-settings was needed to recognize my second screen, and to get my dual head display working again. For reasons that may be unrelated, I could no longer run firefox, although it was there, and I could not find a .lock file.  So, I had to purge and reinstall firefox, but .... All seems well know.

I have to say that was a bit bloody for a simple kernel release.  What happened to the Quality Control and testing?

---

### Post by Kir_B on 2010-02-11
> **markallenneil said:**
> Odd... I've got .NET and FireFox and (as far as I know) the two coexist peacefully.  I'm not running Vista though... still on WinXP... which serves me well enough.  I'm pretty careful though to deselect the "toolbars" which everyone seems to want to install for me (MS, Apple, Sun... all guilty of this).

I'm in rather deep with MS products... the bulk of my career in product development (and leading development) has been on MS operating systems using MS tools.  I've cursed MS more times than I can count.  Yet my experience with Ubuntu has also been very frustrating... I'd have to go back to Windows 3.1 to find a comparable experience.

Anyway, not to rain on your parade... it is heartening to hear you're so happy with Ubuntu.  Best wishes, and again thanks for the helping hand.

I researched the life out of the .net framework and I can tell you with complete certainty, that this little scam that Microsoft pulled, only affected Vista users. I also avoid like the plague, the toolbars that every company tries to install into our systems. I learned early on to choose the "custom" installations, after all, not choosing custom would result with more toolbars in my browser than I have buttons on my toolbars. Okay, I'm exaggeratiung, but not by much.:p

While I do agree that Ubuntu can be veeery frustrating at times. For the most part, the frustration is caused by my own doing, as I love customizing every application that I can. Things like this grub2 being released before it's ready for prime time is one of the rarer sources of frustration. I just don't understand why grub2 was released before it was completed, especially when considering that grub legacy was doing the job with zero problems {there are a lot of people that are p'd off about this}. 

I often find myself wondering just how deeply Microsoft has managed to infiltrate the upper ranks of the Linux community, after all, corporate espionage is just another operational expense when operating a successful monopoly.

Now, having said all that, I'm a little frustrated right now, as I'm just entering into another bout of extensive research to find out why my Compiz, KDE and gnome have all of a sudden stopped playing nice together.

So I hear you and wish you all the luck in the world.

             Peace. Kirby  :rolleyes:

---

### Post by Kir_B on 2010-02-11
> **SalishSea said:**
> Well, success, of a sort.

I (again) issued the 

sudo grub-mkconfig -o /boot/grub/grub.cfg

suggested previously, but this time after having migrated completed to Grub 2.

Then I reconfirmed with envyng that I was using the right NVIDIA drivers.
A bit of hand to hand combat with xorg.conf and nvidia-settings was needed to recognize my second screen, and to get my dual head display working again. For reasons that may be unrelated, I could no longer run firefox, although it was there, and I could not find a .lock file.  So, I had to purge and reinstall firefox, but .... All seems well know.

I have to say that was a bit bloody for a simple kernel release.  What happened to the Quality Control and testing?

Quality control and testing? I'm getting the feeling that Microsofts agents are in control of the testing now. These last three Kernels have not been up to snuff. The 2.6.31-18 was not good for me, as it all of a sudden caused some of my applications to use way way more resources than before. My electricsheep was taking my processor up to 50 degrees celsius {122 farenhiet} in less than a half of an hour. 2.6.31-19/20 have me enjoying a black screen until I get to the log in screen. I guess black is in these days?

Needless to say, I'm back to using the 2.6.31-17 Kernel.

Enjoy your day everyone. Kirby

---

