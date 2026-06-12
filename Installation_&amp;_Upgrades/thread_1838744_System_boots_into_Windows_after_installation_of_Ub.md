---
title: "System boots into Windows after installation of Ubuntu 11.04"
date: 2011-09-04
forum: Installation &amp; Upgrades
---

### Post by aspz on 2011-09-04
Hello, 

I have a system with Windows 7 installed on partition sda1. I installed Ubuntu 11.04 from a USB disk onto partition sda3 which seemed to work ok until the system rebooted. At this point, the system booted straight into Windows. No boot menu was displayed.

What tool can I use to override the Windows boot loader with the Ubuntu boot loader? I've tried Yann-Buntu's Boot-Repair image to repair GRUB, and then the MBR but neither option has had any apparent effect.

I'm out of ideas. What should I try next?

---

### Post by Basher101 on 2011-09-04
I think grub never got installed to your hard drive. Or you did install it but on the ***_Partition _***instead of the MBR. Just reinstall and make SURE that it looks like on the screenshot ***_/dev/sda_*** not /dev/sda***_1_*** or 2...no number must be there just /dev/sda.

---

### Post by aspz on 2011-09-04
Is there a way I can re-install GRUB from the live cd, or do I have to re-install Ubuntu from scratch? It would be good to know just so I can test your solution more quickly.

---

### Post by recluce on 2011-09-04
> **aspz said:**
> Is there a way I can re-install GRUB from the live cd, or do I have to re-install Ubuntu from scratch? It would be good to know just so I can test your solution more quickly.

Herman's GRUB pages contain everything you ever wanted to know about GRUB. For your specific problem (install GRUB from Live CD), go here:

[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Re-install_GRUB_from_Live_CD](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Re-install_GRUB_from_Live_CD)

---

### Post by aspz on 2011-09-04
I followed the instructions on that section of the grub documentation but it failed with this error:

```

ubuntu@ubuntu:~$ ls /media/
c1051ddd-a293-44da-af44-1a63ed712e2f  cdrom
ubuntu@ubuntu:~$ sudo grub-setup -d /media/c1051ddd-a293-44da-af44-1a63ed712e2f/boot/grub /dev/sda
grub-setup: error: cannot stat /media/c1051ddd-a293-44da-af44-1a63ed712e2f/boot/grub/boot.img.

```Googling that error, it appears I've run into this bug in grub-setup: [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/630904](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/630904) The comments on that bug say that I should not be using grub-setup but rather grub-install.

Unfortunately, the documentation for grub-install does not describe how and when you should use it. Can anyone recommend either how get around the error above, or how to use grub-install (or another command) to set up GRUB?

Thanks!

Edit: Well I tried grub-install but I get a similar kind of error:

```

ubuntu@ubuntu:~$ sudo grub-install /dev/sda3
/usr/sbin/grub-probe: error: cannot stat `aufs'.

```

---

### Post by drs305 on 2011-09-04
If you run the boot info script and post the contents of RESULTS.txt we will know what is happening to your system. Boot into the LiveCD, then download/extract/run the script from the following location:
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

RESULTS.txt contains lots of information about your installation and boot setup that should help us sort things out.

In general, from the live cd, you install Grub2 by mounting your Ubuntu partition and then running the following command. sdXY is the partition on which Ubuntu is installed (sda5, sdb1, etc). sdX is the drive (sda, sdb, etc)
```

sudo mount /dev/sdXY /mnt
sudo grub-install --root-directory=/mnt /dev/sdX
```

**EDIT:** Seeing your additional comments, it would be best to just post the RESULTS.txt and hopefully we can sort things out after seeing how you installed Ubuntu.

---

### Post by aspz on 2011-09-04
drs305, I did exactly as you have said, grub-install claimed that it executed successfully. I restarted and find myself back in the land of Windows.

I will try running the boot info script tomorrow. It's getting late now...

---

### Post by YannBuntu on 2011-09-05
> **aspz said:**
> I've tried Yann-Buntu's Boot-Repair image to repair GRUB, and then the MBR but neither option has had any apparent effect

Hello,
please can you indicate the resulting URL ? (it will contain the Boot-Info-Script asked by drs305, and some additional data that may help).

---

### Post by aspz on 2011-09-05
Hi YannBuntu, I wrote down the pastebin urls from the two times that I tried the tool but unfortunately, pastebin claims that they are invalid. I'll post them up here on this thread when I get back home tonight.

---

### Post by YannBuntu on 2011-09-05
yes, please.

Also please connect internet and try again the "Recommended repair" of Boot-Repair, and indicate the new URL.
If the new URL is again invalid, please check into your /tmp/clean/log/ folder, and indicate us the content of the 2011-09-13xxxxxlog.paste file (it's what should have appeared in the URL)

(I also sometimes had invalid URLs, I think it depends on the pastebin provider, i will try to choose a more reliable one).

---

### Post by aspz on 2011-09-05
Here are the pastebin links I got after running the Boot-Repair iso:

[http://pastebin.com/7Wcp4Yhz](http://pastebin.com/7Wcp4Yhz)
[http://pastebin.com/ESWU2wjM](http://pastebin.com/ESWU2wjM)

As you can see they don't appear to be valid (and I'm pretty sure I copied them down correctly).

Attached is the RESULTS.txt from running the boot_info_script.sh

(fyi, sda2 is an old partition containing programs and data from an old installation of Windows XP. The only two OSes are actually Windows 7 on sda1 and Ubuntu on sda3).

---

### Post by aspz on 2011-09-05
Good news everyone!

Before running the boot script, I re-ran the grub-install script, this time with the --root-directory set. This appears to have correctly configured the MBR to read from my Ubuntu install - I'm now posting this from my brand new 11.04 install.

That means that the RESULTS.txt I posted earlier should actually describe a healthy boot setup. I wish I had run it before so I could see exactly what was fixed. Oh well.

---

### Post by YannBuntu on 2011-09-05
This confirms what I thought: the [http://pastebin.com](http://pastebin.com) sometimes gives broken links, so I will solve this by using paste.debian or paste.ubuntu instead. Thanks for your feedback !

---

