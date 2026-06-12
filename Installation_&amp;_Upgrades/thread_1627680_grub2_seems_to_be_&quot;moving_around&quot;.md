---
title: "grub2 seems to be &quot;moving around&quot;"
date: 2010-11-21
forum: Installation &amp; Upgrades
---

### Post by pjmlmas on 2010-11-21
Just curious

GRUB2, multiple ubuntu images on extended partition.
When update manager runs, the grub menu changes. 
i.e. Example of Boot menu
ubuntu 
other os
windows xp
ubuntu /sda7
ubuntu /sda9

perform update

ubuntu
other os
windows xp
ubuntu /sda11
ubuntu /sda9

Notice that /sda7 and /sda11 seemed to switch in the menu. What is happening with respects to GRUB2 ... is this 'chaining?'

---

### Post by oldfred on 2010-11-21
Are you alternatively booting sda7 and sda11? That would explain the difference. The current boot is the grub menu that would be updated, even it that is not the one you boot. Only if you boot the first on the list as that is the one in the MBR will the menu you see on boot be updated.

If you want to see what is installed where.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # (code tags)  in edit panel (at top of message) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] [COLOR=Red]here[/COLOR] [ /code] tags.

---

### Post by kansasnoob on 2010-11-21
I test a lot and have many *buntus/Debians:

```
lance@lance-desktop:~$ sudo update-grub
[sudo] password for lance: 
Generating grub.cfg ...
Found background image: moreblue-orbit-grub.png
Found linux image: /boot/vmlinuz-2.6.35-23-generic
Found initrd image: /boot/initrd.img-2.6.35-23-generic
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found Linux Mint 10 Julia (10) on /dev/sda10
Found Debian GNU/Linux (squeeze/sid) on /dev/sda11
Found Ubuntu 10.10 (10.10) on /dev/sda12
Found Peppermint (peppermint) on /dev/sda13
Found Ubuntu 10.10 (10.10) on /dev/sda14
Found Linux Mint Debian Edition (1) on /dev/sda15
Found Ubuntu natty (development branch) (11.04) on /dev/sda16
Found Ubuntu maverick (development branch) (10.10) on /dev/sda17
Found Ubuntu 9.10 (9.10) on /dev/sda2
Found Ubuntu 10.04.1 LTS (10.04) on /dev/sda3
Found Ubuntu 10.10 (10.10) on /dev/sdb5
done

```

Today I had a kernel update in Natty so it took over boot until I corrected it because the prior settings are somehow "remembered" by dpkg.

So, instead of just running "sudo grub-install /dev/sda" in the OS I want to have control boot I must boot into any OS with grub2 and run:

```
sudo dpkg-reconfigure grub-pc
```

The Tab key moves the cursor to OK, the space bar ticks or unticks selections. I hope that's clear :)

---

