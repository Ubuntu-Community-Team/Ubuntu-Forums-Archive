---
title: "What does this mean? initramfs (problem?), wants to boot from an old swap partition"
date: 2021-07-21
forum: Installation &amp; Upgrades
---

### Post by slaytanicprion on 2021-07-21
See for yourself, I never saw this before. I forgot to get rid of an old swap partition on /sda/5 . Ubuntu Mate is installed on sdb. This makes me afraid to reboot. In 10 years of linux usage where I understand what I'm doing, for the most part, I can't figure out this update process and there doesn't seem to be much about it. Check it out, it will be simpler this way : (btw, I see it is giving me a way to opt out, but I can't type or do anything, it's configuring stuff when this shows up. Please help, I was about to install Wine and that demands a reboot on my side, since I gotta install the whole 32 bit library stuff.

[ATTACH=CONFIG]288842[/ATTACH]

---

### Post by slaytanicprion on 2021-07-21
I just read how it may be corrected by creating /etc/initramfs-tools/conf.d/resume and putting RESUME=none in there. I have mint 17.3 which is very past its time on sda1 also. Should I run OS-Uninstaller? I used it before and it works fine, but a reboot only shows you the result, can't understand why the system insists on having my oldest smallest ridiculous first generation WD Black Caviar SATA at 200gb that I keep in there just because it will not die be sda, in my system settings it's listed third out of 3 in boot order when it comes to the internal drives section, unlike a couple WD Reds in between when I bought it and now. I got all of it backed up anyway (the whole partition), so whatever data I might want to keep on sda1, I already saved it all. 

This doesn't look good and I just after a couple weeks got everything the way I like them, this out-there never seen before kernel update error confuses me, I think it might not be a good idea to go into gparted and delete that swap partition right now. OS-Uninstaller and then Boot-Repair should do it, Boot-Repair always fixed everything, thats why I keep a dvd since years with Boot-Repair OS, which is just Lubuntu with a bunch of "IT" tools coming with it, I'd rather be able to repair and prevent this error before rebooting at all though. Gah, not starting the day too well

---

### Post by slickymaster on 2021-07-21
Please do not post large images into your posts. Many of our users have slow internet connections and data limits. Large images can take a long time to load -- and may even cost a user extra money. Use the attachment functionality provided by the paperclip button above the text entry box.

---

### Post by Dennis N on 2021-07-21
> What does this mean? initramfs (problem?)
Edit the file **/etc/initramfs-tools/conf.d/resume** and set **resume** to equal the UUID of the new swap partition. Then run:
```
sudo update-initramfs -u
```

---

### Post by slaytanicprion on 2021-07-21
yes, I saw also putting the line RESUME=NONE and also 

```
user@desktop:~$ cat /etc/initramfs-tools/conf.d/resume
RESUME=UUID=1053a199-0b8f-44ae-9356-c04f5864b138
  /etc/default/grub also could contain option for resume from swap partition:
  GRUB_CMDLINE_LINUX_DEFAULT="quiet splash resume=/dev/sda5"

sudo update-grub
sudo update-initramfs -c -k $(uname -r)
```

What if I just remove Linux Mint 17.3 from sda1 and the swap (sda5) by using OS-Uninstaller and then run boot-repair? Do I have to keep things this way? I would hope not, I don't even remember my password for LM 17.3, I just left it there because I got plenty of 200gb's at faster speed than 3gb/sec SATA, never bothered removing mint, but it looks like it might be the smart thing to do. Maybe I have to do what you're saying (its similar to what I've pasted here that I found elsewhere) before doing that, looking like I won't be able to boot if the swap on another drive is gone (I didn't create a swap for 20.04 as it is not needed, had no idea it would start using the swap from another drive).

Why is initramfs/ (grub too?) being installed there, I can speed boot directly from any drive at post, but I can't select a partition to do so. 

Thanks a lot, a bit more guidance would be appreciated. Because I think the first "help" I found just told me to create the resume file and put those values in, which ignore the kernel updates...I hope not? If normal booting fails, I wonder what will happen if I speed boot directly on the drive 20.04 is on.

P.S. Sorry mods, I didn't intend on making a duplicate thread, I pressed the back button to edit, but I guess it brought me back to the post creation page and I didn't notice. Old enough to know better than doublepost.

---

### Post by grahammechanical on 2021-07-21
I see the same message and I just ignore it. Rebooting is not a problem. the loading of the OS takes much longer as the kernel tries to find the swap partition and does this for a while until it gives up.

In my case this happened when I installed a version of Debian and I think it gave a new UUID to the swap partition on that hard disk. I have tried setting the resume variable to the new UUID and updating initramfs but the problem remains. So, I just get on with life. It only affects the installs put in before Debian was installed. One day I will fix this by doing clean installs.

Regards

---

