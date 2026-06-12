---
title: "Which forum?"
date: 2022-02-23
forum: Installation &amp; Upgrades
---

### Post by brianon on 2022-02-23
My Chromebook is almost at the end of updates, but I hope to continue using the device by installing Linux. I found the following installation procedure. It looks too easy. Has anyone tried it? 

1. Open Chrome OS developer shell by Ctrl, Alt, and T, key combination. When "Welcome to crosh..." appears, enter the “shell” command at the crosh> prompt:

```
shell
```

2. To update Chromebook’s firmware enter the following terminal command:

```
cd; curl -LO https://mrchromebox.tech/firmware-util.sh && sudo bash firmware-util.sh.
```

3. After firmware update runs enter “1” which installs the update.

4. Continue by entering the terminal command:

```
cd ; curl -Os https://chrx.org/go && sh go.
```

5. Crosh terminal will ask for confirmation of the storage partition. Input the “N” key to continue the installation.

6. Pick a size to allot to GalliumOS. At least 3 GB of free space is needed for the operating system. Then press the “Enter” key.

7. Chromebook will restart. When it's back, the system will be repairing itself. Let the device turn on by itself. The time it takes depends on the hardware.

8. When Chrome OS turns back on, enter the following command at the crosh terminal to begin installing GalliumOS:

```
cd ; curl -Os https://chrx.org/go && sh go
```

9. The Linux-based operating system is now installed on Chromebook. Turn the device off and back on. At the boot screen press Ctrl, L, keys together to boot GalliumOS.

source: [https://chromeready.com/5612/set-up-configure-linux-chromebook/amp/](https://chromeready.com/5612/set-up-configure-linux-chromebook/amp/)

I would be more confident trying the installation knowing the commands are correct and complete. My guess is "Installation and Upgrade" is the right forum. Even if it works for me, I hope to gain a better understanding of what I'm doing than just get it done and move on.

---

### Post by wildmanne39 on 2022-02-23
Moved to Installation and Upgrades sub-forum.

---

### Post by tea for one on 2022-02-24
> **brianon said:**
> 6. Pick a size to allot to GalliumOS. 

Is your Chromebook listed in the Gallium OS devices page?
[https://wiki.galliumos.org/Hardware_Compatibility](https://wiki.galliumos.org/Hardware_Compatibility)

---

### Post by brianon on 2022-02-24
[COLOR=#000000][FONT=sans-serif]Acer Chromebook 15 (CB3-532)[/FONT][/COLOR]

---

### Post by him610 on 2022-02-25
Chrome OS Flex. [https://www.aboutchromebooks.com/news/chrome-os-flex-isnt-the-solution-for-chromebooks-past-their-software-support-date/]("https://www.aboutchromebooks.com/news/chrome-os-flex-isnt-the-solution-for-chromebooks-past-their-software-support-date/")

Someone will figure out how to install Chrome OS Flex on a Chromebook eventually; maybe, even with Google's blessing.

---

### Post by brianon on 2022-02-27
Thanks, but this is not worth going to the trouble for the inexpensive notebook that came with ChromeOS. As for over-writing ChromeOS with Gallium, I got as far as this:

sh: 0: Refusing to exec go from noexec mount; see [https://chromium.googlesource.com/chromiumos/docs/+/master/security/noexec_shell_scripts.md](https://chromium.googlesource.com/chromiumos/docs/+/master/security/noexec_shell_scripts.md)

I'm looking at a brand new Chromebook notebook at the electronics store for a whopping $149.00 (another throw away in a couple of years.)

---

### Post by TheFu on 2022-02-27
I saw an Asus 15inch Core i3 very similar to my Asus laptop for $270 on  a deal site earlier today. [https://slickdeals.net/f/15643492-asus-vivobook-15-f512ja-ph31-bac-15-6-ultrabook-laptop-for-269-99?src=SiteSearchV2Algo1](https://slickdeals.net/f/15643492-asus-vivobook-15-f512ja-ph31-bac-15-6-ultrabook-laptop-for-269-99?src=SiteSearchV2Algo1) It was at Staples (a US office supply store). I'd get that before any Chromebook. Much more capable, more RAM, faster CPU, and replaceable storage, without all the ChromeOS limitations and forced upgrades when Google decides.  Comes with Windows-S, but that's easy to wipe.  It will run any Ubuntu with the i3-10xxx series CPU (5100 passmarks) or you can load a ChromiumOS, if you really want that.  Still a throw-away device, but it should last much longer.  The 1080p screen will be an upgrade over all the cheapo chromebooks.

Of course, a 15in laptop isn't as portable as a 13in or 11in which could be an issue for some.  I miss my 13in laptop - which was a converted chromebook, but that device was fairly high-cost at around $500 after I swapped the 16G m.2 SATA SSD for a 120G version.  Wasn't able to upgrade the RAM to 8G, which always felt limiting to me, but I use virtual machines all the time.

---

### Post by brianon on 2022-03-01
thanks for yhe verbose reply, much appreciated, have been in Chromebook tranquility for so long first i heard of wondos-s, looks like Microsoft playing catchup, can dual boot? was considering a winddos refurbbed, overwrite that w ubuntu, but yhe first thing i would download chrome and right back where i started; anyway, you are wasting your time if you are not working at apple/microsoft/google; I just earned my first badger, ima start a new thread, later...

---

