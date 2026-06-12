---
title: "Startup problem"
date: 2010-08-03
forum: Installation &amp; Upgrades
---

### Post by Noorani on 2010-08-03
Hi, 
My ubuntu 10.04 was working perfectly until today when I installed updates. After downloading and installing the regular updates I was prompted to restart my computer (I think this was because the updates were around 82 mb). Anyway after installing updates I clicked on 'restart now' on the prompt. The computer restarted well until the login screen where I typed my password. After clicking on Login I waited for the desktop to appear but it did not do so. All I could see was my wallpaper(the login screen background is the same as wallpaper) and the cursor There were no panels and I could not right click. So now I can't use my computer. Could anyone please help.
Thanks in advance

---

### Post by Mark Phelps on 2010-08-03
You have a couple of different options ... both of which require seeing the GRUB menu.  To do this, you have to press and hold the Shift key after starting your machine.

Once into the GRUB menu, if you did a kernel update, you can select one of the older kernels to see if that starts OK without the problems.

IF you did not do a kernel update, you should select the Recovery option -- generally right below a normal kernel selection.

---

### Post by Noorani on 2010-08-04
I don't remember whether there was a kernel update. First, I tried using the older kernel but I got the same problem. So, after that I used the recovery mode of the latest kernel. When using this method I got a blue screen with a grey recovery menu with the options:
resume     resume normal boot
clean      try to make free space
dpkg       repair broken packages
failsafeX  run in failsafe graphic mode
grub       update grub bootloader
netroot    drop to root shell prompt with networking

According to me the second, fifth and sixth options are not what Need to use.
When I used the first option I got a command interface to use(Ctrl+Alt+F7 gave me some some strange screen eith white writings on it)
The failsafeX option did not work as it gave me the original problem again
When using the dpkg option I got so many lines of:
**W: Failed to fetch...URL...**
and then finally I got the line:
**W: Some index files failed to download, they have been ignored, or old ones used instead**

So I don't know what to do now
Please help

---

