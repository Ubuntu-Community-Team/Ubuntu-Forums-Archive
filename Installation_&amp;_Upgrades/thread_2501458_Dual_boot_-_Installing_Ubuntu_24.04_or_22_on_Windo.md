---
title: "Dual boot - Installing Ubuntu 24.04 or 22 on Windows 11 Pro for Workstation"
date: 2024-10-08
forum: Installation &amp; Upgrades
---

### Post by jdwis on 2024-10-08
Hi guys

I bought a new HP Laptop Pavilion 16 series, which had Win 11 Home, I then upgraded it to Win 11 Pro for Workstation. 
I read many articles for Dual Boot Win 11 and Ubuntu, and still no complete success as stumbling on Ubuntu could not mount Win-11 drive

In Windows 11, I Turned Off BitLocker, the drive gone through its process and its Turned Off now 
Fastboot is off - in Power options 
In Laptop BIOS Setup - Secure Boot is Disabled, and also Cleared All Secure Boot Keys 

Loaded Ubuntu 22.04 and used "Try Now" - which means its not installed, just trying it. 
On loading of Ubuntu, tried accessing the internal and only 1 hard drive (where Windows 11 is installed) but it gives me following error 
"Failed to mount "494 MB Volume" Error mounting /dev/loop1 at /media/ubuntu/disk: /dev/loop1 already mounted or mount point busy" 

Accessing another HD icon (same HD but probably another partition, it throws following error -- 
"Failed to mount "Windows" 
Error mounting /dev/nvme0n1p3 at /media/ubuntu/Windows: wrong fs type, bad option, bad superblock on /dev/nvme0n1p3, missing codepage or helper program, or other error" 
 
There is nothing wrong with the Hard drive as I scanned the HD with Windows itself and other utilities - no prob with HD 

Could you please advise whats going on and how do I use inbuilt Hard drives's empty space, folders etc where I stored all my documents etc on Windows "C" drive ?

---

### Post by tea for one on 2024-10-08
With BitLocker disabled, Ubuntu should certainly be able to open an undamaged ntfs partition.
Did you use Windows tools to reduce the Windows partition?
I suggest that you boot into Windows 11:-
Run chkdsk
Create some free space for Ubuntu
Power off
Boot into Windows 11 again
Run chkdsk again
Power off if all seems OK
Then boot into a "Try Ubuntu" live session and see if Ubuntu recognises the free space?

---

### Post by jdwis on 2024-10-08
Hi

Thank you so much, I followed your instruction and it helped me sort this problem out.
The only thing I would mention here is that running "chkdsk" did not really help me bu then I had to run "chkdsk /f C:" and then it all worked fine
Now I can use that SSD in Ubuntu, so I am happy with this.

Again thanks for the help, this solved my problem.

---

### Post by tea for one on 2024-10-08
Pleased to have helped.
It's a nice gesture to mark the thread as solved to help other forum users/searchers:-
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by jdwis on 2024-10-09
Yes, sure I will mark it as Solved, it was just I didnt know if something like that existed
Thanks again

---

