---
title: "Lucid beta X Crash Blank Black and Freeze"
date: 2010-03-22
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by svaens on 2010-03-22
Hi all, 

I just updated all to the latest as of march the 23rd from the main repo, and was playing. 

Hadn't done all that much; Open a browser, play with glxgears, shut them both down. 

Then I decided i'd have a look through the panel menus. 

One thing I noticed before the system crashed, as the menu slowly opened, there were no icons next to the menu items. Is that normal now?

So, as I was opening the menu ... Noticed it was not responding very fast .... waited .. then BOOM!!!!

blackness, blank (although a kind of flickering as well) and non-responsiveness to any ctrl-alt combinations. 

I REALLY won't be able to use lucid if it does this on release, so.... 

any idea what I can do to either;

a) fix it
b) find the appropriate error logs so I can post them in a bug report

?


p.s. I've got a sony vaio with intel main board and ATI graphics (HD 3470 mobility) using the open source radeon driver that is installed by default on lucid.

---

### Post by james4001 on 2010-03-26
Hi

I get this same issue. It seems to happen when i am running a web browser, i have tried chrome, epiphany and firefox. I get the most crashes with firefox and now im using chrome it seems to have reduced the frequency of crashes.

After every crash i look through the system logs but cannot see anything obvious causing the crash.

System is fully up to date, tested ram with memtest for a whole night with no errors to eliminate memory problems. I have no issues with windows 7.

Hardware:

VAIO FW11E
Intel P8400
ATi 3470

I have seen many similar crashes however this one is exactly the same as mine. I get a black flickering screen, unresponsive to ctrl alt backspace, alt sysrq reisub, alt f2....

Thanks for your time, james

---

### Post by shaftstick on 2010-03-31
I got the same issu. and it happen when i have thumbnails preview activate in nautilus ( only in folder with videos in it). i solve it by desactivate thumbnails in nautilus options.

but it happen when i try to launch ubuntuone client ( in the systeme panel) i don't have any solution for this one.

it crash sometime on web page with video ( flash)

Lucid lynx update-to-latest
ati radeon hd 2400 
ubuntu native radeon driver
compiz is activate

if any have a idea on what is the problem and how to mark this as but without any log file he'll save my life.

Thanks for your time

---

### Post by jaco223 on 2010-03-31
> **shaftstick said:**
> I got the same issu. and it happen when i have thumbnails preview activate in nautilus ( only in folder with videos in it). i solve it by desactivate thumbnails in nautilus options.

but it happen when i try to launch ubuntuone client ( in the systeme panel) i don't have any solution for this one.

it crash sometime on web page with video ( flash)

Lucid lynx update-to-latest
ati radeon hd 2400 
ubuntu native radeon driver
compiz is activate

if any have a idea on what is the problem and how to mark this as but without any log file he'll save my life.

Thanks for your time

Maybe the problem is with the video driver. I was having a black screen crash issue, and  I would have to hard boot the machine, but a workaround for now might be to edit GRUB and add nomodeset to the boot process:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" edit this line to look like  this:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"

Hope that helps,

Jaco

---

### Post by jaco223 on 2010-03-31
shaftstick, I have the same video card ati radeon hd 2400 xt.

---

### Post by cheapsaket on 2010-03-31
I had the same issues and it was due to the video drivers.
See this thread: [http://ubuntuforums.org/showthread.php?t=1434893](http://ubuntuforums.org/showthread.php?t=1434893)

---

### Post by jaco223 on 2010-03-31
> **cheapsaket said:**
> I had the same issues and it was due to the video drivers.
See this thread: [http://ubuntuforums.org/showthread.php?t=1434893](http://ubuntuforums.org/showthread.php?t=1434893)

cheapsaket did you get the issue resolved?  I'm following your link now, but what has seemed to work for me, as i have not had a crash today was editing GRUB, but I'm going to check out your link. Thanks.

Jaco

Edit. I'm not sure the fglrx will work for my Mac.

---

### Post by jaco223 on 2010-04-01
Zika, I had to reinstall Lucid this morning because I installed kde, but had problems with it, so I wiped
everything and jut finished reinstalling, but now I forget what file I need to edit to add nomodeset.

Jaco

---

### Post by cheapsaket on 2010-04-01
> **jaco223 said:**
> cheapsaket did you get the issue resolved?  I'm following your link now, but what has seemed to work for me, as i have not had a crash today was editing GRUB, but I'm going to check out your link. Thanks.

Jaco

Edit. I'm not sure the fglrx will work for my Mac.

My issue was related to the ATI 3650 card driver that comes with Lucid. I believe others have said disabling KMS would also resolve such an issue.
I went with using the proprietary fglrx drivers.

Sorry couldn't help you.

---

### Post by zika on 2010-04-01
> **jaco223 said:**
> Zika, I had to reinstall Lucid this morning because I installed kde, but had problems with it, so I wiped
everything and jut finished reinstalling, but now I forget what file I need to edit to add nomodeset.

Jaco```
gksu gedit /etc/default/grub
sudo update-grub
```
You might want to try it without nomodeset, I'm on KMS for several hours now...

---

### Post by shaftstick on 2010-04-02
> **jaco223 said:**
> Maybe the problem is with the video driver. I was having a black screen crash issue, and  I would have to hard boot the machine, but a workaround for now might be to edit GRUB and add nomodeset to the boot process:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" edit this line to look like  this:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"

Hope that helps,

Jaco

Thank Jaco Grub edit work for me but still have freezing on video thumbnail preview folder hope this will be solve before Lucid final release

shaftstick

---

### Post by ranch hand on 2010-04-02
> **shaftstick said:**
> Thank Jaco Grub edit work for me but still have freezing on video thumbnail preview folder hope this will be solve before Lucid final release

shaftstick
I hope you are filing bugs.  Nothing will be fixed if bugs are not filed.  This is the whole point of "testing".

Have it break now.  File bugs.  Let the devs work their voodoo.  Then the final will work.

---

### Post by iClouseau88 on 2010-04-02
No, this didn't work for me today.

After making changes,i.e.adding "nomodeset" to the kernel line in GRUB  and sudo update-grub, screen shows:

"Searching for GRUB installation directory...
found /boot/grub
/etc/default/grub: Line 1: nomodeset: command not found"

---

### Post by zika on 2010-04-02
> **iClouseau88 said:**
> No, this didn't work for me today.

After making changes,i.e.adding "nomodeset" to the kernel line in GRUB  and sudo update-grub, screen shows:

"Searching for GRUB installation directory...
found /boot/grub
/etc/default/grub: Line 1: nomodeset: command not found"in */etc/default/grub* set **GRUB_CMDLINE_LINUX_DEFAULT="**whatever_You_have **_nomodeset_"**
Update: I forgot: **sudo update-grub**...

---

### Post by iClouseau88 on 2010-04-02
> **zika said:**
> in */etc/default/grub* set **GRUB_CMDLINE_LINUX_DEFAULT="**whatever_You_have **_nomodeset_"**

OK. I added "nomodeset" to the end of the kernel line but that didn't work.

By the way, I later found out Bug#428769 mentions that compiz-gnome is responsible for black screen, blank screen and freeze problems with Lucid beta 1.  I think this is especially for legacy "ati' and "radeon" drivers.  So, I did the following to get my machine to boot into Lucid the normal way:

1. Boot into kernel 2.6.31-20-generic (recovery mode)
2. Select dpkg to rebuild broken packages
3. Resume load kernel the normal way (or something similar)
4. At the command line, login as usual
5. sudo apt-get remove compiz-gnome
6. sudo gdm --full-restart
7. Once inside Gnome desktop, login
8. Synaptic Package Manager to completely remove anything that has "compiz" (NB: My laptop has legacy ATI Radeon Xpress 200M video card, so I don't need compiz anyway).
9. sudo apt-get update and reboot

I will stick with this kernel 2.6.31-20-generic and avoid updating until well after Lucid is formally released, to make sure all bugs are sorted out.

---

### Post by zika on 2010-04-02
> **iClouseau88 said:**
> OK. I added "nomodeset" to the end of the kernel line but that didn't work.

By the way, I later found out Bug#428769 mentions that compiz-gnome is responsible for black screen, blank screen and freeze problems with Lucid beta 1.  I think this is especially for legacy "ati' and "radeon" drivers.  So, I did the following to get my machine to boot into Lucid the normal way:

1. Boot into kernel 2.6.31-20-generic (recovery mode)
2. Select dpkg to rebuild broken packages
3. Resume load kernel the normal way (or something similar)
4. At the command line, login as usual
5. sudo apt-get remove compiz-gnome
6. sudo gdm --full-restart
7. Once inside Gnome desktop, login
8. Synaptic Package Manager to completely remove anything that has "compiz" (NB: My laptop has legacy ATI Radeon Xpress 200M video card, so I don't need compiz anyway).
9. sudo apt-get update and reboot

I will stick with this kernel 2.6.31-20-generic and avoid updating until well after Lucid is formally released, to make sure all bugs are sorted out.I forgot **sudo update-grub** in my post. I had these blank black freezes up to several days ago, if I used KMS... Then, due to some upgrade, I suppose, I'm in KMS and ... I do not use Compiz so I do not think Compiz was to blame. Yes, I'e tried it periodically, just to be sure that Metacity is not to blame... In UMS there were no problems... Enjoying KMS lately, finally ... (2.6.34-999, 2.6.32-19. 2.6.32-ck in all three variety (generic, preempt, server))(ATI HD3650 512M)
There is no reason to completely remove Compiz. Just switch to Metacity...

---

### Post by iClouseau88 on 2010-04-02
> **zika said:**
> I forgot **sudo update-grub** in my post. I had these blank black freezes up to several days ago, if I used KMS... Then, due to some upgrade, I suppose, I'm in KMS and ... I do not use Compiz so I do not think Compiz was to blame. Yes, I'e tried it periodically, just to be sure that Metacity is not to blame... In UMS there were no problems... Enjoying KMS lately, finally ... (2.6.34-999, 2.6.32-19. 2.6.32-ck in all three variety (generic, preempt, server))(ATI HD3650 512M)
There is no reason to completely remove Compiz. Just switch to Metacity...

Hi,

I did sudo update-grub as well.  Forgot earlier that I had installed DKMS about a year ago. Any way, I did try UMS mode (radeon.modeset=0) but still no go. Spent the last few days struggling with this blank/black screen problem until I stumbled upon the suggestion to remove compiz-gnome.

If nothing else breaks, I am happy with leaving Ubuntu as is for a while, no need to update anything.

---

### Post by jerrylamos on 2010-04-02
> **ranch hand said:**
> I hope you are filing bugs.  Nothing will be fixed if bugs are not filed.  This is the whole point of "testing".

Have it break now.  File bugs.  Let the devs work their voodoo.  Then the final will work.

Bug #553926

I had expected at Beta time it would be refining packages not crashed dead pc's.

My i845 video intel crashes hard randomly, power off time.  Yes there are bugs filed.  No useful workarounds.

My i830 video intel has no screen.  Keyboard works, but no screen.  Bug filed.  No workarounds.

My ati Mobility 7500 crashes to login screen frequently, somehow Firefox goes down and takes Gnome and X with it.  Bugs filed.  No workarounds.

My ati Express 200 was the only one of my four test computers to be running reasonably.

I'm dual booted on all four so when the dreaded update does its work I do have something to run.

Jerry

---

### Post by iClouseau88 on 2010-04-02
Hello jerrylamos,

Do you mind letting me know which kernel you are using for your ati xpress 200 machine and what steps were taken to log into and run Lucid successfully?

Thanks a lot for your help.

---

### Post by shaftstick on 2010-04-06
ok for my test i reintall lucid (previous installation was a dist-upgrade from karmic)

i got more freezing now even when compiz isn't activate. i filed bug on launchpad and waiting for a miracle Lucid is great but this bug is very annoying for a LTS release.

---

### Post by iClouseau88 on 2010-04-07
Try adding "vga=792" to the kernel options (kopts) line in Grub menu, right after "quiet splash", "acpi=off" and "noapic". This works for me.

---

### Post by shaftstick on 2010-04-07
hello all.
i solve the issue by installing kernel version 2.6.33 and use xedger ppa for ati driver.
result no more crash no more freezing and more pleasure using Lucid
Hope this help.

shaftstick

---

### Post by jerrylamos on 2010-04-07
> **jaco223 said:**
> Maybe the problem is with the video driver. I was having a black screen crash issue, and  I would have to hard boot the machine, but a workaround for now might be to edit GRUB and add nomodeset to the boot process:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" edit this line to look like  this:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"

Hope that helps,

Jaco

In my case with i845 intel video and ati Mobility 7500 the option "nomodeset" doesn't work.  KMS is still on and black screens happen.

What does work better is:
for any intel, sudo gedit /etc/default/grub
change "quiet splash" to "quiet splash i915.modeset=0"
for the ati,
change "quiet splash" to "quiet splash radeon.modeset=0"
save
sudo update-grub
reboot

Good luck...Jerry

---

### Post by Éderson on 2010-04-09
How can I update the grub of my computer if I have to start it from cdrom/pendrive?

---

### Post by dino99 on 2010-04-09
> **Éderson said:**
> How can I update the grub of my computer if I have to start it from cdrom/pendrive?

an example how to do:

[http://ubuntuforums.org/showthread.php?t=1263030&page=2](http://ubuntuforums.org/showthread.php?t=1263030&page=2)

---

