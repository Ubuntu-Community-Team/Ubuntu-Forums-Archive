---
title: "Missing entry in grub menu for triple boot"
date: 2022-01-18
forum: Installation &amp; Upgrades
---

### Post by wagoner2 on 2022-01-18
I installed Kubuntu on some empty partitions on a desktop with Windows and Opensuse.  I had dual boot, now I should have triple boot.  Install went well enough, but grub only lists Kubuntu and Windows.  Opensuse is not listed.  

Here is the pastebin from boot-repair  [https://paste.ubuntu.com/p/QMzKTPD4hr/](https://paste.ubuntu.com/p/QMzKTPD4hr/)

Also, I accessed the grub command line from startup, and I have some questions.  From what I remember, I typed the following commands into the grub command line and it went something like this.  The boot directory for opensuse is on (hd0,gpt7).

```
ls
(hd0,gpt1) (hd0,gpt2)  ...............   (hd0,gpt10)

ls (hd0,gpt7)/@/boot/
grub2

```

Opensuse is on sda7 and sda8.  Why does ls (hd0,gpt7)/@/boot/ only show grub2 but not initrd and vmlinuz?  I have looked at these directories with the system booted, so I know that they are there.

---

### Post by oldfred on 2022-01-18
You show UEFI Secure Boot on.
It was my understanding that grub could not boot other installs with Secure boot as it cannot confirm the security.
Did OpenSuse boot Windows, or did you always have to boot from UEFI boot menu?

Can you copy an OpenSuse boot stanza into 40_custom in Ubuntu install?
Or reset UEFI to default boot OpenSuse.
Major grub (or Windows) update  often reset boot order and make that system new default, and you just have to manage that.

I have multiple Ubuntu installs, some obsolete, and just turn off os-prober and only add the current versions I want into 40_custom. 
And grub2 is now by default turning off os-prober as there is some security issue.

Grub 2.06 turns off os-prober
[https://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-22.04-Multi-Boot-Changes](https://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-22.04-Multi-Boot-Changes)
Os-prober now turned off by default Dec 2021
[https://ubuntuforums.org/showthread.php?t=2469993](https://ubuntuforums.org/showthread.php?t=2469993)

---

### Post by wagoner2 on 2022-01-19
> **oldfred said:**
> You show UEFI Secure Boot on.
Can you copy an OpenSuse boot stanza into 40_custom in Ubuntu install?



Thank you for your reply.  Adding a boot stanza into 40_custom sounds like a good idea.  Can you explain this some more?  Where would I copy the boot stanza from?  Is it in the boot directory of my Opensuse partition?  More generally, how do I go about adding a boot option to 40_custom?   I did find the file in /etc/grub.d/

---

### Post by oldfred on 2022-01-19
You can edit 40_custom
sudo nano /etc/grub.d/40_custom
sudo update-grub

You would need to mount your OpenSuse partition and find  /boot/grub2/grub.cfg and copy boot stanza(s) into 40_custom as above.
I also have used a configfile into the other installs grub.cfg, so you can have full grub.

Using 40_custom & Custom menu
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)
Mega-thread with examples, newest at end see post 566 for some examples also.
[https://ubuntuforums.org/showthread.php?t=2076205](https://ubuntuforums.org/showthread.php?t=2076205)
Older mega-thread on custom grub menus, maybe best to read first few & then start at back.
[https://ubuntuforums.org/showthread.php?t=1542338&page=16](https://ubuntuforums.org/showthread.php?t=1542338&page=16)

configfile example to another Ubuntu, should be similar for any grub.
[https://ubuntuforums.org/showthread.php?t=2076205&page=54&p=13788092#post13788092](https://ubuntuforums.org/showthread.php?t=2076205&page=54&p=13788092#post13788092)

---

### Post by wagoner2 on 2022-01-24
I made an attempt at this.
I added an menu entry to 40_custom and then 
sudo update grub. 
Now I have a boot option for Opensuse in grub. It doesn't work however.

If I select my OpenSuse option from the grub menu, and then edit, I get the things I added to 40_custom. It looks about like this 
```

load_video
set gfxpayload=keep
insmod gzio
insmod part_gpt
insmod btrfs
set root='hd0,gpt7'
search --no-floppy --fs-uuid  --set=root 001e9d36-37dc-4b63-ab39-bdcc4fd0c66e
linuxefi /@/boot/vmlinuz-5.3.18-lp152.75-default root =UUID=001e9d36-37dc-4b63-ab39-bdcc4fd0c66e ${extra_cmdline} splash=silent resume=/dev/disk/by-uuid/2945a04b-45ea-41a7-beae-f648830831e3 mitigations=auto quiet
intirdefi     /@/boot/initrd-5.3.18-lp152.75-default

```

When I try to boot it ```
error:  /boot/vmlinuz-5.3.18-lp152.75-default file not found
```

From the grub command line, I can type ```
ls (hd0,gpt7)/@/boot/
```
but it doesn't show vmlinuz or initrd.  Is this why it returns a file not found error?

---

### Post by oldfred on 2022-01-24
Do not know btrfs and what extra commands it needs in grub. Its also uses the sub-volumes.

Line 238 also has this:

set btrfs_relative_path="yes"

Perhaps putting a label on the openSUSE sda7 partition and use a configfile from the grub you boot into the sda7 grub.
Or just specify partition like this in a boot stanza, grub in UEFI uses similar configfile to find grub in the install you are booting. :
configfile (hd0,7)/boot/grub/grub.cfg

See 6.5 on configfile details
[https://www.gnu.org/software/grub/manual/grub/grub.html#Multi_002dboot-manual-config](https://www.gnu.org/software/grub/manual/grub/grub.html#Multi_002dboot-manual-config)
Use labels and configfile to boot another install
[https://askubuntu.com/questions/344125/how-to-add-a-grub2-menu-entry-for-booting-installed-ubuntu-on-a-usb-drive/344359#344359](https://askubuntu.com/questions/344125/how-to-add-a-grub2-menu-entry-for-booting-installed-ubuntu-on-a-usb-drive/344359#344359) &
[https://www.gnu.org/software/grub/manual/grub/grub.html#Multi_002dboot-manual-config](https://www.gnu.org/software/grub/manual/grub/grub.html#Multi_002dboot-manual-config)

---

