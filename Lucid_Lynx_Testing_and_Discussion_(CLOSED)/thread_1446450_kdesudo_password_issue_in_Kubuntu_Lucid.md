---
title: "kdesudo password issue in Kubuntu Lucid"
date: 2010-04-04
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by ggregorsch on 2010-04-04
Hello, ):P
this is my first message posted on this forum so please excuse me if I'm posting in the wrong section.
Since now, I managed to solve all my linux problems by searching on the Internet. But a few days ago, after the last Lucid update, I encountered a problem that I cannot solve:
- after kde starts, four windows appear in the taskbar, each one states: "please enter your password to use this device" and a password field underneath. No matter if I enter the password, next session restart the four windows reappear.I understand this problem is related to some NTFS partitions mounted at system startup. The partitions are indeed mounted and I can access all of them but I wonder how I can get rid off these messages.
I am a linux greenhorn so please be patient with me.:biggrin:
Thanks in advance and excuse my bad english.

---

### Post by tico on 2010-04-10
I'm having the same problem. Any clue on what's happening? How could I solve this issue?

Thanks.

---

### Post by SuilAmhain on 2010-04-10
I had this same problem. I'll try and explain as generic as i can. But I am no linux expert!! :)

When I logged in I was asked to enter my password twice.
The window I got asking me to enter had the title "Password - kdesudo"
and the text: "Please enter password to use this device"
(I spent ages, fruitlessly, searching for those terms so included to help others)

My problem was related to NTFS partitions.
I'm dual booting with Windows 7 which by default has two NTFS partitions. 
One for the Windows bootloader and one for Windows itself.

To test were these partitions the problem i commented out their respective lines in /etc/fstab by adding a # at the beginning of each line that had NTFS as a filesystem type.

Depending on your Ubuntu flavour one of following will enable you to edit that file.

sudo gedit /etc/fstab
sudo kate /etc/fstab
sudo vi /etc/fstab  

After editing save and reboot to confirm that you are no longer asked for passwords @ login.

If you are not asked for password you now know the problem. If you are still asked for the password it is something else and better to undo what you did above.

Using your file browser (Nautilus or Dolphin) navigate to the NTFS partition you want to automount and open it so that /etc/mtab gets updated with details required for next step.

Next i went to /etc/mtab and borrowed the line from there that correctly mounts the partition for usage.

sudo gedit /etc/mtab
sudo kate /etc/mtab
sudo vi /etc/mtab  

Copy the line that refers to your NTFS partition mine looked like:
[FONT="Courier New"]/dev/sda3 /media/sda3 fuseblk rw,nosuid,nodev,allow_other,allow_other,blksize=4096 0 0[/FONT]

Next paste that line into your /etc/fstab
**N.B.** When you have it pasted in change **fuseblk** for **ntfs** it's important you do this or booting will be an issue for you.

So it will now look something like
[FONT="Courier New"]/dev/sda3 /media/sda3 ntfs rw,nosuid,nodev,allow_other,allow_other,blksize=4096 0 0[/FONT]


Save the file and reboot. No annoying password prompts for you :guitar:

---

