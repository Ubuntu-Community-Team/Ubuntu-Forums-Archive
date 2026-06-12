---
title: "how to provide package (grub-pc) options to apt install ?"
date: 2017-06-05
forum: Installation &amp; Upgrades
---

### Post by sfchun on 2017-06-05
Hello 

Using ubuntu Ubuntu-16.04LTS (64bit)

I'm writing a bash script that will help me to rebuild and configure from scratch a physical machine (with root on zfs).
One step is to install grub-pc package that prompts for information.
I've seen on [https://askubuntu.com/questions/146921/how-do-i-apt-get-y-dist-upgrade-without-a-grub-config-prompt](https://askubuntu.com/questions/146921/how-do-i-apt-get-y-dist-upgrade-without-a-grub-config-prompt)  ,
providing additional option : **[COLOR=#111111][FONT=Consolas]-o Dpkg::Options::="--force-confdef"[/FONT][/COLOR]**  to **apt** is possible.

My questions :
- How can I know which option(s) a packages offer ?
- Regarding grub-pc , I would like to perform something like this :
**[COLOR=#111111][FONT=Consolas]# apt install -y -o Dpkg::Options::="--device /dev/nvme0n1[/FONT][/COLOR][COLOR=#111111][FONT=Consolas]" [/FONT][/COLOR][COLOR=#111111][FONT=Consolas]-o Dpkg::Options::="--continue yes[/FONT][/COLOR][COLOR=#111111][FONT=Consolas]" grub-pc[/FONT][/COLOR]** 

if a solution exists with dpkg, I take it :)

the purpose is to run the installation script completly without any interaction.


Thanks a lot for your help.
Regards

---

