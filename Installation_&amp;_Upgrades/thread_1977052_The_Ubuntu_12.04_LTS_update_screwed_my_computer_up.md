---
title: "The Ubuntu 12.04 LTS update screwed my computer up"
date: 2012-05-09
forum: Installation &amp; Upgrades
---

### Post by kensclark15 on 2012-05-09
Well, I just finished downloading 12 GB of a tv show and the update manager said there was a new Ubuntu version out. I said OK to downloading it and it installed fine. Now when I start it up, it goes to the desktop but there is no user bar or anything, just the desktop. Something asks me for my password, I enter it but it doesn't even show up in the box then it said that Compiz failed. I used to use GNOME but I am getting this error with the plain old Ubuntu desktop too. Since I can't access anything I can't try sudo apt-get update/upgrade or anything. My computer was acting fine until this. If I have to do a fresh install... Well, I'll be pissed because I have to download EVERYTHING I had again. Could you please help me? Also, I can access the file system folder. Also, There is no close, minimize, or maximize button on any window and when I right click stuff it doesn't show the little option menu thing.

---

### Post by kensclark15 on 2012-05-09
I was also using the 11.whatever version of Ubuntu before this.

---

### Post by kensclark15 on 2012-05-09
Any ideas? I really don't want to lose everything!:mad:

---

### Post by kensclark15 on 2012-05-09
Here is a picture: [IMG]http://img513.imageshack.us/img513/3083/p4090149.jpg[/IMG] As you can see, there are no buttons on anything.

---

### Post by darkod on 2012-05-09
Hold on. I know you are upset but 35mins is not enough someone to help you.

You were running 11.whatever? You don't even know the version? I guess it was 11.10 because only that would allow you to upgrade directly to 12.04.

If you select the recovery mode entry in the boot menu, does it boot to command prompt? If a menu shows, select something like Drop to root shell.

If it does boot recovery mode, there are few commands you can run.

---

### Post by kensclark15 on 2012-05-09
> **darkod said:**
> Hold on. I know you are upset but 35mins is not enough someone to help you.

You were running 11.whatever? You don't even know the version? I guess it was 11.10 because only that would allow you to upgrade directly to 12.04.

If you select the recovery mode entry in the boot menu, does it boot to command prompt? If a menu shows, select something like Drop to root shell.

If it does boot recovery mode, there are few commands you can run.
I can't even get into GRUB, it says wrong resolution for a long time then it goes straight to the weird looking desktop.

---

### Post by darkod on 2012-05-09
Hmmm, the grub boot menu should be before that. Do you have a dual boot or only ubuntu?

---

### Post by kensclark15 on 2012-05-09
> **darkod said:**
> Hmmm, the grub boot menu should be before that. Do you have a dual boot or only ubuntu?

Well I had a dual boot beofre with Windows 7, but then I formatted the drive and installed only Ubuntu. This is just weird, even if I hold down Ctrl + Alt + F1, it says wrong resolution and I can't get in the console... I hope I don't have to do a fresh install.

---

### Post by |{urse on 2012-05-09
Fresh install time imho. 

You could pop in a livecd and try to rescue grub. 

[http://opensource-sidh.blogspot.com/2011/06/recover-grub-live-ubuntu-cd.html](http://opensource-sidh.blogspot.com/2011/06/recover-grub-live-ubuntu-cd.html)

Stick around for rescue tips if you are desperate, otherwise slave your hard-drive and get whatever you can off of it then start fresh.

---

### Post by |{urse on 2012-05-09
You could also try a different monitor, external if that is a laptop. Maybe you can get grub to show up.

---

### Post by darkod on 2012-05-09
The message about the resolution might be once the OS starts loading. I asked about dual boot because if you have only ubuntu the boot menu never shows. Why would is because there is no other OS to select.

After the POST of the board finishes, you need to hold Shift to show the grub2 menu.

---

### Post by kensclark15 on 2012-05-09
I tried it on a 4:3 monitor instead of a wide screen one. If I run the live cd can I open the terminal in that and do sudo apt-get update then sudo apt-get upgrade?

---

### Post by darkod on 2012-05-09
Not directly. If you simply type that in terminal it will try to do it in the live mode session, not in your hdd installation.

But you can enter your installation with chroot and do it "inside". Do you know your root partition?

If you don't, boot in live mode and post the result of:
sudo fdisk -l (small L)

---

### Post by kensclark15 on 2012-05-09
I'll reply in a bit because I'm downloading the Ubuntu 12.04 LTE ISO and then I have to burn it to a disk.

---

### Post by darkod on 2012-05-09
That's why I asked about the possibility to load the recovery mode. It's much faster and easier, than the chroot option.

The chroot option can be a backup plan.

---

### Post by |{urse on 2012-05-09
He's totally right, try darkod's suggestions first.

/me bows to superior beancount

---

### Post by kensclark15 on 2012-05-09
I'll do the chroot thing because I can't even get on the system recovery thing. Can you tell me more about chroot?

---

### Post by darkod on 2012-05-09
Once you find out which one is the root partition, lets assume it's /dev/sda5, from live mode in terminal you will need to:
Prepare the mount:
```
sudo mount /dev/sda5 /mnt
sudo mount --bind /proc /mnt/proc
sudo mount --bind /dev /mnt/dev
sudo mount --bind /sys /mnt/sys
sudo chroot /mnt
```Now you are like inside the installation. Try few options:
```
dpkg --configure -a
apt-get update
apt-get upgrade
```Unmount and restart to see if it helped:
```
exit
sudo umount /mnt/sys
sudo umount /mnt/dev
sudo umount /mnt/proc
sudo umount /mnt
```Lets see how it goes. Don't forget, with the first command you need to mount the root partition. If it't not /dev/sda5 it needs to be adjusted.

---

### Post by GnuSense on 2012-05-10
I guess I'm missing something. I don't see the point of a chroot or recovery mode. If Ubuntu is the only OS on the machine it won't stop at the grub screen unless the user hits the Shift key after the POST screen. 

Anyway, it sounds to me like 12.04 doesn't like the drivers and you are not getting a viable desktop or display manager.  Can you start another terminal by hitting 'Alt+Control+F1'? If you can get the a TTY, log in as your normal user, then try these commands:

sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install xfce4 
killall lightdm
or 
killall gdm
if that is your display manager.
startxfce4

It sounds to me like compiz is flaking on the machine, probably a driver issue. I'd try a desktop that doesn't require compiz, then sort things out from there.

Also, kensclark15, even if you hopelessly mucked up your install (which I doubt) you should be able to rescue your data with a live CD. Most experienced users prefer to set up a separate /home partition and a 15+ GB '/' partition so even their install gets hosed they can just reinstall the the '/' partition and keep their data intact.

---

### Post by |{urse on 2012-05-10
> If you can get the a TTY

From what I'm reading he can't even see the grub menu and ctrl alt f1 is giving him no prompt.

---

### Post by Sylslay on 2012-05-10
Fresh install but

You could pop in a livecd and try install midnigt commander and log i terminal as root, than chmod everything You like backup and copy it somewhere safe.

---

