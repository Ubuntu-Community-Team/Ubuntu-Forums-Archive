---
title: "Windows, Ubuntu, Grub Boot issue"
date: 2010-02-15
forum: Installation &amp; Upgrades
---

### Post by pablo88 on 2010-02-15
Hi -

I need to tidy up how my PC boots up.

Current sitch:
Windows XP Pro installed to main C drive.
Ubuntu 9.04 installed to an 80Gb USB drive which draws its power from the PC.
Switching PC on brings up GRUB menu where I can choose between Ubuntu or Windows.

For whatever reason, Ubuntu 9.04 will not boot properly, only getting me as far as the login screen. When I try to type in my username, the screen does not respond - I cannot type anything into the login box.

IF the USB drive is not connected to the PC when I switch it on, then there is no way to boot into Windows. I need to change this so that I can boot into Windows without the USB Hard Drive being connected to the PC.

The GRUB thing is obviously on the USB hard drive, so I need to keep it connected to the PC just to boot it up. I'm concerned that if I take that drive and try to upgarde it to 9.10, I will mess up the boot sequence etc and then won't be able to boot up the PC into either Windows or Ubuntu.

Anyone any help on how I do this?

---

### Post by darkod on 2010-02-15
Boot ubuntu. To make sure you get the disk names correct, execute:
sudo fdisk -l

it will show your disks and partitions. Usually the int hdd would be /dev/sda and the ext hdd /dev/sdb. If it's not, use the correct device name in the commands following.

To write generic windows mbr on the int disk so it can boot windows with the ext disconnected:

sudo apt-get install lilo
sudo lilo -M /dev/sda mbr (if the int is /dev/sda, if not use appropriate)

Ignore any warnings. Now you have generic windows mbr on /dev/sda.

For installing grub1 to the MBR of the ext hdd, use this instructions (make sure you use the instructions for 9.04 for grub1, not 9.10 and grub2):
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

After that is done, you should be able to boot straight into windows without the ext hdd, and to get the grub menu if the ext hdd is connected and you select to boot from it.

---

### Post by darkod on 2010-02-15
As for upgrading 9.04 to 9.10, usually clean install is much better than upgrade. In case of a clean install, on the last screen before clicking Install, click on Advanced and make sure grub2 goes to the ext hdd MBR, that way you will avoid your current situation that the computer doesn't boot without the ext hdd.

Also, since you've come so far using 9.04, the new LTS version, 10.04, is released in April so you might consider waiting and installing 10.04 LTS as clean install wiping your 9.04.

---

### Post by pablo88 on 2010-02-15
Thank you darkod. The problem is, I cannot boot into Ubuntu as the boot sequence gets stuck at the login screen. I see the login screen and username entry box, but when I come to type, no characters appear in the box. I suppose if I could fix this then I could carry out the rest of your suggestions.

I do have a laptop also running Ubuntu. Could I connect the USB hard drive to the laptop and fix the sticking boot issue from there?  And if so, what files would I fix ?

---

### Post by darkod on 2010-02-15
Can you boot from the ubuntu cd then? The commands to restore windows mbr are the same as running from the live desktop.
Also, the commands to reinstall grub1 can be run from the live desktop, just make sure you use 9.04 cd.

---

### Post by oldfred on 2010-02-15
I had keyboard issues with my new motherboard a year ago. I had to switch from  usb to the keyboard and mouse ports. I then had to change a BIOS setting for USB keyboard to get it to work with USB as a permanent solution.

---

### Post by recluce on 2010-02-15
A few suggestions:

in your situation, I would evaluate installing a dedicated grub partition on the internal drive. At least with GRUB 0.97, this is very easy to do. A dedicated GRUB partition means that all GRUB files reside on a dedicated, small partition (100 MB is plenty) on your primary drive. Even if Linux on the USB drive is not present, GRUB will have everything to boot Windows. Instructions can be found on this extremely helpful site: 

[http://members.iinet.net.au/~herman546/p15.html#menu.lst](http://members.iinet.net.au/~herman546/p15.html#menu.lst)

Regarding the Ubuntu 9.04 login problem: are you able to use your keyboard with the 9.04 live CD? Is your keyboard USB or PS/2 connected? 

If USB: connected to the computer directly or by hub? What model/type of computer do you have?

---

