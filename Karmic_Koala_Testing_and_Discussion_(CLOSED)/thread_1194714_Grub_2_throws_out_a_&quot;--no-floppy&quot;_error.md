---
title: "Grub 2 throws out a &quot;--no-floppy&quot; error"
date: 2009-06-22
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by malachi1990 on 2009-06-22
Hi!

After updating the grub packages (22-06-09), I rebooted, and found that i was unable to boot due to an error in the grub 2 commands, specifically throwing the --no-floppy error.  I don't have a floppy drive on my laptop.

Because of this error, I am a little hesitant to reboot my computer, because I have to jump through hoops to get past this error (when i correct this error, several others have appeared, and i am unable to boot the recovery mode bc of this).

Can someone explain to me what's going on here?

Thanks!

---

### Post by autocrosser on 2009-06-23
Something new with grub 2--I edited my grub.cfg & added --no-floppy in all of my kernel lines..

Looks like:```
menuentry "Karmic 2.6.30-9-generic" {
    set root=(hd2,2)
    search --no-floppy --fs-uuid --set fc1446a5-94e9-40f8-9ebb-2442107fc13c
    linux    /boot/vmlinuz-2.6.30-9-generic root=UUID=fc1446a5-94e9-40f8-9ebb-2442107fc13c ro  quiet splash
    initrd    /boot/initrd.img-2.6.30-9-generic
```look at the "search' line......

---

### Post by malachi1990 on 2009-06-23
I get an error (when i try to edit as root, no less) that says I'm writing to a read-only disk. I only have one partition on my hard drive.

That's really odd.

---

### Post by autocrosser on 2009-06-23
Sorry--you need to work with a copy of the file--look at the grub theming thread I started....

---

### Post by binbash on 2009-06-23
at grub screen press e and remove --no-floppy then hit ctrl +x to boot.AFter then open grub.cfg and remove all --no-floppy parts.

---

### Post by douham on 2009-06-23
I to am getting these errors. I have managed to dual boot with Jaunty and XP. Grub2 through up these errors for those entries as well. A bug in the update?

---

### Post by ronacc on 2009-06-23
how I recovered from the --no-floppy  error . first like autocrosser said work with a copy of your /boot/grub/grub.cfg file . boot with a live cd , mount your karmic partition and copy your grub.cfg to somewhere to edit it . open the copy with gedit and use search and replace to replace all instances of --no-floppy (including dashes) with a single space . save the edited file under a new name ( I used grub.cfge ) . open a root nautilus  (gksudo nautilus) and copy the edited file to /boot/grub of your karmic partition , rename your original grub.cfg to something else ( I used grub.cfgo ) and then rename the grub.cfge you copied there to grub.cfg . You should now be able to boot normally .

---

### Post by zika on 2009-06-23
> **ronacc said:**
> how I recovered from the --no-floppy  error . first like autocrosser said work with a copy of your /boot/grub/grub.cfg file . boot with a live cd , mount your karmic partition and copy your grub.cfg to somewhere to edit it . open the copy with gedit and use search and replace to replace all instances of --no-floppy (including dashes) with a single space . save the edited file under a new name ( I used grub.cfge ) . open a root nautilus  (gksudo nautilus) and copy the edited file to /boot/grub of your karmic partition , rename your original grub.cfg to something else ( I used grub.cfgo ) and then rename the grub.cfge you copied there to grub.cfg . You should now be able to boot normally .I was lucky to get out of it even easier: On grub menu click on "e", navigate to --no-floppy and erase it from that line, "Ctrl-X" to boot, do "sudo nano /boot/grub/grub.cfg" in Terminal, erase all occurrences of --no-floppy, Save, Exit, and that is it. Try to reboot ... OK.

This is going to be a continuos problem until it is resolved because after each kernel install **--no-floppy** reapears in every line ... :( ... It is hard-coded somewhere and every update-grub puts it in the grub.cfg ... :(

---

### Post by plun on 2009-06-23
I also manage to fix it after installing latest kernel....

But... where is the bug-report ???

[https://launchpad.net/ubuntu/+source/grub/+bugs?field.searchtext=&orderby=-datecreated&search=Search&field.status%3Alist=NEW&field.status%3Alist=INCOMPLETE_WITH_RESPONSE&field.status%3Alist=INCOMPLETE_WITHOUT_RESPONSE&field.status%3Alist=CONFIRMED&field.status%3Alist=TRIAGED&field.status%3Alist=INPROGRESS&field.status%3Alist=FIXCOMMITTED&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package=](https://launchpad.net/ubuntu/+source/grub/+bugs?field.searchtext=&orderby=-datecreated&search=Search&field.status%3Alist=NEW&field.status%3Alist=INCOMPLETE_WITH_RESPONSE&field.status%3Alist=INCOMPLETE_WITHOUT_RESPONSE&field.status%3Alist=CONFIRMED&field.status%3Alist=TRIAGED&field.status%3Alist=INPROGRESS&field.status%3Alist=FIXCOMMITTED&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package=)


This is a "grave-bug"....:shock:

---

### Post by ronacc on 2009-06-23
submitted bug # 391044 .

---

### Post by Nullack on 2009-06-23
Good stuff ronacc.

Simple workaround - edit the grub boot command and delete the no floppy, then once in Ubuntu go sudo nano -w /boot/grub/grub.cfg and delete the no floppy business..... :)

---

### Post by plun on 2009-06-23
> **ronacc said:**
> submitted bug # 391044 .

Thanks...  I did a confirm.

If the meta-package for the new kernel comes out it will be a "mess" with
this error.

---

### Post by jerrylamos on 2009-06-23
> **binbash said:**
> at grub screen press e and remove --no-floppy then hit ctrl +x to boot.AFter then open grub.cfg and remove all --no-floppy parts.

Horrors!  Grub2 says Do Not Edit This File!  Ever!

I wouldn't have to if Grub2 got it right.  Apparently Grub2 never thought they would make a mistake....whoever put the --no-floppy code in forgot to put in the code to handle the phrase.  Oops.

Anyway, you'll need to do a 

sudo chmod 644 /boot/grub/grub.cfg

before you do the 

sudo gedit /boot/grub/grub.cfg

and replace all --no-floppy with

On this install I've had to do that twice.  I don't know when Grub2 decides to re-insert the --no-floppy phrase all over the place.  It's not in /etc/default/grub.

Cheers,  Jerry

---

### Post by zika on 2009-06-23
> **jerrylamos said:**
> Horrors!  Grub2 says Do Not Edit This File!  Ever!

I wouldn't have to if Grub2 got it right.  Apparently Grub2 never thought they would make a mistake....whoever put the --no-floppy code in forgot to put in the code to handle the phrase.  Oops.

Anyway, you'll need to do a 

sudo chmod 644 /boot/grub/grub.cfg

before you do the 

sudo gedit /boot/grub/grub.cfg

and replace all --no-floppy with

On this install I've had to do that twice.  I don't know when Grub2 decides to re-insert the --no-floppy phrase all over the place.  It's not in /etc/default/grub.

Cheers,  JerryUse Terminal editor (nano, for example) and You will not have to change the properties of grub.cfg ... (chmod). Also, use "gksudo" with GUI editor ... :)
"--no-floppy" is hard-coded somewhere deep so it re-emerges on every update-grub.

---

### Post by dinxter on 2009-06-23
Workaround for update-grub,
/usr/lib/grub/grub-mkconfig_lib, remove --no-floppy  from
line 147:    echo "search --no-floppy --fs-uuid --set ${fs_uuid}"

then updating grub should be ok until fix

---

### Post by zika on 2009-06-23
> **dinxter said:**
> Workaround for update-grub,
/usr/lib/grub/grub-mkconfig_lib, remove --no-floppy  from
line 147:    echo "search --no-floppy --fs-uuid --set ${fs_uuid}"

then updating grub should be ok until fixNice catch! Thank You very much!

---

### Post by ronacc on 2009-06-23
thanks dinxter , a simple prevention is even better than a simple fix .

---

### Post by zika on 2009-06-24
> **dinxter said:**
> Workaround for update-grub,
/usr/lib/grub/grub-mkconfig_lib, remove --no-floppy  from
line 147:    echo "search --no-floppy --fs-uuid --set ${fs_uuid}"

then updating grub should be ok until fixBeware: new upgrade of grub2 again introduces "--no-floppy" but we are prepared with Your cure ... ! Thanks again ... :)

---

### Post by Asham on 2009-06-24
I got this message too when I installed updates. At first I thought I had done something wrong when I setup dual booting, but I guess not. It was the exact same message.

I'm still not experienced enough to be using alpha versions, I guess. Beta's usually don't give that much headache but alphas, o boy.. :) But it's fun and you do learn while "living on the edge"! :D

Thanks for providing workarounds. I'll give it another go once alpha 3 is out.

---

### Post by Anzan on 2009-06-24
Thanks very much.

---

### Post by Amaranth on 2009-06-24
grub2 actually supports --no-floppy just fine, the problem is the grub2 installed in your MBR doesn't understand it. A quick grub-install should fix it.

---

### Post by zika on 2009-06-24
> **Amaranth said:**
> grub2 actually supports --no-floppy just fine, the problem is the grub2 installed in your MBR doesn't understand it. A quick grub-install should fix it.Since this is an important piece on my hard could You be more elaborate on how to to do that. I tried simple sudo grub-install with no success ...
Update: I tried again and it worked. Rebooted and even --no-floppy works. Cool! Thank You. So, we have --no-floppy:solved. Update-manager:solved. Mono:solved. Good day for Karmic testing ... :)

---

### Post by Asham on 2009-06-24
Just wanted to report back regarding my issue. I came over this on kubuntu's wiki: [https://wiki.kubuntu.org/KarmicKoala/TechnicalOverview](https://wiki.kubuntu.org/KarmicKoala/TechnicalOverview)

> Due to the conversion to GRUB2, installation will fail if you try to install Karmic Alpha 2 on a system with other OSes installed. This will be fixed for Alpha 3. As a workaround in the meantime, you can choose to use GRUB1 instead.

---

### Post by Amaranth on 2009-06-24
The command will be something like `sudo grub-install /dev/sda` but of course sda may be sdb or etc depending on the drive you have Ubuntu on.

---

### Post by zika on 2009-06-24
> **Amaranth said:**
> The command will be something like `sudo grub-install /dev/sda` but of course sda may be sdb or etc depending on the drive you have Ubuntu on.Thank You again. I've sorted that out ... I was a bit cautious because that could make my machine un-boot-able ... :) I'm not so cautious about other stuff but grub is ofe the things I rarely take care of ... knock on the wood ... :)

---

### Post by jward3010 on 2009-07-03
Did anyone have difficulty searching for this with Google (and I assume other search engines). If I typed "Karmic --no-floppy" I just got results for Karmic, as if the use of "--" from "--no-floppy" excludes the phrase from the search. I tried "--no-floppy Ubuntu" and thats when I became suspicious as I got results that looked way too much like I had just typed Ubuntu on its own, e.g. top of the list was "www.ubuntu.com". So I placed --no-floppy in apostrophes ["--no-floppy" Ubuntu] and then found something relevant. Like this for example.

---

