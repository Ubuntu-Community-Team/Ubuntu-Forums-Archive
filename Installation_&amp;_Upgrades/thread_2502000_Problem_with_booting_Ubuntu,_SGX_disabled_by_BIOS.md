---
title: "Problem with booting Ubuntu, SGX disabled by BIOS"
date: 2024-10-29
forum: Installation &amp; Upgrades
---

### Post by johnym2 on 2024-10-29
Hello
Lately i was installing some drivers in Ubuntu and after rebooting this problem show up:

[https://imgur.com/a/OLC3m91](https://imgur.com/a/OLC3m91)

Only this information pops up and system blocks here.

I was trying to enable SGX in BIOS but could not find the option, becouse my motherboard does not support changing SGX, as i understood.
I have motherboard from ASUS, and i dont like that there are few options in this UEFI settings :(

I have installed Ubuntu and Windows 11 on my laptop.
[IMG]https://imgur.com/a/OLC3m91[/IMG][IMG]https://imgur.com/a/OLC3m91[/IMG]

---

### Post by tea for one on 2024-10-29
SGX disabled by BIOS - It's only a message, nothing to worry about
/dev/nvme0n1p5 : clean - This is good news

Does Ubuntu boot successfully?

---

### Post by johnym2 on 2024-10-29
No, after selecting Ubuntu in boot manager, only this show up and it stops here. Well, i waited like 10 minutes with this message displayed and nothing changed.

Windows works fine.

---

### Post by tea for one on 2024-10-29
> **johnym2 said:**
> Lately i was installing some drivers in Ubuntu and after rebooting this problem show up:
Therefore, it appears that your dilemma may be connected with whatever happened here?

---

### Post by grahammechanical on 2024-10-29
We used to get boot up messages about TPM (Trusted Platform Module) claiming there was a firmware bug. But that has been taken care of in more recent versions of Ubuntu. Or, perhaps its in the Linux kernel.

My laptop has Software Guard Extensions (SGX) enabled. I do not experience any problems with Ubuntu. The motherboard functions are there for those who wish to make use of them. And there should be a provision to adjust or disable the settings for those who wish to do that.

Regards

---

### Post by johnym2 on 2024-10-29
> **tea for one said:**
> Therefore, it appears that your dilemma may be connected with whatever happened here?

I was installing drivers to my network card, becouse i thought that this is the problem why i couldn’t connect to the WiFi which require login and password, wich is other issue.
I looked in internet and downloaded some drivers via terminal.
Typed this command:
[B]
sudo apt-get install bcmwl-kernel-source

[/B]and after installation a got this message:

[https://imgur.com/a/mrCqKxl](https://imgur.com/a/mrCqKxl)

So i rebooted the system, and couldn't come back.

link of the website i got the install command from:

[https://www.fosslinux.com/134496/how-to-install-important-drivers-on-ubuntu.htm](https://www.fosslinux.com/134496/how-to-install-important-drivers-on-ubuntu.htm)

---

### Post by tea for one on 2024-10-29
Can you access your UEFI settings?
Disable Secure Boot
Disable TPM and other similar security options (e.g. ftpm, ptt etc.)

---

### Post by johnym2 on 2024-10-29
Yes, i do
I only could disable Secure Boot, i think:

[https://imgur.com/a/YLyE3l3](https://imgur.com/a/YLyE3l3)

Still dont work and now the message is diffrent:

[https://imgur.com/a/kdcNOl7](https://imgur.com/a/kdcNOl7)

---

### Post by tea for one on 2024-10-29
The new message indicates possible file system damage.
I suggest that you boot into a "Try Ubuntu" live session to run a filesystem check.
Open a terminal and enter:-
```
sudo fsck /dev/nvme0n1p5
```
Also, if your ESP is partition 1
```
sudo fsck /dev/nvme0n1p1
```

After fixing errors (if any), close the terminal and power off the live session.
Any luck with booting the installed Ubuntu system?

---

### Post by johnym2 on 2024-10-29
Try Ubuntu? You mean the recovery mode from boot manager? Becouse there i have access to terminal.

---

### Post by deadflowr on 2024-10-29
No, it's the Try Ubuntu option from the installation media.

---

### Post by johnym2 on 2024-11-08
So I used "Try Ubuntu" and typed:

sudo fsck /dev/nvme0n1p5

and thats the output:

fsck from util-linux 2.40.2
e2fsck 1.47.1 (20-May-2024)
/dev/nvme0n1p5 is mounted.
e2fsck: Cannot continue, aborting.

i guess thats and error, but not sure what to do
Partition is right

---

### Post by tea for one on 2024-11-08
> **johnym2 said:**
> 
fsck from util-linux 2.40.2
e2fsck 1.47.1 (20-May-2024)
/dev/nvme0n1p5 is mounted.
e2fsck: Cannot continue, aborting.

Not really an error, more a warning message.
Running a file system check on a mounted partition can introduce more problems.

Boot into a "Try Ubuntu" session again, open a terminal and enter:-
```
sudo umount /dev/nvme0n1p5
```
```
sudo fsck /dev/nvme0n1p5
```

Also, check the file system on your ESP

---

### Post by johnym2 on 2024-11-08
Thats the output now

[B]fsck from util-linux 2.40.2
e2fsck 1.47.1 (20-May-2024)
/dev/nvme0n1p5: clean, 911229/15155200 files, 12387342/60597504 blocks[/B]

---

### Post by johnym2 on 2024-11-10
Ok, now the output seems constractive

[https://imgur.com/a/3sdcUns](https://imgur.com/a/3sdcUns)

Looks like there is no errors

---

