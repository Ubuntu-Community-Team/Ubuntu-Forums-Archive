---
title: "Dapper to Edgy Upgrade Boot Analysis"
date: 2006-10-29
forum: Installation &amp; Upgrades
---

### Post by Linuturk on 2006-10-29
Per the official instructions on the wiki, I downloaded the edgy desktop cd and ran the upgrade from the cd (my bandwidth is limited). After upgrading from the cd, I connected to the internet and did an upgrade. Everything seemed to work fine.

I've noticed that the boot process seems sluggish. 

First, I have a bootchart attached for analysis. Is it really going slower? Or is it a matter of perception? I don't feel like anything is being done if I don't see the list of services loading up.

Is there any way to see the list of services that are being loaded, like Dapper's usplash?

Second, I've noticed better performance after a fschk runs on my machine. This happens automatically after 30 boots, but I'd like a way to do that manually. I know I can't do it while the disks are mounted, and unmounting them while the system is loaded seems like a bad idea . . .

Thanks ahead of time for your help.

---

### Post by hk_2999 on 2006-10-30
try sudo editing your grub's /boot/grub/menu.lst and remove quiet from /boot/vmlinuz-2.6.17-10-generic root=/dev/sda2 ro quiet splash.

your vmlinuz version might be different from mine, but just mind the pattern.

---

### Post by Linuturk on 2006-10-30
What would that do, exactly?

---

### Post by Akoluth of Nandus on 2006-10-30
That would display status messages during the boot process.

---

### Post by cholly on 2006-10-30
I have the reverse problem.

I upgraded via update manager. After restart everything works fine *until* it starts "graphics mode." I'm using an old CRT and it tells me the frequency is out of scan range. It's low, like for a in the 20's. 

I can hear the login prompt sound and can log in and then hear the startup sound. I switched to a virtual terminal and examined the xorg.conf file and the backup and they appear to be the same in the display section.

I don't have a grub menu of any kind. likely because ubuntu is the only OS on this machine. I get a brief grub count down then the typical Linux start up.

Any ideas?

---

### Post by cholly on 2006-10-30
This is mis-post because I have too many tabs open. Delete if need be.

---

### Post by hk_2999 on 2006-10-30
btw. Linuturk, i havent seen any real evidence of fsck making your filesystem run faster, so i dont really recommend running it all the time.

but if you are really interested, you can try running fsck from the bootcd. just check it's manpage ( man fsck ), for the options you may want to use with it.

---

### Post by Linuturk on 2006-11-01
Thanks for the grub change. I really like to know what is going on as my machine boots.

My system seems to slow at the beginning, as it is "Reading Files needed for boot"

Anything I can do to speed this up? I mainly switched to edgy because of the (I guess exaggerated) boot and shutdown speeds.

---

### Post by McLoud on 2006-11-02
Do you have readahead enabled (its a process)? If not, try enabling it. And if it is, try doing a boot once putting profile in the kernel line, that will make it look again for all files used in the boot so readahead can read them faster.

---

### Post by Linuturk on 2006-11-02
I'm not seeing readahead in the System Monitor. I'll do some research on it though and see if I can find any install instructions or something.

[EDIT]

the package readahead is installed, and after looking through the two files in /etc/readahead/ it seems it is preloading a lot of stuff (including nvidia drivers!) I have an intel graphics chipset) Is this normal? Anything I can do to improve this?

---

### Post by Linuturk on 2007-01-25
I guess no one knows anything about my readahead problem.

---

