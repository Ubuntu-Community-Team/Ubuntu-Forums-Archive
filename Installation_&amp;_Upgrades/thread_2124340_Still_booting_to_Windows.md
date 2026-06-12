---
title: "Still booting to Windows"
date: 2013-03-10
forum: Installation &amp; Upgrades
---

### Post by tmette on 2013-03-10
Hey guys, I'm sure this has come up a thousand times, but I could use a little quick help.

So last night I re-installed windows on my second HDD (500Gb) so I could play some games with friends. My first HDD had Ubuntu 12.04 on it and planned on doing a clean install of 12.10 today. I thought everything would go fine since I installed Windows first and then GRUB would allow me to choose what OS to boot to after I installed 12.10. Well I guess that's not the case.

So now I have the first HDD as this:

/root - 25Gb
/swap - 4Gb
/home - rest of the drive

2nd HDD:

Windows

I chose the first HDD as the place to install the bootloader or whatever for Ubuntu 12.10. Should I have picked the windows drive? Is there any way to fix this or do I have to re-install Ubuntu 12.10 again? :confused:

Any help would be greatly appreciated! :)

---

### Post by darkod on 2013-03-10
It seems 12.10 doesn't install grub2 correctly on the MBR sometimes. Boot the ubuntu cd/dvd in live mode, and if the root partition is /dev/sda1 as you mentioned, in terminal try:
```
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

Also don't forget to set BIOS to boot from sda. Restart and see how it goes.

---

### Post by tmette on 2013-03-10
Thanks, I'll give that a try. I should mention that when I installed Windows, I had the first HDD unplugged. So I will check the boot order in my BIOS, maybe it got switched?

EDIT: Thanks, darkod! I guess the BIOS setting of my HDD boot priority got switched since I didn't have the master drive plugged in. I just changed it back to boot to the master drive first and GRUB came up as normal. :)

---

