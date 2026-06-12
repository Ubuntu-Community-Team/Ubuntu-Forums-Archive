---
title: "Kernel 3.2.0.34 Killed Ubuntu"
date: 2012-11-30
forum: Installation &amp; Upgrades
---

### Post by NM5TF on 2012-11-30
I have been using 12.04 LTS for some time now...

I have been using kernel 3.2.0.33 with no problems...

this morning I installed the update to kernel 3.2.0.34
and now I can't boot....I get an error message stating
that my PC can only run in "low graphics mode" that I 
assume is concerned with my Nvidia graphics card...

it gives me 4 options: 

one is to run in low graphics mode for 1 session

another option is to reset my graphics

another option is to log-in to command line

NONE of these options do anything...it just sits there...

I tried using "boot repair CD" but that also did nothing...
there is a paste of the boot repair output at:

paste.ubuntu.com/1400028/

is there any way I can get back to using kernel 3.2.0.33???

I had to use a copy of 10.04 LTS running in "try Ubuntu mode"
to even get to this forum...

help please!!!

Tommy

---

### Post by snowpine on 2012-11-30
Reboot and choose the old kernel from the GRUB boot menu.

---

### Post by howefield on 2012-11-30
Hold the shift key whilst booting to get a list of installed kernels which will allow you to boot into the previous working one.

Or if 12.04 has an "Advanced Options" selection during the grub boot, select that and you will be able to select the previous kernel.

---

### Post by NM5TF on 2012-11-30
> **snowpine said:**
> Reboot and choose the old kernel from the GRUB boot menu.

the GRUB menu never shows up or I would have used the old kernel...

it just comes up with the low graphics mode warning & hangs there...

does the upgrade to a new kernel purge the old kernel??? I don't
remember it doing so in the past.....

---

### Post by snowpine on 2012-11-30
Here's some help with GRUB2 in Ubuntu: [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by NM5TF on 2012-11-30
> **howefield said:**
> Hold the shift key whilst booting to get a list of installed kernels which will allow you to boot into the previous working one.

Or if 12.04 has an "Advanced Options" selection during the grub boot, select that and you will be able to select the previous kernel.

holding down shift key during boot has no effect....no list
of kernels shows up

it still hangs up at the low graphics mode screen....

I am convinced the problem lies with the Nvidia drivers
not being updated to work with the new Linux kernel...after
every kernel update I have to work with the Nvidia driver
to make it work correctly...this is the 1st time it has killed
the OS tho...

---

### Post by YannBuntu on 2012-11-30
Hello

> **NM5TF said:**
> I tried using "boot repair CD" but that also did nothing...
there is a paste of the boot repair output at:

paste.ubuntu.com/1400028/

Please run Boot-Repair --> Advanced options --> "GRUB options" tab --> tick "Uncomment GFXMODE" --> Apply
Tell us the new URL that will appear.
Then reboot and indicate what you observe.

---

### Post by NM5TF on 2012-11-30
> **YannBuntu said:**
> Hello



Please run Boot-Repair --> Advanced options --> "GRUB options" tab --> tick "Uncomment GFXMODE" --> Apply
Tell us the new URL that will appear.
Then reboot and indicate what you observe.

thanx YannBuntu....that seemed to fix my problem as I can now
see the GRUB menu & select the previous kernel that is working...

all is well so far....

question: will I have to redo this operation every time I reboot,
or will it be a "permanent" solution???

FYI...the new paste is at 

paste.ubuntu.com/1400595/

thanx again

Tommy

---

### Post by YannBuntu on 2012-11-30
This is a permanent fix.

Let's check if the bug is also present in the very last kernel.
If it is, you will absolutely need to report the bug, or you won't be able to use next Ubuntu versions.

Here is how to do it:

go here: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.7-rc7-raring/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.7-rc7-raring/)
Download:
the  *all.deb file
and
the three *amd64.deb files

Install them (there may be an order follow).
Then reboot your PC.
Select the first entry ('Ubuntu'), and see if it boots Ubuntu or not. Remark: this entry is the one with the 3.7-rc7 kernel.

- **If yes**, then it's perfect, that means the bug has already been solved in the last kernel.
- **If not**, you will have to report the bug:
boot your installed Ubuntu via the previous kernel
then open a terminal and type:
```
ubuntu-bug linux
```
this will gather data , and open a Firefox page.
Fill in the bug title: "[Regression] cannot boot since kernel 3.2.0.34"
Fill in the bug description, including a link to this thread.

When you have finished the bug report, please tell us the link to it, so that we can follow-up.

---

### Post by NM5TF on 2012-11-30
YannBuntu...

I downloaded all 4 files from the ppa site you sent...

I was able to install the *all.deb file and the linux-headers-3.7.0-030700rc7-generic_3.7.0-030700rc7.201211252135_amd64.deb
file with no problems...

When I attempted to install the linux-image-3.7.0-030700rc7-generic_3.7.0-030700rc7.201211252135_amd64.deb file it gave
me an error stating that I did not want to install it as it
will break my existing install of the working 3.2.0-33 kernel...

I am unable to install the 3.7 image or extras files....

thanx again for the help in getting my working kernel back!!!

Tommy

---

### Post by YannBuntu on 2012-11-30
ok, then let's try something else: 
download the amd64 iso of the Ubuntu development version: [http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)
burn it on a DVD or liveUSB,
boot on it, and tell us if you can choose "Try Ubuntu", and access the live session ?

---

### Post by NM5TF on 2012-11-30
> **YannBuntu said:**
> ok, then let's try something else: 
download the amd64 iso of the Ubuntu development version: [http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)
burn it on a DVD or liveUSB,
boot on it, and tell us if you can choose "Try Ubuntu", and access the live session ?

I would really like to help with the debug, but the image is
too large to fit on a CD and I don't have a DVD burner or a
USB stick to download it onto....

I could load it onto a VM using Virtual Box, but don't know
if that would suit your purpose or not....let me know if that
option will work for you & I will proceed...

Tommy

---

### Post by YannBuntu on 2012-12-01
No, a VM wouldn't help.

New Ubuntu images (including 12.10) do not fit onto CD any more, so i recommend you buy a USB key...

---

### Post by NM5TF on 2012-12-01
I downloaded the raring-desktop-amd64.iso file and used GRML
to make a GRUB menuentry....it did show up on the GRUB menu 
at boot....
I then tried to boot from it without any success....

It did go to the option screen asking if I wanted to try or install
the OS.....neither option did anything except hang up at a blank 
screen....

I then mounted it via loopback so I could examine the file contents...
results as follows:

/ / EFI/ README.diskdefines autorun.inf boot/ casper/ dists/ install/
isolinux/ md5sum.txt pics/ pool/ preseed/ wubi.exe

I also looked at  casper/ with the results as follows:

/ / filesystem.manifest filesystem.manifest-remove filesystem.size
filesystem.squashfs initrd.lz vmlinuz

I tried to boot it again and observed the following error:

grub> boot = no loaded kernel

I thought the kernel was located in vmlinuz

what am I missing???

any ideas???

Tommy

---

### Post by YannBuntu on 2012-12-01
I am not sure of what you lastly did, but it seems that the last kernel doesn't work either. So please report the bug this way:

> **YannBuntu said:**
> 
boot your installed Ubuntu via the previous kernel
then open a terminal and type:
```
ubuntu-bug linux
```
this will gather data , and open a Firefox page.
Fill in the bug title: "[Regression] cannot boot since kernel 3.2.0.34"
Fill in the bug description, including a link to this thread.

When you have finished the bug report, please tell us the link to it, so that we can follow-up.

---

### Post by NM5TF on 2012-12-01
> **YannBuntu said:**
> I am not sure of what you lastly did, but it seems that the last kernel doesn't work either. So please report the bug this way:

when I entered the code you gave me it did NOT go to a Firefox page...
it came up with an APPORT screen & started gathering data...and then
it generated a "problem report".....

there is NO way to enter any title information or any way to describe
the problem....

all the data gathered points to the 3.2.0-33 kernel that is WORKING
and NOT to the non-working kernel 3.2.0-34 or the new 3.7.0-rc7 kernel

I am reluctant to send the problem report because it points to the 
WORKING kernel....it seems that if I send that report then the devs will
be looking at the wrong kernel...unless I am mistaken....

I have attached a screenshot of the "problem report" below...

Tommy

---

### Post by YannBuntu on 2012-12-01
Don't worry, the devs will not mistake, if you explain the problem in the bug report.
The gathered information show the old kernel, but also many other data that may be useful for the devs.
This was the good way.
The Firefox page will open after you click the "SEND" button in the window you showed.

---

### Post by NM5TF on 2012-12-01
I have filed a bug report for this problem...the report number
is #1085548

Thanks for your help

Tommy

---

### Post by YannBuntu on 2012-12-02
> **NM5TF said:**
> I have filed a bug report for this problem...the report number
is #1085548

it's here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1085548](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1085548)

now let's wait for answer from the Linux kernel developers.

(i removed the "If more informationis needed you can contact me at [email]xxxxxx@gilanet.com[/email]" sentence, because:
- if you write your email lke this, bots can read your email and you will be spammed
- people will ask you more information directly on the bug report, not by email
- and if really necessary they can email you via [your Launchpad account]("https://launchpad.net/~tfrost")
)

---

### Post by NM5TF on 2012-12-02
> **YannBuntu said:**
> it's here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1085548](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1085548)

now let's wait for answer from the Linux kernel developers.

(i removed the "If more informationis needed you can contact me at [email]xxxxxx@gilanet.com[/email]" sentence, because:
- if you write your email lke this, bots can read your email and you will be spammed
- people will ask you more information directly on the bug report, not by email
- and if really necessary they can email you via [your Launchpad account]("https://launchpad.net/~tfrost")
)

Merci YannBuntu!!!

---

