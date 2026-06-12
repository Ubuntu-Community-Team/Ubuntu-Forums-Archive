---
title: "Just updated from 9.10 to 10.04, and it freezes at login"
date: 2012-01-18
forum: Installation &amp; Upgrades
---

### Post by greengregory on 2012-01-18
Hello, and thanks in advance for any help.

I've been running 9.10 for two years now, and just upgraded to 10.04 today. This turned out to be a big mistake, because now my system freezes on the login screen after issuing several error messages. Here are the errors that appear (transcribed, not copied and pasted).

mount: mounting none on /dev failed: No such device
usb_id[232]: unable to access '/devices/pci0000:00/0000:00:1d7/usb2/2-5'
chroot: cannot execute /etc/apparmor/initramfs: No such file or directory
init: ureadahead main process (248) terminated with status 5

Then the ubuntu logo appears, along with another error message (which I saw the first few times I rebooted, but can't see anymore), and then it freezes at the login screen.

This happened a few times, but now it doesn't even get to the login screen--it's stuck on "your disk drives are being checked for errors, this may take some time."

I realize that some of these error messages have been addressed already in other threads, but the problems don't seem to be the same as mine (i.e., many other people seem to get the "mount: mounting none on /dev failed: No such device" message, but their systems boot up just fine).

I'm not an absolute beginner. I know how to navigate the file system and edit files, but not much else. I have no idea which of these errors is/are causing my problem. Any help would be much appreciated.

---

### Post by raja.genupula on 2012-01-18
Hi try this once may be it could help you , please insert a live cd and run fsck once to your harddisk and try again . 

one more thing is choose recovery mode from grub menu and try to boot from failsafeX mode and reinstall your graphics drivers once .


All the best .

---

### Post by mörgæs on 2012-01-18
Hi, welcome to the fora.

You have a long way ahead, if you want to reach 11.10 through upgrades. Have you thought of a fresh install?

---

### Post by nipunshakya on 2012-01-18
@OP: Hi.Warm welcome to the forum. If you are intending to make an upgrade, i suggest you to go for a clean install instead of upgrading current OS version.. This will help you reduce errors in future regarding those you mentioned above..
In a simple language,with each new version, there are few changes and if our machine isn't able to handle those changes, we get errors.
So, instead of worrying about the error, my opinion would be to make a clean fresh install and begin from scratch(if you can manage time for that.).... Still, there is always an option for you to wait for someone to address your error and help you fix it.

Always a clean install isn't a good advice for simple minor errors. But if you are in an upgrade, why not a clean install..?? hehe.. Goodluck :D
Regards, WinuxUser

---

### Post by greengregory on 2012-01-18
Thanks for the advice. I think I will try a new install. My old install was done with wubi, so I'll try the new wubi tonight. Then I'll try to retrieve my files. New question: is there an easy way to move files between different wubi installations?

Edit: I think I found the answer to this new question.

---

### Post by dino99 on 2012-01-18
wubi is good to let you know what ubuntu is, but its not a long term solution: do a real install.

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

