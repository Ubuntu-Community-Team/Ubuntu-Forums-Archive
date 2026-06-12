---
title: "Kernel Panic after upgrade to 13.04"
date: 2013-04-26
forum: Installation &amp; Upgrades
---

### Post by renzomassobrio on 2013-04-26
Hi everyone,

Today I upgraded to 13.04 from 12.10 and the process went through completely without any problems. When I restarted my notebook, the desktop popped up, and after a few seconds it freezed in a kernel-panic black window. That happens everytime I boot without exception, just seconds (10-20) after the desktops appears.
Now I chose advanced Options on grub and booted with the previous kernel version and everything is working fine.
Any suggestion? Any useful command I can run to give you more info?

Thanks in advance for any reply and sorry if i made any mistake.

Renzo

---

### Post by pompel9 on 2013-04-26
Try to boot in safe mode (or what it's called). You can perform a check on your install there.

---

### Post by j2bv16 on 2013-04-26
You can quick tap Ctrl + Alt + F1 to enter a TTY and there log in and perform a sudo apt-get dist-upgrade and a sudo apt-get clean. Maybe something wont install correctly in the upgrade

---

### Post by renzomassobrio on 2013-04-26
@pompel9 @j2bv16:
Thanks for your answers. I had time to Ctrl + Alt + F1 and go to the Terminal, but the kernel-panic appeared as well.
I was able to boot in safe mode, but then instead of a kernel-panic I have a complete freeze after a few seconds, and no ctrl+alt+f1 or anything at all, but a cruel power off from button, worked.
Any other suggestions?
Thanks again!

---

### Post by 4lc0h0l1c on 2013-04-30
> **renzomassobrio said:**
> @pompel9 @j2bv16:
Thanks for your answers. I had time to Ctrl + Alt + F1 and go to the Terminal, but the kernel-panic appeared as well.
I was able to boot in safe mode, but then instead of a kernel-panic I have a complete freeze after a few seconds, and no ctrl+alt+f1 or anything at all, but a cruel power off from button, worked.
Any other suggestions?
Thanks again!

I am having almost the exact same problem as OP.The only difference is that all I get is a mouse cursor before the black kernel panic screen. IIRC output said "general protection fault" (wasn't that an old windows error?). I haven't yet taken the time to write down everything I see on the screen when that happens (obviously no copy/paste or screen cap :p) and I haven't tried to boot into an old kernel. Like the OP, I am also on a notebook and I think it is likely that the cause is the same, and it is not an isolated incident. Further investigation pending.

---

### Post by renzomassobrio on 2013-04-30
I tried installing 13.04 from scratch, but kernel-panic appeared during installation. Any other news about this issue?

---

### Post by sam123 on 2013-04-30
I had something similar when I upgraded to 13.04. I got a message "kernel panic - not syncing: VFS" etc while booting. Here's how I solved it:

I was able to log in using older kernel versions and then I discovered that /usr/sbin/update-initramfs was pointing to /bin/true. Which meant that there was no initramdisk for the latest kernel. I replaced the update-initramfs and things started working.

If your problem is something similar, I can post more detailed instructions.

---

### Post by LadyWindchild on 2013-04-30
I had the same problem and used the disc I bought to go back top 12.10, as it was I had to uninstall and in stall it several times in 12.10 when I switched from windows to this system cause I made a lot of stupid mistakes.
Than I went to upgrade and that was a night mare as well,after it told me to restart my computer all I got was a black screen with only the curser showing.
So now I have solved that problem I bought the disc for the new upgrade its only $5.00 and at least I know I won't mess anything up.
And I know that more than likely the installation will go through, its really worth spending the money to get the correct system installed without any problems.
If anyone out there  is interested in purchasing the disc here is the url[ http://www.osdisc.com/index.html]("http://www.osdisc.com/index.html")

---

### Post by vasiauvi on 2013-05-02
I have also the same issue: "**kernel panic - not syncing no init found. try passing init= option to kernel**" when making a **clean install**. I have also a dual-boot Windows 7 on my Dell Inspiron laptop. I use Ubuntu since 2008 but this is the first time when I get this kind of error.
So, after installing on a clean / and /home partition (ext3 --> also tried with ext4) and restarting the system I get the above error. 

Anyone managed to make it work?

---

### Post by vasiauvi on 2013-05-02
I've installed boot-repair to try and make the system work and I want to share the data gathered by this program:
paste.ubuntu.com/5625275/

Edit: I have installed Kubuntu 13.04 without any issues :|. But why Ubuntu is not working?

Update: after installing KUbuntu I've put again Ubuntu 13.04 on an USB and installed it again. Now it's working. :)

---

### Post by webarthur on 2013-05-02
[COLOR=#000000]I have the same problem... in 12.10 version its ok, but in xubuntu 13.04, I got kernel panic frequently... the openshot crashes every time, I cant edit my videos.[/COLOR]

---

