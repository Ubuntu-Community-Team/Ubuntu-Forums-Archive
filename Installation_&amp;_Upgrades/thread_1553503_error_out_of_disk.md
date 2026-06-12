---
title: "error: out of disk"
date: 2010-08-15
forum: Installation &amp; Upgrades
---

### Post by fourlincoln10 on 2010-08-15
I had Ubuntu 9.something on an old Dell 1u server. I decided to upgrade it because it started stopping during the boot process and making me choose an older kernel. I don't remember the specific error message.

I upgraded to 10.04 and chose to reformat the partitions. Installation went okay, but when I rebooted I got the grub2 recovery prompt. I read in another post that this could be caused by the old partitions not being deleted, so I rebooted with my installation cd, chose manual partition, deleted the old partitions and installed again. 

When I rebooted I received the regular grub2 menu. I played around with manually entering the grub commands as suggested [here]("https://help.ubuntu.com/community/Grub2#Editing%20Menus%20During%20Boot") and finally got Ubuntu to boot.

Grub2 didn't save my changes so I ran sudo apt update-grub and then rebooted. Now it boots, but it throws an error that says error: out of disk'. It shows that error for a few seconds and then finishes booting to the shell and I'm able to login. Not sure what the error message means since it boots to the shell okay. I'm using the server version of 10.04. Everything seems to be working once I log in. Any advice is appreciated.

Thanks,

Troy

---

### Post by oldfred on 2010-08-15
This may be the problem. But I thought is was for versions before 10.04.

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Out_Of_Disk](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Out_Of_Disk)

---

### Post by fourlincoln10 on 2010-08-15
Thank you for your response oldfred. I opened up 10_linux but I can't find the line:

if [ -n \${have_grubenv} ]; then save_env recordfail; fi

The closest thing I can find starts on line 74. It says:

printf "menuentry '${title}' ${class} {\n" "${os}" "${version}"
cat << eof
     recordfail
EOF
     save_default_entry | sed -e "s/^/\t/"


I wonder if I'm having a hard drive problem. The strange thing is Ubuntu shows that error message for a few seconds, but then boots normally.

---

### Post by oldfred on 2010-08-15
They must have updated it, so the instructions are for an older version.

Do you have an entry in fstab that is not valid now? You can check quickly with 

mount -a

If it just comes back to terminal it is ok, if not you get messages.

---

### Post by fourlincoln10 on 2010-08-16
sudo mount -a just returns me to the command prompt. I tried a couple more things from other posts I read:

reinstalling grub:
sudo grub-install --root-directory=/mnt/ /dev/sda
It said the installation completed with no errors
I rebooted and got the grub prompt.

Typing the following into the grub prompt gets my system to boot:

set root=(hd0,1)
linux /vmlinuz root=/dev/sda1
initrd /initrd.img
boot

Things seem to work fine until I reboot. I get the grub prompt again and have to manually type in the commands. Running sudo update-grub got my system to boot without my having to manually type in the commands for a while, but I got the error: out of disk message for a few seconds before the system finished booting.

I'm going to try installing on another hard drive to see if that works.
 

Thanks for your help,

Troy

---

### Post by tom.coyne on 2010-08-30
Hi,
Did you manage to find a solution to your problem? I am having exactly the same problem. Whilst it isn't causing any real problems, I'm just worried that there is a bigger problem in the background.

Thanks,
Tom

---

### Post by fourlincoln10 on 2010-08-30
I gave up and used another hard drive. It worked fine with the other drive. The drive that was giving me problems used to be part of a two disk raid configuration. The server has a raid card in it that didn't work with Ubuntu so I was trying to install w/o it. Just speculating that was part of the problem though. I don't really know. 

Best,

Troy

---

### Post by oldfred on 2010-08-30
RAID is not too common on desktops and that could have been the problem. Data is saved on the drive that interfers.

Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
Also check BIOS for raid settings
More discussion:
[http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738](http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738)

---

