---
title: "Help please: OS upgrade won't boot up now"
date: 2016-01-02
forum: Installation &amp; Upgrades
---

### Post by spencer2 on 2016-01-02
A couple weeks back I did an upgrade from Ubuntu 14 to 16. I didn't really mean to skip 15, it just sort of happened. During upgrade I got lots of kernel error messages --- the laptop went to do its reboot after updates and ever since it won't boot up and all my recovery modes do the same thing. The boot up commands (black background, white dos style letters) will show up as the LT boots but then it freezes at a kernel loading command. 
I am a long time ubuntu user but not super fluent on command line or necessarily what the tutorials are telling me: I've been reading the grub tutorial (my prompt is grub>   ---- not grub2 or anything)... I ran the ls command and got hd0, msdos1, hd0, msdos5. I then ran the set command and went to reboot but got the same problem on reboot (boot commands freeze on a kernel). I ran the memtest from the boot menu and all seems fine; no errors. 
Since I'm using a different laptop from the trouble one to type this, its hard for me to paste all the code i get, but i can certainly type in and paste as much as i can. 
Any ideas, suggestions, etc, would be awesomely appreciated. Thank you.

---

### Post by spencer2 on 2016-01-02
I'd really like solve this problem. If its not fixable, help on how to do a data extraction to an external drive is an option before just using a usb to re-load ubuntu 16 --- but i have years of school research & essays, footage from a paul mccartney performance, music, etc... all on the laptop that I'd really like to avoid losing. I do like learning this stuff, so i'm not opposed to reading or looking stuff up, but I'll probably still need help knowing what i should do, look for, expected command results, etc... 
I'd just really rather fix this on my own and save my data from having to find someone who is linux fluent to pay to fix this.

---

### Post by grahammechanical on 2016-01-02
So you get a Grub boot menu. The problem is not with Grub. What happens when you select Advance options for Ubuntu and then select one of the listed Linux kernels with recovery mode? Do you get to a recovery menu?

The comment "all my recovery modes do the same thing" does not give enlightenment. Are there any 14.04 kernels? Or has the upgrade removed all the existing kernels and left only a 16.04 kernel which would be version 4.3.0.

If you can get to a recovery mode menu, you can run Network to establish an internet connection and then Root shell prompt. At a root shell prompt you can run

```

apt-get update
apt-get upgrade
apt-get dist-upgrade
```

That may or may not get you to a working desktop. You can also run a Ubuntu live session and start copying those files off of the hard disk. Or use the live session to create another partition to store the files on or even install Ubuntu on and then transfer the files over.

I have a partition (Ext4) that I keep all my documents on. In this way I do not worry about breaking Ubuntu. And can simply re-install.

For those who do not know. The point has been reached where it is not possible to upgrade 14.04 to 15.04 or 15.10 because 14.10 has reached end of life. In Ubuntu we get 2 upgrade options. The default setting for an LTS is notify me of the next LTS release. We can change that to notify me of the next release. But the next release from 14.04 has reached end of life and the next LTS has not yet been released.

So, if we are on 14.04, then stay there until May 2016. If we are on 15.04, then upgrade to 15.10 before 15.04 reaches end of life at the end of this month (January). If we are on 15.10, then get ready to upgrade to 16.04 by the end of July 2016.

At the moment the only way to get from 14.04 to 16.04 is to run a certain command. And that command will bring us to 16.04 development version with the type of consequences we see here. By the time 16.04 is released the developers would have produced upgrade scripts that make it possible to upgrade to 16.04 with less risk of things going wrong. Those scripts do not yet exist.

Regards.

---

### Post by spencer2 on 2016-01-02
When i boot up and use the safe boot modes, a whole list of them, any that I select freeze up during the boot process. I have chosen pretty much every listed recovery point (i can access a list of them through my boot menu). 
I do use the advanced options selection from the 4 item list (as seen on the top of the this link: [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)) --- but they all freeze in the boot up process; hence why i'm working in grub menu. 
On a side note/background; I don't know why my notify of version upgrade option wasn't selected. I had been thinking that my OS should've upgraded for quite some time. I do think I remember using the code you indicated above (the terminal command code) for my upgrade: i generally do my upgrades through the terminal. I don't know why it hadn't previously upgraded my 14 to 15; but I do think that essentially my running that code, did the default 16 upgrade, and the gap between 14 & 16 (ie, 15), is what is wrong with my laptop.

---

### Post by spencer2 on 2016-01-02
So, I go into the advanced menu and get a list of options: 

Ubuntu, with Linux 4.2.0-19-generic and the list of recovery mode and non recovery mode (but same numeric generic) goes down 3.13 {~55-0}, then 3.8, 3.5, 3.2 {each with only a couple generic numerics [save 3.2 which has many gen. nums]} and eventually ends at 2.6.38-12 generic. All boot freezes tend to end with 'Kernel panic - not syncing: attempting to kill init!' roughly abouts somewhere near the end of the freeze.

---

