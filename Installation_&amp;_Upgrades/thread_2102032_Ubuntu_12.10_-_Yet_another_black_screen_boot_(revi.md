---
title: "Ubuntu 12.10 - Yet another black screen boot (revisited)"
date: 2013-01-06
forum: Installation &amp; Upgrades
---

### Post by jvincek on 2013-01-06
So, back in the day I started a thread with the oh-so-well-known black screen boot problem. You can find it [here]("http://ubuntuforums.org/showthread.php?t=1888390"). After a few days of torture I gave up and went on using Windows...
Yesterday I got the idea to setup a home server-ish thing on the same laptop, that's just been laying around these days, not doing much. So, I downloaded 12.10, made a bootable USB, started the install and the screen was very dim. Nonetheless, with the help of a flashlight (yeah..) I succesfully navigated all the menus and installed Ubuntu.

And, as you guessed, absolutely no progress has been made since the above-mentioned thread... If anything, it's gotten worse.
I've tried dosens of solutions when editing the boot parameters - radeon.modeset=0, xforcevesa, i915.modeset=0, acpi_osi=Linux, .....
The only thing that gave **any** signs of life was nomodeset (which, if you didn't read the above mentioned thread - helped me in getting low-res screen after boot a year ago in 11.10). But now in 12.10 first I get the "The system is running in low-graphics mode", followed by the "What would you like to do?" dialog, and after choosing "Run in low-graphics mode for just one session" and confirming "Stand by one minute while the display restarts..." I get a black screen with blue vertical stripes, and pink blinking blobs.
You can see that [here]("http://i49.tinypic.com/2u7m4qu.jpg").
There is a blinking blue "cursor" in the far top-left corner but I can't write anything. Pressing Ctrl+Alt+F1 removes the pink blobs (indicating there is some activity there) but again the blue stripes are there and I can't write anything...

In the end, I was very surprised that after more than a year the same problem is still there, and if anything it has gotten even worse (atleast in my case). And from what I can see, many people still have the purple/black screen problem (although most of them solve it with nomodeset).

Since I doubt I'll have the nerves to spend hours and hours trying dozens of workarounds fixing this extremely annoying bug (yes it's a bug and a huge one) again with little or no results, is there a Linux distro that doesn't suffer from this problem?

---

### Post by jvincek on 2013-01-06
Have I "crossed the line" asking for another distro in ubuntu forums?
I mean, don't get me wrong, I appreciate such a great free product but it's very frustrating when you waste a few hours on such a basic problem (boot up the intstalled system) that has been around for more than a year and is a very well known problem...

Any other suggestions?

---

### Post by gordintoronto on 2013-01-06
You haven't crossed the line, but you also have not provided useful information.

What is the video adapter? Run the command lspci and look for the line which includes "VGA."

This page might be helpful:
[http://linux-on-acer-aspire-5732z.blogspot.com/2011/06/backlight-workaround-for-linux-mint-11.html](http://linux-on-acer-aspire-5732z.blogspot.com/2011/06/backlight-workaround-for-linux-mint-11.html)

It suggests trying this command:
setpci -s 00:02.0 F4.B=60

I don't know what that command does. Also, it might not be relevant to your computer.

---

### Post by jvincek on 2013-01-06
Thank you gordintoronto for your response.

The solution from the link you mentioned deals with adjusting the brightness, which I doubt would do any good since the dim screen was a problem only during the install, after it the screen is completely black so I would say it's a problem with graphics drivers. I'll try it tomorrow if no better solution is hinted.

Anyway, the only way I'm able to get to any console input is through recovery mode, and by doing that I executed the command you suggested. The output was as follows (click for full size):

[[IMG]http://i48.tinypic.com/2rolxdw_th.jpg[/IMG]]("http://i48.tinypic.com/2rolxdw.jpg")

Looking at my old thread I also entered ***sudo lshw -C display*** and got the following (note the top is cut-off, I don't know how to decrease font size or set the output to multiple pages...)
[[IMG]http://i49.tinypic.com/1zchjzk_th.jpg[/IMG]]("http://i49.tinypic.com/1zchjzk.jpg")
Also, looking at your linked page, the "00:02.0" seems to be the "active" VGA device (just a guess on my part), and that part is fully visible on the screenshot above.

As mentioned in my previous topic, the relevant (to my opinion) hardware is:
HP G72-a26EZ with 2 graphic chips - ATI HD 5470, and one on the CPU itself - Intel Pentium P6000

For other detailed informations [here]("http://bizsupport1.austin.hp.com/bizsupport/TechSupport/Document.jsp?lang=en&cc=us&taskId=125&prodSeriesId=4169434&prodTypeId=321957&prodSeriesId=4169434&objectID=c02251551") is the HP official info on the laptop, and the Intel official page for the CPU (which has one of the GPUs embedded) can be found [here]("http://ark.intel.com/products/49058/Intel-Pentium-Processor-P6000-3M-Cache-1_86-GHz").

I hope that's enough info to get things rolling :)

---

### Post by jvincek on 2013-01-09
So no hope of fixing this? I'd still apreciate a good alternative distro recommendation that doesn't suffer from this issues if there is no solutions to this hardware/problem combo in ubuntu.

---

### Post by gordintoronto on 2013-01-09
What happened when you tried the setpci command?

Have you read this:
[http://forums.gentoo.org/viewtopic-t-909802.html](http://forums.gentoo.org/viewtopic-t-909802.html)

Are there keys which are supposed to change the backlight?

---

### Post by jvincek on 2013-01-10
First to answer your question - yes there are keys to change the backlight (Fn+F2/F3) but they don't work, I've tried them before & after using nomodeset, radeon.modeset=0, (and many others)

The problem with setpci command suggested [here]("http://linux-on-acer-aspire-5732z.blogspot.com/2011/06/backlight-workaround-for-linux-mint-11.html")  is that I can't edit files with gedit, since I don't have access to any  graphics! As I said, the only way I can write any commands is through  Advanced options for Ubuntu (grub option) > Recovery mode  > Drop  to root shell prompt.
When written there,
```
setpci -s 00:02.0 F4.B=60
```does nothing and outputs nothing,  it doesn't matter if I substitute 60 with 00 (which should control the  brightness as suggested). Whether it is because I'm at the graphically  primitive root shell I really can't tell.

While reading the [second suggested site]("http://forums.gentoo.org/viewtopic-t-909802.html"), I failed at the very first step of method 1:
```
 # emerge -av ati-drivers
```outputs
```
Error in sitecustomize; set PYTHONVERBOSE for traceback:
EOFError: EOF read where not expected
No command 'emerge' found, did you mean: 
Command 'merge' from package 'rcs' (universe)
Command 'fmerge' from package 'fhist' (universe)
Command 'vemerge' from package 'util-vserver' (universe)
Command 'esmerge' from package 'tstools' (universe)
emerge: command not found

```Now,  googling (what else is there to do...) I found that emerge is gentoo's  equivalent of apt-get install, but when trying that - file system is  read-only in root shell.

Found that the solution is "mount -o remount,rw /"[FONT=Tahoma], but after doing that I find that there is no networking after using apt-get install.

Going back  one step, in recovery menu there is a option to enable networking, but  upon doing that the whole thing does nothing. I'm left with a blinking  cursor where I can write anything but doing so does nothing, even  pressing enter - just goes to next line...

Frustrated, I ended up  downloading Fedora (staying clear of Ubuntu branch because a year ago I  tried with Mint with the same outcome), but the install screen is again  - very dim. Nevertheless, with the help of a flashlight (again) I  navigated the screens and installed it. But, at the end of install I got  a message that there was a problem installing bootloader! Great.

Now ofcourse I have a
[/FONT]```
Error: unknown filesystem
grub rescue >
```
and can't do anything.
Googling  again, the quickest solution seems to be Super Grub Disk 2, but hey,  it's website is down and all dowload sites either point to it or have  broken dowload links!

Dissapointed :sad:

---

### Post by jvincek on 2013-01-12
Ok, new info. After Fedora messed up the bootloader, I decided to pull out the laptop hard drive and fix the issues by hooking it up to my PC where there are no black screen problems. Long story short, after a few hours, deleted partitions and by using [boot-repair]("https://help.ubuntu.com/community/Boot-Repair"), I now have a Ubuntu that boots fine (on the PC, not the laptop).

Then I fount [this thread]("http://ubuntuforums.org/showthread.php?t=1668202"), which in its very title has my CPU listed (P6000). I downloaded the Quantal deb's from [drm-intel-next]("http://kernel.ubuntu.com/~kernel-ppa/mainline/drm-intel-next/2012-10-13-quantal/") directory, specifically (OS is x86):

[LIST]
[*]linux-headers-3.6.0-997-generic_3.6.0-997.201210130405_i386.deb
[*]linux-headers-3.6.0-997_3.6.0-997.201210130405_all.deb
[*]linux-image-3.6.0-997-generic_3.6.0-997.201210130405_i386.deb
[*]linux-image-extra-3.6.0-997-generic_3.6.0-997.201210130405_i386.deb
[/LIST]
And run: ```
sudo dpkg -i *.deb
```

But no progress, again the black screen pops up. Next step - try again the before mentioned solutions that weren't available before in hope something of that helps...

---

### Post by jvincek on 2013-02-17
Hey again...
Just wanted to report that sadly I didn't manage to resolve the original issue, which was to enable normal display on my laptop. But, in the first post I mentioned my intention was to setup a home server - so, after the dissapointments of multiple drivers/kernels/workarounds and whatnots, I settled for this:

[LIST=1]
[*]Plugged the hard drive to my PC (which has no display issues) and do a fresh install of Ubuntu
[*]Installed SSH & VNC support
[*]Returned HDD back to laptop, after turn-on I can hear the login screen sound, after which I enter the password
[*]When needed I can login to the server using SSH to do administrative work
[LIST]
[*]when the desktop is needed/preferred, I can also connect via VNC using the *"Accessing your PC over the Internet"* section found at [this helpful page]("https://help.ubuntu.com/community/VNC")
[/LIST]
[/LIST]
So basically I use a workaround to access the server desktop via VNC. Not the smoothest of solutions, but it works and enables me to do anything I could normally do.


Thanks to all suggestions and contributors ;)

---

