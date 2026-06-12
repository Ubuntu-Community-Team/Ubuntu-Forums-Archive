---
title: "Ubuntu 10.4.3 failed to start."
date: 2011-11-12
forum: Installation &amp; Upgrades
---

### Post by SheaMan on 2011-11-12
Totally Linux/Ubuntu noob - kinda know XP/Mac. :guitar:

I burned 10.4.3 (LTS version) onto a CD and set the machine to start from the CD. This is what I see on the screen. 
---
BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) mount: mounting /dev/loop0 on //filesystem.squashfs failed: Input/tput error
Can not mount /dev/loop0 (/cdrom/casper/filesystem.squashfs) on filesystem.sashfs
---

Umm.. I typed help and it seems to be working. If there is a thread that covers this problem a link would be fine :D I did a search for filesystem.squashfs and found zero results. TY!

---

### Post by 73ckn797 on 2011-11-12
This is a typical reply.
Did you check the md5sum's of the downloaded iso? Did you burn the iso at the slowest speed? Did you run the check disk option when booting from the disk? A bad iso will result in a bad burn. Burning too fast will result in a bad burn. A bad burn will cause all kinds of problems.

---

### Post by SheaMan on 2011-11-12
"Did you check the md5sum's" :confused: wuzzat?

I did choose the 'verify' checkmark for my image burner - I am using Daemon Tools lite with the astroburn plugin. I am burning a new copy now - tanks 73, \\:D/ can I call you 73? :smirk:

---

### Post by 73ckn797 on 2011-11-12
Info about the md5sum's can be found here: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto) 

Call me anything you want except late for dinner.:P

I use Brasero which works fine and is included in Ubuntu.

---

### Post by SheaMan on 2011-11-12
I reburned the Disk at the slowest speed and with the verify. 
I tried that disk and got the same issue. 

I looked up md5sum on wikipedia and ..I don't think I have the ability to use that - is there some way of doing that check on XP?

Is there a good search string to use to find some steps to use? Apparently filesystem.squashfs is specific??

Gonna try some stuff BRB. :roll:

---

### Post by SheaMan on 2011-11-12
[http://ubuntuforums.org/showthread.php?t=1598415&highlight=mount%3A+mounting+%2Fdev%2Floop0](http://ubuntuforums.org/showthread.php?t=1598415&highlight=mount%3A+mounting+%2Fdev%2Floop0)

Interesting. Redownloading the ISO.

---

### Post by 73ckn797 on 2011-11-12
Google is your friend. Have your searched for the answer to your XP md5sum question there?

---

### Post by SheaMan on 2011-11-13
I did find a link to a forum with links to download a couple of different md5sum check softwares, but...upon a cursory examination of the file properties ..der.. the iso was only 69 megs large.. :oops:

So..yeah..that was obvious if I had thought to look. I decided to download the server version instead because I want to make the machine a proxy server. Any suggestions for finding advice on how to make a good proxy server?  [-o<

---

### Post by SheaMan on 2011-11-13
Welp, all good! Disk burned and installing. 
Configuring now!

:lolflag: Now..how..do I set the thread header to solved..
edit post? 

Thanks 73!

Aha! [http://ubuntuforums.org/showpost.php?p=4527051&postcount=6](http://ubuntuforums.org/showpost.php?p=4527051&postcount=6)

---

