---
title: "Mint 17 swap partition did not get created correctly during install, hibernate broken"
date: 2015-01-03
forum: MINT
---

### Post by alan45 on 2015-01-03
Hi there,

there is a bit of backstory here as to how this got broken, if you're not interested skip to the end.

Backstory: I installed Linux Mint 17 (based on Ubunut 14.04) recently on my lenovo thinkpad X201 alongside Windows 7.
I'm not new to *nix so as usual, selected the 'Something else' option and partitioned my drive manually, creating an 80GB partition for / and a seperate 2GB swap partition (RAM is 2GB) using gparted. I'm quite certain I got the settings right, although it's possible I did something wrong or didn't spotted an important warning.

Install ran fine, and rebooted, loading Mint with no problems. It wasn't until later that I realised the swap partition wasn't getting mounted on boot, and as a result (I beleive) the hibernate option was greyed out in power management and didn't appear on the shutdown dialogue.
Suspend has been working fine.

I ran gparted again, and my swap partition showed as unknown filesystem type, and obviously wasn't mounted. I formatted it to linux-swap, and ran swapon to get it working. I then manually edited /etc/fstab and added my own entry for the swap partition, removing the previous one left by the install. I rebooted and swap was mounted and used correctly.
After that, hibernate appeared. Great, I thought, all good. So I tried to hibernate, but something went wrong.

The machine shutdown OK, and seemed to write alot to disk before doing so - all seemed OK there.
However on booting up again, Mint loaded as normal without resuming. What's more, after checking ```
swapon -s
``` and ```
free
```, then loading up gparted again, I found that the swap partition was not mounted, and the filesystem type listed in gparted was now linux-suspend.

So my conclusion is that saving worked fine, but something didn't work right on resuming from that saved data.


**tl;dr**

My questions are:
On Mint 17 or Ubuntu 14.04: 
Where do I find log entries for hibernate and resume?
How can I debug the resume process after hibernation?
Given that during installation the swap partition apparently wasn't configured properly, is there anything else I should do to make sure Linux is using it properly?

Thanks for your time and I hope this isn't too specific to Mint, if so I'm happy to pearoast this on the Mint forums instead. Thanks!

---

### Post by alan45 on 2015-01-03
Oh I've also tried running sudo pm-hibernate from the terminal as an article about enabling hibernate on Ubuntu suggested, the same thing happened as when I tried using the dialogue. Machine wrote to disk, powered down, but failed to resume and changed the swap partition to linux-suspend, failing to mount on next boot.

To solve that I have to reformat the swap partition and run swapon.

Any ideas?

---

### Post by ajgreeny on 2015-01-03
Could this be due to a difference in GB and GiB size for your swap, ie, are you absolutely certain you have sufficient swap and that it is not just slightly too small?  I don't know which sizing system Mint uses.

I'm not using Mint, but assuming it's the same as Ubuntu andf the rest of the *buntu family, are you aware that you need to make more configuration changes for hibernate to be enabled than was required in 12.04 and I think all previous ubuntu versions?

Using a text editor make a file with content:-
```
[Re-enable hibernate by default in upower]
Identity=unix-user:*
Action=org.freedesktop.upower.hibernate
ResultActive=yes

[Re-enable hibernate by default in logind]
Identity=unix-user:*
Action=org.freedesktop.login1.hibernate
ResultActive=yes
```

Save it as /etc/polkit-1/localauthority/50-local.d/com.ubuntu.enable-hibernate.pkla

I am not sure if a reboot is needed, but it's worth doing just in case to test this.

---

### Post by alan45 on 2015-01-03
Hi ajgreeny,

thanks for the reply - no I wasn't aware of that, I'll give it a shot.
Good thinking about MiB and MB, Mint uses MiB. I've since increased the size of the swap partition to 9GB (I'm planning a big RAM upgrade so it will need to be atleast 8GB anyway) so there is definitely enough space now.

Yes Mint is basically just Ubuntu 14.04 under the hood, there aren't that many differences as I understand it, mostly UI stuff and choice of window manager.
I'll give that a shot now and see where I get to.

---

### Post by alan45 on 2015-01-03
> Using a text editor make a file with content:-
 	Code:
 	[Re-enable hibernate by default in upower]
Identity=unix-user:*
Action=org.freedesktop.upower.hibernate
ResultActive=yes

[Re-enable hibernate by default in logind]
Identity=unix-user:*
Action=org.freedesktop.login1.hibernate
ResultActive=yes 
Save it as /etc/polkit-1/localauthority/50-local.d/com.ubuntu.enable-hibernate.pkla

There was already a file there with the contents you posted, so I guess that part of the process was either done on install or when I fixed the swap partition. I'm trying playing around with mkswap and swapon, will post back if I get anywhere.

Thanks for your help!

---

### Post by alan45 on 2015-01-03
OK some progress, I've used mkswap and swapon, then edited my entry in fstab to use the UUID of the swap partition. Now when I hibernate, it still doesn't resume but it does mount the swap partition and doesn't leave the linux-suspend filesystem type hanging around. 

I think it's resuming now but not getting to the 'opening last session's programs' stage. Can anyone suggest where to look for errors?

---

### Post by alan45 on 2015-01-03
tried uswsusp too, seems to do more but same end result. does anyone know what to try (aside from a reinstall)? or is there a way to reinstall the OS in-place?

---

