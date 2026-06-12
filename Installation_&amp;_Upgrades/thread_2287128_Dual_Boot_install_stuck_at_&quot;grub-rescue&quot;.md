---
title: "Dual Boot install stuck at &quot;grub-rescue&quot;"
date: 2015-07-17
forum: Installation &amp; Upgrades
---

### Post by zekesax on 2015-07-17
I'm performing a dual boot install for a friend on his Toshiba Satellite R15-S829.
I've installed dual boot Ubuntu / Windows 7 with great success.  I've done many full (wipe hard drive) installations of Lubuntu with great success.  I'm trying to help a friend who doesn't want to lose Windows XP.  I told him, "No Problem, we'll do a dual boot installation."  Problem!  

I've searched around the forums and tried some grub code without any success.  Then, In Ubuntu Community, I came across "Boot Repair" ([https://help.ubuntu.com/community/Boot-Repair#Advanced_options](https://help.ubuntu.com/community/Boot-Repair#Advanced_options)).  I tried this and still ended up at "grub-rescue."

Here is the report compiled by "Boot-Repair":

[http://paste.ubuntu.com/11891322/](http://paste.ubuntu.com/11891322/)

(Is it better to paste the entire summary in a forum?)

I would really like to do a dual boot installation for him.  While I am a noob, he has no experience with Ubuntu/Lubuntu except for what he has seen on my computers.  He was impressed enough to want to give it a try.  

If I'll need to point specifically to a partition, then I'm going to need my hand held. (Sorry)  Hell, I'm going to need my hand held any way.  

Thanks in advance,
Zeke

---

### Post by sudodus on 2015-07-17
I cannot see any error in the boot-info summary that you uploaded. There might still be some error, that someone else can discover.

The computer boots and I think something else is wrong.

1. The iso file and boot media - have you used this same CD/DVD disk to install Lubuntu before? If not, please check the md5sum of the iso file and run the check option at boot.

2. Drivers for old hardware:

Please specify your friend's computer

Brand name and model (known already: Toshiba Satellite R15-S829, but the detailed specs might vary)
+ CPU
+ RAM (size)
+ graphics chip/card
+ wifi chip/card

The long time support version of Lubuntu 14.04.1 LTS with the trusty kernel is better debugged and polished, and more likely to have drivers for old computers than version 15.04. So I suggest that you download Lubuntu 14.04.1 LTS (32-bit alias i386) and check it with md5sum and make a boot CD/DVD disk or USB pendrive.

3. If still no success, maybe a community re-spin based on Ubuntu 12.04 LTS might work, LXLE, Bento, Bodhi.

See also this link: [Old hardware brought back to life](http://ubuntuforums.org/showthread.php?t=2130640)

---

### Post by tokyobadger on 2015-07-17
As stated more hardware specs would be good.
On the opensuse HCL list [someone has this model working](https://en.opensuse.org/HCL:Toshiba_laptops#Satellite_R) but some features were not fully functional, so it looks like it can be done.

Since this is quite old hardware (I'm looking at the CPU, GPU and max RAM specs) it may not be a great experience with the latest Ubuntu, but as sudodus says there are other options. Equally, not knowing how well supported out of the box this hardware is today, you may benefit from the discussion on this model in [this thread](http://ubuntuforums.org/showthread.php?t=1078134) <-- note it is an old thread

You may want to try the install again and make sure that grub is installed to /dev/sda - I noted a couple of messages in the grub-repair output that suggested you might have put grub in the wrong place.

---

### Post by oldfred on 2015-07-17
Can you manually boot from grub rescue?
       Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)
HOWTO: Boot & Install Ubuntu from the Grub Rescue Prompt 
[URL="http://ubuntuforums.org/showthread.php?t=1599293"]http://ubuntuforums.org/showthread.php?t=1599293

[/URL]
 grub rescue:
ls # Do you see (hd0), (hd0,6) ? If so, run the next command. Change if not hd0,6.
configfile (hd0,6)/boot/grub/grub.cfg

OR:

 set prefix=(hd0,6)/boot/grub
set root=(hd0,6)
linux (hd0,6)/vmlinuz root=/dev/sda6 ro
initrd (hd0,6)/initrd.img
boot

 

There are old BIOS that will not boot from any file beyond 137GB on drive. That might be your issue, but it was really old BIOS that that applied.
Since your Windows only uses 15GB of sda1, you can shrink it. Be sure to immediately reboot Windows & run chkdsk.
Then use Something Else to install Widnows and create a separate / (root) of 25GB so that is fully inside the first 100GB or so of drive, and use rest of drive as /home and or another NTFS partition for shared data.

Ubuntu examples, Lubuntu will look slightly different, but process is same.

 Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[URL="https://help.ubuntu.com/community/Grub2/Installing"]https://help.ubuntu.com/community/Grub2/Installing
[/URL]
        Lots of detail, screenshots and essential info.14.04  Something Else example
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

---

