---
title: "Trouble dual-booting Dell XPS 7390"
date: 2019-11-21
forum: Installation &amp; Upgrades
---

### Post by acrosome2 on 2019-11-21
To my great annoyance, I had to buy a Windows 10 machine to be able to remote log in for my new job, so I got the aforementioned Dell XPS 7390, which I just picked up today.  I would of course like to dual-boot it with Ubuntu so that I can actually use it for other things, but I am finding that my years of avoiding anything Microsoft have left me a little shaky on some Microsofty details

First, I tested my bootable Ubuntu 18.04 USB on the machine first, and it worked.

I had googled around, so I then followed the instructions that I found on the Dell website about setting the Bios to UEFI, disabling Legacy Option ROMS, and disabling Secure Boot before actually doing the installation.  I also used the Windows 10 utility to shrink the Windows partition.  Two annoying things happened:

1. Bitlocker demanded it's key, which I eventually found on my (retch!) Microsoft account.

2. The bootable USB no longer works.  It just displays some very very tiny text in the upper left corner of the screen- all I can make out is the word "fail"- and then shuts down.

Hmm.  So, I think I figured out how to turn off Bitlocker, but I've been hesitant to do that yet until I check in with you all.  Any huge downside to that?  My remote work log in uses Citrix Receiver- will turning off Bitlocker interfere with that?  Is this Bitlocker issue the reason the USB boot failed?

For now I have set Secure Boot back on so that I don't have to keep re-entering the Bitlocker key, though I left the other Bios settings changed and the bootable Ubuntu USB *still* no longer works.  Any idea why?  I had been hoping this would be easy, since the 7390 is available from Dell with Ubuntu pre-installed, so at least I know the hardware is compatible, and it's certainly on Canonicals list of compatible machines.

P.S. Microsoft Office is a frikkin *subscription* now?!?  You have to pay $100 for it *every year*?!?

---

### Post by oldfred on 2019-11-22
do not know for sure as we normally have you turn off all the Windows settings.
But you should be able to leave Windows fast start up on, and bitlocker on, but then have to dual boot from UEFI boot menu, not from grub menu. Only a minor inconvience. You still can set in UEFI to default boot the system you use the most.

Most Dell systems have drives set to RAID/Intel RST and you need to install AHCI drivers into Windows first, then change UEFI setting to AHCI.

Even new Dells may need UEFI update and if SSD, SSD firmware update.

How to Install Ubuntu Linux on your Dell PC 
[https://www.dell.com/support/article/us/en/04/sln151664/how-to-install-ubuntu-linux-on-your-dell-pc?lang=en](https://www.dell.com/support/article/us/en/04/sln151664/how-to-install-ubuntu-linux-on-your-dell-pc?lang=en)

Ubuntu 19.10 Provides Good Out-Of-The-Box Support For The Dell XPS 7390 Icelake Laptop
[https://www.phoronix.com/scan.php?page=article&item=dell-xps7390-ubuntu1910&num=1](https://www.phoronix.com/scan.php?page=article&item=dell-xps7390-ubuntu1910&num=1)
[https://www.phoronix.com/scan.php?page=news_item&px=Dell-XPS-7390-More-Options](https://www.phoronix.com/scan.php?page=news_item&px=Dell-XPS-7390-More-Options)
Dell XPS 15 Series 7590 (2019)
[https://askubuntu.com/questions/1161456/how-to-run-ubuntu-on-new-dell-xps-15-7000-series-7590](https://askubuntu.com/questions/1161456/how-to-run-ubuntu-on-new-dell-xps-15-7000-series-7590)
[https://github.com/TillmannBerg/Ubuntu-Dell-XPS-15-2019](https://github.com/TillmannBerg/Ubuntu-Dell-XPS-15-2019)
DELL Inspiron 15 7577 18.04 needed boot parameters
[https://ubuntuforums.org/showthread.php?t=2386049](https://ubuntuforums.org/showthread.php?t=2386049)

---

### Post by acrosome2 on 2019-11-23
I have no angst booting from the UEFI menu- by far most of the time I'll only be using this machine to remote log in to work using Win 10 anyway.

The odd thing, as I mentioned, is that my bootable USB worked once but now somehow fails.  It was 18.04 though.  I'll go try to reset everything back to it's initial state (except for AHCI as mentioned in your link) and then try the 19.10 install.  I really prefer the LTS versions, but I guess I'll work with what I can work with.

More will follow.

---

### Post by acrosome2 on 2019-11-23
Yes, 19.10 installed effortlessly.  I have to wonder what the difference is?  (Maybe I've just learned how to use UEFI better in the past few days?)  Except for AHCI I had reset all of the UEFI settings to their original states, so that's all that's needed.

Thanks.

---

### Post by mörgæs on 2019-11-23
New hardware needs new software. It's also mentioned in the first Phoronix article that 19.10 is the best choice. 

Thanks for marking the thread solved.

---

