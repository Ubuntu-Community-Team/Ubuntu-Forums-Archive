---
title: "New computer, blank HDD, how to install ub"
date: 2010-07-15
forum: Installation &amp; Upgrades
---

### Post by trevk on 2010-07-15
Hi im sure this has been posted a million times but i need some help getting ubuntu to install on my new hdd. just finished building a new computer and wanted to give this os a try so i took out one of my old hdd and formated it. and im at a loss =/ anyone willing to point me in the right direction of give me some advice? thanks!

---

### Post by trevk on 2010-07-15
just to clear things up i have my "main computer" that i dont want to run ubuntu on and my new 2nd computer that i want it to be the main os on.

---

### Post by renovatio94 on 2010-07-15
So you have a desktop with multiple Hdd's in it? Or just one.

---

### Post by trevk on 2010-07-15
yes i have the formated hdd that i want in my new computer on my main computer at the moment.

---

### Post by renovatio94 on 2010-07-15
Download Ubuntu: [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
When you boot up, click the install tab. Set up your time and language. Then when you come to where to install it, click the specify choice. Then click the drive you want to install on. It will show the size of each drive you have in your computer so just make sure you choose the right one.

---

### Post by mörgæs on 2010-07-15
and remember to have wired internet access while installing.

---

### Post by renovatio94 on 2010-07-15
Its very easy and new user friendly. :)

---

### Post by trevk on 2010-07-16
ok now i have a problem. i got it to install to the spare empty hdd. when it was finallizing it stoped at 26%. i turned he computer off and removed the hdd. now when i try to boot my main hdd with window it says GRUB LOADING ERROR NO SUCH DISK. i didnt install it to my hdd that i didnt want to. i made sure i didnt click the 1tb hdd over my old 160gb hdd. what happened?

---

### Post by trevk on 2010-07-16
any help? was kinda hessitant on tryting ubuntu and now im just frustrated =/

---

### Post by trevk on 2010-07-16
still up and looking for answers if anyone see this. i dont have my windows 7 disk and i have no ida why grub it booting when i set it to my 2nd hdd (its now removed)

---

### Post by oldfred on 2010-07-17
When you have multiple drives you also have to use the advance button on the last partition screen where it says ready to install to choose where to install grub. Grub will normally install to the boot drive or sda overwriting your windows boot as it assumes you want to boot your new install.

Shows it for Kamic but essential the same for lucid.
[http://members.iinet.net/~herman546/p28/032_install-now.png]("http://members.iinet.net/%7Eherman546/p28/032_install-now.png")
Install karmic Screens shown with advanced button
[http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml](http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml)

Dual boot 2 drives
[http://members.iinet.net.au/~herman546/p24.html]("http://members.iinet.net.au/%7Eherman546/p24.html")

Restore basic windows boot loader - universe enabled from linux liveCD
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR

If your PC did not come with a complete Vista or Win7 installation CD, you can download a Recovery Disc at the following links:
Windows Vista/7 Recovery Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista will not repair XP (they create the boot sectors differently) but can run chkdsk.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

### Post by gordintoronto on 2010-07-17
On your "main" computer, download Ubuntu (actually, I suggest Linux Mint, a variation on Ubuntu) and "burn the image" to a CD. This is not the same as creating a data CD which contains the file.

On your new computer, with one blank hard drive, boot from the CD and select "install". If it appears to stall, wait a few minutes. Depending on the speed of your computer, it might appear to pause for more than five minutes, but it's doing stuff.

The only tricky part is burning the image.

---

