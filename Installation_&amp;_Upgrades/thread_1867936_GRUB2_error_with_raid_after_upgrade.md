---
title: "GRUB2 error with raid after upgrade"
date: 2011-10-23
forum: Installation &amp; Upgrades
---

### Post by froghead on 2011-10-23
Hi 

I posted this problem on the "Absolute Begginer Talk", 
[http://ubuntuforums.org/showthread.php?t=1867082](http://ubuntuforums.org/showthread.php?t=1867082),
which was probably the incorrect forum to get help on an upgrade.

The problem is I am running 10.10 server edition, at least I was until yesterday, which is when I attempted to upgrade to 11.04.
I have software raid configured.
I got the following error after the restrart:

[FONT=Courier New]"*error: symbol not found: 'grub_env_export'*"[/FONT]

As per the suggestion in the following thread:
[http://ubuntuforums.org/showthread.php?t=1729949](http://ubuntuforums.org/showthread.php?t=1729949)

I booted with the Live CD and then ran
[FONT=Courier New]$sudo msadm --assemble --scan
$sudo palimpsest[/FONT]

I was able to start the raid array and also initiate a "check and repair array", which ran forever, but completed sucessfully.

[FONT=Arial]I then mounted the array:[/FONT]
[FONT=Courier New]sudo mount /dev/md0 /mnt

[FONT=Arial]and then installed GRUB 2.[/FONT]
sudo apt-get install grub-pc

[FONT=Arial]and got the following message[/FONT][I]

"Note: It is possible to install GRUB to partition boot records as well, and 
some appropriate partitions are offered here. However, this forces GRUB to 
use the blocklist mechanism, which makes it less reliable, and therefore is not
recommended.

GRUB install devices:
 [ ] /dev/sda (2320072 MB, MAXTOR_STM3320613AS]
[/I][/FONT][I][FONT=Courier New] [ ] /dev/sdb (2320072 MB, MAXTOR_STM3320613AS][/FONT][FONT=Courier New]
[ ] /dev/sdc (2320072 MB, MAXTOR_STM3320613AS]
[/FONT][FONT=Courier New] [ ] /dev/sdd (2320072 MB, MAXTOR_STM3320613AS][/FONT] "[/I]

[FONT=Arial][SIZE=2]After selecting all 4, I get the following error:[/SIZE][/FONT]

[I][FONT=Courier New]"GRUB[/FONT] failed to install to the following devices:
/dev/sda /dev/sdb /dev/sdc /dev/sdd
Do you want to continue anyway ?
GRUB installation failed. Continue"
[/I][FONT=Courier New]
[FONT=Arial]to which I answered  "No", 

Any suggestions on how I can proceed further as I wish to restore my PC.
Any help would be much appreciated.

[/FONT][/FONT]

---

