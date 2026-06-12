---
title: "unable to boot Ubuntu after upgrade, from 14.04 to 15.10 to 16.04"
date: 2016-05-13
forum: Installation &amp; Upgrades
---

### Post by chethan22 on 2016-05-13
Hi,

I upgraded my Ubuntu 14.04 to 15.10. Everything went fine but GUI refused to load on reboot. I still had access to virtual terminal, and with a hope that upgrading to 16.04 may solve the problem, I upgraded it. On 16.04, the same problem continued; no GUI. 

I still had access to virtual terminal, so I tried some commands suggested on different forums blindly without understanding them, not even bothering to note down them. I purged lightdm, nvidia, installed gdm, set gfxmode to nomodeset, etc etc.

Now, I have lost access even to virtual terminal! Not able to connect to wifi also. When I try to boot, it comes to purple screen and stops there. Pressing ctrl+alt+F2 says "A start job is running for hold until boot process finishes up (*min *s / no limit)".

 Please help!!

I am using HP Pavilion dv6 with Intel i3 processor, 2GB RAM, Intel graphic card.

---

### Post by Bucky Ball on 2016-05-13
Welcome. Upgrading a broken system rarely gives you a fixed one. Always best to have the OS humming nicely before upgrading it. Upgrading is generally not a 'fix', unless it is going to deal with specific or very new hardware. 

As you've "tried some commands suggested on different forums blindly without understanding them, not even bothering to note down them ... purged lightdm, nvidia, installed gdm, set gfxmode to nomodeset, etc etc.," perhaps a back up of valuable data and a clean install of 16.04 LTS may be in order as what you now have is affectionately known in this country as a 'dog's breakfast': e.g. a mess that may prove difficult and time-consuming to unravel, if that is possible.

It is never a good idea pumping in commands when you have no idea what they are about to do. Preferable to ask for advice first and we are happy to give it. ;)

In a virtual terminal, could you give any errors produced by these commands, please:
```

sudo apt autoremove
sudo apt clean
sudo apt autoclean
sudo apt update
sudo apt full-upgrade
```

Please use code tags when posting output here. See green link in my signature below. Thanks.

---

### Post by chethan22 on 2016-05-13
Thanks for the reply. Now I have no access to virtual terminal!

 When I try to boot normally, it comes to purple screen with Ubuntu logo and five blinking dots, and it stops there. If I press ctrl+alt+F1, a blank screen with blinking cursor is appearing.

When I try upstart mode, it also freezes and purple screen saying "loading ramdisk". If I press ctrl+alt+F1, it goes blank, and F2 to F6 say, " a start job is running for hold......". F7 says, ```
/dev/sda7 : clean, 72xxxx/25xxxxx files 74xxxx/25xxxxx blocks
```.

When I try recovery mode, and select networking, it loads some files and then sticks at ```
 grep: /etc/resolve.conf : no such file or directory 
```

---

### Post by Impavidus on 2016-05-14
Create a live disk of 16.04. Use it to create a backup of your important data (if you don't already have one) and do a clean install.

---

### Post by sense5 on 2016-08-31
I got this problem last time installing GDM3 instead of lightDM, it proved wrong, GDM3 won't work well with GNOME 3.18, and prompt [COLOR=#000000] "a start job is running for hold......" [/COLOR]when booting to GUI.

find a way to go back to VT, and reconfigure Display Manager, like '$ dpkg-reconfigure gdm', choose lightdm instead of gdm.

---

