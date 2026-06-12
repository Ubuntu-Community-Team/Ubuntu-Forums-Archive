---
title: "AMD GPU driver 13.4, hang black screen on Ubuntu 12.04."
date: 2013-05-14
forum: Installation &amp; Upgrades
---

### Post by Kreaninw on 2013-05-14
I followed the instructions here

[http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide)

After removed previous driver(13.1) I installed a new one (13.4) and after I rebooted my laptop, I only got black screen after Ubuntu logo. Ctrl+alt+F2 doesn't take me to TTY. 

I don't know what to do any more. I can't use my laptop now(I'm typing on my tablet.). PLEASE HELP!!!

I'm using Acer Aspire 4745G with Intel Core i5-460M and ATI/AMD Mobility Radeon HD5650. Ubuntu 12.04 64-bit.

---

### Post by QIII on 2013-05-14
Hello!

Can you get to the GRUB menu by holding down the SHIFT key when the machine boots?

---

### Post by Kreaninw on 2013-05-14
> **QIII said:**
> Hello!

Can you get to the GRUB menu by holding down the SHIFT key when the machine boots?

Yes, I can get the GRUB menu. But I don't have to holding down the SHIFT key.

---

### Post by QIII on 2013-05-14
OK.  Do you see a selection that says "recovery mode"?

---

### Post by Kreaninw on 2013-05-14
Yes.

---

### Post by QIII on 2013-05-14
Select that.  Look for an entry that says "root shell with networking"  (I think.  This is from memory)

---

### Post by Kreaninw on 2013-05-14
> **QIII said:**
> Select that.  Look for an entry that says "root shell with networking"  (I think.  This is from memory)

I got root shell and networking in separate menus. T-T

---

### Post by QIII on 2013-05-14
Select networking to mount read/write then you should be able to back up and select root

---

### Post by Kreaninw on 2013-05-14
> **QIII said:**
> Select networking to mount read/write then you should be able to back up and select root

Selected. It doesn't go beyond here. Seems like it hanged.

---

### Post by QIII on 2013-05-14
No response t "yes"?

Hit the left, right arrow keys and see if you can shift between the two selections.

---

### Post by Kreaninw on 2013-05-14
> **QIII said:**
> No response t "yes"?

Hit the left, right arrow keys and see if you can shift between the two selections.

Yes, no respond. I already hit Yes. When I hit left arrow, it shows ^[[D^ , and when I hit right arrow, it shows ^[[C^ .

---

### Post by QIII on 2013-05-14
OK.  It should have mounted and then taken you back to the GRUB recovery menu.

What happens if you just press Enter?

---

### Post by Kreaninw on 2013-05-14
> **QIII said:**
> OK.  It should have mounted and then taken you back to the GRUB recovery menu.

What happens if you just press Enter?
 
I can't go back to previous menu. When I hit enter it just add a new line.

---

### Post by QIII on 2013-05-14
Hmmm.  Selecting "yes" should have mounted what is in your fstab and taken you right back to the GRUB recovery screen to select root.

Hold the ALT and SYSREQ buttons (your keyboard may say "Print Screen") and then, slowly, type R E I S U B

Hopefully we'll get a clean reboot.

---

### Post by Kreaninw on 2013-05-14
> **QIII said:**
> Hmmm.  Selecting "yes" should have mounted what is in your fstab and taken you right back to the GRUB recovery screen to select root.

Hold the ALT and SYSREQ buttons (your keyboard may say "Print Screen") and then, slowly, type R E I S U B

Hopefully we'll get a clean reboot.

Yes, I got a clean reboot from the keys above. What I have to do next?

---

### Post by QIII on 2013-05-14
Let's try that again, just in case some computer gremlins were playing with you.  If that doesn't work, I'll think about it for a bit or ask someone for suggestions.

So...

Recovery, networking, root.

I'll cross my fingers.

---

### Post by Kreaninw on 2013-05-14
> **QIII said:**
> Let's try that again, just in case some computer gremlins were playing with you.  If that doesn't work, I'll think about it for a bit or ask someone for suggestions.

So...

Recovery, networking, root.

I'll cross my fingers.

Still doesn't work.

---

### Post by QIII on 2013-05-14
OK.  One more try before I call the cavalry...

Reboot, go to recovery and directly to root.  Let me know when you are there.

---

### Post by Kreaninw on 2013-05-14
> **QIII said:**
> OK.  One more try before I call the cavalry...

Reboot, go to recovery and directly to root.  Let me know when you are there.

Go directly to root and I'm here.

---

### Post by QIII on 2013-05-14
Can you type on the command line?

---

### Post by Kreaninw on 2013-05-15
> **QIII said:**
> Can you type on the command line?

Yes, I can type on the command line.

And I'm connecting this laptop to internet via LAN cable. But I'm not sure without enable it from the menu, it'll be working.

---

### Post by QIII on 2013-05-15
Don't worry about that just for the moment.  What we need to do right away won't take a network connection.

Please be *very *careful.  You are root and your machine will do exactly what you tell it to do -- it'll assume you know exactly what you are doing.

OK?

Ready?

---

### Post by Kreaninw on 2013-05-15
> **QIII said:**
> Don't worry about that just for the moment.  What we need to do right away won't take a network connection.

Please be *very *careful.  You are root and your machine will do exactly what you tell it to do -- it'll assume you know exactly what you are doing.

OK?

Ready?

Yes, I'm ready. :guitar:

---

### Post by QIII on 2013-05-15
We're going to ask the kernel very nicely if it will go ahead and mount your drives read/write based on what is in your fstab.  You don't need to use sudo because you are root.

Type:

```
mount -a
```

---

### Post by Kreaninw on 2013-05-15
> **QIII said:**
> We're going to ask the kernel very nicely if it will go ahead and mount your drives read/write based on what is in your fstab.  You don't need to use sudo because you are root.

Type:

```
mount -a
```

When I typed mount -a and enter. Nothing happen at all.

---

### Post by QIII on 2013-05-15
That's expected.

Now, we are going to rename your /etc/X11/xorg.conf (if it exists).  We're not going to delete it, because I don't want you to use the rm command while you are root.

So:
 
```
mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

---

### Post by Kreaninw on 2013-05-15
> **QIII said:**
> That's expected.

Now, we are going to rename your /etc/X11/xorg.conf (if it exists).  We're not going to delete it, because I don't want you to use the rm command while you are root.

So:
 
```
mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

It says cannot move Read-only file system.

---

### Post by QIII on 2013-05-15
Nutz.

OK.  Type exit to get back to the recovery menu and select network.

---

### Post by Kreaninw on 2013-05-15
> **QIII said:**
> Nutz.

OK.  Type exit to get back to the recovery menu and select network.

I'm in network menu now, hit Yes, and still the same result as before. Nothing happen.

---

### Post by QIII on 2013-05-15
OK.  I fired up my vanilla 12.04 and I have my keyboard pulled over.  Going to walk through this with you.

Reboot and get back to the recovery menu.

---

### Post by Kreaninw on 2013-05-15
> **QIII said:**
> OK.  I fired up my vanilla 12.04 and I have my keyboard pulled over.  Going to walk through this with you.

Reboot and get back to the recovery menu.

Thanks very much. I'm on recovery menu now.

---

### Post by QIII on 2013-05-15
OK.  Go to root and type

```
blkid
```

(That's bee el kay eye dee)

Grab a pic of that.

Then type
```
cat /etc/fstab
```

Grab a pic of that.

Post that back so I can take a look.

---

### Post by Kreaninw on 2013-05-15
k> **QIII said:**
> OK.  Go to root and type

```
blkid
```

(That's bee el kay eye dee)

Grab a pic of that.

Then type
```
cat /etc/fstab
```

Grab a pic of that.

Post that back so I can take a look.

Here are my result.

---

### Post by QIII on 2013-05-15
OK.  Thanks.  This was originally a Windows machine, correct?

Did you overwrite windows or dual boot?

Is it BIOS or UEFI?

---

### Post by Kreaninw on 2013-05-15
> **QIII said:**
> OK.  Thanks.  This was originally a Windows machine, correct?

Did you overwrite windows or dual boot?

Is it BIOS or UEFI?

Yes, this was originally a Windows 7 64-bit machine. It's genuine OEM pre-install with my laptop.

It's dual boot setup. Windows 7 with Ubuntu 12.04. Both are 64-bit version. I'm using Ubuntu as my default OS, so my works are in there but Windows can't see it. T___T 

It's BIOS(I think). UEFI is Windows 8 thing, right? I'm not using Windows 8.

---

### Post by QIII on 2013-05-15
Will it boot to Windows at the moment if you hold the shift key to get to GRUB?

---

### Post by Kreaninw on 2013-05-15
> **QIII said:**
> Will it boot to Windows at the moment if you hold the shift key to get to GRUB?

I can boot to Windows, everything work fine on Windows.

---

### Post by QIII on 2013-05-15
OK.  I hit up the other Moderators for someone to look at this.  It's been far to long since I dual booted, and that was back in the XP or Vista era.  It may take a while, so don't be too worried if you don't get a response right away.

I'm not sure if your problem is your video driver, since you aren't even getting that far.

Don't despair!  ;)

Best wishes!


Edit -- wait one.  Another thing to try that I wasn't thinking of...

---

### Post by QIII on 2013-05-15
Try going to the recovery menu and starting in failsafe graphics mode.

Duhr!  Old man, here.  Sometimes forget to put on my pants before I go to work.  ;)

---

### Post by Kreaninw on 2013-05-15
> **QIII said:**
> Try going to the recovery menu and starting in failsafe graphics mode.

Duhr!  Old man, here.  Sometimes forget to put on my pants before I go to work.  ;)

Here is my result. Nothing happen at all. T___T

To tell you the truth, I'm quite sure it's because AMD 13.4 driver. Because before I got into this stage. I removed all previous driver(13.1) as instructed in [http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide) , and I re-install open source driver as instructed too. After reboot, my laptop was still working fine. Graphic detail was Geasey v 0.4 or something, I can't remember well.

But after I installed 13.4 driver and then reboot again, I got into this stage. I used to update from 12.6(the version in Ubuntu 12.04) to 12.8 and from 12.8 to 13.1, without a problem at all using the same method.

I tried to change my graphic mode between discrete mode and hybrid mode in BIOS. But it doesn't help at all. My previous working setting is on discrete mode with 12.6, 12.8, and 13.1 driver.

---

### Post by Kreaninw on 2013-05-15
I think I found the issue. 

[http://support.amd.com/us/kbarticles/Pages/amdcatalyst13-4linreleasenotes.aspx](http://support.amd.com/us/kbarticles/Pages/amdcatalyst13-4linreleasenotes.aspx)

It says, 13.4 is designed to support Ubuntu 12.10. I'm using 12.4 that's why...

Now I don't care about my system anymore!!! All I want is my data back. I am ready to do a fresh Ubuntu install. 

[B]Is it possible to use Ubuntu CD to repair system partition or do a new install without wiping out all of my data?
[/B]
I also googled and found the app called Boot-Repair. Will it help me surpass black screen and get me to my desktop?

[http://ubuntuforums.org/showthread.php?t=1769482](http://ubuntuforums.org/showthread.php?t=1769482)

Thanks in advance for your help, my problem is really urgent and I really need help. Googled everywhere but couldn't found anything to fix my problem. This forum is my last hope. I just want my data back.

---

### Post by Kreaninw on 2013-05-17
I have managed to repair my Ubuntu without loosing my data. I think it's very little info about this, so I want to share it with you guys. No command line, only GUI and click click click. CHEERS.

1. First, you need Ubuntu CD, here [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop) . Download the CD image and burn it down with your favorite burner.

2. Put it in your PC/laptop and then set boot priority in the BIOS, set your corresponding Bluray/DVD/CD drive to boot first. From your BIOS menu, save and exit your setting. Reboot your system.

3. Now, you will see installation screen like when you first install Ubuntu. Choose "install" option but we'll actually repair a broken Ubuntu. For now, we'll choose to install Ubuntu.

4. Follow the instructions till you see the partition manager screen. This is very important step. 

- First, you need to know about your partitions. Normally, your Ubuntu partitions will be in ext4 format while your Windows partitions will be in NTFS format. This is easy. 

- Next, Ubuntu uses 3 partitions setup. Root ( / ) where your system files locate. Boot ( /boot ) where your boot loader files locate. Home ( /home ) where you data in Home folder(It included your desktop, my document, my pictures, my musics, and everything else where you don't need root permission to read/write the files.) locate. And lastly, it's optional for using Ubuntu but it's a recommend option, SWAP partition, which will show as Unknow format.

- You will need to reconfigure those 3 or 4 partitions. But the real problem is, in partition manager page, it doesn't show you what partition is your root, boot, home, and swap. But you can tell what partition is your root (where your Ubuntu's system files were installed) by choosing in the where to install your boot loader dialog. It will show you the partition and Ubuntu name after it, this is your root partition. For your boot partition, normally it's the smallest one out of the 4. Your home is the biggest one out of the 4. And your swap is in the unknow format.

- Select your root partition and click "change" button. Choose ext4 file system, and mount it as "/" . Don't tick "format" box!!! You must not format any partition if you want to repair it.

-Select your boot partition and click "change" button. Choose ext4 file system, and mount it as "/boot" . Don't tick "format" box!!! You must not format any partition if you want to repair it.

- Select your home partition and click "change" button. Choose ext4 file system, and mount it as "/home" . Don't tick "format" box!!! You must not format any partition if you want to repair it.

- Select your swap partition and click "change" button. Choose ext4 file system, and mount it as "swap" . Don't tick "format" box!!! You must not format any partition if you want to repair it.

5. Choose your boot loader partition the same as your /boot and hit the install button to repair your Ubuntu. While it's installing your Ubuntu, you should see the page where you have to choose your username and password. You have to set your username and password THE SAME as before you do this repair process.

After rebooted, you should be able to boot into Ubuntu flawlessly.

My suggestion to Ubuntu team would be, please make repair process more easily. First, it can be very confusing if I have to choose "install" button to repair my system.

***If you can't log in to your username but able to log in as guest. You may have to setup some gdm thing. See instructions here [http://askubuntu.com/questions/139528/cant-log-in-to-ubuntu-12-04](http://askubuntu.com/questions/139528/cant-log-in-to-ubuntu-12-04) ***

Sorry, I have no screenshot as I don't know how to capture the screen while I'm in setup stage. I think this method can solve any system relate problem without losing your data. The downside is that you have to re-download all apps again not even count reconfigure them will consume your time and productivity. But it's your last resort if no one can help you and you don't know how to fix a specific problem. And sorry if my English is bad.

---

