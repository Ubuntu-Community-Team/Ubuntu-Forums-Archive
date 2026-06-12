---
title: "ubuntu not booting, showing unknown file system, grub rescue."
date: 2011-10-22
forum: Installation &amp; Upgrades
---

### Post by greathtg on 2011-10-22
i have been using windows 7 and ubuntu 10.10 for past few months. then there happened some problem with 7 and it didnt start so i started using ubuntu. then i got 11.10 and i reinstalled ubuntu on same drive which previously had 10.10. but now it's only showing unknown file system. grub rescue >. i am not even getting the option of load windows 7. tried lots of things but with no luck. is there anyone who can help me.

---

### Post by plasmafusion on 2011-10-22
i would just do a fresh install from cd/usb. 
grub will be reinstalled and it should pick up both operating systems.

---

### Post by greathtg on 2011-10-22
i have reinstalled it for some 4-5 times. it shows same thing again and again. grub rescue.

---

### Post by plasmafusion on 2011-10-22
oh.
are you installing it to the master boot record (mbr)? if so i can't think what the problem would be. it should be overwritten correctly.

---

### Post by greathtg on 2011-10-22
sorry bro but i dnt know what is mbr. i m reinstalling it on same drive where 10.10 was installed and i saw the content of that drive using live cd, it has all the files as they should be. even all the windows 7 files are also present. dont know where the problem lies.

---

### Post by plasmafusion on 2011-10-22
have a wee look [here]("http://ubuntuforums.org/showthread.php?t=24113") ?

---

### Post by greathtg on 2011-10-22
i tried what was written in that post. and now instead of grub rescue it showed grub. after which i did all the steps that were written in that post, but still its showing grub again and again. one strange thing is that everytime i reboot, i have to reinstall grub. it shows grub not installed. do you think reinstalling windows and then installing ubuntu will help ?

---

### Post by utnubuuser on 2011-10-22
If you've got a liveCD/USB, load the liveCD/USB, then download and install grub-repair and run it.

I've had similar issues several times, and grub-repair, which is for ubuntu, will take care of it.  

If you haven't got a liveCD/USB, you can still boot the kernel manually if you can get as far as a grub-rescue prompt...  I've had to do this on occasion too, and it's fairly straight-forward - I'll try to find the instructions for you...


Ok, here is one set of instructions for loading a linux from the grub-rescue prompt - note, you need to know which kernel you're running to do this.  I've got lucid on my thinkpad, so I can't help you there though someone else will know which kernel you should be trying to address ie: vmlinuz-2.6.33-32-generic etc...

at the rescue prompt: 

set root=(hd0,1)
linux (hdX,Y)/vmlinuz root=/dev/sdXY ro
# or if (hdX,Y)/vmlinuz does not exist:
linux (hdX,Y)/boot/vmlinuz-2.6.32.25-generic root=/dev/sdXY ro
# then
initrd (hdX,Y)/boot/initrd.img 
# or if (hdX,Y)/initrd.img does not exist:
initrd (hdX,Y)/boot/initrd.img-2.6.33-25-generic 
boot

(X and Y to be replaced with actual hdd and partition numbers - unless you've got more than 1 hard-disk, it'll be hd0, and you can use gparted to find out which partition is ubuntu root (/).)
also, the last time I had to use this approach, my "root" partition, which I located through gparted, was sda5, but in the above commands I had to specify sda4, or hd0,4 instead of five...(which you won't have to if it's grub2) 


and here is a simplified method from the ubuntu documentation wiki [https://help.ubuntu.com/community/Grub2#Boot_a_Specific_Kernel_Manually]("https://help.ubuntu.com/community/Grub2#Boot_a_Specific_Kernel_Manually")
which I've also used successfully

set root=(hdX,Y)	
linux /boot/vmlinuz-<your version> root=/dev/sdXY ro
initrd /boot/initrd-<your version>
boot

again, the real key here is knowing which kernel to call
"root" is the main ubuntu partition

and if you manage to get the kernel booted this way, immediately install "grub-repair" and run it to restore grub.

---

### Post by greathtg on 2011-10-22
i tried to repair it using live cd and this is what i got. i dont know what the heck is wrong with my pc. 
root@ubuntu:/# grub
The program 'grub' is currently not installed.  You can install it by typing:
apt-get install grub
You will have to enable the component called 'main'
root@ubuntu:/# apt-get install grub-pc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
grub-pc is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@ubuntu:/# grub
The program 'grub' is currently not installed.  You can install it by typing:
apt-get install grub
You will have to enable the component called 'main'
root@ubuntu:/# sudo grub
sudo: unable to resolve host ubuntu
sudo: grub: command not found
root@ubuntu:/#

---

### Post by utnubuuser on 2011-10-22
is this through the application called "grub-repair"?

Sorry... my bad... the application is called "Boot-repair", not grub-repair.

in a terminal:> sudo apt-get install boot-repair

after installation it should be in System >> Administration >> Boot Repair

---

### Post by greathtg on 2011-10-22
i did it using command line. didnt find grup repair. googled grub repair and found - 
find /root/grub/stage1 then root (hd0,5) then setup (hd0).  when i rebooted the problem persisted so i rebooted with live cd, and again grub was gone. then i tried to reinstall grub. and result were what i posted in last reply.

---

### Post by utnubuuser on 2011-10-22
and if you're going to try to boot manually from the grub rescue prompt,  one of the other posters thinks the kernel is 3.0.0-12  - I don't know if that's supposed to be 3.0.0-12-generic or not... you can try either...  and initrd will be the same number...

---

### Post by masgeeks on 2011-10-22
Generic - I just checked...

---

### Post by utnubuuser on 2011-10-22
can you install "boot-repair" using the liveDC?  As stated above, I originally posted "grub-repair", though I actually meant "boot-repair"

and in 11.10, there should be no "stage 1" since it's grub2 unless you're using legacy grub

---

### Post by greathtg on 2011-10-22
i tried to install boot-repair. but its showing this -
root@ubuntu:/# apt-get install -y boot-repair
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 boot-repair : Depends: boot-repair-common but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

any idea how to solve it ?

---

### Post by utnubuuser on 2011-10-22
ok, do you have an older version of ubuntu on a liveCD eg. lucid lynx 10.04?  if not, why not try booting the kernel manually as per instructions above.. it looks somewhat complicated, though it really isn't.

according to masgeeks, the kernel version number to insert is 3.0.0-12-generic

---

### Post by greathtg on 2011-10-22
i dont have older version. and i didnt get how to boot the kernel manually. can you give me a link to the instuctions. and isnt there any other way of installing boot-repair ?

---

### Post by utnubuuser on 2011-10-22
ok, two suggestions...

1. go to this link: [http://www.webupd8.org/2011/06/boot-repair-fix-ubuntu-boot-issues.html]("http://www.webupd8.org/2011/06/boot-repair-fix-ubuntu-boot-issues.html")
and follow the instructions...

if that doesn't work,

the instructions for booting the kernel manually are here:
[https://help.ubuntu.com/community/Grub2#Boot_a_Specific_Kernel_Manually]("https://help.ubuntu.com/community/Grub2#Boot_a_Specific_Kernel_Manually")

and keep in mind what I wrote earlier about having to specify sda4 instead of sda5 (in my case), though if I recall correctly, I was trying to recover a messed up grub after installing Fedora which has legacy grub and ubuntu has grub2

---

### Post by utnubuuser on 2011-10-22
and here is another good link on using "boot-repair"[http://www.howopensource.com/2011/08/reinstall-recover-grub-from-ubuntu-live-cd-usb/]("http://www.howopensource.com/2011/08/reinstall-recover-grub-from-ubuntu-live-cd-usb/")

---

### Post by utnubuuser on 2011-10-22
and here is another good link on using "boot-repair"
[http://www.howopensource.com/2011/08/reinstall-recover-grub-from-ubuntu-live-cd-usb/]("http://www.howopensource.com/2011/08/reinstall-recover-grub-from-ubuntu-live-cd-usb/")

---

### Post by utnubuuser on 2011-10-22
yeah, I forgot you need the yannubuntu ppa....

---

### Post by greathtg on 2011-10-22
i installed boot-repair and run it. after rebooting, i got the options of - 
select device to boot -
windows 7 from sda 1. but still i m not getting the option of booting ubuntu ? and that kernel thing is pretty scary. i mean i can try those things but they wont do anything to other drives, right ?

---

### Post by utnubuuser on 2011-10-22
Hiya greathtg

Nah, it's safe...  if you don't find the right kernel, grub will only respond with an error.

I realise it looks kinda intimidating...   though it's not. 

The best instructions are the ones from the the ubuntu documentation wiki,... very straight-forward.  ... feels great too if you manage to load a kernel manually...
then you can install boot-repair from your usual desktop and fix the grub properly.

I noticed that in this set of instructions - [http://www.howopensource.com/2011/08/reinstall-recover-grub-from-ubuntu-live-cd-usb/]("http://www.howopensource.com/2011/08/reinstall-recover-grub-from-ubuntu-live-cd-usb/") the author has a link at the bottom of the post on how to repair the MBR though I don't know it it's applicable to Windows 7 - check it out...

if you can get a grub> prompt ( you might have to press esc as the machine is booting)
enter these commands:
set root=(hdX,Y)
linux /boot/vmlinuz-3.0.0-12-generic root=/dev/sdXY ro
initrd /boot/initrd-3.0.0-12-generic
boot

substituting (hdX,Y) and sdaXY with the partition numbers of your ubuntu installation

according to one of the other forum posters, the kernel that's installed is:3.0.0-12.20

 > "Ubuntu 11.10 includes the 3.0.0-12.20 Ubuntu kernel which brings the 3.0 upstream kernel, the latest mainline release. The Ubuntu kernel is based on the linux v3.0.4 upstream stable kernel."so you might have to adjust the numbers accordingly...

though if you can get into Windows, you can check out which kernel is installed by looking at the ubuntu file-system  -  If I'm not mistaken, the place to look is /boot/grub.... - of course, you can also do the same thing with a liveCD...

---

### Post by utnubuuser on 2011-10-22
so did you get it?

---

### Post by greathtg on 2011-10-22
nah man. i tried these commands. 
set root=(hdX,Y)
linux /boot/vmlinuz-3.0.0-12-generic root=/dev/sdXY ro
initrd /boot/initrd-3.0.0-12-generic
boot

second command didnt work, showed no file found. trying to install kernel and may be after that it ll work. not sure how installing it on live cd will help .

---

### Post by Hakunka-Matata on 2011-10-22
Please download, install, & run **boot_info_script**.  Post the resulting RESULTS.txt file enclosed in [code]tags.

---

### Post by utnubuuser on 2011-10-23
chances are you listed the wrong partition...

try sdaY +-1 the partition you think is the root partition.  I've had instances where I've had to go through the commands a couple times to get it to work.

...and I suppose you looked in /boot to see which vmlinuz-x.x.x-generic and initrd.img-x.x.x-generic to load?

---

### Post by manifeb28 on 2011-10-23
> **greathtg said:**
> i installed boot-repair and run it. after rebooting, i got the options of - 
select device to boot -
windows 7 from sda 1. but still i m not getting the option of booting ubuntu ? and that kernel thing is pretty scary. i mean i can try those things but they wont do anything to other drives, right ?

Run Boot Repair go to Main option tab from Advanced option and you can find "Repair File System" select that check box and try repairing again...

---

### Post by jyothishsv on 2011-10-23
Here's the link
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by utnubuuser on 2011-10-23
I've found an even easier way to boot from the grub> prompt...

All you really need to know is the partition number of your Ubuntu root (/) partition, and the name/number of the kernel.

the partition number you can determine by booting a liveCD, starting gparted and looking at the partition table, or with the command "blkid" in a terminal.
while still in the liveSession, find the name of the kernel by looking in /boot - the kernel is "vmlinuz-x.x.x.x-generic (usually).

Now, to boot that kernel from the grub> prompt, use these three commands:> First command:
root (hd0,X)  
-- this assumes the ubuntu partition is on the first hard-drive (most systems only have 1) and the Ubuntu root / partition is partition number X and that the kernel is in the /boot folder within that partition and not in a separate /boot partition.

second command:
linux /boot/vmlinuz-X.X.X-X-generic root=/dev/sdaY 
-- again, replace X.X.X.X-generic with the name/number of the kernel and replace Y with the number of the partition where the kernel is located.

third command:
boot

That's it.  Provided you've entered the right partition numbers and name of the kernel, the machine will boot unless there's something really messed up.

These instructions are for a regular grub> prompt, (which you can access from a grub-menu by pressing c) if you're stuck at a grub rescue> prompt, the instructions are different. good instructions here:[https://help.ubuntu.com/community/Grub2#Rescue_Mode_.28.27.27grub_rescue.3E.27.27.29_Booting]("https://help.ubuntu.com/community/Grub2#Rescue_Mode_.28.27.27grub_rescue.3E.27.27.29_Booting")

Here's another useful link for booting from the grub> command:[http://sazeit.com/articles/boot-ubuntu-from-grub-prompt]("http://sazeit.com/articles/boot-ubuntu-from-grub-prompt")

---

