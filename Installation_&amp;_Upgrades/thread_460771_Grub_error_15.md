---
title: "Grub error 15"
date: 2007-06-01
forum: Installation &amp; Upgrades
---

### Post by gimpskinny on 2007-06-01
I had 6.10 installed originally. I then did a clean install of the 7.04 lamp server. Now when I boot, I am getting a grub error 15. I have tried to follow other forums on how to fix this, but none of them are working for me.  I think the problem is that I need to change /boot/grub/menu.lst to point to the right place for the kernel, at least thats what other forums are saying. The problem is when I am booting into rescue mode, I cannot get an editor to work right. vi is erratic when I start moving through the text and the arrow keys won't work, so I have to use the j, k, h, and space bar. I know almost nothing about vi, but when I am trying to move the cursor with the space bar, it will start showing text from two lines below behind the cursor, so I don't know what's going on there. And when I try to use nano, I get an error opening terminal: bterm. So some help would be great. Thanks

---

### Post by hellmet on 2007-06-01
You might try re-installing GRUB to avoid all that editing. 
Btw, on 'vi' you need to hit INSERT or the key 'i' to start editing.

---

### Post by gimpskinny on 2007-06-01
hellmet,

Thanks for the suggestion, but I have already tried that. I have reinstalled ubuntu several times and kept getting the same error, so I tried to reinstall grub only with grub-install /dev/sda1. It installed fine, but when I rebooted, I got the same error 15. I think what the problem is is that the /boot/grub/menu.lst file is pointing to the wrong place. When I open it in vi, and I am at work so I don't know exactly how it is, but it has **kernel /vmlinuz.... root=uuid=....** where I think it should be **kernel /boot/vmlinuz.... root=/dev/sda1**. What that tells me is that it is looking in / for the vmlinuz folder instead of /boot. Am I reading that right? But what seems to be the real problem with why I can't fix it is because I cannot get an editor to work in the rescue mode shell. I have used vi once or twice before. When I am using it now though, it is not behaving at all like it should. For one I have to use j, k, h, and space to move the cursor cause for some reason the arrow keys aren't working. I can enter text when I hit the a key, but when I go back to the mode where I can move the cursor, the text shows up two lines below where I entered it. Also when I hit space to move the cursor right, it starts displaying the text from two lines below. So something is seriously messed up. So I was going to try nano instead which I have never used, but when I try opening the file I get **error opening terminal: bterm**. So I am lost as to what is going on. I have been using Ubunutu for over a year now hardly any issues, but when I am trying to install this release it has been a nightmare. Is there any other way I can change that menu.lst file? I was just thinking, could I put it on a floppy and copy it over?

---

