---
title: "How to update grub in a encrypted partition ?"
date: 2018-02-08
forum: Installation &amp; Upgrades
---

### Post by jarodd on 2018-02-08
Two days ago, I made an update in my Ubuntu 16.04. During the update, a grub  screen appeared. A black screen with only this message :

```
GNU GRUB version 2.02~beta2-36ubuntu3.16

Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device or file completions.

grub >
```

I touch the TAB touch, it shows me a lot of commands, but I don't know which one would be useful.

  I try to restart my computer, but I fall into this screen immediately, without loading Ubuntu.


  I have make a Boot Repair report, you can see it in this link : [URL="https://pastebin.com/usvf69A8"]boot-repair report

[/URL]

  It seems some people which have the same problem. They say it's a grub problem, which can be corrupted during its update. They run a grub-update to fix the issue.


  But I cannot simply update grub : the specific part of mine is that I  use encryption of my disk. This is why Boot-repair cannot provide me a  solution.


  I ran a live-usb key with Ubuntu 14.04, I see my partition with all my  data, but I cannot access to it because of permissions (I don't have any  right, so I cannot make backups).

And I don't know how to run a grub-update with this encryption. I am totally stuck since 2 days... :( I hope there is a solution, without reinstalling.

  
Cheers

---

### Post by TheFu on 2018-02-09
Boot-info RAW link for others: [https://pastebin.com/raw/usvf69A8](https://pastebin.com/raw/usvf69A8)

Use the same release in a flash-boot/live-boot as is on the system today.  Don't use a 14.04 live-boot with a 16.04 installed OS.

Boot off the 16.04 live-boot, install cryptsetup and whatever else is needed, probably lvm2 stuff, then mount the encrypted storage, setup a chroot so the HDD is the OS, not the live-boot, and run update-grub.  I'm pretty certain I've posted steps in these forums before. Someone asked a similar question 1 day after I'd done it myself, so the steps were fresh in my mind.  You can search the forums as easily as I could.  

I patch weekly on Saturday morningings and my encrypted 16.04 system hasn't had this issue. If I experience it tomorrow, I'll try to post back here the solution I used.

Sorry I'm not more help.

---

