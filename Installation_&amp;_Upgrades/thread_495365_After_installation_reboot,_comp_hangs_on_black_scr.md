---
title: "After installation reboot, comp hangs on black screen"
date: 2007-07-07
forum: Installation &amp; Upgrades
---

### Post by snwbord2456 on 2007-07-07
First off I am pretty new to Ubuntu. Secondly I recently re-installed Ubuntu after trying to install a cursor scheme that cause Ubuntu to hang on a black screen with the loading cursor.

Thread here:
[http://ubuntuforums.org/showthread.php?t=495236](http://ubuntuforums.org/showthread.php?t=495236)

Because of this I decided to reinstall Ubuntu.
Now after reinstalling Ubuntu when the computer reboots from the installation I get the

Starting Up...

then it hangs on a black screen. I have an ATI card and used the text installer but I havent been able to add the drivers or anything like that because I can only get to a black screen.

---

### Post by gauravp55 on 2007-07-07
Well I don't have a video card yet I faced this problem.. U need to hit ctrl+alt+F1.. That'll show u the boot up process. Try that.Attach a copy of your menu.lst file in /boot/grub

---

### Post by snwbord2456 on 2007-07-07
I ran the virtual terminal and got the X server issue (I have an ATI X1400 card) and this is good because I had to deal with this last time, is it possible for me to just continue ahead and install the ATI drivers without attaching a copy of my menu.lst to my /boot.grub? And if I do need to attach a copy of my menu.lst to the /boot/grub what would the syntax be?

cp menu.lst /boot/grub

? I'm new to Linux so not sure about the command terminal.

edit:

actually the above wont even be possible I went past the X Server errors and its just hanging at

*Running  local boot scrips (/etc/rc.local)

What is wrong and how do I fix it?

---

### Post by gauravp55 on 2007-07-07
menu.lst is a file in /boot/grub that shows the Boot loader menu options. So I need u to post a copy of that file in this thread.

---

### Post by snwbord2456 on 2007-07-07
I'm using a second comp to use the forum, is there a certain part of the menu.lst file that I can simply type? I have to do everyhting through the terminal.

---

### Post by snwbord2456 on 2007-07-08
defauly num

default 0

timeout sec
timeout 3

hiddenmenu
hiddenmenu

Pretty Colours
color cyan/blue white/blue

password
password topsecret

examples

title Windows 95/98/NT/2000
root (hd0,0)
makeactive
chainloader +1

title Linux
root (hd0,1)
kernel /vmlinuz root=/dev/hda2 ro

Start Default Options
defualt kernel options
e.g. kopt=root=/dev/hda1 ro
        kopt_2_6_8=root=/dev/hdc1 ro
        kopt_2_6_8_2_686=root=/dev/hdc2 ro
kopt=root=UUID=a86b2426-7c84-4b5e-8bca-4ff1439f47e8 ro

Setup crashdump menu entries
e.g. crashdump=1
crashdump=0

default grub root device
e.g. groot=(hd0,0)
groot=(hd0,0)

should update-grub create alternative automagic boot options
e.g. alternative=true
       alternative=false
alternative true

should update-grub lock alterbnative automagic boot options
e.g. lockalternative=true
        lockalternative=false
lockalternative=false

additional options to use with the default boot option, but not with the alternatives
e.g. defoptions=vga=791 resume=/dev/hda5
defoptions=quiet splash

should update-grub lock old automagic boot options
e.g. lockhold=false
       lockhold=true
lockhold=false

Xen hypervisor options to use with the default Xen boot option
xenhopt=

Xen Linux kernel options to use with the default Xen boot option
xenkopt=console=tty0

altoption boot targets option
multiple altoptions lines are allowed
e.g. altoptions=(extra menu suffix) extra boot options
        altoptions=(recovery) single
altoptions=(recover mode) single

controls how many kernels should be put into the menu.lst
only counts the first occurence of a kernel, not the alternative kernel options
e.g. howmany=all
       howmany=7
howmany=all

should update-grub create memtest86 boot option
e.g. memtest86=true
       memtest86=false
memtest86=true

should update-grub adjust the value of the default booted system can be true or false
updatedefaultentry=false

End Default options

title Ubuntu, kernel 2.6.20-15-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=a86b2426-7c84-4b5e-8bca-4ff1439f47e8 ro quiet splash
initrd /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root (hd0,0)
kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=a86b2426-7c84-4b5e-8bca-4ff1439447e8 ro single
initrd /boot/initrd.img-2.6.20-15-generic

title Ubuntu, memtest86+
root (hd0,0)
kernel /boot/memtest86+.bin
quiet

---

### Post by snwbord2456 on 2007-07-08
I tried to do apt-get update (without the sudo) and I got

E: Could not open lock file /var/lib/apt/lists/lock - open (13 permission denied)
E: Unable to lock the list directory

Is this a root conflict or shoudl I do something else with the menu.lst, I saw a couple things that sould should update next to them, should I do that or should I just install the ATI drivers like I did last time?

---

### Post by snwbord2456 on 2007-07-08
I installed the ATI drivers and things seem to be working, sorry for the useless post i guess.

---

