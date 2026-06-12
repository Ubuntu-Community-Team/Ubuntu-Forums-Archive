---
title: "Grey bars on top of screen"
date: 2015-09-21
forum: Installation &amp; Upgrades
---

### Post by nana3 on 2015-09-21
Tried to install Ubuntu 14.10 to move up to 15.04. Due to complications, the installation was not completed. I tired to install using the boot meant (Ctrl+Alt+F2); now when I start the computer, nothing works and there is a row of grey gradient bars on the top half of my screen. Please help; URGENT

I'd like to also add that I was not aware that Ubuntu 14.10 had lost support in July. Egg on my face, I guess.

This is what it looks like ans still looks like.

Update: it turns into a black space if i wait long enough.

---

### Post by ian-weisser on 2015-09-22
> **nana3 said:**
> Tried to install Ubuntu 14.10 to move up to 15.04.
Why? Do you have a reason for not following the simpler path of installing 14.04 LTS or 15.04 directly?
Have you tried those simpler paths?> **nana3 said:**
>  Due to complications, the installation was not completed.
Exactly what complications? Errors? Failures? Skips? Freezes? Drops? Smokes? 
Did these complications occur during the install of 14.10? Or during the upgrade from 14.10 to 15.04?
Please provide as much detail as possible - we need much more to narrow the cause (and fix) to a useful number of choices.

How much time and effort are you willing to invest in diagnosing and fixing? Or do you prefer to try reinstalling a supported version of Ubuntu to speed up the process?

---

### Post by nana3 on 2015-09-23
I had 14.04 LTS. I tried to update to 14.10 to move up to 15.04. I didn't finish the installation because I stupidly turned the computer off in the middle, so the login screen would freeze. I attempted to open up a safe mode (Ctrl+Alt+F2) and thought that if I finished up the installation, it would work. Now, when I turn on the computer,I get what you see. No login. Not even any loading. Heck, now the half of the screen that had the grey bars turns into a black space.

Did I wreck my computer? I'm willing to put as much effort as I can to fix this.

---

### Post by ian-weisser on 2015-09-23
> **nana3 said:**
> I didn't finish the installation because I [...] turned the computer off in the middle

Ah, so your system isn't just broken. Your may have pieces of two incomplete, incompatible systems, both broken, and scrambled together.
You might be able to laboriously put those eggs back together if you spent a few days learning the skills...but I doubt it's a worthwhile effort.
The recommended solution is to backup your data, then reinstall from a fresh 14.04 or 15.04 LiveUSB.

Did you wreck your computer? The hardware, no. The software, yes. The software may be thoroughly wrecked.

---

### Post by nana3 on 2015-09-23
Thank you for replying, Ian.

I can't access the data to back up. There's no way I can get onto my computer that I know of?

Should I call someone?

---

### Post by ian-weisser on 2015-09-23
Who would you call? If you know somebody with the proper skills and interests, then certainly contact them.

There are many ways to preserve your data before reinstalling.
Here's one way: Get two USB sticks, one for the Installer (LiveUSB), other for data backup.
Boot using the LiveUSB. Select 'Try Ubuntu'.
Mount your hard drive. Copy your data from the hard drive onto the data USB stick.
Unmount and eject/remove the data USB stick.
Install Ubuntu.

---

### Post by nana3 on 2015-10-11
> **ian-weisser said:**
> Who would you call? If you know somebody with the proper skills and interests, then certainly contact them.

There are many ways to preserve your data before reinstalling.
Here's one way: Get two USB sticks, one for the Installer (LiveUSB), other for data backup.
Boot using the LiveUSB. Select 'Try Ubuntu'.
Mount your hard drive. Copy your data from the hard drive onto the data USB stick.
Unmount and eject/remove the data USB stick.
Install Ubuntu.

Can you elaborate on how to boot w/LiveUSB?

---

### Post by ian-weisser on 2015-10-11
> **nana3 said:**
> Can you elaborate on how to boot w/LiveUSB?

See [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
Obviously, you want to 'Try Ubuntu', not actually install nor reinstall.

---

### Post by nana3 on 2015-10-11
> **ian-weisser said:**
> See [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
Obviously, you want to 'Try Ubuntu', not actually install nor reinstall.

Okay. And should I back up my data beforehand or when it's booted? How would I mount my hard drive?

---

### Post by nana3 on 2015-10-11
> **ian-weisser said:**
> See [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
Obviously, you want to 'Try Ubuntu', not actually install nor reinstall.

Also, I can't access my Ubuntu at all, but I have a Windows I have access to. Should I just get a software that puts Ubuntu on a flash drive? I'm a casual Ubuntu user, I'm still very inexperienced with the intricacies of this (see: how I got into this mess)

---

### Post by ian-weisser on 2015-10-11
Yes you can certainly use Windows to create an Ubuntu LiveUSB. See [http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows)

Backing up your data before mounting the drive upon which it resides would be quite a trick!

After you have booted from the LiveUSB, see [http://askubuntu.com/questions/190239/how-to-access-hard-drive-files-from-livecd](http://askubuntu.com/questions/190239/how-to-access-hard-drive-files-from-livecd) for how to mount your hard drive and backup media.  

One assumes that you don't have dual boot Windows and (broken) Ubuntu on different partitions of the sand hard drive. If you do, say so right now before the Ubuntu repair breaks your Windows, too.

---

### Post by nana3 on 2015-10-11
> **ian-weisser said:**
> Backing up your data before mounting the drive upon which it resides would be quite a trick!

To mount your hard drive and backup media, so that you can backup your data, see [http://askubuntu.com/questions/190239/how-to-access-hard-drive-files-from-livecd](http://askubuntu.com/questions/190239/how-to-access-hard-drive-files-from-livecd)

Okay, three last questions (probably): 

If I get an ISO file, and put the software on a USB drive, the drive will not change my Windows computer to an Ubuntu if I plug it into my other comp, right?

Do I need basic install or persistent line?

Should the computer be off when I plug it in? I'm worried that I'll have to click on something, since I won't be able to do that.

---

### Post by nknwn on 2015-10-11
This video might help: [https://www.youtube.com/watch?v=CFeri7UiYNs](https://www.youtube.com/watch?v=CFeri7UiYNs)
It demonstrates creating a Ubuntu pen drive with Windows and then booting the same computer with the Ubuntu pen drive.
... and..... it will also boot your Ubuntu Computer :)

---

### Post by nana3 on 2015-10-11
Yes!!!
 
I was able to get Ubuntu 15.04 on my desktop via a persistent session!!

...Now I just need help with the mounting and backup. I can't see anything in the ejectable Volumes (996 GB and 4.3 GB) or in Computer, at least none of my old files. The link I was gien before makes me think this is trial-and-error. What do I do now?

---

### Post by nana3 on 2015-10-11
Ah, here's the thing. I don't have permission to copy anything. (-_-)

---

### Post by nknwn on 2015-10-11
Take ownership with chmod
[https://www.youtube.com/watch?v=F_4550AwVtQ](https://www.youtube.com/watch?v=F_4550AwVtQ)

This will allow you to take ownership of the directory and all the files and directories within.
The command: [B]sudo chmod -R 777 /pathtodirectory/directory
[/B]To check the path, right click on the directory and choose properties[B].
Don't make any mistakes in the path like inserting a space as it could cause a big problem :)
[/B]

---

