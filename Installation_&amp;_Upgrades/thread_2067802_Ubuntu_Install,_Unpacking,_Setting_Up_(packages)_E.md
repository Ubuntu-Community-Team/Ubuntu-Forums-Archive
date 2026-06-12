---
title: "Ubuntu Install, Unpacking, Setting Up (packages) Extremely Slow"
date: 2012-10-07
forum: Installation &amp; Upgrades
---

### Post by victor9191 on 2012-10-07
When I installed the latest Ubuntu on my laptop A53SV it took over 2 hours. I noticed in the log that the unpacking was taking the longest. The boot up was quick, software runs quick. I enabled discard,noatime etc. Everything runs great, however when I install packages or even update, the unpacking and setting up takes FOREVER. I benchmark'd the SSD and found the speeds to be really fast. Unraring or Unziping files is fast as well. However, installing any package with apt-get or even Ubuntu software manager is painfully slow. Any advice?

---

### Post by oldfred on 2012-10-08
How much RAM does your system have. Two hours is too long unless system has issues somewhere. 

Do you have parts of system on SSD and parts on a rotating drive? But even my older systems do not take that long.

---

### Post by victor9191 on 2012-10-12
Thanks for replying! 4GB of ram, no it's all on a 128GB SSD. The SSD works great in windows 7. I have only ubuntu on the SSD now. The system is core i7 mobile. I know it runs well, I can't figure out why it's only these processes that take so long. Regular Unrar works fast.

---

### Post by oldfred on 2012-10-12
I have a core duo with 4GB of RAM. I actually install using grub2 to loopmount the ISO on the rotating drive to install to SSD. It takes about 9 minutes. My SSD is a slower one also. Some are spec'd at twice what mine runs at.

Updates take longer as download speed is not as fast, but since last upgrade from Comcast even that is faster now, if I use a local mirror.

Have you changed settings in fstab to reduce writes. You still need discard for trim and noatime to reduce writes. Is BIOS in AHCI or using UEFI?

---

### Post by Ubuntu Warrior on 2012-10-30
Bought a new V4 128GB SSD from Crucial and thought this would put stripes on my Dell OptiPlex GX520 desktop but alas I have the same problems as above. Three failed attempts to install 12.04 (went into a loop, then lost some elements of the screen and finally locked hard) and it took FOREVER to go through the process.

Then tried lubuntu and got that installed but took about 4 hours.

Now wondering if I should send this SSD back to Crucial or try to tweak the OS. Busy creating an install DVD for 12.10 and hoping this will fare better. Really frustrating as I had believed all the hype about an SSD giving life to an old system :(

The same box with a Western Digital WD1600 HD installed 12.04 in less than 40 minutes.

What gives?????

---

### Post by oldfred on 2012-10-30
@Ubuntu Warrior
Again how much RAM?

 Years ago I tried to install full Ubuntu to a PC with only 128MB. I think then 256MB was the minimum, but I did not know that. But I had already created swap and it used swap and installed. But it was 6 hours. :)

If not a lot of RAM, having swap helps, but I normally do not suggest swap on SSD. Also the text based Alternative installer may work better. Same install but less overhead on install plus some extra drivers instead of gui. But there is no alternative for 12.10.

---

