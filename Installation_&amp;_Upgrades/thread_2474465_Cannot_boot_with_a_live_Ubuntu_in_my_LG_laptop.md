---
title: "Cannot boot with a live Ubuntu in my LG laptop"
date: 2022-04-30
forum: Installation &amp; Upgrades
---

### Post by gmvsfl on 2022-04-30
[COLOR=#141414]Hi everyone. I am trying to install Ubuntu on a USB pendrive but first, I **try to boot with a USB ISO of Ubuntu 22**.
I haven't been able to any of the ways to boot Ubuntu USB. I have already tried several ways. In Bios I set secure boot disabled, and I&#8217;ve tried to let legacy and/or uefi. But when laptop starts, only show me windows boot option, none usb option. I&#8217;ve tried to format several times.
This is a windows 11 LG laptop:[/COLOR][INDENT][COLOR=#141414][FONT=&amp]It&#8217;s an LG laptop I-7 16GB, with windows 11. Bios is Inside GC198 version SMBIOS 3.2&#8230; The ISO is Ubuntu 22 desktop burned with balenaetcher, rufus, lilo&#8230;&#8230;. in various pendrives  [/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]It seem to me too that BIOS doesn't allow itself to be manipulated so much. I can mainly change UEFI or LEGACY, order of booting and SECUREBOOT or NOT. At least in my opinion, in what matters most about this problem.[/FONT][/COLOR][/INDENT]
[COLOR=#141414][FONT=&amp]In the past with another laptops of other brands never been given so much trouble. It's impossible. I can't get it.[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]Please help me someone.[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]Thank you.[/FONT][/COLOR]

---

### Post by yancek on 2022-04-30
Are you able to test the USB on another computer to verify that it boots to eliminate that as the problem?  If your drive is GPT and you have windows 11, then it is a UEFI install so you don't need Legacy enabled in the BIOS.  In your BIOS firmware Boot Options, I would expect you would be able to see the USB as an option, usually by the name of the disk manufacturer.  Could you post the options you do see in Boot Options in the BIOS?

---

### Post by tea for one on 2022-04-30
Also, please post security options in your UEFI Set-Up pages.
TPM (Trusted Platform Management)
PTT (Platform Trust Technology) 
Optane
Device Guard
Or similar options

---

### Post by GhX6GZMB on 2022-04-30
On "problem" laptops I prefer booting from a DVD with the .ISO image. The BIOS setup is usually easier, and you have audible feedback when booting, saving a lot of useless waiting time.

---

### Post by gmvsfl on 2022-05-02
> **tea for one said:**
> Also, please post security options in your UEFI Set-Up pages.
TPM (Trusted Platform Management)
PTT (Platform Trust Technology) 
Optane
Device Guard
Or similar options

[ATTACH=CONFIG]290376[/ATTACH][ATTACH=CONFIG]290377[/ATTACH][ATTACH=CONFIG]290378[/ATTACH][ATTACH=CONFIG]290379[/ATTACH][ATTACH=CONFIG]290380[/ATTACH]

---

### Post by gmvsfl on 2022-05-02
[ATTACH=CONFIG]290381[/ATTACH]

[ATTACH=CONFIG]290382[/ATTACH]

> **tea for one said:**
> Also, please post security options in your UEFI Set-Up pages.
TPM (Trusted Platform Management)
PTT (Platform Trust Technology) 
Optane
Device Guard
Or similar options

---

### Post by gmvsfl on 2022-05-02
Those are the screenshots of the actual setupo on my bios.

---

### Post by tea for one on 2022-05-02
Post 9 - Your TPM configuration is currently [COLOR="#0000FF"]ftpm[/COLOR], which looks like it is enabled.
Can you set it to Disabled?

Any luck with booting the USB?

---

### Post by oldfred on 2022-05-02
Many systems need UEFI firmware update.
And if SSD, SSD firmware update.

Have not seen LG before, but others with Insyde.

Acer needed f9 to open more settings with Secure boot on.
 InsydeH20 setup utility
[https://askubuntu.com/questions/870022/how-to-get-grub-boot-option/870074](https://askubuntu.com/questions/870022/how-to-get-grub-boot-option/870074)
[https://askubuntu.com/questions/886536/how-to-install-ubuntu-on-an-acer-with-preinstalled-windows-10-home](https://askubuntu.com/questions/886536/how-to-install-ubuntu-on-an-acer-with-preinstalled-windows-10-home)
Aspire E1-522 InsydeH20 Bios unlock -  7 min video
[https://www.youtube.com/watch?v=7SkBFkzOW0A](https://www.youtube.com/watch?v=7SkBFkzOW0A)

I have in my notes this.
 December 5, 2019  the new products powered by InsydeH2O and verified under Project Athena are the Acer Swift 3 and Swift 5, HP Envy 13 Wood Series, and the Lenovo Yoga C940 and Yoga S740
Project Athena is Intel standardization.
[https://www.intel.com/content/www/us/en/newsroom/resources/press-kits-project-athena.html#gs.z9c2bm](https://www.intel.com/content/www/us/en/newsroom/resources/press-kits-project-athena.html#gs.z9c2bm)

---

