---
title: "Installation Problems ASUS G1s"
date: 2008-03-09
forum: Installation &amp; Upgrades
---

### Post by nyto on 2008-03-09
Hi guys, I'm having quite a few problems he trying to install Ubuntu on my ASUS G1s laptop.

I burned a live DVD and chose to boot from CD. 

The first few times when I tried to install I just got a black screen and had to pull the power out to force the computer to restart.

After searching on-line, used F6 to add break=top then ran the install still got a black screen. Rebooted again via removing power.

I repeated the above and changed the screen from VGA to 1025x768x32. At the command prompt I put in "modprobe piix" and "exit", this took me to another black screen. So I pulled the power again.

The third time, I stayed on VGA, when I got to what I assume was the command prompt (couldn't see because of the black screen), I typed in "modprobe piix" and "exit". Then I saw what looked to me like Ubuntu installing (Ubuntu logo and text with an installation bar). As the installation bar finished, once again my screen went black.

That's as far as I got, I was doing this yesterday so I might've got my screen displays mixed up.

//Nyto

---

### Post by Pumalite on 2008-03-09
Post your specs. Try the Alternate CD.

---

### Post by nyto on 2008-03-09
ASUS G1S-A1 
Intel® Core™2 Duo Processor T7500 2.2 GHz, 800 FSB, 4MB L2 Cache
2048MB DDR2 667Mhz (1GBx2)
160GB 5400R SATA
15.4" WSXGA+ (Glare) (1680*1050)
NVIDIA 8600MGT 256MB (GDDRIII) (DX10)

---

### Post by Pumalite on 2008-03-09
Definitely install with the Alternate CD and configure your xserver at the end of the install.

---

### Post by nyto on 2008-03-10
Thanks Pumalite, I'll try that when I get home from work today.

Could you tell me or link me to a place that gives me information on what I need to do to "configure your xserver"?

And is there anything that I need to do prior to installing, other then having un-partioned space on my hard-drive?

Thanks,
//Nyto

P.S. I'm running Windows Vista right now and will be dual booting...

---

### Post by RSLxH on 2008-03-10
> **nyto said:**
> Thanks Pumalite, I'll try that when I get home from work today.

Could you tell me or link me to a place that gives me information on what I need to do to "configure your xserver"?

And is there anything that I need to do prior to installing, other then having un-partioned space on my hard-drive?

Thanks,
//Nyto

P.S. I'm running Windows Vista right now and will be dual booting...

Firstly, after the install, you will need to install your Nvidia driver, either the Open Source Driver from the repos, or the proprietry driver from the nvidia website. Then you can run "sudo dpkg-reconfigure xserver-xorg" in the terminal and an xserver config will appear where you need to answer a series of questions step by step. 

As for the dual boot, howto-forge has a good gude:
[http://howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty](http://howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty)

If you search Google for "dual-boot vista ubuntu" you will get a huge list of them.

Good luck

---

