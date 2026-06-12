---
title: "Kernel messup..."
date: 2017-01-21
forum: Installation &amp; Upgrades
---

### Post by johnstefnds on 2017-01-21
Ok everything was working fine with my system for a year or so.. (ubuntu 16.04, AMD FX 8320, 16GB RAM,asrock 970 pro3,120 GB SSD /dev/sda device with separate ext2 partition for grub the main partition being ext4 and a swap folder)

But I had the fine idea to download linux 4.8 kernel... which seemed successful.. I restarted my computer it booted but the login screen (still remembering my custom wallpaper and my username) was low res with black space around it.. I tried to log in both in my account (root) and as a guest but no matter what it would try to log in (log in bar with the user list dissapearing as it would normally) but in a few seconds (while the screen gets black for a split second) I am landed on the login page again....


I restarted my pc and tried to log in with my older kernel 4.4.0.59 or something like that first time it booted I got in the computer with my main account but at random it froze... I had to use hardshutdown from the PC case since nothing was responding 

Next thing I know is that in grub all my previous kernels dissapeared only the 4.8 and the latest 4.4 one were on my list and when I tried to boot with the 4.4 one it just wouldnt boot! I noticed on the console screen (that shows boot order stuff etc before loading the login screen) a message like that " unable to clean up the mess created by 0blsomething"  

Sorry I cant remember the exact text but it surely had the word "mess" in it and something that starts with 0 

Now what I did is to run ubuntu live disk and install boot repair..

I run it followed all the steps but when it was at the step "updating grub" the PC froze!!!!!

Hard shutdown...

But grub loaded and the 4.8 kernel gone but the 4.4 one still available I clicked on that and now again it loads the login screen but on low res (just as it did with 4.8) and when I try to log in it accepts the password but lands me back to the log in screen!!!

I tried to run the ubuntu live disk again started boot repair again only this time I checked on "check file systems" and on "purge all the kernels and reinstall latest" and " update grub to the latest version"

I made a back up it asked me for (and dont know how to use it) 

This time it finished successfully nothing froze everything seemed to be fine. 

It created this link [http://paste.ubuntu.com/23842287/](http://paste.ubuntu.com/23842287/)

And I have also the backupzip file....

I restarted the system normally (from the restart option from ubuntu live )

But now after the bios screen there is a black screen for a few seconds (grub doesnt even load at all) and computer restarts on its own showing again the bios screen and then a black screen and then restart again.. that loop over and over only thing I can do now is to click F11 on the bios screen and choose to boot from the live DVD...

Through the liveDVD I can see that on my main Disk where ubuntu was installed all the files and folders are there nothing has been corrupted or deleted... 

What can I do to boot again with my homefolder and settings intact? please tell me that I just need to install the kernel again and everything will work :D

---

### Post by johnstefnds on 2017-01-21
turns out that boot repair set my main harddrive (the one with the ubuntu installation /dev/sda) as EFI and not UEFI and I suppose thats why I see a blackscreen/reboot loop after the motherboard post message screen,

Can I use my backup file (that boot repair ) created to fix this? how?

---

### Post by ubfan1 on 2017-01-21
Can you successfully login with the guest account? If so, the dot files (files whose first character is a period) are causing the problem and need to be recreated.  These files are called "hidden" so you might need to set the view to see them or use -a on the ls command.  Move them all except the . and the .. into a directory to get them out of the way, and try login again.  The most likely ones to cause problems are the .Xauthority file and the .cache directory.

---

### Post by johnstefnds on 2017-01-21
> **ubfan1 said:**
> Can you successfully login with the guest account? If so, the dot files (files whose first character is a period) are causing the problem and need to be recreated.  These files are called "hidden" so you might need to set the view to see them or use -a on the ls command.  Move them all except the . and the .. into a directory to get them out of the way, and try login again.  The most likely ones to cause problems are the .Xauthority file and the .cache directory.

No I could not and currently I cant even load grub...

---

### Post by Bucky Ball on 2017-01-22
My confusion is that, if you are running 16.04, why are you on the 3.0 kernels at all??? The current 16.04.1 kernel is:

4.4.0-59-generic

... at least on my install. :-k

Are the kernels you installed still supported???

Tried plugging in an ethernet cable, going to recovery root shell, getting online and running these commands?

```
sudo apt autoremove
sudo apt update
sudo apt full-upgrade
```

Reboot after that and see what you get.

---

### Post by Doug S on 2017-01-22
> **Bucky Ball said:**
> My confusion is that, if you are running 16.04, why are you on the 3.0 kernels at all??? The current 16.04.1 kernel is:

4.4.0-59-generic

... at least on my install. :-kGood observation. This can happen when one upgrades versions instead of doing a fresh installation. It happened to me just two days ago while upgrading a 12.04 server to 14.04 and then to 16.04. To fix the issue, and as suggested [here]("http://askubuntu.com/questions/815002/kernel-did-not-upgrade-between-14-04-lts-to-16-04-lts"), I had to do:
```
sudo apt install linux-generic
```

---

### Post by johnstefnds on 2017-01-22
Yes I am sorry guys where ever you see a "3" in the kernel version change it with a "4" actually I am going to do that my self by editing the post

---

### Post by johnstefnds on 2017-01-22
> **Bucky Ball said:**
> My confusion is that, if you are running 16.04, why are you on the 3.0 kernels at all??? The current 16.04.1 kernel is:

4.4.0-59-generic

... at least on my install. :-k

Are the kernels you installed still supported???

Tried plugging in an ethernet cable, going to recovery root shell, getting online and running these commands?

```
sudo apt autoremove
sudo apt update
sudo apt full-upgrade
```

Reboot after that and see what you get.

I dont have a second PC all I can do is put in the live disk and work with that and download stuff by using my phone.

---

### Post by Bucky Ball on 2017-01-22
I didn't say anything about a second machine. :-k

Your phone is a second machine, though, I guess. Not sure how you'll tether to it wirelessly from the recovery root kernel, though. Hopefully you're across that. ;)

---

### Post by johnstefnds on 2017-01-28
I didnt solve it per se but I formated the disk and installed ubuntu 16.10 from scratch... :(

---

