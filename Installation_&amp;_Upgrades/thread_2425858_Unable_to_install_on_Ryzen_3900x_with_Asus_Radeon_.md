---
title: "Unable to install on Ryzen 3900x with Asus Radeon rx 5700 xt"
date: 2019-08-31
forum: Installation &amp; Upgrades
---

### Post by baguacircle on 2019-08-31
Hello,

I recently purchased the Ryzen 3900x and ASUS RT 5700 XT  largely due to the reports of built in kernel support. So far I have  been unable to install Ubuntu successfully. I have trying running the  live installer for 18.04.2, 18.04.3 as well as 19.04 to no avail.

I am seeing the following errors when trying to boot into the live install:

[ATTACH=CONFIG]283904[/ATTACH]

My hardware is as follows:

Motherboard: MSI MPG x570 Gaming Pro Carbon Wifi
Processor: AMD Ryzen 3900X
Graphics: ASUS Radeon RT 5700 XT
RAM: 32GB

I have updated the BIOS to the latest version as of 8/26 as I have read that the previous issues had been resolved. 

[ATTACH=CONFIG]283905[/ATTACH]

I have ensured that secure boot is not enabled. 

I have seen multiple articles that seem to indicate people have gotten this working with the processor / graphics combo.

[https://level1techs.com/article/ryzen-3000-radeon-5700-xt-ready-linux](https://level1techs.com/article/ryzen-3000-radeon-5700-xt-ready-linux)

[https://forum.manjaro.org/t/amd-ryzen-7-3700x-and-radeon-rx-5700-xt-support/94005](https://forum.manjaro.org/t/amd-ryzen-7-3700x-and-radeon-rx-5700-xt-support/94005)

[https://www.reddit.com/r/linux_gaming/comments/cabvl1/ryzen_7_3700x_and_radeon_rx_5700_xt_on_manjaro/](https://www.reddit.com/r/linux_gaming/comments/cabvl1/ryzen_7_3700x_and_radeon_rx_5700_xt_on_manjaro/)

I am hoping that someone has indeed gotten this to work and can help troubleshoot the issue.

Thank you.

---

### Post by Autodave on 2019-08-31
Have you enabled AHCI in the BIOS?  That is the error that you are getting.  Spinned HDs must have that enabled, SSDs will work w/o it, but should be enabled anyhow.

---

### Post by Autodave on 2019-08-31
After that, you may need to refer to this link for the graphics card:  [https://ubuntuforums.org/showthread.php?t=2425799](https://ubuntuforums.org/showthread.php?t=2425799)

---

### Post by oldfred on 2019-08-31
Have you updated UEFI?

       AMD UEFI/BIOS update for Ryzen 3000 series
[https://www.phoronix.com/scan.php?page=news_item&px=Ryzen-3000-BIOS-Update-Good](https://www.phoronix.com/scan.php?page=news_item&px=Ryzen-3000-BIOS-Update-Good)
AMD Releases BIOS Fix To Motherboard Partners For Booting Newer Linux Distributions July 2019
[https://www.phoronix.com/scan.php?page=news_item&px=AMD-Releases-Linux-Zen2-Fix](https://www.phoronix.com/scan.php?page=news_item&px=AMD-Releases-Linux-Zen2-Fix)
[https://www.phoronix.com/scan.php?page=article&item=ryzen-3700x-3900x-linux&num=2](https://www.phoronix.com/scan.php?page=article&item=ryzen-3700x-3900x-linux&num=2)

---

### Post by baguacircle on 2019-08-31
Hi Autodave,

The AHCI is enabled in the BIOS. 

[ATTACH=CONFIG]283907[/ATTACH]

Thanks for the link regarding the graphics card. At the moment I can't even get it to boot to a terminal in Ubuntu though, so I'm not sure how I'm going to run the apt install. 

@oldfred I saw those posts on Phoronix and I believe I have the latest BIOS from MSI with the 7B93v124(Beta version) that was released on the 26th. I have tried installing with all three of the release versions mentioned in my original post after updating the BIOS to the latest. 

I have a bad feeling that there is still something needing fixed in the BIOS as I did manage to get Windows installed but am seeing an issue with Destiny 2. Prior to the latest BIOS update it wouldn't even show up on the screen when trying to run Destiny 2. After the update I thought it was working but I was only able to play for about 5 minutes or so before the machine rebooted. I think the graphics card got too hot but I'm not sure. I know Destiny 2 has also been an issue with this processor and graphics card. 

Perhaps others that got this to work were using different motherboards with a better BIOS fix?

For full disclosure, I've also tried installing Manjaro KDE 18.1.0rc8 as well as 18.04-stable, Debian 9.9.0, 10.0.0 and PopOS 19.04 to no avail. I did see somewhere that apparently FreeBSD installs great on it out of the box but I haven't tried it yet.

---

