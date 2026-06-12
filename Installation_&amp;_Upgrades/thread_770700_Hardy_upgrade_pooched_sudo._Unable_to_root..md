---
title: "Hardy upgrade pooched sudo. Unable to root."
date: 2008-04-27
forum: Installation &amp; Upgrades
---

### Post by mikebravo on 2008-04-27
Upgrade from Gutsy to Hardy looked good until I tried to run UpdateManager. It hung immediately. Search on these forums said problem was in hosts file. Sure enough, cat /etc/hosts shows second line reads 127.0.1.1 mike-linux.workgroup instead of just 127.0.1.1 mike-linux.  Big problem is that this noob does not know how to edit that file when he cannot sudo and gedit. Can someone please give me How-To on how to edit files as root whether Ubuntu likes it or not.  Must have noob level details, not just generalities.    Thanks

---

### Post by Antaresje on 2008-04-27
Boot from a live-cd, and open a terminal. 'sudo mount /dev/xxx /mnt', where xxx is your ubuntu root partition (sda1 or something). If you don't know which it is, then first boot your regular ubuntu and look at the output of 'df -h'. The partition listed as mounted on / is your root partition.

Then do 'sudo vi /mnt/etc/hosts'. Or replace 'vi' with whatever editor you prefer.

---

### Post by ansicplusplus on 2008-04-27
Hy,
I solved this using the network-manager-applet. The last of the tabs shows a list which resembles the contents of the hosts file. Before editing the entry for 127.0.1.1 make sure you remove the domain 'workgroup' on the second tab right under your computers name. It seems that it is automatically appended to your computers name. I am not sure, why the upgrade applications or sudo stumble over this.

Yours, ansicplusplus

---

### Post by wickerman1413 on 2008-04-27
Or reboot into recovery mode, drop to shell, vi /etc/hosts, remove the domain name from the line beginning 127.0.0.1 that has your machine name, save, exit and reboot.

---

### Post by IT-Joker on 2008-04-27
I had the same problem ( [http://ubuntuforums.org/showthread.php?t=769338](http://ubuntuforums.org/showthread.php?t=769338) )

You can reboot to recovery and then edit the file from command line.
Be warned that working with vi is more like a torture if you aren't experienced with it ;)

I was told about nano in the thread linked above. It looks much easier to use for beginners. So you should be able to do it with:
nano /etc/hosts

---

### Post by mikebravo on 2008-04-28
> **Antaresje said:**
> Boot from a live-cd, and open a terminal. 'sudo mount /dev/xxx /mnt', where xxx is your ubuntu root partition (sda1 or something). If you don't know which it is, then first boot your regular ubuntu and look at the output of 'df -h'. The partition listed as mounted on / is your root partition.

Then do 'sudo vi /mnt/etc/hosts'. Or replace 'vi' with whatever editor you prefer.
Turns out that post #3 was the easy way to go. I tried it your way (df -h says /dev/sda2 19 gig is mounted on / ) but sudo mount /dev/sda2/mnt returns mount: can't find /dev/sda2 in /etc/fstab or /etc/mtab   and I do not know enough to understand what it is saying.     Feel free to educate me.

---

### Post by bdoe on 2008-04-28
Typing gksudo gedit /etc/hosts worked for me, and saved me from having to muck about in VIM or boot off the live CD.

---

### Post by graphius on 2008-04-28
Wow, Thanks, gksudo worked.

kind of sucks that Hardy broke that though...

---

