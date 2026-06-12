---
title: "Could not download the release notes"
date: 2011-04-30
forum: Installation &amp; Upgrades
---

### Post by Pizarro on 2011-04-30
I've updated to 11.04 and system-about ubuntu seems to confirm this,but update manager tells me "new ubuntu release 11.04 is available". If I press upgrade it then tells me that "Could not download the release notes" and nothing happens. What should I do ?

---

### Post by Rubi1200 on 2011-04-30
What does this command show:

```
cat /etc/*release
```

It could be a bug?

---

### Post by Pizarro on 2011-04-30
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.10
DISTRIB_CODENAME=maverick
DISTRIB_DESCRIPTION="Ubuntu 10.10"

now I'm even more confused

---

### Post by Gillingham on 2011-04-30
I had a similar issue and after several attempts got passed that message.  I think it is simply a reflection that the servers are busy.  Certainly my download is taking ages 6 hours so far and I have a good connection speed to other sites.  I guess this is what I get for upgrading on the first Saturday of a new release :-)

---

### Post by Rubi1200 on 2011-04-30
> **Pizarro said:**
> DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.10
DISTRIB_CODENAME=maverick
DISTRIB_DESCRIPTION="Ubuntu 10.10"

now I'm even more confused
Yes me too. But I think Gillingham may be right about the servers being busy. There was a bug recently in About Ubuntu which said you had 11.04 when 10.10 was still installed.

Try the update manager again in a few hours and see what happens.

The other code to check is this:

```
uname -r
```

This should confirm which kernel you have installed.

---

### Post by Pizarro on 2011-05-01
2.6.35-29-generic

---

### Post by Pizarro on 2011-05-01
Have tried again and it seems to have worked. But now after the initial bios boot screen the monitor goes onto standby and then after some time kicks into life andthe desktop appears.Very strange.

Oh and I've just realised in the black out stage Is where grub appears and so I can't see a boot menu to get to windows !!

---

### Post by Rubi1200 on 2011-05-01
Okay, so you have made some progress; good :-)

About the next issue: from within Ubuntu open this file with the default text editor and post the contents here please:
> /etc/default/grub

Also, if you run ```
sudo update-grub
``` does that change anything with regards to seeing the GRUB menu so you can access Windows?

---

### Post by Pizarro on 2011-05-01
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

 Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"




have run sudo update-grub


Monitor reports out of frequency when it goes into standbye.

---

### Post by Pizarro on 2011-05-01
I think that grub is not installed so I am trying sudo apt-get install grub


makes no difference.

---

### Post by Rubi1200 on 2011-05-01
Take a look here for some possible solutions:
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

Also, the way to reinstall GRUB can be found here:
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

---

### Post by Pizarro on 2011-05-01
ok I've re-installed grub using Rescatux. I now can get a boot menu listing lots of kernals, memtest and grub2. No windows though. How do I get windows back in this menu ?

Looking around windows is not mentioned in boot/grub/menu.lst. I assume this is the problem, but not sure what to do.

---

