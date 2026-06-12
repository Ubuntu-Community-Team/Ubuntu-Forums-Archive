---
title: "Installation hang on EDGY; DG965RY"
date: 2007-01-18
forum: Installation &amp; Upgrades
---

### Post by adnansanni on 2007-01-18
I after 3days with downloading finally got EDGY.  but it doesn't load the karnel while installation. when the karnel is loading its just hang. I'm using live cd 32bit.
My pc is core2dou with DG965RY mother board and ati x800xl. and 512ram

after boot with the cd, it give me some option. if I select start or install or cheak the cd; it's goes to start load the karnel, show the ubuntu logo, and a bar going left right and after 10 seconds bar is stoped, logo is blured. it hangs forever.

I'm new user of linux. so I don't understand how can I add some parameter?
like nousb. acpi=off, noprobe. I did some way but i am not sure it went on right way.

if I select F6. then I got:
[Boot option] file=/cdrom/preseed/ubuntu.seed boat=casper initrd=/casper/initrd.gz ramdisk_size=1048576 root=/dev/ram rw quiet splash --
My quistion is where should I add the parameter? after splash -- ? or should I delete the all lines and then write? I'm confused. and what should i write? like just nousb or something more?

ok guys hope you'll give me the solution. because I really want to use ubuntu. and it's cost me lots of money to download. ](*,) 
I write the cd from ISO properly and also write with lower speed. sorry for my bad english. plz don't tell me to download alternative cd, cuase it's not possible again.

---

### Post by sloggerkhan on 2007-01-18
Why did it cost you money to download?

But here's what to try: 
hit f6 and change the boot line to 
file=/cdrom/preseed/ubuntu.seed boat=casper initrd=/casper/initrd.gz ramdisk_size=1048576 root=/dev/ram rw --

Hopefully it will boot.

Then, once it boots AND if you see a black screen instead of a desktop (which can happen on some laptops), hit ctr-alt-f2

(Once again, ONLY try this if you have a laptop which boots into a blank screen. On some laptops the wrong port is used for video out.)

You should see a command line.
type: sudo nano /etc/X11/xorg.conf

add under the device section:
Option "Monitor layout" "LVDS,CRT"
Option "Meta modes" "680x480,(max width res here),(max height res here)"

write out and exit, then hit ctrl-alt-f7 and then hit ctrl-alt-delete (may have to hit twice or hold down.)

(Once again, ONLY try this if you have a laptop which boots into a blank screen. On some laptops the wrong port is used for video out.)

---

### Post by sloggerkhan on 2007-01-18
(accidental duplicate post)

In my last post, I am assuming you have a usplash problem.

---

### Post by adnansanni on 2007-01-18
> **sloggerkhan said:**
> (accidental duplicate post)

In my last post, I am assuming you have a usplash problem.

Hey many many thanks for your reply. atleast I saw some improbe there.

In bangladesh internet download speed too slow. and 700mb download is just dreaming of most dialup user. and also have to paid lots of money to ISP.

I did as you say. boot with file=/cdrom/preseed/ubuntu.seed boat=casper initrd=/casper/initrd.gz ramdisk_size=1048576 root=/dev/ram rw --

after that lot's of code and lines goes through there, and at last its stop with these line:

BusyBox V1.1.3 (Debian 1:1.1.3-2ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands
/bin/sh: can'taccess tty; job control turned off
(initramfs)

if I type: sudo nano /etc/X11/xorg.conf here then got:

/bin/sh: sudo: not found

I also cheacked that with cd or ls command there isn't X11 directory under etc
on DG965RY motherboard, any linux doesn't sopport pata drive (cd-rom,dvd-rom).
Does it conflict with that? my hard disk sata. and monitor is LCD 17".

Thanks again for reply. I'll wait for your next solution.

---

### Post by sloggerkhan on 2007-01-18
The last part might not have been needed with an x800 (usually you need with x700).

However, the shell you end up in does not sound like the standard shell with a standard live CD file system.  Make sure that you use the default boot choice, press f6, then remove the words quiet splash. (Hopefully that's already what you did.)

Otherwise I have no idea since it sounds like your live CD booted to an unusual environment. The only thing I can think of is trying to exit the shell you wind up in and see if it continues loading.

---

### Post by adnansanni on 2007-01-19
hey thanks for your help. I'm going to download 64bit edition hope this time won't face any problem

---

### Post by kubstix on 2007-01-19
Its an issue with 965 chipset having no IDE support anymore.  Add (linux all-generic-ide pci=nommconf) to the kernel and it should install fine.

---

### Post by adnansanni on 2007-01-19
> **kubstix said:**
> Its an issue with 965 chipset having no IDE support anymore.  Add (linux all-generic-ide pci=nommconf) to the kernel and it should install fine.

hey thanks, but that isn't work also. I'm downloading the alternate 64 version. hope that will work.

---

### Post by adnansanni on 2007-01-20
> **kubstix said:**
> Its an issue with 965 chipset having no IDE support anymore.  Add (linux all-generic-ide pci=nommconf) to the kernel and it should install fine.

I added the (linux all-generic-ide pci=nommconf) with F6mode and end the line after - -. but it still asking me the cd-rom driver. now I got alternate ISO 64.

---

