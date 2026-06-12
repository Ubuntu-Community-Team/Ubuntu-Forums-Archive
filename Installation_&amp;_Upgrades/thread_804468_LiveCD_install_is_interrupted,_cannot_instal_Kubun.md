---
title: "LiveCD install is interrupted, cannot instal Kubuntu"
date: 2008-05-23
forum: Installation &amp; Upgrades
---

### Post by agrabah on 2008-05-23
Hello everyone!

I have a huge problem, and hope you can help me solve it (somehow).
The situation:
I had Kubuntu 7.10 installed. Yesterday I decided to install 8.04 from a LiveCD. 
I let the computer work, and when I came back, there was that black screen with the blue Kubuntu logo, and a message to remove the cd and press enter.
That I did. The computer did not reboot, but turned itself off. I turned it on, and lo and behold - grub says error 15, and nothing else happens.
OK - I rebooted the LiveCD and checked what grub error 15 is. Upon discovering that the aforementioned programme seems to be unable to find a specific file, I figured I should reinstall Grub. I do ```
sudo grub
``` and ```
find /boot/grub/stage1
```. No stage1 found. And true - there was no grub subdirectory in my /boot. To keep a long story short - I came to the conclusion that grub was not installed. I copied the file in question from /usr/lib/grub to /boot/grub, and grub-install and grub-update did work fine and reported success.
Now comes the tricky part: upon reboot I was faced with, what appeared at first as a normal boot, but then grub died again, saying something along the lines of (sorry, I forgot to write it down - I was furious) "not being able to sync". It just seemed to me there are still files missing.
Anyway - I reinstalled Kubuntu various times, and even went back to 7.10. I think you've guessed it - same error. Upon further inquiry I discovered that everytime I reinstalled kubuntu, it showed different data on the amount of free space on my root partition. Then I watched the installation procedure closely - it broke off at about 30% (without any error messages). Seems like my CD drive is the culprit. The hard drive seems allright, as I can access my data without any trouble.
Now the problem:
- is there something else that could be the problem?
- what can I do? 
- is there any "verbose" mode to the installation on liveCD?
- can I use the alternate installation CD (and more important - can I burn it from a liveCD)?

Thanks, and please consider me an inexperienced user when writing your replies. The path I described above was a result of a few hours worth of furious googling.

Tine

---

### Post by Pumalite on 2008-05-23
Clean the lens in you burner or replace it. The Alternate is a good idea. Do md5sum on the iso, burn at 4x, etc

---

